---
title: "kernel choice on 32bit ?"
date: 2009-10-01
forum: New to Ubuntu
---

### Post by nirax on 2009-10-01
Hi,

sorry for the stupid question, but i just recently switched after 5 years gentoo to ubuntu with my amd64 system. 
Im ok running it with 32 bit, but what wonders me is:

are there any processor specific kernels to be installed ? 
In this thread ( [click here for ubuntu forum thread ]("http://ubuntuforums.org/showthread.php?t=242071") ) i see a hint that apt-get install kernel-k7 might be the right ubuntu kernel for my system, yet its not in my list. 
is there only one kind of ubuntu preconfigured kernel available ? (besides compiling by hand)

my uname -a currently:
```
Linux nirax-desktop 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:49:34 UTC 2009 i686 GNU/Linux
```

greetings,
nirax

---

### Post by nhasian on 2009-10-01
unfortunately there is no way to upgrade from 32 bit to 64 bit.  you will need to reinstall with a 64bit ubuntu liveCD.  Luckily for you Karmic Koala Beta ISO was just released today :)

---

### Post by nirax on 2009-10-01
thanks for your reply.
but its clear for me that there is no upgrade path from 32bit to 64bit.

what i am asking is:
Do you have any processor specific kernel build ready in ubuntu ?

like this guy in the post i quoted mentions:

> Re: Which 32bit kernel for amd64?
apt-get install linux-k7

i can perform manually optimized builds for nearly every processor - while remaining on 32bit.. the post suggest such thing was once available in ubuntu already prebuilt. as apt cant find any linux-k7 anymore i wonder if that changed

to be even clearer

I mean a prebuild kernel having the processor family you find running make menuconfig on your kernel sources already set to K7 (As example, of other amd64 (running 32bit) features that could be selected.

here you can find it..
> processor type and features -> processor family

or from .config following preset and compiled with MK7 set.
> CONFIG_M586=y
# CONFIG_M586TSC is not set
# CONFIG_M586MMX is not set
# CONFIG_M686 is not set
# CONFIG_MPENTIUMII is not set
# CONFIG_MPENTIUMIII is not set
# CONFIG_MPENTIUMM is not set
# CONFIG_MPENTIUM4 is not set
# CONFIG_MK6 is not set
# CONFIG_MK7 is not set
# CONFIG_MK8 is not set


edit//mmh looks like i just build it myself. nm

---

### Post by nirax on 2009-10-02
last update:
no custom build kernel required for speed improvement.

found interesting post from the time the optimized kernels were discontinued in ubuntu

[https://lists.ubuntu.com/archives/ubuntu-devel/2006-August/019983.html](https://lists.ubuntu.com/archives/ubuntu-devel/2006-August/019983.html)

thanks all, your devs saved me some tweaking hours :)

---

