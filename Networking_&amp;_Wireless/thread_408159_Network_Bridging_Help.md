---
title: "Network Bridging Help"
date: 2007-04-13
forum: Networking &amp; Wireless
---

### Post by ap.sampson on 2007-04-13
Hokay!  In windows I use a network bridge so that my xbox is able to communicate with the rest of the network, the internet, etc...

Whenever I try to set up a bridge in Ubuntu, the xbox connects to everything just fine; however, my desktop can't see anything - which is ridiculous, since everything the xbox can see is coming through said desktop.

Any help?

Note: I've tried GuideDog and Firestarter - these don't seem to work for what I need.  Yes, they share the connection and the xbox can download weather and RSS feeds, but it doesn't have access to network shares.

Network Config: Cable Modem ->Router->Switch->Desktop  DHCP all around.

---

### Post by PokerJoker on 2007-04-13
if u do a "sudo route" command, what's the routing table say? Is your dekstop traffic directed to your gateway ie. router?

[ See my previous answer ]

---

### Post by ap.sampson on 2007-04-13
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
192.168.1.0     *               255.255.255.0   U     0      0        0 br0
link-local      *               255.255.0.0     U     0      0        0 eth1
link-local      *               255.255.0.0     U     0      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 br0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
default         *               0.0.0.0         U     1000   0        0 eth1

```

---

