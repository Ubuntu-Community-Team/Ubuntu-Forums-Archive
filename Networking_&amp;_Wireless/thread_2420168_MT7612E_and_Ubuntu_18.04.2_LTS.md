---
title: "MT7612E and Ubuntu 18.04.2 LTS"
date: 2019-05-31
forum: Networking &amp; Wireless
---

### Post by hmcode on 2019-05-31
Hello. I've recently bought a wi-fi card from [https://aliexpress.com/item/32817460933.html?dp=6e77d5fc568b05d3a74b745ca41239c1&af=139947&cv=47843&afref=&mall_affr=pr3&aff_platform=aaf&cpt=1525296767111&sk=VnYZvQVf&aff_trace_key=77a8dd49634b40a29384852a5010bec9-1525296767111-08032-VnYZvQVf&terminal_id=6cea2a81d8f2462fb987f0d2efeb5b74](https://aliexpress.com/item/32817460933.html?dp=6e77d5fc568b05d3a74b745ca41239c1&af=139947&cv=47843&afref=&mall_affr=pr3&aff_platform=aaf&cpt=1525296767111&sk=VnYZvQVf&aff_trace_key=77a8dd49634b40a29384852a5010bec9-1525296767111-08032-VnYZvQVf&terminal_id=6cea2a81d8f2462fb987f0d2efeb5b74)
It uses MTK MT7612E chipset. It is, however, not recognized by Ubuntu 18.04. What can I do to make it work?

---

### Post by hmcode on 2019-05-31
Just installed newer kernels 4.20 and 5.X versions and got this card recognized. Performance is bad though, don't know whether it's a driver problem or rather incompatibility between Ubuntu 18.04 and kernels above 4.19. If anyone can come up with a solution for 4.15 I'll appreciate it.

---

### Post by praseodym on 2019-05-31
Can you please show the outputs of
```

lspci -nnk
lsusb
```
Maybe we find a driver for 4.15

---

### Post by hmcode on 2019-05-31
lspci:
```

00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 02)
    Subsystem: Lenovo Core Processor DRAM Controller [17aa:2193]
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 02)
    Subsystem: Lenovo Core Processor Integrated Graphics Controller [17aa:21c1]
    Kernel driver in use: i915
    Kernel modules: i915
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
    Subsystem: Lenovo 5 Series/3400 Series Chipset HECI Controller [17aa:215f]
    Kernel modules: mei_me
00:16.3 Serial controller [0700]: Intel Corporation 5 Series/3400 Series Chipset KT Controller [8086:3b67] (rev 06)
    Subsystem: Lenovo 5 Series/3400 Series Chipset KT Controller [17aa:2162]
    Kernel driver in use: serial
00:19.0 Ethernet controller [0200]: Intel Corporation 82577LM Gigabit Network Connection [8086:10ea] (rev 06)
    Subsystem: Lenovo 82577LM Gigabit Network Connection [17aa:2153]
    Kernel driver in use: e1000e
    Kernel modules: e1000e
00:1a.0 USB controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 06)
    Subsystem: Lenovo 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [17aa:2163]
    Kernel driver in use: ehci-pci
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b57] (rev 06)
    Subsystem: Lenovo 5 Series/3400 Series Chipset High Definition Audio [17aa:215e]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 06)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 06)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.3 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 [8086:3b48] (rev 06)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 06)
    Subsystem: Lenovo 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [17aa:2163]
    Kernel driver in use: ehci-pci
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a6)
00:1f.0 ISA bridge [0601]: Intel Corporation QS57 Chipset LPC Interface Controller [8086:3b0f] (rev 06)
    Subsystem: Lenovo QS57 Chipset LPC Interface Controller [17aa:2166]
    Kernel driver in use: lpc_ich
    Kernel modules: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller [8086:3b2f] (rev 06)
    Subsystem: Lenovo 5 Series/3400 Series Chipset 6 port SATA AHCI Controller [17aa:2168]
    Kernel driver in use: ahci
    Kernel modules: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 06)
    Subsystem: Lenovo 5 Series/3400 Series Chipset SMBus Controller [17aa:2167]
    Kernel modules: i2c_i801
00:1f.6 Signal processing controller [1180]: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem [8086:3b32] (rev 06)
    Subsystem: Lenovo 5 Series/3400 Series Chipset Thermal Subsystem [17aa:2190]
    Kernel driver in use: intel ips
    Kernel modules: intel_ips
03:00.0 Network controller [0280]: MEDIATEK Corp. Device [14c3:7612]
    Subsystem: MEDIATEK Corp. Device [14c3:7612]
05:00.0 SD Host controller [0805]: Ricoh Co Ltd MMC/SD Host Controller [1180:e822] (rev 01)
    Subsystem: Lenovo MMC/SD Host Controller [17aa:2133]
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci_pci
05:00.1 System peripheral [0880]: Ricoh Co Ltd R5U2xx (R5U230 / R5U231 / R5U241) [Memory Stick Host Controller] [1180:e230] (rev 01)
    Subsystem: Lenovo R5U2xx (R5U230 / R5U231 / R5U241) [Memory Stick Host Controller] [17aa:2134]
ff:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 02)
    Subsystem: Lenovo Core Processor QuickPath Architecture Generic Non-core Registers [17aa:2196]
ff:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 02)
    Subsystem: Lenovo Core Processor QuickPath Architecture System Address Decoder [17aa:2196]
ff:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 02)
    Subsystem: Lenovo Core Processor QPI Link 0 [17aa:2196]
ff:02.1 Host bridge [0600]: Intel Corporation 1st Generation Core i3/5/7 Processor QPI Physical 0 [8086:2d11] (rev 02)
    Subsystem: Lenovo 1st Generation Core i3/5/7 Processor QPI Physical 0 [17aa:2196]
ff:02.2 Host bridge [0600]: Intel Corporation 1st Generation Core i3/5/7 Processor Reserved [8086:2d12] (rev 02)
    Subsystem: Lenovo 1st Generation Core i3/5/7 Processor Reserved [17aa:2196]
ff:02.3 Host bridge [0600]: Intel Corporation 1st Generation Core i3/5/7 Processor Reserved [8086:2d13] (rev 02)
    Subsystem: Lenovo 1st Generation Core i3/5/7 Processor Reserved [17aa:2196]

```

lsusb:
```

Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 17ef:480d Lenovo Integrated Webcam [R5U877]
Bus 001 Device 004: ID 0a5c:217f Broadcom Corp. BCM2045B (BDC-2.1)
Bus 001 Device 003: ID 147e:2016 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```


If I execute lspci running 5.1.6 kernel I can see this as part of lspci -nnk output
```

03:00.0 Network controller [0280]: MEDIATEK Corp. Device [14c3:7612]
    Subsystem: MEDIATEK Corp. Device [14c3:7612]
    Kernel driver in use: mt76x2e
    Kernel modules: mt76x2e

```

Is [this]("https://github.com/i80s/mtk-sources/tree/master/mt76x2e") one is what I need? How do I compile it and run?

---

