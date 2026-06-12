---
title: "Dd-wrt"
date: 2008-07-04
forum: Networking &amp; Wireless
---

### Post by shortylonglegs on 2008-07-04
I have an old ZyXel router lying around here and wanted to try out this DD-WRT thing.  I've heard good things about it, but don't know where to start.  Their website didn't offer much information that I could find.  If someone could just point me in the right direction to get started that would be great.  It doesn't really need to be DD-WRT either, just something along those lines.  Thanks

---

### Post by kevdog on 2008-07-04
Here is the supported hardware list:
[http://www.dd-wrt.com/wiki/index.php/Supported_Devices](http://www.dd-wrt.com/wiki/index.php/Supported_Devices)

Another project is Open-wrt
[http://wiki.openwrt.org/TableOfHardware?action=show&redirect=toh#head-1666ce1afea860be958b872a1ac5fe3d2ec4c286](http://wiki.openwrt.org/TableOfHardware?action=show&redirect=toh#head-1666ce1afea860be958b872a1ac5fe3d2ec4c286)

Tomato is an older project also.
[http://www.polarcloud.com/firmware](http://www.polarcloud.com/firmware)

---

### Post by Zack McCool on 2008-07-04
Really, there's not much to getting started.  Check the supported hardware lists, and see if your router is supported, and with which versions.  Download the correct version for your device.  Update the firmware on the device using the .bin you just downloaded.  Log in to the new router and configure it.

I use dd-wrt on a Linksys wrt-54g v2, and it works great.  Far richer feature set than you get from the stock firmware...

---

### Post by shortylonglegs on 2008-07-04
How do I know which setup to use for my router?

---

### Post by Zack McCool on 2008-07-07
Look through the list, see which one is compatible.  They have 3 main versions, a full, mini and micro.  There are also other, specialty versions.

Some routers have memory limitations.  For instance, a Linksys wrt54g up to version 4 has at least 8 MB of memory for use, but v5 and 6 only have 2mb.  The older routers can use the full dd-wrt, but the newer ones need a mini version, with limited functionality.

What is the exact model of your router?

---

### Post by kevdog on 2008-07-07
Read the site carefully or you will brick your router (which you can recover from but its a pain).  I remember having to flash first with the micro version then went onto install the full version.  Just make sure to read the instructions on the dd-wrt website entirely before flashing your router.  I'm not trying to scare you, just save you a headache.

---

