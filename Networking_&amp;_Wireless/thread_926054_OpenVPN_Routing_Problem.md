---
title: "OpenVPN Routing Problem"
date: 2008-09-21
forum: Networking &amp; Wireless
---

### Post by iLLiCiTgr on 2008-09-21
Hello guys. I'm having trouble routing openvpn on my server.
I'm currently having several ips on the server on 2 subnets
85.x.x.224/27 from which i own .254
and
78.xx.xx.88/29 from which 89-95 are usable for me.

I have used a subnet of 10.8.1.0 for my openvpn.
I've successfully routed the 78.x subnet so the traffic goes through vpn.
But when ever i am trying to route the 85.x ip, all of my computers traffic stops.

I've tried this on windows clients, on my ubuntu client and still no luck

This is my clients routing

Destination Gateway Genmask Flags Metric Ref Use Iface
10.8.1.5 0.0.0.0 255.255.255.255 UH 0 0 0 tun0
78.xx.xx.88 10.8.1.5 255.255.255.248 UG 0 0 0 tun0
192.168.192.0 0.0.0.0 255.255.255.0 U 0 0 0 br0
10.8.1.0 10.8.1.5 255.255.255.0 UG 0 0 0 tun0
169.254.0.0 0.0.0.0 255.255.0.0 U 1000 0 0 eth0
0.0.0.0 192.168.192.1 0.0.0.0 UG 100 0 0 br0

While on my server the routing goes as this

Destination Gateway Genmask Flags Metric Ref Use Iface
10.8.1.2 0.0.0.0 255.255.255.255 UH 0 0 0 tun0
78.xx.xx.88 0.0.0.0 255.255.255.248 U 0 0 0 eth0
85.xx.xx.224 0.0.0.0 255.255.255.224 U 0 0 0 eth0
10.8.1.0 10.8.1.2 255.255.255.0 UG 0 0 0 tun0
0.0.0.0 85.xx.xx.225 0.0.0.0 UG 100 0 0 eth0
0.0.0.0 85.xx.xx.225 0.0.0.0 UG 100 0 0 eth0
0.0.0.0 85.xx.xx.225 0.0.0.0 UG 100 0 0 eth0
0.0.0.0 85.xx.xx.225 0.0.0.0 UG 100 0 0 eth0
0.0.0.0 85.xx.xx.225 0.0.0.0 UG 100 0 0 eth0
0.0.0.0 85.xx.xx.225 0.0.0.0 UG 100 0 0 eth0

I have tried manually adding route to my ubuntu client

route add -host 85.xx.xx.254 gw 10.8.1.5 netmask 255.255.255.255 metric 0
route add -net 85.xx.xx.224 gw 10.8.1.5 netmask 255.255.255.224 metric 0

and yet, no luck.

I've even tried pushing the route 85.xx.xx.254 255.255.255.255 from the openvpn configuration and again, nothing.

Can anyone help me?

---

### Post by iLLiCiTgr on 2008-09-22
essentially i have added this 2 lines on my server configuration

push "route 78.xx.xx.88 255.255.255.248"
push "route 85.xx.xx.224 255.255.255.224"

while windows validate this routes and i can successfully access 85.xx.xx.254. But from my ubuntu client, when try to access 85.xx.xx.254 or 78.xx.xx.89 non of the traffic goes to either route. i have to mannualy remove the 85.xx.xx.224 route so that i can access 78.xx.xx.89 again.

I really need your help on this guys.
Appreciate it

---

### Post by magicstore on 2008-09-22
Did you try tcpdump -i eth0  and tcpdump -i tun0 on your server ?

Can you see the packets there ?
(what means - routing TO the server works, but not back to the client)

---

### Post by iLLiCiTgr on 2008-09-26
thanks for the info.
I'll check it out tomorrow and see what you've got there

---

### Post by j.bunce on 2008-09-26
> 78.xx.xx.88/29 from which 89-95 are usable for me.

.95 is the broadcast address. You only have 89-94 for hosts on a /29 subnet.

Make sure you're not NAT'ing between the two subnets.

---

