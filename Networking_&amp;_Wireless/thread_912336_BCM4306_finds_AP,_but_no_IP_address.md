---
title: "BCM4306 finds AP, but no IP address"
date: 2008-09-06
forum: Networking &amp; Wireless
---

### Post by mike310z on 2008-09-06
Should this device work in 8.04 brand new install ?

It sees the router, it shows it mac address, signal strength etc but I cannot get an IP address out of it, I have tried all combination's for encryption etc.

Card is fine via windows.

I have tried a manual forced install, tided every GUI combination, I just don't know what try next.

dmesg shows

> [  843.197351] input: b43-phy0 as /devices/virtual/input/input9
[  843.362466] b43-phy0 debug: Loading firmware version 351.126 (2006-07-29 05:54:02)
[  844.595399] b43-phy0 debug: Chip initialized
[  844.595681] b43-phy0 debug: 30-bit DMA initialized
[  844.597364] Registered led device: b43-phy0:tx
[  844.597708] Registered led device: b43-phy0:rx
[  844.598057] Registered led device: b43-phy0:radio
[  844.598098] b43-phy0 debug: Wireless interface started
[  844.635381] b43-phy0 debug: Adding Interface type 2
[  844.641928] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  881.458005] wlan0: Initial auth_alg=0
[  881.458017] wlan0: authenticate with AP 00:0c:41:76:53:e8
[  881.657485] wlan0: authenticate with AP 00:0c:41:76:53:e8
[  881.857363] wlan0: authenticate with AP 00:0c:41:76:53:e8
[  882.057246] wlan0: authentication with AP 00:0c:41:76:53:e8 timed out

> wlan0     Scan completed :
          Cell 01 - Address: 00:0C:41:76:53:E8
                    ESSID:"linksys"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=86/100  Signal level=-45 dBm  Noise level=-70 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=00000011beed118e

>  *-network:0
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: 82562EZ 10/100 Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 02
       serial: 00:0c:f1:b4:5a:74
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0c:41:64:c8:28
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

---

