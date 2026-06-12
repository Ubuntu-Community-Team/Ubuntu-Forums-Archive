---
title: "Linux as a router"
date: 2007-12-17
forum: Networking &amp; Wireless
---

### Post by rodtempleton on 2007-12-17
My apologies if this seems to be a no-brainer to some, but....

I'm trying to set up a Linux router with the following configuration:

eth0: DHCP client on a 192.168.75.x network (255.255.255.0) - currently has 192.168.75.220
eth1: static address of 192.168.101.254 (255.255.255.0)

From a laptop plugged into eth1, with a static address of 192.168.101.226, I can ping both 101.254 and 75.220, but I can't ping any further than that.

A look at the routing table: 

> route

Destination          Gateway      Genmask                Flags   Metric  Ref   Use Iface
192.168.101.0          *            255.255.255.0          U           0      0     eth1
192.168.75.0            *            255.255.255.0          U           0      0     eth0
169.25.0.0                *            255.255.255.0          U           0      0     eth1
default                gateway.ra   0.0.0.0                     UG        0      0     eth0

There's more to the address under the gateway entry, obviously, but it's been changed here.

I'd appreciate any thoughts on getting this working.

Thanks,
Rod

---

### Post by foolsh on 2007-12-18
try installing ipmasq and maybe dnsmasq.
I see what your trying to set up but wouldn't it be easier to bridge the two ifaces and give it the dhcp recieved address?

---

