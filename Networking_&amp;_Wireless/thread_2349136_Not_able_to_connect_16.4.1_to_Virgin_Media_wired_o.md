---
title: "Not able to connect 16.4.1 to Virgin Media wired or wireless"
date: 2017-01-11
forum: Networking &amp; Wireless
---

### Post by chromey85 on 2017-01-11
Hi Everyone,

I'm gonna start like everyone else and say that I'm pretty clueless when it comes to ubuntu, i want to move away from windows because it is sooo laggy and when i managed to get ubuntu installed the first time, it booted really quick.

anyhow, here is my set-up:

Gigabyte GA 990X sli gamming motherboard
AM3+ FX 6300
8gb RAM
EVGA GTX 660 SC
TP-Link TL-WDN4800 PCi card

So I am having a number of issues (does not want to install, Grub2 does not install so installer crashes, cant connect to internet) and I think i should deal with he internet side first hoping that the rest will sort itself out.

The password to the wifi is correct but when I connect the ethernet in, it refuses to connect to the super hub 2ac.

Here is that i pulled of the terminal:

```

ubuntu@ubuntu:~$ sudo iwconfig


lo        no wireless extensions.


wlp5s0    IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
enp6s0    no wireless extensions.
```

```


ubuntu@ubuntu:~$ sudo lspci -v


00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (external gfx0 port B) (rev 02)
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (external gfx0 port B)
    Flags: fast devsel
    Capabilities: [f0] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [c4] HyperTransport: Slave or Primary Interface
    Capabilities: [40] HyperTransport: Retry Mode
    Capabilities: [54] HyperTransport: UnitID Clumping
    Capabilities: [9c] HyperTransport: #1a
    Capabilities: [70] MSI: Enable- Count=1/4 Maskable- 64bit-


00:00.2 IOMMU: Advanced Micro Devices, Inc. [AMD/ATI] RD990 I/O Memory Management Unit (IOMMU)
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] RD990 I/O Memory Management Unit (IOMMU)
    Flags: fast devsel, IRQ 26
    Capabilities: [40] Secure device <?>
    Capabilities: [54] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [64] HyperTransport: MSI Mapping Enable+ Fixed+


00:02.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port B) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 27
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: fd000000-fe0fffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000d9ffffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot+), MSI 00
    Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [b0] Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port B)
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Capabilities: [190] Access Control Services
    Kernel driver in use: pcieport
    Kernel modules: shpchp


00:09.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port H) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 24
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Memory behind bridge: fe400000-fe4fffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot+), MSI 00
    Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [b0] Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port H)
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Capabilities: [190] Access Control Services
    Kernel driver in use: pcieport
    Kernel modules: shpchp


00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] (rev 40) (prog-if 01 [AHCI 1.0])
    Subsystem: Gigabyte Technology Co., Ltd SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 19
    I/O ports at f040 [size=8]
    I/O ports at f030 [size=4]
    I/O ports at f020 [size=8]
    I/O ports at f010 [size=4]
    I/O ports at f000 [size=16]
    Memory at fe50b000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [70] SATA HBA v1.0
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: ahci
    Kernel modules: ahci


00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
    Subsystem: Gigabyte Technology Co., Ltd SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at fe50a000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci-pci


00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
    Subsystem: Gigabyte Technology Co., Ltd SB7x0/SB8x0/SB9x0 USB EHCI Controller
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at fe509000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
    Capabilities: [e4] Debug port: BAR=1 offset=00e0
    Kernel driver in use: ehci-pci


00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
    Subsystem: Gigabyte Technology Co., Ltd SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at fe508000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci-pci


00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
    Subsystem: Gigabyte Technology Co., Ltd SB7x0/SB8x0/SB9x0 USB EHCI Controller
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at fe507000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
    Capabilities: [e4] Debug port: BAR=1 offset=00e0
    Kernel driver in use: ehci-pci


00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 42)
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller
    Flags: 66MHz, medium devsel
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c_piix4, sp5100_tco


00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) (rev 40)
    Subsystem: Gigabyte Technology Co., Ltd SBx00 Azalia (Intel HDA)
    Flags: bus master, slow devsel, latency 32, IRQ 16
    Memory at fe500000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel


00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller
    Flags: bus master, 66MHz, medium devsel, latency 0


00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge (rev 40) (prog-if 01 [Subtractive decode])
    Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=64


00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller (prog-if 10 [OHCI])
    Subsystem: Gigabyte Technology Co., Ltd SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at fe506000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci-pci


00:15.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    Memory behind bridge: fe300000-fe3fffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot-), MSI 00
    Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [b0] Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: pcieport
    Kernel modules: shpchp


00:15.1 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB700/SB800/SB900 PCI to PCI bridge (PCIE port 1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    Memory behind bridge: fe200000-fe2fffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot-), MSI 00
    Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [b0] Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] SB700/SB800/SB900 PCI to PCI bridge (PCIE port 1)
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: pcieport
    Kernel modules: shpchp


00:15.3 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB900 PCI to PCI bridge (PCIE port 3) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fe100000-fe1fffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot-), MSI 00
    Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [b0] Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] SB900 PCI to PCI bridge (PCIE port 3)
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: pcieport
    Kernel modules: shpchp


00:16.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
    Subsystem: Gigabyte Technology Co., Ltd SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at fe505000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci-pci


00:16.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
    Subsystem: Gigabyte Technology Co., Ltd SB7x0/SB8x0/SB9x0 USB EHCI Controller
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at fe504000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
    Capabilities: [e4] Debug port: BAR=1 offset=00e0
    Kernel driver in use: ehci-pci


00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 0
    Flags: fast devsel
    Capabilities: [80] HyperTransport: Host or Secondary Interface


00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 1
    Flags: fast devsel


00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 2
    Flags: fast devsel
    Kernel modules: amd64_edac_mod


00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 3
    Flags: fast devsel
    Capabilities: [f0] Secure device <?>
    Kernel driver in use: k10temp
    Kernel modules: k10temp


00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 4
    Flags: fast devsel
    Kernel driver in use: fam15h_power
    Kernel modules: fam15h_power


00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 5
    Flags: fast devsel


01:00.0 VGA compatible controller: NVIDIA Corporation GK106 [GeForce GTX 660] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: eVga.com. Corp. GK106 [GeForce GTX 660]
    Flags: bus master, fast devsel, latency 0, IRQ 42
    Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=128M]
    Memory at d8000000 (64-bit, prefetchable) [size=32M]
    I/O ports at e000 [size=128]
    Expansion ROM at fe000000 [disabled] [size=512K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [b4] Vendor Specific Information: Len=14 <?>
    Capabilities: [100] Virtual Channel
    Capabilities: [128] Power Budgeting <?>
    Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
    Capabilities: [900] #19
    Kernel driver in use: nouveau
    Kernel modules: nvidiafb, nouveau


01:00.1 Audio device: NVIDIA Corporation GK106 HDMI Audio Controller (rev a1)
    Subsystem: eVga.com. Corp. GK106 HDMI Audio Controller
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at fe080000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel


02:00.0 USB controller: ASMedia Technology Inc. Device 1343 (prog-if 30 [XHCI])
    Subsystem: Gigabyte Technology Co., Ltd Device 5007
    Flags: bus master, fast devsel, latency 0, IRQ 28
    Memory at fe400000 (64-bit, non-prefetchable) [size=32K]
    Capabilities: [50] MSI: Enable- Count=1/8 Maskable- 64bit+
    Capabilities: [68] MSI-X: Enable+ Count=8 Masked-
    Capabilities: [78] Power Management version 3
    Capabilities: [80] Express Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [200] Advanced Error Reporting
    Capabilities: [280] #19
    Capabilities: [300] Latency Tolerance Reporting
    Kernel driver in use: xhci_hcd


04:00.0 USB controller: VIA Technologies, Inc. VL805 USB 3.0 Host Controller (rev 01) (prog-if 30 [XHCI])
    Subsystem: Gigabyte Technology Co., Ltd VL805 USB 3.0 Host Controller
    Flags: fast devsel, IRQ 16
    Memory at fe300000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: [80] Power Management version 3
    Capabilities: [90] MSI: Enable- Count=1/4 Maskable- 64bit+
    Capabilities: [c4] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting


05:00.0 Network controller: Qualcomm Atheros AR93xx Wireless Network Adapter (rev 01)
    Subsystem: Qualcomm Atheros AR93xx Wireless Network Adapter
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at fe200000 (64-bit, non-prefetchable) [size=128K]
    Expansion ROM at fe220000 [disabled] [size=64K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable- Count=1/4 Maskable+ 64bit+
    Capabilities: [70] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [300] Device Serial Number 00-00-00-00-00-00-00-00
    Kernel driver in use: ath9k
    Kernel modules: ath9k


06:00.0 Ethernet controller: Intel Corporation I211 Gigabit Network Connection (rev 03)
    Subsystem: Gigabyte Technology Co., Ltd I211 Gigabit Network Connection
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at fe100000 (32-bit, non-prefetchable) [size=128K]
    I/O ports at d000 [size=32]
    Memory at fe120000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable- Count=1/1 Maskable+ 64bit+
    Capabilities: [70] MSI-X: Enable+ Count=5 Masked-
    Capabilities: [a0] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Device Serial Number 40-8d-5c-ff-ff-e4-c5-85
    Capabilities: [1a0] Transaction Processing Hints
    Kernel driver in use: igb
    Kernel modules: igb


```

```

ubuntu@ubuntu:~$ sudo lshw -c network


  *-network               
       description: Wireless interface
       product: AR93xx Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlp5s0
       version: 01
       serial: f4:f2:6d:0a:75:a4
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=4.4.0-31-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:17 memory:fe200000-fe21ffff memory:fe220000-fe22ffff
  *-network
       description: Ethernet interface
       product: I211 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: enp6s0
       version: 03
       serial: 40:8d:5c:e4:c5:85
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=igb driverversion=5.3.0-k duplex=full firmware=0. 6-1 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:19 memory:fe100000-fe11ffff ioport:d000(size=32) memory:fe120000-fe123fff

```

Many thanks in advance

---

