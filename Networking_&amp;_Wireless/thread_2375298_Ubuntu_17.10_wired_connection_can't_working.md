---
title: "Ubuntu 17.10 wired connection can't working"
date: 2017-10-23
forum: Networking &amp; Wireless
---

### Post by rakibul on 2017-10-23
Hi
In** Ubuntu 17.10 wired connection is not working** but **wifi **is worked fine.When I was installed  Ubuntu 16.04 LTS and 16.10 * **before** installing Ubuntu 17.10 *,Same problem occurred.I am use** Lenovo ideapad 320.**My cable is ok.But When create **dsl connection** , connection was not working in 16.04 and 16.10.In this reason i** switched** 16.04 **to** 17.10 **but still **same Problem.

---

### Post by praseodym on 2017-10-23
Lets check the hardware in use:
```

lspci -nnk
lsmod
```

---

### Post by rakibul on 2017-10-24
when try lspci -nnk:
##########################
00:00.0 Host bridge [0600]: Intel Corporation Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers [8086:5904] (rev 02)
    Subsystem: Lenovo Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers [17aa:3817]
00:02.0 VGA compatible controller [0300]: Intel Corporation HD Graphics 620 [8086:5916] (rev 02)
    Subsystem: Lenovo HD Graphics 620 [17aa:39c5]
    Kernel driver in use: i915
    Kernel modules: i915
00:14.0 USB controller [0c03]: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller [8086:9d2f] (rev 21)
    Subsystem: Lenovo Sunrise Point-LP USB 3.0 xHCI Controller [17aa:3844]
    Kernel driver in use: xhci_hcd
00:14.2 Signal processing controller [1180]: Intel Corporation Sunrise Point-LP Thermal subsystem [8086:9d31] (rev 21)
    Subsystem: Lenovo Sunrise Point-LP Thermal subsystem [17aa:3836]
    Kernel driver in use: intel_pch_thermal
    Kernel modules: intel_pch_thermal
00:15.0 Signal processing controller [1180]: Intel Corporation Sunrise Point-LP Serial IO I2C Controller #0 [8086:9d60] (rev 21)
    Subsystem: Lenovo Sunrise Point-LP Serial IO I2C Controller [17aa:383b]
    Kernel driver in use: intel-lpss
    Kernel modules: intel_lpss_pci
00:16.0 Communication controller [0780]: Intel Corporation Sunrise Point-LP CSME HECI #1 [8086:9d3a] (rev 21)
    Subsystem: Lenovo Sunrise Point-LP CSME HECI [17aa:3843]
    Kernel driver in use: mei_me
    Kernel modules: mei_me
00:17.0 SATA controller [0106]: Intel Corporation Sunrise Point-LP SATA Controller [AHCI mode] [8086:9d03] (rev 21)
    Subsystem: Lenovo Sunrise Point-LP SATA Controller [AHCI mode] [17aa:383f]
    Kernel driver in use: ahci
    Kernel modules: ahci
00:1c.0 PCI bridge [0604]: Intel Corporation Sunrise Point-LP PCI Express Root Port #5 [8086:9d14] (rev f1)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.5 PCI bridge [0604]: Intel Corporation Sunrise Point-LP PCI Express Root Port #6 [8086:9d15] (rev f1)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1f.0 ISA bridge [0601]: Intel Corporation Device [8086:9d4e] (rev 21)
    Subsystem: Lenovo Device [17aa:3817]
00:1f.2 Memory controller [0580]: Intel Corporation Sunrise Point-LP PMC [8086:9d21] (rev 21)
    Subsystem: Lenovo Sunrise Point-LP PMC [17aa:3845]
    Kernel driver in use: intel_pmc_core
00:1f.3 Audio device [0403]: Intel Corporation Device [8086:9d71] (rev 21)
    Subsystem: Lenovo Device [17aa:380d]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel, snd_soc_skl
00:1f.4 SMBus [0c05]: Intel Corporation Sunrise Point-LP SMBus [8086:9d23] (rev 21)
    Subsystem: Lenovo Sunrise Point-LP SMBus [17aa:3841]
    Kernel modules: i2c_i801
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [17aa:388a]
    Kernel driver in use: r8169
    Kernel modules: r8169
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter [10ec:8821]
    Subsystem: Lenovo RTL8821AE 802.11ac PCIe Wireless Network Adapter [17aa:a814]
    Kernel driver in use: rtl8821ae
    Kernel modules: rtl8821ae
[B]note:
my isp give me username:c15@rakib and password ****. i want to connect my wired connection using this credentials. please give me some instruction how to connect with this.
[/B]

---

