---
title: "Wireless Issues"
date: 2008-01-30
forum: Networking &amp; Wireless
---

### Post by Straevaras on 2008-01-30
I'm not sure why but my wireless has disappeared from network manager. I'm getting the following:

```
straevaras@straevaras-laptop:~ sudo lshw -C network
[sudo] password for straevaras:
  *-network:0
       description: Ethernet interface
       product: BCM4401-BO 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:12:3f:18:33:fc
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=half latency=32 link=no module=b44 multicast=yes port=twisted pair speed=10MB/s
  *-network:1 UNCLAIMED
       description: Network controller
       product: PRO/Wireless 2915ABG Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32 maxlatency=24 mingnt=3

```

Any ideas anyone?

---

### Post by Hightide on 2008-01-30
HI Starevaras

Your post states the following:

 *-network:1 UNCLAIMED

this indicates that your driver is not installed. Can you review your driver installation procedures?

Try Kevdog's thread

[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

regards
:)

---

### Post by Straevaras on 2008-01-30
Hey

I'm trying go through the procedure of reinstalling the drivers, but it seems that I can't even do that, I can never get anything to build...

Ubuntu used to be working with my wireless card but then one day it just stopped working and I don't know why...

---

### Post by Straevaras on 2008-01-30
I'm trying to build and install the driver for Intel 2915ABG again but I keep getting the following when I try to build the drivers:

```
straevaras@straevaras-laptop:~/Desktop/ieee80211-1.2.18$ sudo make
Makefile:17: 
Makefile:18: WARNING: $SHELL not set to bash.
Makefile:19: If you experience build errors, try
Makefile:20: 'make SHELL=/bin/bash'.
Makefile:21: 
Checking in /lib/modules/2.6.22-14-386 for ieee80211 components...
grep: /lib/modules/2.6.22-14-386/build//.config: No such file or directory
grep: /lib/modules/2.6.22-14-386/build//include/linux/autoconf.h: No such file or directory
make -C /lib/modules/2.6.22-14-386/build M=/home/straevaras/Desktop/ieee80211-1.2.18 modules
make[1]: Entering directory `/lib/modules/2.6.22-14-386/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.22-14-386/build'
make: *** [modules] Error 2
```

Kevdog's thread doesn't help me any since my network device is Unclaimed and I'm not exactly sure how I would review my driver installation procedures.  When I installed Ubuntu from the beginning, all was good.

It configured and was correctly using my wireless network card with no problems whatsoever.  Now one day, I start up my computer and the driver appears to have completely disappear and the wireless network option is completely gone from network manager.

I've seen a lot of the same problem in other threads, but it appears to me (unless I'm missing something) that none of these problems were actually solved.  Surely someone out there has had this problem and managed to resolve it?

---

### Post by Crimson_Wake on 2008-01-30
my log is similar, except that I have...

logical name: eth0 (wired connection) has no problem connecting.
logical name: eth1 (wifi connection) is DISABLED.

How do I ENABLE my built in wifi card?

I'm running an HP Pavilion ze4400 and I'm running Gutsy solo (no dual boot XP/LX)

Thanks!

---

