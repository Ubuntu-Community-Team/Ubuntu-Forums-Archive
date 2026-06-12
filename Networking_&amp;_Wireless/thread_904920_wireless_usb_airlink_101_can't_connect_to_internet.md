---
title: "wireless usb airlink 101 can't connect to internet"
date: 2008-08-29
forum: Networking &amp; Wireless
---

### Post by brucegriffin on 2008-08-29
I have an airlink 101 awll3028 usb wireless network adapter and when I first plugged it in of course it didn't work. I went and did the ndiswrapper and after doing all I thought I needed to do it now blinks and acts like it wants to work. It is also recognized now in system-administration-network when I have it plugged in as it added wireless adapter there as one of the options. It seems to be there at the end of the lshw -C Network. I am posting below the results from a lsusb, a uname- m, and a lshw -C Network and hope someone can help me get it to work.




Results of lsusb

```
Bus 003 Device 002: ID 0bda:8189 Realtek Semiconductor Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```



[PHP]results of uname -m

i686[/PHP]



```
results of lshw -C Network

 *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth0
       version: 10
       serial: 00:19:db:83:42:74
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.105 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:11:a3:08:9b:84
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net8187b driverversion=1.52+Airlink101,05/11/2007,5.108 multicast=yes wireless=IEEE 802.11g
```

---

