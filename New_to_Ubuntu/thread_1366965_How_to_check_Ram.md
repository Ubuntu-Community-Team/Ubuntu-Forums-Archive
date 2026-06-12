---
title: "How to check Ram?"
date: 2009-12-29
forum: New to Ubuntu
---

### Post by mickeyjoe on 2009-12-29
Where do I click or what sudo command in terminal can I type to check how much Ram my system has or can still take?

---

### Post by Mahngiel on 2009-12-29
System > Administration > System Monitor

---

### Post by fatcrab on 2009-12-29
You can also add the monitor to a panel.I keep one there to keep an eye on my cpu.

---

### Post by sandyd on 2009-12-29
use htop / top

---

### Post by ptviperz on 2009-12-29
> **mickeyjoe said:**
> Where do I click or what sudo command in terminal can I type to check how much Ram my system has or can still take?

From the command line:

free -m

```
brent@brent-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          8002       1470       6532          0         85        722
-/+ buffers/cache:        662       7340
Swap:            0          0          0

```

---

### Post by cascade9 on 2009-12-29
> **mickeyjoe said:**
> Where do I click or what sudo command in terminal can I type to check how much Ram my system has or can still take?
Everyones given you good advice on how to tell your current RAM. Its pretty easy to do that. 

As for how much RAM you can actually install...that can be a bit more difficult. A lot of the time you need to actually take the cover off and check the motherboard, as sometimes different version of the same chipset can have several different max RAM amounts (a good example is 815). 

Sometimes different manufacturers have different max RAM for the same chipset. a good example of this is the AMD 785/SB710 chipsets.

Asrock A785GM-LE (AMD 785/SB710, DDR2, 8GB max)-

[http://www.asrock.com/mb/overview.asp?Model=A785GM-LE](http://www.asrock.com/mb/overview.asp?Model=A785GM-LE)

Asus M4A785D-M Pro (AMD 785/SB710, DDR2, 16GB max)- 

[http://www.asus.com/product.aspx?P_ID=yCI8UenairUZJWET&templete=2](http://www.asus.com/product.aspx?P_ID=yCI8UenairUZJWET&templete=2)

---

