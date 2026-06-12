---
title: "Multiple default routes"
date: 2007-03-18
forum: Networking &amp; Wireless
---

### Post by dc2447 on 2007-03-18
I have two network cards on different lan's in the same server.

This works well apart from the fact there are two default routes.

> $ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth1
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 eth1
0.0.0.0         192.168.1.254   0.0.0.0         UG        0 0          0 

This /shouldn't/ be a problem as 192.168.0.1 has a default route of 192.168.1.254 which is the main gateway but there seems to be some type of routing loop when both defulat routes are enabled and the machine doesn't seem to be able to get out to the internet

This is solved by:

sudo route del default gw 192.168.0.1

Thoughts?

---

### Post by lloyd_b on 2007-03-18
If you're using static IP info, then all you need to do is delete the "gateway ..." line associated with eth1 in the file "/etc/network/interfaces".  This will prevent that "192.168.0.1" route from being created.

For DHCP assigned info, you'll need to modify the "/etc/dhcp3/dhclient.conf" file to limit the eth1 interface so that it doesn't accept a gateway.  Sorry - I'm not experienced enough with DHCP to give you any directions on how to accomplish this.

Lloyd B.

---

### Post by dc2447 on 2007-03-18
I have that commented out

auto eth1
iface eth1 inet static
address 192.168.0.201
netmask 255.255.255.0
#gateway 192.168.0.1

But I still get a gateway.

I'm wondering if it's a bug

---

### Post by lloyd_b on 2007-03-18
> I have that commented out

```
auto eth1
iface eth1 inet static
address 192.168.0.201
netmask 255.255.255.0
#gateway 192.168.0.1
```

But I still get a gateway.

I'm wondering if it's a bug

Just for the heck of it, try deleting that line and see what happens.  *Something* is causing that route to be created, and that's one of the few things I can think of that could do so.

Lloyd B.

---

### Post by dc2447 on 2007-03-18
> **lloyd_b said:**
> Just for the heck of it, try deleting that line and see what happens.  *Something* is causing that route to be created, and that's one of the few things I can think of that could do so.

Lloyd B.

Yeah - deleting the line entirely did it - buggy

---

