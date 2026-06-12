---
title: "network problem after edgy upgrade"
date: 2006-10-22
forum: Networking &amp; Wireless
---

### Post by Marco Renoldi on 2006-10-22
after upgrade to edgy I have no network.. But i can connect with a dapper live distro.
The configuration files are ok (interfaces, dhclient, resolv...) but if i ping [www.google.it](www.google.it) it says "unknown host". After a sudo /etc/init.d/networking restart i geet this:

DHCPREQUEST on eth0 to 255.255.255.255 port 67
ip length 328 disagrees with bytes received 332.
accepting packet with data after udp payload.
ip length 328 disagrees with bytes received 332.
accepting packet with data after udp payload.
DHCPACK from 1.240.65.248
SIOCADDRT: File exists
send_packet: Operation not permitted
There is already a pid file /var/run/dhclient.eth0.pid with pid 269026824

Any ideas?

---

### Post by Kalif on 2006-11-30
I had a similar problem with another distro a few years ago. Then it happened that the particular kernel module for supporting my network adapter had a new name and after figuring out that it was an easy fix.
/k

---

