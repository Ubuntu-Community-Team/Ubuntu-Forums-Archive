---
title: "enabling rt2500 wireless"
date: 2005-07-23
forum: Networking &amp; Wireless
---

### Post by sgforums on 2005-07-23
Hi,

I've got a stock ubuntu installation with security and update repositories enabled. 

I've been following the wiki [https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo](https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo)

but when I get to the make stage, I get the following error.

make[1]: Entering directory `/usr/src/linux-headers-2.6.10-5-386'
make[1]: *** No rule to make target `wireless/rt2500-cvs-20050722/Module'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
rt2500.ko failed to build!
make: *** [module] Error 1

This is something quite simple I'm sure, as I haven't seen anyone else on the forum with the same issue with a solution. I thought it might be something obvious such as incorrectly installing build-essential or kernel-headers-$(uname -r) but the apt-get for both of those packages seemed to go without error. 

What does this make error actually mean? Is there something missing in the kernel source or is there something wrong with the wireless module. 

Ta
sg

---

### Post by sgforums on 2005-07-23
I've solved my own problem, somewhat inadvertently. 

Seems that if I untar the rt2500 tar.gz in my home directory it all works fine. If I untar it in a subdirectory of my home directory I get the error described in the previous POST. I assume something to do with paths or environment variables. I'm really not sure what but this made it work. 

sg

---

