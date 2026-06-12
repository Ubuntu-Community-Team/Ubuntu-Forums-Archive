---
title: "WG111v2 problem, setting up wireless network"
date: 2006-12-23
forum: Networking &amp; Wireless
---

### Post by malfist on 2006-12-23
I recieved a wireless router (linksystems) and a WG111v2 (netgear) for christmas. I've tried setting them up but I fail. The wired connections work with both the windows in this computer (Ubuntu 6.10). I've googled how to set up the connection and it isn't working. I've tried using the ndiswrapper and setting it up that way. When I go into networking under admin tasks I can activate the wan0 (which is the WG111v2). It takes forever to activate it and then to close the thing too after I've activated it. Then when I try to go somewhere on the internet Firefox gives me the error message that is the same as when I forget to plug in the wired connection (I take it up when I'm not home (not only my house)). Any suggestions?

---

### Post by kvonb on 2007-01-02
Plug the usb dongle in then open a terminal (Menu->Applications->Accessories->Terminal) and type this in:

lsusb | grep NetGear

If you get this:

ID 0846:4240 NetGear, Inc. WG111 WiFi (v2)

It is actually a version 1, NOT version 2!


I have these modules and I'm trying to sort it out right now, I'll let you know if I get it working.  Alternatively search these forums for:

```
0846:4240
```It will spit out any related threads, let me know if you get it working before me please :)

EDIT:

I got mine working using this guide here:

[http://ubuntuforums.org/showthread.php?t=329299](http://ubuntuforums.org/showthread.php?t=329299)

---

