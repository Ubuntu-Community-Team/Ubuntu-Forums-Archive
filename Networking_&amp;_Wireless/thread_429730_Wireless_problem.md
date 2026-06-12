---
title: "Wireless problem"
date: 2007-05-01
forum: Networking &amp; Wireless
---

### Post by sephirothsigep on 2007-05-01
alright i have a dell 5150(i know it sucks ) with a broadcom 4306 wireless card.

I used ndiswrapper to install my xp wireless drives using the following steps 

1 install ndiswrapper 
2 blacklist the bcm43xx drives 
3 installed drives with
            -          sudo ndiswrapper -i /location/driverName.inf
            -          sudo ndiswrapper -m
            -          sudo depmod -a
            -          sudo modprobe ndiswrapper
4 changed eth1 to wlan0

my wireless drivers worked fine. everyhting was working and then today after rebooting my computer once i got to class NO wireless. in order to get my wireless to work i have to reload the ndiswrapper kernel module  with sudo modprobe ndiswrapper at startup. what is going on.

[SIZE="5"]here is the output for before i reload the ndiswrapper module [/SIZE]
```
matt@jenova:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:12:3F:D8:6B:44  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 

eth0:avah Link encap:Ethernet  HWaddr 00:12:3F:D8:6B:44  
          inet addr:169.254.6.25  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:504 (504.0 b)  TX bytes:504 (504.0 b)

matt@jenova:~$ more /etc/iftab 
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:12:3f:d8:6b:44 arp 1
wlan0 mac 00:90:96:bb:34:2f arp 1

matt@jenova:~$ ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)
```
[SIZE="5"]
here is my output after reloading ndiswrapper [/SIZE]

```
matt@jenova:~$ sudo modprobe ndiswrapper

matt@jenova:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:12:3F:D8:6B:44  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 

eth0:avah Link encap:Ethernet  HWaddr 00:12:3F:D8:6B:44  
          inet addr:169.254.6.25  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1168 (1.1 KiB)  TX bytes:1168 (1.1 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:90:96:BB:34:2F  
          inet addr:192.168.0.201  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::290:96ff:febb:342f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:203 errors:0 dropped:0 overruns:0 frame:0
          TX packets:220 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:62120 (60.6 KiB)  TX bytes:22564 (22.0 KiB)
          Interrupt:19 Memory:faffc000-faffe000 

matt@jenova:~$ more /etc/iftab 
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:12:3f:d8:6b:44 arp 1
wlan0 mac 00:90:96:bb:34:2f arp 1

bcmwl5 : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)
```

---

