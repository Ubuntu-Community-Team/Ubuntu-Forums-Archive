---
title: "Trouble forwarding via static route"
date: 2008-09-01
forum: Networking &amp; Wireless
---

### Post by Zeddy on 2008-09-01
I am scratching my head over this problem:

I have two routers running Ubuntu 8.04
Each router has 3 NICs.

The goal is:  I want hosts on the Eth0 network of both routers to be able to communicate with hosts on the Eth2 network of both routers, via the common 10.210.128.0/24 subnet (Eth1 on both).  But I can't get it working.

Setup:
(All IPs are static)

Router 1
Eth0 10.218.128.1/24
Eth1 10.210.128.1/24
Eth2 10.215.128.1/24

Router 2
Eth0 10.218.129.1/24
Eth1 10.210.128.2/24
Eth2 10.215.129.1/24

The Eth1 networks of each router are connected via a switch.

I have ip_forward turned on.
I have static routes configured:
Router 1
route add -net 10.215.129.0 netmask 255.255.255.0 gw 10.210.128.2 dev eth1

Router 2
route add -net 10.215.128.0 netmask 255.255.255.0 gw 10.210.128.1 dev eth1

If logged in to router 1, I can ping hosts on the 10.215.129.0 network and get a response.
If logged in to router 2, I can ping hosts on the 10.215.128.0 network and get a response.
So static routes are working.

From the 10.218.128.0 network, I can ping hosts on the 10.215.128.1 network and get a response.
From the 10.218.129.0 network, I can ping hosts on the 10.215.129.1 network and get a response.
So forwarding is working.

However, I can not ping hosts on the 10.215.129 network from the 10.218.128 network, (forwarding via the Router1 static route),
nor can I ping hosts on the 10.215.128 network from the 10.218.129 network, (forwarding via the Router2 static route).
The pings time out (I do not get an ICMP network unreachable message)

I can't see where I'm going wrong. 
Do I simply need to add set of return routes?

Thanks

---

### Post by NadmanET on 2008-09-03
I just typed up this big long string about routing statements and how they work because I misread your routing statements earlier.  After a second look at your post I realized what I wrote did not apply so I erased it.  Just know that I typed up like a page and a half for you man!  LOL

Yes, you definitely need return routes.  Traffic has to know how to get there and back.  As it is now 10.215.128.0/24 should be able to talk to 10.215.129.0/24.  You just have to add routes for your 10.218 networks to both routers.  

Let us know how it goes network rockstar!  :guitar:

---

