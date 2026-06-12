---
title: "Wireless option shows up in network manager but I can't connect"
date: 2008-08-24
forum: Networking &amp; Wireless
---

### Post by dontTaseMe on 2008-08-24
Hi, i've been playing around with Hardy Heron on a Toshiba Satellite a215-s5825 and everything works fine and dandy except for my wireless connection.  

It doesn't automatically work, or show up on the network manager, so I went ahead and looked for some solutions.

This is the farthest I got:
I tried ndiswrapper on the drivers I was using for windows xp, and it said hardware detected: yes, and the wireless option showed up on the network manager, but I was unable to connect(I can even see the available networks and signal strength sometimes).

Having failed with that and assuming the driver was at fault, I followed these([https://help.ubuntu.com/community/ToshibaSatelliteA215S7422Guide]("https://help.ubuntu.com/community/ToshibaSatelliteA215S7422Guide")) instructions(which seem to install drivers some kind soul made).  I disabled the ndiswrapper drivers, and tried it, and again the wireless option shows up in the network manager but I still cannot connect.

Any help with this laptop or a a215 model(i believe the s##### just have different amounts of memory/bells and whistles) would be much appreciated

edit: also heres the results from iwconfig and ifconfig in case it helps
```
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:a0:d1:98:3d:d4  
          inet addr:128.226.227.65  Bcast:128.226.227.255  Mask:255.255.255.0
          inet6 addr: fe80::2a0:d1ff:fe98:3dd4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:38231 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18991 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:31370627 (29.9 MB)  TX bytes:1884317 (1.7 MB)
          Interrupt:220 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:398 errors:0 dropped:0 overruns:0 frame:0
          TX packets:398 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:23467 (22.9 KB)  TX bytes:23467 (22.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:16:44:95:3c:5a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---

### Post by dontTaseMe on 2008-08-25
bump, (still unresolved)

---

