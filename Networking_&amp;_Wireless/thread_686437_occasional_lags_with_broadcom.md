---
title: "occasional lags with broadcom"
date: 2008-02-03
forum: Networking &amp; Wireless
---

### Post by jan quark on 2008-02-03
just wanted to start some brainstorming

sometimes I encounter heavy lags during my internet sessions

it is nothing serious I think but annoying

my inet si working , I can post this :)

it's not an critical issue just wanted to ask if there is some solution or tweak

ipv6 is disabled

I use kazehakase as the webbrowser

furthermore the fwcutter method to enable the drivers

have tested every ( believe me ) method to enable the drivers with ndiswrapper, nothing works


thank you for your ideas and experiences


some specs:

```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"Nasza1309siec"  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:15:0C:64:1C:BE   
          Bit Rate=24 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=61/100  Signal level=-72 dBm  Noise level=-69 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

```
05:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
```

```
  *-network               
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth1
       version: 01
       serial: 00:19:7e:47:bb:43
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic ip=192.168.178.23 latency=0 module=bcm43xx multicast=yes wireless=IEEE 802.11b/g
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:5d:de:8e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=1.01 latency=64 module=b44 multicast=yes
```


it's not an critical issue just wanted to ask if there is some solution or tweak

---

