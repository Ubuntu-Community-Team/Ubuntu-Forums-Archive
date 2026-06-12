---
title: "Please help interpret this..."
date: 2010-10-22
forum: New to Ubuntu
---

### Post by BugBuster on 2010-10-22
This is my output of lspci:
```
 
$lspci -knn
00:00.0 Host bridge [0600]: ATI Technologies Inc RS690 Host Bridge [1002:7910]
	Subsystem: ATI Technologies Inc RS690 Host Bridge [1002:7910]
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx) [1002:7912]
00:07.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3) [1002:7917]
	Kernel driver in use: pcieport
00:12.0 SATA controller [0106]: ATI Technologies Inc SB600 Non-Raid-5 SATA [1002:4380]
	Subsystem: Micro-Star International Co., Ltd. Device [1462:7329]
	Kernel driver in use: ahci
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI0) [1002:4387]
	Subsystem: Micro-Star International Co., Ltd. Device [1462:7373]
	Kernel driver in use: ohci_hcd
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI1) [1002:4388]
	Subsystem: Micro-Star International Co., Ltd. Device [1462:7373]
	Kernel driver in use: ohci_hcd
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI2) [1002:4389]
	Subsystem: Micro-Star International Co., Ltd. Device [1462:7373]
	Kernel driver in use: ohci_hcd
00:13.3 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI3) [1002:438a]
	Subsystem: Micro-Star International Co., Ltd. Device [1462:7373]
	Kernel driver in use: ohci_hcd
00:13.4 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI4) [1002:438b]
	Subsystem: Micro-Star International Co., Ltd. Device [1462:7373]
	Kernel driver in use: ohci_hcd
00:13.5 USB Controller [0c03]: ATI Technologies Inc SB600 USB Controller (EHCI) [1002:4386]
	Subsystem: Micro-Star International Co., Ltd. Device [1462:7373]
	Kernel driver in use: ehci_hcd
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 14)
	Subsystem: Micro-Star International Co., Ltd. Device [1462:7373]
00:14.1 IDE interface [0101]: ATI Technologies Inc SB600 IDE [1002:438c]
	Subsystem: Micro-Star International Co., Ltd. Device [1462:7373]
	Kernel driver in use: pata_atiixp
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]
	Subsystem: Micro-Star International Co., Ltd. Device [1462:7373]
	Kernel driver in use: HDA Intel
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB600 PCI to LPC Bridge [1002:438d]
	Subsystem: Micro-Star International Co., Ltd. Device [1462:7373]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
	Kernel driver in use: k8temp
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS690 [Radeon X1200 Series] [1002:791e]
	Subsystem: Micro-Star International Co., Ltd. K9AG Neo2 [1462:7327]
01:05.2 Audio device [0403]: ATI Technologies Inc Radeon X1200 Series Audio Controller [1002:7919]
	Subsystem: ATI Technologies Inc Radeon X1200 Series Audio Controller [1002:7919]
	Kernel driver in use: HDA Intel
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)
	Subsystem: Micro-Star International Co., Ltd. Device [1462:373c]
	Kernel driver in use: r8169
03:02.0 Ethernet controller [0200]: D-Link System Inc DGE-530T Gigabit Ethernet Adapter (rev 11) [1186:4b01] (rev 11)
	Subsystem: D-Link System Inc DGE-530T Gigabit Ethernet Adapter (rev 11) [1186:4b01]
	Kernel driver in use: skge
03:03.0 Communication controller [0780]: Conexant Systems, Inc. Conexant SoftK56 Data/Fax Modem [14f1:2f50] (rev 01)
	Subsystem: Conexant Systems, Inc. Device [14f1:205f]

```

I notice that some entries show the kernel modules in use for that bit of hardware while some don't...So does this mean that the drivers for those entries that do not have "Kernel module in use:' line are missing? In other words are these parts not functional?

I know about the Data/Fax modem for sure as it lacks the drivers..but what about the others?

---

### Post by Chesamo on 2010-10-22
iirc, all of the lines that lack the "kernel driver in use" are things that are handled by the CPU hardware instead of the OS.

---

### Post by BugBuster on 2010-10-22
> **Chesamo said:**
> iirc, all of the lines that lack the "kernel driver in use" are things that are handled by the CPU hardware instead of the OS.

Do you mean by the cpu driver?

---

### Post by anewguy on 2010-10-22
The actual CPU hardware built in to your motherboard.  Be it just the CPU, or the CPU and a combination of north and possibly south bridge chipsets.  All hardware functions - no driver involved.

Dave ;)

---

### Post by Chesamo on 2010-10-22
> **BugBuster said:**
> Do you mean by the cpu driver?
...CPUs don't need drivers. The kernel just has to be compiled with its instruction set.

---

