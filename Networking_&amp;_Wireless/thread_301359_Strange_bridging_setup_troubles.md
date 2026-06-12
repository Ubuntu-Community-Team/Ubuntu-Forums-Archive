---
title: "Strange bridging setup troubles"
date: 2006-11-17
forum: Networking &amp; Wireless
---

### Post by pooryorick on 2006-11-17
I'm having some troubles with a particularly aggravating network setup...

Two Ubuntu boxes: boxA and boxB. boxA has an Atheros wireless interface ath0 (10.1.1.11) and a wired ethernet interface eth0 (10.1.1.91). boxB has a wired ethernet interface eth0 (10.1.1.92)

ath0 on boxA is connected to the greater network (this is the router & gateway at 10.1.1.254, plus some other devices).

boxA and boxB are crossover-connected by eth0 on each machine (i.e. 10.1.1.91 is connected to 10.1.1.92).

Now the plan is to allow boxB to get full network access (including Internet) through boxA. I've been playing with route and arp for about two days on and off, and I've got them able to ping each other, but I cannot seem to get actual data to forward through boxA.

My arp:
Address                  HWtype  HWaddress           Flags Mask            Iface
boxB                     ether   (mac)  CM                    ath0
10.1.1.254               ether   (mac)   C                     ath0

Kernel IP routing table:
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
why             *               255.255.255.255 UH    0      0        0 eth0
10.1.1.0        *               255.255.255.0   U     0      0        0 ath0
10.0.0.0        *               255.0.0.0       U     0      0        0 eth0
default         10.1.1.254      0.0.0.0         UG    0      0        0 ath0


Sorry if that's too hard to read. If you can tell me how to copy and paste bash tables into this forum easily I can do it again. :-| 

My only thought is that the arp for boxB should be on device eth0.

This is driving me nuts, any help would be massively appreciated.

---

