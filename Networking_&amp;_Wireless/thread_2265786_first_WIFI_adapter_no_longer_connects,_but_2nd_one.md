---
title: "first WIFI adapter no longer connects, but 2nd one is ok"
date: 2015-02-17
forum: Networking &amp; Wireless
---

### Post by chihwah_li on 2015-02-17
With Ubuntu 14.04, with latest updates.
I compiled and installed the driver for the AE6000 Linksys WIFI adapter (AC580). 
[http://hprath.com/2014/06/cisco-linksys-ae6000-ac580-media-tek-mt7610u-mt7630u-mt7650u-linux-x64-driver-patch/](http://hprath.com/2014/06/cisco-linksys-ae6000-ac580-media-tek-mt7610u-mt7630u-mt7650u-linux-x64-driver-patch/)
It was working perfectly.  Then I pulled it out and tried the WUSB600N Linksys.
The WUSB600N also works. But now I got a problem with the AE6000.

with $ iwconfig I can see it being identied correctly, but it cannot connect to my WIFI router.
Before installing the WUSB600N version 2, the AE6000 was working perfectly.

AE6000 is known as the  device name Ra0
WUSB600N is identified as wlan0

Now only wlan0 is working if I connect it, ra0 refuses to connect to my WIFI router.
What could can I do to solve this?

---

