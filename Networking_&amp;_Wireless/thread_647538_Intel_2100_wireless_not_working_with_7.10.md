---
title: "Intel 2100 wireless not working with 7.10"
date: 2007-12-22
forum: Networking &amp; Wireless
---

### Post by tbrsaington on 2007-12-22
I have been reading around on the forums looking for a solution but nothing has worked so far.
I have tried the suggestion in this [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188) with no luck.
I have read something about reinstalling a package? But I am a linux newbie so I am not sure what I am meant to be doing with that. Any pointers would be appreciated.

ps. No networks appear in the network manager either.

Regards
Thomas

when running dhclient 
```
**There is already a pid file /var/run/dhclient.pid with pid 134519120**
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:0c:f1:13:d4:2b
Sending on   LPF/eth1/00:0c:f1:13:d4:2b
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

lshw -C network outputs this

```
*-network:0             
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: eth0
       version: 01
       serial: 00:0a:e4:23:fb:e4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=1.01 ip=192.168.1.64 latency=64 module=b44 multicast=yes
  *-network:1
       description: Wireless interface
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 6
       bus info: pci@0000:02:06.0
       logical name: eth1
       version: 04
       serial: 00:0c:f1:13:d4:2b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 latency=64 maxlatency=34 mingnt=2 module=ipw2100 multicast=yes wireless=unassociated

```

lspci:
```
02:06.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)

```

---

