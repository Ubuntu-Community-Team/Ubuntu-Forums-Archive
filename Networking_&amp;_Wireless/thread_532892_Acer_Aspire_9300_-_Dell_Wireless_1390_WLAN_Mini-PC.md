---
title: "Acer Aspire 9300 - Dell Wireless 1390 WLAN Mini-PCI Card - help installing"
date: 2007-08-23
forum: Networking &amp; Wireless
---

### Post by bjorntheart on 2007-08-23
I've been trying to get my Acer Aspire's wireless up and running, but nooothing, zip, zero

I've followed this post  [http://ubuntuforums.org/showthread.php?t=224349&highlight=acer_acpi]("http://ubuntuforums.org/showthread.php?t=224349&highlight=acer_acpi")  and installed acer_acpi-0.7.tar.gz.

Here is my lshw -C network output
>  *-network DISABLED
       description: Wireless interface
       product: Dell Wireless 1390 WLAN Mini-PCI Card
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@01:00.0
       logical name: eth1
       version: 01
       serial: 00:19:7e:2c:c5:06
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-16-generic latency=0 link=no multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:c0100000-c0103fff irq:19

I've just recently switched over to Linux. I tried to setup a dual boot Win Vista Home and Ubutuntu Feisty 64bit, but to my own advantage, I wiped the windows partition. I don't regret doing it for one second, but I now need some help with the wireless.

Thanx alot to all the Linux pros who are willing to help

Cia

---

### Post by kevdog on 2007-08-23
Just a few points of clarification --

You are using a 64 bit Ubuntu version?
Do you have a 64 bit driver for your card -- meaning specifically a 64 bit windows XP driver?

Your Dell integrated wireless card has a broadcom chipset.  Two ways to install drivers for broadcom cards are to use the reverse engineered bcm43xx driver, or use ndiswrapper in combination with the Windows XP driver.

Im going to have to look to see if the bcm43xx driver supports 64 bit.
***Edit
Yes there is a 64 bit kernel module for the bcm43xx driver - [http://www.linux-geek.org/index.php/2007/04/22/dell-1390-native-linux-driver-how-to-updated](http://www.linux-geek.org/index.php/2007/04/22/dell-1390-native-linux-driver-how-to-updated)

Your choice which method to use -- both had ad/disadvantages
bcm43xx approach to installing -- much easier, max speed (at this time) 11 Mbs/sec, supports packet injection
ndiswrapper - much more difficult to install (relative comparison), max speed 54 Mbs/sec, no packet injection

---

