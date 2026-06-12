---
title: "Internal Wireless Card - Not Recognized"
date: 2007-10-06
forum: Networking &amp; Wireless
---

### Post by dougtron on 2007-10-06
Hey I've seen a few other threads on this but none of the help supplied on there is working with my issue...so here it goes.

I've just purchased a new laptop and I'm running both Vista and Ubuntu.... the wireless works just fine on Vista, it picked it up immediately. (there is an on/off switch on the laptop)

But when I run Ubuntu, under the network managing, it only shows Wired Connection and Dial Up Connection, there isn't even a spot for Wireless Connection (which I know exists based on seeing other screen shots)

Anyway, I have no idea where to look for the drivers or anything, but from what I understand the lspci is something you guys like to see so here it is (sorry it wasn't formatted correctly so I tried to space it out to the best of my ability)

LSPCI------
00:00.0 Host bridge: ATI Technologies Inc Unknown device 7910
00:01.0 
PCI bridge: ATI Technologies Inc Unknown device 7912
00:04.0 
PCI bridge: ATI Technologies Inc Unknown device 7914
00:05.0 
PCI bridge: ATI Technologies Inc Unknown device 7915
00:06.0 
PCI bridge: ATI Technologies Inc Unknown device 7916
00:12.0 
SATA controller: ATI Technologies Inc SB600 Non-Raid-5 
SATA
00:13.0 
USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 
USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 
USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 
USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 
USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 
USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 
SMBus: ATI Technologies Inc SB600 SMBus (rev 14)
00:14.1 
IDE interface: ATI Technologies Inc SB600 
IDE
00:14.2 
Audio device: ATI Technologies Inc SB600 Azalia
00:14.3 
ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 
PCI bridge: ATI Technologies Inc SB600 PCI to PCI Bridge
00:18.0 
Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] 
HyperTransport Technology Configuration
00:18.1 
Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] 
Address Map
00:18.2 
Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 
Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] 
Miscellaneous Control
01:05.0 
VGA compatible controller: ATI Technologies Inc Unknown device 791f
08:00.0 
Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
14:06.0 
FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832 (rev 05)
14:06.1 
Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
14:06.2 
System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 12)
14:06.3 
System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
14:06.4 
System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

Sorry for the newbie-esque question, I'm not a complete idiot but I can't seem to get this internal wireless stuff to work. Thanks in advance for any advice!

-Douglas

---

### Post by dougtron on 2007-10-06
Update----

Still need help, but found another thread guiding people to the drivers for mac80211 RTL8187....

only problem is the install instructions are:   To Compile: make  To Install: make install

I don't understand these instructions, at all. Please help!

---

