---
title: "VPNC connects but can't ping in Dapper"
date: 2007-02-22
forum: Networking &amp; Wireless
---

### Post by user2037 on 2007-02-22
Laptop is plugged into Windows machine that is sharing a dial-up connection. So its providing service from 192.168.0.1.

After Installing Vpnc I can connected to corporate VPN but I can not ping the internal network. Although the outside world is still reachable.

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
xxx.xxx.xxx.xxx   192.168.0.1     255.255.255.255 UGH   0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 tun0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0

Then installed Network Manager and Vpnc plug-in (plug-in from Linux2go) in the hope that I was configuring something improperly. Now I can connect to the VPN from NM but can't ping anyone.

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
xxx.xxx.xxx.xxx   192.168.0.1     255.255.255.255 UGH   0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 tun0

What should the route look like?

---

