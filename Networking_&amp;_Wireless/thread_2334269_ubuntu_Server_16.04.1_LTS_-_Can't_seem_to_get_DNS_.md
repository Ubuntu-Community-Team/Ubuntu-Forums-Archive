---
title: "ubuntu Server 16.04.1 LTS - Can't seem to get DNS working with Static IP"
date: 2016-08-17
forum: Networking &amp; Wireless
---

### Post by wh33t2 on 2016-08-17
Hey forums,

Here is my /etc/network/interfaces file.
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto enp2s0
iface enp2s0 inet static
address 192.168.0.3
netmask 255.255.255.0
gateway 192.168.0.1
broadcast 192.168.0.255
dns-search shaw.router
dns-servers 64.59.160.14 64.59.160.101

#iface enp2s0 inet dhcp

```

Any ideas what I'm doing wrong? What is really strange is that the whole thing works fine on DHCP.

```
:~$ ping google.ca
ping: unknown host google.ca
```

---

### Post by gordintoronto on 2016-08-18
I think it should be dns-nameservers

---

