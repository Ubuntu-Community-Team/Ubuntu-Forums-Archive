---
title: "Task on QUAGGA"
date: 2007-01-03
forum: Networking &amp; Wireless
---

### Post by newbie_capri on 2007-01-03
I am using ubuntu 6.10..and have two NICs on each PC. 
Using QUAGGA 0.99 on both. Now my task is:


Interconnect two computers A and B with two links, configure the cost of 
each link and see if the software can perform routing calculation properly.

For example, if the two links are L1 and L2, by setting the cost of L1 
to 10 and the cost of L2 to 100, the software should be able to choose 
L1 for the packets going from one to the other. Once it is done, try to 
disconnect L1 and see if the system can perform routing recalculation 
and switch to L2.

Use zebra and ospf.

Does anyone have any links or ways to go for it. I am facing difficulty in configuring the daemons.

Any response will be deeply appreciated.

Thank you

---

### Post by newbie_capri on 2007-01-03
I found this link--> but i m having problems in understanding this. Can u help me in stepping on this...

[http://lists.quagga.net/pipermail/quagga-dev/2005-November/003801.html](http://lists.quagga.net/pipermail/quagga-dev/2005-November/003801.html)



I have the problem to get a link between 2 OSPF neighbors, maybe there is any 
idea:

router1:

playground# sh ip ospf interface
eth0 is up
  Internet Address 192.168.20.2/24, Broadcast 192.168.20.255, Area 0.0.0.0
  Router ID 192.168.20.2, Network Type BROADCAST, Cost: 10
  Transmit Delay is 1 sec, State DR, Priority 1
  Designated Router (ID) 192.168.20.2, Interface Address 192.168.20.2
  No backup designated router on this network
  Timer intervals configured, Hello 10, Dead 40, Wait 40, Retransmit 5
    Hello due in 00:00:09
  Neighbor Count is 0, Adjacent neighbor count is 0
eth1 is up
  Internet Address 10.35.42.21/24, Broadcast 10.255.255.255, Area 0.0.0.0
  Router ID 192.168.20.2, Network Type BROADCAST, Cost: 10
  Transmit Delay is 1 sec, State Backup, Priority 1
  Designated Router (ID) 10.35.42.23, Interface Address 10.35.42.23
  Backup Designated Router (ID) 192.168.20.2, Interface Address 10.35.42.21
  Timer intervals configured, Hello 10, Dead 40, Wait 40, Retransmit 5
    Hello due in 00:00:01
  Neighbor Count is 1, Adjacent neighbor count is 1

playground# sh ip ospf neighbor

Neighbor ID     Pri   State           Dead Time   Address         Interface           
RXmtL RqstL DBsmL
10.35.42.23       1   Full/DR         00:00:31    10.35.42.23     
eth1:10.35.42.21     0     0     0

playground# sh ip ospf interface eth0
eth0 is up
  Internet Address 192.168.20.2/24, Broadcast 192.168.20.255, Area 0.0.0.0
  Router ID 192.168.20.2, Network Type BROADCAST, Cost: 10
  Transmit Delay is 1 sec, State DR, Priority 1
  Designated Router (ID) 192.168.20.2, Interface Address 192.168.20.2
  No backup designated router on this network
  Timer intervals configured, Hello 10, Dead 40, Wait 40, Retransmit 5
    Hello due in 00:00:04
  Neighbor Count is 0, Adjacent neighbor count is 0

-----------------------
router 2:

gremlin# sh ip ospf interface
eth0 is up
  ifindex 2, MTU 1500 bytes, BW 0 Kbit   <UP,BROADCAST,RUNNING,MULTICAST>
  OSPF not enabled on this interface
eth1 is up
  ifindex 3, MTU 1500 bytes, BW 0 Kbit   <UP,BROADCAST,RUNNING,MULTICAST>
  Internet Address 192.168.20.1/24, Broadcast 192.168.20.255, Area 0.0.0.0
  Router ID 192.168.20.1, Network Type BROADCAST, Cost: 10
  Transmit Delay is 1 sec, State DR, Priority 1
  Designated Router (ID) 192.168.20.1, Interface Address 192.168.20.1
  No backup designated router on this network
  Multicast group memberships: OSPFAllRouters OSPFDesignatedRouters
  Timer intervals configured, Hello 10, Dead 40, Wait 40, Retransmit 5
    Hello due in 00:00:01
  Neighbor Count is 1, Adjacent neighbor count is 0

gremlin# sh ip ospf neighbor

Neighbor ID     Pri   State           Dead Time   Address         Interface           
RXmtL RqstL DBsmL
192.168.20.2      1   Init/DROther    00:00:34    192.168.20.2    
eth1:192.168.20.1     0     0     0

gremlin# sh ip ospf interface eth1
eth1 is up
  ifindex 3, MTU 1500 bytes, BW 0 Kbit   <UP,BROADCAST,RUNNING,MULTICAST>
  Internet Address 192.168.20.1/24, Broadcast 192.168.20.255, Area 0.0.0.0
  Router ID 192.168.20.1, Network Type BROADCAST, Cost: 10
  Transmit Delay is 1 sec, State DR, Priority 1
  Designated Router (ID) 192.168.20.1, Interface Address 192.168.20.1
  No backup designated router on this network
  Multicast group memberships: OSPFAllRouters OSPFDesignatedRouters
  Timer intervals configured, Hello 10, Dead 40, Wait 40, Retransmit 5
    Hello due in 00:00:05
  Neighbor Count is 1, Adjacent neighbor count is 0

--------
on router1:

playground:~# tethereal -i eth0
Capturing on eth0
  0.000000 192.168.20.2 -> 224.0.0.5    OSPF Hello Packet
  7.762431   10.42.1.65 -> 224.0.0.5    OSPF Hello Packet <= wrong src-ip 
 10.000268 192.168.20.2 -> 224.0.0.5    OSPF Hello Packet
 17.762010   10.42.1.65 -> 224.0.0.5    OSPF Hello Packet
 20.000754 192.168.20.2 -> 224.0.0.5    OSPF Hello Packet
 27.761618   10.42.1.65 -> 224.0.0.5    OSPF Hello Packet

playground:~# tail -f /var/log/quagga/ospfd.log
2005/11/06 13:52:59 OSPF: Packet from [10.42.1.65] received on link eth0 but 
no ospf_interface <= wrong src-ip (192.168.20.1 expected i think)
2005/11/06 13:53:09 OSPF: Packet from [10.42.1.65] received on link eth0 but 
no ospf_interface
2005/11/06 13:53:19 OSPF: Packet from [10.42.1.65] received on link eth0 but 
no ospf_interface
2005/11/06 13:53:29 OSPF: Packet from [10.42.1.65] received on link eth0 but 
no ospf_interface

playground:~# cat /etc/quagga/ospfd.conf
[...]
interface eth0
!
interface eth1
[...]
!
router ospf
 ospf router-id 192.168.20.2
 compatible rfc1583
 redistribute kernel route-map static
 redistribute connected route-map static
 redistribute static route-map static
 passive-interface eth0
 network 10.35.42.0/24 area 0.0.0.0
 network 192.168.20.0/24 area 0.0.0.0
!
access-list static permit 10.42.0.0/16
access-list static permit 10.35.8.0/24
access-list static deny any

playground:~# cat /etc/debian_version
3.1
playground:~# uname -a
Linux playground 2.6.8-1-386 #1 Thu Nov 11 12:18:43 EST 2004 i686 GNU/Linux
playground:~# /usr/lib/quagga/ospfd -v
ospfd version 0.98.3
Copyright 1996-2005 Kunihiro Ishiguro, et al.

-------
on router2:

gremlin:~# tail -f /var/log/quagga/ospfd.log
2005/11/06 04:50:57 OSPF: OSPFd 0.99.1 starting: vty at 2604
2005/11/06 04:50:57 OSPF: interface 192.168.20.1 join AllSPFRouters Multicast 
group.
2005/11/06 04:51:37 OSPF: DR-Election[1st]: Backup 192.168.20.1
2005/11/06 04:51:37 OSPF: DR-Election[1st]: DR     192.168.20.1
2005/11/06 04:51:37 OSPF: DR-Election[2nd]: Backup 0.0.0.0
2005/11/06 04:51:37 OSPF: DR-Election[2nd]: DR     192.168.20.1
2005/11/06 04:51:37 OSPF: interface 192.168.20.1 join AllDRouters Multicast 
group.
2005/11/06 04:56:17 OSPF: DR-Election[1st]: Backup 10.42.1.65
2005/11/06 04:56:17 OSPF: DR-Election[1st]: DR     10.42.1.65
2005/11/06 04:56:17 OSPF: DR-Election[2nd]: Backup 0.0.0.0
2005/11/06 04:56:17 OSPF: DR-Election[2nd]: DR     10.42.1.65

gremlin:~# cat /etc/quagga/ospfd.conf
[...]
interface eth0
!
interface eth1
!
interface eth2
[...]
!
router ospf
 ospf router-id 192.168.20.1
 compatible rfc1583
 passive-interface eth0
 network 10.42.1.65/16 area 0.0.0.0
 network 192.168.20.0/24 area 0.0.0.0

gremlin:~# cat /etc/debian_version
testing/unstable
gremlin:~# uname -a
Linux gremlin 2.6.12-1-686 #1 Tue Sep 27 12:52:50 JST 2005 i686 GNU/Linux
gremlin:~# /usr/lib/quagga/ospfd -v
ospfd version 0.99.1
Copyright 1996-2005 Kunihiro Ishiguro, et al.


Thanks for your help in advance. With kind regards, Jan.
-- 
-----BEGIN GEEK CODE BLOCK-----
Version: 3.12
GIT d-- s+: a- C+++ UL++++ P+ L+++ E- W+++ N+++ o++ K++ w---
O M-- V- PS PE Y++ PGP++ t-- 5 X R tv- b+ DI- D++
G++ e++ h-- r+++ y+++
------END GEEK CODE BLOCK------
-------------- next part --------------
A non-text attachment was scrubbed...
Name: not available
Type: application/pgp-signature
Size: 189 bytes
Desc: not available
Url : [http://lists.quagga.net/pipermail/quagga-dev/attachments/20051106/b7d32ecd/attachment.bin](http://lists.quagga.net/pipermail/quagga-dev/attachments/20051106/b7d32ecd/attachment.bin)

---

### Post by newbie_capri on 2007-01-03
can anyone help me out with some tips and tricks for this task..I am helpless...

---

### Post by loell on 2007-01-04
i don't know if there are quagga routing suite users here, but i'm glad that you're trying :)

have your tried [Open Flexible router]("http://www.vyatta.com/products/")?

---

### Post by newbie_capri on 2007-01-04
but i ve heard and read that QUAGGA is flexible for all different kinds of routing protocols..But I am intrested in implementing the task on this..

anyway thanks for the link..

---

### Post by newbie_capri on 2007-01-05
i am trying to keep this alive so that someone can help me out...

---

### Post by tengprofa on 2007-05-26
i have same problem almost

on old lin. I have kernel route tabel wornig with no problems, but in ubuntu 7.04 I did everything(so I think) same but quagga doesn't work 

I can access internet from the console but when I connect as user to server I can't go to net.

---

