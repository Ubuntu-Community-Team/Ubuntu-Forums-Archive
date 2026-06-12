---
title: "Amilo A1650g WLan Problem"
date: 2014-04-06
forum: Networking &amp; Wireless
---

### Post by sabine123 on 2014-04-06
Hello all!
Im new here and a new User from Lubuntu. I'd googling the hole internet and nothing helped me with my problem so i hope u can help me.
The Led light is on at my laptop but theres nothing to connect. I have the Amilo A1650g Laptop.

I hope this help:

> sabine@sabine-AMILO-A1650G:~$ lspci -nn | grep Network 
02:05.0 Network controller [SUP][[280]]("http://forum.ubuntuusers.de/topic/keine-funknetzwerke-wlan-lampe-leuchtet-am-lap/#source-280")[/SUP]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02) 

sabine@sabine-AMILO-A1650G:~$ iwconfig 

lo        no wireless extensions.
eth0      no wireless extensions.



Sry for bad English :P

---

### Post by chili555 on 2014-04-06
Did you check the sticky at the top?

---

