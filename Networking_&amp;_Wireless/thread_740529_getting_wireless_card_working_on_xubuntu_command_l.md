---
title: "getting wireless card working on xubuntu command line only laptop"
date: 2008-03-30
forum: Networking &amp; Wireless
---

### Post by binaryloc on 2008-03-30
synopsis: I need to know how to get ndiswrapper working, as apt-get instal ndiswrapper-utils has been depreciated and ndiswrapper-common doesn't have utils.  Also, I need ot know how to manage an installed network card from the command line.

I've got a dynex chip with that uses the bcm43xx chipset (I'm very upset they don't use atheros anymore!)

Anyway, I am having trouble getting the card set up.  No lights come on, but ifconfig -a registers it as eth1, and iwconfig eth1 essid 'ssid' works just find, except for the fact that the chip doesn't seem to be working, as niether light comes on and I can't connect to any networks.

I need to know how to:
1. get a working driver up.  I may try the ndiswrapper approach, but I tried apt-get install ndiswrapper-utils and apt informed me that ndiswrapper-utils has been replaced with common.  So I apt-get install ndiswrapper-common and I get the message "Error: no ndiswrapper utils found!" when I try to use ndiswrapper.  Hmph.  If someone can tell me how to overcome this annoyance with ndiswrapper, I will be able to get the driver installed I think.

2. connect to a non-wep, non-wpa network from the command line (again, xubuntu command line install.)

if someone could help, that would be great.

---

### Post by binaryloc on 2008-03-30
updae:got it working.  For reference, I rmmod'd ndiswrapper, apt-get remove'd fwcutter, and went into /etc/network/interfaces and took the two lines on eth0, then copies them and replaced eth0 with eth1

then iwconfig eth1 essid 'honey pot'

woohoo!

---

