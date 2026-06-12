---
title: "Wierd Wlan issue! Connected to router and acccess gateway but cant access internet."
date: 2007-02-06
forum: Networking &amp; Wireless
---

### Post by stormfrog on 2007-02-06
This is my Network (from Laptop1):

(LAPTOP1) <-> (WLAN ROUTER) <-> (GATEWAY SERVER) <-> (INTERNET)
 [works!]             [works!]                       [works!]                    [FAILS]

I have other computers:

Laptop 2: connects in the same way as Laptop1, works perfectly.
Desktop Computer: Wired to the Wlan Router, works perfectly.

With Laptop1 I have complete LAN access, INCLUDING the gateway. In other words, I have succefully connected to the WLAN router - but I cannot reach the internet. If I disable ra0 (my wlan) and start eth0 (my wired connection). Everything works flawless and I can reach the internet.

What is happening here? I am completely and utterly confused!


Some settings:

/etc/network/interfaces
```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:100 errors:0 dropped:0 overruns:0 frame:0
          TX packets:100 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11166 (10.9 KiB)  TX bytes:11166 (10.9 KiB)

ra0       Link encap:Ethernet  HWaddr 00:19:5B:6D:2F:FA  
          inet addr:192.168.1.142  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:5bff:fe6d:2ffa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15086 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2867 errors:0 dropped:0 overruns:0 carrier:0
          collisions:104 txqueuelen:1000 
          RX bytes:1949038 (1.8 MiB)  TX bytes:257564 (251.5 KiB)
          Interrupt:11

```

Kernel IP routing table
```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 ra0

```

cat /etc/resolv.conf 
```

domain mir.fallman.org
nameserver 172.16.3.3

```

rt61sta.dat (RT61 driver settings for my wlan card)
```

[Default]
CountryRegion=0
CountryRegionABand=7
WirelessMode=0
SSID=nethernet
NetworkType=Infra
Channel=0
AuthMode=WPAPSK
EncrypType=TKIP
DefaultKeyID=1
Key1Type=0
Key1Str=0123456789
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=
WPAPSK=secretpassword
TxBurst=0
PktAggregate=0
WmmCapable=0
APSDCapable=0
APSDAC=0;0;0;0
BGProtection=0
IEEE80211H=0
TxRate=0
RTSThreshold=2347
FragThreshold=2346
RoamThreshold=75
PSMode=CAM
TxPreamble=0
FastRoaming=0

```

---

