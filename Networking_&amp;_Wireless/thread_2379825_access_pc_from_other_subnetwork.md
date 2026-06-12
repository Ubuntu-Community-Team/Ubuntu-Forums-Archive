---
title: "access pc from other subnetwork"
date: 2017-12-10
forum: Networking &amp; Wireless
---

### Post by marchello_lippi2 on 2017-12-10
Hi all, 

I got two routers, one is uplink for the second. 
Local address of pc connected to the first is 192.168.0.122, other pc is connected to the 2nd router and local address is 192.168.1.37 .
I can ping 192.168.0.122 from 192.168.1.37, 
but I can not ping 192.168.1.37 from 192.168.0.122, this is what I'd like to solve. 
Any suggestions? 
Both pc are under ubuntu if matters.
What additional details should I provide? 
Please advise.

traceroute from 192.168.1.37 to 192.168.0.122
> $ traceroute 192.168.0.122
traceroute to 192.168.0.122 (192.168.0.122), 30 hops max, 60 byte packets
 1  192.168.1.1 (192.168.1.1)  99.758 ms  99.475 ms  99.478 ms
 2  192.168.0.122 (192.168.0.122)  104.967 ms  105.033 ms  105.136 ms

---

### Post by The Cog on 2017-12-10
My immediate thought is wanting to see the routing tables from the command **ip route list**.
Is either router performing NAT?

---

### Post by marchello_lippi2 on 2017-12-10
**The Cog**

192.168.0.122 :
> 
$ ip route list
default via 192.168.0.1 dev enp2s0  proto static  metric 100 
169.254.0.0/16 dev enp2s0  scope link  metric 1000 
192.168.0.0/24 dev enp2s0  proto kernel  scope link  src 192.168.0.122  metric 100


192.168.1.37 :
> $ ip route list
default via 192.168.1.1 dev wlp3s0  proto static  metric 600 
169.254.0.0/16 dev wlp3s0  scope link  metric 1000 
192.168.1.0/24 dev wlp3s0  proto kernel  scope link  src 192.168.1.37  metric 600

>>> Is either router performing NAT?
Well, yes for both of them afaik. Why?

---

### Post by The Cog on 2017-12-10
The routing tables look straightforward. This makes me think firewalling, or something oddhappening in the routers (which brings me back to NAT). NAT behaves much like a firewall, only allowing connections to form in one direction.

I am inclined to use tcpdump on 192.168.0.122 to verify that it sees the pings from 192.168.1.37 as coming from that address (i.e. no NAT between the two PCs). So on 192.168.0.122, run the command 
```
sudo tcpdump -np -i enp2s0 icmp
``` and then do the ping from 192.168.1.37. I would hope to see the packets using the addresses we know are on the PCs.

Assuming that the addresses are as expected, use the above tcpdump command and try to ping 192.168.1.37 from 192.168.0.122. Verify in the tcpdump output that echo request packets are being sent.

Then use the command```
sudo tcpdump -np -i wlp3s0 icmp
``` on 192.168.1.37 and then try to ping it from 192.168.0.122. Verify that the echo requests are in fact delivered, and whether or not the echo reply is being sent.

---

