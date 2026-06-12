---
title: "Incompatibilities between NetworkManager and avahi-daemon?"
date: 2007-08-18
forum: Networking &amp; Wireless
---

### Post by IceCap on 2007-08-18
I have a Dell Latitude 840C with TrueMobile 1450 (Broadcom) running Feisty.  To get it running I installed ndiswrapper according to the instructions here.
  The card seems to be working but what I believe I have is a problem between NetworkManager and the avahi-deaemon as described in several places:

[https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/131822]("https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/131822")
[https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/82287]("https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/82287")

  Network Tools shows eth1 as the device for the 1450 card but not connection.  It shows eth1:avahi as a device interacting with the card and running it at 54Mbps when I set it up with my wireless network.  It sees the network (and my neighbors unsecure network) but it looks like NetworkManager isn't able to control it correctly.

  Does anyone know if this is a known issue and how to get around it?  I tried the remedies listed in one of the links above but it didn't work.

  The next thing to try is to install the drivers that don't utilize ndiswrapper but I have a feeling that they will only run my card at 11Mbps.

  Thanks
  IC

---

### Post by moore.bryan on 2007-08-18
*you could try using [wicd]("http://wicd.sourceforge.net/") instead.  i don't know if it will solve your specific problem, but it has fixed things on my system (thinkpad z61e) and many others...*

---

