---
title: "Network connection slowly dies after 5 min."
date: 2008-05-16
forum: Networking &amp; Wireless
---

### Post by Chainz on 2008-05-16
After fresh install (Ubuntu 8.04), working on wireless (LinkSys router), I started Firefox and opened few sites (mostly Ubuntu Documentation).
After few minutes (2 or 3) some sites stopped opening, then more stopped opening, after about 5 min. I couldn't open a single page.

I decided to install Opera - exactly same result.
Then I turned to wired connection - still the same!

Always after restart it works for few minutes.

And now I don't know what might be the problem, since all other computers in the network work fine, windows on the same machine works fine... :cry:

---

### Post by hermes0710 on 2008-05-16
Do what you and from the point that everything is getting messed up open a terminal and run the command "dmesg" and post here the output

---

### Post by arrancaru on 2008-05-17
Same problema with a gigaset se361 wireless router. Wireless on windows is fine but in ubuntu it dies after some minutes.

---

### Post by Chainz on 2008-05-19
Here it goes:

```
[    0.000000] Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e8000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ffb0000 (usable)
[    0.000000]  BIOS-e820: 000000007ffb0000 - 000000007ffc0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007ffc0000 - 000000007fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fff0000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
[    0.000000] 1151MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 524208) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   524208
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   524208
[    0.000000] On node 0 totalpages: 524208
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2303 pages used for memmap
[    0.000000]   HighMem zone: 292529 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FAD60 checksum 0
[    0.000000] ACPI: RSDP 000FAD60, 0021 (r2 ACPIAM)
[    0.000000] ACPI: XSDT 7FFB0100, 003C (r1 A M I  OEMXSDT  10000401 MSFT       97)
[    0.000000] ACPI: FACP 7FFB0290, 00F4 (r3 A M I  OEMFACP  10000401 MSFT       97)
[    0.000000] ACPI: DSDT 7FFB03F0, 3763 (r1  A0049 A0049000        0 INTL  2002026)
[    0.000000] ACPI: FACS 7FFC0000, 0040
[    0.000000] ACPI: APIC 7FFB0390, 005C (r1 A M I  OEMAPIC  10000401 MSFT       97)
[    0.000000] ACPI: OEMB 7FFC0040, 003F (r1 A M I  OEMBIOS  10000401 MSFT       97)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:2 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:2 APIC version 20
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:7fb80000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e8000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e8000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 520113
[    0.000000] Kernel command line: root=UUID=ae76d1bd-61b5-4882-98e1-fb98f5f60d3e ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2806.479 MHz processor.
[   33.339821] Console: colour VGA+ 80x25
[   33.339825] console [tty0] enabled
[   33.340283] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   33.340741] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   33.477876] Memory: 2066464k/2096832k available (2157k kernel code, 29044k reserved, 998k data, 364k init, 1179328k highmem)
[   33.477885] virtual kernel memory layout:
[   33.477886]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   33.477887]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   33.477888]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   33.477889]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   33.477890]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
[   33.477891]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
[   33.477892]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
[   33.477895] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   33.477940] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   33.557773] Calibrating delay using timer specific routine.. 5617.52 BogoMIPS (lpj=11235055)
[   33.557801] Security Framework initialized
[   33.557810] SELinux:  Disabled at boot.
[   33.557826] AppArmor: AppArmor initialized
[   33.557830] Failure registering capabilities with primary security module.
[   33.557839] Mount-cache hash table entries: 512
[   33.557989] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000 00000000
[   33.558002] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   33.558005] CPU: L2 cache: 512K
[   33.558007] CPU: Physical Processor ID: 0
[   33.558010] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b080 00004400 00000000 00000000 00000000
[   33.558022] Compat vDSO mapped to ffffe000.
[   33.558036] Checking 'hlt' instruction... OK.
[   33.574101] SMP alternatives: switching to UP code
[   33.575718] Early unpacking initramfs... done
[   33.891921] ACPI: Core revision 20070126
[   33.891967] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   33.893701] CPU0: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 05
[   33.893720] SMP alternatives: switching to SMP code
[   33.894359] Booting processor 1/1 eip 3000
[   33.904394] Initializing CPU#1
[   33.984757] Calibrating delay using timer specific routine.. 5613.17 BogoMIPS (lpj=11226359)
[   33.984766] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000 00000000
[   33.984777] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   33.984779] CPU: L2 cache: 512K
[   33.984781] CPU: Physical Processor ID: 0
[   33.984784] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b080 00004400 00000000 00000000 00000000
[   33.984993] CPU1: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 05
[   33.985034] Total of 2 processors activated (11230.70 BogoMIPS).
[   33.985163] ENABLING IO-APIC IRQs
[   33.985339] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   34.132559] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   34.152530] Brought up 2 CPUs
[   34.152555] CPU0 attaching sched-domain:
[   34.152559]  domain 0: span 03
[   34.152561]   groups: 01 02
[   34.152565]   domain 1: span 03
[   34.152567]    groups: 03
[   34.152570] CPU1 attaching sched-domain:
[   34.152572]  domain 0: span 03
[   34.152574]   groups: 02 01
[   34.152578]   domain 1: span 03
[   34.152580]    groups: 03
[   34.152896] net_namespace: 64 bytes
[   34.152907] Booting paravirtualized kernel on bare hardware
[   34.153485] Time: 19:34:28  Date: 05/19/08
[   34.153519] NET: Registered protocol family 16
[   34.153804] EISA bus registered
[   34.153810] ACPI: bus type pci registered
[   34.153991] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=2
[   34.153994] PCI: Using configuration type 1
[   34.153995] Setting up standard PCI resources
[   34.167166] ACPI: EC: Look up EC in DSDT
[   34.170995] ACPI: Interpreter enabled
[   34.170999] ACPI: (supports S0 S1 S3 S4 S5)
[   34.171017] ACPI: Using IOAPIC for interrupt routing
[   34.177349] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   34.177848] Force enabled HPET at base address 0xfed00000
[   34.177856] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[   34.177860] PCI quirk: region 0480-04bf claimed by ICH4 GPIO
[   34.178393] PCI: Transparent bridge - 0000:00:1e.0
[   34.178418] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   34.178517] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[   34.183964] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   34.184059] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   34.184154] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   34.184248] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 7 10 11 12 14 15)
[   34.184346] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 *6 7 10 11 12 14 15)
[   34.184439] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 *4 5 6 7 10 11 12 14 15)
[   34.184539] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[   34.184633] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   34.184790] Linux Plug and Play Support v0.97 (c) Adam Belay
[   34.184834] pnp: PnP ACPI init
[   34.184843] ACPI: bus type pnp registered
[   34.187626] pnp: PnP ACPI: found 11 devices
[   34.187629] ACPI: ACPI bus type pnp unregistered
[   34.187634] ASUS P4P800 detected. Disabling PnPBIOS
[   34.187636] PnPBIOS: Disabled
[   34.187986] PCI: Using ACPI for IRQ routing
[   34.187990] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   34.212243] NET: Registered protocol family 8
[   34.212246] NET: Registered protocol family 20
[   34.212377] hpet clockevent registered
[   34.212384] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   34.212390] hpet0: 3 64-bit timers, 14318180 Hz
[   34.213434] AppArmor: AppArmor Filesystem Enabled
[   34.216222] Time: tsc clocksource has been installed.
[   34.232246] system 00:07: ioport range 0x680-0x6ff has been reserved
[   34.232249] system 00:07: ioport range 0x290-0x297 has been reserved
[   34.232256] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   34.232259] system 00:08: ioport range 0x800-0x87f has been reserved
[   34.232262] system 00:08: ioport range 0x480-0x4bf has been reserved
[   34.232266] system 00:08: iomem range 0xfed20000-0xfed8ffff has been reserved
[   34.232269] system 00:08: iomem range 0xffb00000-0xffbfffff could not be reserved
[   34.232276] system 00:09: iomem range 0xfec00000-0xfec00fff has been reserved
[   34.232279] system 00:09: iomem range 0xfee00000-0xfee00fff has been reserved
[   34.232287] system 00:0a: iomem range 0x0-0x9ffff could not be reserved
[   34.232289] system 00:0a: iomem range 0xc0000-0xdffff could not be reserved
[   34.232292] system 00:0a: iomem range 0xe0000-0xfffff could not be reserved
[   34.232295] system 00:0a: iomem range 0x100000-0x7ffeffff could not be reserved
[   34.232298] system 00:0a: iomem range 0xfff00000-0xffffffff could not be reserved
[   34.262814] PCI: Bridge: 0000:00:01.0
[   34.262816]   IO window: disabled.
[   34.262822]   MEM window: fc900000-fe9fffff
[   34.262825]   PREFETCH window: cff00000-dfefffff
[   34.262831] PCI: Bridge: 0000:00:1e.0
[   34.262835]   IO window: d000-dfff
[   34.262841]   MEM window: fea00000-feafffff
[   34.262845]   PREFETCH window: disabled.
[   34.262861] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   34.262875] NET: Registered protocol family 2
[   34.304090] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   34.304425] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   34.305014] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   34.305364] TCP: Hash tables configured (established 131072 bind 65536)
[   34.305369] TCP reno registered
[   34.316177] checking if image is initramfs... it is
[   34.711202] Switched to high resolution mode on CPU 1
[   34.715042] Switched to high resolution mode on CPU 0
[   34.943171] Freeing initrd memory: 7694k freed
[   34.943889] audit: initializing netlink socket (disabled)
[   34.943904] audit(1211225668.348:1): initialized
[   34.944185] highmem bounce pool size: 64 pages
[   34.946768] VFS: Disk quotas dquot_6.5.1
[   34.946873] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   34.947040] io scheduler noop registered
[   34.947043] io scheduler anticipatory registered
[   34.947045] io scheduler deadline registered
[   34.947058] io scheduler cfq registered (default)
[   34.947144] Boot video device is 0000:01:00.0
[   34.947559] isapnp: Scanning for PnP cards...
[   35.300362] isapnp: No Plug & Play device found
[   35.339925] Real Time Clock Driver v1.12ac
[   35.340055] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   35.341660] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   35.341748] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   35.341889] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   35.344051] serio: i8042 KBD port at 0x60,0x64 irq 1
[   35.344058] serio: i8042 AUX port at 0x60,0x64 irq 12
[   35.353662] mice: PS/2 mouse device common for all mice
[   35.353836] EISA: Probing bus 0 at eisa.0
[   35.353875] EISA: Detected 0 cards.
[   35.353879] cpuidle: using governor ladder
[   35.353881] cpuidle: using governor menu
[   35.353979] NET: Registered protocol family 1
[   35.354013] Using IPI No-Shortcut mode
[   35.354046] registered taskstats version 1
[   35.354146]   Magic number: 8:466:597
[   35.354202]   hash matches device ptyd1
[   35.354270] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   35.354272] EDD information not available.
[   35.354591] Freeing unused kernel memory: 364k freed
[   35.373999] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   36.633404] fuse init (API version 7.9)
[   36.871482] usbcore: registered new interface driver usbfs
[   36.871516] usbcore: registered new interface driver hub
[   36.872189] usbcore: registered new device driver usb
[   36.882794] USB Universal Host Controller Interface driver v3.0
[   36.882872] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[   36.882888] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   36.882894] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   36.883191] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   36.883231] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000eec0
[   36.883432] usb usb1: configuration #1 chosen from 1 choice
[   36.883471] hub 1-0:1.0: USB hub found
[   36.883481] hub 1-0:1.0: 2 ports detected
[   36.986586] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
[   36.986601] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   36.986607] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   36.986646] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   36.986677] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000ef00
[   36.986850] usb usb2: configuration #1 chosen from 1 choice
[   36.986889] hub 2-0:1.0: USB hub found
[   36.986899] hub 2-0:1.0: 2 ports detected
[   37.090360] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   37.090377] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   37.090383] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   37.090418] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   37.090449] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ef20
[   37.090628] usb usb3: configuration #1 chosen from 1 choice
[   37.090667] hub 3-0:1.0: USB hub found
[   37.090677] hub 3-0:1.0: 2 ports detected
[   37.194080] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 16
[   37.194097] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   37.194103] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   37.194144] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   37.194172] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000ef40
[   37.194342] usb usb4: configuration #1 chosen from 1 choice
[   37.194384] hub 4-0:1.0: USB hub found
[   37.194394] hub 4-0:1.0: 2 ports detected
[   37.297913] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19
[   37.297934] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   37.297941] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   37.297979] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   37.301906] ehci_hcd 0000:00:1d.7: debug port 1
[   37.301919] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   37.301939] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xfebff800
[   37.317665] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   37.317846] usb usb5: configuration #1 chosen from 1 choice
[   37.317890] hub 5-0:1.0: USB hub found
[   37.317900] hub 5-0:1.0: 8 ports detected
[   37.341980] SCSI subsystem initialized
[   37.395361] libata version 3.00 loaded.
[   37.421543] ata_piix 0000:00:1f.1: version 2.12
[   37.421564] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[   37.421573] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   37.421638] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   37.426304] scsi0 : ata_piix
[   37.426425] scsi1 : ata_piix
[   37.428285] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[   37.428292] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[   37.648310] ata1.00: ATA-6: ST3120026A, 3.06, max UDMA/100
[   37.648314] ata1.00: 234441648 sectors, multi 16: LBA48 
[   37.664195] ata1.00: configured for UDMA/100
[   37.983449] ata2.00: ATAPI: LG CD-ROM CRD-8522B, 1.01, max MWDMA2
[   38.154820] ata2.00: configured for MWDMA2
[   38.154971] scsi 0:0:0:0: Direct-Access     ATA      ST3120026A       3.06 PQ: 0 ANSI: 5
[   38.155979] scsi 1:0:0:0: CD-ROM            LG       CD-ROM CRD-8522B 1.01 PQ: 0 ANSI: 5
[   38.157182] ACPI: PCI Interrupt 0000:02:05.0[A] -> GSI 22 (level, low) -> IRQ 20
[   38.157226] skge 1.13 addr 0xfeafc000 irq 20 chip Yukon-Lite rev 7
[   38.157653] skge eth0: addr 00:11:d8:27:15:7a
[   38.174302] Driver 'sd' needs updating - please use bus_type methods
[   38.174432] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   38.174458] sd 0:0:0:0: [sda] Write Protect is off
[   38.174462] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   38.174498] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   38.175003] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   38.175023] sd 0:0:0:0: [sda] Write Protect is off
[   38.175027] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   38.175057] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   38.175063]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   38.195069]  sda1 sda2 sda3 sda4 < sda5 sda6 >
[   38.240048] sd 0:0:0:0: [sda] Attached SCSI disk
[   38.245897] sr0: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
[   38.245903] Uniform CD-ROM driver Revision: 3.20
[   38.245975] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   38.255470] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   38.255507] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   38.719280] Attempting manual resume
[   38.719285] swsusp: Resume From Partition 8:6
[   38.719287] PM: Checking swsusp image.
[   38.719489] PM: Resume from disk failed.
[   38.736242] EXT3-fs: INFO: recovery required on readonly filesystem.
[   38.736251] EXT3-fs: write access will be enabled during recovery.
[   46.365409] kjournald starting.  Commit interval 5 seconds
[   46.365429] EXT3-fs: sda5: orphan cleanup on readonly fs
[   46.365438] ext3_orphan_cleanup: deleting unreferenced inode 254778
[   46.365484] ext3_orphan_cleanup: deleting unreferenced inode 278581
[   46.386089] ext3_orphan_cleanup: deleting unreferenced inode 278580
[   46.389846] ext3_orphan_cleanup: deleting unreferenced inode 278579
[   46.389864] ext3_orphan_cleanup: deleting unreferenced inode 424337
[   46.398674] ext3_orphan_cleanup: deleting unreferenced inode 424326
[   46.407825] ext3_orphan_cleanup: deleting unreferenced inode 424324
[   46.408953] ext3_orphan_cleanup: deleting unreferenced inode 254774
[   46.422231] ext3_orphan_cleanup: deleting unreferenced inode 269732
[   46.422257] ext3_orphan_cleanup: deleting unreferenced inode 269731
[   46.422275] ext3_orphan_cleanup: deleting unreferenced inode 269729
[   46.432494] ext3_orphan_cleanup: deleting unreferenced inode 253375
[   46.448694] ext3_orphan_cleanup: deleting unreferenced inode 254876
[   46.448717] ext3_orphan_cleanup: deleting unreferenced inode 254635
[   46.461551] ext3_orphan_cleanup: deleting unreferenced inode 294019
[   46.471957] ext3_orphan_cleanup: deleting unreferenced inode 294015
[   46.482151] ext3_orphan_cleanup: deleting unreferenced inode 254923
[   46.498146] ext3_orphan_cleanup: deleting unreferenced inode 310102
[   46.498349] ext3_orphan_cleanup: deleting unreferenced inode 310101
[   46.498366] ext3_orphan_cleanup: deleting unreferenced inode 310100
[   46.498381] ext3_orphan_cleanup: deleting unreferenced inode 310099
[   46.498397] ext3_orphan_cleanup: deleting unreferenced inode 310098
[   46.498414] ext3_orphan_cleanup: deleting unreferenced inode 310097
[   46.498430] ext3_orphan_cleanup: deleting unreferenced inode 310096
[   46.498447] ext3_orphan_cleanup: deleting unreferenced inode 310095
[   46.503041] ext3_orphan_cleanup: deleting unreferenced inode 310094
[   46.503058] ext3_orphan_cleanup: deleting unreferenced inode 310093
[   46.503074] ext3_orphan_cleanup: deleting unreferenced inode 310092
[   46.503091] ext3_orphan_cleanup: deleting unreferenced inode 310090
[   46.503107] ext3_orphan_cleanup: deleting unreferenced inode 310089
[   46.503123] ext3_orphan_cleanup: deleting unreferenced inode 310088
[   46.508463] ext3_orphan_cleanup: deleting unreferenced inode 301921
[   46.508659] ext3_orphan_cleanup: deleting unreferenced inode 254625
[   46.515218] ext3_orphan_cleanup: deleting unreferenced inode 254780
[   46.517796] ext3_orphan_cleanup: deleting unreferenced inode 254499
[   46.524624] ext3_orphan_cleanup: deleting unreferenced inode 254737
[   46.532252] ext3_orphan_cleanup: deleting unreferenced inode 254573
[   46.536883] ext3_orphan_cleanup: deleting unreferenced inode 254571
[   46.554385] ext3_orphan_cleanup: deleting unreferenced inode 278694
[   46.554569] ext3_orphan_cleanup: deleting unreferenced inode 278687
[   46.554589] ext3_orphan_cleanup: deleting unreferenced inode 277945
[   46.564697] ext3_orphan_cleanup: deleting unreferenced inode 277988
[   46.564717] ext3_orphan_cleanup: deleting unreferenced inode 277974
[   46.571225] ext3_orphan_cleanup: deleting unreferenced inode 277972
[   46.573187] ext3_orphan_cleanup: deleting unreferenced inode 277968
[   46.579030] ext3_orphan_cleanup: deleting unreferenced inode 277966
[   46.581019] ext3_orphan_cleanup: deleting unreferenced inode 277960
[   46.583546] ext3_orphan_cleanup: deleting unreferenced inode 254491
[   46.592727] ext3_orphan_cleanup: deleting unreferenced inode 254489
[   46.602212] ext3_orphan_cleanup: deleting unreferenced inode 254407
[   46.608353] ext3_orphan_cleanup: deleting unreferenced inode 254405
[   46.612449] ext3_orphan_cleanup: deleting unreferenced inode 254497
[   46.618987] ext3_orphan_cleanup: deleting unreferenced inode 254837
[   46.625382] ext3_orphan_cleanup: deleting unreferenced inode 254832
[   46.625580] ext3_orphan_cleanup: deleting unreferenced inode 253565
[   46.625601] ext3_orphan_cleanup: deleting unreferenced inode 440665
[   46.625614] ext3_orphan_cleanup: deleting unreferenced inode 440648
[   46.625624] ext3_orphan_cleanup: deleting unreferenced inode 440647
[   46.625634] ext3_orphan_cleanup: deleting unreferenced inode 440646
[   46.625644] ext3_orphan_cleanup: deleting unreferenced inode 440645
[   46.625654] ext3_orphan_cleanup: deleting unreferenced inode 440644
[   46.625663] EXT3-fs: sda5: 61 orphan inodes deleted
[   46.625665] EXT3-fs: recovery complete.
[   46.953023] EXT3-fs: mounted filesystem with ordered data mode.
[   53.848158] intel_rng: FWH not detected
[   54.015910] iTCO_vendor_support: vendor-support=0
[   54.075750] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   54.075916] iTCO_wdt: Found a ICH5 or ICH5R TCO device (Version=1, TCOBASE=0x0860)
[   54.075977] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   54.147658] Linux agpgart interface v0.102
[   54.219487] agpgart: Detected an Intel 865 Chipset.
[   54.230132] agpgart: AGP aperture is 256M @ 0xe0000000
[   54.295247] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   54.355173] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   54.447210] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   54.697444] input: Power Button (FF) as /devices/virtual/input/input3
[   54.734082] ACPI: Power Button (FF) [PWRF]
[   54.734239] input: Power Button (CM) as /devices/virtual/input/input4
[   54.769559] ACPI: Power Button (CM) [PWRB]
[   56.132162] gameport: EMU10K1 is pci0000:02:09.1/gameport0, io 0xdff0, speed 1147kHz
[   56.198136] nvidia: module license 'NVIDIA' taints kernel.
[   56.404489] input: PS2++ Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[   56.712615] ACPI: PCI Interrupt 0000:02:0c.0[A] -> GSI 20 (level, low) -> IRQ 21
[   56.726582] phy0: Selected rate control algorithm 'simple'
[   57.059180] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   57.059434] NVRM: loading NVIDIA Linux x86 Kernel Module  96.43.05  Tue Jan 22 19:36:58 PST 2008
[   57.154294] ACPI: PCI Interrupt 0000:02:09.0[A] -> GSI 21 (level, low) -> IRQ 22
[   57.154325] snd-ca0106: Model 1002 Rev 00000000 Serial 10021102
[   58.524070] lp: driver loaded but no devices found
[   58.757352] Adding 779112k swap on /dev/sda6.  Priority:-1 extents:1 across:779112k
[   59.317770] EXT3 FS on sda5, internal journal
[   60.555623] ip_tables: (C) 2000-2006 Netfilter Core Team
[   60.989126] No dock devices found.
[   64.187935] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   64.187943] apm: disabled - APM is not SMP safe.
[   64.451984] ppdev: user-space parallel port driver
[   64.634140] audit(1211218498.234:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5038 profile="/usr/sbin/cupsd" namespace="default"
[   65.725857] Bluetooth: Core ver 2.11
[   65.727007] NET: Registered protocol family 31
[   65.727015] Bluetooth: HCI device and connection manager initialized
[   65.727023] Bluetooth: HCI socket layer initialized
[   65.772349] skge eth0: enabling interface
[   65.781181] Bluetooth: L2CAP ver 2.9
[   65.781188] Bluetooth: L2CAP socket layer initialized
[   65.847124] Bluetooth: RFCOMM socket layer initialized
[   65.847149] Bluetooth: RFCOMM TTY layer initialized
[   65.847153] Bluetooth: RFCOMM ver 1.8
[   67.507070] skge eth0: Link is up at 100 Mbps, full duplex, flow control both
[   67.953962] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   67.953991] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   67.954029] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   69.245287] NET: Registered protocol family 10
[   69.246794] lo: Disabled Privacy Extensions
[   69.249369] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   69.915379] NET: Registered protocol family 17
[   86.840424] eth0: no IPv6 routers present
[  228.782336] NVRM: Xid (0001:00): 6, PE0000 0414 00ff9007 0000fba4 00196400 00ff9007
[  279.379752] NVRM: Xid (0001:00): 6, PE0000 15c0 00000000 0000fc40 000df5c0 00ffffff
[  317.312919] NVRM: Xid (0001:00): 6, PE0000 043c 00ffffff 0000fc40 000df598 00ffffff
[ 1230.861237] NVRM: Xid (0001:00): 6, PE0000 0404 00d7d9e0 0000fdbc 000d6400 00d7d9e0
[ 1230.876741] NVRM: Xid (0001:00): 6, PE0000 0000 01017c00 000007ac 00000000 00086400
[ 1235.015189] NVRM: Xid (0001:00): 6, PE0000 0404 00d7d9e0 0000fdfc 00096400 00d7d9e0
[ 1235.026458] NVRM: Xid (0001:00): 13, 0000 01014200 00000062 00000300 00086400 00000002
[ 1243.691015] NVRM: Xid (0001:00): 6, PE0000 10bc 00d7d9e0 0000f28c 0cc56400 00d7d9e0
[ 1244.697834] NVRM: Xid (0001:00): 6, PE0000 0404 00d7d9e0 0000fdc4 00096400 00d7d9e0
[ 1244.715102] NVRM: Xid (0001:00): 6, PE0000 0000 01017c00 000007a4 00000000 01010037
[ 1245.585571] NVRM: Xid (0001:00): 6, PE0000 0400 fffafbfc 0000fdfc 000d6400 00d7d9e0
[ 1245.684280] NVRM: Xid (0001:00): 6, PE0000 0404 00cdd1d8 0000fdf8 00096400 00cdd1d8
[ 1245.696271] NVRM: Xid (0001:00): 13, 0000 01014200 00000062 00000300 00086400 00000002
[ 1246.703189] NVRM: Xid (0001:00): 6, PE0000 10bc 00d7d9e0 0000f28c 0cc16400 00d7d9e0
[ 1247.123045] NVRM: Xid (0001:00): 6, PE0000 0404 00d7d9e0 0000fdfc 000d6400 00d7d9e0
[ 1247.139335] NVRM: Xid (0001:00): 13, 0000 01014200 00000062 00000300 00086400 00000002
```

Hope you could figure something out of it :)

---

### Post by jtrindle on 2008-05-19
Could you post a copy/past text capture of top -n 1 ?

The -n 1 means it will run only once, instead of continuously, which makes it easier to capture.

I'm looking for the first four lines.

Thanks!

---

### Post by Chainz on 2008-05-20
I'll try to put the output later in the evening today.

But just an update:
Running system from live CD, with Wireless card, removed from the machine, still gives same problem. :(

---

### Post by Chainz on 2008-05-20
Of course I need to sun it as root, so the command looks like:
```
sudo dmesg -n 1
```
and gives totally no output :(

...Unless you asked me to run: ```
top -n 1
```
with output:
```

top - 21:58:03 up 34 min,  2 users,  load average: 0.12, 0.18, 0.11
Tasks: 118 total,   1 running, 117 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.4%us,  0.7%sy,  0.1%ni, 95.2%id,  1.5%wa,  0.0%hi,  0.2%si,  0.0%st
Mem:   2075460k total,   603240k used,  1472220k free,    32724k buffers
Swap:   779112k total,        0k used,   779112k free,   300016k cached

 PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
6444 seb       20   0  208m  79m  23m S    2  3.9   0:48.83 firefox            
   1 root      20   0  2844 1692  544 S    0  0.1   0:01.26 init              
   2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd          
   3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
   4 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0        
   5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0        
   6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
   7 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1        
   8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1        
   9 root      15  -5     0    0    0 S    0  0.0   0:00.02 events/0          
  10 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/1          
  11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper            
  47 root      15  -5     0    0    0 S    0  0.0   0:00.04 kblockd/0          
  48 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/1          
  51 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpid            
  52 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify      
 120 root      15  -5     0    0    0 S    0  0.0   0:00.00 kseriod            
 
```

---

