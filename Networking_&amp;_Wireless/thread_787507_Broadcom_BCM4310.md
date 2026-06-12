---
title: "Broadcom BCM4310"
date: 2008-05-08
forum: Networking &amp; Wireless
---

### Post by coldopm on 2008-05-08
According to this post [http://ubuntuforums.org/showthread.php?t=779754&highlight=BCM4310](http://ubuntuforums.org/showthread.php?t=779754&highlight=BCM4310) it does not work with Hardy. Anyone know otherwise or can help me get my wireless running???

---

### Post by coldopm on 2008-05-08
Someone please help me get my wireless working. Pretty Please!

---

### Post by coldopm on 2008-05-08
PS here is my lshw -C network

coldopm@coldopm-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:09:41:ce:4b
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A ip=24.67.91.177 latency=0 module=sky2 multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
coldopm@coldopm-laptop:~$

---

### Post by WoodyMahan on 2008-05-09
Let's simplify.  I know the card works natively, because I am using one right now.  However, I have noticed that since I upgraded to Hardy, my download speed has noticeably slowed down.  If you need an immediate connect, then make sure your laptop is connected via cable, then go to System> Hardware Drivers.  The Broadcom b43 driver is listed there.  Simply click to enable it and follow the wizard which will download the native driver (which I mentioned above is not perfect).  Other wise you will need to install and configure ndiswrapper which is a program that allows linux to use windows drivers for wireless cards.  Instructions are [_here_]("http://ubuntuforums.org/showthread.php?t=780590").

---

### Post by coldopm on 2008-05-09
> **WoodyMahan said:**
> Let's simplify.  I know the card works natively, because I am using one right now.  However, I have noticed that since I upgraded to Hardy, my download speed has noticeably slowed down.  If you need an immediate connect, then make sure your laptop is connected via cable, then go to System> Hardware Drivers.  The Broadcom b43 driver is listed there.  Simply click to enable it and follow the wizard which will download the native driver (which I mentioned above is not perfect).  Other wise you will need to install and configure ndiswrapper which is a program that allows linux to use windows drivers for wireless cards.  Instructions are [_here_]("http://ubuntuforums.org/showthread.php?t=780590").

System>Admin>Hardware Drivers is empty!? Does that seem off?
Says, "No proprietary drivers are in use on this system."

---

### Post by Ayuthia on 2008-05-09
> **coldopm said:**
> According to this post [http://ubuntuforums.org/showthread.php?t=779754&highlight=BCM4310](http://ubuntuforums.org/showthread.php?t=779754&highlight=BCM4310) it does not work with Hardy. Anyone know otherwise or can help me get my wireless running???
It only states that the native b43 driver might not work (It is currently in the non-working section with a question mark--I have no formal confirmation that it does not work).  NDISwrapper has some confirmations for this card.

You might try to install it via the no-fluff way: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851)

or via alex_kent_18: [http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

---

### Post by WoodyMahan on 2008-05-09
Apparently I am retarded and was unaware of it.  After checking I see that I am using a BCM 4318, which could be completely different than the 4310.  If ndiswrapper doesn't work, you could probably invest in a cheap USB wireless adapter that will run natively with Linux.

---

### Post by MaindotC on 2008-05-20
coldopm what's the status of this issue?  Are you still having problems?

---

