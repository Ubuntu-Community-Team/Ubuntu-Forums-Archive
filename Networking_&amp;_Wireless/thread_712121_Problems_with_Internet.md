---
title: "Problems with Internet"
date: 2008-03-01
forum: Networking &amp; Wireless
---

### Post by xblaze88 on 2008-03-01
So i recently installed Gutsy on my laptop. It has a Realtek RTL8139/810x Family Fast Ethernet NIC lan card and an Atheros AR5005G Wireless Network Adapter. 

The problem I have is that while my wireless internet works fine, my regular wired internet does not work at all. I am at university and dont really know how exactly the connections are routed. However most people seem to be able to use the internet just fine with ubuntu. The internet works perfectly on my windows boot

When I run ifconfig this is what i get:

```

ath0      Link encap:Ethernet  HWaddr 00:11:F5:FD:FD:67  
          inet6 addr: fe80::211:f5ff:fefd:fd67/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

ath0:avah Link encap:Ethernet  HWaddr 00:11:F5:FD:FD:67  
          inet addr:169.254.10.234  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth0      Link encap:Ethernet  HWaddr 00:A0:D1:35:88:46  
          inet6 addr: fe80::2a0:d1ff:fe35:8846/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:4389 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0xa000 

eth0:avah Link encap:Ethernet  HWaddr 00:A0:D1:35:88:46  
          inet addr:169.254.6.96  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:10 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8055 (7.8 KB)  TX bytes:8055 (7.8 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-11-F5-FD-FD-67-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9600 errors:0 dropped:0 overruns:0 frame:3952
          TX packets:550 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 

```


Further, running dhclient doesnt help either as i get a bunch of messages that end with : "No DHCPOFFERS received".

I dont really know much about networking OR ubuntu, so please provide me with noob help!

Thanks! :)

---

