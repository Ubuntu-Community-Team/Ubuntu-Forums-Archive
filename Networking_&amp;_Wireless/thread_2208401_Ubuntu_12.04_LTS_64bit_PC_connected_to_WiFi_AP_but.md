---
title: "Ubuntu 12.04 LTS 64bit PC connected to WiFi AP but no internet"
date: 2014-02-28
forum: Networking &amp; Wireless
---

### Post by galapogos on 2014-02-28
[COLOR=#333333][FONT=UbuntuRegular]I'm getting intermittent problems with internet access on my Ubuntu 12.04 LTS desktop when connected to my Prolink Wifi router. I have Android devices connected to the same router that are working fine so I know the router isn't the problem.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]While connected, I'm able to ping my own IP address as well as 127.0.0.1, but I'm unable to ping other devices in the same network, nor are other devices able to ping me. I'm also unable to ping 8.8.8.8.

Strangely, I have another Linksys WiFi AP that's connected to the Prolink AP, and when my PC is connected to the Linksys AP it's able to access the internet and ping other devices in the same network just fine.

My ifconfig output looks like this:
[/FONT][/COLOR]```
&#8203;lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4293 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4293 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:340380 (340.3 KB)  TX bytes:340380 (340.3 KB)


vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:192.168.208.1  Bcast:192.168.208.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:316 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:192.168.104.1  Bcast:192.168.104.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:319 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlan1     Link encap:Ethernet  HWaddr a0:f3:c1:24:17:33  
          inet addr:192.168.100.105  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::a2f3:c1ff:fe24:1733/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:84931 errors:0 dropped:0 overruns:0 frame:0
          TX packets:79162 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:79697850 (79.6 MB)  TX bytes:16584602 (16.5 MB)

```

My IP routing table looks like this:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.100.2   0.0.0.0         UG    0      0        0 wlan1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan1
192.168.100.0   0.0.0.0         255.255.255.0   U     2      0        0 wlan1
192.168.104.0   0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
192.168.208.0   0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
```
[COLOR=#333333][FONT=UbuntuRegular]
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Any idea how I can fix this problem?[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Thanks.[/FONT][/COLOR]

---

### Post by galapogos on 2014-03-02
Anyone?

---

