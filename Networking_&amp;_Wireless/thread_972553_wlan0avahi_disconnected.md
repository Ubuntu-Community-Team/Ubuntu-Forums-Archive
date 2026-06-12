---
title: "wlan0:avahi disconnected"
date: 2008-11-05
forum: Networking &amp; Wireless
---

### Post by e12596 on 2008-11-05
im running ubuntu 8.10 with a d link dwl-520+ wireless card. the driver for that is acx100. the network monitor says that  wlan0:avahi is disconnected. i am a noob and dont understand how to connect to a password protected network. please help:confused: sooo confused

heres what i got when i ran iwconfig and ifconfig

```
iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b+  ESSID:"Modern Computer"  Nickname:"acx v0.3.36"
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   Tx-Power=18 dBm   Sensitivity=187/255  
          Retry min limit:7   RTS thr:off   
          Power Management:off
          Link Quality=66/100  Signal level=56/100  Noise level=1/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```

```
ifconfig

eth0      Link encap:Ethernet  HWaddr 00:11:11:cb:ca:c4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:247 errors:0 dropped:0 overruns:0 frame:0
          TX packets:247 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:18819 (18.8 KB)  TX bytes:18819 (18.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:80:c8:ac:45:8f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xccc0 

wlan0:avahi Link encap:Ethernet  HWaddr 00:80:c8:ac:45:8f  
          inet addr:169.254.8.84  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0xccc0 
```

---

