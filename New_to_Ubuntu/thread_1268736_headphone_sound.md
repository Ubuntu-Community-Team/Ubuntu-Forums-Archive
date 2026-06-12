---
title: "headphone sound"
date: 2009-09-17
forum: New to Ubuntu
---

### Post by dzon65 on 2009-09-17
If I wanna have sound through the headphone,(8.10)I can only do this by putting the plug halfway.As such,the front speakers aren't muted.So,there's clearly a sound connection but it's only applyable like this.Now,I don't have the surround nore headphone option in my volumemixer.Anyone had this issue before?Btw,the jack's just fine.I don't have this problem when in vista.

---

### Post by relay_man on 2009-09-17
Here are few things to check before getting into settings and system.

Do your headphones have a stereo plug? (Three connections; tip, ring, and sleeve?)
Some mono headphones can short stereo jacks and disable all audio at the jack.

Have you plugged and un-plugged the plug into the jack several times ?
Laptops are especially prone to a build-up of dust and grit in the headphone and mic jack openings and cause an inconsistent connection.

When you insert the plug into the jack, is it seating all the way in? (May take a very firm pressure, mine does)

Have you tried a different set of headphones?

---

### Post by dzon65 on 2009-09-18
Yes,stereo.I've tried two,same thing.Besides,when I try it in vista,it works.As if the soundcard in ubuntu is recognizing just part of it

---

### Post by relay_man on 2009-09-18
O.K.
Please give your machine maker and specs.

---

### Post by dzon65 on 2009-09-18
Relay man.I'll post the specs tomorrow,have to go now.Thanks in advance.

---

### Post by dzon65 on 2009-09-20
Relay man.Goodmorning.Ok,tell me what specs you need.Here's the outcome for the soundcards.cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC883
Codec: Motorola Si3054

---

### Post by relay_man on 2009-09-21
Hi

Laptop or desktop?
Manufacturer?
Model # ?

Could you post the output of 

lspci -v

---

### Post by dzon65 on 2009-09-22
Medion 98300 laptop.Here's the outcome:
john@ubuntu:~$ lspci -v
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
    Subsystem: Wistron Corp. Device 4075
    Flags: bus master, 66MHz, fast devsel, latency 0
    Capabilities: <access denied>

00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
    Subsystem: Wistron Corp. Device 4075
    Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
    Subsystem: Wistron Corp. Device 4075
    Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
    Subsystem: Wistron Corp. Device 4075
    Flags: 66MHz, fast devsel

00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
    Subsystem: Wistron Corp. Device 4075
    Flags: bus master, 66MHz, fast devsel, latency 0

00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
    Subsystem: Wistron Corp. Device 4075
    Flags: bus master, 66MHz, fast devsel, latency 0
    Capabilities: <access denied>

00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
    Subsystem: Wistron Corp. Device 4075
    Flags: 66MHz, fast devsel

00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
    Subsystem: Wistron Corp. Device 4075
    Flags: 66MHz, fast devsel

00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: c4000000-c40fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2)
    Subsystem: Wistron Corp. Device 4075
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
    Memory at c2000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at c1000000 (64-bit, non-prefetchable) [size=16M]
    [virtual] Expansion ROM at 88000000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nvidia

00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
    Subsystem: Wistron Corp. Device 4076
    Flags: bus master, 66MHz, fast devsel, latency 0
    Capabilities: <access denied>

00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
    Subsystem: Wistron Corp. Device 4076
    Flags: bus master, 66MHz, fast devsel, latency 0

00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
    Subsystem: Wistron Corp. Device 4076
    Flags: 66MHz, fast devsel, IRQ 10
    I/O ports at 3040 [size=64]
    I/O ports at 3000 [size=64]
    Capabilities: <access denied>
    Kernel driver in use: nForce2_smbus
    Kernel modules: i2c-nforce2

00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
    Subsystem: Wistron Corp. Device 4076
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
    Memory at c0040000 (32-bit, non-prefetchable) [size=256K]

00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 10)
    Subsystem: Wistron Corp. Device 4076
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
    Memory at c0004000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd
    Kernel modules: ohci-hcd

00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 20)
    Subsystem: Wistron Corp. Device 4076
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
    Memory at c0005000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd
    Kernel modules: ehci-hcd

00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1) (prog-if 8a [Master SecP PriP])
    Subsystem: Device f7c0:4076
    Flags: bus master, 66MHz, fast devsel, latency 0
    [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
    [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
    I/O ports at 3080 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_amd
    Kernel modules: ata_generic, pata_acpi, pata_amd

00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1) (prog-if 85 [Master SecO PriO])
    Subsystem: Wistron Corp. Device 4076
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19
    I/O ports at 30b0 [size=8]
    I/O ports at 30a4 [size=4]
    I/O ports at 30a8 [size=8]
    I/O ports at 30a0 [size=4]
    I/O ports at 3090 [size=16]
    Memory at c0006000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: sata_nv
    Kernel modules: ata_generic, pata_acpi, sata_nv

00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) (prog-if 01)
    Flags: bus master, 66MHz, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=64
    Memory behind bridge: c3000000-c30fffff
    Capabilities: <access denied>

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
    Subsystem: Wistron Corp. Device 4076
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
    Memory at c0000000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
    Subsystem: Wistron Corp. Device 4076
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
    Memory at c0007000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at 30b8 [size=8]
    Capabilities: <access denied>
    Kernel driver in use: forcedeth
    Kernel modules: forcedeth

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
    Flags: fast devsel
    Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
    Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
    Flags: fast devsel
    Capabilities: <access denied>
    Kernel driver in use: k8temp
    Kernel modules: k8temp

03:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (prog-if 10)
    Subsystem: Wistron Corp. Device 3305
    Flags: bus master, medium devsel, latency 64, IRQ 20
    Memory at c3000000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ohci1394
    Kernel modules: ohci1394

03:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
    Subsystem: Wistron Corp. Device 3305
    Flags: bus master, medium devsel, latency 64, IRQ 18
    Memory at c3000800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

03:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
    Subsystem: Wistron Corp. Device 3305
    Flags: medium devsel, IRQ 10
    Memory at c3000c00 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ricoh-mmc
    Kernel modules: ricoh_mmc

03:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
    Subsystem: Wistron Corp. Device 3305
    Flags: medium devsel, IRQ 10
    Memory at c3001000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>

03:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff) (prog-if ff)
    !!! Unknown header type 7f

john@ubuntu:~$

---

### Post by Luuna on 2009-09-27
Hi !

I'm having a similar problem with Ubuntu 9.04 : nothing happens when I plug headphones in. I have no "headphone" or "surround" option in my volume control preference (screenshot).

Computer : HP dv7-2065ef laptop with a front headphone plug in
I've got the latest AlsaMixer version on.

lspci -v :
```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
    Subsystem: Hewlett-Packard Company Device 3624
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00007000-00007fff
    Memory behind bridge: da000000-da0fffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
    Subsystem: Hewlett-Packard Company Device 3624
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 80e0 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
    Subsystem: Hewlett-Packard Company Device 3624
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at 80c0 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)
    Subsystem: Hewlett-Packard Company Device 3624
    Flags: bus master, medium devsel, latency 0, IRQ 19
    Memory at da105c00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 3624
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at da100000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00006000-00006fff
    Memory behind bridge: d9000000-d9ffffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000d0ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00005000-00005fff
    Memory behind bridge: d8000000-d8ffffff
    Prefetchable memory behind bridge: 00000000d1000000-00000000d1ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: d7000000-d7ffffff
    Prefetchable memory behind bridge: 00000000d2000000-00000000d2ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: d6000000-d6ffffff
    Prefetchable memory behind bridge: 00000000d3000000-00000000d3ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=07, subordinate=09, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: d5000000-d5ffffff
    Prefetchable memory behind bridge: 00000000d4000000-00000000d4ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
    Subsystem: Hewlett-Packard Company Device 3624
    Flags: bus master, medium devsel, latency 0, IRQ 20
    I/O ports at 80a0 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
    Subsystem: Hewlett-Packard Company Device 3624
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 8080 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
    Subsystem: Hewlett-Packard Company Device 3624
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 8060 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
    Subsystem: Hewlett-Packard Company Device 3624
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 8040 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
    Subsystem: Hewlett-Packard Company Device 3624
    Flags: bus master, medium devsel, latency 0, IRQ 20
    Memory at da105800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=32
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 3624
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) (prog-if 01)
    Subsystem: Hewlett-Packard Company Device 3624
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 2297
    I/O ports at 8108 [size=8]
    I/O ports at 8114 [size=4]
    I/O ports at 8100 [size=8]
    I/O ports at 8110 [size=4]
    I/O ports at 8020 [size=32]
    Memory at da105000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 3624
    Flags: medium devsel, IRQ 11
    Memory at da106000 (64-bit, non-prefetchable) [size=256]
    I/O ports at 8000 [size=32]
    Kernel modules: i2c-i801

00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
    Subsystem: Hewlett-Packard Company Device 3624
    Flags: fast devsel, IRQ 11
    Memory at da104000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>

01:00.0 VGA compatible controller: ATI Technologies Inc M96 [Mobility Radeon HD 4650]
    Subsystem: Hewlett-Packard Company Device 3624
    Flags: bus master, fast devsel, latency 0, IRQ 2294
    Memory at c0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at 7000 [size=256]
    Memory at da000000 (32-bit, non-prefetchable) [size=64K]
    Expansion ROM at da020000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx

01:00.1 Audio device: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series]
    Subsystem: Hewlett-Packard Company Device 3624
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at da010000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

02:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
    Subsystem: Intel Corporation Device 1211
    Flags: bus master, fast devsel, latency 0, IRQ 2295
    Memory at d9000000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: iwlagn
    Kernel modules: iwlagn

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 3624
    Flags: bus master, fast devsel, latency 0, IRQ 2296
    I/O ports at 5000 [size=256]
    Memory at d1010000 (64-bit, prefetchable) [size=4K]
    Memory at d1000000 (64-bit, prefetchable) [size=64K]
    Expansion ROM at d1020000 [disabled] [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

06:00.0 FireWire (IEEE 1394): JMicron Technologies, Inc. IEEE 1394 Host Controller (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 3624
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at d6000000 (32-bit, non-prefetchable) [size=2K]
    Memory at d6000d00 (32-bit, non-prefetchable) [size=128]
    Memory at d6000c80 (32-bit, non-prefetchable) [size=128]
    Memory at d6000c00 (32-bit, non-prefetchable) [size=128]
    Capabilities: <access denied>
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

06:00.1 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
    Subsystem: Hewlett-Packard Company Device 3624
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at d6000b00 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

06:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller (prog-if 01)
    Subsystem: Hewlett-Packard Company Device 3624
    Flags: fast devsel, IRQ 16
    Memory at d6000a00 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel modules: sdhci-pci

06:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
    Subsystem: Hewlett-Packard Company Device 3624
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at d6000900 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>

06:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller
    Subsystem: Hewlett-Packard Company Device 3624
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at d6000800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>

```Thanks !

PS: I also posted on [http://ubuntuforums.org/showthread.php?p=8016379#post8016379](http://ubuntuforums.org/showthread.php?p=8016379#post8016379) this thread before seeing this one.

---

### Post by dzon65 on 2009-09-28
Hi.Yes,nothing much to be found on the forum about this,is there?A lot of people having this problem but most of them have the surround or headphone option in their soundmixer.

---

