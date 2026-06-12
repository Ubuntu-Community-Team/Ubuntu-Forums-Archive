---
title: "Travelmate2700 neti2200 can't find wireless networks"
date: 2014-08-15
forum: Networking &amp; Wireless
---

### Post by UnSourCeR on 2014-08-15
Hello I installed lubuntu in my Travelmate 2700 and followed the instructions for ndiswrapper and windows drivers, but my laptop does not find any wireless networks. I tried various netis2200.inf files witout success. If you have any suggestion let me know 

```

[   21.038258] ndiswrapper: module verification failed: signature and/or  required key missing - tainting kernel
[   21.075821] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[   22.337245] ndiswrapper: driver neti2220 (LanExpress,08/16/2004,2.23.08.2004) loaded
[   22.383147] ndiswrapper: using IRQ 18
[   22.596977] usbcore: registered new interface driver ndiswrapper
[   28.220080] ndiswrapper (iw_set_ap_address:677): setting AP mac address failed (C0010015)

```
ndiswrapper -l
```
neti2220 : driver installed
    device (17FE:2220) present

```

iwconfig
```
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:0 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


lo        no wireless extensions.


eth0      no wireless extensions.

```

sudo lshw -C network

```

*-network:0             
       description: &#913;&#963;&#973;&#961;&#956;&#945;&#964;&#951; &#948;&#953;&#949;&#960;&#945;&#966;&#942;
       product: IPN 2220 802.11g
       &#954;&#945;&#964;&#945;&#963;&#954;&#949;&#965;&#945;&#963;&#964;&#942;&#962;: InProComm Inc.
       physical id: 2
       &#960;&#955;&#951;&#961;&#959;&#966;&#959;&#961;&#943;&#949;&#962; &#948;&#953;&#945;&#973;&#955;&#959;&#965;: pci@0000:02:02.0
       &#955;&#959;&#947;&#953;&#954;&#972; &#972;&#957;&#959;&#956;&#945;: wlan0
       version: 00
       serial: 00:0e:9b:9d:2b:07
       &#960;&#955;&#940;&#964;&#959;&#962;: 32 bits
       &#961;&#959;&#955;&#972;&#953;: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+neti2220 driverversion=1.59+LanExpress,08/16/2004,2.23. latency=64 link=no maxlatency=32 mingnt=32 multicast=yes wireless=IEEE 802.11g
       &#960;&#972;&#961;&#959;&#953;: irq:18 ioport:a400(size=32) &#956;&#957;&#942;&#956;&#951;:e8200800-e820081f &#956;&#957;&#942;&#956;&#951;:e8200000-e82007ff
  *-network:1
       description: Ethernet interface
       product: RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
       &#954;&#945;&#964;&#945;&#963;&#954;&#949;&#965;&#945;&#963;&#964;&#942;&#962;: Realtek Semiconductor Co., Ltd.
       physical id: 3
       &#960;&#955;&#951;&#961;&#959;&#966;&#959;&#961;&#943;&#949;&#962; &#948;&#953;&#945;&#973;&#955;&#959;&#965;: pci@0000:02:03.0
       &#955;&#959;&#947;&#953;&#954;&#972; &#972;&#957;&#959;&#956;&#945;: eth0
       version: 10
       serial: 00:0f:b0:5f:65:b4
       &#956;&#941;&#947;&#949;&#952;&#959;&#962;: 100Mbit/s
       &#967;&#969;&#961;&#951;&#964;&#953;&#954;&#972;&#964;&#951;&#964;&#945;: 100Mbit/s
       &#960;&#955;&#940;&#964;&#959;&#962;: 32 bits
       &#961;&#959;&#955;&#972;&#953;: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.2.11 latency=128 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       &#960;&#972;&#961;&#959;&#953;: irq:19 ioport:a000(size=256) &#956;&#957;&#942;&#956;&#951;:e8200c00-e8200cff

```

---

### Post by UnSourCeR on 2014-08-16
bump

---

