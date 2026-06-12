---
title: "installing wag511 (netgear, atheros chip)"
date: 2007-08-22
forum: Networking &amp; Wireless
---

### Post by zamolxis on 2007-08-22
I'm trying to get a WAG511 in my desktop going, but I have no luck. Although the driver appears in the Restricted Drivers Manager list "Atheros Hardware Access Layer (HAL)", the network interface is not listed, and it doesn't appear in Network -> Connections tab either.

lspci:
```
$
00:00.0 Host bridge: nVidia Corporation nForce3 Host Bridge (rev a4)
00:01.0 ISA bridge: nVidia Corporation nForce3 LPC Bridge (rev a6)
00:01.1 SMBus: nVidia Corporation nForce3 SMBus (rev a4)
00:02.0 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.1 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.2 USB Controller: nVidia Corporation nForce3 USB 2.0 (rev a2)
00:05.0 Ethernet controller: nVidia Corporation nForce3 Ethernet (rev a5)
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 Audio (rev a2)
00:08.0 IDE interface: nVidia Corporation nForce3 IDE (rev a5)
00:0a.0 PCI bridge: nVidia Corporation nForce3 PCI Bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 AGP Bridge (rev a4)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 CardBus bridge: Ricoh Co Ltd RL5c475
01:06.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
01:07.0 RAID bus controller: Silicon Image, Inc. SiI 3512 [SATALink/SATARaid] Serial ATA Controller (rev 01)
02:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
03:00.0 VGA compatible controller: ATI Technologies Inc RV350 AR [Radeon 9600]
03:00.1 Display controller: ATI Technologies Inc RV350 AR [Radeon 9600] (Secondary)

```

iwconfig:
```
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

vmnet8    no wireless extensions.

vmnet1    no wireless extensions.
```

The card is connected through a PCMCIA to PCI bridge (Ricoh RLSC475(II) Cardbus Controller), but since the driver appears in the Restricted Drive Manager list everytime I plug it in, I doubt it is a problem.

Any suggestion is welcome.

tia

---

### Post by sricketts on 2007-08-22
Do you mave madwifi-tools installed? I have the same chipset in my WG311T, and needed the madwifi drivers to get everything working. Although I seem to remember the Networking Manager recognized the device without madwifi.

sr

---

### Post by zamolxis on 2007-08-22
That's the feeling I got as well reading other posts - madwifi only helps if the card is already there. :(
Strangely, Windows was able to detect it with no prob

---

