---
title: "WPA suddenly not working on Belkin router"
date: 2007-06-26
forum: Networking &amp; Wireless
---

### Post by IB_IG on 2007-06-26
I am using 7.04 and I have been able to use the wireless networking normally with WPA for several weeks.  I am using a Belkin wireless-G router.  Starting a few days ago, whenever I connect to the wireless network, it fails to connect when I give it the WPA key.  The WPA key on the router has not changed, and other computers are able to connect to it normally.  It also works if I connect the computer to the router with a wire.  Anyone have any ideas?

---

### Post by spd106 on 2007-06-26
It's probably a good idea to check the /var/log/syslog for error messages. You should be able to follow the association and authentication process done by Network Manager as it sets up the connection. Then you will probably see where the process fails.

Good luck

---

