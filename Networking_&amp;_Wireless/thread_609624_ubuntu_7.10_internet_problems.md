---
title: "ubuntu 7.10 internet problems"
date: 2007-11-11
forum: Networking &amp; Wireless
---

### Post by shaun1982 on 2007-11-11
Hi everyone,

sorry for the long post!!
I've just installed ubuntu 7.10 on my toshiba laptop. I can't seem to get a internet connection wired or wireless. This is what I've found so far, 

 sudo lshw -C network

-network UNCLAIMED     
       description: Ethernet controller
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0

  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:05:07.0
       logical name: eth0
       version: 10
       serial: 00:1a:92:fa:e6:2b
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
 configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.100.10 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s

The wireless light on the laptop is on. Network manager lists the ethernet interface but not the wireless adapter. the wireless adapter is listed in the Restricted drivers  as 
Atheros Hardware Access Layer (HAL)     ENABLED	IN USE

My windows dual boot works fine.
Any help would be great.
Shaun

---

### Post by westcoasteagles on 2007-11-11
I'm having a similar problem with my dual boot PC. Here is a copy of my post on another section of the forum...

Originally loaded 7.10 on a dedicated drive by itself with no problem - was able to connect to the internet.

Got brave and decided to create a dual boot drive for the same machine. Installed XP first then installed 7.10. Can connect to the internet without any problem in XP BUT can't in 7.10 despite it having worked on the same machine on a dedicated drive.

I noticed that the network icon in the top right corner of the screen has an exclamation mark icon on it.

When I do the "sudo ifconfig" it sees eth0 - but the output doesn't show any stats (or I should say - all stats are 0).

When I do the sudo pppoeconf it timesout and says sorry, check the cable, bla bla bla...

Anyone know why the dual boot system would corrupt this?

cheers
:confused:

So, this seems to be a dual boot issue. Any ideas where to start looking to find the problem?

---

### Post by westcoasteagles on 2007-11-11
there may eventually be an answer to this problem by following this thread...
[http://ubuntuforums.org/showthread.php?t=607276](http://ubuntuforums.org/showthread.php?t=607276)

---

### Post by westcoasteagles on 2007-11-12
Alright, this thread solved my problem....

[http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)

---

