---
title: "IPv6 address instead of IPv4"
date: 2008-10-08
forum: Networking &amp; Wireless
---

### Post by Fr0ns on 2008-10-08
Hey,

After setting up a DHCP server with DHCP3D I encountered some problems with normal LAN connectivity. The DHCP3D serve doesn't automatically load because the machine uses DHCP.

Since I got DHCP3D working I haven't been able to connect to my normal lan via DHCP. Ifconfig only shows and "inet6 addr" and not an "inet addr" 

*I think this is the problem, I haven't had any luck with blacklisting the ipv6 module.*

/etc/network/interfaces:
```
auto eth0
iface eth0 inet dhcp
(also tried adding 255.255.255.0)
```

Ubuntu Server 2.6.24-19-server

---

