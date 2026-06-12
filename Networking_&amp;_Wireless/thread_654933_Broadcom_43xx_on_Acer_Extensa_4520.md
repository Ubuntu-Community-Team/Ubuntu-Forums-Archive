---
title: "Broadcom 43xx on Acer Extensa 4520"
date: 2007-12-31
forum: Networking &amp; Wireless
---

### Post by wvdavis on 2007-12-31
New installation with Gutsy Gibbon. I have tried the HOW TO Sticky for Broadcom. It lead me to ndiswrapper and did not work. The Restricted Device Manager seems to have installed the driver successfully. I can see it in Network Manager. I suspect the problem may be a PCI bridge. When I boot up there are 2 error messages related to PCI bridges 7 and 8?

---

### Post by csat on 2008-01-01
Hello and happy new year.

Try this tutorial [->HERE<-](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29)

---

### Post by wvdavis on 2008-01-04
Smooth sailing so far.

I've installed the driver successfully but I need to edit the /etc/iftab file. Except I don't have one. It must be called something else in Gutsy Gibbon or doesn't exit yet?

---

### Post by wvdavis on 2008-01-12
This tutorial failed too but a similar one worked.

I ran my device listing through the Debian device identifier. It identified my wireless card as a Broadcom 43xx - which I already knew. But it also said my card was a Dell 1390 wireless. So I tried this fix using ndiswrapper with the Dell driver: [http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)
Works just fine though I haven't gotten WPA or even WEP to work.

---

### Post by csat on 2008-01-13
> **wvdavis said:**
> This tutorial failed too but a similar one worked.

I ran my device listing through the Debian device identifier. It identified my wireless card as a Broadcom 43xx - which I already knew. But it also said my card was a Dell 1390 wireless. So I tried this fix using ndiswrapper with the Dell driver: [http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)
Works just fine though I haven't gotten WPA or even WEP to work.

Great.  In fact this tutorial is better thatn the Wiki page.  So now it is a good idea to tag title with SOLVED word.
Check thread tools at top message screen for this.

Good luck.

---

