---
title: "Interface seems to be configured correctly but does not respond to packets it RX"
date: 2023-11-09
forum: Networking &amp; Wireless
---

### Post by sdavid5670 on 2023-11-09
Firstly, I am very new to Linux.  I can barely navigate the command line so please be patient with me.

I have a Dell 740 server with Ubuntu 18.04.  I have two NICs cabled to my network switches (10G fiber).  I have configured both interfaces using /etc/network/interfaces (which is what the vendor's installation instructions tell me that I should do).  One interface works perfectly fine.  I can ping it.  It replies.  I see TX and RX in the 'ip -s link' output.  I can ssh to the server using the IP address configured on this interface (which is eth2).

4: eth2: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP mode DEFAULT group default qlen 1000
    link/ether b8:59:9f:b0:9b:b8 brd ff:ff:ff:ff:ff:ff
    RX: bytes  packets  errors  dropped overrun mcast   
    66.9k      880      0       0       0       205     
    TX: bytes  packets  errors  dropped carrier collsns 
    95.3k      589   

The other interface (eth1) is not behaving correctly.  It is configured with an IP address.  It shows state="UP".  The port is up on the switch.  When I fire up a tcpdump for that interface I see a bunch of multicast packets (OSPF, HSRP, etc).  I see ARP but the server doesn't respond to it even though it owns the IP address.  If I program another device on the network with an ARP entry for that mac and then ping the address I receive the ICMP packet (according to tcpdump) but do not reply.  If I try to ping something else on the network the server does not send an ARP request.  

3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether b8:59:9f:39:f1:a1 brd ff:ff:ff:ff:ff:ff
    inet 10.130.233.16/26 brd 10.130.233.63 scope global eth1

3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP mode DEFAULT group default qlen 1000
    link/ether b8:59:9f:39:f1:a1 brd ff:ff:ff:ff:ff:ff promiscuity 0 addrgenmode eui64 numtxqueues 192 numrxqueues 48 gso_max_size 65536 gso_max_segs 65535 
    RX: bytes  packets  errors  dropped overrun mcast   
    52706      540      0       0       0       519     
    TX: bytes  packets  errors  dropped carrier collsns 
    0          0        0       0       0       0       

I have an identical server and it does not have this issue.   I have no idea where to start.  Any suggestions would be greatly appreciated.

---

