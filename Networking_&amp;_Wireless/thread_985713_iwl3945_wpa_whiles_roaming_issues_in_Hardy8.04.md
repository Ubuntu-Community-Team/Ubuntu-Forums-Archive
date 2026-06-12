---
title: "iwl3945 wpa whiles roaming issues in Hardy8.04"
date: 2008-11-17
forum: Networking &amp; Wireless
---

### Post by Paul6253 on 2008-11-17
First some necessary info:

  *-network
       description: Ethernet interface
       product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 13
       serial: 00:13:a9:7d:4c:c6
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: 02
       serial: 00:18:de:63:27:1d
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.2 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
eth0      Link encap:Ethernet  HWaddr 00:13:a9:7d:4c:c6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

wlan0     Link encap:Ethernet  HWaddr 00:18:de:63:27:1d  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:deff:fe63:271d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:547054 errors:0 dropped:0 overruns:0 frame:0
          TX packets:296539 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:799595777 (762.5 MB)  TX bytes:25677491 (24.4 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-18-DE-63-27-1D-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


Hi Im yet another with problems with getting wpa to work. I've tried 
all the suggestions, played with the supplicant program , edited 
/etc/networks files,,,etc. What frustrates me the most is I had wpa
working two days ago. Then I decided to ditch windows and install ubuntu
by itself. I did nothing new , same install and as before , wireless
worked fine...but now no wpa. It even says under iwlist that it's not supported ---->
iwlist wlan0 wpa
wlan0     2 key sizes : 40, 104bits
          4 keys available :
Error reading wpa keys (SIOCGIWENCODEEXT): Operation not supported

When I used NetworkManager the setting is roaming. The scanned networks
show up fine. The one wpa encrypted network does not have a drop down
for wpa, only wep. If I try to use 'connect to another network' and
manually edit a wpa key it still doesnt work. I don't know. 
I spent 2 days with this crap...more time than most have..I don't know how people deal with this. 
Again, not to be redundant, I had wpa working! I don't know how but I did.
Any help would be greatly appreciated.

-Paul

---

