---
title: "modem close to working but no close enough"
date: 2006-11-01
forum: Networking &amp; Wireless
---

### Post by nesh87 on 2006-11-01
Hey guys, 
im new to linux i recently made the switch to ubuntu 6.10 from windows xp and planning to make it perminant. Ive installed my favorite software by downloading them from another pc and sending them to my HP Pavilion DV1000 using bluetooth. I tried many ways to get my modem to work but no success. Yesterday i installed "sl-modem-daemon_2.9.9d+e-pre2-7_i386.deb" and it seems to do the job. Now Gnome-ppp detects my modem in TTSys0 but everytime i dial i get no dial tone error.

I have attached a text document with the outputs of lspci, lspci -n and wvdial.conf

Also i attached an image showing Device Manager detecting my Modem and it was already detected before installing the sl-modem-daemon.

Appreciate any help!

---

### Post by _duncan_ on 2006-11-01
Hi. Most pci modems require 2 things to work: A modem driver + daemon. The hardest part actually is finding a suitable driver to match your specific modem.

I'm not familiar with intel modems, but the following link might give you an idea of the process:

[Dialup Modem How To]("https://help.ubuntu.com/community/DialupModemHowto")

If the above doesn't help you, another possibility is to look at the [www.linmodems.org](www.linmodems.org) website. It's an umbrella organization that helps potential linux users to get their internal software modems working.

good luck!

---

