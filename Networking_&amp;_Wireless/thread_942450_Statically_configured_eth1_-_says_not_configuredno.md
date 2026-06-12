---
title: "Statically configured eth1 - says not configured/no such process"
date: 2008-10-09
forum: Networking &amp; Wireless
---

### Post by maxhavoc on 2008-10-09
I have a statically configured eth1 which I cannot seem to get working. It was working fine, then I rebooted and now it no longer works.

When I do ifdown eth1 I get:
```

ifdown: interface eth1 not configured

```

When I do ifup eth1 I get:
```

SIOCADDRT: No such process
Failed to bring up eth1.

```

Here is the relevant portion of my /etc/network/interfaces file:
```

iface eth1 inet static
address 10.250.0.10
netmask 255.255.255.248
gateway 10.250.0.1

auto eth1

```

Anyone have any ideas why this might be happening? Thanks.

---

### Post by maxhavoc on 2008-10-09
This forum moves fast...bump...

---

### Post by dblade on 2008-10-09
Check and see under System->Administration->Network if eth1 (Wired Connection?) is set to Roaming and if so uncheck that under properties and set the configuration accordingly.

I'm using a wired connection and I don't know what the roaming thing would mean in that context, but when it's set, it does muck with ifdown, ifup, and init.d/networking to the point that they don't really do anything.  That and the avahi-daemon have been a real pain for me sometimes.

---

### Post by cariboo on 2008-10-09
I would also run:

```
lshw -C network
```

And post the output here, to see what happened to eth0.

Jim

---

