---
title: "IPv6 MSS set from IPv4 MTU?"
date: 2008-06-19
forum: Networking &amp; Wireless
---

### Post by skyguy on 2008-06-19
While debugging an MSS/MTU problem, I noticed that on Ubuntu 8.04 (kernel 2.6.24-18) the MSS for IPv6 TCP connections was being set to 1440 (correct for an MTU of 1500) but my router on that segment is advertising an MTU of 1466 and so the MSS should be 1406.

My system is picking up the IPv6 MTU on eth0 from the router :
$ sysctl -a|grep mtu
net.ipv4.ip_no_pmtu_disc = 0
net.ipv4.route.mtu_expires = 600
net.ipv4.route.min_pmtu = 552
net.ipv4.tcp_mtu_probing = 0
net.ipv6.route.mtu_expires = 600
net.ipv6.conf.lo.mtu = 16436
net.ipv6.conf.wmaster0.mtu = 1500
net.ipv6.conf.eth1.mtu = 1500
net.ipv6.conf.all.mtu = 1280
net.ipv6.conf.default.mtu = 1280
net.ipv6.conf.eth0.mtu = 1466

but the eth0 interface is using MTU 1500 :
$ ip -6 addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qlen 1000
    inet6 2001:4d48:ad51:21:212:79ff:fec7:3d6/64 scope global dynamic 
       valid_lft 2591747sec preferred_lft 604547sec
    inet6 fe80::212:79ff:fec7:3d6/64 scope link 
       valid_lft forever preferred_lft forever

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:12:79:c7:03:d6  
          inet addr:192.168.1.150  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2001:4d48:ad51:21:212:79ff:fec7:3d6/64 Scope:Global
          inet6 addr: fe80::212:79ff:fec7:3d6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13518 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11375 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2244827 (2.1 MB)  TX bytes:1076071 (1.0 MB)
          Interrupt:22 

This causes a problem trying to browse the web - ISPs seem to block/not-generate the required ICMPv6 "Packet too large" packets, so the sending web server's packets get dropped at the ADSL link and never make it back to the desktop.

Two questions:
1) Is this correct behaviour for the IPv6 TCP stack?
2) Is there a way to set the interface MTU other than by manually configuring it on each desktop machine?

Thanks in advance
-Kevin

---

