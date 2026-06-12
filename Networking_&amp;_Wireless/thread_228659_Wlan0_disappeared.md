---
title: "Wlan0 disappeared?"
date: 2006-08-03
forum: Networking &amp; Wireless
---

### Post by UberIcarus on 2006-08-03
My wifi card dissappeared for no particular reason after turning on my laptop. Every time I turn it on there's no wifi card.

However, if I run Ifconfig and iwconfig it'll pop back up, but as eth1 (which doesn't work), instead of wlan0 (which does work).

I've got a broadcom card, and I'm using ndiswrapper, anyone have any advice?

---

### Post by nicculus on 2006-08-03
After doing some updates today and rebooting my card using ndiswrapper changed from wlan0 to eth1 on its own.  It is still acting the same way not able to associate with ap (topic for another thread), but thought I would mention it.

---

