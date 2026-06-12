---
title: "DLink DWL-G650+ (acx111) not working after textinstall"
date: 2006-11-11
forum: Networking &amp; Wireless
---

### Post by deelite on 2006-11-11
hi,

in 1 of my notebooks i installed ubuntu 6.10 from the live-cd. the wifi-card DLink DWL-G650+ (acx111) works very well.

my other notebook has only 192mb of ram. the live-cd works (the wifi-card too) but the installation from this cd hangs up after some minutes. so i used the alternate install-cd and did the install in text-mode.

and now my problem: ubuntu works very well after text-install. but my wifi card NOT. i can see it in the device-manager and it seems to be correctly recognized. but it is not working (no led) and i can see no wireless network connection like on my other notekook or with the live-cd.

how can i get a working wifi-card after textinstall? or how can i install ubuntu with live-cd and only 192mb ram?

thank you very much for your help.

---

### Post by FrodoB on 2006-11-12
Look at:

[http://www.ubuntuforums.org/showthread.php?t=296507](http://www.ubuntuforums.org/showthread.php?t=296507)

He explains how to get a firmware loaded.

Looks promising, there are a lot of firmwares already in Edgy. Look in:

/lib/firmware/2.6.17-10-generic/acx

to see them all and there is are readme.txt file.

---

