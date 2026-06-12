---
title: "Broadcom 94306 - my driver in progress"
date: 2005-05-30
forum: Networking &amp; Wireless
---

### Post by CloudNine on 2005-05-30
Lo,

I've looked through the forum here and in the customisation forum, and found that many of you have had problems with the bcm94306 chipset (i.e. there's no linux driver for it). I'm working on a driver for this (and that includes reverse-engineering the NDIS driver), and at one point I was able to read the MAC address (before rewriting parts of it). The bcm94306 chipset is the one with the pci vendor id 14E4 and device id 4320 of course.

So this post is to make aware of what's happenning, and I guess also a call for help. I've only got one set-up at the moment, I can't possibly test everything (since wireless network cards are complicated beasts). The driver's being tested on a 2.4 kernel, so it's probably a simple thing to port it to 2.6. E-mail me at [EMAIL=mwhitworth@gmail.com]mwhitworth@gmail.com[/EMAIL] if you're willing to join in with a testing effort. I will post on the Linux Kernel Mailing List, when I've got something more substanial.

CloudNine

---

