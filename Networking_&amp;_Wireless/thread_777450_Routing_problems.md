---
title: "Routing problems"
date: 2008-05-01
forum: Networking &amp; Wireless
---

### Post by hmaich on 2008-05-01
Hello all,

I'm newbie in Linux and I have a doubt concerning networks.
Here I have 2 networks. A wireless network (I use to connect to internet) and a wired network, I use sometimes to file sharing.
The problem is, every time I connect to the wired network I lose the internet connection.

I checked the routing table and figure out a new default route is create to comply to the wired net.
So, if I remove this default route and create a specific one by myself, I got the internet and file sharing working again.
The problem is, I don't want to do it every time I connect to this net.

Is there any way to set this setting automatically when I connect to the wired net?

Thank you,

Here are the routing table before and after the wired connection and the way I want it to be.

BEFORE:
maich@Giulia:~$ route -n

Kernel IP routing table

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

192.168.178.0   0.0.0.0         255.255.255.0   U     0      0        0 wlan0

169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0

169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0

0.0.0.0         192.168.178.1   0.0.0.0         UG    0      0        0 wlan0

0.0.0.0.0         0.0.0.0         U     1000   0        0 eth0

AFTER:
maich@Giulia:~$ route -n

Kernel IP routing table

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

192.168.178.0   0.0.0.0         255.255.255.0   U     0      0        0 wlan0

169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0

169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0

0.0.0.0         169.254.0.1     0.0.0.0         UG    0      0        0 eth0

0.192.168.178.1   0.0.0.0         UG    0      0        0 wlan0

I WANT:
Kernel IP routing table

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

192.168.178.0   0.0.0.0         255.255.255.0   U     0      0        0 wlan0

169.254.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0

0.0.0.0         192.168.178.1   0.0.0.0         UG    0      0        0 wlan0

---

