---
title: "Wifi issue in ubunutu dual booted with hp laptop"
date: 2019-10-11
forum: Networking &amp; Wireless
---

### Post by bhanu904 on 2019-10-11
Dual boot hp & ubuntu 


Suddenly my wifi adapters got missing i am using hp laptop with win 10 and ubuntu dual boot


I have done all the process mentioned here : [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)



This is the output of log 

[https://pastebin.com/8Nt6Cmbq](https://pastebin.com/8Nt6Cmbq)

---

### Post by praseodym on 2019-10-11
Please show

```
lspci -nnk
cat /sys/bus/sdio/devices/*
```

---

### Post by bhanu904 on 2019-10-11
> **praseodym said:**
> Please show

```
lspci -nnk
cat /sys/bus/sdio/devices/*
```


here is output :
```
lspci -nnk

00:00.0 Host bridge [0600]: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Host Bridge/DRAM Registers [8086:1904] (rev 08)
	Subsystem: Hewlett-Packard Company Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Host Bridge/DRAM Registers [103c:820c]
	Kernel driver in use: skl_uncore
00:02.0 VGA compatible controller [0300]: Intel Corporation Skylake GT2 [HD Graphics 520] [8086:1916] (rev 07)
	Subsystem: Hewlett-Packard Company Skylake GT2 [HD Graphics 520] [103c:820c]
	Kernel driver in use: i915
	Kernel modules: i915
00:04.0 Signal processing controller [1180]: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem [8086:1903] (rev 08)
	Subsystem: Hewlett-Packard Company Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem [103c:820c]
	Kernel driver in use: proc_thermal
	Kernel modules: processor_thermal_device
00:14.0 USB controller [0c03]: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller [8086:9d2f] (rev 21)
	Subsystem: Hewlett-Packard Company Sunrise Point-LP USB 3.0 xHCI Controller [103c:820c]
	Kernel driver in use: xhci_hcd
00:14.2 Signal processing controller [1180]: Intel Corporation Sunrise Point-LP Thermal subsystem [8086:9d31] (rev 21)
	Subsystem: Hewlett-Packard Company Sunrise Point-LP Thermal subsystem [103c:820c]
	Kernel driver in use: intel_pch_thermal
	Kernel modules: intel_pch_thermal
00:16.0 Communication controller [0780]: Intel Corporation Sunrise Point-LP CSME HECI #1 [8086:9d3a] (rev 21)
	Subsystem: Hewlett-Packard Company Sunrise Point-LP CSME HECI [103c:820c]
	Kernel driver in use: mei_me
	Kernel modules: mei_me
00:17.0 SATA controller [0106]: Intel Corporation Sunrise Point-LP SATA Controller [AHCI mode] [8086:9d03] (rev 21)
	Subsystem: Hewlett-Packard Company Sunrise Point-LP SATA Controller [AHCI mode] [103c:820c]
	Kernel driver in use: ahci
	Kernel modules: ahci
00:1c.0 PCI bridge [0604]: Intel Corporation Sunrise Point-LP PCI Express Root Port #1 [8086:9d10] (rev f1)
	Kernel driver in use: pcieport
00:1c.4 PCI bridge [0604]: Intel Corporation Sunrise Point-LP PCI Express Root Port #5 [8086:9d14] (rev f1)
	Kernel driver in use: pcieport
00:1c.5 PCI bridge [0604]: Intel Corporation Sunrise Point-LP PCI Express Root Port #6 [8086:9d15] (rev f1)
	Kernel driver in use: pcieport
00:1f.0 ISA bridge [0601]: Intel Corporation Sunrise Point-LP LPC Controller [8086:9d48] (rev 21)
	Subsystem: Hewlett-Packard Company Sunrise Point-LP LPC Controller [103c:820c]
00:1f.2 Memory controller [0580]: Intel Corporation Sunrise Point-LP PMC [8086:9d21] (rev 21)
	Subsystem: Hewlett-Packard Company Sunrise Point-LP PMC [103c:820c]
00:1f.3 Audio device [0403]: Intel Corporation Sunrise Point-LP HD Audio [8086:9d70] (rev 21)
	Subsystem: Hewlett-Packard Company Sunrise Point-LP HD Audio [103c:820c]
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel, snd_soc_skl
00:1f.4 SMBus [0c05]: Intel Corporation Sunrise Point-LP SMBus [8086:9d23] (rev 21)
	Subsystem: Hewlett-Packard Company Sunrise Point-LP SMBus [103c:820c]
	Kernel modules: i2c_i801
01:00.0 3D controller [0302]: NVIDIA Corporation GM108M [GeForce 940MX] [10de:134d] (rev a2)
	Subsystem: Hewlett-Packard Company GM108M [GeForce 940MX] [103c:820c]
	Kernel driver in use: nvidia
	Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS522A PCI Express Card Reader [10ec:522a] (rev 01)
	Subsystem: Hewlett-Packard Company RTS522A PCI Express Card Reader [103c:820c]
	Kernel driver in use: rtsx_pci
	Kernel modules: rtsx_pci
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL810xE PCI Express Fast Ethernet controller [10ec:8136] (rev 0a)
	Subsystem: Hewlett-Packard Company RTL810xE PCI Express Fast Ethernet controller [103c:820c]
	Kernel driver in use: r8169
	Kernel modules: r8169
```


---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

cat /sys/bus/sdio/devices/*

cat: '/sys/bus/sdio/devices/*': No such file or directory





---------------------------------------------------------------------------

I always have issues. sometimes they work and sometimes they dont

---

### Post by praseodym on 2019-10-11
Does it work in Win10? Hardware issue?

---

### Post by bhanu904 on 2019-10-11
before the last update on windows 10 it worked on ubunutu.. after some update.. now it doesnt work on either of those

---

### Post by bhanu904 on 2019-10-11
> **praseodym said:**
> Does it work in Win10? Hardware issue?

[COLOR=#000000]before the last update on windows 10 it worked on ubunutu.. after some update.. now it doesnt work on either of those[/COLOR]

---

### Post by bhanu904 on 2019-10-17
> **bhanu904 said:**
> Dual boot hp & ubuntu 


Suddenly my wifi adapters got missing i am using hp laptop with win 10 and ubuntu dual boot


I have done all the process mentioned here : [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)



This is the output of log 

[https://pastebin.com/8Nt6Cmbq](https://pastebin.com/8Nt6Cmbq)

Bump i need some help havent solved this yet

---

