---
title: "VPN and routing"
date: 2007-12-14
forum: Networking &amp; Wireless
---

### Post by bamarob on 2007-12-14
I'm finally able to connect to our VPN at work (we recently switched to a Cisco ASA device), but am having issues with network routing.  Before connecting to the VPN the 'route' command returns:

raldridge@raldridge-lt2:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth1
default         192.168.1.1     0.0.0.0         UG    100    0        0 eth1


After connecting to the VPN (X.X.X.X is our internet accessible VPN address):

raldridge@raldridge-lt2:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
X.X.X.X   192.168.1.1     255.255.255.255 UGH   0      0        0 eth1
lincoln.tsteel. *               255.255.255.255 UH    0      0        0 tun0
monroe.tsteel.c *               255.255.255.255 UH    0      0        0 tun0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth1
default         *               0.0.0.0         U     0      0        0 tun0
default         192.168.1.1     0.0.0.0         UG    100    0        0 eth1


I need to somehow add/configure routes where all 172.x.x.x and 10.x.x.x traffic gets routed through the VPN tunnel and all other traffic continues to go out to the internet.

I'm using KVpnc for my client.  Any suggestions would be greatly appreciated.

BamaRob

---

### Post by Dragon43 on 2007-12-16
I get all that working and 7.10 still will not open the other computers.  I now get two networks, MSwork one and my inhouseone.  All I want is my little inhouse one....  And for it to work... GRrrrrrrr

---

