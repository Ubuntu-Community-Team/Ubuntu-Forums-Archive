---
title: "Wireless USB (Ubuntu 6.10)"
date: 2006-11-28
forum: Networking &amp; Wireless
---

### Post by mjs_sporko on 2006-11-28
Hi,

I've been trying all day to get my wireless dongle working with Ubuntu 6.10, with little success.

My dongle is a Elements CWD-854, which appears to be a cheap version of this [CNet one]("http://www.cnet.com.tw/product/cwd-854d.htm").
It works well in WinXP with the drivers on the CD (rt73.*).

With a fresh install my "System -> Administration -> Networking" shows wlan0 and wmaster0 available.
After setting the ESSID to what Windows says its SSID is (there was no mention of ESSID in Windows), I still can't access the Internet.

Next I tried the "ndiswrapper" method using both WinXP and Win2K drivers that were on the installation CD. Still no action but I must be getting close right?

Any ideas on what to try next?

Here is the output of some commands that might be relavent.

`ifconfig`
```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:486 errors:0 dropped:0 overruns:0 frame:0
          TX packets:486 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:36100 (35.2 KiB)  TX bytes:36100 (35.2 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:08:A1:A0:C7:60  
          inet addr:192.168.1.5  Mask:255.255.255.0
          inet6 addr: fe80::208:a1ff:fea0:c760/64 Scope:Link
          UP RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:576 (576.0 b)
          Base address:0x1000 

wmaster0  Link encap:UNSPEC  HWaddr 00-08-A1-A0-C7-60-00-00-00-00-00-00-00-00-00-00  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0x1000 
```

`iwlist wlan0 scan` (The output alternates between the following two, could this be due to a weak signal?)
```
wlan0     No scan results
```
```
wlan0     Scan completed :
          Cell 01 - Address: 00:14:85:D1:05:C0
                    ESSID:"GIGABYTE"
                    Mode:Master
                    Frequency:2.437 GHz
                    Encryption key:off
                    Extra:tsf=0000003da0e2ad68
```

`lsusb`
```
Bus 003 Device 007: ID 148f:2573 Ralink Technology, Corp. 
Bus 003 Device 003: ID 05e3:0702 Genesys Logic, Inc. USB 2.0 IDE Adapter
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0926:8888  
Bus 001 Device 001: ID 0000:0000
```

`ndiswrapper -l`
```
installed drivers:
rt73		driver installed, hardware (18E8:6196) present
```

Cheers,
Martin.

---

