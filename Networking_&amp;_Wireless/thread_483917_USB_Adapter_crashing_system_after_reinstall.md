---
title: "USB Adapter crashing system after reinstall"
date: 2007-06-25
forum: Networking &amp; Wireless
---

### Post by Pat Mustard on 2007-06-25
Hi

I recently installed Feisty, got it working, added a Belkin USB Wirelesss adapter, eventually got it working.

Reinstalled feisty from scratch, now whenever I plug in the USB Wirelesss adapter the system freezes up.

I am hugely confused, what could have changed that could have affected this?

Thanks

---

### Post by Pat Mustard on 2007-06-26
Aha!  I have it figured out.

I am using a Belkin wireless-G USB adapter F5D7050, not sure of the version off hand.
I previously had it working using the serialmonkey rt73 replacement driver.

I finally got it working on the fresh install last night.  
From reading the forums I got the impression that it might be caused by "bad" drivers trying to operate the device.  
So I first removed and blacklisted all the drivers that serialmonkey covers, completed the rt73 setup and eventually coaxed it into working.

I'm glad it all works but I can't quite figure out why this didn't happen before?

:popcorn:

---

