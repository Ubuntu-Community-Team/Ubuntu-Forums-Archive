---
title: "Newbie WiFi not working. Results of Code"
date: 2008-12-01
forum: Networking &amp; Wireless
---

### Post by Silver_fox on 2008-12-01
Hi,

The WiFi light is alight, but I cannot see or be seen by my wireless network.

I have posted before and picking through the threads, I hope I have enough information for people to help. I have run these in terminal and this is the result:

beef@beef-laptop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:12:3f:1d:d3:44   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:18  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:240 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:240 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:15040 (15.0 KB)  TX bytes:15040 (15.0 KB) 
 
wlan0     Link encap:Ethernet  HWaddr 00:14:a4:4e:5c:c4   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
 
wmaster0  Link encap:UNSPEC  HWaddr 00-14-A4-4E-5C-C4-00-00-00-00-00-00-00-00-00-00   
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
 
beef@beef-laptop:~$ iwlist scan 
lo        Interface doesn't support scanning. 
 
eth0      Interface doesn't support scanning. 
 
wmaster0  Interface doesn't support scanning. 
 
wlan0     No scan results 
 
pan0      Interface doesn't support scanning. 
 
beef@beef-laptop:~$ lshw -C network 
WARNING: you should run this program as super-user. 
  *-network:0              
       description: Ethernet interface 
       product: BCM4401-B0 100Base-TX 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: eth0 
       version: 02 
       serial: 00:12:3f:1d:d3:44 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes 
  *-network:1 
       description: Network controller 
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller 
       vendor: Broadcom Corporation 
       physical id: 3 
       bus info: pci@0000:02:03.0 
       version: 02 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master 
       configuration: driver=b43-pci-bridge latency=64 module=ssb 
  *-network:0 
       description: Wireless interface 
       physical id: 1 
       logical name: wlan0 
       serial: 00:14:a4:4e:5c:c4 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg 
  *-network:1 DISABLED 
       description: Ethernet interface 
       physical id: 2 
       logical name: pan0 
       serial: 3e:65:a4:2c:d8:6b 
       capabilities: ethernet physical 
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes 
beef@beef-laptop:~$

---

