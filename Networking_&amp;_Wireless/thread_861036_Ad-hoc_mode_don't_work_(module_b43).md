---
title: "Ad-hoc mode don't work (module b43)"
date: 2008-07-16
forum: Networking &amp; Wireless
---

### Post by name29 on 2008-07-16
I have a wifi card Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g use the diriver b43. The I version of ubuntu is 8.04 (congratulations!). My problem is: I want to create a wifi network ad-hoc only that my laptop shows some problems. To set up ad-hoc arrangements must first throw down the interface with ifconfig and if for example I try to make a iwlist I see the other computers connected to the network ad-hoc but all I see a MAC address other than their own! In the sense if a PC has MAC "00:29:6 d: fe: c0: 3f" I see with iwlist scan: Address "00:21:45: e6: f0: 91." is not a little strange? when then configure iwconfig with "iwconfig wlan0 mode ad-hoc essid name29mesh" and then I see that iwconfig iwconfig tries to associate with "00:21:45: e6: f0: 91" and of course the signal is 0. if they do "iwconfig wlan0 ap 00:29:6 d: fe: c0: 3f" the signal becomes 66.

Another information: how do I see PCs that are connected to my? with iwlist?

---

### Post by waster on 2008-09-06
sadly ad-hoc still not supported by upstream wireless kernel development for the horrible broadcom chips. you have to use ndiswrapper and blacklist ssb and b43.

---

### Post by waster on 2008-09-12
turns out it is supported, but you have to bring down the interface to change mode.

I had lots of crashes using b43, but I think it might have been networkmanager. the changelog showed they had fixed a bug in counting interface references which was known to cause hangs, but i haven't dared go back to b43 yet. ndis works now.

---

### Post by waster on 2008-09-15
seems to be stable with most recent ppa networkmanager 0.7

---

