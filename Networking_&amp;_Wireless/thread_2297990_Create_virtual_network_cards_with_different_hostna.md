---
title: "Create virtual network cards with different hostnames and MAC addresses"
date: 2015-10-08
forum: Networking &amp; Wireless
---

### Post by dam034 on 2015-10-08
Hi,

I created a VPS with the server version of ubuntu.

I want to create multiple virtual network cards because I need multiple IP addresses from DHCP server.

The actual content of /etc/network/interfaces is this:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```
I want to create other virtual network interfaces using the physical network interface eth0, but each of them must have its DHCP client name and its MAC address.

Is this possible? If so, how?


Thanks,
dam034

---

