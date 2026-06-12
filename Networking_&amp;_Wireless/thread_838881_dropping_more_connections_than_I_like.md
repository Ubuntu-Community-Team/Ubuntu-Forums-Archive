---
title: "dropping more connections than I like"
date: 2008-06-23
forum: Networking &amp; Wireless
---

### Post by scholzilla on 2008-06-23
I'm connecting fine, but drop connections more often than I'd like to, even though network manager shows a good signal strength. I'm running realtek's 8187L chipset on a 32bit hardy box. 

A few outputs that might be useful:

from iwconfig

```
wlan0     IEEE 802.11g  ESSID:"TOOLEY'S "  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:17:3F:DF:E6:C7   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=60/64  Signal level=52/65  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```


from ifconfig:

```
wlan0     Link encap:Ethernet  HWaddr 00:c0:a8:d8:96:a1  
          inet addr:192.168.2.5  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:a8ff:fed8:96a1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7860 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7649 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7839466 (7.4 MB)  TX bytes:1469975 (1.4 MB)
```

Any thoughts?

---

