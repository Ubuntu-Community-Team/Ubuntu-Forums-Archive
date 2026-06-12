---
title: "Trying to configure  Atheros AR5005G- AR2413 on Hardy Heron"
date: 2008-05-04
forum: Networking &amp; Wireless
---

### Post by cisco182 on 2008-05-04
I tried to configure this with ndiswrapper using this tutorial: [http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828)
obviusly with AR5005g driver, I also tried to configure it with ndiswrapper 1.45, 1.52 and using the ndis from synaptic. please help! the issue is that this isn't my first time using ubuntu. I tried with different links of drivers but they were the same. maybe any help with madwifi or another suggestions?

lspci
```
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
09:02.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
09:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
09:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

I also tried with Gusty Gibbon.

---

### Post by cisco182 on 2008-05-04
soory about this post. the answer was very simple, follow that tutorial (the link is up), the error was stupid , I didn't check the wireless switch, the reason was because the icon was erased and I didn't knew:) about that because isn;t my laptop.. ndiswrapper rocks! works very well with atheros!!

---

