---
title: "Acer 3680 wireless won't work"
date: 2008-10-16
forum: Networking &amp; Wireless
---

### Post by mrtickles on 2008-10-16
I finally took the plunge after years of back and forth hemming and hawing and went open source and just put ubuntu on my Acer Aspire 3680.  One problem ... I cant get the wireless connection to work.  Any suggestions / help would be greatly appreciated!

---

### Post by Ayuthia on 2008-10-16
Can you go into the Terminal and post the results of lspci -nn?  We need some help in identifying your wireless card.  Thanks!

---

### Post by mrtickles on 2008-10-16
Not sure if this is what you need.

**BCM94311mcg wlan mini-pci (rev 01)**

Have been out of the loop for awhile so am kinda re-learning/learning alot

---

### Post by Ayuthia on 2008-10-16
If you have a wired connection, you can get the system up to date and then go to System->Administration->Hardware Drivers and select either Broadcom options.  The STA is the proprietary driver made my Broadcom and the other one is the open source b43 driver (but needs some info from proprietary firmware to make it work).  Either option will work.

If you don't have a wired connection, you can try this link:
[http://ubuntuforums.org/showthread.php?t=779754](http://ubuntuforums.org/showthread.php?t=779754)
In Option 2, there is some information about how to download the files you need so that you can install it in Ubuntu without an internet connection.

Hope that helps.

---

### Post by mrtickles on 2008-10-16
Thanks tons ... will give it a shot!!

---

