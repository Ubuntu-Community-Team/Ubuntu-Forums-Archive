---
title: "Intel pro 100 82557/8/9 issues"
date: 2008-02-26
forum: Networking &amp; Wireless
---

### Post by gramgram on 2008-02-26
Hi folks, I need some help please:

The following is the result of lshw -C network  

*-network DISABLED      

       description: Ethernet interface

       product: 82557/8/9 Ethernet Pro 100

       vendor: Intel Corporation

       physical id: 0

       bus info: pci@0000:02:00.0

       logical name: eth0

       version: 01

       serial: 00:a0:c9:24:f7:02

       width: 32 bits

       clock: 33MHz

       capabilities: bus_master ethernet physical

       configuration: broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI firmware=N/A latency=32 maxlatency=56 mingnt=8 module=e100 multicast=yes

I installed the e1000 linux drivers but still can't see eht0 when I do a ifconfig
I did a reboot, tried the manual network connection with both DHCP and static Ip within the range of the DHCP of my router, but still no internet !

Any help would be greatly appreciated.:(:(

---

### Post by Meserias on 2008-03-14
:lolflag:
You are not alone, as  newbie few time time ago I start with left foot my Linux experience having this Intel PRO/100+ card in my computer. It's installing but doesn't work not EVEN half from a half in comparation with RTL8139.
I spend many time tring to solve this but no luck :(
Piece of OLD crap from INTEL. ](*,):-k

---

