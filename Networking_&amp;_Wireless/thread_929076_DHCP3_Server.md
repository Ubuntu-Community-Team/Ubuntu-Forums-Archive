---
title: "DHCP3 Server"
date: 2008-09-24
forum: Networking &amp; Wireless
---

### Post by MightyMartian on 2008-09-24
I've got a quick question about the DHCP3 server.  I'm building a firewall/NAT router box that is getting its outside address from the ISP via DHCP, but the private address space (192.168.0.x/24) is static, with a range to be provided by DHCP3 server.

How do I tell the DHCP server to only work on the internal network card (in this case eth1)?

---

### Post by Iowan on 2008-09-24
**/etc/init.d/dhcp3-server** references the variable $INTERFACES. 
Edit the value in **/etc/default/dhcp3-server**.

---

