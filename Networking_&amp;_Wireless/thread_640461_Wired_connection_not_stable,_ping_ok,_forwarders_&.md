---
title: "Wired connection not stable, ping ok, forwarders &quot;hangs&quot;..."
date: 2007-12-14
forum: Networking &amp; Wireless
---

### Post by dirkvic on 2007-12-14
I installed Edubuntu yesterday and have not been successful setting up a proper network connection.

After installation I have a wired connection. This works in Vista (dual booted). And I have set up eth0 with DHCP. It seems to be ok, but I can only access a few sites in firefox. Pinging sites seems ok.

When using wget vg.no I get this:
```
--13:29:47--  http://vg.no/
           => `index.html'
Resolving vg.no... 193.69.165.21
Connecting to vg.no|193.69.165.21|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://www.vg.no/ [following]
--13:29:47--  http://www.vg.no/
           => `index.html'
Resolving www.vg.no... 193.69.165.21
Reusing existing connection to vg.no:80.
HTTP request sent, awaiting response...
```
After a while (couple of mins) it times out.

ping:
```
PING vg.no (193.69.165.21) 56(84) bytes of data.
64 bytes from 193.69.165.21: icmp_seq=1 ttl=247 time=11.1 ms
64 bytes from 193.69.165.21: icmp_seq=2 ttl=247 time=55.2 ms
64 bytes from 193.69.165.21: icmp_seq=3 ttl=247 time=11.2 ms
64 bytes from 193.69.165.21: icmp_seq=4 ttl=247 time=11.2 ms
64 bytes from 193.69.165.21: icmp_seq=5 ttl=247 time=11.6 ms
64 bytes from 193.69.165.21: icmp_seq=6 ttl=247 time=11.4 ms
64 bytes from 193.69.165.21: icmp_seq=7 ttl=247 time=11.7 ms
64 bytes from 193.69.165.21: icmp_seq=8 ttl=247 time=11.2 ms
64 bytes from 193.69.165.21: icmp_seq=9 ttl=247 time=117 ms

--- vg.no ping statistics ---
9 packets transmitted, 9 received, 0% packet loss, time 41083ms
rtt min/avg/max/mdev = 11.178/28.022/117.110/34.332 ms
```

ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:A0:D1:CC:3C:19  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:263 errors:95 dropped:0 overruns:0 frame:95
          TX packets:158 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:38105 (37.2 KB)  TX bytes:12208 (11.9 KB)
          Interrupt:21 Base address:0xdead 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:224 (224.0 b)  TX bytes:224 (224.0 b)
```

If anything else is needed to help me with a diagnose, let me know :)

---

