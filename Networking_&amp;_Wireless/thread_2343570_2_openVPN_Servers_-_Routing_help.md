---
title: "2 openVPN Servers - Routing help"
date: 2016-11-17
forum: Networking &amp; Wireless
---

### Post by dbecker on 2016-11-17
2 openvpn servers (one is UDP, one is TCP), both on the same physical box, same physical LAN. 
The 2 servers are on the 192.168.44.0 subnet.

```
##server1.conf
server 10.8.0.0 255.255.255.0
push "route 192.168.44.0 255.255.255.0"
push "route 10.10.1.0 255.255.255.0"
route 10.10.1.0 255.255.255.0
push "route 10.10.2.0 255.255.255.0"
route 10.10.2.0 255.255.255.0
push "route 10.10.4.0 255.255.255.0"
route 10.10.4.0 255.255.255.0

```

```
##server2.conf
server 10.7.0.0 255.255.255.0
push "route 192.168.44.0 255.255.255.0"
push "route 10.10.1.0 255.255.255.0"
route 10.10.1.0 255.255.255.0
push "route 10.10.2.0 255.255.255.0"
route 10.10.2.0 255.255.255.0
push "route 10.10.4.0 255.255.255.0"
route 10.10.4.0 255.255.255.0
```

server2/ccd/client2
```
iroute 10.10.4.0 255.255.255.0
```

client2 local subnet is: 10.10.4.0
client2 connected to server2 via TLS connection
client2 can ONLY access the 192.168.44.0 subnet, NONE of the other 10.10.x.x subnets?

```
root@openvpnServer:/home/administrator# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         FVS336GV3       0.0.0.0         UG    0      0        0 eth0
10.7.0.0        10.7.0.2        255.255.255.0   UG    0      0        0 tun1
10.7.0.2        *               255.255.255.255 UH    0      0        0 tun1
10.8.0.0        10.8.0.2        255.255.255.0   UG    0      0        0 tun0
10.8.0.2        *               255.255.255.255 UH    0      0        0 tun0
10.10.1.0       10.7.0.2        255.255.255.0   UG    0      0        0 tun1
10.10.2.0       10.7.0.2        255.255.255.0   UG    0      0        0 tun1
10.10.4.0       10.8.0.2        255.255.255.0   UG    0      0        0 tun0
192.168.44.0    *               255.255.255.0   U     0      0        0 eth0

```

Here are the errors on server2 log, these started showing up after I created server2
```
RTNETLINK answers: Operation not permitted
Thu Nov 17 05:33:24 2016 ERROR: Linux route delete command failed: external program exited with error status: 2
RTNETLINK answers: Operation not permitted
Thu Nov 17 05:33:24 2016 ERROR: Linux route delete command failed: external program exited with error status: 2
RTNETLINK answers: Operation not permitted
Thu Nov 17 05:33:24 2016 ERROR: Linux route delete command failed: external program exited with error status: 2
RTNETLINK answers: Operation not permitted
Thu Nov 17 05:33:24 2016 ERROR: Linux route delete command failed: external program exited with error status: 2


```

[FONT=arial]The local routing table of client2 includes routes to all of the 10.10.x.x subnets, so they are being received by connecting clients, but I can't access them from clinet2??

thanks.
[/FONT]

---

