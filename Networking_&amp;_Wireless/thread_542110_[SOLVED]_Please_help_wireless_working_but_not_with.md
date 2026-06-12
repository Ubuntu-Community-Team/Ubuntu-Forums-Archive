---
title: "[SOLVED] Please help wireless working but not with encryption"
date: 2007-09-03
forum: Networking &amp; Wireless
---

### Post by alexkc1 on 2007-09-03
Hello all, this is my first post in any forum so sorry if any things amiss.

I recently installed Ubuntu 7.04, my belkin f5d7001 was recognised by ubuntu and the bcm43xx driver/firmware was added. 

The card did not work with this driver so i have blacklisted it and am using ndiswrapper to load the belkin window drivers. 

The card is now opperational, I can see networks and connect and use unsecured networks however i can't connect or use my network when any encryption is turned on (wpa or wep).

I heave read through some of the forum questions and the stickies but my situation seems to be slightly different, If there is anybody who feels tthey could help I would greatly appreciate it.

Thanks in advance, Alex

sudo gedit /etc/network/interfaces:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

Can't see any wlan?

---

### Post by lsmobrian on 2007-09-03
did you try installing bcm43xx-cutter  (not sure if its still needed or not, this is only used with non ndiswrapper)

with ndiswrapper method, did you install wpa supplicant

ihave us robotics with same driver, i never tried ndiswrapper, but bcm43xx-fwcutter let me do wep and wpa

---

### Post by alexkc1 on 2007-09-03
thank you for the response i have wpa supliment running but haven't tried cutter might try that now

Many thanks,

alex

---

### Post by alexkc1 on 2007-09-03
A fresh install and follow darknoob's sticky and all is good, one happy Linux User

---

