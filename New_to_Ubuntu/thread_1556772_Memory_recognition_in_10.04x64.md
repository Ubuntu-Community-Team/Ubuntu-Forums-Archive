---
title: "Memory recognition in 10.04x64"
date: 2010-08-19
forum: New to Ubuntu
---

### Post by julri764 on 2010-08-19
New to ubuntu. My system is running the 64 bit version, but only recognizes 3.6 of my 4 gigs.

HP dv5-1125nr
AMD TurionX2
ATI Radeon Graphics

---

### Post by overdrank on 2010-08-19
Hi and welcome, I have moved your post to its own thread. :)

If your system has a integrated graphics card this is what is using your additional memory. :)

---

### Post by Temposs on 2010-08-19
Welcome to Ubuntu, julri!

That reading is probably normal. I think it is recognizing all of your memory, but the calculation of that Ubuntu makes to add together the amount of memory in your computer makes it come out a bit lower than what your sticks of memory say on the package they came in.

I have 2gb of memory and Ubuntu says I have 1.9gb.

---

### Post by uRock on 2010-08-19
This machine has 4GB also, but a small part of it is used by the onboard graphics.(The HP in my signature.)
```
dragonlady@dragonlady-ubuntu:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3709        979       2729          0         57        334
-/+ buffers/cache:        587       3122
Swap:         3059          0       3059

```

---

### Post by rtlustyo on 2010-08-19
I too have an HP pavilion and my memory reads 3.62 GiB, seems pretty normal.

---

### Post by julri764 on 2010-08-24
Thanks for the responses!

---

