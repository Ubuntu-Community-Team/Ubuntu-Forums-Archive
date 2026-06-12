---
title: "Missing nm-applet packing in Gutsy"
date: 2007-08-22
forum: Networking &amp; Wireless
---

### Post by n8bounds on 2007-08-22
Hi guys.  I've been using gutsy because its easier than manually installing newer drivers (which I apparently need) in Feisty.  Anyway, I've installed network-manager-pptp like I always have and tried to connect to the pptp server at work.  The nm-vpn-properties program wasn't installed.  I see no way to install it.  I installed everything in the repos that starts with network-manager*.  KVPNC works fine, but is ugly in my gnome desktop and does not integrate with my network-manager icon in my systray.  Any hints?

---

### Post by htor on 2008-01-10
I have the same problem with this package.

---

### Post by n8bounds on 2008-01-10
Crap, I fixed it and I forgot how...

---

### Post by zero-9376 on 2008-01-10
maybe a reinstall? go to synaptic search for network manager and mark all packages for reinstall

---

### Post by htor on 2008-01-14
It solves all:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/107070](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/107070)

---

### Post by Milkensen on 2008-01-14
If you are unable to add a valid nm-applet when adding (you knoww... right click...) an applet called "notification area", then go for the following (it will take you just 2 minutes):

Create a new systray. Add to it everything you had in the current systray.. building a new complete one. 
The trick: add an applet called "notification area". There should appear the nm-applet on it.
Delete the old systray. 
That's all!

---

