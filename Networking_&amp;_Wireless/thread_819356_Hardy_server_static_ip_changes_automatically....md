---
title: "Hardy server static ip changes automatically..."
date: 2008-06-05
forum: Networking &amp; Wireless
---

### Post by twgray on 2008-06-05
I have installed Hardy server behind a router.  After installation, I changed my IP address from DHCP to static by editing my /etc/network/interfaces file as follows:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.0.1.xxx
netmask 255.255.255.0
network 10.0.1.0
broadcast 10.0.1.0
gateway 10.0.1.1

The router, of course, has NAT enabled.  Sometime overnight, the static IP address changes to one in the range that the router is assigning using DHCP, as if the static IP were renewing with DHCP.  What am I doing wrong, or missing?

---

