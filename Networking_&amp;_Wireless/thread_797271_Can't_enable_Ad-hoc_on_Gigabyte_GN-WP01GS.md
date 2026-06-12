---
title: "Can't enable Ad-hoc on Gigabyte GN-WP01GS"
date: 2008-05-17
forum: Networking &amp; Wireless
---

### Post by atay_ on 2008-05-17
I'm trying to enable ad-hoc by this introduction:
[https://help.ubuntu.com/community/WifiDocs/Adhoc](https://help.ubuntu.com/community/WifiDocs/Adhoc)

but I stopped in this place:
```
root@atay# iwconfig wlan0 mode ad-hoc
root@atay# ifconfig wlan0 up
SIOCSIFFLAGS: Operation not supported
root@atay# iwconfig wlan0 mode managment
root@atay# ifconfig wlan0 up
root@atay# 
```

like You see - in ad-hoc mode don't work.

My card is GN-WP01GS (Win XP recognizing). 

I used google and find to download drivers RT61 and it will be maybe works. But there are only dead links

and I don't know. Wrong drivers or I'm doing something wrong. Can someone help me ?

Ubuntu 8.04 - oryginal drivers
```
root@atay# lspci | grep Realtek
02:0f.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)

root@atay# lshw -C network
  *-network:0
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 7
       bus info: pci@0000:02:07.0
       logical name: wmaster0
       version: 00
       serial: 00:14:85:bb:2e:05
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci ip=192.168.0.1 latency=32 module=rt61pci multicast=yes wireless=IEEE 802.11g
```

---

