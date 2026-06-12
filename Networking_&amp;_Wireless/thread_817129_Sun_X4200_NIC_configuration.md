---
title: "Sun X4200 NIC configuration"
date: 2008-06-03
forum: Networking &amp; Wireless
---

### Post by sinaghazi on 2008-06-03
Hi,

We use 2 physical ports out of 4 NICs in a Sun X4200 X64 Server.
And we have 2 VMWare virtual ports for NAT and Bridge to virtual machines.  

Following is our Kernel IP routing table.
```

Kernel IP routing table
Destination     Gateway  Genmask   Flags Metric Ref  Use Iface
XX.XX.72.176    *        255.255.255.240 U     0     0   0 eth1
192.168.201.0   *        255.255.255.0   U     0     0   0 vmnet8
192.168.92.0    *        255.255.255.0   U     0     0   0 vmnet1
192.168.10.0    *        255.255.255.0   U     0     0   0 eth0
default         XX.XX.72.177    0.0.0.0  UG    100   0   0 eth1

```

We use Hardy 8.04 and a clean shorewall firewall only for eth1. 

We can access the internet from the box. 
We can access the box from the internet. 
We can not access the box from the LAN (eth0) AND
We can not access the LAN from the box. 

What are the possible issues we might be facing?

Cheers,
~Sina

---

