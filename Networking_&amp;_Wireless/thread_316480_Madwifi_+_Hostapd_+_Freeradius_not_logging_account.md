---
title: "Madwifi + Hostapd + Freeradius not logging accounting traffic"
date: 2006-12-10
forum: Networking &amp; Wireless
---

### Post by slaterm61 on 2006-12-10
Hi,
I recently follows the instructions provided by phoboulinos
in another thread, and got my ubuntu 6.10 server working as a wireless access point with Radius authentication.

The authentication is working well enough, but it does not seem to be logging any traffic in the radius stop packet.

The MySql logs the queries, and the AcctInputOctets and AcctOutp
utOctets fields are empty.

The radius detail file, does not even include those attributes.

Is this an issue with the madwifi driver, hostapd or something in my config which i can post later if needed.

regards,
Michael

---

