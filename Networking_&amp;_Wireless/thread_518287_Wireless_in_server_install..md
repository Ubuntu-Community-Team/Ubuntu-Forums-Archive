---
title: "Wireless in server install."
date: 2007-08-05
forum: Networking &amp; Wireless
---

### Post by sythem on 2007-08-05
So I recently got an old laptop with a broken ethernet port and a dlink 630 rev c wireless card. My annoyance is that during the install, the wireless was configured and established a working connection. But now that the installs done, it doesn't even list my wireless card during iwconfig. Just lo and eth0. It can't have an inet connection so is there some way of getting it to work from the packages on the cd?

---

### Post by ugm6hr on 2007-08-05
I think you need to activate the Atheros HAL for the madwifi restricted drivers.  I'm not sure how to do that from the server install (presumably you have no GUI).

Assuming your card is actually this one: [http://madwifi.org/wiki/Compatibility/D-Link#DWL-G630](http://madwifi.org/wiki/Compatibility/D-Link#DWL-G630)

---

### Post by sythem on 2007-08-05
Well nvm b/c I got the eth0 working by proping the cable up so it's working for the moment and I have a madwifi howto.

---

