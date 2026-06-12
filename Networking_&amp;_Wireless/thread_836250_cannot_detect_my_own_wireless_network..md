---
title: "cannot detect my own wireless network."
date: 2008-06-21
forum: Networking &amp; Wireless
---

### Post by billesboelle on 2008-06-21
Hi.
I have my own wireless router(belkin wireless G and ofc the usb adapter that should pair it)

Problem is i cant detect its open network in ubuntu, but i can get it to work in xp.

I tried "iwlist scan" but this doesnt show mine.
drivers seem to be working fine with another network, as internet and all is working flawlessly.

Any ideas ?

Regards, Alex.

---

### Post by drpaul on 2008-06-21
Some more detail about your problem would be useful. Can you connect to other wireless networks? Do you have both wired and wireless connections? Outputs from lshw -C network, iwconfig, ifconfig

Paul

---

### Post by billesboelle on 2008-06-21
No wires attached.

wireless usb adapter works with other networks, cant detect my own network.

 lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:06:02.0
       logical name: eth0
       version: 10
       serial: 00:50:ba:8c:87:5d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 3
       bus info: pci@0000:06:03.0
       logical name: wmaster0
       version: 00
       serial: 00:11:6b:39:d0:c7
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci ip=192.168.0.103 latency=32 module=rt61pci multicast=yes wireless=IEEE 802.11g
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:17:3f:51:e4:a6
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11b/g



 iwconfig


lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"default"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:46:45:3D:98   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=71/100  Signal level=-50 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth1      IEEE 802.11b/g  ESSID:"default"  Nickname:"zd1211"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:46:45:3D:98   
          Bit Rate=24 Mb/s   
          Link Quality=100/100  Signal level=44/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



 ifconfig

eth0      Link encap:Ethernet  HWaddr 00:50:ba:8c:87:5d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Base address:0xb400 

eth1      Link encap:Ethernet  HWaddr 00:17:3f:51:e4:a6  
          inet6 addr: fe80::217:3fff:fe51:e4a6/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2266 errors:1806 dropped:0 overruns:0 frame:1806
          TX packets:796 errors:1 dropped:49 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:744935 (727.4 KB)  TX bytes:38378 (37.4 KB)

eth1:avahi Link encap:Ethernet  HWaddr 00:17:3f:51:e4:a6  
          inet addr:169.254.8.87  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2475 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2475 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:123812 (120.9 KB)  TX bytes:123812 (120.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:11:6b:39:d0:c7  
          inet addr:192.168.0.103  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:6bff:fe39:d0c7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6362 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4097 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4831638 (4.6 MB)  TX bytes:919667 (898.1 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-11-6B-39-D0-C7-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

