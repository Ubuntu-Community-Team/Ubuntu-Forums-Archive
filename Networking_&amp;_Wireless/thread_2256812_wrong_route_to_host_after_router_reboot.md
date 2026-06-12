---
title: "wrong route to host after router reboot"
date: 2014-12-14
forum: Networking &amp; Wireless
---

### Post by lars77 on 2014-12-14
Hi. 

I have the following setup:
12.04 server 192.168.1.2, running zoneminder, and constantly downloading from 192.168.2.2 and 192.168.2.3
14.10 server acting as default gateway 192.168.1.1. 
Openwrt router 192.168.1.3, that is the gateway to 192.168.2.0/24 the network.
2 hosts, 192.168.2.2 and 192.168.2.3, dlink cameras.
the 12.04 server has the following routes set up:
default 192.168.1.1
192.168.2.0/24 via 192.168.1.3 dev eth0

The problem:
at start, the setup works perfect. I can ping both 192.168.2.2 and 192.168.2.3, end get responses. 
if I reboot the openwrt router, which I have to do every night because it has a tendency to hang after a couple of days, the following happens:
the router boots, and the 12.04 server can successfully ping either 192.168.2.2 or 192.168.2.3, but not both. Let's assume it is the 192.168.2.2 host, that is not responding in this example. I get no icmp responses, like unreachable. Just 100% lost packages when I ctrl-c.
If I "tcpdump icmp and host 192.168.2.2" on the two gateways and the 12.04 server, the 12.04 server show the icmp packets leaving as I ping. The openwrt router shows no packages, but the 14.10 server, the default route, does. The 14.10 server does however not respond to the pings, and does not redirect anything, although also it knows the route to 192.162.2.0/24. In this case, pinging 192.168.2.3 will show packages on the openwrt router, and not on the default gateway. 
The rest of the network works. The 14.10 server, for example, can ping 192.168.2.2. 
If I reboot the 12.04 server, everything goes back to normal, and it can ping 192.168.2.2 again. 
The routing table of 12.04 server does not change between normal operation, and when stuff stops working.
And it is kind of funny how the problem sort of alternates between the two hosts 192.168.2.3 and 192.168.2.2.
It is kind of like the 12.04 server sets up the default route as the route to one of the hosts when it can't get any responses from the openwrt router. So it ignores the static route for one host, but uses the static route for the other. 

Does anyone understand what's going on, and know a solution?

---

### Post by lars77 on 2014-12-15
Think I found it. My firewall setup on the default gateway was set up to accept icmp on the internal interface, but was told to drop on output. My bad. I imagine this made the gateway into a black hole for icmp packets, confusing everything:) I have fixed it now, and regard it as solved, but wont be testing it until tonight.

---

