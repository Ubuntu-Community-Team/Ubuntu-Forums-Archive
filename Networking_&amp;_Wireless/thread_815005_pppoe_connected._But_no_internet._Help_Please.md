---
title: "pppoe connected. But no internet. Help Please"
date: 2008-06-01
forum: Networking &amp; Wireless
---

### Post by nkataria on 2008-06-01
I am using UBUNTU operating system along with windows XP in my PC. I was using 'pppoeconf' in UBUNTU to connect to Internet through my ISP. But recently(2 months by now) Internet access through the same utility has stopped in Ubuntu. I am able to connect to my ISP, but not able to surf Internet. When I connect to net(using pon dsl-provider command), and give 'ifconfig' command, I see the following output ::
------------------------------------------------------------
ppp0      Link encap:Point-to-Point Protocol
          inet addr:221.128.197.90  P-t-P:202.63.173.66  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:289 errors:0 dropped:0 overruns:0 frame:0
          TX packets:397 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:222814 (217.5 KiB)  TX bytes:38245 (37.3 KiB)
------------------------------------------------------------
I able to connect to my ISP website by giving its IP address (202.63.173.66). But when I give any other site's address (eg. [www.yahoo.com](www.yahoo.com)), the browser status bar shows 'looking for ...', and no data is received. I also tried to ping DNS server(in /etc/resolve.conf file), and other sites's IP address (Google's IP address --> 64.233.167.99), but it fails.
I am able to connect to the internet successfully in Windows XP on the same PC. 
Two of my friends having connection of the same ISP and using Linux OS is also facing the same problem.
Can you help us ?

The output of various commands on Ubuntu is appended as below ::

1. sudo ifconfig
---------------------------------------------------------------------
eth0      Link encap:Ethernet  HWaddr 00:30:F1:4D:96:AC  
          inet addr:10.10.146.206  Bcast:10.10.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2906572 errors:0 dropped:0 overruns:0 frame:0
          TX packets:129740 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:584754941 (557.6 MiB)  TX bytes:19303851 (18.4 MiB)
          Interrupt:209 Base address:0xcc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1156 (1.1 KiB)  TX bytes:1156 (1.1 KiB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:221.128.197.43  P-t-P:202.63.173.66  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:304 errors:0 dropped:0 overruns:0 frame:0
          TX packets:362 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:254099 (248.1 KiB)  TX bytes:34781 (33.9 KiB)
-----------------------------------------------------------------------------

2. sudo ip a
-----------------------------------------------------------------------------
1: lo: <LOOPBACK,UP> mtu 16436 qdisc noqueue 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
2: eth0: <BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:30:f1:4d:96:ac brd ff:ff:ff:ff:ff:ff
    inet 10.10.146.206/16 brd 10.10.255.255 scope global eth0
4: ppp0: <POINTOPOINT,MULTICAST,NOARP,UP> mtu 1492 qdisc pfifo_fast qlen 3
    link/ppp 
    inet 221.128.197.43 peer 202.63.173.66/32 scope global ppp0
-------------------------------------------------------------------------------

3. sudo ip route 
--------------------------------------------------------------------------------
202.63.173.66 dev ppp0  proto kernel  scope link  src 221.128.197.43 
10.10.0.0/16 dev eth0  proto kernel  scope link  src 10.10.146.206 
default dev ppp0  scope link 
---------------------------------------------------------------------------------

4. sudo plog
----------------------------------------------------------------------------------
Jun  1 18:49:54 nk pppd[4955]: CHAP authentication succeeded: Welcome to XXXX.
Jun  1 18:49:54 nk pppd[4955]: CHAP authentication succeeded
Jun  1 18:49:54 nk pppd[4955]: peer from calling number 00:11:11:7D:DF:31 authorized
Jun  1 18:49:54 nk pppd[4955]: Cannot determine ethernet address for proxy ARP
Jun  1 18:49:54 nk pppd[4955]: local  IP address 221.128.197.43
Jun  1 18:49:54 nk pppd[4955]: remote IP address 202.63.173.66
Jun  1 18:49:54 nk pppd[4955]: primary   DNS address 202.63.164.17
Jun  1 18:49:54 nk pppd[4955]: secondary DNS address 202.63.164.18
--------------------------------------------------------------------------------------

5. sudo route -n
-------------------------------------------------------------------------------------
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
202.63.173.66   0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
10.10.0.0       0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0
---------------------------------------------------------------------------------------

- Navneet Kataria

---

### Post by nkataria on 2008-06-03
Any Body wanna help me ??
:confused:

---

