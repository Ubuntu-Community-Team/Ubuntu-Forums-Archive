---
title: "Problem connecting to network printer with different private IP address scheme"
date: 2008-08-21
forum: Networking &amp; Wireless
---

### Post by Charlotte18 on 2008-08-21
I'm on a Windows 2003 network where the DCHP and domain controller are on a 172.16 scheme, and the printers are served from this 172.16 server. However, the printers' IP addresses are 192.168.x.x addresses even though they're served from the 172.16.x.x server. (The 172.16.x.x server has a nic assigned to a 192.168 address, so it adds those printers and serves them out to the 172.16 world.) In Windows XP desktops, this is no problem, and the 192.168 printers show up in the directory of 172.16 desktops because the 172.16 desktops are going through the 172.16 print server, which has the 192.168 printers added to it.

In Ubuntu 8.04, I'm joined to the domain with likewise. I get a 172.16 dhcp assignment. I'm using the HP Device manager, and from there can see and install the 192.168 printers. But I get a "connection error" immediately after the printers are added. The reason seems to be that these printers are being added by their 192.168 IP addresses, which cannot be pinged from the Ubuntu boxes.

Does anybody have some advice about what to do here, not including manually assigning 172.16 addresses to the printers?

---

### Post by Iowan on 2008-08-21
Just a crazy know-nothing guess from here: add a route to the 192.168 machines via the print server's address.
 (route add?)

---

### Post by Charlotte18 on 2008-08-22
The Ubuntu PC uses dhcp from the 172.16 domain. To add a route to 192.168 addresses, does dhcp have to be off in Ubuntu, with the 172.16 address assigned statically?

---

