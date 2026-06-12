---
title: "Hundreds of Martians"
date: 2008-06-06
forum: Networking &amp; Wireless
---

### Post by DrJohn999 on 2008-06-06
Using Shorewall 4.0.6 -- no problems but rather an observation and a question. This behavior is new after installing Ubuntu server 8.04 and this Perl version of Shorewall.

I see hundreds of martian packets logged from eth0 (external interface, fixed IP), one almost exactly every nine minutes, or around 150/day. They all come from aaa.bbb.ccc.255, where my fixed IP on eth0 is aaa.bbb.ccc.170. It's as if someone (the ISP? e.g. Verizon FIOS) is scanning continuously through the entire subnet. They seem harmless enough.

Is there any good reason not to set logmartians=0 in /etc/shorewall/interfaces? Route filtering is enabled here:

```
root@K8NLR6:/proc/sys/net/ipv4/conf/eth0# cat rp_filter
1
```

The result for /etc/shorewall/interfaces would be:

```
#ZONE   INTERFACE       BROADCAST       OPTIONS
net     eth0            detect          dhcp,tcpflags,routefilter,nosmurfs,logmartians=0,blacklist
loc     eth1            detect          dhcp,tcpflags,detectnets,nosmurfs

```

and all those little guys would be silenced!

Thanks,

Dr John

---

### Post by DrJohn999 on 2009-12-29
They're baaaack... after 18 months.

Same behavior -- hundreds of martian packets logged in shorewall daily, with dest to the fixed IP wan nic on my server and source from the mac of the ISP's gateway address, but with an IP address ending in .255. 

```
1 Time(s): [559538.066706] martian source aaa.bbb.ccc.ddd from aaa.bbb.ccc.255, on dev eth0
 1 Time(s): [559538.066710] ll header: [eth0 mac]:[ISP mac]:08:00
```

I haven't tried sniffing out the rest of it -- might be interesting.

The ISP's mac is from ```
arp -a
``` It's definitely their gateway server.

The only recent change on my side would be connecting a DLink WAN - LAN firewall / router (actually the one that the ISP supplied originally) at the WAN IP address adjacent to the server's, to establish an internal isolated subnet on it's own WAN IP.

It's not really a problem but more of an irritation that raises questions: why and what are they doing? Are they trying to ascertain which IP addresses are in use in the fixed IP block I lease, by eliciting a response from the DLink that's running their firmware version? (Just A Theory).

---

