---
title: "How to connect wifi via command-line"
date: 2017-01-26
forum: Networking &amp; Wireless
---

### Post by spookybathtub on 2017-01-26
I have a machine running Kodi on Ubuntu 14.04.  There is no keyboard or mouse attached, so I want to connect to wifi using ssh.  I've read several guides on this, but it's not working for me.  With both of these methods, I don't see any networks listed

```
$ iwlist wlan0 scan
wlan0     No scan results

$ nmcli dev wifi
SSID                              BSSID               MODE             FREQ       RATE       SIGNAL   SECURITY   ACTIVE 
```

ifconfig doesn't show wlan0 at first, until after I run **sudo ifconfig wlan0 up**:
```
$ ifconfigeth0      Link encap:Ethernet  HWaddr bc:ae:c5:c1:f8:4b  
          inet addr:192.168.3.102  Bcast:192.168.3.255  Mask:255.255.255.0
          inet6 addr: fe80::beae:c5ff:fec1:f84b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13477 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18028 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1938720 (1.9 MB)  TX bytes:11162511 (11.1 MB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:17716 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17716 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1214633 (1.2 MB)  TX bytes:1214633 (1.2 MB)


wlan0     Link encap:Ethernet  HWaddr 48:5d:60:33:03:42  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

---

