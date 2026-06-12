---
title: "prime number proof"
date: 2011-03-15
forum: New to Ubuntu
---

### Post by hdanap on 2011-03-15
Hi Guys,

is there a formula for finding prime numbers, just learning some programming in python and came across this problem set,

Write a function, is_prime, which takes a single integral argument and  returns True when the argument is a prime number and False otherwise.  Add doctests to your function as you develop it.

All i have been able to do is print if the numbers are divisible by the counter printing out true or false.

The solution eludes me.

this is my attempt, im clueless

def is_factor(a,b):
    if a % b == 0:
        print True
    else:
        print False
        
print is_factor(6,4)


def is_prime(n):
    i = 1
    while i <= n:
        is_factor(n,i)
        i+=1
        
       


if __name__ == '__main__':
    import doctest
    doctest.testmod()


help anyone please.  

Please python solution

---

### Post by TeoBigusGeekus on 2011-03-15
How I'd do it in C:
Create a loop from 2 to n-1 (n is the number you want to test).
If any of the divisions n/(all numbers from 2 to n-1) gives a remainder of zero, return false, else return true.

---

### Post by Blutkoete on 2011-03-15
It's enough to test all numbers from 2 to the square root of n.

---

### Post by TeoBigusGeekus on 2011-03-15
> **Blutkoete said:**
> It's enough to test all numbers from 2 to the square root of n.

I stand corrected.

---

### Post by JKyleOKC on 2011-03-15
Since any integer can be expressed as a product of primes (including primes themselves, with factors 1 and itself) you can speed things up a bit by keeping a list of the primes already identified, starting at 2. For any test number n, cycle through the list. If n mod list[i] = 0 return false, else try next list item. If it reaches the end of the list, add n to the list and return true.

You must, of course, set an upper limit for n since it could theoretically go to infinity, as could the list. However for any number than can be expressed in your program, this should work and since the list always will have fewer than n items for any arbitrary value of n to be tested, will always be faster than executing the mod function for all non-prime factors using a counter.

---

### Post by r-senior on 2011-03-15
Were algorithms like the Sieve of Erasthones discussed prior to you being given this homework assignment?

---

### Post by fabricator4 on 2011-03-15
> **TeoBigusGeekus said:**
> How I'd do it in C:
Create a loop from 2 to n-1 (n is the number you want to test).
If any of the divisions n/(all numbers from 2 to n-1) gives a remainder of zero, return false, else return true.


That's a lot of testing, if you want to find the really big primes.

Hint: can you think of ANY non-prime number that is divisible by any other non-prime number, that is NOT divisible also by a prime number.

Also, it is pointless testing for division past (n/2)+1 - the result will always be less than 2.

;-)

Chris

---

### Post by philinux on 2011-03-15
> **r-senior said:**
> Were algorithms like the Sieve of Erasthones discussed prior to you being given this homework assignment?

+1 and if it is homework we dont support it.

---

### Post by hdanap on 2011-03-15
Thanks for the direction, 

This is not homework of any sort, im reading a book "How to think like a computer scientist" and there are exercises you have to figure out before moving to the next chapter, is that considered homework?

well i figured it out


def square_root(n):
    return n ** 0.5


#print square_root(49)


def is_prime(n):
    i = 2
    while i <= square_root(n):
        if n % i == 0:
            return False
        i+=1
    return True
        
print is_prime(7)    

is that good enough

---

### Post by kentrel on 2011-03-15
```

for PrimeTest in range(2,10000):
    IsPrime = 1
    for TestFactor in range(2,PrimeTest):
        if (PrimeTest % TestFactor ==0):
            IsPrime=0
            break

```

---

