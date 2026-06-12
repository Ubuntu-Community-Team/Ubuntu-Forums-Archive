---
title: "Disable ndiswrapper"
date: 2014-10-14
forum: Networking &amp; Wireless
---

### Post by pooldemon6000 on 2014-10-14
I just read to get my tl-wdn4800 working properly with ath9k module, I need to pass nohwcrypt=1.

is there a way to disable ndiswrapper without un installing it just in case my issue of only being able to ping in terminal and not Internet connection otherwise returns?

I've tried blacklisting ndiswrapper and allowing ath9k to be loaded, rebooted and nada.

maybe I missed a step?

Edit:
had to update initramfs

ath9k still had the same issue, should I just get the one from wirelessdrivers.com or whatever the site is and build it myself?

---

