---
title: "&quot;waiting for network key&quot; Hardy Broadcom wireless problem"
date: 2008-05-08
forum: Networking &amp; Wireless
---

### Post by quizzical on 2008-05-08
Hey everyone.

I'v had a good look around in the forums for some advice on this issue, if I have missed the answer it is not for want of looking.

I have been running ubuntu 7.10 on my HP pavilion G5000 for some months and have had no problems. Wireless worked wonderfully using the ndiswrapper method.

I recently upgraded to Hardy and have been having problems since. I am aware of the issue with the ssb module and believe I have that fixed, the ssb module is now loaded after ndiswrapper. I have also run through removing, then reinstalling ndiswrapper and associated drivers with no joy.

 I am able to see the wireless network I want to connect to but when I hit connect the system tray animates connecting endlessly and displays a tooltip saying "waiting for network key".

I know the network key is correct, I have checked this many times. The symptoms are very similar to those reported in [URL="https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/204868"]
[COLOR="Blue"]https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/204868[/COLOR][/URL]
bug report in network-manager. However, apparently a fix has been released and I'm running the latest version so I am not sure whether to raise another bug report.

So, to reiterate: I can see the wireless network but when I connect nothing happens but appparently the system is waiting for a wireless key.

heres the output from ifconfig:
```
@UbuntuTop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:d4:f3:1f:15  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Base address:0x2000 

eth1      Link encap:Ethernet  HWaddr 00:1a:73:67:e5:56  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Memory:50000000-50004000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1562 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1562 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:78100 (76.2 KB)  TX bytes:78100 (76.2 KB)

```

here's the output from iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

and here's the output from lshw -C network
```

*-network               
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth1
       version: 01
       serial: 00:1a:73:67:e5:56
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 8
       bus info: pci@0000:08:08.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:f3:1f:15
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes



```

on other thing I have noticed is that when I try to set the ESSID of the network using iwconfig nothing happens. I run 
```
sudo iwconfig eth1 essid "ESSID in quotes"
```
but running iwconfig again shows that the ESSID is still set to off/any.

Apologies if this is an obvious problem, i've been banging my head against it for days now and if anyone can help i would be very grateful.

Cheers
Alex

---

