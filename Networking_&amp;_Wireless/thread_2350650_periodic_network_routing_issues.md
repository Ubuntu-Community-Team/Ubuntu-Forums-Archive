---
title: "periodic network routing issues"
date: 2017-01-26
forum: Networking &amp; Wireless
---

### Post by msbaa on 2017-01-26
I've been having this weird problem with two systems (one physical and one vm) where periodically, they lose the ability to communicate with one or two ip's on a remote subnet. The remote subnet is accessible via the default gateway. Both systems poll these networks (one runs rancid for cisco configs and the other opennms to ping/snmp,service check, etc). Most of the time, the issue happens after an mpls or power outage at the remote site, but the weird thing is the host can connect to some ip's on that subnet but not others. The fix is to ifdown eth0 and then ifup eth0. See the traceroutes below. When the issue is occurring, the packets are being forwarded to an incorrect ip address. The topology in the datacenter (dc1) is as follows:

```

                             ----> dc1-asa --> internet
host eth0 --> dc1-core-6-20 |
                             ----> dc1-mpls --> remote1

```

dc1-core-6-20 makes the route decision to forward mpls routes to dc1-mpls and default route to dc1-asa. You'll see that when it's not working, the host is forwarding directly to dc1-asa for some reason even though the default route is set to forward to dc1-mpls.

```

$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.254.0.1      0.0.0.0         UG    0      0        0 eth0
10.254.0.0      0.0.0.0         255.255.252.0   U     0      0        0 eth0


$ traceroute 10.0.0.5
traceroute to 10.0.0.5 (10.0.0.5), 30 hops max, 60 byte packets
 1  dc1-asa1 (10.254.0.3)  0.243 ms  0.225 ms  0.234 ms
 2  * * *
 3  * * *
 4  *^C


$ sudo route add  -host 10.0.0.5 gw 10.254.0.1


$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.254.0.1      0.0.0.0         UG    0      0        0 eth0
10.254.0.0      0.0.0.0         255.255.252.0   U     0      0        0 eth0
10.0.0.5        10.254.0.1      255.255.255.255 UGH   0      0        0 eth0


$ traceroute 10.0.0.5
traceroute to 10.0.0.5 (10.0.0.5), 30 hops max, 60 byte packets
 1  dc1-asa1 (10.254.0.3)  0.243 ms  0.225 ms  0.234 ms
 2  * * *
 3  * * *
 4  * * *
 5  * * *
 6  * * *
 7  *^C


$ sudo ifdown eth0 && sudo ifup eth0


$ traceroute 10.0.0.5
traceroute to 10.0.0.5 (10.0.0.5), 30 hops max, 60 byte packets
 1  dc1-core-6-20 (10.254.3.253)  11.098 ms  11.149 ms  11.226 ms
 2  dc1-mpls (10.254.1.10)  0.522 ms  0.588 ms  0.599 ms
 3  10.100.213.145 (10.100.213.145)  4.079 ms  4.076 ms  4.195 ms
 4  10.200.92.125 (10.200.92.125)  42.094 ms  41.794 ms  41.928 ms
 5  10.200.92.126 (10.200.92.126)  38.410 ms  38.405 ms  38.512 ms
 6  remote1-3850 (10.0.0.5)  41.454 ms * *

```

I'm running ubuntu 14.04. This has been happening for a while now and only experienced this issue once I upgraded from CentOS to Ubuntu. 

Any help would be greatly appreciated.

---

