---
title: "lost broadband access"
date: 2008-05-29
forum: Networking &amp; Wireless
---

### Post by gwman on 2008-05-29
connected for months with Thompson DCM425 modem and Realtek RTL811/8168b card, recently dowloaded 8.04 and still working.  Comcast went dead and now is back up but all I get is 'page not found'.

checked dchp active with adresses, eth1 shows IPv4 with addresses, hardware checker show card good, modem shows active, checked firewall on/off/on.  rebooted with modem off (3 times)to reinstall but didn't resolve issue.

Any ideas about source of problem?

---

### Post by superprash2003 on 2008-05-29
please post ifconfig output .. also try pinging your modem and post output..

---

### Post by gwman on 2008-06-03
eth0      Link encap:Ethernet  HWaddr 00:1a:4d:9b:f3:b7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:220 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:18:f8:0f:5a:19  
          inet addr:98.223.238.163  Bcast:255.255.255.255  Mask:255.255.248.0 
          inet6 addr: fe80::218:f8ff:fe0f:5a19/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:667 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:360 errors:1 dropped:0 overruns:0 carrier:2 
          collisions:0 txqueuelen:1000 
          RX bytes:236574 (231.0 KB)  TX bytes:22490 (21.9 KB) 
          Interrupt:19 Base address:0xd000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:133284 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:133284 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:6672044 (6.3 MB)  TX bytes:6672044 (6.3 MB) 



From 98.223.238.163 icmp_seq=47 Destination Host Unreachable
From 98.223.238.163 icmp_seq=48 Destination Host Unreachable
From 98.223.238.163 icmp_seq=49 Destination Host Unreachable
From 98.223.238.163 icmp_seq=50 Destination Host Unreachable
From 98.223.238.163 icmp_seq=51 Destination Host Unreachable
From 98.223.238.163 icmp_seq=52 Destination Host Unreachable
From 98.223.238.163 icmp_seq=53 Destination Host Unreachable

---

