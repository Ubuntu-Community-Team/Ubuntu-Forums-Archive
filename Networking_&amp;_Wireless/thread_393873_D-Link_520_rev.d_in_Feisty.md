---
title: "D-Link 520 rev.d in Feisty"
date: 2007-03-26
forum: Networking &amp; Wireless
---

### Post by HanSolo69 on 2007-03-26
I was trying all night to get my D-Link 520 revision D wireless PCI card working in the Beta using ndiswrapper.  this is my first time using ndiswrapper and i'm having all kinds of problems.  i guess first off, does anyone know if ndiswrapper or this card works in Feisty?

---

### Post by spd106 on 2007-03-26
There are so many versions of this card, so could you please open a terminal and post here the output of ```
lspci 
```and perhaps ```
sudo lshw -class network
```

---

### Post by HanSolo69 on 2007-03-26
this is what i get after running those, i ran lspci second here.

```
 *-network:0 UNCLAIMED   
       description: Ethernet controller 
       product: RTL8180L 802.11b MAC 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 6 
       bus info: pci@02:06.0 
       version: 20 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list 
       configuration: latency=64 maxlatency=64 mingnt=32 
       resources: ioport:a000-a0ff iomemory:fa000000-fa0000ff irq:10 
  *-network:1 
       description: Ethernet interface 
       product: RTL-8139/8139C/8139C+ 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: a 
       bus info: pci@02:0a.0 
       logical name: eth0 
       version: 10 
       serial: 00:0f:ea:2b:66:3e 
       size: 10MB/s 
       capacity: 100MB/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s 
       resources: ioport:a400-a4ff iomemory:fa001000-fa0010ff irq:18 
ryan@ubuntu:~$ lspci 
00:00.0 Host bridge: ALi Corporation M1689 K8 Northbridge [Super K8 Single Chip] 
00:01.0 PCI bridge: ALi Corporation AGP8X Controller 
00:02.0 PCI bridge: ALi Corporation M5249 HTT to PCI Bridge 
00:03.0 ISA bridge: ALi Corporation M1563 HyperTransport South Bridge (rev 70) 
00:03.1 Bridge: ALi Corporation M7101 Power Management Controller [PMU] 
00:04.0 Multimedia audio controller: ALi Corporation M5455 PCI AC-Link Controller Audio Device (rev 20) 
00:0e.0 IDE interface: ALi Corporation M5229 IDE (rev c7) 
00:0e.1 IDE interface: ALi Corporation ULi 5289 SATA (rev 10) 
00:0f.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) 
00:0f.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) 
00:0f.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) 
00:0f.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01) 
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration 
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map 
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller 
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control 
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro] 
01:00.1 Display controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro] (Secondary) 
02:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC (rev 20) 
02:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10) 
```

---

### Post by spd106 on 2007-03-26
Have you read this wiki page [https://help.ubuntu.com/community/WifiDocs/Device/RTL8180L](https://help.ubuntu.com/community/WifiDocs/Device/RTL8180L)?

---

