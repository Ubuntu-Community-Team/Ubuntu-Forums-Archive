---
title: "Increasing Wireless Signal"
date: 2007-11-18
forum: Networking &amp; Wireless
---

### Post by Nevon on 2007-11-18
I'm on a clean Xubuntu install, and my wireless seems to be working by default. However, I get a very poor signal. Using wireless assistant I only get 2/5 stars. In the same spot, my friend who's on a mac, is getting a 5 star signal.

I don't know the model of my wireless card, because this is not my laptop. Is there anyway I can check it? I also have no idea what driver I'm using.

I don't know if it helps, but here's the output from running lspci.
```
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:08.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
00:0c.0 Multimedia audio controller: ESS Technology ES1988 Allegro-1 (rev 12)
00:0d.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 0c)
00:0d.1 Serial controller: Agere Systems Unknown device 045b
00:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
01:01.0 VGA compatible controller: S3 Inc. 86C270-294 Savage/IX-MV (rev 13)
```

---

### Post by nosh on 2007-11-18
You can check the model of your wireless card by running this in the console.

```
sudo lshw -class network
```

generally I have seen that laptops can get very different signal strengths depending on their card.  I hope this helps.

---

### Post by Nevon on 2007-11-19
Thank you. Could you help me make some sense out of this though? 
```
 *-network               
       description: WLI-PCM-L11
       product: Version 01.01
       vendor: MELCO
       physical id: 0
       slot: Socket 0
       resources: irq:3
  *-network
       description: Ethernet interface
       product: 82557/8/9 [Ethernet Pro 100]
       vendor: Intel Corporation
       physical id: d
       bus info: pci@00:0d.0
       logical name: eth0
       version: 0c
       serial: 00:00:f0:6c:18:ba
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI duplex=full firmware=N/A ip=192.168.1.32 latency=66 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: iomemory:e8020000-e8020fff ioport:1000-103f iomemory:e8000000-e801ffff irq:11
  *-network
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:02:2d:3d:94:d2
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Lucent/Agere 7.28 link=no multicast=yes wireless=IEEE 802.11b
```

---

