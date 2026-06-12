---
title: "SOLVED: Network Manager overwrites resolv.com"
date: 2008-09-28
forum: Networking &amp; Wireless
---

### Post by mvn on 2008-09-28
The solution posted at [http://ubuntuforums.org/showthread.php?t=581029](http://ubuntuforums.org/showthread.php?t=581029) DOES work but there MUST be a ; at the end of the prepend line!  Without it no errors are generated but it is ignored by dhclient.

prepend domain-name-servers ip.address.of.your.server;

M

---

