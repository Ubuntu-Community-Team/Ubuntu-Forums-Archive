---
title: "Dell Inspiron 1525 wireless problem!!!!!!"
date: 2008-10-21
forum: Networking &amp; Wireless
---

### Post by cksonline on 2008-10-21
Hi all

I recently purchased DELL 1525 N series having Dell Wireless 1395 WLAN Mini-Card. I am not sure if the ubuntu support my hardware or not. Plz can any body help me i have also gown through dell support in Ubuntu form but all in vain....

Br
cksonline

---

### Post by Ayuthia on 2008-10-21
It should work in Intrepid but for Hardy, the driver is available in 8.04.1 but not in 8.04.  The driver was introduced in 2.6.24-17 but it seems to work in 2.6.24-19 (Which I think is in 8.04.1) and some improvements were made in 2.6.24-21 (the most current Hardy kernel).

You should only have to go to System->Administration->Hardware Drivers to activate the wl/Broadcom STA driver.

Hope that helps.

---

