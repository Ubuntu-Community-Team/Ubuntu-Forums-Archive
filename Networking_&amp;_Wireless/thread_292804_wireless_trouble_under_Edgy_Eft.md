---
title: "wireless trouble under Edgy Eft"
date: 2006-11-04
forum: Networking &amp; Wireless
---

### Post by rusyear04 on 2006-11-04
hi there...

i just installed ubuntu (edgy eft) onto my laptop (hp pavillion dv1000) it has an integrated
Intel Corporation PRO/Wireless 2200 BG -device.

but i have no clue why it's not working...](*,) 

since i'm pretty new to linux, all i know is that:
*) in the list of supported cards this device IS listed (although for earlier ubuntu versions)
*) the WLAN-LED on the laptop is turned off and does not start after pressing the "WLAN-quick-launch" button. other quicklaunch-buttons do work partially (volume & music-program)
*) my wireless-router is set to wpa -if that helps you.


thanx in advace.

ps: it's the first time i put linux on my notebook, so i have no clue how it would have/has behaved under older OS.

---

### Post by jpeddicord on 2006-11-04
Right-click the panel, and select Add to Panel. Double-click Network Monitor in the list. Watch that icon for a few minutes; if you start to see a little red X randomly appear, then it may be related to this bug:

[https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/66176](https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/66176)

If it is, add a comment to the bug with your card specifications. This will send an email to the bug team, which should hopefully get it some attention.

Wireless support in Edgy is very poor compared to Dapper, and that is why I don't use Edgy at the moment.

Jacob

---

### Post by rusyear04 on 2006-11-06
don't really get it...

it's working now, but i have no clue why :cool:

i tried quite a few things with ifdown and ifup but none worked. then i moved the laptop to another place, turned it on and it found quite a few WiFis around PLUS i was able to add my own (hidden) net...

no clue why how.

anyhow, thanx for your help! :KS

---

### Post by grim4593 on 2006-11-08
I have an integrated Intel Corporation PRO/Wireless 2200 BG and it worked fine after updating dapper to edgy.
*shrugs*

---

### Post by Sakaishi on 2006-11-10
I have the same dv1000 laptop.  My wireless worked fine under dapper but it doesn't in edgy.  I'm trying to connect to a WEP protected network.  What did you do to get yours to work?  I'm pulling my hair out over here.:evil:

---

### Post by rusyear04 on 2006-11-17
i did nothing...

but when it started to work the laptop was in a place where there are several WLANs around...
and it kicked off.

my own LAN was hidden (no broadcast) plus encrypted... WPA. but when i said "connect to other network" i was promted to enter name, key and all that stuff and it worked without any trouble.

tomorrow i will be at home-home again and we'll see wether it has difficulties finding my parents WLAN (which it did have in first place).

---

