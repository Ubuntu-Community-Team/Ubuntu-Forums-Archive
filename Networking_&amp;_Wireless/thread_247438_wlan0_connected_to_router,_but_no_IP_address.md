---
title: "wlan0 connected to router, but no IP address"
date: 2006-08-30
forum: Networking &amp; Wireless
---

### Post by scottb1062 on 2006-08-30
I have an Acer C100 with kubuntu 6.06 and a Linksys WRT54G router.  I have tried both the internal wireless card and a PCMCIA DLink adapter.  Both appear to be found by kubuntu.  when I run Wireless Assistant, my router is listed, but when I click on it, I get "connection failed".  I have put in the WEP key and tried both "Open System" and "Shared Key" (I don't know which to pick).

iwconfig shows my ESSID, so it appears to be finding the router, and it is picking up the right channel for the router.  However, I am not getting an IP address.  iwconfig says "Encryption key:off", so I wonder if that is relevant.

Any ideas what to try next?

---

### Post by NetworkGuy on 2006-08-30
Exactly what type of D-Link adapter do you have?

---

### Post by scottb1062 on 2006-08-30
DWL-650.

More info:
I was wrong when I said the internal wireless is detected; it is not.  The DWL-650 is detected.  when I boot up, iwconfig does not show the ESSID.  once I run the Wireless Assitant and click on the ESSID (and the connection fails), and I get a Link light on the DWL-650.  Now I get the ESSID in iwconfig.

---

### Post by NetworkGuy on 2006-08-30
I'm going to have to sit back and watch this on.  According to the WiFi documentation on the Wiki, this driver should work without any problems.  

Sorry

---

### Post by smoking81 on 2006-09-09
hi!
I have the same problem: wireless found/connection fails. The card is intel bg2200..
How did you solve?
Thanks!

---

