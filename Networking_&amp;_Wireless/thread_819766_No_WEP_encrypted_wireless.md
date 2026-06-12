---
title: "No WEP encrypted wireless"
date: 2008-06-05
forum: Networking &amp; Wireless
---

### Post by Peter K Nicol on 2008-06-05
Almost the same old story again, I'm sorry to say. I've followed many threads and I thought that I was almost there. I can access unsecured networks but not my home network - WEP encryption. This was partly thanks to kevdog (the top sticky).
I find that my home network continually asks for a password. wi-fi radar shows that I am connected but I can't do anything.
Output from lshw -C network, ifconfig and iwconfig below.

> peter@peter-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 42
       serial: 00:09:6b:82:fe:9c
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A ip=192.168.0.4 latency=66 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:6c:b6:4a:95
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net111v2 driverversion=1.52+NETGEAR Inc.,3/16/2006,5.12 multicast=yes wireless=IEEE 802.11g
peter@peter-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:09:6b:82:fe:9c  
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::209:6bff:fe82:fe9c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1454 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1603 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1222497 (1.1 MB)  TX bytes:215671 (210.6 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:107 errors:0 dropped:0 overruns:0 frame:0
          TX packets:107 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8499 (8.2 KB)  TX bytes:8499 (8.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:14:6c:b6:4a:95  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:149 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:25408 (24.8 KB)

peter@peter-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

peter@peter-laptop:~$ 


Any thoughts and or suggestions would be greatly appreciated.

Peter

---

### Post by dmizer on 2008-06-05
try removing wi-fi radar, disabling NetworkManager, and simply configuring your wireeless card in:
system > administration > network

---

### Post by Peter K Nicol on 2008-06-06
I'll give it a try and report back

---

### Post by Peter K Nicol on 2008-06-18
This is what I did in the end, and it works fine.

[http://ubuntuforums.org/showthread.php?t=830762](http://ubuntuforums.org/showthread.php?t=830762)

---

