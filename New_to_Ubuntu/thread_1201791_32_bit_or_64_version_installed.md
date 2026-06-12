---
title: "32 bit or 64 version installed?"
date: 2009-07-01
forum: New to Ubuntu
---

### Post by riph72 on 2009-07-01
Hello all,
 
How can I actually tell from within Ubuntu, whether I am using the 32 bit or 64 bit version?
 
I know which version I'm using because I installed it, but I want to know how it can be confirmed!
 
Regards,
Richard.

---

### Post by Idefix82 on 2009-07-01
Open the terminal and type in
```
uname -a
```
This will return info about your system, in particular whether it's 32 or 64 bit.

Edit: In fact,
```
uname -i
```
will return exactly what you want.

---

### Post by oldos2er on 2009-07-01
Run **uname -a** in a terminal. If you have 64-bit Ubuntu, you will see something like Linux 2.6.28-13-generic #44-Ubuntu SMP Tue Jun 2 07:55:09 UTC 2009 **x86_64** GNU/Linux, the relevant part being x86_64. If it says i686, it's 32-bit.

---

### Post by riph72 on 2009-07-02
Thanks for the replies, I will do as advised...

---

### Post by riph72 on 2009-07-02
Just out of interest; what would happen if I attempted to install a 64 bit version of Ubuntu on a 32 bit machine?
 
(I am curious, I don't intend actually doing this!)

---

### Post by WRDN on 2009-07-02
> **riph72 said:**
> Just out of interest; what would happen if I attempted to install a 64 bit version of Ubuntu on a 32 bit machine?
 
(I am curious, I don't intend actually doing this!)

When you tried to run the 64bit LiveCD on a machine with a 32bit CPU, it would produce an error message when you selected any option beside Test Memory and boot from first hard disk.

---

### Post by shocktherapyXLI on 2009-07-02
> **WRDN said:**
> When you tried to run the 64bit LiveCD on a machine with a 32bit CPU, it would produce an error message before the options menu appeared.
I think that this answers my question on the thread I made. I wish I would would have read this before I posted it.  Sorry about that.

---

### Post by riph72 on 2009-07-02
> **WRDN said:**
> When you tried to run the 64bit LiveCD on a machine with a 32bit CPU, it would produce an error message when you selected any option beside Test Memory and boot from first hard disk.
 Yes, that's exactly what just happened  :grin:

---

