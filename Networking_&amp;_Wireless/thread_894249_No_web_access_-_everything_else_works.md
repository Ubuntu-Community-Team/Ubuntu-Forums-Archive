---
title: "No web access - everything else works"
date: 2008-08-19
forum: Networking &amp; Wireless
---

### Post by abadr on 2008-08-19
Hi,

My main Kubuntu desktop has problems accessing the web (wired connection). I get intermittent access that's 80% off. Sometimes it loads the HTML page only and timeout when loading the images and sometimes nothing at all. Once in a blue moon it gets the complete page.

This problem seems to be web access specific. I can access local network shares with no problem and Skype works as well.

This problem is unique to a single computer on my home network which has other clients properly accessing the web  (4 wired computers, 2 wireless devices and a wired set top box). 3com ADSL router and a 3com switch.

I would appreciate it if you could advise me on how to fix this. Thanks

PS: I also have VMware installed on this computer hence the vmnet interfaces.

ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:16:17:be:2c:72
          inet addr:10.0.0.20  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:17ff:febe:2c72/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3283626 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3901865 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:91203211 (86.9 MB)  TX bytes:530964730 (506.3 MB)
          Base address:0xdf00 Memory:fdce0000-fdd00000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:17704 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17704 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:28303776 (26.9 MB)  TX bytes:28303776 (26.9 MB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01
          inet addr:192.168.23.1  Bcast:192.168.23.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1055 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08
          inet addr:192.168.222.1  Bcast:192.168.222.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1056 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

route
```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.23.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
10.0.0.0        0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.222.0   0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         10.0.0.1        0.0.0.0         UG    100    0        0 eth0

```

---

