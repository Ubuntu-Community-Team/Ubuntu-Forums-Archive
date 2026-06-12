---
title: "Ethernet Problem"
date: 2008-03-06
forum: Networking &amp; Wireless
---

### Post by Nuclear_darkness on 2008-03-06
When i first installed ubuntu the ethernet worked fine, connected automatically as it should, after the first big download of updates it no longer works. It will recognise that the ethernet is plugged in and will connect to a network but it doesnt enable me to use the net.

Wireless does work however.

Results from ifconfig -a

```
eth0      Link encap:Ethernet  HWaddr 00:19:66:31:9D:54  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4321 errors:0 dropped:0 overruns:0 frame:0
          TX packets:541 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1512320 (1.4 MB)  TX bytes:58054 (56.6 KB)
          Interrupt:18 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:865 (865.0 b)  TX bytes:865 (865.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:1B:FC:66:7A:15  
          inet addr:192.168.1.67  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:fcff:fe66:7a15/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:76059 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52133 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:97243174 (92.7 MB)  TX bytes:7211161 (6.8 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1B-FC-66-7A-15-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

Any help is very much appreciated guys.

---

### Post by SpaceTeddy on 2008-03-07
cat you please post content of the file /etc/network/interfaces ?
also, then you have only plugged in the cable network, can you print the output of ifconfig and route -n again (see what the network configuration on the ethernet is set to)

---

