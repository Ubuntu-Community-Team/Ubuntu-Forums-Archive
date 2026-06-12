---
title: "eth0 is showing as &quot;unmanaged&quot;"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by Vunutus on 2009-05-06
My network connection works perfectly fine, but it seems to have problems with GUI tools. There's constantly a thing sitting in my notification area showing an X over the network icon. If I click on it it says "Wired network: Device is unmanaged". The network configuration tool shows absolutely nothing, and firestarter says something like "the device is not ready" when I start it up.

I think this all started happening about the time I started messing with my network settings in order to get my virtual box machines to appear as part of my LAN. I followed a guide that I didn't entirely understand (or remember). It ultimately worked, but I'm left with quirks like this.

Here's the output of ifconfig if it will help:

```

br0       Link encap:Ethernet  HWaddr 00:15:f2:60:69:19  
          inet addr:192.168.1.45  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::215:f2ff:fe60:6919/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1347116 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1059258 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1225593735 (1.2 GB)  TX bytes:97926619 (97.9 MB)

eth0      Link encap:Ethernet  HWaddr 00:15:f2:60:69:19  
          inet6 addr: fe80::215:f2ff:fe60:6919/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1347116 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1059258 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1244478862 (1.2 GB)  TX bytes:102238110 (102.2 MB)
          Interrupt:23 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:255212 errors:0 dropped:0 overruns:0 frame:0
          TX packets:255212 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17129487 (17.1 MB)  TX bytes:17129487 (17.1 MB)

vbox0     Link encap:Ethernet  HWaddr 7e:a1:29:fa:ee:fa  
          inet6 addr: fe80::7ca1:29ff:fefa:eefa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:14228 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

---

### Post by cariboo on 2009-05-06
Can you right-click Network Manager and select Edit Connection? If so you can add eth0 to the list to solve your problems?

---

