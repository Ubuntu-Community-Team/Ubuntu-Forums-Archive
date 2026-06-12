---
title: "2 ISPS and problems"
date: 2015-06-24
forum: Networking &amp; Wireless
---

### Post by mariusz7 on 2015-06-24
I'm sitting 2 days on this and I have no idea what's wrong. Can you tell mi anything that helps?

Internet:
eth0 - 10.0.0.1 gate 10.0.0.138
eth3 - 89.20.153.60 gate 89.20.153.1 - my new connection

local
eth1 - 192.168.0.1

**default via 10.0.0.138 dev eth0**
      10.0.0.0/24 dev eth0  scope link  src 10.0.0.1
89.20.153.0/26 dev eth3  proto kernel  scope link  src      89.20.153.60
      192.168.0.0/24 dev eth1  scope link  src 192.168.0.1
everything works fine



when I change to:
** default via 89.20.153.1 dev eth3**
     10.0.0.0/24 dev eth0  scope link  src 10.0.0.1
    89.20.153.0/26 dev eth3  proto kernel  scope link  src      89.20.153.60
     192.168.0.0/24 dev eth1  scope link  src 192.168.0.1

everything stops working and packets are sent from 

tcpdump: listening on eth3, link-type EN10MB (Ethernet), capture      size 65535 bytes
        10.0.0.1 > 213.180.141.140: ICMP echo request, id      768, seq 22570, length 40
        10.0.0.1 > 213.180.141.140: ICMP echo request, id      768, seq 22826, length 40
 instead of 89.20.153.60 > 213.180.141.140

I even got something like this:
listening on eth3, link-type EN10MB (Ethernet), capture size      65535 bytes
    22:22:02.223430 IP 89.25.153.60 > 213.180.141.140: ICMP      echo request, id 10398, seq 2, length 64
    22:22:02.244392 IP 213.180.141.140 > 89.25.153.60: ICMP      echo reply, id 10398, seq 2, length 64
    22:22:02.325218 IP 10.0.0.1 > 213.180.141.140: ICMP echo      request, id 768, seq 57898, length 40
    22:22:07.608427 IP 10.0.0.1 > 213.180.141.140: ICMP echo      request, id 768, seq 58154, length 40
    22:22:13.108799 IP 10.0.0.1 > 213.180.141.140: ICMP echo      request, id 768, seq 58410, length 40

from router everything works fine but from eth1 not. 

------------------------------------------------
when I set 2 internet's together:

ip route show table T1
10.0.0.0/24 dev eth0  scope link  src 10.0.0.1
default via 10.0.0.138 dev eth0

ip route show table T2
89.20.153.0/26 dev eth3  scope link  src 89.20.153.60
default via 89.20.153.1 dev eth3

ip route show
89.20.153.0/26 dev eth3  scope link  src 89.20.153.60
10.0.0.0/24 dev eth0  scope link  src 10.0.0.1
192.168.0.0/24 dev eth1  scope link  src 192.168.0.1
192.168.252.0/24 via 192.168.0.100 dev eth1
default
        nexthop via 10.0.0.138  dev eth0 weight 1
nexthop via 89.20.153.1  dev eth3 weight 1

eth1 works for a few minutes (via eth0 and eth3) then DNS is down and on the router there is never connection outside and no DNS. 

------------------------------------------------
Chain POSTROUTING (policy ACCEPT 1704 packets, 133K bytes)
 pkts bytes target     prot opt in     out     source               destination
  965 46420 MASQUERADE  all  --  *      eth0    192.168.0.0/22      !192.168.0.0/22
  489 23536 MASQUERADE  all  --  *      eth3    192.168.0.0/22      !192.168.0.0/22

(tried with SNAT - the same)
 INPUT, OUTPUT, FORWARD - ACCEPT

 I did the same on other router and everything's working great and here it doesn't - any help?

---

### Post by Skaperen on 2015-06-25
*try*: when you switch to 89.20.153.1 disable eth0.

i am guessing because i do not understand your network.

---

### Post by mariusz7 on 2015-06-25
I hoped I explained it :)
I got 2 connections to internet - by eth0 and eth3. Eth1 is a local network. I want to use 2 connections to route internet to everyone in local network. 
When I disable eth0 it is working fine, on eth3. 
Yesterday I maganed to make it working - eth0 and eth3 and everyone in local network have internet but I cannot use internet on the router because it sends packets randomly through eth0 or eth3 and that's why DNS is down and router connection is down. 

My question - by using
iptables -t mangle -A PREROUTING -i eth1 -d 156.154.70.22 -j MARK --set-mark 1
I can manage to any connection FROM LAN (eth1) to 156.154.70.22 goes always via eth0.  
How can I create a iptables rule to set mark 1 on any connection made by router itself? "! -i eth+" didn't work.
I think that would solve my current problem.

---

