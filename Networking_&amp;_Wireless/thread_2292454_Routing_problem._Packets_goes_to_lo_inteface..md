---
title: "Routing problem. Packets goes to lo inteface."
date: 2015-08-28
forum: Networking &amp; Wireless
---

### Post by spam-accepter on 2015-08-28
Hi! 
Please help!

I have a problem with routing. Problem causes time to time and not persistent. After "ifdown eth0; ifup eth0" all working well, but this solution is wery bad.

ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:15:5d:01:fb:18
          inet addr:10.0.1.11  Bcast:10.0.3.255  Mask:255.255.252.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:476039676 errors:0 dropped:1209857 overruns:0 frame:0
          TX packets:133004681 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:59099091987 (59.0 GB)  TX bytes:53174116756 (53.1 GB)


eth1      Link encap:Ethernet  HWaddr 00:15:5d:01:fb:19
          inet addr:192.168.25.16  Bcast:192.168.25.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:55441017 errors:0 dropped:1248533 overruns:0 frame:0
          TX packets:53845813 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:11819863762 (11.8 GB)  TX bytes:11662822373 (11.6 GB)


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:4925085 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4925085 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1039728720 (1.0 GB)  TX bytes:1039728720 (1.0 GB)

```


netstat -rn:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         10.0.1.152      0.0.0.0         UG        0 0          0 eth0
10.0.0.0        0.0.0.0         255.255.252.0   U         0 0          0 eth0
91.224.126.12   192.168.25.2    255.255.255.255 UGH       0 0          0 eth1
192.168.1.0     10.0.1.152      255.255.255.0   UG        0 0          0 eth0
192.168.25.0    0.0.0.0         255.255.255.0   U         0 0          0 eth1

```


Sometime, after some host (one or more) on 192.168.1.0/24 network was unreachable then comes online again, i can not connect to this host. Pakets goes to lo interface but not to def. gateway.
In current case problem with remote IP: 192.168.1.81, 192.168.1.102, 192.168.1.104. Other IP in network 192.168.1.0/24 accessible. 


tcpdump -nni lo icmp
```
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on lo, link-type EN10MB (Ethernet), capture size 65535 bytes
11:39:37.506353 IP 10.0.1.11 > 10.0.1.11: ICMP host 192.168.1.81 unreachable, length 556
11:39:37.506367 IP 10.0.1.11 > 10.0.1.11: ICMP host 192.168.1.81 unreachable, length 556
11:39:37.506377 IP 10.0.1.11 > 10.0.1.11: ICMP host 192.168.1.102 unreachable, length 556
11:39:37.506386 IP 10.0.1.11 > 10.0.1.11: ICMP host 192.168.1.81 unreachable, length 556
11:39:41.003423 IP 10.0.1.11 > 10.0.1.11: ICMP host 192.168.1.81 unreachable, length 556
11:39:44.998238 IP 10.0.1.11 > 10.0.1.11: ICMP host 192.168.1.81 unreachable, length 556
11:39:49.002187 IP 10.0.1.11 > 10.0.1.11: ICMP host 192.168.1.81 unreachable, length 556
11:39:52.306180 IP 10.0.1.11 > 10.0.1.11: ICMP host 192.168.1.104 unreachable, length 556
11:39:52.306196 IP 10.0.1.11 > 10.0.1.11: ICMP host 192.168.1.104 unreachable, length 556
11:39:52.306207 IP 10.0.1.11 > 10.0.1.11: ICMP host 192.168.1.81 unreachable, length 556
11:39:52.306217 IP 10.0.1.11 > 10.0.1.11: ICMP host 192.168.1.104 unreachable, length 556

```


tcpdump -i eth0 host 192.168.1.102 (not worked)
```
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 65535 bytes
11:53:54.118841 IP 192.168.1.102.sip > pbx.myHost.sip: SIP, length: 532
11:53:54.618236 IP 192.168.1.102.sip > pbx.myHost.sip: SIP, length: 532
11:53:55.654417 IP 192.168.1.102.sip > pbx.myHost.sip: SIP, length: 532
11:53:57.641952 IP 192.168.1.102.sip > pbx.myHost.sip: SIP, length: 532
11:54:01.619298 IP 192.168.1.102.sip > pbx.myHost.sip: SIP, length: 532
```


tcpdump -i eth0 host 192.168.1.103 (worked):
```
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 65535 bytes
11:57:19.529349 IP pbx.myHost.sip > 192.168.1.103.sip: SIP, length: 521
11:57:19.618438 IP 192.168.1.103.sip > pbx.myHost.sip: SIP, length: 407
11:57:29.621217 IP pbx.myHost.sip > 192.168.1.103.sip: SIP, length: 521
11:57:29.708995 IP 192.168.1.103.sip > pbx.myHost.sip: SIP, length: 407
```

---

### Post by The Cog on 2015-08-28
using the -n flag on tcpdump would help. I have no idea what address pbx.myHost.sip is.

The packets you see on the loopback interface are just ICMP destination unreachable messages. This is your PC telling itself that it cannot reach the destination address. I don't think you should worry about these messages. They do suggest that either the default route has disappeared or it has lost the ARP (IP->MAC address lookup) entry for the default gateway though.

When the problem next occurs, can you capture the routing table, the arp table and do a trace of eth0 for a short while:
```
route -n
arp -n
tcpdump -np -e -i eth0
```

---

### Post by SeijiSensei on 2015-08-28
Are you adding the route for 192.168.1.0/24 manually?  If so, don't.  Your routing table says that 10.0.1.152 is the gateway for that network as well as being the default gateway.  So without a specific route for 192.168.1.0/24, traffic for that network will be sent to the default gateway like all other traffic.

---

### Post by spam-accepter on 2015-08-31
> **The Cog said:**
> using the -n flag on tcpdump would help. I have no idea what address pbx.myHost.sip is.

The packets you see on the loopback interface are just ICMP destination unreachable messages. This is your PC telling itself that it cannot reach the destination address. I don't think you should worry about these messages. They do suggest that either the default route has disappeared or it has lost the ARP (IP->MAC address lookup) entry for the default gateway though.

When the problem next occurs, can you capture the routing table, the arp table and do a trace of eth0 for a short while:
```
route -n
arp -n
tcpdump -np -e -i eth0
```

I can mistake, but arp table does not contain MAC that plased into non-local network. Rigth?


> **SeijiSensei said:**
> Are you adding the route for 192.168.1.0/24 manually? If so, don't. Your routing table says that 10.0.1.152 is the gateway for that network as well as being the default gateway. So without a specific route for 192.168.1.0/24, traffic for that network will be sent to the default gateway like all other traffic.

Yes. Route for route for 192.168.1.0/24 added manually. It was experiment.

---

### Post by SeijiSensei on 2015-08-31
Maybe the problem is on the other side, with the route for packets from 192.168.1.0/24 back to 10.0.1.0/24 not set up correctly on the router(s) handling traffic for the 192.168 subnet.

---

