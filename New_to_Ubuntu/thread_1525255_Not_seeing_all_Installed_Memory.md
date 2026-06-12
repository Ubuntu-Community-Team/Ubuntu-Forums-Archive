---
title: "Not seeing all Installed Memory"
date: 2010-07-06
forum: New to Ubuntu
---

### Post by Jim2029 on 2010-07-06
I'm running the live cd of 10.06LTS 64Bit AMD and its working great on my HP DV6810us. I ahve 4GB ram installed in this laptop but Ubuntu is only seeing 3.6GB of the ram and using 486mb of it. 

So my questions are, Why doesn't it see the full 4 gigs? AND How much ram does Ubuntu support?

---

### Post by corrytonapple on 2010-07-06
I don't know how much Ubuntu supports, but the Ubuntu live CD is 64 bit, and 64 bit OSes support over 16GB. Is the 3.6GB free memory or total?

---

### Post by Rubi1200 on 2010-07-06
If you go to Applications > Accessories > Terminal on the LiveCD and type this in:

```
free -m
```

what do you get?

---

### Post by cascade9 on 2010-07-06
Its probably seeing 3.6GB because the other 0.4GB is being 'shared' to the video card (no dedicatied video memory means it has to use the main system RAM) 

To be honest, I have no idea of the maximum RAM supported by linux distros, but it would have to be at least 16GB, and I would guess 64GB+.

---

### Post by Rubi1200 on 2010-07-06
> **cascade9 said:**
> Its probably seeing 3.6GB because the other 0.4GB is being 'shared' to the video card (no dedicatied video memory means it has to use the main system RAM) 

To be honest, I have no idea of the maximum RAM supported by linux distros, but it would have to be at least 16GB, and I would guess 64GB+.

Nice answer; I like it!

As an aside; how would one check to see if that is the case?

---

### Post by Rubi1200 on 2010-07-06
Ok, silly me! #-o

```
cat /proc/meminfo
```

This is the way to go; much more complete information there.

---

### Post by Jim2029 on 2010-07-06
I did the command in the terminal and it looks to show 3.8gb regnised. I have 128 shared to video, the max that the bios will allow. So its all found and used.

---

### Post by bodhi.zazen on 2010-07-06
> **Rubi1200 said:**
> Nice answer; I like it!

As an aside; how would one check to see if that is the case?

You will be limited by the motherboard and $$ before you are limited by the kernel

[http://lkml.indiana.edu/hypermail/linux/kernel/0812.2/00292.html](http://lkml.indiana.edu/hypermail/linux/kernel/0812.2/00292.html)

---

### Post by cascade9 on 2010-07-06
> **Jim2029 said:**
> I did the command in the terminal and it looks to show 3.8gb regnised. I have 128 shared to video, the max that the bios will allow. So its all found and used.

Odd, according to HP, up to 1071MB can be alocated to video RAM- 

> **Video  Memory**Up to 1071 MB

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01391847&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=us&product=3686683](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01391847&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=us&product=3686683)

> **bodhi.zazen said:**
> You will be limited by the motherboard and $$ before you are limited by the kernel

[http://lkml.indiana.edu/hypermail/linux/kernel/0812.2/00292.html](http://lkml.indiana.edu/hypermail/linux/kernel/0812.2/00292.html)

16TB- Ohh well, I got the 16 part right at least :lolflag:

---

### Post by pricetech on 2010-07-06
How much RAM is enough ??  More than you currently have.  This rule applies to everyone I know at least.

---

### Post by bodhi.zazen on 2010-07-06
> **pricetech said:**
> How much RAM is enough ??  More than you currently have.  This rule applies to everyone I know at least.

For the "average" Ubuntu desktop you do not need more then 2 Gb, max. For many users 1 Gb is sufficient.

---

