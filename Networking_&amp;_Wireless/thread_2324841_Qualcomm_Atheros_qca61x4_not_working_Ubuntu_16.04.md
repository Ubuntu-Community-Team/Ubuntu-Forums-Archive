---
title: "Qualcomm Atheros qca61x4 not working Ubuntu 16.04"
date: 2016-05-16
forum: Networking &amp; Wireless
---

### Post by Aerion4 on 2016-05-16
Hello, I could use a little help with this one. I've followed the steps in [http://ubuntuforums.org/showthread.php?t=2304154&p=13398554%29](http://ubuntuforums.org/showthread.php?t=2304154&p=13398554%29) and several other posts regarding this issue, but I can't seem to get this wireless card to work. I have attached the wireless.info.tar file, and here is some output. In the wireless section, it says underneath Wi-Fi section, "device not ready"


```
 00:00.0 Host bridge: Intel Corporation Sky Lake Host Bridge/DRAM Registers (rev 08)
    Subsystem: Acer Incorporated [ALI] Skylake Host Bridge/DRAM Registers
    Flags: bus master, fast devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=10 <?>

00:02.0 VGA compatible controller: Intel Corporation Sky Lake Integrated Graphics (rev 07) (prog-if 00 [VGA controller])
    Subsystem: Acer Incorporated [ALI] Skylake Integrated Graphics
    Flags: bus master, fast devsel, latency 0, IRQ 128
    Memory at 92000000 (64-bit, non-prefetchable) [size=16M]
    Memory at a0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 5000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [40] Vendor Specific Information: Len=0c <?>
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [ac] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [100] #1b
    Capabilities: [200] Address Translation Service (ATS)
    Capabilities: [300] #13
    Kernel driver in use: i915_bpo
    Kernel modules: i915_bpo

00:14.0 USB controller: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller (rev 21) (prog-if 30 [XHCI])
    Subsystem: Acer Incorporated [ALI] Sunrise Point-LP USB 3.0 xHCI Controller
    Flags: bus master, medium devsel, latency 0, IRQ 125
    Memory at 94300000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: [70] Power Management version 2
    Capabilities: [80] MSI: Enable+ Count=1/8 Maskable- 64bit+
    Kernel driver in use: xhci_hcd

00:14.2 Signal processing controller: Intel Corporation Sunrise Point-LP Thermal subsystem (rev 21)
    Subsystem: Acer Incorporated [ALI] Sunrise Point-LP Thermal subsystem
    Flags: bus master, fast devsel, latency 0, IRQ 255
    Memory at 9432a000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: [50] Power Management version 3
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-

00:15.0 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller (rev 21)
    Subsystem: Acer Incorporated [ALI] Sunrise Point-LP Serial IO I2C Controller
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at 9432b000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: [80] Power Management version 3
    Capabilities: [90] Vendor Specific Information: Len=14 <?>
    Kernel driver in use: intel-lpss
    Kernel modules: intel_lpss_pci

00:16.0 Communication controller: Intel Corporation Sunrise Point-LP CSME HECI (rev 21)
    Subsystem: Acer Incorporated [ALI] Sunrise Point-LP CSME HECI
    Flags: bus master, fast devsel, latency 0, IRQ 129
    Memory at 9432c000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: [50] Power Management version 3
    Capabilities: [8c] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Kernel driver in use: mei_me
    Kernel modules: mei_me

00:17.0 SATA controller: Intel Corporation Sunrise Point-LP SATA Controller [AHCI mode] (rev 21) (prog-if 01 [AHCI 1.0])
    Subsystem: Acer Incorporated [ALI] Sunrise Point-LP SATA Controller [AHCI mode]
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 126
    Memory at 94328000 (32-bit, non-prefetchable) [size=8K]
    Memory at 9432f000 (32-bit, non-prefetchable) [size=256]
    I/O ports at 5080 [size=8]
    I/O ports at 5088 [size=4]
    I/O ports at 5060 [size=32]
    Memory at 9432d000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [70] Power Management version 3
    Capabilities: [a8] SATA HBA v1.0
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1c.0 PCI bridge: Intel Corporation Device 9d10 (rev f1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 122
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: 93000000-93ffffff
    Prefetchable memory behind bridge: 0000000080000000-0000000091ffffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Acer Incorporated [ALI] Device 1030
    Capabilities: [a0] Power Management version 3
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Access Control Services
    Capabilities: [200] L1 PM Substates
    Capabilities: [220] #19
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port (rev f1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 123
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: 94200000-942fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Acer Incorporated [ALI] Sunrise Point-LP PCI Express Root Port
    Capabilities: [a0] Power Management version 3
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Access Control Services
    Capabilities: [200] L1 PM Substates
    Capabilities: [220] #19
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port (rev f1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 124
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    Memory behind bridge: 94000000-941fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Acer Incorporated [ALI] Sunrise Point-LP PCI Express Root Port
    Capabilities: [a0] Power Management version 3
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Access Control Services
    Capabilities: [200] L1 PM Substates
    Capabilities: [220] #19
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation Sunrise Point-LP LPC Controller (rev 21)
    Subsystem: Acer Incorporated [ALI] Sunrise Point-LP LPC Controller
    Flags: bus master, medium devsel, latency 0

00:1f.2 Memory controller: Intel Corporation Sunrise Point-LP PMC (rev 21)
    Subsystem: Acer Incorporated [ALI] Sunrise Point-LP PMC
    Flags: bus master, fast devsel, latency 0
    Memory at 94324000 (32-bit, non-prefetchable) [size=16K]

00:1f.3 Audio device: Intel Corporation Sunrise Point-LP HD Audio (rev 21)
    Subsystem: Acer Incorporated [ALI] Sunrise Point-LP HD Audio
    Flags: bus master, fast devsel, latency 32, IRQ 138
    Memory at 94320000 (64-bit, non-prefetchable) [size=16K]
    Memory at 94310000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: [50] Power Management version 3
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel, snd_soc_skl

00:1f.4 SMBus: Intel Corporation Sunrise Point-LP SMBus (rev 21)
    Subsystem: Acer Incorporated [ALI] Sunrise Point-LP SMBus
    Flags: medium devsel, IRQ 255
    Memory at 9432e000 (64-bit, non-prefetchable) [size=256]
    I/O ports at 5040 [size=32]
    Kernel modules: i2c_i801

01:00.0 3D controller: NVIDIA Corporation GM108M [GeForce 940M] (rev a2)
    Subsystem: Acer Incorporated [ALI] GM108M [GeForce 940M]
    Flags: bus master, fast devsel, latency 0, IRQ 139
    Memory at 93000000 (32-bit, non-prefetchable) [size=16M]
    Memory at 80000000 (64-bit, prefetchable) [size=256M]
    Memory at 90000000 (64-bit, prefetchable) [size=32M]
    I/O ports at 4000 [size=128]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [250] Latency Tolerance Reporting
    Capabilities: [258] L1 PM Substates
    Capabilities: [128] Power Budgeting <?>
    Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
    Capabilities: [900] #19
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_361

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
    Subsystem: Acer Incorporated [ALI] RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
    Flags: bus master, fast devsel, latency 0, IRQ 127
    I/O ports at 3000 [size=256]
    Memory at 94204000 (64-bit, non-prefetchable) [size=4K]
    Memory at 94200000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 01
    Capabilities: [b0] MSI-X: Enable- Count=4 Masked-
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 00-00-00-00-00-00-00-00
    Capabilities: [170] Latency Tolerance Reporting
    Capabilities: [178] L1 PM Substates
    Kernel driver in use: r8169
    Kernel modules: r8169

03:00.0 Network controller: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter (rev 32)
    Subsystem: Lite-On Communications Inc QCA6174 802.11ac Wireless Network Adapter
    Flags: bus master, fast devsel, latency 0, IRQ 130
    Memory at 94000000 (64-bit, non-prefetchable) [size=2M]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable+ Count=8/8 Maskable+ 64bit-
    Capabilities: [70] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [148] Virtual Channel
    Capabilities: [168] Device Serial Number 00-00-00-00-00-00-00-00
    Capabilities: [178] Latency Tolerance Reporting
    Capabilities: [180] L1 PM Substates
    Kernel driver in use: ath10k_pci
    Kernel modules: ath10k_pci 
```

```
 zane@technomancer:~$ iwconfig
enp2s0    no wireless extensions.

lo        no wireless extensions.

wlp3s0    IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on 
```

Please let me know if you need any more information. THank you.

---

