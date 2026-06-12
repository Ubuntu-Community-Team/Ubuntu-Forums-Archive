---
title: "Wireless randomly stops working (madwifi)"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by Adamantus on 2009-02-03
I'm running 8.04 with an Atheros 242x wireless card. I setup Madwifi and it works very well usually, but my wireless will sometimes just stop (as in there is no option to even choose wireless in network connections), and I'm forced to use wired. And there doesn't seem to be anything that causes it. I won't update my computer or change it in anyway, and when I start it up wireless will be gone. I'll restart it a couple of times and it will reappear. What could be causing this?

lspci output:

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 02)

ifconcig:

eth0      Link encap:Ethernet  HWaddr 00:1e:68:aa:f6:00  
          inet addr:66.254.236.236  Bcast:66.254.239.255  Mask:255.255.248.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23420 errors:0 dropped:4062424572 overruns:0 frame:0
          TX packets:9415 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12574376 (11.9 MB)  TX bytes:1919750 (1.8 MB)
          Interrupt:221 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:575 errors:0 dropped:0 overruns:0 frame:0
          TX packets:575 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17347 (16.9 KB)  TX bytes:17347 (16.9 KB)

---

### Post by brian_p on 2009-02-04
> **Adamantus said:**
> I'm running 8.04 with an Atheros 242x wireless card. I setup Madwifi and it works very well usually, but my wireless will sometimes just stop (as in there is no option to even choose wireless in network connections), and I'm forced to use wired. And there doesn't seem to be anything that causes it. I won't update my computer or change it in anyway, and when I start it up wireless will be gone. I'll restart it a couple of times and it will reappear. What could be causing this?

Something like this can be difficult to diagnose and fix. Start by assuming your Madwifi and network setups are correct. When the wireless connection is lost switch off the wireless access point, leave it off for a while and switch on again. See if the connection is remade:

```
sudo iwconfig
```

Basically, you need to be sure the wireless access point is behaving itself.

---

