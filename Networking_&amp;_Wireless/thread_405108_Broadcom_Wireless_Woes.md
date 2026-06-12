---
title: "Broadcom Wireless Woes"
date: 2007-04-09
forum: Networking &amp; Wireless
---

### Post by Eigenwert on 2007-04-09
I've been using the 64bit version of Edgy for some time now. A few days ago I decided to dual boot Edgy and Feisty Fawn just to see how Feisty worked with my system. Up until I installed Feisty my wireless (Broadcom 4311 card) was working perfectly. Since then my wireless is broken. Typing in "lspci" shows no wireless adapter at all, and no other programs are seeing my wireless card. Does anyone have any ideas or suggestions on how to fix this?

Thanks

EW

---

### Post by bdogg64 on 2007-04-09
> **Eigenwert said:**
> I've been using the 64bit version of Edgy for some time now. A few days ago I decided to dual boot Edgy and Feisty Fawn just to see how Feisty worked with my system. Up until I installed Feisty my wireless (Broadcom 4311 card) was working perfectly. Since then my wireless is broken. Typing in "lspci" shows no wireless adapter at all, and no other programs are seeing my wireless card. Does anyone have any ideas or suggestions on how to fix this?

Thanks

EW

This should work for you. I have the same card.

[http://www.ubuntuforums.org/showthread.php?t=346083](http://www.ubuntuforums.org/showthread.php?t=346083)

---

### Post by Eigenwert on 2007-04-09
Thanks for the reply, but that doesn't really address my problem. Despite the external switch being in the "on" position for my wireless card, ubuntu is not even detecting the card. As I said, the output from "lspci" contains nothing indicating a wireless adapter at all. I know it's there because I had it working before (for 4 months, even!).

EW

---

### Post by bdogg64 on 2007-04-09
> **Eigenwert said:**
> Thanks for the reply, but that doesn't really address my problem. Despite the external switch being in the "on" position for my wireless card, ubuntu is not even detecting the card. As I said, the output from "lspci" contains nothing indicating a wireless adapter at all. I know it's there because I had it working before (for 4 months, even!).

EW

Ok, is your wireless not working in either Edgy or Feisty now? Or is it just feisty? Are the wireless indicators on your laptop showing that it is at least present?

---

### Post by Eigenwert on 2007-04-09
Wireless is not working on either Edgy or Feisty. The external indicator on my laptop shows that the wireless card is present and on (blue light as opposed to an orange light). Just for laughs, here's the output of "lspci" (on Edgy)
```


00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
05:00.0 VGA compatible controller: nVidia Corporation Unknown device 01d6 (rev a1)
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
07:05.1 Class 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

```

EW

---

### Post by bdogg64 on 2007-04-09
Can you post the output from

```
dmesg
```

---

### Post by Eigenwert on 2007-04-09
```
[    0.000000] Bootdata ok (command line is root=/dev/sda5 ro quiet splash noapic nolapic)
[    0.000000] Linux version 2.6.17-11-generic (root@king) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Thu Feb 1 18:03:05 UTC 2007 (Ubuntu 2.6.17-11.35-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ff00000 (usable)
[    0.000000]  BIOS-e820: 000000003ff00000 - 000000003ff17000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ff17000 - 000000003ff80000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003ff80000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v000 HP                                    ) @ 0x00000000000f8970
[    0.000000] ACPI: RSDT (v001 HP       RSDT   0x06040000  LTP 0x00000000) @ 0x000000003ff0fc14
[    0.000000] ACPI: FADT (v001 HP     MCP51M   0x06040000 PTL_ 0x000f4240) @ 0x000000003ff16dcd
[    0.000000] ACPI: SSDT (v001 HP     POWERNOW 0x06040000  LTP 0x00000001) @ 0x000000003ff16e41
[    0.000000] ACPI: MCFG (v001 HP       MCFG   0x06040000  LTP 0x00000000) @ 0x000000003ff16f56
[    0.000000] ACPI: MADT (v001 HP       APIC   0x06040000  LTP 0x00000000) @ 0x000000003ff16f92
[    0.000000] ACPI: BOOT (v001     HP $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x000000003ff16fd8
[    0.000000] ACPI: DSDT (v001 HP       MCP51M 0x06040000 MSFT 0x0100000e) @ 0x0000000000000000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] Number of nodes 1
[    0.000000] Node 0 MemBase 0000000000000000 Limit 000000003ff00000
[    0.000000] NUMA: Using 63 for the hash shift.
[    0.000000] Using node hash shift of 63
[    0.000000] Bootmem setup node 0 0000000000000000-000000003ff00000
[    0.000000] On node 0 totalpages: 256857
[    0.000000]   DMA zone: 2589 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 254268 pages, LIFO batch:31
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:12 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: Skipping IOAPIC probe due to 'noapic' option.
[    0.000000] Using ACPI for processor (LAPIC) configuration information
[    0.000000] Intel MultiProcessor Specification v1.4
[    0.000000]     Virtual Wire compatibility mode.
[    0.000000] OEM ID: nVIDIA   Product ID: C51-MCP51    APIC at: 0xFEE00000
[    0.000000] I/O APIC #1 Version 17 at 0xFEC00000.
[    0.000000] Setting APIC routing to physical flat
[    0.000000] Processors: 1
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] Checking aperture...
[    0.000000] CPU 0: aperture @ c40000000 size 32 MB
[    0.000000] Aperture from northbridge cpu 0 too small (32 MB)
[    0.000000] No AGP bridge found
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Built 1 zonelists
[    0.000000] Kernel command line: root=/dev/sda5 ro quiet splash noapic nolapic
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] time.c: Using 3.579545 MHz WALL PM GTOD PIT/TSC timer.
[    0.000000] time.c: Detected 2009.177 MHz processor.
[   15.947773] Console: colour VGA+ 80x25
[   15.948304] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   15.949223] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[   15.959818] Memory: 1019720k/1047552k available (2129k kernel code, 27436k reserved, 1424k data, 188k init)
[   16.039470] Calibrating delay using timer specific routine.. 4021.89 BogoMIPS (lpj=8043797)
[   16.039519] Security Framework v1.0.0 initialized
[   16.039524] SELinux:  Disabled at boot.
[   16.039545] Mount-cache hash table entries: 256
[   16.039658] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   16.039661] CPU: L2 Cache: 512K (64 bytes/line)
[   16.039664] CPU 0/0(1) -> Node 0 -> Core 0
[   16.039675] SMP alternatives: switching to UP code
[   16.039745] Freeing SMP alternatives: 20k freed
[   16.039861] checking if image is initramfs... it is
[   16.550257] Freeing initrd memory: 6051k freed
[   16.553618] ACPI: Core revision 20060707
[   16.556481] ACPI: Looking for DSDT ... not found!
[   16.611507] Using local APIC timer interrupts.
[   16.661217] result 12557371
[   16.661219] Detected 12.557 MHz APIC timer.
[   16.662736] Brought up 1 CPUs
[   16.662744] testing NMI watchdog ... OK.
[   16.702780] migration_cost=0
[   16.702998] NET: Registered protocol family 16
[   16.703021] ACPI: bus type pci registered
[   16.706374] PCI: Using MMCONFIG at e0000000
[   16.706404] PCI: No mmconfig possible on device 0:18
[   16.706580] PCI: No mmconfig possible on device 7:5
[   16.711359] ACPI: Interpreter enabled
[   16.711361] ACPI: Using PIC for interrupt routing
[   16.712161] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   16.712164] PCI: Probing PCI hardware (bus 00)
[   16.712328] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[   16.714032] PCI: Ignoring BAR0-3 of IDE controller 0000:00:0d.0
[   16.714371] Boot video device is 0000:05:00.0
[   16.714711] PCI: Transparent bridge - 0000:00:10.0
[   16.714740] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   16.745660] ACPI: Embedded Controller [EC0] (gpe 16) interrupt mode.
[   16.746049] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[   16.746898] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR0._PRT]
[   16.747158] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[   16.747312] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
[   16.747624] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   16.747902] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 *11 14 15)
[   16.748177] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 *11 14 15)
[   16.748451] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   16.748724] ACPI: PCI Interrupt Link [LK1E] (IRQs 5 7 9 10 *11 14 15)
[   16.748996] ACPI: PCI Interrupt Link [LK2E] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   16.749274] ACPI: PCI Interrupt Link [LK3E] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   16.749548] ACPI: PCI Interrupt Link [LK4E] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   16.749822] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 *10 11 14 15)
[   16.750095] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 *10 11 14 15)
[   16.750370] ACPI: PCI Interrupt Link [LUS0] (IRQs 5 7 9 10 *11 14 15)
[   16.750665] ACPI: PCI Interrupt Link [LUS2] (IRQs 5 *7 9 10 11 14 15)
[   16.750940] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 *10 11 14 15)
[   16.751216] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   16.751490] ACPI: PCI Interrupt Link [LACI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   16.751764] ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   16.752038] ACPI: PCI Interrupt Link [LPID] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   16.752319] ACPI: PCI Interrupt Link [LTID] (IRQs *5 7 9 10 11 14 15)
[   16.752595] ACPI: PCI Interrupt Link [LSI1] (IRQs 5 7 9 *10 11 14 15), disabled.
[   16.752705] Linux Plug and Play Support v0.97 (c) Adam Belay
[   16.752714] pnp: PnP ACPI init
[   16.754868] pnp: PnP ACPI: found 11 devices
[   16.754913] PCI: Using ACPI for IRQ routing
[   16.754917] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   16.755039] PCI-DMA: Disabling IOMMU.
[   16.755467] pnp: 00:03: ioport range 0x1000-0x107f could not be reserved
[   16.755470] pnp: 00:03: ioport range 0x1080-0x10ff has been reserved
[   16.755472] pnp: 00:03: ioport range 0x1400-0x147f has been reserved
[   16.755475] pnp: 00:03: ioport range 0x1480-0x14ff could not be reserved
[   16.755478] pnp: 00:03: ioport range 0x1800-0x187f has been reserved
[   16.755481] pnp: 00:03: ioport range 0x1880-0x18ff has been reserved
[   16.755483] pnp: 00:03: ioport range 0x2000-0x203f has been reserved
[   16.755664] PCI: Bridge: 0000:00:02.0
[   16.755666]   IO window: 4000-4fff
[   16.755669]   MEM window: c0200000-c03fffff
[   16.755672]   PREFETCH window: c3200000-c33fffff
[   16.755674] PCI: Bridge: 0000:00:03.0
[   16.755676]   IO window: 5000-5fff
[   16.755679]   MEM window: c0400000-c05fffff
[   16.755681]   PREFETCH window: c3400000-c35fffff
[   16.755686] PCI: Failed to allocate mem resource #6:20000@e0000000 for 0000:05:00.0
[   16.755688] PCI: Bridge: 0000:00:04.0
[   16.755690]   IO window: disabled.
[   16.755692]   MEM window: c1000000-c2ffffff
[   16.755695]   PREFETCH window: d0000000-dfffffff
[   16.755698] PCI: Bridge: 0000:00:10.0
[   16.755699]   IO window: disabled.
[   16.755703]   MEM window: c3000000-c30fffff
[   16.755705]   PREFETCH window: disabled.
[   16.755713] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   16.755718] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   16.755723] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   16.755729] PCI: Setting latency timer of device 0000:00:10.0 to 64
[   16.755785] NET: Registered protocol family 2
[   16.934398] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[   16.934585] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[   16.935910] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   16.936590] TCP: Hash tables configured (established 131072 bind 65536)
[   16.936593] TCP reno registered
[   16.936776] Simple Boot Flag at 0x36 set to 0x1
[   16.936915] IA32 emulation $Id: sys_ia32.c,v 1.32 2002/03/24 13:02:28 ak Exp $
[   16.937235] audit: initializing netlink socket (disabled)
[   16.937243] audit(1176135920.992:1): initialized
[   16.937368] VFS: Disk quotas dquot_6.5.1
[   16.937385] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   16.937428] Initializing Cryptographic API
[   16.937431] io scheduler noop registered
[   16.937438] io scheduler anticipatory registered
[   16.937444] io scheduler deadline registered
[   16.937460] io scheduler cfq registered (default)
[   16.937858] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   16.937862] pcie_portdrv_probe->Dev[02fc:10de] has invalid IRQ. Check vendor BIOS
[   16.937876] assign_interrupt_mode Found MSI capability
[   16.937906] Allocate Port Service[0000:00:02.0:pcie00]
[   16.937940] Allocate Port Service[0000:00:02.0:pcie03]
[   16.937969] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   16.937972] pcie_portdrv_probe->Dev[02fd:10de] has invalid IRQ. Check vendor BIOS
[   16.937986] assign_interrupt_mode Found MSI capability
[   16.938003] Allocate Port Service[0000:00:03.0:pcie00]
[   16.938029] Allocate Port Service[0000:00:03.0:pcie03]
[   16.938061] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   16.938064] pcie_portdrv_probe->Dev[02fb:10de] has invalid IRQ. Check vendor BIOS
[   16.938078] assign_interrupt_mode Found MSI capability
[   16.938094] Allocate Port Service[0000:00:04.0:pcie00]
[   16.938121] Allocate Port Service[0000:00:04.0:pcie03]
[   16.957444] Real Time Clock Driver v1.12ac
[   16.957479] Linux agpgart interface v0.101 (c) Dave Jones
[   16.957482] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   16.957933] mice: PS/2 mouse device common for all mice
[   16.958437] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   16.958604] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   16.958607] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   16.958837] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   16.986026] serio: i8042 AUX port at 0x60,0x64 irq 12
[   16.987859] serio: i8042 KBD port at 0x60,0x64 irq 1
[   16.988056] TCP bic registered
[   16.988063] NET: Registered protocol family 1
[   16.988068] NET: Registered protocol family 8
[   16.988070] NET: Registered protocol family 20
[   16.991403] ACPI: (supports S0 S3 S4 S5)
[   16.991445] drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   16.991463] Freeing unused kernel memory: 188k freed
[   17.083199] input: AT Translated Set 2 keyboard as /class/input/input0
[   17.088938] atkbd.c: Spurious ACK on isa0060/serio0. Some program, like XFree86, might be trying access hardware directly.
[   17.123610] vga16fb: initializing
[   17.123615] vga16fb: mapped to 0xffff8100000a0000
[   17.323956] Console: switching to colour frame buffer device 80x25
[   17.323961] fb0: VGA16 VGA frame buffer device
[   18.354261] Capability LSM initialized
[   18.380274] ACPI Exception (acpi_processor-0693): AE_NOT_FOUND, Processor Device is not present [20060707]
[   18.380279] ACPI: Getting cpuindex for acpiid 0x1
[   18.381989] ACPI: Thermal Zone [THRM] (55 C)
[   18.711002] SCSI subsystem initialized
[   18.714345] libata version 1.20 loaded.
[   18.715344] sata_nv 0000:00:0e.0: version 0.8
[   18.715355] PCI: Enabling device 0000:00:0e.0 (0005 -> 0007)
[   18.715622] ACPI: PCI Interrupt Link [LTID] enabled at IRQ 5
[   18.715625] PCI: setting IRQ 5 as level-triggered
[   18.715628] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LTID] -> GSI 5 (level, low) -> IRQ 5
[   18.715711] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   18.715772] ata1: SATA max UDMA/133 cmd 0x30C0 ctl 0x30B6 bmdma 0x3090 irq 5
[   18.715792] ata2: SATA max UDMA/133 cmd 0x30B8 ctl 0x30B2 bmdma 0x3098 irq 5
[   18.919746] ata1: SATA link up 1.5 Gbps (SStatus 113)
[   19.087716] ata1: dev 0 cfg 49:2f00 82:706b 83:7c09 84:6023 85:7069 86:3c09 87:6023 88:203f
[   19.087720] ata1: dev 0 ATA-7, max UDMA/100, 156301488 sectors: LBA48
[   19.099697] ata1: dev 0 configured for UDMA/100
[   19.099700] scsi0 : sata_nv
[   19.307236] ata2: SATA link down (SStatus 0)
[   19.307239] scsi1 : sata_nv
[   19.307774]   Vendor: ATA       Model: TOSHIBA MK8034GS  Rev: AH30
[   19.307782]   Type:   Direct-Access                      ANSI SCSI revision: 05
[   19.308582] NFORCE-MCP51: IDE controller at PCI slot 0000:00:0d.0
[   19.308598] NFORCE-MCP51: chipset revision 241
[   19.308600] NFORCE-MCP51: not 100% native mode: will probe irqs later
[   19.308603] NFORCE-MCP51: BIOS didn't set cable bits correctly. Enabling workaround.
[   19.308608] NFORCE-MCP51: 0000:00:0d.0 (rev f1) UDMA133 controller
[   19.308615]     ide0: BM-DMA at 0x3080-0x3087, BIOS settings: hda:DMA, hdb:pio
[   19.308623] Probing IDE interface ide0...
[   19.323554] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[   19.323565] sda: Write Protect is off
[   19.323567] sda: Mode Sense: 00 3a 00 00
[   19.323579] SCSI device sda: drive cache: write back
[   19.323623] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[   19.323630] sda: Write Protect is off
[   19.323632] sda: Mode Sense: 00 3a 00 00
[   19.323643] SCSI device sda: drive cache: write back
[   19.323647]  sda: sda1 sda2 < sda5 sda6 sda7 > sda4
[   19.427001] sd 0:0:0:0: Attached scsi disk sda
[   20.046371] hda: HL-DT-STCD-RW/DVD DRIVE GCC-4244N, ATAPI CD/DVD-ROM drive
[   20.382522] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   20.392106] hda: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, DMA
[   20.392113] Uniform CD-ROM driver Revision: 3.20
[   20.513938] Probing IDE interface ide1...
[   20.557266] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.54.
[   20.557563] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 10
[   20.557566] PCI: setting IRQ 10 as level-triggered
[   20.557569] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [LMAC] -> GSI 10 (level, low) -> IRQ 10
[   20.557575] PCI: Setting latency timer of device 0000:00:14.0 to 64
[   20.557582] forcedeth: using HIGHDMA
[   20.588778] ieee1394: Initialized config rom entry `ip1394'
[   20.599829] usbcore: registered new driver usbfs
[   20.600256] usbcore: registered new driver hub
[   20.601914] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[   21.081225] eth0: forcedeth.c: subsystem: 0103c:30b7 bound to 0000:00:14.0
[   21.082143] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 11
[   21.082147] PCI: setting IRQ 11 as level-triggered
[   21.082151] ACPI: PCI Interrupt 0000:07:05.0[A] -> Link [LNK1] -> GSI 11 (level, low) -> IRQ 11
[   21.133649] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 11
[   21.133653] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LUS0] -> GSI 11 (level, low) -> IRQ 11
[   21.133734] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   21.133739] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[   21.133991] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[   21.336102] ohci_hcd 0000:00:0b.0: irq 11, io mem 0xc0004000
[   21.338167] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[c3000000-c30007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   21.394686] usb usb1: configuration #1 chosen from 1 choice
[   21.394774] hub 1-0:1.0: USB hub found
[   21.394786] hub 1-0:1.0: 8 ports detected
[   21.500761] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 7
[   21.500764] PCI: setting IRQ 7 as level-triggered
[   21.500767] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [LUS2] -> GSI 7 (level, low) -> IRQ 7
[   21.500853] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[   21.500858] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[   21.501035] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
[   21.501064] ehci_hcd 0000:00:0b.1: debug port 1
[   21.501068] PCI: cache line size of 64 is not supported by device 0000:00:0b.1
[   21.501076] ehci_hcd 0000:00:0b.1: irq 7, io mem 0xc0005000
[   21.501083] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   21.501198] usb usb2: configuration #1 chosen from 1 choice
[   21.501285] hub 2-0:1.0: USB hub found
[   21.501292] hub 2-0:1.0: 8 ports detected
[   21.680118] Attempting manual resume
[   21.725806] kjournald starting.  Commit interval 5 seconds
[   21.725816] EXT3-fs: mounted filesystem with ordered data mode.
[   22.459117] usb 1-3: new full speed USB device using ohci_hcd and address 2
[   22.619063] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[009fc0009484d800]
[   22.697880] usb 1-3: configuration #1 chosen from 1 choice
[   23.006393] usb 1-6: new low speed USB device using ohci_hcd and address 3
[   23.223182] usb 1-6: configuration #1 chosen from 1 choice
[   32.409331] input: PC Speaker as /class/input/input1
[   32.627031] sdhci: Secure Digital Host Controller Interface driver, 0.12
[   32.627034] sdhci: Copyright(c) Pierre Ossman
[   32.627066] sdhci: SDHCI controller found at 0000:07:05.1 [1180:0822] (rev 19)
[   32.627356] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 11
[   32.627359] ACPI: PCI Interrupt 0000:07:05.1[B] -> Link [LNK2] -> GSI 11 (level, low) -> IRQ 11
[   32.627515] mmc0: SDHCI at 0xc3000800 irq 11 DMA
[   32.763144] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   32.769533] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   33.094737] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000
[   33.106519] Bluetooth: Core ver 2.8
[   33.106523] NET: Registered protocol family 31
[   33.106524] Bluetooth: HCI device and connection manager initialized
[   33.106536] Bluetooth: HCI socket layer initialized
[   33.137412] usbcore: registered new driver hiddev
[   33.145946] input: USB Mouse as /class/input/input2
[   33.145996] input: USB HID v1.00 Mouse [USB Mouse] on usb-0000:00:0b.0-6
[   33.146007] usbcore: registered new driver usbhid
[   33.146010] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   33.159074] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   33.161245] Bluetooth: HCI USB driver ver 2.9
[   33.162964] usbcore: registered new driver hci_usb
[   33.194516] ts: Compaq touchscreen protocol output
[   33.410805] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   33.440941] NET: Registered protocol family 10
[   33.441029] lo: Disabled Privacy Extensions
[   33.441385] IPv6 over IPv4 tunneling driver
[   33.615789] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 10
[   33.615793] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LAZA] -> GSI 10 (level, low) -> IRQ 10
[   33.615886] PCI: Setting latency timer of device 0000:00:10.1 to 64
[   33.998914] nvidia: module license 'NVIDIA' taints kernel.
[   34.261546] ACPI: PCI Interrupt Link [LK1E] enabled at IRQ 11
[   34.261550] ACPI: PCI Interrupt 0000:05:00.0[A] -> Link [LK1E] -> GSI 11 (level, low) -> IRQ 11
[   34.261558] PCI: Setting latency timer of device 0000:05:00.0 to 64
[   34.261689] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  1.0-9755  Mon Feb 26 23:16:31 PST 2007
[   34.488232] lp: driver loaded but no devices found
[   34.523443] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[   34.523446] ieee1394: sbp2: Try serialize_io=0 for better performance
[   34.562422] ndiswrapper version 1.41 loaded (smp=yes)
[   34.642943] usbcore: registered new driver ndiswrapper
[   34.738503] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.60.2)
[   34.738541] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x10 (1150 mV)
[   34.738544] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x12 (1100 mV)
[   34.738547] powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x14 (1050 mV)
[   34.738549] powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x18 (950 mV)
[   34.738553] cpu_init done, current fid 0xc, vid 0x10
[   34.765141] Adding 2048276k swap on /dev/disk/by-uuid/21ac8080-04e2-4a06-97a3-cf860d3fc865.  Priority:-1 extents:1 across:2048276k
[   34.845745] EXT3 FS on sda5, internal journal
[   35.073471] kjournald starting.  Commit interval 5 seconds
[   35.082726] EXT3 FS on sda7, internal journal
[   35.082731] EXT3-fs: mounted filesystem with ordered data mode.
[   37.649357] ACPI: AC Adapter [ACAD] (on-line)
[   37.683904] ACPI: Battery Slot [BAT0] (battery present)
[   37.696192] ACPI: Power Button (FF) [PWRF]
[   37.696200] ACPI: Power Button (CM) [PWRB]
[   37.696207] ACPI: Sleep Button (CM) [SLPB]
[   37.696213] ACPI: Lid Switch [LID]
[   37.776171] ibm_acpi: ec object not found
[   37.800528] pcc_acpi: loading...
[   37.839412] wmi_add device=ffff81003dcdd800
[   37.839415] calling WQBA
[   37.868667] ACPI: Video Device [UVGA] (multi-head: yes  rom: no  post: no)
[   37.868789] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   43.921442] eth0: no IPv6 routers present
[   49.364010] Bluetooth: L2CAP ver 2.8
[   49.364013] Bluetooth: L2CAP socket layer initialized
[   49.392452] Bluetooth: RFCOMM socket layer initialized
[   49.392466] Bluetooth: RFCOMM TTY layer initialized
[   49.392468] Bluetooth: RFCOMM ver 1.7
[   56.357245] ISO 9660 Extensions: Microsoft Joliet Level 3
[   56.586464] ISOFS: changing to secondary root
[  586.055942] eth0: no IPv6 routers present

```

---

### Post by bdogg64 on 2007-04-09
Ok, I think I ran into the same problem you are having with kernel 2.6.17-11. I was using 2.6.17-10 up until the kernel upgrade was released and one i booted the newer kernel image, my wireless stopped working altogether. Have you tried booting with 2.6.17-10 to see if your wireless still works?

---

### Post by Eigenwert on 2007-04-09
I had to boot into recovery mode because of my nVidia drivers, but "lspci" still didn't show anything. 

Man, this is frustrating. I don't understand how installing Feisty could break wireless for Edgy as well.

EW

---

### Post by bdogg64 on 2007-04-09
> **Eigenwert said:**
> I had to boot into recovery mode because of my nVidia drivers, but "lspci" still didn't show anything. 

Man, this is frustrating. I don't understand how installing Feisty could break wireless for Edgy as well.

EW

Can you post your **dmesg** from booting into kernel 2.6.17-10 ? Which kernel are you running in feisty? Post that too

---

### Post by Eigenwert on 2007-04-09
dmesg into 2.6.17-10 gives the following:

```
[    0.000000] Bootdata ok (command line is root=/dev/sda5 ro quiet splash noapic nolapic)
[    0.000000] Linux version 2.6.17-10-generic (root@king) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Tue Dec 5 21:16:35 UTC 2006 (Ubuntu 2.6.17-10.34-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ff00000 (usable)
[    0.000000]  BIOS-e820: 000000003ff00000 - 000000003ff17000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ff17000 - 000000003ff80000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003ff80000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v000 HP                                    ) @ 0x00000000000f8970
[    0.000000] ACPI: RSDT (v001 HP       RSDT   0x06040000  LTP 0x00000000) @ 0x000000003ff0fc14
[    0.000000] ACPI: FADT (v001 HP     MCP51M   0x06040000 PTL_ 0x000f4240) @ 0x000000003ff16dcd
[    0.000000] ACPI: SSDT (v001 HP     POWERNOW 0x06040000  LTP 0x00000001) @ 0x000000003ff16e41
[    0.000000] ACPI: MCFG (v001 HP       MCFG   0x06040000  LTP 0x00000000) @ 0x000000003ff16f56
[    0.000000] ACPI: MADT (v001 HP       APIC   0x06040000  LTP 0x00000000) @ 0x000000003ff16f92
[    0.000000] ACPI: BOOT (v001     HP $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x000000003ff16fd8
[    0.000000] ACPI: DSDT (v001 HP       MCP51M 0x06040000 MSFT 0x0100000e) @ 0x0000000000000000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] Number of nodes 1
[    0.000000] Node 0 MemBase 0000000000000000 Limit 000000003ff00000
[    0.000000] NUMA: Using 63 for the hash shift.
[    0.000000] Using node hash shift of 63
[    0.000000] Bootmem setup node 0 0000000000000000-000000003ff00000
[    0.000000] On node 0 totalpages: 256857
[    0.000000]   DMA zone: 2589 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 254268 pages, LIFO batch:31
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:12 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: Skipping IOAPIC probe due to 'noapic' option.
[    0.000000] Using ACPI for processor (LAPIC) configuration information
[    0.000000] Intel MultiProcessor Specification v1.4
[    0.000000]     Virtual Wire compatibility mode.
[    0.000000] OEM ID: nVIDIA   Product ID: C51-MCP51    APIC at: 0xFEE00000
[    0.000000] I/O APIC #1 Version 17 at 0xFEC00000.
[    0.000000] Setting APIC routing to physical flat
[    0.000000] Processors: 1
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] Checking aperture...
[    0.000000] CPU 0: aperture @ c40000000 size 32 MB
[    0.000000] Aperture from northbridge cpu 0 too small (32 MB)
[    0.000000] No AGP bridge found
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Built 1 zonelists
[    0.000000] Kernel command line: root=/dev/sda5 ro quiet splash noapic nolapic
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] time.c: Using 3.579545 MHz WALL PM GTOD PIT/TSC timer.
[    0.000000] time.c: Detected 2009.158 MHz processor.
[   15.127822] Console: colour VGA+ 80x25
[   15.128354] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   15.129273] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[   15.139878] Memory: 1020020k/1047552k available (2129k kernel code, 27136k reserved, 1424k data, 188k init)
[   15.219514] Calibrating delay using timer specific routine.. 4021.91 BogoMIPS (lpj=8043827)
[   15.219566] Security Framework v1.0.0 initialized
[   15.219571] SELinux:  Disabled at boot.
[   15.219591] Mount-cache hash table entries: 256
[   15.219708] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   15.219711] CPU: L2 Cache: 512K (64 bytes/line)
[   15.219714] CPU 0/0(1) -> Node 0 -> Core 0
[   15.219726] SMP alternatives: switching to UP code
[   15.219794] Freeing SMP alternatives: 20k freed
[   15.219911] checking if image is initramfs... it is
[   15.709652] Freeing initrd memory: 5751k freed
[   15.712864] ACPI: Core revision 20060707
[   15.715759] ACPI: Looking for DSDT ... not found!
[   15.770936] Using local APIC timer interrupts.
[   15.820646] result 12557254
[   15.820647] Detected 12.557 MHz APIC timer.
[   15.822804] Brought up 1 CPUs
[   15.822812] testing NMI watchdog ... OK.
[   15.862850] migration_cost=0
[   15.863069] NET: Registered protocol family 16
[   15.863090] ACPI: bus type pci registered
[   15.866440] PCI: Using MMCONFIG at e0000000
[   15.866469] PCI: No mmconfig possible on device 0:18
[   15.866646] PCI: No mmconfig possible on device 7:5
[   15.871496] ACPI: Interpreter enabled
[   15.871498] ACPI: Using PIC for interrupt routing
[   15.872308] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   15.872311] PCI: Probing PCI hardware (bus 00)
[   15.872474] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[   15.874193] PCI: Ignoring BAR0-3 of IDE controller 0000:00:0d.0
[   15.874539] Boot video device is 0000:05:00.0
[   15.874880] PCI: Transparent bridge - 0000:00:10.0
[   15.874908] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   15.906298] ACPI: Embedded Controller [EC0] (gpe 16) interrupt mode.
[   15.906711] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[   15.907545] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR0._PRT]
[   15.907806] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[   15.907961] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
[   15.908275] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   15.908559] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 *11 14 15)
[   15.908844] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 *11 14 15)
[   15.909124] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   15.909405] ACPI: PCI Interrupt Link [LK1E] (IRQs 5 7 9 10 *11 14 15)
[   15.909685] ACPI: PCI Interrupt Link [LK2E] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   15.909966] ACPI: PCI Interrupt Link [LK3E] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   15.910247] ACPI: PCI Interrupt Link [LK4E] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   15.910528] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 *10 11 14 15)
[   15.910824] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 *10 11 14 15)
[   15.911106] ACPI: PCI Interrupt Link [LUS0] (IRQs 5 7 9 10 *11 14 15)
[   15.911386] ACPI: PCI Interrupt Link [LUS2] (IRQs 5 *7 9 10 11 14 15)
[   15.911667] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 *10 11 14 15)
[   15.911947] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   15.912230] ACPI: PCI Interrupt Link [LACI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   15.912510] ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   15.912796] ACPI: PCI Interrupt Link [LPID] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   15.913086] ACPI: PCI Interrupt Link [LTID] (IRQs *5 7 9 10 11 14 15)
[   15.913369] ACPI: PCI Interrupt Link [LSI1] (IRQs 5 7 9 *10 11 14 15), disabled.
[   15.913479] Linux Plug and Play Support v0.97 (c) Adam Belay
[   15.913492] pnp: PnP ACPI init
[   15.915706] pnp: PnP ACPI: found 11 devices
[   15.915749] PCI: Using ACPI for IRQ routing
[   15.915753] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   15.915922] PCI-DMA: Disabling IOMMU.
[   15.916377] pnp: 00:03: ioport range 0x1000-0x107f could not be reserved
[   15.916380] pnp: 00:03: ioport range 0x1080-0x10ff has been reserved
[   15.916383] pnp: 00:03: ioport range 0x1400-0x147f has been reserved
[   15.916386] pnp: 00:03: ioport range 0x1480-0x14ff could not be reserved
[   15.916388] pnp: 00:03: ioport range 0x1800-0x187f has been reserved
[   15.916391] pnp: 00:03: ioport range 0x1880-0x18ff has been reserved
[   15.916394] pnp: 00:03: ioport range 0x2000-0x203f has been reserved
[   15.916567] PCI: Bridge: 0000:00:02.0
[   15.916570]   IO window: 4000-4fff
[   15.916573]   MEM window: c0200000-c03fffff
[   15.916576]   PREFETCH window: c3200000-c33fffff
[   15.916578] PCI: Bridge: 0000:00:03.0
[   15.916580]   IO window: 5000-5fff
[   15.916583]   MEM window: c0400000-c05fffff
[   15.916585]   PREFETCH window: c3400000-c35fffff
[   15.916590] PCI: Failed to allocate mem resource #6:20000@e0000000 for 0000:05:00.0
[   15.916592] PCI: Bridge: 0000:00:04.0
[   15.916594]   IO window: disabled.
[   15.916596]   MEM window: c1000000-c2ffffff
[   15.916599]   PREFETCH window: d0000000-dfffffff
[   15.916601] PCI: Bridge: 0000:00:10.0
[   15.916603]   IO window: disabled.
[   15.916606]   MEM window: c3000000-c30fffff
[   15.916608]   PREFETCH window: disabled.
[   15.916617] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   15.916621] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   15.916626] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   15.916632] PCI: Setting latency timer of device 0000:00:10.0 to 64
[   15.916687] NET: Registered protocol family 2
[   16.102456] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[   16.102643] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[   16.103971] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   16.104657] TCP: Hash tables configured (established 131072 bind 65536)
[   16.104660] TCP reno registered
[   16.104840] Simple Boot Flag at 0x36 set to 0x1
[   16.104978] IA32 emulation $Id: sys_ia32.c,v 1.32 2002/03/24 13:02:28 ak Exp $
[   16.105292] audit: initializing netlink socket (disabled)
[   16.105301] audit(1176142572.980:1): initialized
[   16.105423] VFS: Disk quotas dquot_6.5.1
[   16.105442] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   16.105483] Initializing Cryptographic API
[   16.105487] io scheduler noop registered
[   16.105493] io scheduler anticipatory registered
[   16.105500] io scheduler deadline registered
[   16.105515] io scheduler cfq registered (default)
[   16.105906] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   16.105910] pcie_portdrv_probe->Dev[02fc:10de] has invalid IRQ. Check vendor BIOS
[   16.105925] assign_interrupt_mode Found MSI capability
[   16.105956] Allocate Port Service[0000:00:02.0:pcie00]
[   16.105988] Allocate Port Service[0000:00:02.0:pcie03]
[   16.106019] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   16.106022] pcie_portdrv_probe->Dev[02fd:10de] has invalid IRQ. Check vendor BIOS
[   16.106036] assign_interrupt_mode Found MSI capability
[   16.106052] Allocate Port Service[0000:00:03.0:pcie00]
[   16.106078] Allocate Port Service[0000:00:03.0:pcie03]
[   16.106106] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   16.106109] pcie_portdrv_probe->Dev[02fb:10de] has invalid IRQ. Check vendor BIOS
[   16.106123] assign_interrupt_mode Found MSI capability
[   16.106139] Allocate Port Service[0000:00:04.0:pcie00]
[   16.106164] Allocate Port Service[0000:00:04.0:pcie03]
[   16.125201] Real Time Clock Driver v1.12ac
[   16.125237] Linux agpgart interface v0.101 (c) Dave Jones
[   16.125240] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   16.125691] mice: PS/2 mouse device common for all mice
[   16.126148] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   16.126319] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   16.126323] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   16.126589] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   16.153448] serio: i8042 AUX port at 0x60,0x64 irq 12
[   16.154970] serio: i8042 KBD port at 0x60,0x64 irq 1
[   16.155164] TCP bic registered
[   16.155172] NET: Registered protocol family 1
[   16.155177] NET: Registered protocol family 8
[   16.155180] NET: Registered protocol family 20
[   16.159096] ACPI: (supports S0 S3 S4 S5)
[   16.159138] drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   16.159156] Freeing unused kernel memory: 188k freed
[   16.253212] input: AT Translated Set 2 keyboard as /class/input/input0
[   16.285382] vga16fb: initializing
[   16.285387] vga16fb: mapped to 0xffff8100000a0000
[   16.485824] Console: switching to colour frame buffer device 80x25
[   16.485829] fb0: VGA16 VGA frame buffer device
[   17.566361] Capability LSM initialized
[   17.597097] ACPI Exception (acpi_processor-0693): AE_NOT_FOUND, Processor Device is not present [20060707]
[   17.597102] ACPI: Getting cpuindex for acpiid 0x1
[   17.598529] ACPI: Thermal Zone [THRM] (56 C)
[   17.925067] SCSI subsystem initialized
[   17.928419] libata version 1.20 loaded.
[   17.929415] sata_nv 0000:00:0e.0: version 0.8
[   17.929426] PCI: Enabling device 0000:00:0e.0 (0005 -> 0007)
[   17.929695] ACPI: PCI Interrupt Link [LTID] enabled at IRQ 5
[   17.929698] PCI: setting IRQ 5 as level-triggered
[   17.929701] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LTID] -> GSI 5 (level, low) -> IRQ 5
[   17.929785] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   17.929847] ata1: SATA max UDMA/133 cmd 0x30C0 ctl 0x30B6 bmdma 0x3090 irq 5
[   17.929866] ata2: SATA max UDMA/133 cmd 0x30B8 ctl 0x30B2 bmdma 0x3098 irq 5
[   18.135741] ata1: SATA link up 1.5 Gbps (SStatus 113)
[   18.303712] ata1: dev 0 cfg 49:2f00 82:706b 83:7c09 84:6023 85:7069 86:3c09 87:6023 88:203f
[   18.303716] ata1: dev 0 ATA-7, max UDMA/100, 156301488 sectors: LBA48
[   18.315700] ata1: dev 0 configured for UDMA/100
[   18.315702] scsi0 : sata_nv
[   18.523230] ata2: SATA link down (SStatus 0)
[   18.523235] scsi1 : sata_nv
[   18.523774]   Vendor: ATA       Model: TOSHIBA MK8034GS  Rev: AH30
[   18.523782]   Type:   Direct-Access                      ANSI SCSI revision: 05
[   18.524579] NFORCE-MCP51: IDE controller at PCI slot 0000:00:0d.0
[   18.524595] NFORCE-MCP51: chipset revision 241
[   18.524597] NFORCE-MCP51: not 100% native mode: will probe irqs later
[   18.524600] NFORCE-MCP51: BIOS didn't set cable bits correctly. Enabling workaround.
[   18.524605] NFORCE-MCP51: 0000:00:0d.0 (rev f1) UDMA133 controller
[   18.524612]     ide0: BM-DMA at 0x3080-0x3087, BIOS settings: hda:DMA, hdb:pio
[   18.524621] Probing IDE interface ide0...
[   18.539534] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[   18.539545] sda: Write Protect is off
[   18.539547] sda: Mode Sense: 00 3a 00 00
[   18.539559] SCSI device sda: drive cache: write back
[   18.539604] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[   18.539612] sda: Write Protect is off
[   18.539614] sda: Mode Sense: 00 3a 00 00
[   18.539625] SCSI device sda: drive cache: write back
[   18.539629]  sda: sda1 sda2 < sda5 sda6 sda7 > sda4
[   18.640440] sd 0:0:0:0: Attached scsi disk sda
[   19.262367] hda: HL-DT-STCD-RW/DVD DRIVE GCC-4244N, ATAPI CD/DVD-ROM drive
[   19.598597] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   19.608265] hda: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, DMA
[   19.608273] Uniform CD-ROM driver Revision: 3.20
[   19.725848] Probing IDE interface ide1...
[   19.769143] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.54.
[   19.769443] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 10
[   19.769445] PCI: setting IRQ 10 as level-triggered
[   19.769449] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [LMAC] -> GSI 10 (level, low) -> IRQ 10
[   19.769454] PCI: Setting latency timer of device 0000:00:14.0 to 64
[   19.769461] forcedeth: using HIGHDMA
[   19.801146] ieee1394: Initialized config rom entry `ip1394'
[   19.812192] usbcore: registered new driver usbfs
[   19.812621] usbcore: registered new driver hub
[   19.814263] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[   20.293220] eth0: forcedeth.c: subsystem: 0103c:30b7 bound to 0000:00:14.0
[   20.294139] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 11
[   20.294143] PCI: setting IRQ 11 as level-triggered
[   20.294146] ACPI: PCI Interrupt 0000:07:05.0[A] -> Link [LNK1] -> GSI 11 (level, low) -> IRQ 11
[   20.345698] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 11
[   20.345702] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LUS0] -> GSI 11 (level, low) -> IRQ 11
[   20.345785] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   20.345790] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[   20.346041] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[   20.548114] ohci_hcd 0000:00:0b.0: irq 11, io mem 0xc0004000
[   20.550178] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[c3000000-c30007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   20.606685] usb usb1: configuration #1 chosen from 1 choice
[   20.606775] hub 1-0:1.0: USB hub found
[   20.606787] hub 1-0:1.0: 8 ports detected
[   20.712768] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 7
[   20.712771] PCI: setting IRQ 7 as level-triggered
[   20.712774] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [LUS2] -> GSI 7 (level, low) -> IRQ 7
[   20.712858] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[   20.712863] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[   20.713042] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
[   20.713071] ehci_hcd 0000:00:0b.1: debug port 1
[   20.713075] PCI: cache line size of 64 is not supported by device 0000:00:0b.1
[   20.713083] ehci_hcd 0000:00:0b.1: irq 7, io mem 0xc0005000
[   20.713091] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   20.713205] usb usb2: configuration #1 chosen from 1 choice
[   20.713296] hub 2-0:1.0: USB hub found
[   20.713303] hub 2-0:1.0: 8 ports detected
[   20.892427] Attempting manual resume
[   20.928094] kjournald starting.  Commit interval 5 seconds
[   20.928105] EXT3-fs: mounted filesystem with ordered data mode.
[   21.671116] usb 1-3: new full speed USB device using ohci_hcd and address 2
[   21.831071] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[009fc0009484d800]
[   21.909876] usb 1-3: configuration #1 chosen from 1 choice
[   22.218392] usb 1-6: new low speed USB device using ohci_hcd and address 3
[   22.435186] usb 1-6: configuration #1 chosen from 1 choice
[   30.566247] input: PC Speaker as /class/input/input1
[   30.627614] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   30.659698] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   31.604252] sdhci: Secure Digital Host Controller Interface driver, 0.12
[   31.604256] sdhci: Copyright(c) Pierre Ossman
[   31.604288] sdhci: SDHCI controller found at 0000:07:05.1 [1180:0822] (rev 19)
[   31.604577] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 11
[   31.604580] ACPI: PCI Interrupt 0000:07:05.1[B] -> Link [LNK2] -> GSI 11 (level, low) -> IRQ 11
[   31.604739] mmc0: SDHCI at 0xc3000800 irq 11 DMA
[   31.687936] Bluetooth: Core ver 2.8
[   31.687940] NET: Registered protocol family 31
[   31.687942] Bluetooth: HCI device and connection manager initialized
[   31.687954] Bluetooth: HCI socket layer initialized
[   31.708118] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   31.714596] Bluetooth: HCI USB driver ver 2.9
[   31.715832] usbcore: registered new driver hci_usb
[   31.799414] usbcore: registered new driver hiddev
[   31.807698] input: USB Mouse as /class/input/input2
[   31.807752] input: USB HID v1.00 Mouse [USB Mouse] on usb-0000:00:0b.0-6
[   31.807763] usbcore: registered new driver usbhid
[   31.807766] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   31.869499] ts: Compaq touchscreen protocol output
[   31.956569] NET: Registered protocol family 10
[   31.956660] lo: Disabled Privacy Extensions
[   31.957007] IPv6 over IPv4 tunneling driver
[   32.014814] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000
[   32.078971] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   32.256042] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 10
[   32.256046] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LAZA] -> GSI 10 (level, low) -> IRQ 10
[   32.256137] PCI: Setting latency timer of device 0000:00:10.1 to 64
[   33.216074] lp: driver loaded but no devices found
[   33.256968] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[   33.256972] ieee1394: sbp2: Try serialize_io=0 for better performance
[   33.306898] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[   33.343894] ndiswrapper (wrapper_init:129): loadndiswrapper failed (1536); check system log for messages from 'loadndisdriver'
[   33.344873] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed
[   33.470218] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.60.2)
[   33.470257] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x10 (1150 mV)
[   33.470260] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x12 (1100 mV)
[   33.470263] powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x14 (1050 mV)
[   33.470265] powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x18 (950 mV)
[   33.470270] cpu_init done, current fid 0xc, vid 0x10
[   33.506990] Adding 2048276k swap on /dev/disk/by-uuid/21ac8080-04e2-4a06-97a3-cf860d3fc865.  Priority:-1 extents:1 across:2048276k
[   33.593069] EXT3 FS on sda5, internal journal
[   33.820793] kjournald starting.  Commit interval 5 seconds
[   33.831393] EXT3 FS on sda7, internal journal
[   33.831398] EXT3-fs: mounted filesystem with ordered data mode.
[   34.042106] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[   34.042938] ndiswrapper (wrapper_init:129): loadndiswrapper failed (1536); check system log for messages from 'loadndisdriver'
[   34.042985] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed
[   34.066829] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[   34.067658] ndiswrapper (wrapper_init:129): loadndiswrapper failed (1536); check system log for messages from 'loadndisdriver'
[   34.067704] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed
[   34.094508] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[   34.095317] ndiswrapper (wrapper_init:129): loadndiswrapper failed (1536); check system log for messages from 'loadndisdriver'
[   34.095365] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed
[   34.117912] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[   34.118713] ndiswrapper (wrapper_init:129): loadndiswrapper failed (1536); check system log for messages from 'loadndisdriver'
[   34.118760] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed
[   34.141931] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[   34.142764] ndiswrapper (wrapper_init:129): loadndiswrapper failed (1536); check system log for messages from 'loadndisdriver'
[   34.142811] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed
[   34.165874] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[   34.166705] ndiswrapper (wrapper_init:129): loadndiswrapper failed (1536); check system log for messages from 'loadndisdriver'
[   34.166751] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed
[   36.006323] ACPI: AC Adapter [ACAD] (on-line)
[   36.041066] ACPI: Battery Slot [BAT0] (battery present)
[   36.053278] ACPI: Power Button (FF) [PWRF]
[   36.053285] ACPI: Power Button (CM) [PWRB]
[   36.053292] ACPI: Sleep Button (CM) [SLPB]
[   36.053297] ACPI: Lid Switch [LID]
[   36.149623] ibm_acpi: ec object not found
[   36.173609] pcc_acpi: loading...
[   36.220105] wmi_add device=ffff810037aaf800
[   36.220109] calling WQBA
[   36.261681] ACPI: Video Device [UVGA] (multi-head: yes  rom: no  post: no)
[   36.261795] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   41.657822] eth0: no IPv6 routers present
[   45.849339] Bluetooth: L2CAP ver 2.8
[   45.849342] Bluetooth: L2CAP socket layer initialized
[   45.876056] Bluetooth: RFCOMM socket layer initialized
[   45.876070] Bluetooth: RFCOMM TTY layer initialized
[   45.876072] Bluetooth: RFCOMM ver 1.7
[   56.962431] ISO 9660 Extensions: Microsoft Joliet Level 3
[   57.215774] ISOFS: changing to secondary root

```

---

### Post by Eigenwert on 2007-04-09
dmesg in Feisty give me:

```
[    0.000000] Linux version 2.6.20-12-generic (root@yellow) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Wed Mar 21 19:34:23 UTC 2007 (Ubuntu 2.6.20-12.20-generic)
[    0.000000] Command line: root=UUID=76e4b7bb-3cf2-4fd6-9798-936aa85b970a ro quiet splash noapic nolapic 
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ff00000 (usable)
[    0.000000]  BIOS-e820: 000000003ff00000 - 000000003ff17000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ff17000 - 000000003ff80000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003ff80000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 157) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 261888) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v000 HP                                    ) @ 0x00000000000f8970
[    0.000000] ACPI: RSDT (v001 HP       RSDT   0x06040000  LTP 0x00000000) @ 0x000000003ff0fc14
[    0.000000] ACPI: FADT (v001 HP     MCP51M   0x06040000 PTL_ 0x000f4240) @ 0x000000003ff16dcd
[    0.000000] ACPI: SSDT (v001 HP     POWERNOW 0x06040000  LTP 0x00000001) @ 0x000000003ff16e41
[    0.000000] ACPI: MCFG (v001 HP       MCFG   0x06040000  LTP 0x00000000) @ 0x000000003ff16f56
[    0.000000] ACPI: MADT (v001 HP       APIC   0x06040000  LTP 0x00000000) @ 0x000000003ff16f92
[    0.000000] ACPI: BOOT (v001     HP $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x000000003ff16fd8
[    0.000000] ACPI: DSDT (v001 HP       MCP51M 0x06040000 MSFT 0x0100000e) @ 0x0000000000000000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] Number of nodes 1
[    0.000000] Node 0 MemBase 0000000000000000 Limit 000000003ff00000
[    0.000000] Entering add_active_range(0, 0, 157) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 261888) 1 entries of 3200 used
[    0.000000] NUMA: Using 63 for the hash shift.
[    0.000000] Using node hash shift of 63
[    0.000000] Bootmem setup node 0 0000000000000000-000000003ff00000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      157
[    0.000000]     0:      256 ->   261888
[    0.000000] On node 0 totalpages: 261789
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1082 pages reserved
[    0.000000]   DMA zone: 2859 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 3524 pages used for memmap
[    0.000000]   DMA32 zone: 254268 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] Intel MultiProcessor Specification v1.4
[    0.000000] MPTABLE: OEM ID: nVIDIA   MPTABLE: Product ID: C51-MCP51    MPTABLE: APIC at: 0xFEE00000
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] I/O APIC #1 at 0xFEC00000.
[    0.000000] Setting APIC routing to physical flat
[    0.000000] Processors: 1
[    0.000000] Nosave address range: 000000000009d000 - 000000000009e000
[    0.000000] Nosave address range: 000000000009e000 - 00000000000a0000
[    0.000000] Nosave address range: 00000000000a0000 - 00000000000d2000
[    0.000000] Nosave address range: 00000000000d2000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34048 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 257127
[    0.000000] Kernel command line: root=UUID=76e4b7bb-3cf2-4fd6-9798-936aa85b970a ro quiet splash noapic nolapic 
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[   14.016823] Console: colour VGA+ 80x25
[   14.017342] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   14.018251] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[   14.018353] Checking aperture...
[   14.018357] CPU 0: aperture @ c40000000 size 32 MB
[   14.018358] Aperture too small (32 MB)
[   14.025131] No AGP bridge found
[   14.035717] Memory: 1020032k/1047552k available (2213k kernel code, 27124k reserved, 1158k data, 304k init)
[   14.112472] Calibrating delay using timer specific routine.. 4021.99 BogoMIPS (lpj=8043996)
[   14.112524] Security Framework v1.0.0 initialized
[   14.112528] SELinux:  Disabled at boot.
[   14.112550] Mount-cache hash table entries: 256
[   14.112677] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   14.112680] CPU: L2 Cache: 512K (64 bytes/line)
[   14.112683] CPU 0/0 -> Node 0
[   14.112700] SMP alternatives: switching to UP code
[   14.112811] Freeing SMP alternatives: 24k freed
[   14.112913] Early unpacking initramfs... done
[   14.419826] ACPI: Core revision 20060707
[   14.422683] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   14.424858] ACPI: setting ELCR to 0200 (from 0ca0)
[   14.477850] Using local APIC timer interrupts.
[   14.527560] result 12557506
[   14.527561] Detected 12.557 MHz APIC timer.
[   14.527994] Brought up 1 CPUs
[   14.528004] time.c: Using 3.579545 MHz WALL PM GTOD PIT/TSC timer.
[   14.528006] time.c: Detected 2009.201 MHz processor.
[   14.528296] Time: 19:21:35  Date: 03/09/107
[   14.528328] NET: Registered protocol family 16
[   14.528397] ACPI: bus type pci registered
[   14.528402] PCI: Using configuration type 1
[   14.533212] ACPI: Interpreter enabled
[   14.533214] ACPI: Using PIC for interrupt routing
[   14.534042] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   14.534047] PCI: Probing PCI hardware (bus 00)
[   14.534205] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[   14.535136] Boot video device is 0000:05:00.0
[   14.535414] PCI: Transparent bridge - 0000:00:10.0
[   14.535448] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   14.567043] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[   14.567944] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR0._PRT]
[   14.568209] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[   14.568369] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
[   14.568678] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   14.568950] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 *11 14 15)
[   14.569221] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 *11 14 15)
[   14.569491] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   14.569761] ACPI: PCI Interrupt Link [LK1E] (IRQs 5 7 9 10 *11 14 15)
[   14.570034] ACPI: PCI Interrupt Link [LK2E] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   14.570304] ACPI: PCI Interrupt Link [LK3E] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   14.570573] ACPI: PCI Interrupt Link [LK4E] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   14.570846] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 *10 11 14 15)
[   14.571115] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 *10 11 14 15)
[   14.571385] ACPI: PCI Interrupt Link [LUS0] (IRQs 5 7 9 10 *11 14 15)
[   14.571654] ACPI: PCI Interrupt Link [LUS2] (IRQs 5 *7 9 10 11 14 15)
[   14.571938] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 *10 11 14 15)
[   14.572208] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   14.572480] ACPI: PCI Interrupt Link [LACI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   14.572750] ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   14.573020] ACPI: PCI Interrupt Link [LPID] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   14.573298] ACPI: PCI Interrupt Link [LTID] (IRQs *5 7 9 10 11 14 15)
[   14.573570] ACPI: PCI Interrupt Link [LSI1] (IRQs 5 7 9 *10 11 14 15), disabled.
[   14.573681] Linux Plug and Play Support v0.97 (c) Adam Belay
[   14.573691] pnp: PnP ACPI init
[   14.575842] pnp: PnP ACPI: found 11 devices
[   14.575924] PCI: Using ACPI for IRQ routing
[   14.575928] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   14.576014] NET: Registered protocol family 8
[   14.576015] NET: Registered protocol family 20
[   14.576509] pnp: 00:03: ioport range 0x1000-0x107f could not be reserved
[   14.576512] pnp: 00:03: ioport range 0x1080-0x10ff has been reserved
[   14.576516] pnp: 00:03: ioport range 0x1400-0x147f has been reserved
[   14.576521] pnp: 00:03: ioport range 0x1480-0x14ff could not be reserved
[   14.576524] pnp: 00:03: ioport range 0x1800-0x187f has been reserved
[   14.576527] pnp: 00:03: ioport range 0x1880-0x18ff has been reserved
[   14.576531] pnp: 00:03: ioport range 0x2000-0x203f has been reserved
[   14.576793] PCI: Bridge: 0000:00:02.0
[   14.576796]   IO window: 4000-4fff
[   14.576799]   MEM window: c0200000-c03fffff
[   14.576802]   PREFETCH window: c3200000-c33fffff
[   14.576805] PCI: Bridge: 0000:00:03.0
[   14.576807]   IO window: 5000-5fff
[   14.576810]   MEM window: c0400000-c05fffff
[   14.576813]   PREFETCH window: c3400000-c35fffff
[   14.576819] PCI: Failed to allocate mem resource #6:20000@e0000000 for 0000:05:00.0
[   14.576871] PCI: Bridge: 0000:00:04.0
[   14.576873]   IO window: disabled.
[   14.576876]   MEM window: c1000000-c2ffffff
[   14.576879]   PREFETCH window: d0000000-dfffffff
[   14.576882] PCI: Bridge: 0000:00:10.0
[   14.576884]   IO window: disabled.
[   14.576887]   MEM window: c3000000-c30fffff
[   14.576890]   PREFETCH window: disabled.
[   14.576900] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   14.576906] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   14.576912] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   14.576920] PCI: Setting latency timer of device 0000:00:10.0 to 64
[   14.576991] NET: Registered protocol family 2
[   14.615906] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[   14.616090] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[   14.617331] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   14.617971] TCP: Hash tables configured (established 131072 bind 65536)
[   14.617975] TCP reno registered
[   14.627943] checking if image is initramfs... it is
[   15.373606] Freeing initrd memory: 6813k freed
[   15.377567] Simple Boot Flag at 0x36 set to 0x1
[   15.377900] audit: initializing netlink socket (disabled)
[   15.377911] audit(1176146496.124:1): initialized
[   15.378034] VFS: Disk quotas dquot_6.5.1
[   15.378049] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   15.378094] io scheduler noop registered
[   15.378096] io scheduler anticipatory registered
[   15.378098] io scheduler deadline registered
[   15.378110] io scheduler cfq registered (default)
[   15.580339] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   15.580358] assign_interrupt_mode Found MSI capability
[   15.580362] Allocate Port Service[0000:00:02.0:pcie00]
[   15.580422] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   15.580441] assign_interrupt_mode Found MSI capability
[   15.580444] Allocate Port Service[0000:00:03.0:pcie00]
[   15.580497] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   15.580515] assign_interrupt_mode Found MSI capability
[   15.580518] Allocate Port Service[0000:00:04.0:pcie00]
[   15.602114] Real Time Clock Driver v1.12ac
[   15.602154] Linux agpgart interface v0.101 (c) Dave Jones
[   15.602156] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   15.602689] mice: PS/2 mouse device common for all mice
[   15.603170] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   15.603350] input: Macintosh mouse button emulation as /class/input/input0
[   15.603383] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   15.603387] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   15.603620] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   15.620406] serio: i8042 KBD port at 0x60,0x64 irq 1
[   15.620412] serio: i8042 AUX port at 0x60,0x64 irq 12
[   15.620489] TCP cubic registered
[   15.620497] NET: Registered protocol family 1
[   15.621398] ACPI: (supports S0 S3 S4 S5)
[   15.621442]   Magic number: 3:501:394
[   15.621556] drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   15.621610] Freeing unused kernel memory: 304k freed
[   15.633266] input: AT Translated Set 2 keyboard as /class/input/input1
[   16.811187] Capability LSM initialized
[   16.844597] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   16.846082] ACPI: Thermal Zone [THRM] (57 C)
[   17.428290] usbcore: registered new interface driver usbfs
[   17.428323] usbcore: registered new interface driver hub
[   17.428345] usbcore: registered new device driver usb
[   17.429031] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   17.429323] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 11
[   17.429326] PCI: setting IRQ 11 as level-triggered
[   17.429330] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LUS0] -> GSI 11 (level, low) -> IRQ 11
[   17.429342] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   17.429346] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[   17.429463] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[   17.429480] ohci_hcd 0000:00:0b.0: irq 11, io mem 0xc0004000
[   17.466666] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.59.
[   17.476811] ieee1394: Initialized config rom entry `ip1394'
[   17.502462] usb usb1: configuration #1 chosen from 1 choice
[   17.502486] hub 1-0:1.0: USB hub found
[   17.502498] hub 1-0:1.0: 8 ports detected
[   17.608741] NFORCE-MCP51: IDE controller at PCI slot 0000:00:0d.0
[   17.608758] NFORCE-MCP51: chipset revision 241
[   17.608760] NFORCE-MCP51: not 100% native mode: will probe irqs later
[   17.608764] NFORCE-MCP51: BIOS didn't set cable bits correctly. Enabling workaround.
[   17.608769] NFORCE-MCP51: 0000:00:0d.0 (rev f1) UDMA133 controller
[   17.608776]     ide0: BM-DMA at 0x3080-0x3087, BIOS settings: hda:DMA, hdb:pio
[   17.608785] Probing IDE interface ide0...
[   17.623463] SCSI subsystem initialized
[   17.628475] libata version 2.20 loaded.
[   17.915604] usb 1-3: new full speed USB device using ohci_hcd and address 2
[   18.144558] usb 1-3: configuration #1 chosen from 1 choice
[   18.347154] hda: HL-DT-STCD-RW/DVD DRIVE GCC-4244N, ATAPI CD/DVD-ROM drive
[   18.454909] usb 1-6: new low speed USB device using ohci_hcd and address 3
[   18.655890] usb 1-6: configuration #1 chosen from 1 choice
[   18.668239] usbcore: registered new interface driver hiddev
[   18.674006] input: USB Mouse as /class/input/input2
[   18.674122] input: USB HID v1.00 Mouse [USB Mouse] on usb-0000:00:0b.0-6
[   18.674134] usbcore: registered new interface driver usbhid
[   18.674137] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   18.687256] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   18.689088] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 10
[   18.689091] PCI: setting IRQ 10 as level-triggered
[   18.689095] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [LMAC] -> GSI 10 (level, low) -> IRQ 10
[   18.689102] PCI: Setting latency timer of device 0000:00:14.0 to 64
[   18.689109] forcedeth: using HIGHDMA
[   19.210332] eth0: forcedeth.c: subsystem: 0103c:30b7 bound to 0000:00:14.0
[   19.210710] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 11
[   19.210713] ACPI: PCI Interrupt 0000:07:05.0[A] -> Link [LNK1] -> GSI 11 (level, low) -> IRQ 11
[   19.263087] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[c3000000-c30007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   19.267494] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 7
[   19.267498] PCI: setting IRQ 7 as level-triggered
[   19.267502] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [LUS2] -> GSI 7 (level, low) -> IRQ 7
[   19.267512] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[   19.267516] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[   19.267693] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
[   19.267725] ehci_hcd 0000:00:0b.1: debug port 1
[   19.267729] PCI: cache line size of 64 is not supported by device 0000:00:0b.1
[   19.267737] ehci_hcd 0000:00:0b.1: irq 7, io mem 0xc0005000
[   19.267746] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   19.267797] usb 1-3: USB disconnect, address 2
[   19.269948] usb usb2: configuration #1 chosen from 1 choice
[   19.269983] hub 2-0:1.0: USB hub found
[   19.269993] hub 2-0:1.0: 8 ports detected
[   19.380147] sata_nv 0000:00:0e.0: version 3.3
[   19.380160] PCI: Enabling device 0000:00:0e.0 (0005 -> 0007)
[   19.380418] ACPI: PCI Interrupt Link [LTID] enabled at IRQ 5
[   19.380421] PCI: setting IRQ 5 as level-triggered
[   19.380426] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LTID] -> GSI 5 (level, low) -> IRQ 5
[   19.380446] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   19.380490] ata1: SATA max UDMA/133 cmd 0x00000000000130c0 ctl 0x00000000000130b6 bmdma 0x0000000000013090 irq 5
[   19.380516] ata2: SATA max UDMA/133 cmd 0x00000000000130b8 ctl 0x00000000000130b2 bmdma 0x0000000000013098 irq 5
[   19.380527] scsi0 : sata_nv
[   19.397728] usb 1-6: USB disconnect, address 3
[   19.849133] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   19.868971] ata1.00: ATA-7: TOSHIBA MK8034GSX, AH301H, max UDMA/100
[   19.868974] ata1.00: 156301488 sectors, multi 16: LBA48 
[   19.884890] ata1.00: configured for UDMA/100
[   19.884900] scsi1 : sata_nv
[   20.196667] ata2: SATA link down (SStatus 0 SControl 300)
[   20.207260] ATA: abnormal status 0x7F on port 0x00000000000130bf
[   20.207283] usb 1-3: new full speed USB device using ohci_hcd and address 4
[   20.207382] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK8034GS AH30 PQ: 0 ANSI: 5
[   20.219551] hda: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, DMA
[   20.219557] Uniform CD-ROM driver Revision: 3.20
[   20.219613] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[   20.219624] sda: Write Protect is off
[   20.219626] sda: Mode Sense: 00 3a 00 00
[   20.219640] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   20.219683] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[   20.219692] sda: Write Protect is off
[   20.219694] sda: Mode Sense: 00 3a 00 00
[   20.219707] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   20.219710]  sda: sda1 sda2 < sda5 sda6 sda7 > sda4
[   20.317609] sd 0:0:0:0: Attached scsi disk sda
[   20.320685] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   20.430551] usb 1-3: configuration #1 chosen from 1 choice
[   20.544391] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[009fc0009484d800]
[   20.648072] kjournald starting.  Commit interval 5 seconds
[   20.648083] EXT3-fs: mounted filesystem with ordered data mode.
[   20.739968] usb 1-6: new low speed USB device using ohci_hcd and address 5
[   20.940884] usb 1-6: configuration #1 chosen from 1 choice
[   20.950864] input: USB Mouse as /class/input/input3
[   20.950881] input: USB HID v1.00 Mouse [USB Mouse] on usb-0000:00:0b.0-6
[   31.232293] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   31.247389] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   31.413476] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x3040
[   31.413506] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x3000
[   31.869635] sdhci: Secure Digital Host Controller Interface driver, 0.12
[   31.869638] sdhci: Copyright(c) Pierre Ossman
[   31.869679] sdhci: SDHCI controller found at 0000:07:05.1 [1180:0822] (rev 19)
[   31.869972] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 11
[   31.869975] ACPI: PCI Interrupt 0000:07:05.1[B] -> Link [LNK2] -> GSI 11 (level, low) -> IRQ 11
[   31.869999] sdhci:slot0: Controller reports > 25 MHz base clock, but no high speed support.
[   31.870045] mmc0: SDHCI at 0xc3000800 irq 11 DMA
[   32.065926] input: PC Speaker as /class/input/input4
[   32.189110] Bluetooth: Core ver 2.11
[   32.189169] NET: Registered protocol family 31
[   32.189171] Bluetooth: HCI device and connection manager initialized
[   32.189174] Bluetooth: HCI socket layer initialized
[   32.213975] Bluetooth: HCI USB driver ver 2.9
[   32.258927] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 10
[   32.258931] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LAZA] -> GSI 10 (level, low) -> IRQ 10
[   32.258949] PCI: Setting latency timer of device 0000:00:10.1 to 64
[   32.272914] usbcore: registered new interface driver hci_usb
[   33.030571] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000
[   33.096122] input: SynPS/2 Synaptics TouchPad as /class/input/input5
[   33.228367] fuse init (API version 7.8)
[   33.313829] lp: driver loaded but no devices found
[   33.597775] EXT3 FS on sda6, internal journal
[   33.868439] kjournald starting.  Commit interval 5 seconds
[   33.868791] EXT3 FS on sda7, internal journal
[   33.868796] EXT3-fs: mounted filesystem with ordered data mode.
[   35.068062] NET: Registered protocol family 17
[   37.078057] NET: Registered protocol family 10
[   37.078138] lo: Disabled Privacy Extensions
[   43.040549] No dock devices found.
[   43.071980] ACPI: AC Adapter [ACAD] (on-line)
[   43.086823] ACPI: Video Device [UVGA] (multi-head: yes  rom: no  post: no)
[   43.086946] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   43.175774] ACPI: Battery Slot [BAT0] (battery present)
[   43.190126] Using specific hotkey driver
[   43.245243] input: Power Button (FF) as /class/input/input6
[   43.248985] ACPI: Power Button (FF) [PWRF]
[   43.272604] input: Power Button (CM) as /class/input/input7
[   43.276455] ACPI: Power Button (CM) [PWRB]
[   43.299844] input: Sleep Button (CM) as /class/input/input8
[   43.303545] ACPI: Sleep Button (CM) [SLPB]
[   43.327121] input: Lid Switch as /class/input/input9
[   43.330838] ACPI: Lid Switch [LID]
[   43.361245] ibm_acpi: ec object not found
[   43.385717] pcc_acpi: loading...
[   43.395834] wmi_add device=ffff81003df6c800
[   43.395837] calling WQBA
[   43.616247] powernow-k8: Found 1 AMD Turion(tm) 64 Mobile Technology MK-36 processors (version 2.00.00)
[   43.616285] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x10
[   43.616287] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x12
[   43.616290] powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x14
[   43.616292] powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x18
[   47.161711] eth0: no IPv6 routers present
[   50.229388] ppdev: user-space parallel port driver
[   51.266759] Bluetooth: L2CAP ver 2.8
[   51.266762] Bluetooth: L2CAP socket layer initialized
[   51.291413] Bluetooth: RFCOMM socket layer initialized
[   51.291425] Bluetooth: RFCOMM TTY layer initialized
[   51.291427] Bluetooth: RFCOMM ver 1.8
[   57.411114] eth0: no IPv6 routers present
[   62.754355] ISO 9660 Extensions: Microsoft Joliet Level 3
[   62.935175] ISOFS: changing to secondary root
[  172.558192] ISO 9660 Extensions: Microsoft Joliet Level 3
[  172.660729] ISOFS: changing to secondary root

```

However, I booted into Feisty and installed the some 280-odd updates, rebooted, and did a quick "lspci" The wireless card showed up! So I quickly did a reboot into Edgy, and no wireless card. I booted back to Feisty, and no more wireless card. WTF is going on!?!?!? This dmesg output is from that last boot into Feisty.

EW

---

### Post by bdogg64 on 2007-04-09
> **Eigenwert said:**
> 

However, I booted into Feisty and installed the some 280-odd updates, rebooted, and did a quick "lspci" The wireless card showed up! So I quickly did a reboot into Edgy, and no wireless card. I booted back to Feisty, and no more wireless card. WTF is going on!?!?!? This dmesg output is from that last boot into Feisty.

EW

Try booting into the latest feisty kernel if you have it (2.6.20-14) and see if your wireless card shows up. Your ndiswrapper is also outdated, so you might want to update that too.

---

### Post by Eigenwert on 2007-04-09
I booted 2.6.20-14 and recompiled my ndiswrapper (version 1.41) and reinstalled that. Still nothing. Here's the dmesg:

```
[    0.000000] Linux version 2.6.20-14-generic (root@yellow) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Mon Apr 2 16:32:46 UTC 2007 (Ubuntu 2.6.20-14.22-generic)
[    0.000000] Command line: root=UUID=76e4b7bb-3cf2-4fd6-9798-936aa85b970a ro quiet splash noapic nolapic 
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ff00000 (usable)
[    0.000000]  BIOS-e820: 000000003ff00000 - 000000003ff17000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ff17000 - 000000003ff80000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003ff80000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 157) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 261888) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v000 HP                                    ) @ 0x00000000000f8970
[    0.000000] ACPI: RSDT (v001 HP       RSDT   0x06040000  LTP 0x00000000) @ 0x000000003ff0fc14
[    0.000000] ACPI: FADT (v001 HP     MCP51M   0x06040000 PTL_ 0x000f4240) @ 0x000000003ff16dcd
[    0.000000] ACPI: SSDT (v001 HP     POWERNOW 0x06040000  LTP 0x00000001) @ 0x000000003ff16e41
[    0.000000] ACPI: MCFG (v001 HP       MCFG   0x06040000  LTP 0x00000000) @ 0x000000003ff16f56
[    0.000000] ACPI: MADT (v001 HP       APIC   0x06040000  LTP 0x00000000) @ 0x000000003ff16f92
[    0.000000] ACPI: BOOT (v001     HP $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x000000003ff16fd8
[    0.000000] ACPI: DSDT (v001 HP       MCP51M 0x06040000 MSFT 0x0100000e) @ 0x0000000000000000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] Number of nodes 1
[    0.000000] Node 0 MemBase 0000000000000000 Limit 000000003ff00000
[    0.000000] Entering add_active_range(0, 0, 157) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 261888) 1 entries of 3200 used
[    0.000000] NUMA: Using 63 for the hash shift.
[    0.000000] Using node hash shift of 63
[    0.000000] Bootmem setup node 0 0000000000000000-000000003ff00000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      157
[    0.000000]     0:      256 ->   261888
[    0.000000] On node 0 totalpages: 261789
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1086 pages reserved
[    0.000000]   DMA zone: 2855 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 3524 pages used for memmap
[    0.000000]   DMA32 zone: 254268 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] Intel MultiProcessor Specification v1.4
[    0.000000] MPTABLE: OEM ID: nVIDIA   MPTABLE: Product ID: C51-MCP51    MPTABLE: APIC at: 0xFEE00000
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] I/O APIC #1 at 0xFEC00000.
[    0.000000] Setting APIC routing to physical flat
[    0.000000] Processors: 1
[    0.000000] Nosave address range: 000000000009d000 - 000000000009e000
[    0.000000] Nosave address range: 000000000009e000 - 00000000000a0000
[    0.000000] Nosave address range: 00000000000a0000 - 00000000000d2000
[    0.000000] Nosave address range: 00000000000d2000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34048 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 257123
[    0.000000] Kernel command line: root=UUID=76e4b7bb-3cf2-4fd6-9798-936aa85b970a ro quiet splash noapic nolapic 
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[   14.294272] Console: colour VGA+ 80x25
[   14.294796] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   14.295706] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[   14.295809] Checking aperture...
[   14.295812] CPU 0: aperture @ c40000000 size 32 MB
[   14.295814] Aperture too small (32 MB)
[   14.302762] No AGP bridge found
[   14.313357] Memory: 1020008k/1047552k available (2217k kernel code, 27148k reserved, 1162k data, 304k init)
[   14.389922] Calibrating delay using timer specific routine.. 4022.07 BogoMIPS (lpj=8044146)
[   14.389974] Security Framework v1.0.0 initialized
[   14.389978] SELinux:  Disabled at boot.
[   14.390001] Mount-cache hash table entries: 256
[   14.390128] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   14.390131] CPU: L2 Cache: 512K (64 bytes/line)
[   14.390133] CPU 0/0 -> Node 0
[   14.390151] SMP alternatives: switching to UP code
[   14.390262] Freeing SMP alternatives: 24k freed
[   14.390362] Early unpacking initramfs... done
[   14.698007] ACPI: Core revision 20060707
[   14.700894] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   14.703269] ACPI: setting ELCR to 0200 (from 0ca0)
[   14.756252] Using local APIC timer interrupts.
[   14.805961] result 12557367
[   14.805963] Detected 12.557 MHz APIC timer.
[   14.809435] Brought up 1 CPUs
[   14.809445] time.c: Using 3.579545 MHz WALL PM GTOD PIT/TSC timer.
[   14.809447] time.c: Detected 2009.179 MHz processor.
[   14.809755] Time: 22:53:58  Date: 03/09/107
[   14.809787] NET: Registered protocol family 16
[   14.809857] ACPI: bus type pci registered
[   14.809862] PCI: Using configuration type 1
[   14.814824] ACPI: Interpreter enabled
[   14.814827] ACPI: Using PIC for interrupt routing
[   14.815661] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   14.815665] PCI: Probing PCI hardware (bus 00)
[   14.815828] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[   14.816785] Boot video device is 0000:05:00.0
[   14.817061] PCI: Transparent bridge - 0000:00:10.0
[   14.817095] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   14.849248] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[   14.850114] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR0._PRT]
[   14.850385] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[   14.850547] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
[   14.850869] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   14.851149] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 *11 14 15)
[   14.851426] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 *11 14 15)
[   14.851705] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   14.851983] ACPI: PCI Interrupt Link [LK1E] (IRQs 5 7 9 10 *11 14 15)
[   14.852258] ACPI: PCI Interrupt Link [LK2E] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   14.852533] ACPI: PCI Interrupt Link [LK3E] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   14.852810] ACPI: PCI Interrupt Link [LK4E] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   14.853086] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 *10 11 14 15)
[   14.853384] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 *10 11 14 15)
[   14.853665] ACPI: PCI Interrupt Link [LUS0] (IRQs 5 7 9 10 *11 14 15)
[   14.853940] ACPI: PCI Interrupt Link [LUS2] (IRQs 5 *7 9 10 11 14 15)
[   14.854217] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 *10 11 14 15)
[   14.854492] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   14.854768] ACPI: PCI Interrupt Link [LACI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   14.855046] ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   14.855322] ACPI: PCI Interrupt Link [LPID] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   14.855611] ACPI: PCI Interrupt Link [LTID] (IRQs *5 7 9 10 11 14 15)
[   14.855889] ACPI: PCI Interrupt Link [LSI1] (IRQs 5 7 9 *10 11 14 15), disabled.
[   14.855996] Linux Plug and Play Support v0.97 (c) Adam Belay
[   14.856006] pnp: PnP ACPI init
[   14.858224] pnp: PnP ACPI: found 11 devices
[   14.858272] PCI: Using ACPI for IRQ routing
[   14.858275] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   14.858367] NET: Registered protocol family 8
[   14.858369] NET: Registered protocol family 20
[   14.858887] pnp: 00:03: ioport range 0x1000-0x107f could not be reserved
[   14.858891] pnp: 00:03: ioport range 0x1080-0x10ff has been reserved
[   14.858893] pnp: 00:03: ioport range 0x1400-0x147f has been reserved
[   14.858898] pnp: 00:03: ioport range 0x1480-0x14ff could not be reserved
[   14.858901] pnp: 00:03: ioport range 0x1800-0x187f has been reserved
[   14.858904] pnp: 00:03: ioport range 0x1880-0x18ff has been reserved
[   14.858906] pnp: 00:03: ioport range 0x2000-0x203f has been reserved
[   14.859173] PCI: Bridge: 0000:00:02.0
[   14.859175]   IO window: 4000-4fff
[   14.859179]   MEM window: c0200000-c03fffff
[   14.859181]   PREFETCH window: c3200000-c33fffff
[   14.859184] PCI: Bridge: 0000:00:03.0
[   14.859186]   IO window: 5000-5fff
[   14.859189]   MEM window: c0400000-c05fffff
[   14.859191]   PREFETCH window: c3400000-c35fffff
[   14.859196] PCI: Failed to allocate mem resource #6:20000@e0000000 for 0000:05:00.0
[   14.859248] PCI: Bridge: 0000:00:04.0
[   14.859250]   IO window: disabled.
[   14.859253]   MEM window: c1000000-c2ffffff
[   14.859255]   PREFETCH window: d0000000-dfffffff
[   14.859258] PCI: Bridge: 0000:00:10.0
[   14.859259]   IO window: disabled.
[   14.859263]   MEM window: c3000000-c30fffff
[   14.859265]   PREFETCH window: disabled.
[   14.859275] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   14.859280] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   14.859286] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   14.859293] PCI: Setting latency timer of device 0000:00:10.0 to 64
[   14.859365] NET: Registered protocol family 2
[   14.885362] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[   14.885554] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[   14.886798] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   14.887435] TCP: Hash tables configured (established 131072 bind 65536)
[   14.887438] TCP reno registered
[   14.897399] checking if image is initramfs... it is
[   15.642549] Freeing initrd memory: 6821k freed
[   15.646524] Simple Boot Flag at 0x36 set to 0x1
[   15.646852] audit: initializing netlink socket (disabled)
[   15.646864] audit(1176159238.112:1): initialized
[   15.646986] VFS: Disk quotas dquot_6.5.1
[   15.647002] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   15.647047] io scheduler noop registered
[   15.647049] io scheduler anticipatory registered
[   15.647051] io scheduler deadline registered
[   15.647063] io scheduler cfq registered (default)
[   15.849296] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   15.849316] assign_interrupt_mode Found MSI capability
[   15.849319] Allocate Port Service[0000:00:02.0:pcie00]
[   15.849376] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   15.849395] assign_interrupt_mode Found MSI capability
[   15.849397] Allocate Port Service[0000:00:03.0:pcie00]
[   15.849450] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   15.849469] assign_interrupt_mode Found MSI capability
[   15.849472] Allocate Port Service[0000:00:04.0:pcie00]
[   15.870960] Real Time Clock Driver v1.12ac
[   15.871002] Linux agpgart interface v0.102 (c) Dave Jones
[   15.871004] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   15.871496] mice: PS/2 mouse device common for all mice
[   15.871960] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   15.872166] input: Macintosh mouse button emulation as /class/input/input0
[   15.872195] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   15.872199] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   15.872433] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   15.889013] serio: i8042 KBD port at 0x60,0x64 irq 1
[   15.889018] serio: i8042 AUX port at 0x60,0x64 irq 12
[   15.889096] TCP cubic registered
[   15.889103] NET: Registered protocol family 1
[   15.890056] ACPI: (supports S0 S3 S4 S5)
[   15.890102]   Magic number: 3:337:906
[   15.890166]   hash matches device ptyz2
[   15.890217] drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   15.890272] Freeing unused kernel memory: 304k freed
[   15.901907] input: AT Translated Set 2 keyboard as /class/input/input1
[   17.088758] Capability LSM initialized
[   17.122619] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   17.124053] ACPI: Thermal Zone [THRM] (56 C)
[   17.652172] usbcore: registered new interface driver usbfs
[   17.652197] usbcore: registered new interface driver hub
[   17.652216] usbcore: registered new device driver usb
[   17.653341] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 7
[   17.653344] PCI: setting IRQ 7 as level-triggered
[   17.653349] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [LUS2] -> GSI 7 (level, low) -> IRQ 7
[   17.653360] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[   17.653363] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[   17.653485] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
[   17.653516] ehci_hcd 0000:00:0b.1: debug port 1
[   17.653520] PCI: cache line size of 64 is not supported by device 0000:00:0b.1
[   17.653528] ehci_hcd 0000:00:0b.1: irq 7, io mem 0xc0005000
[   17.653537] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   17.653617] usb usb1: configuration #1 chosen from 1 choice
[   17.653644] hub 1-0:1.0: USB hub found
[   17.653650] hub 1-0:1.0: 8 ports detected
[   17.685739] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.59.
[   17.713334] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   17.769869] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 10
[   17.769873] PCI: setting IRQ 10 as level-triggered
[   17.769877] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [LMAC] -> GSI 10 (level, low) -> IRQ 10
[   17.769884] PCI: Setting latency timer of device 0000:00:14.0 to 64
[   17.769891] forcedeth: using HIGHDMA
[   17.775827] SCSI subsystem initialized
[   17.781025] libata version 2.20 loaded.
[   17.797880] ieee1394: Initialized config rom entry `ip1394'
[   18.293262] eth0: forcedeth.c: subsystem: 0103c:30b7 bound to 0000:00:14.0
[   18.293820] pata_amd 0000:00:0d.0: version 0.2.8
[   18.293847] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   18.293899] ata1: PATA max UDMA/133 cmd 0x00000000000101f0 ctl 0x00000000000103f6 bmdma 0x0000000000013080 irq 14
[   18.294237] ata2: PATA max UDMA/133 cmd 0x0000000000010170 ctl 0x0000000000010376 bmdma 0x0000000000013088 irq 15
[   18.294251] scsi0 : pata_amd
[   18.616655] ata1.00: ATAPI, max MWDMA2
[   18.784434] ata1.00: configured for MWDMA2
[   18.784444] scsi1 : pata_amd
[   18.784643] ata2: port disabled. ignoring.
[   18.789061] scsi 0:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4244N 1.02 PQ: 0 ANSI: 5
[   18.793638] sata_nv 0000:00:0e.0: version 3.3
[   18.793651] PCI: Enabling device 0000:00:0e.0 (0005 -> 0007)
[   18.793917] ACPI: PCI Interrupt Link [LTID] enabled at IRQ 5
[   18.793919] PCI: setting IRQ 5 as level-triggered
[   18.793923] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LTID] -> GSI 5 (level, low) -> IRQ 5
[   18.793943] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   18.793984] ata3: SATA max UDMA/133 cmd 0x00000000000130c0 ctl 0x00000000000130b6 bmdma 0x0000000000013090 irq 5
[   18.794008] ata4: SATA max UDMA/133 cmd 0x00000000000130b8 ctl 0x00000000000130b2 bmdma 0x0000000000013098 irq 5
[   18.794019] scsi2 : sata_nv
[   19.263604] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   19.271751] ata3.00: ATA-7: TOSHIBA MK8034GSX, AH301H, max UDMA/100
[   19.271754] ata3.00: 156301488 sectors, multi 16: LBA48 
[   19.283732] ata3.00: configured for UDMA/100
[   19.283741] scsi3 : sata_nv
[   19.599144] ata4: SATA link down (SStatus 0 SControl 300)
[   19.609740] ATA: abnormal status 0x7F on port 0x00000000000130bf
[   19.609837] scsi 2:0:0:0: Direct-Access     ATA      TOSHIBA MK8034GS AH30 PQ: 0 ANSI: 5
[   19.611504] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 11
[   19.611508] PCI: setting IRQ 11 as level-triggered
[   19.611512] ACPI: PCI Interrupt 0000:07:05.0[A] -> Link [LNK1] -> GSI 11 (level, low) -> IRQ 11
[   19.663917] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[c3000000-c30007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   19.668320] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 11
[   19.668323] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LUS0] -> GSI 11 (level, low) -> IRQ 11
[   19.668334] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   19.668338] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[   19.668519] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[   19.668533] ohci_hcd 0000:00:0b.0: irq 11, io mem 0xc0004000
[   19.692429] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[   19.692434] Uniform CD-ROM driver Revision: 3.20
[   19.692483] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   19.695524] sr 0:0:0:0: Attached scsi generic sg0 type 5
[   19.695544] scsi 2:0:0:0: Attached scsi generic sg1 type 0
[   19.699251] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[   19.700866] sda: Write Protect is off
[   19.700869] sda: Mode Sense: 00 3a 00 00
[   19.701778] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   19.701852] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[   19.701861] sda: Write Protect is off
[   19.701863] sda: Mode Sense: 00 3a 00 00
[   19.701875] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   19.701880]  sda:<6>usb usb2: configuration #1 chosen from 1 choice
[   19.729207] hub 2-0:1.0: USB hub found
[   19.729220] hub 2-0:1.0: 8 ports detected
[   19.736608]  sda1 sda2 < sda5 sda6 sda7 > sda4
[   19.806237] sd 2:0:0:0: Attached scsi disk sda
[   20.081912] kjournald starting.  Commit interval 5 seconds
[   20.081921] EXT3-fs: mounted filesystem with ordered data mode.
[   20.138442] usb 2-3: new full speed USB device using ohci_hcd and address 2
[   20.376223] usb 2-3: configuration #1 chosen from 1 choice
[   20.685724] usb 2-6: new low speed USB device using ohci_hcd and address 3
[   20.902533] usb 2-6: configuration #1 chosen from 1 choice
[   20.945569] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[009fc0009484d800]
[   32.069291] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   32.080666] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   32.444275] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x3040
[   32.444303] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x3000
[   32.688524] sdhci: Secure Digital Host Controller Interface driver
[   32.688528] sdhci: Copyright(c) Pierre Ossman
[   32.688566] sdhci: SDHCI controller found at 0000:07:05.1 [1180:0822] (rev 19)
[   32.688847] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 11
[   32.688850] ACPI: PCI Interrupt 0000:07:05.1[B] -> Link [LNK2] -> GSI 11 (level, low) -> IRQ 11
[   32.688916] mmc0: SDHCI at 0xc3000800 irq 11 DMA
[   32.930080] Bluetooth: Core ver 2.11
[   32.930132] NET: Registered protocol family 31
[   32.930134] Bluetooth: HCI device and connection manager initialized
[   32.930137] Bluetooth: HCI socket layer initialized
[   32.995275] Bluetooth: HCI USB driver ver 2.9
[   33.046078] input: PC Speaker as /class/input/input2
[   33.133151] usbcore: registered new interface driver hci_usb
[   33.139411] usbcore: registered new interface driver hiddev
[   33.232656] input: USB Mouse as /class/input/input3
[   33.232730] input: USB HID v1.00 Mouse [USB Mouse] on usb-0000:00:0b.0-6
[   33.232742] usbcore: registered new interface driver usbhid
[   33.232745] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   33.283047] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 10
[   33.283052] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LAZA] -> GSI 10 (level, low) -> IRQ 10
[   33.283069] PCI: Setting latency timer of device 0000:00:10.1 to 64
[   33.657547] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000
[   33.721920] input: SynPS/2 Synaptics TouchPad as /class/input/input4
[   33.889320] fuse init (API version 7.8)
[   33.966759] lp: driver loaded but no devices found
[   34.232618] ndiswrapper version 1.41 loaded (smp=yes)
[   34.297598] usbcore: registered new interface driver ndiswrapper
[   34.540998] EXT3 FS on sda6, internal journal
[   34.772203] kjournald starting.  Commit interval 5 seconds
[   34.772537] EXT3 FS on sda7, internal journal
[   34.772541] EXT3-fs: mounted filesystem with ordered data mode.
[   35.104775] NET: Registered protocol family 10
[   35.104863] lo: Disabled Privacy Extensions
[   36.237384] NET: Registered protocol family 17
[   38.940506] No dock devices found.
[   38.972357] ACPI: AC Adapter [ACAD] (on-line)
[   38.991062] ACPI: Video Device [UVGA] (multi-head: yes  rom: no  post: no)
[   38.991189] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   39.102535] ACPI: Battery Slot [BAT0] (battery present)
[   39.117154] Using specific hotkey driver
[   39.172599] input: Power Button (FF) as /class/input/input5
[   39.176581] ACPI: Power Button (FF) [PWRF]
[   39.200556] input: Power Button (CM) as /class/input/input6
[   39.204330] ACPI: Power Button (CM) [PWRB]
[   39.227865] input: Sleep Button (CM) as /class/input/input7
[   39.231642] ACPI: Sleep Button (CM) [SLPB]
[   39.255486] input: Lid Switch as /class/input/input8
[   39.259277] ACPI: Lid Switch [LID]
[   39.291166] ibm_acpi: ec object not found
[   39.316373] pcc_acpi: loading...
[   39.326567] wmi_add device=ffff81003df6d800
[   39.326570] calling WQBA
[   39.528929] powernow-k8: Found 1 AMD Turion(tm) 64 Mobile Technology MK-36 processors (version 2.00.00)
[   39.528977] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x10
[   39.528980] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x12
[   39.528983] powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x14
[   39.528985] powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x18
[   45.866026] ppdev: user-space parallel port driver
[   47.099749] Bluetooth: L2CAP ver 2.8
[   47.099753] Bluetooth: L2CAP socket layer initialized
[   47.118480] Bluetooth: RFCOMM socket layer initialized
[   47.118491] Bluetooth: RFCOMM TTY layer initialized
[   47.118493] Bluetooth: RFCOMM ver 1.8
[   51.246103] eth0: no IPv6 routers present
[   79.722949] eth0: no IPv6 routers present

```

EW

---

### Post by skip27 on 2007-04-10
Hi Eigenwert,

I'm not too familiar with your setup, but I have a few ideas about where to start. The fact that your hardware isn't showing up at all would suggest to me either complete hardware failure or something outside of the OS.

First, are there any settings in the BIOS which control your wireless chip? If so, what are they set at? If there is no specific BIOS setting, there are a couple of things you can try. First, once in the BIOS configuration screen, reset all of your settings to default. Or second, you can reflash your BIOS with the latest version (or the same version if you wish). My theory is that if it isn't an explicit setting that controls your wireless chip, perhaps it is a secondary setting which indirectly affects its functionality.

Also, I would recommend booting into a different distro/OS altogether to isolate the problem. Does Knoppix see your hardware? Do you happen to have a spare version of Windows lying around? As much as I despise Microsoft, my main concern at this point is simply to isolate the problem. If Windows doesn't detect your hardware using Broadcom's drivers, I would suspect that your hardware is no longer functional.

---

### Post by Eigenwert on 2007-04-10
> **skip27 said:**
>   First, are there any settings in the BIOS which control your wireless chip? If so, what are they set at?

I didn't see any BIOS settings for my wireless chip. 

> **skip27 said:**
>  If there is no specific BIOS setting, there are a couple of things you can try. First, once in the BIOS configuration screen, reset all of your settings to default. 

Did that, booted into Windows and Edgy, no wireless.

> **skip27 said:**
>   Or second, you can reflash your BIOS with the latest version (or the same version if you wish). My theory is that if it isn't an explicit setting that controls your wireless chip, perhaps it is a secondary setting which indirectly affects its functionality. 

This is something I have never done before. The problem is, I'm flying out of town tomorrow, so I don't have time to do this, and wont until sometime next week.

> **skip27 said:**
>  Also, I would recommend booting into a different distro/OS altogether to isolate the problem. Does Knoppix see your hardware? Do you happen to have a spare version of Windows lying around? As much as I despise Microsoft, my main concern at this point is simply to isolate the problem. If Windows doesn't detect your hardware using Broadcom's drivers, I would suspect that your hardware is no longer functional.

I do still have Windows installed, and wireless was working with it earlier. Booted in now, and the card is no longer detected. So, my wireless card is boned. Since this laptop is only 5 months old, it should be covered under warranty. Still, this is a major pain in the backside. :mad: 

EW

---

### Post by bdogg64 on 2007-04-10
Yep, what he said. :)

---

