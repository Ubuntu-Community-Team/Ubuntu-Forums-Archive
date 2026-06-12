---
title: "2 network-cards, problems with routing ?"
date: 2008-11-01
forum: Networking &amp; Wireless
---

### Post by GoldWing on 2008-11-01
Hi,


I have an ubuntu-server with 2 network cards and both connected to the same switch.
I want to use the server to install vmware-server (it actually works great already).
I want to do an apt-get update, but he cannot connect to the servers. The resolving seems ok, but he doesn't download anything.
Same counts for wget ...

I've done a standard setup with 2 static IP's.


root@oliware-server:/etc/network# route  -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.16.208.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
192.168.10.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.10.0    0.0.0.0         255.255.255.0   U     0      0        0 eth1
172.16.174.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
0.0.0.0         192.168.10.1    0.0.0.0         UG    100    0        0 eth1
0.0.0.0         192.168.10.1    0.0.0.0         UG    100    0        0 eth0
root@oliware-server:/etc/network# ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:22:64:16:f8:ef  
          inet addr:192.168.10.100  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::222:64ff:fe16:f8ef/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:820946 errors:0 dropped:0 overruns:0 frame:0
          TX packets:508904 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:1115722350 (1.1 GB)  TX bytes:85926637 (85.9 MB)
          Memory:f3000000-f3020000 

root@oliware-server:/etc/network# ifconfig eth1
eth1      Link encap:Ethernet  HWaddr 00:50:fc:ee:f8:6b  
          inet addr:192.168.10.101  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::250:fcff:feee:f86b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:370124 errors:0 dropped:0 overruns:0 frame:0
          TX packets:300367 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:322309683 (322.3 MB)  TX bytes:164196728 (164.1 MB)
          Interrupt:20 Base address:0x1100 
root@oliware-server:/etc/network# cat /etc/resolv.conf 
nameserver 192.168.10.1


What did I forget ?

---

### Post by GoldWing on 2008-11-02
ok, solved, you can never have 2 standard gateways.
removed 1 gateway from the interfaces file.

---

