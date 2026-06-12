---
title: "Segmentation fault"
date: 2010-01-26
forum: New to Ubuntu
---

### Post by newport_j on 2010-01-26
I have a long program that I compiled for 32 bits and ran on 32 Ubunbtu. It worked perfectly. 
 
When I ported the code to a 64 bit Ubuntu system and compiled it for 64 bits, I got a segmentation fault when I ran it. 
 
I then compiled it for 32 bits on the 64 Ubuntu system. When I ran it on the 64 bit Ubuntu, I also got a segmentation fault.
 
Is this possible? It seems to not want to run on 64 bit Linux whether it is compiled for 32 or 64 bits; in each case I get a seg fault.
 
I located using a full screen debugger the line where the computer crashes; is this also the line that the seg fault occurs on?
 
The line that crashes the program occurs early in the program execution so that should mena that finding the seg fault is easier.
 
newport_j

---

### Post by jd65pl on 2010-01-26
Do you have an example of the program? Are all the 32bit dependencies met on the 64bit system?

---

### Post by ibuclaw on 2010-01-26
Are you using longs in your program? :)

Best method I recommend is to leave bread crumbs in your code around debug flags:

ie:
```

#ifdef DEBUG_ON
    printf("%s: line %d in my_function()\n", __FILE__,__LINE__);
#endif

```
Then compile with -DDEBUG_ON

When you run the application, find the last print point before the segfault, then you can continue tracing that section of the code into more fine grain debug points, until you find the killer function that stops it.

Regards
Iain

---

### Post by avidday on 2010-01-26
> **newport_j said:**
> 
 
Is this possible? It seems to not want to run on 64 bit Linux whether it is compiled for 32 or 64 bits; in each case I get a seg fault.

Of course it is possible. The size of some fundamental types changes between 64 bit and 32 bit Linux. It is pretty easy to have some address or large array indexing calculations which are made with signed int on IA32 that will fail on x86_64. Also some casts or unions which are safe on IA32 (where, for example sizeof(int) is equal to sizeof(void *)) will fail on x86_64.
 
> The line that crashes the program occurs early in the program execution so that should mena that finding the seg fault is easier.If you compile the code without optimization settings and with debugging settings on, and then just run the program inside gdb, it will automatically show you the file and line where the segfault is taking place, and typing **bt **will show the call stack so you can see the sequence of function calls that lead to the place where failure occurred.

---

