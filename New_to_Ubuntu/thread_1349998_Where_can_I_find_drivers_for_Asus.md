---
title: "Where can I find drivers for Asus?"
date: 2009-12-08
forum: New to Ubuntu
---

### Post by arnicainthemembrane on 2009-12-08
My Asus Eeepc 1005HA has the following:

01:00.0 Ethernet controller: Attansic Technology Corp. Device 1062 (rev c0)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network

...but no internet with Ubuntu 9.10. Works fine with WinXP.

Where can I find the right drivers?

---

### Post by Temposs on 2009-12-08
If you go to System->Administration->Hardware Drivers, are there any drivers for your network card listed?

---

### Post by mikewhatever on 2009-12-08
Are you saying neither ethernet nor wireless work? I don't think Asus provides drivers for Ubuntu, or does it?

---

### Post by sgosnell on 2009-12-09
You shouldn't need any drivers.  Networking should work on the EEE, the drivers are in the kernel.  That said, Karmic doesn't work for me on my 900, for a wide variety of reasons.  Jaunty, OTOH, works OOTB, and with the 2.6.30 kernel, it works very well.

---

### Post by Scunnered on 2009-12-09
I have an Asus X51L and my wireless connection works straight out of the box.  All that was necessary was to click on the Wireless network connection and select the available network from the list offered.

I would imagine that you have the same wireless card as I.  Hope this assists

---

### Post by ukripper on 2009-12-09
for wireless follow this:
 Administration --> Software Sources --> Updates and check/enable &#8220;Unsupported Updates (karmic-backports)&#8221;.

Then then in terminal type this:
```
sudo apt-get update && sudo apt-get install linux-backports-modules-karmic
``` this will install required modules for you.

Just reboot and it should be working.

---

