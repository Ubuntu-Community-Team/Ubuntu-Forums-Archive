---
title: "[SOLVED] Networking blues"
date: 2007-10-16
forum: Networking &amp; Wireless
---

### Post by jcgrav on 2007-10-16
Hello all,

I am currently experiencing some network flaw. Previously the network operations were flawless, and without any changes in routine or hardware the Internet functions ceased to operate. I can still ping my router, I can telnet or log into the router but I am not able to get to the I-net.

Router Linksys, Eth0-Realtek (onboard)

---

### Post by helgman on 2007-10-16
Check default gateway settings (using *route*).

Make sure that your DNS-settings are correct (nameserver statements in */etc/resolv.conf*).

If you are writing your posts from behind the same router then make sure that the above settings are the same on both systems, else, make sure that the router has a connection to the Internet.

If you have any questions, just ask away.

Regards,
Helgman

---

