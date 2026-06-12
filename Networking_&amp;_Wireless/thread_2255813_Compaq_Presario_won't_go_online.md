---
title: "Compaq Presario won't go online"
date: 2014-12-07
forum: Networking &amp; Wireless
---

### Post by darren-jansen on 2014-12-07
I have Ubuntu 12.04 on my Compaq Presario CQ50.

It won't let me online even though the wireless off/on button is blue. If I click on the little network symbol on the menu bar, it says wireless is disabled by hardware switch.

It won't let me use a wired connection either.

Anybody know how I can download and install the wireless drivers.

Another user had a similar problem in a previous forum post. ([http://ubuntuforums.org/showthread.php?t=1572977](http://ubuntuforums.org/showthread.php?t=1572977)) He resolved it by asking his school to turn on the network CAT5 ports. However, I'm on a home network and I'm not sure if I have that same problem or how I would resolve it.

Anybody have any idea what I should do?

This information might be helpful perhaps.

~$ lspci
00:00.0 RAM memory: NVIDIA Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: NVIDIA Corporation Device 075e (rev a2)
00:01.1 SMBus: NVIDIA Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.3 Co-processor: NVIDIA Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: NVIDIA Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB controller: NVIDIA Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB controller: NVIDIA Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB controller: NVIDIA Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB controller: NVIDIA Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:06.0 IDE interface: NVIDIA Corporation MCP78S [GeForce 8200] IDE (rev a1)
00:07.0 Audio device: NVIDIA Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)
00:08.0 PCI bridge: NVIDIA Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 IDE interface: NVIDIA Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) (rev a2)
00:0a.0 Ethernet controller: NVIDIA Corporation MCP77 Ethernet (rev a2)
00:0b.0 PCI bridge: NVIDIA Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:14.0 PCI bridge: NVIDIA Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 11h Processor HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 11h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 11h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 11h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 11h Processor Link Control
02:00.0 VGA compatible controller: NVIDIA Corporation C77 [GeForce 8200M G] (rev a2)
07:00.0 Ethernet controller: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) (rev 01)


Thanks so much for your help!

---

### Post by mörgæs on 2014-12-08
Do you get wired internet access in a live boot of 14.04?

---

