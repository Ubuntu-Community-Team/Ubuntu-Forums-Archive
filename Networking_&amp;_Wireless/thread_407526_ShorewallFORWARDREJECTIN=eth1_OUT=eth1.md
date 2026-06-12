---
title: "Shorewall:FORWARD:REJECT:IN=eth1 OUT=eth1"
date: 2007-04-12
forum: Networking &amp; Wireless
---

### Post by chris.zeman on 2007-04-12
I am running Ubuntu server, and attempting multiple static routes. Here's the layout:
```

Network Interfaces:
eth0: IP - 10.1.10.210 (Connected to Comcast Cable Modem/Router)
eth1: IP - 172.16.100.200 (Connected to LAN)

```

Another server (Windows) on our network is connected to the company LAN, with a 10.115.0.0 network, and has Internet Connection Sharing enabled. I setup a static route on Ubuntu to route any packets destined for the 10.115.0.0 network through the Windows server. I can ping machines on that other network from Ubuntu, but the packets from machines on our LAN aren't being forwarded by Ubuntu.

To summarize, I want the machines connected to our LAN to access the internet throught eth0. That part is working great. I want the machines connected to our LAN to access company servers through the Windows server (IP: 172.16.100.100).

I already know this is an iptables issue. The problem is that the solutions I've found don't fit my situation. :( 

```

Apr 12 08:06:46 automation kernel: [44141418.560000] Shorewall:FORWARD:REJECT:IN=eth1 OUT=eth1 SRC=172.16.1.7 DST=10.115.2.12 LEN=106 TOS=0x00 PREC=0x00 TTL=127 ID=34678 PROTO=UDP SPT=1105 DPT=161 LEN=86 
Apr 12 08:06:52 automation kernel: [44141424.560000] Shorewall:FORWARD:REJECT:IN=eth1 OUT=eth1 SRC=172.16.1.7 DST=10.115.2.12 LEN=106 TOS=0x00 PREC=0x00 TTL=127 ID=34679 PROTO=UDP SPT=1105 DPT=161 LEN=86 
Apr 12 08:06:58 automation kernel: [44141430.560000] Shorewall:FORWARD:REJECT:IN=eth1 OUT=eth1 SRC=172.16.1.7 DST=10.115.2.12 LEN=106 TOS=0x00 PREC=0x00 TTL=127 ID=34680 PROTO=UDP SPT=1105 DPT=161 LEN=86 
Apr 12 08:07:04 automation kernel: [44141436.560000] Shorewall:FORWARD:REJECT:IN=eth1 OUT=eth1 SRC=172.16.1.7 DST=10.115.2.12 LEN=106 TOS=0x00 PREC=0x00 TTL=127 ID=34681 PROTO=UDP SPT=1105 DPT=161 LEN=86
```


```

@automation:~# iptables -t nat -L
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination
net_dnat   all  --  anywhere             anywhere            policy match dir in                                                                              pol none

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination
eth0_masq  all  --  anywhere             anywhere

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

Chain eth0_masq (1 references)
target     prot opt source               destination
MASQUERADE  all  --  10.115.0.0/16        anywhere            policy match dir o                                                                             ut pol none
MASQUERADE  all  --  172.16.0.0/16        anywhere            policy match dir o                                                                             ut pol none

Chain net_dnat (1 references)
target     prot opt source               destination
DNAT       tcp  --  anywhere             anywhere            tcp dpt:40159 to:17                                                                             2.16.1.2:40159
DNAT       udp  --  anywhere             anywhere            udp dpt:22513 to:17                                                                             2.16.1.2:22513
DNAT       tcp  --  anywhere             anywhere            tcp dpt:13044 to:17                                                                             2.16.90.1:13044
DNAT       udp  --  anywhere             anywhere            udp dpt:61693 to:17                                                                             2.16.90.1:61693
DNAT       tcp  --  anywhere             anywhere            tcp dpt:5800 to:172                                                                             .16.1.2:5800
DNAT       tcp  --  anywhere             anywhere            tcp dpt:5900 to:172                                                                             .16.1.2:5900
DNAT       tcp  --  anywhere             anywhere            tcp dpt:5385 to:172                                                                             .16.1.5:5380
DNAT       tcp  --  anywhere             anywhere            tcp dpt:5390 to:172                                                                             .16.1.10:5380
DNAT       tcp  --  anywhere             anywhere            tcp dpt:5382 to:172                                                                             .16.1.2:5380
DNAT       tcp  --  anywhere             anywhere            tcp dpt:5391 to:172                                                                             .16.90.1:5380
DNAT       tcp  --  anywhere             anywhere            tcp dpt:52628 to:17                                                                             2.16.90.1:52628

```


```

@automation:~# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.1.10.0       *               255.255.255.0   U     0      0        0 eth0
10.115.0.0      172.16.100.100  255.255.0.0     UG    0      0        0 eth1
172.16.0.0      *               255.255.0.0     U     0      0        0 eth1
default         10.1.10.1       0.0.0.0         UG    0      0        0 eth0
root@automation:~#

```

I would REALLY appreciate any advice! :D 

Thank you,
Chris

---

