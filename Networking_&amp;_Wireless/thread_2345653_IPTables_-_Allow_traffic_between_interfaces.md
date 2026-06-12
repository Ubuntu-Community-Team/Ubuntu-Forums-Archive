---
title: "IPTables - Allow traffic between interfaces"
date: 2016-12-06
forum: Networking &amp; Wireless
---

### Post by 1ontheriver on 2016-12-06
Hello,


 I am a newbie when it comes to Linux so I am hoping the answer is simple here. I am testing VOIP traffic across a wireless mesh network using different routing protocols. For some reason one of the protocols will not route between interfaces on the edge devices. I tried static routing without the protocol and it suffers the same problem. I am assuming there is some security feature that the first two protocols disable that the third does not.

 Topology

 ClientA-----wired------AP01-------wireless-------AP02-----wired------ClientB

 ClientA eth0 - 2002::2/64
 AP01 eth0    - 2002::1/64
 AP01 wlan0   - 2001::1/64
 AP02 wlan0   - 2001::5/64
 AP02 eth0    - 2003::1/64
 ClientB eth0 - 2003::2/64

 Client A default gateway is 2002::1/64
 Client B default gateway is 2003::1/64
 AP01 has a static route to the network 2003::/64 with next hop 2001::5/64
 AP02 has a static route to the network 2002::/64 with next hop 2001::1/64
 Note: This is when I configure it statically. The routing protocol add the routes when I configure it

 ClientA can ping both interfaces of AP01 but no further
 ClientB can ping both interfaces of AP02 but no further
 AP01 can ping Client A and both interfaces of AP02
 AP02 can ping Client B and both interfaces of AP01

 ClientA and ClientB are IBM desktops running Linux
 AP01 and AP02 are Raspberry Pi3 devices running Rasbian Wheezy

 When the mesh is configured using BMX6 or OLSR I can ping end to end.
 When the mesh is configured using Babel or using static routes I hit the problem.

 All devices are configured as dual stack with IPv4 addresses on eth0 used for management traffic. The IPv4 network is a flat network 172.20.20.0/24 which I do not believe should be relevant but I have included it here for completeness.

 I have confirmed that the correct interfaces are being used to reach each network.

Recently I have tried playing with IP6tables and applied the following commands on AP01 and AP02 but it did not fix the problem. I must avoid the use of NAT at all costs.
sudo sysctl -w net.ipv6.conf.all.forwarding=1
sudo sysctl -w net.ipv6.conf.all.proxy_ndp=1
sudo sysctl -w net.ipv6.conf.all.autoconf=0
sudo sysctl -w net.ipv6.conf.all.accept_ra=0
sudo ip6tables -A INPUT -i eth0 -j ACCEPT
sudo ip6tables -A INPUT -i wlan1 -j ACCEPT
sudo ip6tables -A FORWARD -i eth0 -o wlan1 -j ACCEPT
sudo ip6tables -A FORWARD -i wlan1 -o eth0 -j ACCEPT

pi@AP-1:~ $ sudo ip6tables -L -nv
Chain INPUT (policy ACCEPT 364 packets, 42290 bytes)
 pkts bytes target     prot opt in     out     source               destination
Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination
  711 73944 ACCEPT     all      eth0   wlan1   ::/0                 ::/0
    0     0 ACCEPT     all      wlan1  eth0    ::/0                 ::/0
Chain OUTPUT (policy ACCEPT 402 packets, 47473 bytes)
 pkts bytes target     prot opt in     out     source               destination



 Thank you in advance for reading my post and hopefully somebody can help.

---

