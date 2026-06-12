---
title: "Ipw3945 has disappeared after upgrade,"
date: 2007-04-09
forum: Networking &amp; Wireless
---

### Post by Krolik on 2007-04-09
Hi! 
I have a very common problem :) my wireless card Intel ipw3945 has disappeared after upgrade to a new kernel (v13 and v14 too) I have follow many how-to's from this forum, but it still does't work.

Below is output from console, that you probably want to see.

```
krolik@laptop:~$ sudo /sbin/ipw3945d-2.6.20-14-generic 
ipw3945d - regulatory daemon
Copyright (C) 2005-2006 Intel Corporation. All rights reserved.
version: 1.7.22
2007-04-09 21:21:17: ERROR: Could not find Intel PRO/Wireless 3945ABG Network Connection


krolik@laptop:~$ lspci |grep ipw3945
krolik@laptop:~$ 


krolik@laptop:~$ sudo lshw -C network  *-network UNCLAIMED     
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@02:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: iomemory:fdfff000-fdffffff irq:7
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@03:07.0
       logical name: eth0
       version: 10
       serial: 00:18:f3:34:74:96
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: ioport:d800-d8ff iomemory:fe8fec00-fe8fecff irq:16


krolik@laptop:~$ sudo lsmod |grep 3945
krolik@laptop:~$ 


krolik@laptop:~$ uname -r
2.6.20-14-generic

krolik@laptop:~$ sudo iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.


krolik@laptop:~$ sudo apt-get install linux-restricted-modules-2.6.20-14-generic linux-restricted-modules-generic 
Czytanie list pakietów... Gotowe
Budowanie drzewa zale&#380;no&#347;ci       
Reading state information... Gotowe
linux-restricted-modules-2.6.20-14-generic is up to date
linux-restricted-modules-generic is up to date
linux-restricted-modules-generic set to manual installed.
0 aktualizowanych, 0 nowo instalowanych, 0 usuwanych i 0 nieaktualizowanych.
krolik@laptop:~$ 


krolik@laptop:~$ sudo modprobe ipw3945 
FATAL: Error inserting ipw3945 (/lib/modules/2.6.20-14-generic/kernel/ubuntu/wireless/ipw3945/ipw3945.ko): Unknown symbol in module, or unknown parameter (see dmesg)
2007-04-09 21:26:11: ERROR: Could not find Intel PRO/Wireless 3945ABG Network Connection



krolik@laptop:~$ dmesg |grep ipw
[   28.600000] ipw3945: Unknown symbol ieee80211_wx_get_encodeext
[   28.600000] ipw3945: Unknown symbol ieee80211_wx_set_encode
[   28.600000] ipw3945: Unknown symbol ieee80211_wx_get_encode
[   28.600000] ipw3945: Unknown symbol ieee80211_txb_free
[   28.600000] ipw3945: Unknown symbol ieee80211_wx_set_encodeext
[   28.600000] ipw3945: Unknown symbol ieee80211_wx_get_scan
[   28.600000] ipw3945: Unknown symbol escape_essid
[   28.600000] ipw3945: Unknown symbol ieee80211_freq_to_channel
[   28.604000] ipw3945: Unknown symbol ieee80211_set_geo
[   28.604000] ipw3945: Unknown symbol ieee80211_rx
[   28.604000] ipw3945: Unknown symbol ieee80211_get_channel
[   28.604000] ipw3945: Unknown symbol ieee80211_channel_to_index
[   28.604000] ipw3945: Unknown symbol ieee80211_rx_mgt
[   28.604000] ipw3945: Unknown symbol ieee80211_get_geo
[   28.604000] ipw3945: Unknown symbol free_ieee80211
[   28.604000] ipw3945: Unknown symbol ieee80211_tx_frame
[   28.604000] ipw3945: Unknown symbol ieee80211_is_valid_channel
[   28.604000] ipw3945: Unknown symbol ieee80211_get_channel_flags
[   28.604000] ipw3945: Unknown symbol alloc_ieee80211
[  126.284000] ipw3945: Unknown symbol ieee80211_wx_get_encodeext
[  126.284000] ipw3945: Unknown symbol ieee80211_wx_set_encode
[  126.284000] ipw3945: Unknown symbol ieee80211_wx_get_encode
[  126.288000] ipw3945: Unknown symbol ieee80211_txb_free
[  126.288000] ipw3945: Unknown symbol ieee80211_wx_set_encodeext
[  126.288000] ipw3945: Unknown symbol ieee80211_wx_get_scan
[  126.288000] ipw3945: Unknown symbol escape_essid
[  126.288000] ipw3945: Unknown symbol ieee80211_freq_to_channel
[  126.288000] ipw3945: Unknown symbol ieee80211_set_geo
[  126.288000] ipw3945: Unknown symbol ieee80211_rx
[  126.288000] ipw3945: Unknown symbol ieee80211_get_channel
[  126.288000] ipw3945: Unknown symbol ieee80211_channel_to_index
[  126.288000] ipw3945: Unknown symbol ieee80211_rx_mgt
[  126.288000] ipw3945: Unknown symbol ieee80211_get_geo
[  126.288000] ipw3945: Unknown symbol free_ieee80211
[  126.288000] ipw3945: Unknown symbol ieee80211_tx_frame
[  126.288000] ipw3945: Unknown symbol ieee80211_is_valid_channel
[  126.288000] ipw3945: Unknown symbol ieee80211_get_channel_flags
[  126.288000] ipw3945: Unknown symbol alloc_ieee80211
[  543.512000] ipw3945: Unknown symbol ieee80211_wx_get_encodeext
[  543.512000] ipw3945: Unknown symbol ieee80211_wx_set_encode
[  543.512000] ipw3945: Unknown symbol ieee80211_wx_get_encode
[  543.512000] ipw3945: Unknown symbol ieee80211_txb_free
[  543.512000] ipw3945: Unknown symbol ieee80211_wx_set_encodeext
[  543.512000] ipw3945: Unknown symbol ieee80211_wx_get_scan
[  543.512000] ipw3945: Unknown symbol escape_essid
[  543.512000] ipw3945: Unknown symbol ieee80211_freq_to_channel
[  543.516000] ipw3945: Unknown symbol ieee80211_set_geo
[  543.516000] ipw3945: Unknown symbol ieee80211_rx
[  543.516000] ipw3945: Unknown symbol ieee80211_get_channel
[  543.516000] ipw3945: Unknown symbol ieee80211_channel_to_index
[  543.516000] ipw3945: Unknown symbol ieee80211_rx_mgt
[  543.516000] ipw3945: Unknown symbol ieee80211_get_geo
[  543.516000] ipw3945: Unknown symbol free_ieee80211
[  543.516000] ipw3945: Unknown symbol ieee80211_tx_frame
[  543.516000] ipw3945: Unknown symbol ieee80211_is_valid_channel
[  543.516000] ipw3945: Unknown symbol ieee80211_get_channel_flags
[  543.516000] ipw3945: Unknown symbol alloc_ieee80211

```

---

### Post by floke on 2007-04-09
Did you get the restricted modules part of the upgrade?
I have similar problems with the same card until the restricted mods come through.

---

### Post by Krolik on 2007-04-09
> **Steve.K said:**
> Did you get the restricted modules part of the upgrade?
I have similar problems with the same card until the restricted mods come through.

 i have to install restricted modules by myself, but there are already in the system:

```
krolik@laptop:~$ sudo apt-get install linux-restricted-modules-2.6.20-14-generic linux-restricted-modules-generic 
Czytanie list pakietów... Gotowe
Budowanie drzewa zale&#380;no&#347;ci       
Reading state information... Gotowe
linux-restricted-modules-2.6.20-14-generic is up to date
linux-restricted-modules-generic is up to date
linux-restricted-modules-generic set to manual installed.
0 aktualizowanych, 0 nowo instalowanych, 0 usuwanych i 0 nieaktualizowanych.
krolik@laptop:~$ 
```

---

