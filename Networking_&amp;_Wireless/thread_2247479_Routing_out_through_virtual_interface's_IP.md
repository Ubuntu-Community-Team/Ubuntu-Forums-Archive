---
title: "Routing out through virtual interface's IP"
date: 2014-10-08
forum: Networking &amp; Wireless
---

### Post by mail18 on 2014-10-08
Fresh 14.04.01 server installation (in Hyper-V).
eth0 is connected to ISP.

Using *ip addr add x.x.x.3 dev eth0*, I've added another public IP, so:
```
eth0: x.x.x.2
eth0:1: x.x.x.3
```

I added default route using:
```
ip route add default via x.x.x.1 dev eth0:1 src x.x.x.3
```

However the result from *ip route* shows (eth0 instead of eth0:1):
```
default via x.x.x.1 dev eth0  src x.x.x.3
```

Result from *curl myexternalip.com/raw* is:
```
x.x.x.2
```

How do I route out through virtual interface's IP?

PS: Adding multiple network cards is not an option because of Hyper-V's NICs count limitation.
PS2: I've also tried this in CentOS 7 w/ the same results.

---

### Post by SeijiSensei on 2014-10-08
You first need to add the virtual interface with ifconfig:
```
sudo ifconfig eth0:1 10.10.10.10 netmask 255.255.255.0
```

However there is absolutely no benefit to this from a routing perspective.  You still only have one interface, so all the traffic will go through it no matter how it's addressed.

---

### Post by Michael_McKenney on 2014-10-08
You need a device that can handle sub interfaces properly like a Cisco Firewall.  I have 11 VLANs routing through 3 ports on my ASA-5520 from VMware 5.5 U2 and HP Layer 3 switches.  On the layer 3 switches, I have policy based routing rules for each VLAN.  It sets up the gateway of last resort for each VLAN.  The issue is each 1 Gbps port has 3-4 Gbps pipes routing through them.  You can get bogged down.

---

