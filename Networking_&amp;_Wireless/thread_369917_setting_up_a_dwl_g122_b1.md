---
title: "setting up a dwl g122 b1"
date: 2007-02-25
forum: Networking &amp; Wireless
---

### Post by gundamseedes on 2007-02-25
how do i set up a dlink dwl g122 b1 on ubuntu?.. im having trouble following some guides as they dont proceed well and usualyl end up with errors.. i would appreciate if you could help me thanks!

---

### Post by FreedomIsntFree on 2007-02-25
I have tried for years to get the g122 working.  Most of the tutorials do not work.  This card is simply just not running well on a linux system.  Better off just getting a new card.

---

### Post by gundamseedes on 2007-02-25
hey how about a linksys WUSB54GC

oh yeah btw mines nto a card mines a usb for both linksys and d link

---

### Post by thejacko on 2007-03-09
This is the trick that I make my Ubuntu working with dwl g122 b1,
first, check wether the device has been on the list of device manager,usually this device can be recognized (I have tried it on Ubuntu 6.06, 6.10, and feisty, all of them recognize my device).I'm using static IP address, but I think this can be work as well as if you using DHCP 
If you sure, then you can follow with this steps:
Run teminal program;
type this, sudo ifconfig "your device place" (in my system is rausb0) " your IP address"
example: sudo ifconfig rausb0 192.168.2.40
next type sudo ifconfig "your device place" (in my system is rausb0) " your IP address" netmask "your netmask address"
example: sudo ifconfig rausb0 192.168.2.40 netmask 255.255.255.0
next type sudo route add default gw "your gateway address"
example: sudo route add default gw 192.168.2.1
then type sudo echo "nameserver (your primer DNS address) search (your prefered DNS address)"
example: sudo echo "nameserver xxx.xxx.xxx.xxx search xxx.xxx.xxx.xxx"
then try to ping a website, type ping [www.yahoo.com](www.yahoo.com) for example, you can start to ping your gateway address too. and you can see wether it made it or not.
after that you can configure your network setting, click system --> networking, and fill again the setting like you do above, then activate the setting, I hope this can help you, best regard and keep Ubuntu with Us

---

