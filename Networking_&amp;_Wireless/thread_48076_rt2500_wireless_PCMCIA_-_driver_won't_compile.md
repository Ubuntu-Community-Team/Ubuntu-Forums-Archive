---
title: "rt2500 wireless PCMCIA - driver won't compile"
date: 2005-07-11
forum: Networking &amp; Wireless
---

### Post by sglynn on 2005-07-11
Hi,

I've had Hoary running for a while now, installed mostly as a base install, however as one of the security updates that were kernel related trashed the boot sequence, causing a "kernel panic" I had to upgrade the kernel to a newer version that would otherwise be expected (currently running 2.6.12-3-386)

I was following the installation instructions for the rt2500 @
[https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/](https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/) 

referenced from 
[http://rt2x00.serialmonkey.com/wiki/index.php/HOWTOS](http://rt2x00.serialmonkey.com/wiki/index.php/HOWTOS)

I've tried with both the CVS nightly build and the stable beta build, and in both cases have received the following error when attempting to run make from within the driver/Module directory as instructed by the how-to.

make[1]: Entering directory `/usr/src/linux-headers-2.6.12-3-386'
make[1]: *** No rule to make target `wireless/rt2500-cvs-20050710/Module'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-3-386'
rt2500.ko failed to build!
make: *** [module] Error 1

I have apt-get installed linux-headers for my kernel and build-essentials. My /lib/modules/kernel..../build symlink is also correct. Not sure what the above is trying to tell me? 

Any help appreciated. 

Regards
Simon

---

### Post by scoon on 2005-07-14
Hey there, 

That does not appear to be ubuntu related.  Check with the module maintainers for help. 

regards, 

scoon

---

