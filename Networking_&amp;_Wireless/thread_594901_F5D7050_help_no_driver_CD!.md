---
title: "F5D7050 help: no driver CD!"
date: 2007-10-28
forum: Networking &amp; Wireless
---

### Post by ramcosca on 2007-10-28
Stupid title, I know... but that's about what's happening to me right now.

I've gotten my dad's computer up and running Kubuntu 7.04.  Everything except the WiFi (and I'm pretty sure the 3D capabilities of his video card, but whatever, he doesn't need those) has worked.  His computer has a Belkin F5D7050 ver 1000.

I've looked through this forum on a how-to but it all says we need the driver CD... which we don't have.  This USB stick was a gift from my sister, she gave him only the adapter and nothing else.  It worked on XP because we found the driver online but on Kubuntu... well.. you get the point.

Any help gladly appreciated.

PS: I've already got the Easy-Peasy Wireless tutorial page and many threads here bookmarked. All I need is help on how to get rt2500usb.inf which is, apparently, all I really need.


Addendum: Disregard this vvvvvvv I have to edit all of that. ;)

---

### Post by evilregis on 2007-10-28
[http://www.belkin.com/support/download.asp?download=F5D7050&lang=1&mode](http://www.belkin.com/support/download.asp?download=F5D7050&lang=1&mode)

Sounds like you just need that.  Download the drivers, unpack them if necessary and point ndiswrapper to the .inf file.

---

### Post by ramcosca on 2007-10-28
The only .inf file I see there is the autorun.inf! :(

That's not the one the tutorials point me to.

---

### Post by evilregis on 2007-10-28
Is that the driver you downloaded for XP?  Is it a self-extracting exe or an actual executable?

---

### Post by ramcosca on 2007-10-28
It's for XP, apparently the self-extracting one. I changed the .exe to .zip and opened, the only .inf there was the autorun.inf

---

