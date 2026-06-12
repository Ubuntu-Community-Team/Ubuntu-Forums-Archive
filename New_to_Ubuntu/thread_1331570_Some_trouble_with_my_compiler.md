---
title: "Some trouble with my compiler"
date: 2009-11-19
forum: New to Ubuntu
---

### Post by slip5789 on 2009-11-19
I am having trouble compiling some code that uses POSIX threads. When I include the -lpthread option in the gcc compiler, it fails.  The code is for a class I'm taking and compiles just fine on the lab computers that run RHEL.

I'm wondering if there's a way to ensure I have an up-to-date compiler or if there are any libraries I need to install to get it running properly with pthreads.

Any tips would be appreciated.

---

### Post by ibuclaw on 2009-11-19
> **slip5789 said:**
> I am having trouble compiling some code that uses POSIX threads. When I include the -lpthread option in the gcc compiler, it fails.  The code is for a class I'm taking and compiles just fine on the lab computers that run RHEL.

I'm wondering if there's a way to ensure I have an up-to-date compiler or if there are any libraries I need to install to get it running properly with pthreads.

Any tips would be appreciated.

First, ensure that **libc6-dev** is installed.

If it is, can you post the **entire output** of the compile command.
It is not obvious where it fails to compile the program if you just say "fails to compile".
It could be a missing header ... or the syntax you use.

ie:
```
(int)foo = bar;
```
Is valid gcc3.4, but incorrect in gcc4.0 and later versions.

Regards
Iain

---

### Post by slip5789 on 2009-11-19
I've made some changes to the program since getting the original problem and now it looks like I have a bunch of syntax errors.

Right now I was just looking for a quick terminal command to check the compiler version. I have a feeling it's a syntax error but I would like to find out what gcc version is on the computer that isn't having the problem.

If that doesn't help, I'll post the output once I get the known syntax errors worked out.

---

