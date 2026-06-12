---
title: "Coexistence of iBurst and LAN connection?"
date: 2008-06-17
forum: Networking &amp; Wireless
---

### Post by pnuts2 on 2008-06-17
Hey guys, new to ubuntu here. Can anyone please help me with the following problem?

Currently, I have two ways of connecting to the internet.

1) iburst, via USB modem.
2) college LAN.

I successfully set up the iBurst services using one of the guides on line and it is
working perfectly OK "if I disable the LAN port". Whenever I activate my LAN port all
internet traffic seem to be diverted through the LAN port instead of my activated 
iBurst port.

This is somehow annoying because I have a NAS set up as well and I often need to read
files from it. I would like to do this without allowing internet to go through LAN
since it costs heaps more money than my iBurst. I am able to achieve the following in
windows without any configuration

1) normal internet service via iBurst
2) concurrent access to my NAS via LAN

Can anyone suggest how to fix this problem? Below is the output of my ifconfig

brian@Kurama:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:f2:94:ec:f0  
          inet6 addr: fe80::215:f2ff:fe94:ecf0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15566 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34802 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1545390 (1.4 MB)  TX bytes:114795232 (109.4 MB)
          Interrupt:18 Base address:0xa000 

ib0       Link encap:Ethernet  HWaddr 00:c0:ee:0c:14:71  
          inet6 addr: fe80::2c0:eeff:fe0c:1471/64 Scope:Link
          UP BROADCAST RUNNING NOARP PROMISC DYNAMIC  MTU:1500  Metric:1
          RX packets:189 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9369 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:149760 (146.2 KB)  TX bytes:94399 (92.1 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:900 (900.0 B)  TX bytes:900 (900.0 B)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:125.253.44.206  P-t-P:125.253.44.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1456  Metric:1
          RX packets:170 errors:0 dropped:0 overruns:0 frame:0
          TX packets:185 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:146789 (143.3 KB)  TX bytes:17829 (17.4 KB)

Thanks a lot!

---

