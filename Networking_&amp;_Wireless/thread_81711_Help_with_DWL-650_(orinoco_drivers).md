---
title: "Help with DWL-650 (orinoco drivers)"
date: 2005-10-25
forum: Networking &amp; Wireless
---

### Post by carlosqueso on 2005-10-25
I have a DWL-650 wlan card rev.M with the realtek chipset.  I thought it was supposed to just work.  The system appears to recognize it (see my lspci output below), but I can't set it up in network config.  Can anybody help?

```
will@burgess:~$ lspci
0000:00:00.0 Host bridge: ATI Technologies Inc AGP Bridge [IGP 320M] (rev 13)
0000:00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 320M] (rev 01)
0000:00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
0000:00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
0000:00:07.0 ISA bridge: ALi Corporation M1533 PCI to ISA Bridge [Aladdin IV]
0000:00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
0000:00:0a.0 CardBus bridge: O2 Micro, Inc. OZ6912 Cardbus Controller
0000:00:0c.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
0000:00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
0000:00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
0000:00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
0000:01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1
0000:02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC (rev 20)
```

---

### Post by islandboy on 2006-04-13
Did you ever find a resolution to this. I have the same pci card and have had no luck getting it to show up as an interface. I do get similar output from lspci.

---

### Post by az on 2006-04-13
0000:02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC (rev 20)

That is not the orinoco chipset.  You probably have a different revision.  You can use your card with ndiswrapper, if you get the latest windows driver from realtek.

Dapper has preliminary support for this chipset.  Currently, I can get about 25Kps, which sucks, but is a start.  I assume the driver will improve dramatically since this is a popular 802.11b chipset.  If Dapper releases with a poor realtek driver, you can always blacklist it and continue to use ndiswrapper.


Here is the lastest .inf file:
[http://www.realtek.com.tw/downloads/downloads1-3.aspx?Keyword=8180](http://www.realtek.com.tw/downloads/downloads1-3.aspx?Keyword=8180)

---

