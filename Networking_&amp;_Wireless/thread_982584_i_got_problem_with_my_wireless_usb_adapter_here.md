---
title: "i got problem with my wireless usb adapter here"
date: 2008-11-14
forum: Networking &amp; Wireless
---

### Post by adiphia on 2008-11-14
My usb adapter is Belkin F5D8051C, N1 Wireless USB Adapter 8051 BELKIN
as u can see from below, the belkin is recognized by 64bit ubuntu

Bus 008 Device 004: ID 050d:805c Belkin Components 
Bus 008 Device 003: ID 0644:0201 TEAC Corp. 
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 005: ID 046d:c719 Logitech, Inc. 
Bus 005 Device 004: ID 046d:c718 Logitech, Inc. 
Bus 005 Device 003: ID 413c:8130 Dell Computer Corp. 
Bus 005 Device 002: ID 046d:0b05 Logitech, Inc. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 006: ID 0424:2514 Standard Microsystems Corp. 
Bus 004 Device 005: ID 05a9:2641 OmniVision Technologies, Inc. 
Bus 004 Device 004: ID beef:0006  
Bus 004 Device 003: ID 0424:2512 Standard Microsystems Corp. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 046d:c521 Logitech, Inc. MX620 Laser Cordless Mouse
Bus 001 Device 004: ID 413c:2010 Dell Computer Corp. 
Bus 001 Device 003: ID 413c:1003 Dell Computer Corp. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

driver is installed too,personally i am not quite sure if the driver is right one...first i tried windows xp 32 bit version, but no luck...then by checking the chipset, i tried Marvel one which should support..but strange thing is....the system cant even identify my adapter. so i tried vista 64 bit one..


netr28ux : driver installed
	device (050D:805C) present

but still iwconfig cant find any device
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

help with me appropriate..

---

### Post by adiphia on 2008-11-16
well, i am managed to make the wireless working...but the strange thing is the  adapter can see wireless connections available but it just doesnt let me connect..i tried all methods WPA WEP etc
below is my information

iwconfig
```


lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Auto  Frequency:2.442 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:14:7F:56:63:FC
                    ESSID:"BTHomeHub-2913"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.442 GHz (Channel 7)
                    Quality:43/100  Signal level:-68 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s

                    Extra:bcn_int=100
                    Extra:atim=0


```
```

  *-network               
       description: Ethernet interface
       product: 82566DC-2 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:1e:c9:4b:e6:22
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e driverversion=0.2.0 firmware=1.1-1 ip=192.168.2.2 latency=0 module=e1000e multicast=yes
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1c:df:a3:93:15
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+rt2870 driverversion=1.52+Belkin International, Inc., multicast=yes wireless=IEEE 802.11g


```

---

### Post by adiphia on 2008-11-17
wired...cant really figure out what happened:confused:
```

Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:1c:df:a3:93:15
Sending on   LPF/wlan0/00:1c:df:a3:93:15
Listening on LPF/eth0/00:1e:c9:4b:e6:22
Sending on   LPF/eth0/00:1e:c9:4b:e6:22
Sending on   Socket/fallback
DHCPREQUEST of 192.168.2.2 on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPREQUEST of 192.168.2.2 on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
No DHCPOFFERS received.

```

---

