---
title: "USB Bluetooth Adapter"
date: 2008-07-29
forum: Networking &amp; Wireless
---

### Post by castles on 2008-07-29
I have a porto usb bluetooth adapter that I've been trying to get to work in Ubuntu Hardy. The model number is BA-500 and the only information I can find in Google is [this]("http://www.lmc.com.au/products/Networking_-_Wireless/Porto/554685/Porto_Micro_Bluetooth_USB_Adapter_%5BBA-500%5D")

This is my lsusb output:
```
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 046d:c51b Logitech, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000
```  

and my hciconfig output:

```
hci0:	Type: USB
	BD Address: 00:00:00:00:00:00 ACL MTU: 0:0 SCO MTU: 0:0
	DOWN 
	RX bytes:0 acl:0 sco:0 events:0 errors:0
	TX bytes:0 acl:0 sco:0 commands:0 errors:0
```

Any suggestions on what I should try or should I just go out and buy a better supported dongle?

---

### Post by p221072 on 2008-07-29
Post the output of the *dmesg *command after you plug in the device

---

### Post by castles on 2008-07-29
here it is..

```
[    0.000000] Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fff0000 (usable)
[    0.000000]  BIOS-e820: 000000007fff0000 - 000000007fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fff3000 - 0000000080000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 1151MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f5310
[    0.000000] Entering add_active_range(0, 0, 524272) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   524272
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   524272
[    0.000000] On node 0 totalpages: 524272
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2303 pages used for memmap
[    0.000000]   HighMem zone: 292593 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F6E50 checksum 0
[    0.000000] ACPI: RSDP 000F6E50, 0014 (r0 GBT   )
[    0.000000] ACPI: RSDT 7FFF3000, 002C (r1 GBT    AWRDACPI 42302E31 AWRD  1010101)
[    0.000000] ACPI: FACP 7FFF3040, 0074 (r1 GBT    AWRDACPI 42302E31 AWRD  1010101)
[    0.000000] ACPI: DSDT 7FFF30C0, 417E (r1 GBT    AWRDACPI     1000 MSFT  100000C)
[    0.000000] ACPI: FACS 7FFF0000, 0040
[    0.000000] ACPI: APIC 7FFF7240, 0068 (r1 GBT    AWRDACPI 42302E31 AWRD  1010101)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:2 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:2 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:7ec00000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 520177
[    0.000000] Kernel command line: root=UUID=f6b1941f-b381-49ca-92bc-e9365b582fa9 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2612.665 MHz processor.
[   29.748265] Console: colour VGA+ 80x25
[   29.748269] console [tty0] enabled
[   29.748717] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   29.749161] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   29.896454] Memory: 2067096k/2097088k available (2157k kernel code, 28628k reserved, 998k data, 364k init, 1179584k highmem)
[   29.896464] virtual kernel memory layout:
[   29.896465]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   29.896466]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   29.896467]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   29.896468]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   29.896470]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
[   29.896471]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
[   29.896472]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
[   29.896475] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   29.896520] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   29.976352] Calibrating delay using timer specific routine.. 5229.72 BogoMIPS (lpj=10459449)
[   29.976382] Security Framework initialized
[   29.976390] SELinux:  Disabled at boot.
[   29.976407] AppArmor: AppArmor initialized
[   29.976411] Failure registering capabilities with primary security module.
[   29.976420] Mount-cache hash table entries: 512
[   29.976573] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000 00000000
[   29.976587] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   29.976590] CPU: L2 cache: 512K
[   29.976593] CPU: Physical Processor ID: 0
[   29.976595] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b080 00004400 00000000 00000000 00000000
[   29.976608] Compat vDSO mapped to ffffe000.
[   29.976622] Checking 'hlt' instruction... OK.
[   29.992688] SMP alternatives: switching to UP code
[   29.994365] Early unpacking initramfs... done
[   30.313943] ACPI: Core revision 20070126
[   30.313993] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   30.319643] CPU0: Intel(R) Pentium(R) 4 CPU 2.60GHz stepping 09
[   30.319663] SMP alternatives: switching to SMP code
[   30.320310] Booting processor 1/1 eip 3000
[   30.330383] Initializing CPU#1
[   30.407324] Calibrating delay using timer specific routine.. 5225.48 BogoMIPS (lpj=10450975)
[   30.407334] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000 00000000
[   30.407345] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   30.407347] CPU: L2 cache: 512K
[   30.407350] CPU: Physical Processor ID: 0
[   30.407352] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b080 00004400 00000000 00000000 00000000
[   30.407564] CPU1: Intel(R) Pentium(R) 4 CPU 2.60GHz stepping 09
[   30.407607] Total of 2 processors activated (10455.21 BogoMIPS).
[   30.407738] ENABLING IO-APIC IRQs
[   30.407916] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   30.555129] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   30.575100] Brought up 2 CPUs
[   30.575125] CPU0 attaching sched-domain:
[   30.575128]  domain 0: span 03
[   30.575131]   groups: 01 02
[   30.575135]   domain 1: span 03
[   30.575138]    groups: 03
[   30.575141] CPU1 attaching sched-domain:
[   30.575143]  domain 0: span 03
[   30.575145]   groups: 02 01
[   30.575149]   domain 1: span 03
[   30.575151]    groups: 03
[   30.575472] net_namespace: 64 bytes
[   30.575479] Booting paravirtualized kernel on bare hardware
[   30.576094] Time:  8:35:10  Date: 04/16/08
[   30.576128] NET: Registered protocol family 16
[   30.576432] EISA bus registered
[   30.576439] ACPI: bus type pci registered
[   30.600467] PCI: PCI BIOS revision 2.10 entry at 0xfb5f0, last bus=3
[   30.600470] PCI: Using configuration type 1
[   30.600472] Setting up standard PCI resources
[   30.608577] ACPI: EC: Look up EC in DSDT
[   30.612929] ACPI: Interpreter enabled
[   30.612933] ACPI: (supports S0 S1 S4 S5)
[   30.612951] ACPI: Using IOAPIC for interrupt routing
[   30.617958] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   30.618488] Force enabled HPET at base address 0xfed00000
[   30.618495] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[   30.618499] PCI quirk: region 1080-10bf claimed by ICH4 GPIO
[   30.619359] PCI: Transparent bridge - 0000:00:1e.0
[   30.619389] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   30.619529] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   30.626069] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   30.626185] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
[   30.626289] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[   30.626394] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   30.626498] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   30.626604] ACPI: PCI Interrupt Link [LNKF] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[   30.626709] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   30.626815] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 *4 5 6 7 9 10 11 12 14 15)
[   30.627011] Linux Plug and Play Support v0.97 (c) Adam Belay
[   30.627060] pnp: PnP ACPI init
[   30.627071] ACPI: bus type pnp registered
[   30.627291] pnpacpi: exceeded the max number of mem resources: 12
[   30.629570] pnp: PnP ACPI: found 10 devices
[   30.629573] ACPI: ACPI bus type pnp unregistered
[   30.629578] PnPBIOS: Disabled by ACPI PNP
[   30.629946] PCI: Using ACPI for IRQ routing
[   30.629951] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   30.674865] NET: Registered protocol family 8
[   30.674868] NET: Registered protocol family 20
[   30.675007] hpet clockevent registered
[   30.675013] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   30.675019] hpet0: 3 64-bit timers, 14318180 Hz
[   30.676063] AppArmor: AppArmor Filesystem Enabled
[   30.678694] Time: tsc clocksource has been installed.
[   30.694864] system 00:00: iomem range 0xf0000-0xf3fff could not be reserved
[   30.694868] system 00:00: iomem range 0xf4000-0xf7fff could not be reserved
[   30.694871] system 00:00: iomem range 0xf8000-0xfbfff could not be reserved
[   30.694874] system 00:00: iomem range 0xfc000-0xfffff could not be reserved
[   30.694877] system 00:00: iomem range 0x7fff0000-0x7fffffff could not be reserved
[   30.694880] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[   30.694884] system 00:00: iomem range 0x100000-0x7ffeffff could not be reserved
[   30.694887] system 00:00: iomem range 0xfec00000-0xfec00fff could not be reserved
[   30.694890] system 00:00: iomem range 0xfee00000-0xfee00fff could not be reserved
[   30.694893] system 00:00: iomem range 0xfed20000-0xfed8ffff could not be reserved
[   30.694897] system 00:00: iomem range 0xffb00000-0xffb7ffff could not be reserved
[   30.694900] system 00:00: iomem range 0xfff00000-0xffffffff could not be reserved
[   30.694910] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
[   30.694913] system 00:03: ioport range 0x290-0x29f has been reserved
[   30.694916] system 00:03: ioport range 0x800-0x805 has been reserved
[   30.725475] PCI: Bridge: 0000:00:01.0
[   30.725479]   IO window: b000-bfff
[   30.725485]   MEM window: f8000000-f9ffffff
[   30.725489]   PREFETCH window: e8000000-f7ffffff
[   30.725493] PCI: Bridge: 0000:00:03.0
[   30.725497]   IO window: a000-afff
[   30.725502]   MEM window: fc000000-fc0fffff
[   30.725505]   PREFETCH window: disabled.
[   30.725511] PCI: Bridge: 0000:00:1e.0
[   30.725514]   IO window: 7000-9fff
[   30.725520]   MEM window: fa000000-fbffffff
[   30.725524]   PREFETCH window: disabled.
[   30.725545] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   30.725559] NET: Registered protocol family 2
[   30.762728] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   30.763071] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   30.763661] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   30.764006] TCP: Hash tables configured (established 131072 bind 65536)
[   30.764012] TCP reno registered
[   30.774814] checking if image is initramfs... it is
[   31.177516] Switched to high resolution mode on CPU 0
[   31.177658] Switched to high resolution mode on CPU 1
[   31.406619] Freeing initrd memory: 7279k freed
[   31.407347] audit: initializing netlink socket (disabled)
[   31.407362] audit(1208334910.392:1): initialized
[   31.407646] highmem bounce pool size: 64 pages
[   31.410375] VFS: Disk quotas dquot_6.5.1
[   31.410480] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   31.410649] io scheduler noop registered
[   31.410652] io scheduler anticipatory registered
[   31.410654] io scheduler deadline registered
[   31.410669] io scheduler cfq registered (default)
[   31.410754] Boot video device is 0000:01:00.0
[   31.411184] isapnp: Scanning for PnP cards...
[   31.764300] isapnp: No Plug & Play device found
[   31.803995] Real Time Clock Driver v1.12ac
[   31.804130] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   31.805825] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   31.805917] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   31.806062] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   31.808955] serio: i8042 KBD port at 0x60,0x64 irq 1
[   31.808965] serio: i8042 AUX port at 0x60,0x64 irq 12
[   31.827985] mice: PS/2 mouse device common for all mice
[   31.828169] EISA: Probing bus 0 at eisa.0
[   31.828177] Cannot allocate resource for EISA slot 1
[   31.828200] Cannot allocate resource for EISA slot 7
[   31.828202] Cannot allocate resource for EISA slot 8
[   31.828204] EISA: Detected 0 cards.
[   31.828208] cpuidle: using governor ladder
[   31.828210] cpuidle: using governor menu
[   31.828310] NET: Registered protocol family 1
[   31.828343] Using IPI No-Shortcut mode
[   31.828378] registered taskstats version 1
[   31.828496]   Magic number: 4:66:574
[   31.828555]   hash matches device ptyb6
[   31.828619] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   31.828621] EDD information not available.
[   31.828926] Freeing unused kernel memory: 364k freed
[   31.850136] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   33.112847] fuse init (API version 7.9)
[   33.133768] ACPI: Fan [FAN] (on)
[   33.143065] ACPI: Thermal Zone [THRM] (22 C)
[   33.367067] usbcore: registered new interface driver usbfs
[   33.367104] usbcore: registered new interface driver hub
[   33.370199] usbcore: registered new device driver usb
[   33.380152] USB Universal Host Controller Interface driver v3.0
[   33.380241] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[   33.380259] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   33.380266] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   33.380589] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   33.380631] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000cc00
[   33.380859] usb usb1: configuration #1 chosen from 1 choice
[   33.380910] hub 1-0:1.0: USB hub found
[   33.380921] hub 1-0:1.0: 2 ports detected
[   33.452508] SCSI subsystem initialized
[   33.483964] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
[   33.483980] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   33.483986] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   33.484028] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   33.484059] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000c000
[   33.484235] usb usb2: configuration #1 chosen from 1 choice
[   33.484276] hub 2-0:1.0: USB hub found
[   33.484286] hub 2-0:1.0: 2 ports detected
[   33.507766] libata version 3.00 loaded.
[   33.589561] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   33.589580] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   33.589587] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   33.589641] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   33.589676] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000c400
[   33.589893] usb usb3: configuration #1 chosen from 1 choice
[   33.589942] hub 3-0:1.0: USB hub found
[   33.589959] hub 3-0:1.0: 2 ports detected
[   33.591251] Intel(R) PRO/1000 Network Driver - version 7.3.20-k2-NAPI
[   33.591258] Copyright (c) 1999-2006 Intel Corporation.
[   33.691446] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 16
[   33.691464] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   33.691471] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   33.691510] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   33.691536] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000c800
[   33.691717] usb usb4: configuration #1 chosen from 1 choice
[   33.691760] hub 4-0:1.0: USB hub found
[   33.691769] hub 4-0:1.0: 2 ports detected
[   33.795438] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19
[   33.795459] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   33.795465] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   33.795514] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   33.799438] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   33.799457] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xfc100000
[   33.827000] usb 2-1: new full speed USB device using uhci_hcd and address 2
[   33.838975] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   33.839176] usb usb5: configuration #1 chosen from 1 choice
[   33.839219] hub 5-0:1.0: USB hub found
[   33.839230] hub 5-0:1.0: 8 ports detected
[   33.949504] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 18 (level, low) -> IRQ 18
[   33.949520] PCI: Setting latency timer of device 0000:02:01.0 to 64
[   34.307021] e1000: 0000:02:01.0: e1000_probe: (PCI:33MHz:32-bit) 00:20:ed:8c:27:2a
[   34.546241] usb 5-5: new high speed USB device using ehci_hcd and address 3
[   34.580480] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[   34.580563] ACPI: PCI Interrupt 0000:03:04.2[B] -> GSI 21 (level, low) -> IRQ 20
[   34.630329] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[fb010000-fb0107ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   34.632692] ACPI: PCI Interrupt 0000:03:0a.0[A] -> GSI 22 (level, low) -> IRQ 21
[   34.682477] ohci1394: fw-host1: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[fb012000-fb0127ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   34.709030] usb 5-5: configuration #1 chosen from 1 choice
[   34.764955] ata_piix 0000:00:1f.1: version 2.12
[   34.764978] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   34.765030] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   34.766132] scsi0 : ata_piix
[   34.766235] scsi1 : ata_piix
[   34.767229] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[   34.767234] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[   34.948222] usb 2-1: new full speed USB device using uhci_hcd and address 3
[   35.108111] ata1.00: ATAPI: HITACHI CDR-8435, 0010, max MWDMA2
[   35.109707] usb 2-1: configuration #1 chosen from 1 choice
[   35.112145] sysfs: duplicate filename 'usbdev2.3_ep81' can not be created
[   35.112153] WARNING: at /build/buildd/linux-2.6.24/fs/sysfs/dir.c:424 sysfs_add_one()
[   35.112159] Pid: 1386, comm: khubd Not tainted 2.6.24-16-generic #1
[   35.112169]  [<c01d29af>] sysfs_add_one+0x9f/0xe0
[   35.112182]  [<c01d379a>] sysfs_create_link+0x8a/0x110
[   35.112193]  [<c027b9bc>] device_add+0x14c/0x510
[   35.112201]  [<c0210b29>] kobject_init+0x29/0x40
[   35.112209]  [<f88a06aa>] usb_create_ep_files+0x17a/0x2f0 [usbcore]
[   35.112249]  [<f889fa97>] usb_create_sysfs_intf_files+0xb7/0xe0 [usbcore]
[   35.112278]  [<f889b532>] usb_set_configuration+0x3a2/0x5d0 [usbcore]
[   35.112311]  [<f88a3b06>] generic_probe+0x76/0xb0 [usbcore]
[   35.112342]  [<f889d393>] usb_probe_device+0x33/0x40 [usbcore]
[   35.112367]  [<c027d988>] driver_probe_device+0x88/0x190
[   35.112376]  [<c0315065>] klist_next+0x55/0xb0
[   35.112385]  [<c027cc84>] bus_for_each_drv+0x44/0x70
[   35.112394]  [<c027db56>] device_attach+0x86/0x90
[   35.112399]  [<c027da90>] __device_attach+0x0/0x10
[   35.112406]  [<c027cbf5>] bus_attach_device+0x45/0x90
[   35.112414]  [<c027bc88>] device_add+0x418/0x510
[   35.112423]  [<f88962f6>] usb_new_device+0x56/0xa0 [usbcore]
[   35.112450]  [<f8897a97>] hub_thread+0x687/0xcb0 [usbcore]
[   35.112474]  [<c021345e>] rb_erase+0x15e/0x280
[   35.112489]  [<c0140b70>] autoremove_wake_function+0x0/0x40
[   35.112499]  [<f8897410>] hub_thread+0x0/0xcb0 [usbcore]
[   35.112523]  [<c01408b2>] kthread+0x42/0x70
[   35.112530]  [<c0140870>] kthread+0x0/0x70
[   35.112537]  [<c0105677>] kernel_thread_helper+0x7/0x10
[   35.112546]  =======================
[   35.112755] sysfs: duplicate filename 'usbdev2.3_ep83' can not be created
[   35.112761] WARNING: at /build/buildd/linux-2.6.24/fs/sysfs/dir.c:424 sysfs_add_one()
[   35.112768] Pid: 1386, comm: khubd Not tainted 2.6.24-16-generic #1
[   35.112775]  [<c01d29af>] sysfs_add_one+0x9f/0xe0
[   35.112787]  [<c01d379a>] sysfs_create_link+0x8a/0x110
[   35.112798]  [<c027b9bc>] device_add+0x14c/0x510
[   35.112807]  [<c0210b29>] kobject_init+0x29/0x40
[   35.112814]  [<f88a06aa>] usb_create_ep_files+0x17a/0x2f0 [usbcore]
[   35.112845]  [<f889fa97>] usb_create_sysfs_intf_files+0xb7/0xe0 [usbcore]
[   35.112869]  [<f889b532>] usb_set_configuration+0x3a2/0x5d0 [usbcore]
[   35.112901]  [<f88a3b06>] generic_probe+0x76/0xb0 [usbcore]
[   35.112929]  [<f889d393>] usb_probe_device+0x33/0x40 [usbcore]
[   35.112949]  [<c027d988>] driver_probe_device+0x88/0x190
[   35.112958]  [<c0315065>] klist_next+0x55/0xb0
[   35.112968]  [<c027cc84>] bus_for_each_drv+0x44/0x70
[   35.112977]  [<c027db56>] device_attach+0x86/0x90
[   35.112982]  [<c027da90>] __device_attach+0x0/0x10
[   35.112988]  [<c027cbf5>] bus_attach_device+0x45/0x90
[   35.112995]  [<c027bc88>] device_add+0x418/0x510
[   35.113004]  [<f88962f6>] usb_new_device+0x56/0xa0 [usbcore]
[   35.113027]  [<f8897a97>] hub_thread+0x687/0xcb0 [usbcore]
[   35.113047]  [<c021345e>] rb_erase+0x15e/0x280
[   35.113059]  [<c0140b70>] autoremove_wake_function+0x0/0x40
[   35.113068]  [<f8897410>] hub_thread+0x0/0xcb0 [usbcore]
[   35.113085]  [<c01408b2>] kthread+0x42/0x70
[   35.113090]  [<c0140870>] kthread+0x0/0x70
[   35.113095]  [<c0105677>] kernel_thread_helper+0x7/0x10
[   35.113104]  =======================
[   35.117099] ata1.01: HPA unlocked: 117229295 -> 117231408, native 117231408
[   35.117109] ata1.01: ATA-5: ST360021A, 3.19, max UDMA/100
[   35.117115] ata1.01: 117231408 sectors, multi 16: LBA 
[   35.117137] ata1.00: device is on DMA blacklist, disabling DMA
[   35.169098] usbcore: registered new interface driver libusual
[   35.178074] usbcore: registered new interface driver hiddev
[   35.178219] Initializing USB Mass Storage driver...
[   35.178495] scsi2 : SCSI emulation for USB Mass Storage devices
[   35.178609] usb-storage: device found at 3
[   35.178613] usb-storage: waiting for device to settle before scanning
[   35.181206] input: Bluetooth Device Bluetooth Device as /devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1:1.2/input/input2
[   35.204658] input,hidraw0: USB HID v1.10 Keyboard [Bluetooth Device Bluetooth Device] on usb-0000:00:1d.1-1
[   35.207891] input: Bluetooth Device Bluetooth Device as /devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1:1.3/input/input3
[   35.227590] input,hidraw1: USB HID v1.10 Mouse [Bluetooth Device Bluetooth Device] on usb-0000:00:1d.1-1
[   35.227626] usbcore: registered new interface driver usbhid
[   35.227633] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   35.227690] usbcore: registered new interface driver usb-storage
[   35.227695] USB Mass Storage support registered.
[   35.288593] ata1.00: configured for PIO4
[   35.303699] ata1.01: configured for UDMA/100
[   35.531050] ata2.00: HPA unlocked: 234439535 -> 234441648, native 234441648
[   35.531059] ata2.00: ATA-6: ST3120022A, 8.01, max UDMA/100
[   35.531064] ata2.00: 234441648 sectors, multi 16: LBA48 
[   35.547143] ata2.00: configured for UDMA/100
[   35.553454] scsi 0:0:0:0: CD-ROM            HITACHI  CDR-8435         0010 PQ: 0 ANSI: 5
[   35.553667] scsi 0:0:1:0: Direct-Access     ATA      ST360021A        3.19 PQ: 0 ANSI: 5
[   35.553863] scsi 1:0:0:0: Direct-Access     ATA      ST3120022A       8.01 PQ: 0 ANSI: 5
[   35.572108] Driver 'sr' needs updating - please use bus_type methods
[   35.575693] Driver 'sd' needs updating - please use bus_type methods
[   35.606433] sr0: scsi3-mmc drive: 32x/32x cd/rw xa/form2 cdda tray
[   35.606439] Uniform CD-ROM driver Revision: 3.20
[   35.606513] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   35.606827] sd 0:0:1:0: [sda] 117231408 512-byte hardware sectors (60022 MB)
[   35.606852] sd 0:0:1:0: [sda] Write Protect is off
[   35.606857] sd 0:0:1:0: [sda] Mode Sense: 00 3a 00 00
[   35.606898] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   35.606989] sd 0:0:1:0: [sda] 117231408 512-byte hardware sectors (60022 MB)
[   35.607014] sd 0:0:1:0: [sda] Write Protect is off
[   35.607019] sd 0:0:1:0: [sda] Mode Sense: 00 3a 00 00
[   35.607062] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   35.607068]  sda:<5>sr 0:0:0:0: Attached scsi generic sg0 type 5
[   35.612409] sd 0:0:1:0: Attached scsi generic sg1 type 0
[   35.612443] scsi 1:0:0:0: Attached scsi generic sg2 type 0
[   35.625692]  sda1 sda2 < sda5 >
[   35.645248] sd 0:0:1:0: [sda] Attached SCSI disk
[   35.645374] sd 1:0:0:0: [sdb] 234441648 512-byte hardware sectors (120034 MB)
[   35.645399] sd 1:0:0:0: [sdb] Write Protect is off
[   35.645404] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   35.645442] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   35.645529] sd 1:0:0:0: [sdb] 234441648 512-byte hardware sectors (120034 MB)
[   35.645552] sd 1:0:0:0: [sdb] Write Protect is off
[   35.645556] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   35.645593] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   35.645599]  sdb: sdb1 sdb2 < sdb5 >
[   35.681460] sd 1:0:0:0: [sdb] Attached SCSI disk
[   35.898061] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023c00910522af]
[   36.033801] ieee1394: Host added: ID:BUS[1-00:1023]  GUID[0020ed0a008a712c]
[   36.056834] Attempting manual resume
[   36.056838] swsusp: Resume From Partition 8:21
[   36.056840] PM: Checking swsusp image.
[   36.057041] PM: Resume from disk failed.
[   36.098877] kjournald starting.  Commit interval 5 seconds
[   36.098895] EXT3-fs: mounted filesystem with ordered data mode.
[   40.163578] usb-storage: device scan complete
[   40.164065] scsi 2:0:0:0: Direct-Access              USB DISK 2.0     PMAP PQ: 0 ANSI: 0 CCS
[   40.165539] sd 2:0:0:0: [sdc] 2015232 512-byte hardware sectors (1032 MB)
[   40.166165] sd 2:0:0:0: [sdc] Write Protect is off
[   40.166168] sd 2:0:0:0: [sdc] Mode Sense: 23 00 00 00
[   40.166171] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[   40.168779] sd 2:0:0:0: [sdc] 2015232 512-byte hardware sectors (1032 MB)
[   40.169404] sd 2:0:0:0: [sdc] Write Protect is off
[   40.169408] sd 2:0:0:0: [sdc] Mode Sense: 23 00 00 00
[   40.169411] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[   40.169417]  sdc: sdc1
[   40.170729] sd 2:0:0:0: [sdc] Attached SCSI removable disk
[   40.170772] sd 2:0:0:0: Attached scsi generic sg3 type 0
[   45.356793] Linux agpgart interface v0.102
[   45.427683] agpgart: Detected an Intel i875 Chipset.
[   45.432854] agpgart: AGP aperture is 128M @ 0xe0000000
[   45.567230] intel_rng: FWH not detected
[   45.635087] EDAC MC: Ver: 2.1.0 Apr 10 2008
[   45.718907] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   45.813335] EDAC i82875p: i82875p init one
[   45.814142] PCI: Unable to reserve mem region #1:1000@fecf0000 for device 0000:00:06.0
[   45.814311] EDAC MC0: Giving out device to 'i82875p_edac' 'i82875p': DEV 0000:00:00.0
[   45.814358] EDAC PCI0: Giving out device to module 'i82875p_edac' controller 'EDAC PCI controller': DEV '0000:00:00.0' (POLLED)
[   45.854686] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   45.894121] iTCO_vendor_support: vendor-support=0
[   45.946487] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   45.990222] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   45.990351] iTCO_wdt: Found a ICH5 or ICH5R TCO device (Version=1, TCOBASE=0x1060)
[   45.990398] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   46.427460] input: Power Button (FF) as /devices/virtual/input/input5
[   46.452572] ACPI: Power Button (FF) [PWRF]
[   46.452755] input: Power Button (CM) as /devices/virtual/input/input6
[   46.487935] ACPI: Power Button (CM) [PWRB]
[   46.679790] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input7
[   47.776123] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   48.032200] [fglrx] Maximum main memory to use for locked dma buffers: 1899 MBytes.
[   48.032251] [fglrx] ASYNCIO init succeed!
[   48.032484] [fglrx] PAT is enabled successfully!
[   48.051377] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
[   48.193121] gameport: EMU10K1 is pci0000:03:04.1/gameport0, io 0x7400, speed 1147kHz
[   48.712444] ACPI: PCI Interrupt 0000:03:02.0[A] -> GSI 22 (level, low) -> IRQ 21
[   48.720553] phy0: Selected rate control algorithm 'simple'
[   48.767251] Bluetooth: Core ver 2.11
[   48.827490] NET: Registered protocol family 31
[   48.827495] Bluetooth: HCI device and connection manager initialized
[   48.827502] Bluetooth: HCI socket layer initialized
[   48.860987] Bluetooth: HCI USB driver ver 2.9
[   48.863358] usbcore: registered new interface driver hci_usb
[   49.527651] ACPI: PCI Interrupt 0000:03:04.0[A] -> GSI 18 (level, low) -> IRQ 18
[   49.531553] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/emu10k1/../../alsa-kernel/pci/emu10k1/emufx.c:1544: Installing spdif_bug patch: Audigy 2 Platinum [SB0240P]
[   50.778364] lp: driver loaded but no devices found
[   50.937882] Adding 4803392k swap on /dev/sdb5.  Priority:-1 extents:1 across:4803392k
[   51.509991] EXT3 FS on sdb1, internal journal
[   52.759036] ip_tables: (C) 2000-2006 Netfilter Core Team
[   54.517068] No dock devices found.
[   55.911054] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   55.911061] apm: disabled - APM is not SMP safe.
[   56.208731] ppdev: user-space parallel port driver
[   56.408278] audit(1208334935.778:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5245 profile="/usr/sbin/cupsd" namespace="default"
[   56.547905] RPC: Registered udp transport module.
[   56.547913] RPC: Registered tcp transport module.
[   56.600581] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   56.700677] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   56.717714] NFSD: starting 90-second grace period
[   59.152211] hci_usb_intr_rx_submit: hci0 intr rx submit failed urb dfbc3794 err -22
[   59.188456] Bluetooth: L2CAP ver 2.9
[   59.188465] Bluetooth: L2CAP socket layer initialized
[   59.290561] Bluetooth: RFCOMM socket layer initialized
[   59.290581] Bluetooth: RFCOMM TTY layer initialized
[   59.290585] Bluetooth: RFCOMM ver 1.8
[   59.294878] hci_cmd_task: hci0 command tx timeout
[   61.288451] hci_cmd_task: hci0 command tx timeout
[   62.043858] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   64.761601] [fglrx] Internal AGP support requested, but kernel AGP support active.
[   64.761611] [fglrx] Have to use kernel AGP support to avoid conflicts.
[   64.761617] [fglrx] AGP detected, AgpState   = 0x1f004a1b (hardware caps of chipset)
[   64.761801] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   64.761822] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   64.761857] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   64.761909] [fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
[   64.770915] [fglrx] GART Table is not in FRAME_BUFFER range 
[   64.770930] [fglrx] Reserve Block - 0 offset =  0X0 length = 0X40000
[   64.770935] [fglrx] Reserve Block - 1 offset =  0X7fff000 length = 0X1000
[   64.877421] [fglrx] interrupt source 20008000 successfully enabled
[   64.877432] [fglrx] enable ID = 0x00000004
[   64.877445] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
[   64.877569] [fglrx] interrupt source 10000000 successfully enabled
[   64.877573] [fglrx] enable ID = 0x00000005
[   64.877581] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
[   67.312810] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[   68.605646] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[   69.898476] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[   71.199289] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[   72.492110] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[   73.784933] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[   75.077761] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[   76.370589] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[   77.679378] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[   78.976223] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[   79.652959] NET: Registered protocol family 10
[   79.653566] lo: Disabled Privacy Extensions
[   79.656581] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   79.657476] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   80.269034] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[   81.561865] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[   82.858679] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[   84.151508] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[   85.444329] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[   86.745140] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[   86.987986] NET: Registered protocol family 17
[   87.996020] wlan0: Initial auth_alg=0
[   87.996034] wlan0: authenticate with AP 00:13:f7:08:31:34
[   87.999369] wlan0: RX authentication from 00:13:f7:08:31:34 (alg=0 transaction=2 status=0)
[   87.999379] wlan0: authenticated
[   87.999384] wlan0: associate with AP 00:13:f7:08:31:34
[   88.009766] wlan0: RX AssocResp from 00:13:f7:08:31:34 (capab=0x431 status=0 aid=2)
[   88.009777] wlan0: associated
[   88.009785] wlan0: CTS protection enabled (BSSID=00:13:f7:08:31:34)
[   88.009790] wlan0: switched to short barker preamble (BSSID=00:13:f7:08:31:34)
[   88.014421] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   88.037991] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[   89.338782] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[   90.609178] padlock: VIA PadLock not detected.
[   90.647562] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[   91.940393] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[   93.233219] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[   94.581928] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[   95.888493] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[   97.183526] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[   98.432452] wlan0: no IPv6 routers present
[   98.476367] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[   99.773172] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  101.066003] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  102.422666] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  103.715503] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  105.008324] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  106.305140] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  107.597969] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  108.890797] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  109.476425] wlan0: CTS protection disabled (BSSID=00:13:f7:08:31:34)
[  110.183626] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  111.476461] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  112.769286] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  114.062112] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  115.354948] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  116.655750] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  117.944587] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  119.241405] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  120.534236] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  121.827068] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  123.123879] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  124.416708] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  125.711280] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  126.024584] wlan0: CTS protection enabled (BSSID=00:13:f7:08:31:34)
[  126.072630] wlan0: no IPv6 routers present
[  127.006360] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  128.299184] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  129.595996] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  130.892817] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  132.185647] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  133.482511] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  134.775333] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  136.068120] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  137.364957] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  138.661775] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  139.962566] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  141.258876] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  142.552213] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  143.849050] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  145.141877] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  146.434709] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  147.731507] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  149.024332] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  150.317176] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  151.618051] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  152.922789] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  154.215640] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  155.513916] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  156.809224] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  158.102052] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  159.394892] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  160.691712] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  161.988539] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  163.281351] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  164.570199] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  165.863038] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  167.155840] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  168.452656] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  169.745494] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  171.038343] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  172.335136] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  173.683828] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  174.980649] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  176.278096] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  177.574288] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  178.867129] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  180.159937] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  181.456755] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  182.765544] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  184.062372] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  185.367178] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  186.672383] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  187.980753] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  189.273587] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  190.574404] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  191.879180] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  193.183984] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  194.476985] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  195.769661] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  197.062508] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  198.355302] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  199.648133] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  200.944955] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  202.241762] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  203.534590] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  204.839395] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  206.144188] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  207.441002] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  208.737815] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  210.030658] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  211.323479] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  212.616314] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  213.909129] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  215.201953] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  216.494782] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  217.787625] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  219.080438] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  220.373265] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  221.666114] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  222.962916] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  224.255745] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  225.544584] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  226.837413] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  228.130238] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  229.423109] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  230.715893] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  232.012714] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  233.305550] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  234.598384] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  235.891198] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  237.187137] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  238.490857] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  239.785642] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  241.082458] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  242.383279] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  243.676120] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  244.976920] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  246.272928] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  247.574536] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  248.867379] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  249.739672] wlan0: CTS protection disabled (BSSID=00:13:f7:08:31:34)
[  250.160181] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  251.454694] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  252.749831] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  254.050645] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  255.349473] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  256.652255] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  257.951477] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  259.319896] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  260.614585] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  261.907386] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  262.495916] wlan0: CTS protection enabled (BSSID=00:13:f7:08:31:34)
[  263.200211] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  264.548904] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  265.853682] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  267.150502] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  268.447314] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  269.740154] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  271.036971] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  272.329809] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  273.626610] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  274.920832] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  276.216260] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  277.513079] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  278.805989] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  280.102717] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  281.399559] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  282.692360] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  283.985190] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  285.278020] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  286.570845] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  287.863678] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  289.160504] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  290.459627] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  291.754126] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  293.046956] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  294.339782] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  295.632610] usb 2-1: reset full speed USB device using uhci_hcd and address 3
```

---

### Post by p221072 on 2008-07-29
It seems like the device cannot be mounted and keeps on being resetted:
*usb 2-1: reset full speed USB device using uhci_hcd and address 3*
I'm afraid the adapter is not supported by the generic drivers, I'm sorry I can't help you.

---

### Post by castles on 2008-07-29
Ahh well, thanks for trying.

---

### Post by markers on 2008-09-04
hey guys. I've been looking around and I saw this thread and hoped that anyone would be able to help me. I am also having a difficult time getting my bluetooth adapter to play nice with Hardy. If anyone can help my Bluetooth dongle is an Anycom USB-500.

---

### Post by castles on 2008-09-04
My suggestion.. do what I did and jumped onto ebay and purchased a new adapter for $8 delivered (It did take 2 weeks to arrive).

---

### Post by KittyKitty on 2011-04-23
I actually get nearly an identical error message (error -28) during my plug/unplugging of a broadcom 2045a adapter that does have drivers and does work, the problem was related to current load on the hub i was plugging the device into.
moved it to a powered port and all was well

---

