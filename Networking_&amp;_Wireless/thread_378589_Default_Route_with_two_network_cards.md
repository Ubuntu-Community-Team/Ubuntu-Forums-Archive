---
title: "Default Route with two network cards"
date: 2007-03-07
forum: Networking &amp; Wireless
---

### Post by pmgeahan on 2007-03-07
Situation:

Edgy Eft, kernel 2.6.17-10-generic.

This system has three network cards, each connecting to a different physical network.  All three cards work fine.  

eth0 is a wired interface with a static IP.  This device can route out to the Internet.

eth1 is a wired interface with a dynamic IP.  This device cannot route out to the Internet.

eth2 is a wired interface with a statis IP.  This device can route out to the Internet.

When I boot, my routing table has two default entries; one to go out via eth0, one to go out via eth2.  I want, on boot, for the routing table to contain one default entry, to route out through eth0.  I do not want a default route through eth2.

Can anyone point me to either a way to prevent a default route from forming for eth2 or for forcing the 'master' default route to be eth0?

Thanks a ton.

/etc/network/interfaces:
```
auto lo
iface lo inet loopback

iface eth1 inet dhcp


auto eth2
iface eth2 inet static
address 192.168.1.205
netmask 255.255.255.0
gateway 192.168.1.254

auto eth0
iface eth0 inet static
address 192.168.8.205
netmask 255.255.255.0
gateway 192.168.8.1


up route add default gw 192.168.8.1 dev eth0

```

---

### Post by lloyd_b on 2007-03-07
If you remove the "gateway..." line from the configuration for eth2, that extra default route should disappear with it.

At that point, the only network you'll be able to reach via eth2 is the 192.168.8.x subnet (which I believe is what you want - correct me if I'm wrong).

Lloyd B.

---

### Post by pmgeahan on 2007-03-07
Blast, I knew it was something that simple.  Works like a charm(even without the up route line).

Thanks!

---

