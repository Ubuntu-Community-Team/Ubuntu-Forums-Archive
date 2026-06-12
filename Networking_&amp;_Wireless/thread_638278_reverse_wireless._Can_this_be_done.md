---
title: "reverse wireless. Can this be done?"
date: 2007-12-11
forum: Networking &amp; Wireless
---

### Post by bobosity on 2007-12-11
I'm tired of playing with ndiswrapper. However, I do have three wireless routers. Can this work:

Cable comes from wall to cable modem. Wire goes from there to wireless router #1. Main computer runs wire to the router. Router #2 sits elsewhere and receives wirelessly from R1.
Another system runs wire to R2 and treats it like a standard ethernet connection. No ndiswrapper.

Is this possible?

Thanks....

---

### Post by Whiffle on 2007-12-11
Yup:

[http://www.dd-wrt.com/wiki/index.php/Wireless_Bridge](http://www.dd-wrt.com/wiki/index.php/Wireless_Bridge)

---

### Post by kevdog on 2007-12-11
Im doing that right now but Computer #2 for me is wireless.  Im running in Repeater Bridge mode.  If you dont need wireless on the router #2, then you can use simply client bridge mode.  With dd-wrt many things are possible.

---

### Post by SoloSalsa on 2007-12-11
*maybe*
Most 'cheap' routers (most anything sold in Best Buy, Circuit City, etcetera for the mainstream home users) will not do this.  They sell things called 'bridge's or such to do this...  The truth is, if the device has jacks and an antenna, then it is capable of doing this.  However, the manufacturers restrict functionality from the firmware.  You might want to try putting Linux on your router!  OpenWrt is a project that supplies alternate firmware for routers, with *much* more functionality that the manufacturers give the consumers.  Do note, that running alternate software on your router is against warranty!  If you want to give it a try, see if one of your models is capable here.
[http://wiki.openwrt.org/TableOfHardware](http://wiki.openwrt.org/TableOfHardware)

---

