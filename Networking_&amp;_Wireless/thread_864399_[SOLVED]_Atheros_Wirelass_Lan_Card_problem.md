---
title: "[SOLVED] Atheros Wirelass Lan Card problem"
date: 2008-07-19
forum: Networking &amp; Wireless
---

### Post by 3m_g33k on 2008-07-19
Hello all,

Just recently installed Ubuntu for the first time, so this is a completely new world for me!

Ive managed to get a wired connection working, but my build in wireless card doesnt seem to be recognized at all but I did get a message saying that a propriety driver is being used to support my WIFI card but when I go into my network settings but dont see any option whatsoever to do a scan for wireless networks, is there some additional software I need to install or enable?

Any help would be much appreciated!!

Thanks,

Craig

---

### Post by ojinxy on 2008-07-19
Im in the same boat as you Craig i dual boot so to get wireless im suck rebouting and going into Windows Vista to use wireless where it works like a breeze. Why is linux so hard to configure. Ive trie a lot of fouroumns and none work.

---

### Post by cybrsaylr on 2008-07-19
> **ojinxy said:**
> Im in the same boat as you Craig i dual boot so to get wireless im suck rebouting and going into Windows Vista to use wireless where it works like a breeze. Why is linux so hard to configure. Ive trie a lot of fouroumns and none work.

I just got my Toshiba wireless working yesterday finally thanks to help in this forum. Just go through the threads. Linux is different because you have about 100 distros, some with 8 or 9 versions and then there are so many different PCs out there. Because of this you have to do some digging the get the right working configuration for wireless to work.

---

### Post by 3m_g33k on 2008-07-19
Hey Cybsalyr,

Ive got a Toshiba as well (Equium to be precise) - how did you get your wireless card to work?

---

### Post by ojinxy on 2008-07-19
PCI (sysfs)
*-network
description: Ethernet interface
product: MCP67 Ethernet
vendor: nVidia Corporation
physical id: a
bus info: pci@0000:00:0a.0
logical name: eth0
version: a2
serial: 00:1e:68:85:0d:31
width: 32 bits
clock: 66MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.2.6 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
*-network UNCLAIMED
description: Ethernet controller
product: AR242x 802.11abg Wireless PCI Express Adapter
vendor: Atheros Communications Inc.
physical id: 0
bus info: pci@0000:03:00.0
version: 01
width: 64 bits
clock: 33MHz
capabilities: cap_list
configuration: latency=0

these are my specs im using ubuntu 8.04 hardy if anyone can help me get wireless working i would be forever greatful.

---

### Post by ugm6hr on 2008-07-19
I know it is reassuring to huddle in groups when something doesn't work, but it is only fair to allow the OP to keep his/her thread.

Everyone else - please start your won, unless you are using the same chipset.

If you want help setting up networking, please follow the advice linked here:
[http://ubuntuforums.org/showthread.php?p=5024425](http://ubuntuforums.org/showthread.php?p=5024425)

Breaking my own rules - I will help ojinxy:
> product: AR242x 802.11abg Wireless PCI Express Adapter
Search for AR5007 in this forum (or in Tips and Tutorials) - there are lots of How-Tos for this chipset (note the difference between 32-bit and 64-bit versions though!) - in fact here's one: [http://ubuntuforums.org/showthread.php?t=800686](http://ubuntuforums.org/showthread.php?t=800686)

---

### Post by 3m_g33k on 2008-07-19
Following on from the advice from the last post I found the method outlined here: [http://ubuntuforums.org/showthread.php?t=792158&highlight=AR5007](http://ubuntuforums.org/showthread.php?t=792158&highlight=AR5007) worked best for me. Ive got my wireless up and running now no problem!

Thanks for everyones contributions!

Rock on!:guitar:

---

### Post by fibonaccifreak on 2008-07-19
Sounds like all you have to do is deselect the Atheros drivers [pci and hal] under Hardware Drivers and blacklist the atheros_pci. In a terminal do 'sudo gedit /etc/modprobe.d/blacklist' add 'blacklist ath_pci' to the bottom of the file. The 64-bit windows drivers I use are at [http://blakecmartin.googlepages.com/...-64-0.2.tar.gz](http://blakecmartin.googlepages.com/...-64-0.2.tar.gz). If you use 32 bit use these [http://blakecmartin.googlepages.com/...-32-0.2.tar.gz](http://blakecmartin.googlepages.com/...-32-0.2.tar.gz). did you install the ndis stuff - (ndisgtk, ndiswrappercommon,ndiswrapper-utils) ?

Thanks to Dizzle7677 for the above comment...wireless works like a charm

---

### Post by ugm6hr on 2008-07-19
> **3m_g33k said:**
> Following on from the advice from the last post I found the method outlined here: [http://ubuntuforums.org/showthread.php?t=792158&highlight=AR5007](http://ubuntuforums.org/showthread.php?t=792158&highlight=AR5007) worked best for me. Ive got my wireless up and running now no problem!


Coincidence that the 2 of you have the same wifi chipset :)

---

