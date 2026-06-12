---
title: "How I can enter a permanent static route"
date: 2007-03-25
forum: Networking &amp; Wireless
---

### Post by SiriusTux on 2007-03-25
How can I enter a static route in Ubuntu?
I many distro you can add a line like this:

10.0.0.0/8 via 192.168.1.254

in the following file:
"/etc/sysconfig/network-scripts/route-eth0"

this will add a permanent route to the net 10.0.0.0/8 using gw 192.168.1.254 viewed from interface eth0

Is there something similar in Ubuntu?

Thanx everyones

Sirius

---

### Post by spd106 on 2007-03-25
I'm not sure this is the best way, but try adding this line to the /etc/network/interfaces file.
```
auto eth0
iface eth0 inet dhcp
[COLOR="Red"]post-up ip route add to 10.0.0.0/8 via 192.168.1.254 dev eth0[/COLOR]

```

---

