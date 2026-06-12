---
title: "Strangeness with NIC Bonding"
date: 2016-04-18
forum: Networking &amp; Wireless
---

### Post by adam193 on 2016-04-18
Is 802.3ad bonding broken in Ubuntu?  This was the case on 15.10 and now 16.04

I have some serious strangeness going on. The bond is up and working, but i get errors on boot or when I try to restart networking:

```
&#10095; ping 10.0.2.1 -I bond0 -c2                                                                                                                                                                                                                  root@mynas
PING 10.0.2.1 (10.0.2.1) from 10.0.2.35 bond0: 56(84) bytes of data.
64 bytes from 10.0.2.1: icmp_seq=1 ttl=64 time=0.268 ms
64 bytes from 10.0.2.1: icmp_seq=2 ttl=64 time=0.263 ms


--- 10.0.2.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms


&#10095; cat /proc/net/bonding/bond0                                                                                                                                                                                                                 root@nas
Ethernet Channel Bonding Driver: v3.7.1 (April 27, 2011)


Bonding Mode: IEEE 802.3ad Dynamic link aggregation
Transmit Hash Policy: layer2 (0)
MII Status: up
MII Polling Interval (ms): 100
Up Delay (ms): 100
Down Delay (ms): 100


802.3ad info
LACP rate: fast
Min links: 0
Aggregator selection policy (ad_select): stable
System priority: 65535
System MAC address: XXXXXX
Active Aggregator Info:
    Aggregator ID: 1
    Number of ports: 2
    Actor Key: 9
    Partner Key: 2
    Partner Mac Address: XXXXX
```

As I said, networking is giving an error (the ifup error below is the error that occurs on boot or when networking is restarted):

```

&#10095; ifdown bond0                                                                                                                                                                                                                                root@nas
ifdown: interface bond0 not configured


~
&#10095; ifup bond0                                                                                                                                                                                                                                 
Waiting for a slave to join bond0 (will timeout after 60s)
RTNETLINK answers: File exists
Failed to bring up bond0. 

```

The config is simple:

```

#bond
auto bond0
iface bond0 inet static
metric 200
address 10.0.2.35
netmask 255.255.255.0
mtu 9000
bond-slaves enp4s0 enp5s7


auto enp4s0
iface enp4s0 inet manual
bond-master bond0


auto enp5s7
iface enp5s7 inet manual
bond-master bond0

```

And this stuff passed as modules options. I suspect something goofy is broken with the bonding as I had to put these options here instead of in the interfaces file. Not to mention I had to put the interfaces AFTER the bond or else it's like the options were ignored.

```

options bonding mode=802.3ad miimon=100 lacp_rate=1 updelay=100 downdelay=100 

```

I have a similarly configured CentOS server, and it works perfectly, with all the bonding options in the ethernet config files.

Thanks for any insight.

---

