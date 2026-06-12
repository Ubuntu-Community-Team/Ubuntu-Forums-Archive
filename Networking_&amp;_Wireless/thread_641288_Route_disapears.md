---
title: "Route disapears"
date: 2007-12-15
forum: Networking &amp; Wireless
---

### Post by elfstone2 on 2007-12-15
Hello,
I use VPN with VPNC and have some troubles with it. Before starting vpnc, the result of route looks like this:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
128.141.0.0     *               255.255.0.0     U     0      0        0 eth0
default         default-route-2 0.0.0.0         UG    0      0        0 eth0
```

Wenn I start vpnc, everything works, and route says:
```
ernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
ipsec04.lrz-mue default-route-2 255.255.255.255 UGH   0      0        0 eth0
128.141.0.0     *               255.255.0.0     U     0      0        0 eth0
default         *               0.0.0.0         U     0      0        0 tun0
```

This works for 10-60 Minutes, then it stops. I cant make new connection, already existing ones are stable (like irc, icq). Pings dont get replies, and when I start route, there is no replay, it simply is stuck in a loop. Something in my network is crashin, but i dont know what. When i stop vpnc and restart again, it works again.

Hope anyone can help me,
greetings
Thomas

---

### Post by elfstone2 on 2007-12-21
Hi.. i just found out (should have checked before maybe), that its a dns-problem..

I can ping ips, but no hostnames. But it only happens, when vpn is active, and the problem dissapears when i reconnect, so i guess the problem is somewhere on my side. What can i do, to fix this?

Greetings,
elfstone

---

### Post by kevdog on 2007-12-21
What dns servers are you using???

---

### Post by elfstone2 on 2008-01-16
Ok, I found out more:

The vpnconnection goes to a hostname, not an ip-adress. When i connect to wlan, I get an dns-server in my local domain written into my resolv.conf. When i start the vpn-connection, I get my resolv.conf overwritten, and i get an dns-server from outside.
This works fine, for a while. Then after some time, the resolv.conf gets overwritten again (maybe by dhcp?) and i get the local dns-server again.

Since the local dns-server is not reachable from outside, I cant reach it anymore (all traffic is routed via vpn), and i cant make any new conections. How can i prevent / change this behaviour?

---

