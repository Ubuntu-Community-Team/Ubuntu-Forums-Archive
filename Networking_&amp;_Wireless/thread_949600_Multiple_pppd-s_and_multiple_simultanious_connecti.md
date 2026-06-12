---
title: "Multiple pppd-s and multiple simultanious connections"
date: 2008-10-16
forum: Networking &amp; Wireless
---

### Post by DataMatrix on 2008-10-16
I have the following issue: I a server machine running apache2.2.x, php5, vsftpd, teamspeak, etc.
Currently i have only one ISP connection on Eth1 via PPPOE. A friend of mine requires a bandwidth consuming connection and I intend to get a second ISP connection on Eth0 (don't ask why Eth0 is sitting non-connected, ubuntu just arranged them that way by itself on installation). I also have a subnetwork connected to Eth2 (has static ip). The second ISP connection will be used by an apache2 virtual host (the same apache will still using the other connection, but i think i can handle apache's config). My question is: can I have 2 pppd daemons to maintain 2 pppoe connections. Eth1 will still remain the default route. Here is ifconfig dump:
```
datamatrix@pripyat:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:e0:4c:23:d7:06  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
<statistics omitted><new ISP must go here>
          Interrupt:20 Base address:0xe400 

eth1      Link encap:Ethernet  HWaddr 00:19:e0:13:c6:24  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
<statistics omitted><current ISP>
          Interrupt:19 Base address:0xe800 

eth2      Link encap:Ethernet  HWaddr 00:1a:92:5b:c3:12  
          inet addr:192.168.10.1  Bcast:192.168.10.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
<statistics omitted><subnetwork>

eth1:avahi Link encap:Ethernet  HWaddr 00:19:e0:13:c6:24  
          inet addr:169.254.5.223  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:19 Base address:0xe800 

lo        Link encap:Local Loopback            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
<statistics omitted>

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:78.142.62.79  P-t-P:78.142.60.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
<statistics omitted>

```

Here is also "ip r" dump:
```
datamatrix@pripyat:~$ ip r
78.142.60.1 dev ppp0  proto kernel  scope link  src 78.142.62.79 
192.168.10.0/24 dev eth2  proto kernel  scope link  src 192.168.10.1 
169.254.0.0/16 dev eth1  proto kernel  scope link  src 169.254.5.223 
169.254.0.0/16 dev eth2  scope link  metric 1000 
default dev ppp0  scope link 
default dev eth1  scope link  metric 1000 

```

```
datamatrix@pripyat:~$ uname -a
Linux pripyat 2.6.24-21-generic #1 SMP Mon Aug 25 17:32:09 UTC 2008 i686 GNU/Linux
```

Note: I used pppoeconf to configure the pppoe connection the first time. I took a look on the files in /etc/ppp and I understood most of them (chap_secrets, pap_secrets, options, pppoe_on_boot, resolv/), but I still remain confused on how to have multiple pppd daemons without trashing the current configuration (i mean i want just to add the new connection and keep the previous functionality untouched).

PS(edit): what i think i should to is to make a copy of /etc/ppp/peers/dsl-provider to /etc/ppp/peers/dsl-provider-isp2 and add [exec pppd call dsl-provider-isp2] to /etc/ppp/pppoe_on_boot

I hope I have been desriptive enought. :( :confused:

---

