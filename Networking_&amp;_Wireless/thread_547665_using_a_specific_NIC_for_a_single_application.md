---
title: "using a specific NIC for a single application"
date: 2007-09-10
forum: Networking &amp; Wireless
---

### Post by moonlightcheese on 2007-09-10
first post here, and i'd like to say that i've gotten some awesome support here already.  anytime i googled certain questions specific to ubuntu i was able to pull up something here in the form of a faq or forum post that aided me in solving a number of issues including getting my dual head ATi X1300 Pro to display to two monitors among other things.  the faqs and support here are great, keep up the good work.

now... the actual problem:

i'm using the TSC to log into a Windows desktop on eth0, and i have another NIC in the machine connected to a DSL line.  i'd like to be able to use the eth0 for just the TSC and use eth1 (DSL line) as the default connection in ubuntu.  is there a way to just start TSC with a command option or something to get it to use eth0 or is the answer more complex than that?

---

### Post by bwhitaker on 2007-09-10
It's a little more complicated than that.  I'm betting you've got 2 default gateways now, can you give us a print out of your route table?

```

$route

```
or 
```

$ip route

```


this is mine:
```

$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.33.0        *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.33.1      0.0.0.0         UG    0      0        0 eth0

```

---

### Post by moonlightcheese on 2007-09-10
$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.49.0    *               255.255.255.0   U     0      0        0 vmnet8
192.168.155.0   *               255.255.255.0   U     0      0        0 vmnet1
170.168.8.0     *               255.255.252.0   U     0      0        0 eth1
link-local      *               255.255.0.0     U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth1
default         hsrp-vlan8.ns.g 0.0.0.0         UG    0      0        0 eth1
default         *               0.0.0.0         U     1000   0        0 eth0


$ ip route
192.168.49.0/24 dev vmnet8  proto kernel  scope link  src 192.168.49.1 
192.168.155.0/24 dev vmnet1  proto kernel  scope link  src 192.168.155.1 
170.168.8.0/22 dev eth1  proto kernel  scope link  src 170.168.10.96 
169.254.0.0/16 dev eth0  proto kernel  scope link  src 169.254.10.247 
169.254.0.0/16 dev eth1  scope link  metric 1000 
default via 170.168.11.254 dev eth1 
default dev eth0  scope link  metric 1000 

the vmnet are just virtual adapters for vmware player.

---

### Post by moonlightcheese on 2007-09-11
::bump::

---

