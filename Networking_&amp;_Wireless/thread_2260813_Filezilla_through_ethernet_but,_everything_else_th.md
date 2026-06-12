---
title: "Filezilla through ethernet but, everything else through wifi?"
date: 2015-01-14
forum: Networking &amp; Wireless
---

### Post by mamamia88 on 2015-01-14
I would like to set my computer up to run file transfers in filezilla to go through an ethernet cable but, I would like to have all my internet activity go through my wireless interface.  Is this possible to do?

---

### Post by TheFu on 2015-01-14
Yes, but it probably isn't worth the hassle and complexity.  

Stock networking likes to use subnets/netmasks to determine routing. You want to use something other than that - which means non-standard networking.  

Using iptables with the -userid option and running one of the programs under a different uid, you can force that you want. Others here have, however, I have not.  -m owner --uid-owner are the options to look into.

Good luck.

---

