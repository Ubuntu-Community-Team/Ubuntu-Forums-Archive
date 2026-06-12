---
title: "shorewall vpn bridge"
date: 2008-03-23
forum: Networking &amp; Wireless
---

### Post by ubuntogenius on 2008-03-23
Im running Ubuntu 7.1 with Shorewall as a router/firewall for my home network.

 I have pptp client configured to connect to my office.  From the ubuntu desktop I can browse shares etc.
From other computers in the LAN I can't browse or ping anything on the office LAN.


I assume this is because shorewall is not configured to bridge the interfaces.  ppp0 and eth11(my LAN nic which hands out DHCP leases)

I am configureing shorewall via webmin.

thanks

---

### Post by farahbod on 2008-03-24
What do you install on office computer? (I mean which OS)

Did you setup proper routes on it?

---

