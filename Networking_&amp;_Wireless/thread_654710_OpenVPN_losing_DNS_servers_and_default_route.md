---
title: "OpenVPN losing DNS servers and default route"
date: 2007-12-31
forum: Networking &amp; Wireless
---

### Post by jakev383 on 2007-12-31
I am connecting to an openvpn installation on Endian Firewall (a lot like IPCop).
Anyway, when Windows clients connect they're part of the network, and can still browse the Internet. When I connect with the network manager openvpn client on my Ubuntu machine, I can access the other internal network, but I can no longer communicate with the rest of the Internet.  Here's my route command before the VPN connection:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.76.0    *               255.255.255.0   U     0      0        0 eth1
default         192.168.76.1    0.0.0.0         UG    0      0        0 eth1

And I have my DNS servers in /etc/resolv.conf. Now when I connect to the VPN, my route looks like:

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
208.12.142.12   192.168.76.1    255.255.255.255 UGH   0      0        0 eth1
192.168.76.0    *               255.255.255.0   U     0      0        0 eth1
default         *               0.0.0.0         U     0      0        0 tap0

And I lose my DNS entries in /etc/resolv.conf. 

Does anyone have any suggestions? It would only have to be a setting on my side, since Win clients have no problems, right?
Thanks in advance.

---

