---
title: "eth0: PCI Bus error 2290."
date: 2009-11-24
forum: New to Ubuntu
---

### Post by AlbertHall05 on 2009-11-24
I have been running Kubuntu 6.06 on an old computer. I uses an ASUS MB model TXP4 with 327MB memory, an Intell 233MX CPU and a 20 GB HD. It is a but slow but it is functional. The network card is a PCI RealTek 8139(***mii      5212      8139too,8139cp***
  from the lspci) . It is connected to a Lynksys BEFSR41 router that is connected to the Cable company's RCA DHG535 Broadband Residential VOIP MODEM. The BIOS of the MB is the latest update available. 
When I tested the LIVECD for  Xubuntu upgrade 9.10 I found that the system loops at boot time. The  message returned continuously is "eth0: PCI Bus error 2290.". The previous message before this one is Starting init crypto disks      [OK]
I installed another network card, an ADMTek AN983B, that returned the same message at boot.
When I disconnect the RJ45 cat 5 cable from the card, I can complete the full boot to the xubuntu window icon list. If I now plug the RJ45 cable into the network card, the system hangs. I used the terminal window to identify the card and status using ifconfig
Since the RJ45 is not connected at this time, there is no inet addr listed, only the HWaddr.
the loopback(lo) shows the inet addr:127.0.0.1
When I plug the RJ45 into the network card the computer stops responding, and I must disconnect the RJ45 and shut the power off before restarting the computer. 
I have not found any other forum messages regarding this particular type of error. I tested both Xubuntu  9.10 and Ubuntu 9.10 with the same result. 
 
Albert

---

### Post by cariboo on 2009-11-28
What is the output of:

```
dmesg | tail -n15
```

after you plug the network cable in?

Are the correct drivers for nics being loaded? Type:

```
sudo lshw -C network
```

to check which driver is being loaded.

---

### Post by pratheesh on 2010-03-17
I get this error, PCI bus error 2290 when I shutdown my system (not so often). I am using Ubuntu 9.10, 2.6.31-20-generic

output of dmesg | tail -n15

==BEGIN==
[   28.355081] ppdev: user-space parallel port driver
[   29.691344] [drm] TV-14: set mode NTSC 480i 0
[   29.831314] [drm] TV-14: set mode NTSC 480i 0
[   30.095055] [drm] TV-14: set mode NTSC 480i 0
[   30.235006] [drm] TV-14: set mode NTSC 480i 0
[   30.499105] [drm] TV-14: set mode NTSC 480i 0
[   30.639084] [drm] TV-14: set mode NTSC 480i 0
[   42.962556] [drm] TV-14: set mode NTSC 480i 0
[   43.105994] [drm] TV-14: set mode NTSC 480i 0
[   43.368082] [drm] TV-14: set mode NTSC 480i 0
[   43.508555] [drm] TV-14: set mode NTSC 480i 0
[   43.772303] [drm] TV-14: set mode NTSC 480i 0
[   43.912419] [drm] TV-14: set mode NTSC 480i 0
[  109.085068] __ratelimit: 3 callbacks suppressed
[  109.085073] gvfsd-metadata[2018]: segfault at 8 ip 0804d2ea sp bfdbe670 error 4 in gvfsd-metadata[8048000+c000]

==END==

output of sudo lshw -C network

==BEGIN==
*-network               
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wmaster0
       version: 01
       serial: 00:22:68:9a:6e:a0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 memory:91300000-9130ffff
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:1e:ec:82:af:4c
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=10.94.1.16 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:16 ioport:1000(size=256) memory:91200000-912000ff
==END==

---

