---
title: "Issues with AirLink+ USB wireless stick (zd1211rw) in VMWare"
date: 2007-07-08
forum: Networking &amp; Wireless
---

### Post by turtlepowwa on 2007-07-08
Hi,
I have a clean install of Fiesty 7.04 as a guest OS in VMWare (WinXP host).

The device in question is an AirLink+ USB wireless stick that has a zd1211 chipset; and it seems that the zd1211rw driver (the one that comes with the latest version of ubuntu) *should* handle the device.

Now, begins the weirdness.  Whenever the wireless stick seems to be "busy", it seems like the OS 'trips', and locks up for half a second.  This results in the OS printing out multiple letters of keyboard input at the same time, in whatever window i'm in.  Also, occasionally, one letter will 'stick', and keep printing that letter for about 20-30 chars :confused:.  This of course renders typing... somewhat of a challenge. :)
I've checked dmesg and various other logs... things look mostly ok, although I'd be glad to post them if needed.

Is the problem with the device?  The driver?  Perhaps.. VMWare?!
If anyone else has experienced this problem before, or as any information related to it...

Thanks in advance 8-).

p.s: network connectivity works, although terribly sporadic.  Any tips/tricks on getting this usb stick to work better?

---

