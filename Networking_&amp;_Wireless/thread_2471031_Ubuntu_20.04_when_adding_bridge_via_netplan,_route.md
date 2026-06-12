---
title: "Ubuntu 20.04: when adding bridge via netplan, routes/IPs are duplicated"
date: 2022-01-20
forum: Networking &amp; Wireless
---

### Post by temmokan on 2022-01-20
OS: Ubuntu 20.04.3, all the latest updates installed.
 I am trying to create a bridge interface, to enslave current (eno1)
 Netplan configuration:

 ```
# This is the network config written by 'subiquity'
network:
  version: 2
  renderer: networkd

  ethernets:
    eno1:
      dhcp4: false
      dhcp6: false

  bridges:
    br0:
      interfaces: [eno1]
      addresses: [10.20.0.21/24]
      gateway4: 10.20.0.1
      nameservers:
        search: [example.com]
        addresses: [10.20.0.1,10.20.0.10]
      dhcp4: false
      dhcp6: false
``` 
When I run "netplan try", I see:
 ```
** (generate:2332): WARNING **: 12:54:41.673: Problem encountered while validatingdefault route consistency.Please set up multiple routing tables and use `routing-policy` instead.
Error: Conflicting default route declarations for IPv4 (table: main, metric: default), first declared in br0 but also in eno1
```
If I reboot the system, the "route" shows the below:
 ```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         10.20.0.1       0.0.0.0         UG    0      0        0 br0
default         10.20.0.1       0.0.0.0         UG    0      0        0 eno1
10.20.0.0        0.0.0.0        255.255.255.0   U     0      0        0 br0
10.20.0.0        0.0.0.0        255.255.255.0   U     0      0        0 eno1
```
The system remains usable, but the configuration is obviously abnormal.
 $ networkctl displays:
 ```
networkctl 
IDX LINK TYPE     OPERATIONAL SETUP     
  1 lo   loopback carrier     unmanaged 
  2 eno1 ether    routable    configured
  3 br0  bridge   routable    configured
```
How do I make eno1 enslaved and prevent it from creating duplicates of routing entry/IP address?

---

### Post by TheFu on 2022-01-21
I don't see anything wrong in the netplan.  
Perhaps I'm missing something too?  

In my reference version, the "version" is at a different indentation level, but I think that is incorrect.  eno1 shouldn't be getting any IP addresses - IPv4 or IPv6.  Anyway, you can check this for issues:

```
#   [ for bridge + static - KVM ]
network:
 version: 2
  renderer: networkd
  ethernets:
     eth0:
       dhcp4: false
       dhcp6: false
  bridges:
      br0:
        interfaces: [eth0]
        dhcp4: false
        dhcp6: false
        addresses: [192.168.1.15/24]
        gateway4: 192.168.1.1
        nameservers:
           addresses: [192.168.1.1]
```

It is slightly simpler than yours.  Simply and test?

I'd hate to think that the order of entries matters in YAML, but that is something to try too.  I think the version, ethernets and bridges should all be on the same level, as you have them, not as my reference does.

You've certainly seen these examples: [https://netplan.io/examples/](https://netplan.io/examples/) but perhaps a lurker in a year hasn't.

---

