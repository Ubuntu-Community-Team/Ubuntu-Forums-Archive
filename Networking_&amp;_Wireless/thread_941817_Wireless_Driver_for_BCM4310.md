---
title: "Wireless Driver for BCM4310 ?"
date: 2008-10-08
forum: Networking &amp; Wireless
---

### Post by vijyendra on 2008-10-08
Hello,
I have been trying very hard to start my wireless connection in past 2 days.

Is it possible at all to start it?
My Network card is Broadcom"s  BCM4310
DEll Wireless 1370 miniCard
My System is Dell Studio 1535.

Please help..i have read a lot in other forums...but yet not successful... so a specific help would be fantastic

Keenly waiting for help
[email]stealth.vijay@gmail.com[/email]
Thanks

---

### Post by Ayuthia on 2008-10-08
Have you already gone into System->Administration->Hardware Drivers and enabled the wl driver?  You will also need to make sure that the Broadcom b43 driver is not enabled.

If you have done that and you have a working wired connection, you can get your system up to date and your wireless should start working.  The other option is to reinstall using the 8.04.1 version.  

If you don't want to try those steps, you can try the ndiswrapper route.  Here is a link to a guide that should help:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

