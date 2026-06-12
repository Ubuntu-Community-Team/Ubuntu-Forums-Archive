---
title: "Can't get my internal wireless card recognized"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by dhar23 on 2008-12-26
I've posted in the past regarding my inability to use ubuntu to recognize any nearby wireless networks. I just checked my hardware profiles, and my wireless card is listed as an unknown device. I assume this is the core of my problem. Is there any simple way to get it recognized? I've gone over my network settings repeatedly and can't find any other problem. I'm still very new to Ubuntu, so any help I could get would be greatly appreciated. 

thanks.

---

### Post by melojo on 2008-12-26
Can you post the output of

```
sudo lspci
```

and

```
sudo lshw -C network
```

This will give us more info.

---

### Post by ieee488 on 2008-12-26
There's a Sticky post at the top of the first page of this forum with a whole host of troubleshooting tips.

---

### Post by dhar23 on 2008-12-26
melojo, 

apologies for the delayed response.

After typing sudo lspci, I get: 

admin@localhost:~$ sudo lspci
[sudo] password for admin: 
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 06e9 (rev a1)
02:00.0 Memory controller: Intel Corporation Turbo Memory Controller (rev 11)
03:00.0 Network controller: Intel Corporation Unknown device 4237
0c:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
0d:00.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
0d:00.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
0d:00.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
0d:00.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
0d:00.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

I get this after entering that second command you gave me: 

admin@localhost:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 00
       serial: 00:21:5d:72:dd:94
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth0
       version: 02
       serial: 00:22:15:eb:15:b5
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.008.00-NAPI duplex=full ip=192.168.1.3 latency=0 link=yes module=r8168 multicast=yes port=twisted pair speed=100MB/s
admin@localhost:~$ 

If you could let me know what you think whenever you get a chance, that would be a huge help. 

ieee488, I'll check that sticky post over as well. 

Thanks.

---

### Post by melojo on 2008-12-27
Can you post the output of
```
 iwlist 
```

It looks like your wireless is recognized as wmaster0

If it is working iwlist brings up wireless networks that are close by.

---

### Post by Michael.Godawski on 2008-12-27
> **melojo said:**
> Can you post the output of
```
 iwlist 
```It looks like your wireless is recognized as wmaster0

If it is working iwlist brings up wireless networks that are close by.

I would run

```
sudo iwlist scan
```
to check if your wlan network is recognized.

---

### Post by melojo on 2008-12-28
> **Michael.Godawski said:**
> I would run

```
sudo iwlist scan
```
to check if your wlan network is recognized.

Thanks forgot the scan switch, but you don't need sudo to run iwlist.

---

