---
title: "Cannot pick up wireless signal"
date: 2008-06-25
forum: Networking &amp; Wireless
---

### Post by xfireinfernox on 2008-06-25
Hello, 
First off, I am new to linux so I'm still a little "overwhelmed" by it all. I am trying to get my wireless network to work. Wired connection works just fine. I've tried every troubleshooting article I could find but nothing seems to work. So, here we go. 

I am currently running Ubuntu 8.04 on a HP Pavillion dv6000. 
My router is a Linksys WRT54G transmitting a 2.4GHz WPA-secure signal.

lshw -C network
```
 *-network               
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:14:a5:db:02:a7
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,03/23/2006, 4.40.1 latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

```

wconfig wlan0
```
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

ifconfig wlan0
```

wlan0     Link encap:Ethernet  HWaddr 00:14:a5:db:02:a7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Memory:b8000000-b8004000 

```

sudo dhclient wlan0
```

Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:14:a5:db:02:a7
Sending on   LPF/wlan0/00:14:a5:db:02:a7
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

if there is any other information you need, please let me know. I have already tried the "WifiDocs/Driver/bcm43xx/Feisty No-Fluff" document with no success. I love linux but I need the wireless connection.

Also, manual configuration is an absolute last resort. I go to a university with several different access points and don't want to have to re-configure my wireless card each time.

---

### Post by xfireinfernox on 2008-06-26
BUMP

is there anyone that has any ideas?

---

### Post by kevdog on 2008-06-26
You could try installing WICD in place of Network Manager if you really want a GUI.

---

