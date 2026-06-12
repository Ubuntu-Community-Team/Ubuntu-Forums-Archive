---
title: "do i installed Ubuntu correctly ????????????"
date: 2011-07-23
forum: New to Ubuntu
---

### Post by jpjohnj on 2011-07-23
currently i had a problem with system performance..........


i installed ubuntu in my laptop.i made 20gb for root and 300gp for swap.does this affect my system performance....


if yes...how to chance the partition size in ubuntu or do i have any solution for that..


i need your help ...............

---

### Post by bodhi.zazen on 2011-07-23
300 gb for swap is wayyy too much.

IMO swap should be = ram X 2 max 1 gb, unless you are using a laptop / netbook and wish to hibernate / suspend in which case swap = ram + 128 mb.

If this is a fresh install, simply re-install and go with the default partition sizes or as an alternate boot the live CD , fire up gparted, unmount your swap, and re-seize away.

---

### Post by jpjohnj on 2011-07-24
thank you...


after installing ubuntu 11.04 , my system performance is slow now.it hang,when i am opening  multiple programs. my system configuration is

[B]CPU : Intel Pentium P6100 processor , 3MB L2 cache , 2GHz
Mobile Intel HM55 Express Chipset
System memory
Dual-channel DDR3 SDRAM support
1 GB DDR3 memory, upgradable to 4GB using two soDIMM modules
Display : 15.6-inch HD 1366 x 768 (WXGA) pixel resolution,16:9 aspect ratio
Graphics : Intel HD Graphics with 128 MB of dedicated system memory, supporting Microsoft DirectX 10
[/B]

i am allocating 20GB for root and 300GB for swap memory.does this kind of memory allocation slowdown my system performance.........

if yes......i need a solution....please help me...

---

### Post by dragonboss on 2011-07-24
300GB for swap is unnecessary, it should usually be at least the same size as your installed RAM, for more info on swap see [here]("https://help.ubuntu.com/community/SwapFaq")
I would assume this may be the cause of the slowdowns you're experiencing. Also, in my experiences with Ubuntu, when the hard disk is close to being full, the system does slow down as well.

---

### Post by amjjawad on 2011-07-24
> **jpjohnj said:**
> i am allocating 20GB for root and 300GB for swap memory.

Please, read this: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)


[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by knutschr on 2011-07-24
Install and run gparted to change the size.
```
sudo apt-get install gparted
```

---

### Post by 3rdalbum on 2011-07-24
300 gigs swap is very likely to slow down your computer because it has to keep track of all that memory.

I highly recommend NOT using Gparted to resize a hard disk that is currently in use! Instead, use the Partition Editor tool when booting from the Ubuntu CD, or download and burn the Gparted Live CD, and then do the resizing.

---

### Post by amjjawad on 2011-07-24
> **3rdalbum said:**
> I highly recommend [COLOR=Red]**NOT **[/COLOR]using Gparted to resize a hard disk that is currently in use! Instead, use the Partition Editor tool when booting from the Ubuntu CD, or download and burn the Gparted Live CD, and then do the resizing.

I second that!

---

### Post by bodhi.zazen on 2011-07-24
> **jpjohnj said:**
> thank you...


after installing ubuntu 11.04 , my system performance is slow now.it hang,when i am opening  multiple programs. my system configuration is

[B]CPU : Intel Pentium P6100 processor , 3MB L2 cache , 2GHz
Mobile Intel HM55 Express Chipset
System memory
Dual-channel DDR3 SDRAM support
1 GB DDR3 memory, upgradable to 4GB using two soDIMM modules
Display : 15.6-inch HD 1366 x 768 (WXGA) pixel resolution,16:9 aspect ratio
Graphics : Intel HD Graphics with 128 MB of dedicated system memory, supporting Microsoft DirectX 10
[/B]

i am allocating 20GB for root and 300GB for swap memory.does this kind of memory allocation slowdown my system performance.........

if yes......i need a solution....please help me...

Your question was asked and answered my my first post, what part do you not understand ?

---

