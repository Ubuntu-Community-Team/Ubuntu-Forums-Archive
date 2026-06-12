---
title: "Bridge and VPN"
date: 2008-05-10
forum: Networking &amp; Wireless
---

### Post by ethrandil on 2008-05-10
Hihow,

I need to run virtualbox in a so called host-interface-mode. Therefore I need a custom network configuration, incl. a bridge mode interface.

My /etc/network/interfaces looks like this: 
```
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.

auto eth0
iface eth0 inet manual
up ifconfig eth0 up

auto br0
iface br0 inet dhcp
bridge_ports eth0
```

With this manual configuration, network-manager does not work. So I need a way to configure VPN and br0 manually. Do you have any hints for me?

mfg
- eth

---

