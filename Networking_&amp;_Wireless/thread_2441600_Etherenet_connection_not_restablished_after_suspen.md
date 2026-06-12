---
title: "Etherenet connection not restablished after suspend"
date: 2020-04-25
forum: Networking &amp; Wireless
---

### Post by boballen552 on 2020-04-25
This has actually been an issue since some point in the 16.04 life cycle, initially 16.04 did not have this problem. I stopped being able to connect to the wired network connection after suspending. I assumed I installed something to break it but I've recently played with a few Ubuntu variants (Pop!_OS, Elementary, Ubuntu, Kubutnu) all the latest stable versions over the last month or so and the problem is persisting. There are certainly some type of logs that would provide hardware info but I'm going to need a bit of help figuring that out. I suspect it is an issue with my specific hardware.

I just installed 20.04 Kubutnu. A hardware list as a start:
 ```
lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0100] (rev 09)
        Subsystem: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0100]
        Kernel driver in use: snb_uncore
00:01.0 PCI bridge [0604]: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port [8086:0101] (rev 09)
        Kernel driver in use: pcieport
00:16.0 Communication controller [0780]: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)
        Subsystem: eVga.com. Corp. 6 Series/C200 Series Chipset Family MEI Controller [3842:1023]
        Kernel driver in use: mei_me
        Kernel modules: mei_me
00:1a.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 [8086:1c2d] (rev 05)
        Subsystem: eVga.com. Corp. 6 Series/C200 Series Chipset Family USB Enhanced Host Controller [3842:1023]
        Kernel driver in use: ehci-pci
00:1b.0 Audio device [0403]: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 05)
        Subsystem: Realtek Semiconductor Co., Ltd. 6 Series/C200 Series Chipset Family High Definition Audio Controller [10ec:0889]
        Kernel driver in use: snd_hda_intel
        Kernel modules: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 [8086:1c10] (rev b5)
        Kernel driver in use: pcieport
00:1c.1 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 [8086:1c12] (rev b5)
        Kernel driver in use: pcieport
00:1c.2 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 [8086:1c14] (rev b5)
        Kernel driver in use: pcieport
00:1c.3 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 [8086:1c16] (rev b5)
        Kernel driver in use: pcieport
00:1c.4 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 [8086:1c18] (rev b5)
        Kernel driver in use: pcieport
00:1c.5 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 [8086:1c1a] (rev b5)
        Kernel driver in use: pcieport
00:1c.6 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 7 [8086:1c1c] (rev b5)
        Kernel driver in use: pcieport
00:1c.7 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 8 [8086:1c1e] (rev b5)
        Kernel driver in use: pcieport
00:1d.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 [8086:1c26] (rev 05)
        Subsystem: eVga.com. Corp. 6 Series/C200 Series Chipset Family USB Enhanced Host Controller [3842:1023]
        Kernel driver in use: ehci-pci
00:1f.0 ISA bridge [0601]: Intel Corporation Z68 Express Chipset LPC Controller [8086:1c44] (rev 05)
        Subsystem: eVga.com. Corp. Z68 Express Chipset LPC Controller [3842:1023]
        Kernel driver in use: lpc_ich
        Kernel modules: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation 6 Series/C200 Series Chipset Family 6 port Desktop SATA AHCI Controller [8086:1c02] (rev 05)
        Subsystem: eVga.com. Corp. 6 Series/C200 Series Chipset Family 6 port Desktop SATA AHCI Controller [3842:1023]
        Kernel driver in use: ahci
        Kernel modules: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller [8086:1c22] (rev 05)
        Subsystem: eVga.com. Corp. 6 Series/C200 Series Chipset Family SMBus Controller [3842:1023]
        Kernel driver in use: i801_smbus
        Kernel modules: i2c_i801
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GM206 [GeForce GTX 960] [10de:1401] (rev a1)
        Subsystem: Micro-Star International Co., Ltd. [MSI] GM206 [GeForce GTX 960] [1462:3202]
        Kernel driver in use: nvidia
        Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia
01:00.1 Audio device [0403]: NVIDIA Corporation GM206 High Definition Audio Controller [10de:0fba] (rev a1)
        Subsystem: Micro-Star International Co., Ltd. [MSI] GM206 High Definition Audio Controller [1462:3202]
        Kernel driver in use: snd_hda_intel
        Kernel modules: snd_hda_intel
03:00.0 USB controller [0c03]: VIA Technologies, Inc. VL80x xHCI USB 3.0 Controller [1106:3432] (rev 02)
        Subsystem: VIA Technologies, Inc. VL80x xHCI USB 3.0 Controller [1106:3432]
        Kernel driver in use: xhci_hcd
04:00.0 IDE interface [0101]: JMicron Technology Corp. JMB368 IDE controller [197b:2368]
        Subsystem: JMicron Technology Corp. JMB368 IDE controller [197b:2368]
        Kernel driver in use: pata_jmicron
        Kernel modules: pata_jmicron, pata_acpi
05:00.0 IDE interface [0101]: Marvell Technology Group Ltd. 88SE6111/6121 SATA II / PATA Controller [11ab:6121] (rev b2)
        Subsystem: Marvell Technology Group Ltd. 88SE6111/6121 1/2 port SATA II + 1 port PATA Controller [11ab:6121]
        Kernel driver in use: pata_marvell
        Kernel modules: ahci, pata_marvell, pata_acpi
06:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8057 PCI-E Gigabit Ethernet Controller [11ab:4380] (rev 10)
        Subsystem: eVga.com. Corp. 88E8057 PCI-E Gigabit Ethernet Controller [3842:1023]
        Kernel driver in use: sky2
        Kernel modules: sky2
07:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8057 PCI-E Gigabit Ethernet Controller [11ab:4380] (rev 10)
        Subsystem: eVga.com. Corp. 88E8057 PCI-E Gigabit Ethernet Controller [3842:1023]
        Kernel driver in use: sky2
        Kernel modules: sky2
08:00.0 PCI bridge [0604]: Texas Instruments XIO2000(A)/XIO2200A PCI Express-to-PCI Bridge [104c:8231] (rev 03)
09:00.0 FireWire (IEEE 1394) [0c00]: Texas Instruments XIO2200A IEEE-1394a-2000 Controller (PHY/Link) [104c:8235] (rev 01)
        Kernel driver in use: firewire_ohci
        Kernel modules: firewire_ohci
```

Any ideas? Thanks

---

