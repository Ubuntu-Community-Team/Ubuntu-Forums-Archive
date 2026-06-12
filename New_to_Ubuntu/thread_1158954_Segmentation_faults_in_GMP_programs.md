---
title: "Segmentation faults in GMP programs"
date: 2009-05-14
forum: New to Ubuntu
---

### Post by mozza314 on 2009-05-14
Hi

Can't seem to understand why I'm getting segfaults in my program -

```
#include <gmpxx.h>
#include <iostream> 
using namespace std; 
 
int main() 
{ 
    mpz_t fib[3];
    mpz_set_ui(fib[0], 1);
    mpz_set_ui(fib[1], 1);
    //unsigned int fib[3] = {1,1};
    
    int n;
    int i = 2;
    
    cout << "This program finds the nth fibonacci number." << endl; 
    cout << "n = ";
    cin >> n;
    
    for (i=2;i<n;i++)
        mpz_add(fib[i%3], fib[(i-1)%3], fib[(i-2)%3]);
        //fib[i%3] = fib[(i-1)%3] + fib[(i-2)%3];
    
    cout << fib[i%2] << endl;
     
    return 0; 
}
```Could someone else try compiling and running it? It could be my install of gmp...

---

