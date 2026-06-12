---
title: "Two ethernet devices working simultaneously."
date: 2017-03-24
forum: Networking &amp; Wireless
---

### Post by 1nkmed on 2017-03-24
Hi all, this is my first post and I'm a Ubuntu newb... Be gentle!

SO... I have 3 network adapters... ethernet 1  (enp0s25 - onboard)  ethernet 2 (enx5882a88cf327 - USB adapter and crossover cable to Win10 machine) and WiFi (wlo1) 

I want to either connect to the internet through ethernet1 or WiFi and I want to run VNC over crossover to access headless win10 machine at the same time.

I can get internet access over ethernet1 and Wifi and I can get the VNC server/viewer connected over the crossover, but I cannot get them all working at the same time. If the internet connection is enabled, I cant connect VNC. I have to disconnect VNC to get internet access again... I have tried various things and have been googling vigorously.. please help


```
ink@Inklap:~$  cat /var/lib/NetworkManager/NetworkManager.state
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
ink@Inklap:~$ ifconfig
enp0s25   Link encap:Ethernet  HWaddr a0:b3:cc:27:e7:f6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:d4400000-d4420000 


enx5882a88cf327 Link encap:Ethernet  HWaddr 58:82:a8:8c:f3:27  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:529 errors:0 dropped:3 overruns:0 frame:0
          TX packets:259 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:90218 (90.2 KB)  TX bytes:31202 (31.2 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:3191 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3191 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:230415 (230.4 KB)  TX bytes:230415 (230.4 KB)


vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:172.16.53.1  Bcast:172.16.53.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:581 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:172.16.239.1  Bcast:172.16.239.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:580 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlo1      Link encap:Ethernet  HWaddr 60:67:20:27:36:88  
          inet addr:192.168.1.71  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::9c75:ec49:8a89:79fc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2736813 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1433682 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4098910560 (4.0 GB)  TX bytes:138800860 (138.8 MB)

```

---

### Post by TheFu on 2017-03-26
Sounds like a routing issue.  Please post your routing table.
**$ route**

---

