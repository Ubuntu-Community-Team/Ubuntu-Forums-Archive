---
title: "USB Network Adapters"
date: 2006-11-12
forum: Networking &amp; Wireless
---

### Post by tigershark on 2006-11-12
Hi!
I have recently begin to use Ubuntu instead of winxp and now I'm going to buy a usb network adapter and wondering if you have any sugestions which one to buy.
Which one is compatible with ubuntu?

---

### Post by ajgreeny on 2006-11-12
Have a look at:-
[http://doc.gwos.org/index.php/Networkwifi](http://doc.gwos.org/index.php/Networkwifi)
This has a lot of info on wireless devices and its parent site has lots of hardware information you may find very useful.

---

### Post by FrodoB on 2006-11-12
I have several working USB wireless devices, but each of them requires compiling and installing the drivers.

Belkin F5D7050 ver 3000

Belkin F5D7050 ver 4000

Airlink101 AWLL3026

The Airlink101 AWLL3036 and the Belkin F5D7050 ver 4000 both use the Zydas zd1211b chipset. The are recognized in Edgy by the zd1211rw driver, but it is broken, so you have to get a driver that works from [http://zd1211.ath.cx/](http://zd1211.ath.cx/) and modify the makefile for the zd1211b version of the zd1211 family. The Belkin is the better constructed of the two, I think.

The Belkin F5D7050 ver 3000 requires the rt73 driver from Ralink's web site and you have to modify the rtmp_def.h file and add the device's USB ID to it.

So I don't have any easy suggestions, all require downloading software and building drivers.

If you are interested I would suggest building the drivers first and purchasing based upon which seemed easier. I can post instructions for any of them that you would like.

---

