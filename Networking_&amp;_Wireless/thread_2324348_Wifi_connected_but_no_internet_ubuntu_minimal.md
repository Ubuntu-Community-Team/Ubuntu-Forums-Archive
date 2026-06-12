---
title: "Wifi connected but no internet ubuntu minimal"
date: 2016-05-13
forum: Networking &amp; Wireless
---

### Post by vasu-agrawal on 2016-05-13
I'm using an ubuntu minimal 16.04 install. I've installed XFCE and network manager, and used XFCE's network manager plugin to connect to a wifi network. I'm able to connect to it, but I'm unable to actually browse the internet or ping anything when on wifi network. The ethernet link works fine when plugged in. Below I've pasted some outputs from various commands which I've seen to be frequently requested, I can paste anything else if necessary. What do I need to do to get wifi to work properly?

```
$ ifconfig
enp9s0    Link encap:Ethernet  HWaddr f8:a9:63:32:45:cd  
          inet addr:192.168.1.23  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::faa9:63ff:fe32:45cd/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:36264 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13049 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:51832461 (51.8 MB)  TX bytes:1086600 (1.0 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:352 errors:0 dropped:0 overruns:0 frame:0
          TX packets:352 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:31578 (31.5 KB)  TX bytes:31578 (31.5 KB)

wlp8s0    Link encap:Ethernet  HWaddr a0:88:69:98:2e:39  
          inet addr:192.168.1.22  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::cc2c:d67c:7c63:c7a9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:739 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:193226 (193.2 KB)  TX bytes:1876 (1.8 KB)
```



```

$ iwconfig
enp9s0    no wireless extensions.

wlp8s0    IEEE 802.11abgn  ESSID:"ASUS-2"  
          Mode:Managed  Frequency:5.745 GHz  Access Point: 54:A0:50:D1:4E:CC   
          Bit Rate=433.3 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=63/70  Signal level=-47 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:4   Missed beacon:0

lo        no wireless extensions.




```


```
$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 enp9s0
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlp8s0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 enp9s0
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp8s0
```

---

