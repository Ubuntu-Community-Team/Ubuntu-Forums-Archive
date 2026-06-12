---
title: "Network Settings adds several default routes?"
date: 2008-10-07
forum: Networking &amp; Wireless
---

### Post by it.henrik on 2008-10-07
Hi,

Network Settings is messing up my routing table :)

I have a computer connected to several networks and I am trying to use network manager to handle the network configurations.

right now I have it like this:
eth0 - dhcp
eth1 - static/24 (no gateway) 
eth2 - static/8 + gateway

With this configuration I get 2 default routes?

What I want is the default route from the DHCP and just a gateway for the eth2 - static/8 network, how can I get this result using ubuntus "Network Settings"-tool?

heres the results from route (A.B.C.* is just my DHCP:d ip adress)

```
route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth1
A.B.C.0    *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth2
10.0.0.0        *               255.0.0.0       U     0      0        0 eth2
default         10.20.0.1       0.0.0.0         UG    100    0        0 eth2
default         A.B.C.1    0.0.0.0         UG    100    0        0 eth0
```

---

### Post by willca on 2008-10-07
Can you post the contents of this file.

/etc/network/interfaces

---

### Post by it.henrik on 2008-10-07
```
cat /etc/network/interfaces 
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth0

iface eth2 inet static
address 10.20.0.81
netmask 255.0.0.0
gateway 10.20.0.1



iface eth1 inet static
address 192.168.1.2
netmask 255.255.255.0

auto eth1

auto eth2
```

---

### Post by willca on 2008-10-07
iface eth2 inet static
address 10.20.0.81
netmask 255.0.0.0
gateway 10.20.0.1  <---- take this out


sudo /etc/init.d/networking restart

Test if you can still get to those hosts via you eth2. If not, then add a specific route for it specifically by not putting a gateway entry in the /etc/network/interfaces file.

---

