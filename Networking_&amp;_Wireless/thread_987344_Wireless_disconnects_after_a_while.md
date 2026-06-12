---
title: "Wireless disconnects after a while"
date: 2008-11-19
forum: Networking &amp; Wireless
---

### Post by SpriteSODA on 2008-11-19
Hi guys,
I have a wireless USB adapter - Wistron NeWeb DRUC-U3 .
I managed to install it using Ndiswrapper and a driver disk I had.
When I log in to the system, it manages to connect and I can browse the web, but after a few minutes it looses the connection and fails to log in back again, prompting for WEP password that i fill in but no use, fails to connect. sometimes when it happends i cant get an output from iwconfig at all, and sometimes it just freezes the whole system. The only way to regain connection is to reboot the PC.

when i typed ndiswrapper -l it writes that there is an alternate driver p54usb, so i looked for all his aliases and added them all to the blacklist, didn't help. in lshw -C Network it says the driver is: "ndiswrapper+prisma02" .

I thought that maybe the driver isn't that great, and tried looking for another one, maybe more up-to-date, but after scanning google for hours i failed to find one.

I hope you guys can help me :)

P.S: my distro is Ubuntu 8.10

ty.

---

### Post by SpriteSODA on 2008-11-20
tried installing Wicd, no help there.

---

### Post by lifestream on 2008-11-20
Hey, I heard you on the IRC.
Giving you a little bump here, and wondering if you've read:
[http://ph.ubuntuforums.com/showthread.php?t=891555](http://ph.ubuntuforums.com/showthread.php?t=891555)
It doesn't really offer a solution, BUT there's a bunch of tips that might help you:

* compile driver from scratch,
* tell us which version of ndiswrapper you're using
* If the wireless works depending if it's unsecured, wpa, wep, etc.

I used to have this same problem, but on Windows, with a wireless card too. That, and I had a piece of c*** router.

Just a few things that might help us help you :D Also try bumping that other thread, with your information. It hasn't been updated in a week.

Best of luck

---

### Post by SpriteSODA on 2008-11-20
ty for the reply.
I tired Ndiswrapper 1.52 and 1.53, both i've compiled from it's files :(

im thinking maybe my drivers for the device aren't that good, but I simply CANT find any other, except in a website DriverGuide.com but I can't download from there.

---

