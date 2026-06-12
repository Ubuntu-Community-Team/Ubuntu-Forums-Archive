---
title: "Cannot connect to wired or wireless on Inspiron 1505 install"
date: 2008-08-24
forum: Networking &amp; Wireless
---

### Post by falconguard on 2008-08-24
I recently installed Hardy on my Dell Inspiron 1505 and I cannot connect to either a wired or wireless network connection. I've tried everything that I can think of but to no avail. This is my first real Linux experience so it could be I'm missing something. I've read that I need to install firmware for the wireless NIC to function, but the instruction seem like they are written for rather experienced Linux/Ubuntu users. What really baffles me is that the wired ethernet connection doesn't work. This seems to me that it should just work. If anyone has any insight into these issues it would be much appreciated. Let me know if you need any more info to help!

---

### Post by falconguard on 2008-08-26
here is the result of ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:15:c5:05:45:06  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:22 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:1746 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:1746 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:87300 (85.2 KB)  TX bytes:87300 (85.2 KB) 

and here is the result of lshw -C network:

  *-network               
       description: Network controller 
       product: BCM94311MCG wlan mini-PCI 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:0b:00.0 
       version: 01 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list 
       configuration: driver=b43-pci-bridge latency=0 module=ssb 
  *-network 
       description: Ethernet interface 
       product: BCM4401-B0 100Base-TX 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:03:00.0 
       logical name: eth0 
       version: 02 
       serial: 00:15:c5:05:45:06 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes 
  *-network DISABLED 
       description: Wireless interface 
       physical id: 1 
       logical name: wlan0 
       serial: 00:14:a4:7c:97:c7 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g 


i hope this helps someone help me...as I am still baffled.

---

