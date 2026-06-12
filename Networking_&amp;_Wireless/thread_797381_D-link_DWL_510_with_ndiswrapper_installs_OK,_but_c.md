---
title: "D-link DWL 510 with ndiswrapper installs OK, but crashes system"
date: 2008-05-17
forum: Networking &amp; Wireless
---

### Post by il_bale on 2008-05-17
Hi,

I have just installed the D-Link DWL 510 windows drivers with ndisgtk, and everything went fine. However a few seconds after the network connection is established, the system reboots.

I'm running Ubuntu 8.04 Desktop i386. The D-Link driver was downloaded from:

[ftp://ftp.dlink.co.uk/wireless/dwl-510/dwl-510_drv_270104.zip](ftp://ftp.dlink.co.uk/wireless/dwl-510/dwl-510_drv_270104.zip)

Below is the output of some command line commands:

sudo lshw -C network

  *-network:0             
       description: Ethernet interface
       product: 3c940 10/100/1000Base-T [Marvell]
       vendor: 3Com Corporation
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: eth1
       version: 12
       serial: 00:0c:6e:f3:85:a6
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.13 firmware=N/A latency=64 link=no maxlatency=31 mingnt=23 module=skge multicast=yes port=twisted pair
  *-network:1
       description: Ethernet interface
       product: 3c905B 100BaseTX [Cyclone]
       vendor: 3Com Corporation
       physical id: 9
       bus info: pci@0000:02:09.0
       logical name: eth0
       version: 30
       serial: 00:10:5a:64:fe:78
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full ip=192.168.0.106 latency=64 link=yes maxlatency=10 mingnt=10 module=3c59x multicast=yes port=MII speed=100MB/s
  *-network:2
       description: Wireless interface
       product: DWL-510 2.4GHz Wireless PCI Adapter
       vendor: D-Link System Inc
       physical id: b
       bus info: pci@0000:02:0b.0
       logical name: wlan0
       version: 20
       serial: 00:40:05:3e:d7:73
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netdlwl driverversion=1.52+D-Link,05/23/2003,5.140.052 latency=64 link=no maxlatency=64 mingnt=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11b

ndiswrapper -v

utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-16-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.52
vermagic:       2.6.24-16-generic SMP mod_unload 586 

ndiswrapper -l

netdlwl : driver installed
	device (1186:3300) present

Many thanks in advance,

Bale

---

### Post by il_bale on 2008-05-17
It seems that I fixed this myself after all. As mentioned in the NDIS Wrapper pages ([http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_c-f/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_c-f/)), the D-Link driver has some problems and the driver for the Realtek 8180L chipset used by the card works better.

You can download the Realtek driver from here (windows xp version will do)

[http://www.realtek.com.tw/downloads/downloads1-3.aspx?Keyword=8180](http://www.realtek.com.tw/downloads/downloads1-3.aspx?Keyword=8180)

After that you will need to modify the PCI ID of the device in the NET8180.INF file. That means that you need to replace every occurrence of PCI\VEN_10EC&DEV_8180 with PCI\VEN_1186&DEV_3300 (the Realtek PCI ID is 10ec:8180 whereas the D-Link is 1186;3300).

All this was mentioned in this page that I obviously should have read more carefully:

[http://www.samwel.tk/bart/various/dwl-510-on-linux-2.6.html](http://www.samwel.tk/bart/various/dwl-510-on-linux-2.6.html)

Hopefully this is helpful for someone.

Cheers,

Bale

---

