---
title: "Gateway MA3 laptop wireless"
date: 2009-10-26
forum: New to Ubuntu
---

### Post by Orientsee on 2009-10-26
I recently got a Gateway MA3 laptop as a gift. I installed 9.04 which works perfectly fine. I have it attached to the web via an ethernet connection and that works well. My problem is the wireless. Ubuntu does not recognize the wireless. I have read the forums but it is very confusing. Is there some clearcut procedure?

My other question is if this all seems too much, is there a USB wireless stick that is pretty much guaranteed to work without all the rigamarole?

Thanks,

Orientsee

---

### Post by mapes12 on 2009-10-26
Please could you post the output to ```
lspci
```

For wifi kit that is plug and play in Ubu have a look here: [http://www.linuxemporium.co.uk/products/wireless/](http://www.linuxemporium.co.uk/products/wireless/)

---

### Post by Orientsee on 2009-10-26
lspci output

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
05:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 2a08 (rev 02)
08:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
08:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
08:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

This is what it gave me.

Thanks,
Orientsee

---

