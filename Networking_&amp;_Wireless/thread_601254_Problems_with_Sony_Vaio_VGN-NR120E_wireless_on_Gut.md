---
title: "Problems with Sony Vaio VGN-NR120E wireless on Gutsy upgrade"
date: 2007-11-03
forum: Networking &amp; Wireless
---

### Post by thunderbunny on 2007-11-03
So, I upgraded to Gutsy Gibbon through Update Manager tonight, and my wireless (Atheros AR5007EG, erroneously reported by lspci as 5006), while working in some semi-reasonable capacity before, now appears to be totally hosed. I reinstalled ndiswrapper and the WinXP drivers for the device, but when I run wicd no wireless networks show up. Everything from iwconfig, ifconfig, lspci looks okay to me (except for the non-associated access point showing up in iwconfig).

One thing I noticed is that the middle light on the bottom right of my laptop, which I THINK is wireless, is no longer blinking. Do I need some kind of special ACPI package for Sony Vaio in Gutsy? Or what else could I be doing wrong? I'd really appreciate anyone's help!

---

### Post by thunderbunny on 2007-11-03
Uh, never mind, the problem seems to have fixed itself. Okay, not exactly; I cleaned out /etc/modprobe/ndiswrapper, uninstalled and recompiled my version of ndiswrapper, then uninstalled and reinstalled the net5211.inf file. Then restarted, and was shocked to find that I had a wireless signal. The second LED on my laptop apparently doesn't do anything.

I would like to encourage anyone with a problem similar to mine to read the post at [http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828) since it's pretty much a comprehensive FAQ on these kinds of cards.

---

