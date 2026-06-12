---
title: "The &quot;Eethenet keeps dropping&quot; conundrum"
date: 2019-09-01
forum: Networking &amp; Wireless
---

### Post by winecurmudgeon2 on 2019-09-01
I installed Xubuntu 18.04.3 on an HP Elitedesk 705 yesterday, and the ethernet connection kept dropping. I have been running Xubuntu since 9.04, and have never had this problem. But it's apparently not uncommon these days. I finally got it to work by editing network/interfaces as described [here]("https://askubuntu.com/questions/1049302/wired-ethernet-not-working-ubuntu-18-04") (and after fixing an unmanaged network error after I edited the file).

So here's my question: I am running Xubuntu 18.04.03 on another machine, a Kingdel, which I installed shortly after 18.04 was released. It has never given me any problems, and the ethernet has always performed flawlessly.

The ethernet hardware (assuming I interpreted lshw correctly) on the Kingdel is a Realtek RTL8111/8168/8411, but it is a Broadcom NetXtreme BCM5762 on the HP. Where do we go from here? Do I file a bug report? Do I post here and hope someone can explain what's going on?

Thanks, as always, for your advice and insight.

---

### Post by praseodym on 2019-09-02
Please show

```
lspci -nnk
```

on the HP

---

### Post by winecurmudgeon2 on 2019-09-03
Below. Currently, I don't have the cable in and all seems to be working with a Realtek USB dongle.

```

boss@Empire-Server:~$ lspci -nnk
00:00.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 30h-3fh) Processor Root Complex [1022:1422]
    Subsystem: Hewlett-Packard Company Family 15h (Models 30h-3fh) Processor Root Complex [103c:2215]
00:00.2 IOMMU [0806]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 30h-3fh) I/O Memory Management Unit [1022:1423]
    Subsystem: Hewlett-Packard Company Family 15h (Models 30h-3fh) I/O Memory Management Unit [103c:2215]
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Kaveri [Radeon R5 Graphics] [1002:1315]
    Subsystem: Hewlett-Packard Company Kaveri [Radeon R5 Graphics] [103c:2215]
    Kernel driver in use: radeon
    Kernel modules: radeon, amdgpu
00:01.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Kaveri HDMI/DP Audio Controller [1002:1308]
    Subsystem: Hewlett-Packard Company Kaveri HDMI/DP Audio Controller [103c:2215]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
00:02.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 30h-3fh) Processor Root Port [1022:1424]
00:03.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 30h-3fh) Processor Root Port [1022:1424]
00:04.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 30h-3fh) Processor Root Port [1022:1424]
00:10.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller [1022:7814] (rev 09)
    Subsystem: Hewlett-Packard Company FCH USB XHCI Controller [103c:2215]
    Kernel driver in use: xhci_hcd
00:10.1 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller [1022:7814] (rev 09)
    Subsystem: Hewlett-Packard Company FCH USB XHCI Controller [103c:2215]
    Kernel driver in use: xhci_hcd
00:11.0 SATA controller [0106]: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] [1022:7801] (rev 40)
    Subsystem: Hewlett-Packard Company FCH SATA Controller [AHCI mode] [103c:2215]
    Kernel driver in use: ahci
    Kernel modules: ahci
00:12.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller [1022:7807] (rev 11)
    Subsystem: Hewlett-Packard Company FCH USB OHCI Controller [103c:2215]
    Kernel driver in use: ohci-pci
00:12.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller [1022:7808] (rev 11)
    Subsystem: Hewlett-Packard Company FCH USB EHCI Controller [103c:2215]
    Kernel driver in use: ehci-pci
00:13.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller [1022:7807] (rev 11)
    Subsystem: Hewlett-Packard Company FCH USB OHCI Controller [103c:2215]
    Kernel driver in use: ohci-pci
00:13.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller [1022:7808] (rev 11)
    Subsystem: Hewlett-Packard Company FCH USB EHCI Controller [103c:2215]
    Kernel driver in use: ehci-pci
00:14.0 SMBus [0c05]: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller [1022:780b] (rev 16)
    Subsystem: Hewlett-Packard Company FCH SMBus Controller [103c:2215]
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c_piix4, sp5100_tco
00:14.2 Audio device [0403]: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller [1022:780d] (rev 01)
    Subsystem: Hewlett-Packard Company FCH Azalia Controller [103c:2215]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
00:14.3 ISA bridge [0601]: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge [1022:780e] (rev 11)
    Subsystem: Hewlett-Packard Company FCH LPC Bridge [103c:2215]
00:14.4 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] FCH PCI Bridge [1022:780f] (rev 40)
00:14.5 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller [1022:7809] (rev 11)
    Subsystem: Hewlett-Packard Company FCH USB OHCI Controller [103c:2215]
    Kernel driver in use: ohci-pci
00:15.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Hudson PCI to PCI bridge (PCIE port 0) [1022:43a0]
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:15.2 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Hudson PCI to PCI bridge (PCIE port 2) [1022:43a2]
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:18.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 30h-3fh) Processor Function 0 [1022:141a]
00:18.1 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 30h-3fh) Processor Function 1 [1022:141b]
00:18.2 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 30h-3fh) Processor Function 2 [1022:141c]
00:18.3 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 30h-3fh) Processor Function 3 [1022:141d]
    Kernel driver in use: k10temp
    Kernel modules: k10temp
00:18.4 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 30h-3fh) Processor Function 4 [1022:141e]
    Kernel driver in use: fam15h_power
    Kernel modules: fam15h_power
00:18.5 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 30h-3fh) Processor Function 5 [1022:141f]
03:00.0 Ethernet controller [0200]: Broadcom Limited NetXtreme BCM5762 Gigabit Ethernet PCIe [14e4:1687] (rev 10)
    Subsystem: Hewlett-Packard Company NetXtreme BCM5762 Gigabit Ethernet PCIe [103c:2215]
    Kernel driver in use: tg3
    Kernel modules: tg3





```

---

### Post by winecurmudgeon2 on 2019-09-08
Mark it solved. Don't know why I didn't think of this earlier. I attached a $13 RJ45 USB ethernet adapter to the ethernet cable, and then plugged it into a USB port. I have a 1 gigabyte connection using the asix driver, and it has bypassed the Broadcom network card.

So far, so good. The ethernet connection has been running constantly for two days with no dropped connections, and I have tried to get it to drop.

---

