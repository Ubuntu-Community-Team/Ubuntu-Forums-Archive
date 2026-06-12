---
title: "WiFi and dropped packets"
date: 2006-09-06
forum: Networking &amp; Wireless
---

### Post by Jason Spaceman on 2006-09-06
I finally got my laptop's Intel 3945 wifi card working with Ubuntu and wpa_supplicant.  But I noticed this when I do a 'ifconfig':

```
wlan0     Link encap:Ethernet  HWaddr 00:13:02:1F:CE:1D
          inet addr:192.168.0.6  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:2ff:fe1f:ce1d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:43775 errors:3 dropped:1053 overruns:0 frame:0
          TX packets:7834 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:5396016 (5.1 MiB)  TX bytes:1360248 (1.2 MiB)
          Interrupt:169 Base address:0xe000 Memory:d4000000-d4000fff
```

I notice, on the RX packets section, that I get errors and dropped packets.  Is this normal for wifi?  Or is there some problem that I don't know about?  My wifi is working fine, web pages are downloading well, etc.  I haven't really tested it yet by doing bandwidth intensive stuff, but so far it's been good.

---

