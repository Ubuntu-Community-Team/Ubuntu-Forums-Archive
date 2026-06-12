---
title: "DHCP error &quot;no subnet declaration for eth0&quot;"
date: 2005-09-18
forum: Networking &amp; Wireless
---

### Post by Poppa Stylez on 2005-09-18
Hello everyone, hopefully you can help me, because this is driving me up the wall.
I'm trying to configure my ubuntu 5.04 pc to be a DHCP server, but whenever i run "dhcp3-server restart" (or dhcpd-server restart can't remember which one), i get an error which tells me that it couldn't start and to check my syslog. So i check my syslog and i'm given the error message "no subnet declaration for eth0 (0.0.0.0).

What the HELL DOES THAT MEAN!!!!!

My dhcpd.conf file looks like the following...

subnet 192.168.0.0 netmask 255.255.255.0 {
range 192.168.0.1 192.168.0.254
}

---

### Post by Poppa Stylez on 2005-09-18
Figured it out. Didn't assign myself a static i.p. address!
Doh!

---

