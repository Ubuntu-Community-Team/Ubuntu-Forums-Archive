---
title: "wireless adapter keeps droping connection on edgy"
date: 2007-02-06
forum: Networking &amp; Wireless
---

### Post by xpan on 2007-02-06
Hi,

On my second machine (desktop) I am using an Asus USB 2.0 WLan Adapter (WL-1676) which was properly recognized by ubuntu edgy eft.

Up to now, I have managed to create a small home (samba) network sharing folders on both machines.

However, *sometimes* when I am trying to transfer files from my laptop to a shared folder on my desktop, the desktop seems to drop its wireless connection unexpectedly. 

Any ideas why this is happening?

PS: it doesn't happen every time, but when it happens the only way to make it work again is by restarting the machine

---

### Post by ukripper on 2007-02-09
well perhaps next time when it drops you can try following commands in the terminal if you are using ndiswrapper.

$ sudo depmod -a
$ sudo modprobe ndiswrapper

$ sudo ifdown eth1  
$ sudo ifup eth1

or if your wireless is on wlan0:
$ sudo ifdown wlan0
$ sudo ifup wlan0

I know it won't resolve your ongoing problem but atleast would save you a reboot. Just a suggestion.

---

