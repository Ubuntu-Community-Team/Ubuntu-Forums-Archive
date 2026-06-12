---
title: "HP Laptop NC6400 and wireless"
date: 2008-02-17
forum: Networking &amp; Wireless
---

### Post by ed0gg on 2008-02-17
Hello, 
I am having problem connecting to wireless at all on my nc6400 . I blacklisted the ipw3845 driver and I am loading iwl3945 however I still do not see my wireless network. Any help would be appreciated. I am running Hardy Alpha4.
Here is my iw and if config


> lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wlan0_rename  IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

> eth0      Link encap:Ethernet  HWaddr 00:16:d4:a0:86:15  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d4ff:fea0:8615/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1038 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1008 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1046628 (1022.0 KB)  TX bytes:173513 (169.4 KB)
          Interrupt:16 

eth1      Link encap:UNSPEC  HWaddr 00-18-DE-CF-79-92-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:30 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1500 (1.4 KB)  TX bytes:1500 (1.4 KB)

wlan0_rename Link encap:Ethernet  HWaddr 00:18:de:cf:79:92  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
Thank you

---

