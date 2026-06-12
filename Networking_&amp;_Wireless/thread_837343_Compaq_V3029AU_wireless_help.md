---
title: "Compaq V3029AU wireless help"
date: 2008-06-22
forum: Networking &amp; Wireless
---

### Post by prashob on 2008-06-22
v3029   wlan is not working
===========================
I am using **compaq v3029** notebook and OS is ubuntu 8.04.This is using **BCM4312** broadcom chipset.I installed wirelessdriver using ndiswrapper.The driver file I used for installation was "**bcmwl5**".This I got from windows installtion area.After this step my network manager is showing 80% signal strength.But I am not able to connect to it.I gave all info
in network manager->wirelessconnection(in roaming mode).

 In System->preferences->Windows wireless driver:
 In currently installed driver area , its showing  "**bcmwl5  Hardware present:no**"
 My settings are based on static IP configuration.This wireless has WEP enabled network with 64bit pass key.
I tried the following commands in my terminal.


1)**sudo lshw -C network**
==================================================================
   *-network               
       description: Network controller
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:bc:02:ec
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.101 multicast=yes wireless=IEEE 802.11g
====================================================================================
2)**ifconfig**
====================================================================================

eth0      Link encap:Ethernet  HWaddr 00:16:d3:16:28:ff  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d3ff:fe16:28ff/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:55013 errors:0 dropped:0 overruns:0 frame:0
          TX packets:63064 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:33296526 (31.7 MB)  TX bytes:24226169 (23.1 MB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:340 errors:0 dropped:0 overruns:0 frame:0
          TX packets:340 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17332 (16.9 KB)  TX bytes:17332 (16.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:14:a5:bc:02:ec  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-14-A5-BC-02-EC-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
===========================================================================
3)**iwconfig**
===========================================================================
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"WA1003A"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
===========================================================================

4)**dmesg | grep wlan0**
========================================
[   48.861021] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   53.316154] ADDRCONF(NETDEV_UP): wlan0: link is not ready
==========================================

Need help for enabling my wireless....

Thanks,
Prashob

---

