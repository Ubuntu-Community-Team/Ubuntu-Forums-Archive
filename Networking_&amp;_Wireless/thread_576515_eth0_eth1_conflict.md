---
title: "eth0 eth1 conflict"
date: 2007-10-15
forum: Networking &amp; Wireless
---

### Post by infinitezero on 2007-10-15
I have two Ethernet cards on my system, eth0 and eth1. I have eth0 connected to a router for my LAN and eth1 connected to a cable modem with a static IP. If anyone on the LAN access my computer (via eth0, samba) then nobody can access my ftp server or wiki page via eth1. Do I need to make the samba eth1 instead of eth0?


Thanks,
iz

---

### Post by infinitezero on 2007-10-15
Do I need to install a NAT server?

iz

---

### Post by milton1 on 2007-10-15
not sure what the issue is here, but you could try connecting your router to the cable modem, then forward necessary ports to your ftp server. This at least would help determine if the conflict is with eth0/eth1, or somewhere else on your system.

---

