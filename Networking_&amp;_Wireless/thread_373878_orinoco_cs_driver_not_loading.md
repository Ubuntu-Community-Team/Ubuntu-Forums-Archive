---
title: "orinoco_cs driver not loading"
date: 2007-03-01
forum: Networking &amp; Wireless
---

### Post by acidblue on 2007-03-01
Using Dapper 6.06 with a Lucent Orinoc silver card.
Woks in Mepis but not in Ubuntu.
iwconfig gives "Hermes I" which of course is not the right chipset driver.
I need to load the 'orinoco_cs' driver for my card, not sure if 6.06 has this
driver.
Do i need to download it?
If I need to download it how do I get Dapper to use it?

---

### Post by chili555 on 2007-03-01
It's included in Dapper and may already be loaded. Check sudo lsmod and see if you see orinoco_cs and hostap. Post back and we'll get you going.

---

### Post by acidblue on 2007-03-04
Thanks I got it working.
Had to clear old AP info in 'Networking'
It was trying to connect to old AP not in range anymore.
New AP info was updated almost instantly.

---

