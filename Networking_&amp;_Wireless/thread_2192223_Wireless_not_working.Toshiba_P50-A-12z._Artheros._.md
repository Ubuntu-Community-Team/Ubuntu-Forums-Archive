---
title: "Wireless not working.Toshiba P50-A-12z. Artheros. Ubuntu 12.04"
date: 2013-12-06
forum: Networking &amp; Wireless
---

### Post by chemolari on 2013-12-06
I installed Ubuntu 12.04 over a Toshiba P50-A-12z and after  reformattting the disk with windows8 (I always kept windows before on a  smaller partition but this time, windows8 was to bad even for me to keep  so there it goes). 
  After doing a recommended upgrade of Ubuntu I solved some issues but I  still am having problems with the wireless (I get a good wired  connection though). Wireless used to work well with Windows8 before  removing it from my system. I had to play with the BIOS to install  Ubuntu from disk (disable the UEFI) but I doubt this should have any  effect on the wireless performance. I tried many things I saw in this  and other forums but nothing seems to work. I suspect the issue is on  the driver that may not be available as on Intel's website say this  device was released on the second half of 2013 and maybe too new for  unsoported OS?. I checked on intel's webpage and even though they say  the offer support for linux could not find the driver for what I think  is my wireless device. Still, I hope a smart shoul from this forum could  offer some help.  Any help would be much appreciated. First, some useful info. 
  rfkill only shows bluetooth. Pressing F12 turns bluetooth on and off but no sign of wireless

  ```
rfkill list
5: hci0: Bluetooth
Soft blocked: no
Hard blocked: no

```

  lshw -C network shows the device is UNCLAIMED. 
   
```
*-network UNCLAIMED     
   description: Network controller
   product: Wireless 7260
   vendor: Intel Corporation
   physical id: 0
   bus info: pci@0000:03:00.0
   version: 73
   width: 64 bits
   clock: 33MHz
   capabilities: bus_master cap_list
   configuration: latency=0
   resources: memory:f7900000-f7901fff
  *-network
   description: Ethernet interface
   product: QCA8171 Gigabit Ethernet
   vendor: Qualcomm Atheros
   physical id: 0
   bus info: pci@0000:04:00.0
   logical name: eth0
   version: 10
   serial: 54:be:f7:73:00:bd
   size: 100Mbit/s
   capacity: 1Gbit/s
   width: 64 bits
   clock: 33MHz
   capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
   configuration: autonegotiation=on broadcast=yes driver=alx driverversion=1.2.3 duplex=full firmware=N/A ip=192.168.1.105 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
   resources: irq:19 memory:f7800000-f783ffff ioport:d000(size=128)
   
```
  
lspci shows what I think is the best description of the hardware. I  should have checked this info from windows8 but now is too late. Is  there other way of finding out if this is the hardware or can I trust  the info from lspci?

  ```

lspci
03:00.0 Network controller: Intel Corporation Wireless 7260 (rev 73)
04:00.0 Ethernet controller: Qualcomm Atheros QCA8171 Gigabit Ethernet (rev 10)
  
```

From my limited knowledge, I think the driver is alx (is it?). Below some info about it:

```

  modinfo alx
filename:       /lib/modules/3.8.0-34-generic/kernel/ubuntu/alx/alx.ko
version:        1.2.3
license:        Dual BSD/GPL
description:    Qualcomm Atheros Gigabit Ethernet Driver
author:         Qualcomm Corporation, <nic-devel@qualcomm.com>
srcversion:     896F432F7919E2B2C08B0B3
alias:          pci:v00001969d000010A0sv*sd*bc*sc*i*
alias:          pci:v00001969d000010A1sv*sd*bc*sc*i*
alias:          pci:v00001969d00001090sv*sd*bc*sc*i*
alias:          pci:v00001969d00001091sv*sd*bc*sc*i*
depends:        mdio
intree:         Y
vermagic:       3.8.0-34-generic SMP mod_unload modversions 
  
```

Do I need to upgrade this driver or wait for a newer version?

```

  Thanks!

```

---

### Post by chili555 on 2013-12-06
Please see the answers on your question at askubuntu.

---

