---
title: "How can i make the networkmanager stops with DHCP?"
date: 2008-11-17
forum: Networking &amp; Wireless
---

### Post by _Seven_ on 2008-11-17
Hi guys.

Well i have the version 8.10 installed on a computer in my University. The strange is when i turn on my pc i have internet for a while but within an hour i lose it without reason. If a do a **ifconfig** with internet, i have this output:

eth0      Link encap:Ethernet  HWaddr 00:19:99:47:5d:04  
          inet addr:10.231.1.113  Bcast:10.231.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:303 errors:0 dropped:0 overruns:0 frame:0
          TX packets:217 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:325149 (325.1 KB)  TX bytes:20785 (20.7 KB)
          Memory:d0020000-d0040000 

and in my resolv.conf file is written this:
domain deec.uc.pt
search deec.uc.pt
nameserver 10.10.0.1
nameserver 10.10.0.1

when i lose the internet, i type the same comand i have this output:
eth0      Link encap:Ethernet  HWaddr 00:19:99:47:5d:04 
          inet addr:192.168.1.66  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:99ff:fe47:5d04/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25651 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17066 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:11747711 (11.7 MB)  TX bytes:2212033 (2.2 MB)
          Memory:d0020000-d0040000

My resolv.conf changes too to other configurations.

Well i think that is the networkmanager that is automatically changing the ip, dns, mask and all this things. I tried to fix the DNS and domain search in the network configuration but the problem continues. 

There is a solution to this? Can i make the networkmanager only search for new configurations manually?

Thank you guys.

---

