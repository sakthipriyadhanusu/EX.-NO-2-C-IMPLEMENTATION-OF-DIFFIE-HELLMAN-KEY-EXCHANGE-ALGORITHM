# EX.-NO-6-IMPLEMENTATION OF DIFFIE HELLMAN KEY EXCHANGE ALGORITHM

## AIM:
To implement the Diffie-Hellman Key Exchange algorithm using C language.

## ALGORITHM:
  
  STEP-1: Both Alice and Bob shares the same public keys g and p.
  
  STEP-2: Alice selects a random public key a.
  
  STEP-3: Alice computes his secret key A as g a mod p.
  
  STEP-4: Then Alice sends A to Bob.
  
  STEP-5: Similarly Bob also selects a public key b and computes his secret key as B and sends the same back to Alice.
  
  STEP-6: Now both of them compute their common secret key as the other one’s secret key power of a mod p.
  
## PROGRAM:
```#include <stdio.h>
#include <math.h>

int main() {
    int p = 23; // Publicly known prime number
    int g = 5;  // Publicly known primitive root
    int x = 4;  // Alice's private key (only Alice knows this)
    int y = 3;  // Bob's private key (only Bob knows this)

    // Alice computes g^x mod p and sends it to Bob
    double aliceSends = fmod(pow(g, x), p);
    
    // Bob computes (Alice's value)^y mod p to get the shared secret
    double bobComputes = fmod(pow(aliceSends, y), p);

    // Bob computes g^y mod p and sends it to Alice
    double bobSends = fmod(pow(g, y), p);

    // Alice computes (Bob's value)^x mod p to get the shared secret
    double aliceComputes = fmod(pow(bobSends, x), p);

    // For verification: Both Alice and Bob's computed secrets should match
    double sharedSecret = fmod(pow(g, (x * y)), p);

    printf("Diffie-Hellman Key Exchange Algorithm\n");
    printf("Alice Sends : %.0f\n", aliceSends);
    printf("Bob Computes : %.0f\n", bobComputes);
    printf("Bob Sends : %.0f\n", bobSends);
    printf("Alice Computes : %.0f\n", aliceComputes);
    printf("Shared Secret : %.0f\n", sharedSecret);

    // Check if the shared secrets match
    if ((aliceComputes == sharedSecret) && (aliceComputes == bobComputes)) {
        printf("Success: Shared Secrets Match! Shared Secret: %.0f\n", sharedSecret);
    } else {
        printf("Error: Shared Secrets do not Match\n");
    }

    return 0;
}

```

## OUTPUT:
![Screenshot 2024-11-08 195620](https://github.com/user-attachments/assets/7006e090-330f-43fc-96c5-cb682d424a81)


## RESULT:
  Thus the Diffie-Hellman key exchange algorithm had been successfully implemented using C
