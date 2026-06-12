---
title: "Yet another broadcom issue (4311 card, HP dv6000z laptop) bcmwl5"
date: 2006-09-29
forum: Networking &amp; Wireless
---

### Post by enigma_0Z on 2006-09-29
First off, I'd like to say that the bcm43xx module does not work. The module loads fine and everything, but it does not actually create the extra ethernet device.

I know that people have gotten the bcmwl5 driver to work before, and I know that it is the one for me (My card is a broadcom "Unknown device 4311").

Ndiswrapper still fails to load, complaining about three ntoskrnl.exe errors:

```
[17179666.592000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[17179666.688000] ndiswrapper (import:239): unknown symbol: ntoskrnl.exe:'strrchr'
[17179666.688000] ndiswrapper (import:239): unknown symbol: ntoskrnl.exe:'MmFreeContiguousMemorySpecifyCache'
[17179666.688000] ndiswrapper (import:239): unknown symbol: ntoskrnl.exe:'MmAllocateContiguousMemorySpecifyCache'
[17179666.688000] ndiswrapper (import:239): unknown symbol: ntoskrnl.exe:'MmGetPhysicalAddress'
[17179666.688000] ndiswrapper (load_sys_files:218): couldn't prepare driver 'bcmwl5'
[17179666.692000] ndiswrapper (load_wrap_driver:112): loadndiswrapper failed (65280); check system log for messages from 'loadndisdriver'
[17180144.592000] ndiswrapper (free_all_objects:332): object ee6b0c9c type 2 was not freed, freeing it now
[17180439.868000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[17180439.872000] ndiswrapper (load_wrap_driver:112): loadndiswrapper failed (65280); check system log for messages from 'loadndisdriver'

```

lspci:
```
0000:00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
0000:00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
0000:00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
0000:00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
0000:00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
0000:00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
0000:00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
0000:00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
0000:00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
0000:00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
0000:00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
0000:00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
0000:00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
0000:00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
0000:00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
0000:00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
0000:00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
0000:00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
0000:00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
0000:00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
0000:00:10.1 0403: nVidia Corporation MCP51 High Definition Audio (rev a2)
0000:00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:03:00.0 Network controller: Broadcom Corporation: Unknown device 4311 (rev 01)
0000:05:00.0 VGA compatible controller: nVidia Corporation: Unknown device 01d6 (rev a1)
0000:07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd: Unknown device 0832
0000:07:05.1 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
0000:07:05.2 System peripheral: Ricoh Co Ltd: Unknown device 0843 (rev 01)
0000:07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
0000:07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

```

[edit]
Fixed it! The version of ndiswrappers that comes with Ubuntu is old compared to this driver. I built the latest version from source and everything works like it should (you can ignore the forcing ipsg-something-or-other from 0 to 2).

Look here: [http://www.ubuntuforums.org/showthread.php?t=140214&page=2](http://www.ubuntuforums.org/showthread.php?t=140214&page=2)
 near the bottom of the page!
[/edit]

---

