---
title: "dhcp3-server initialisation fails"
date: 2008-08-29
forum: Networking &amp; Wireless
---

### Post by kcode on 2008-08-29
i am trying to PXE boot my machine.
on /etc/init.d/dhcp3-server start
i got
 * Starting DHCP server dhcpd3
   ...fail!

a snippet of dhcpd.conf which i edited:

 #subnet 10.254.239.0 netmask 255.255.255.224 {
next-server 172.28.31.2;
filename "pxelinux.0";
#  range 10.254.239.10 10.254.239.20;
#  option routers rtr-239-0-1.example.org, rtr-239-0-2.example.org;
#}

---

