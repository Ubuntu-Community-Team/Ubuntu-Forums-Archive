---
title: "Can't ping router and internal newtork devices"
date: 2008-07-06
forum: Networking &amp; Wireless
---

### Post by el.demiurgo on 2008-07-06
Hi everyone!
I am new in Ubuntu. I like it a lot but I am having some problems with networking.
I can't ping my Xbox, router, Xbox360 or other PC in my network from my wireless adapter. It works from the wired one.



My ifconfig shields:
eth0      Link encap:Ethernet  HWaddr 00:0e:a6:bc:dc:59  
          inet addr:192.168.0.201  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2128 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:133171 (130.0 KB)  TX bytes:133171 (130.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:19:5b:80:03:19  
          inet addr:192.168.0.109  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::219:5bff:fe80:319/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4859 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4897 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2175495 (2.0 MB)  TX bytes:810932 (791.9 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-19-5B-80-03-19-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

I don't have any firewall installed I believe.

Thanks for your help!

---

