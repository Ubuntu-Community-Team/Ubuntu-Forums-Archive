---
title: "openvpn routing issues"
date: 2008-07-10
forum: Networking &amp; Wireless
---

### Post by azelter on 2008-07-10
I have set up a VPN between two computers on 2 different networks. One computer, the VPN client, is my home computer, which is behind a router and has an internal IP address of 192.168.1.99 (router is .1) the other is external to my home network and has a real IP address - lets call it aaa.bbb.ccc.50 (its default gateway is aaa.bbb.ccc.100 - both are real IP addresses).
My home computer has 2 network interfaces. eth0 and eth1. eth1 is attached to my home router and has the IP 192.168.1.99. eth0 is configured as 10.8.16.1 but could be changed to anything.
The openvpn IP address for my home computer is 10.9.8.2 and the external computer's VPN IP address is 10.9.8.1. Both have the virtual interface tun0.
With the setup I have so far I can ping 10.9.8.1 from 10.9.8.2 and viceversa.
My problem lies in that what I want to setup - is a route to the outside world wide web *through* the vpn for an additional computer attached to eth0 of my home computer via a crossover cable.
I don't care if the vpn client can access the vpn at all. I want eth0 to be plugged in to the additional computer and to forward all internet requests from the additional computer through the VPN to the real world. Thus my home computer would essentially be a router for this additional computer - but would route everything through the VPN (10.9.8.0) not through my home network (192.168.1.0).
With this I am stuck.
I configured eth0 with an IP address of 10.8.16.1 and gave the internet device of the additional computer I want to be routed through the VPN an IP address of 10.8.16.2. Both could ping each other. I did sysctl -w net.ipv4.ip_forward=1 for both the home computer and the remote VPN server. I then did /sbin/iptables -t nat -A POSTROUTING -s 10.8.16.0/24 -o tun0 -j MASQUERADE in the hopes that that would cause my home computer to catch packets coming from eth0 (10.8.16.2 - the laptop I'm plugging in) and send them over the VPN (tun0). I then did /sbin/iptables -t nat -A POSTROUTING -s 10.9.8.0/24 -o eth0 -j MASQUERADE on the VPN server in the hopes that the VPN server would then forward those packets to the real world. This does not work. I get no ability to connect to the web from the additional computer 10.8.16.2 in this way. I have played around adding various different namesrvers/and routes to the setup but have not come upon a combination that works and I'm rather stuck. I think what I am missing are the right route commands, but am not sure what I'm doing wrong. I included an attachment of the setup I am trying to achieve and would be very grateful if anyone has any ideas where I'm going wrong or things I have missed (like the proper route commands). Ideas how to get the same result through bridging or some other method would also be gratefully accepted.
Thanks!

---

### Post by azelter on 2008-07-11
I suppose the post above was too complex. Perhaps someone can answer this question.

If I have a computer with a default gateway of 10.8.16.1 and it sends a packet to an external IP address it should get sent to 10.8.16.1 first right? Then if 10.8.16.1 has an iptables rule that says:
iptables -t nat -A POSTROUTING -s 10.8.16.0/24 -o tun+ -j MASQUERADE
this computer should send that packet out over all it's configured tun interfaces right? And if that computer is has an openvpn tun0 IP number of 10.9.8.2 which points to 10.9.8.1 in it's routing table like so:

10.9.8.1     0.0.0.0         255.255.255.255     UH    0   0   0     tun0

then that packet should reach 10.9.8.1 right? And if the 10.9.8.1 computer has an iptables rule that says:
iptables -t nat -A POSTROUTING -s 10.9.8.0/24 -o eth0 -j MASQUERADE
shouldn't that computer then forward the packet out to the real world via eth0?

---

