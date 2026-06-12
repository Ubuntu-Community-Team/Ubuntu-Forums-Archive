---
title: "Getting a printer to work/ checking if it can work."
date: 2009-01-22
forum: New to Ubuntu
---

### Post by tomsax on 2009-01-22
I have a rather old laser printer and I want to see if I can use it with Xubuntu.  It an Epson 5900L.  Nothing happens when I plug it in, but then this was the case with my webcam which I have now got working.  Any ideas on how to proceed?

Thanks a million!

Tom

---

### Post by compgeek83 on 2009-01-22
Never played with a directly connected printer in Linux, if the drivers are built in I would think it would be working with no problems just by plugging it in.

I have had really good luck with HP laserjets with built in print servers over a network.

---

### Post by blubaustin on 2009-01-22
[http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-EPL-5900L](http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-EPL-5900L)

Says it works, theres even instruction on that link.

---

### Post by notquitemichael on 2009-01-22
when you plug it in, turn it on (if possible,) and then run the dmesg command from the terminal.

you should see some information about the usb connection, if you post it on the forums people may be able to help you locate firmware etc.

---

### Post by tomsax on 2009-01-22
okay, this is what I got after typing dmesg


tom@tom-laptop:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-9-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Nov 20 21:57:00 UTC 2008 (Ubuntu 2.6.27-9.19-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000000bef0000 (usable)
[    0.000000]  BIOS-e820: 000000000bef0000 - 000000000beff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000000beff000 - 000000000bf00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000000bf00000 - 000000000c000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fffc0000 - 0000000100000000 (reserved)
[    0.000000] last_pfn = 0xbef0 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to bef0000 @ 7000-d000
[    0.000000] RAMDISK: 0b70c000 - 0bedfa7c
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP 000F7290, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 0BEF8CCA, 0030 (r1 PTLTD    RSDT    6040000  LTP        0)
[    0.000000] ACPI: FACP 0BEFEE2B, 0074 (r1 ATI    Raptor    6040000 ATI     F4240)
[    0.000000] ACPI: DSDT 0BEF8CFA, 6131 (r1    ATI U1_M1535  6040000 MSFT  100000D)
[    0.000000] ACPI: FACS 0BEFFFC0, 0040
[    0.000000] ACPI: BOOT 0BEFEE9F, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: SSDT 0BEFEEC7, 0139 (r1 PTLTD  POWERNOW  6040000  LTP        1)
[    0.000000] ACPI: DMI detected: Hewlett-Packard
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 190MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 0bef0000
[    0.000000]   low ram: 00000000 - 0bef0000
[    0.000000]   bootmap 00002000 - 000037e0
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 000bef0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c0a20]    TEXT DATA BSS ==> [0000100000 - 00005c0a20]
[    0.000000]   #4 [000b70c000 - 000bedfa7c]          RAMDISK ==> [000b70c000 - 000bedfa7c]
[    0.000000]   #5 [00005c1000 - 00005c4000]    INIT_PG_TABLE ==> [00005c1000 - 00005c4000]
[    0.000000]   #6 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #7 [0000007000 - 0000009000]          PGTABLE ==> [0000007000 - 0000009000]
[    0.000000]   #8 [0000002000 - 0000004000]          BOOTMAP ==> [0000002000 - 0000004000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0000bef0
[    0.000000]   HighMem  0x0000bef0 -> 0x0000bef0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0000bef0
[    0.000000] On node 0 totalpages: 48783
[    0.000000] free_area_init_node: node 0, pgdat c048a580, node_mem_map c1000000
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 44390 pages, LIFO batch:7
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffb000 (011b1000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d0000
[    0.000000] PM: Registered nosave memory: 00000000000d0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 10000000 (gap: c000000:f3fc0000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 48353
[    0.000000] Kernel command line: root=UUID=591c6c10-23c7-4212-bbd8-a1e3dc23b0a0 ro ROOTFLAGS=syncio quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 1855.097 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.004000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[    0.004000] Memory: 180064k/195520k available (2572k kernel code, 14916k reserved, 1160k data, 424k init, 0k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xcc800000 - 0xff3fe000   ( 811 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xcbef0000   ( 190 MB)
[    0.004000]       .init : 0xc04ab000 - 0xc0515000   ( 424 kB)
[    0.004000]       .data : 0xc038335a - 0xc04a5680   (1160 kB)
[    0.004000]       .text : 0xc0100000 - 0xc038335a   (2572 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004021] Calibrating delay loop (skipped), value calculated using timer frequency.. 3710.19 BogoMIPS (lpj=7420388)
[    0.004057] Security Framework initialized
[    0.004071] SELinux:  Disabled at boot.
[    0.004120] AppArmor: AppArmor initialized
[    0.004134] Mount-cache hash table entries: 512
[    0.004414] Initializing cgroup subsys ns
[    0.004421] Initializing cgroup subsys cpuacct
[    0.004424] Initializing cgroup subsys memory
[    0.004450] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004453] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004479] Checking 'hlt' instruction... OK.
[    0.020463] SMP alternatives: switching to UP code
[    0.026533] Freeing SMP alternatives: 11k freed
[    0.026540] ACPI: Core revision 20080609
[    0.032356] ACPI: Checking initramfs for custom DSDT
[    0.400346] ACPI: setting ELCR to 0200 (from 0e28)
[    0.402370] weird, boot CPU (#0) not listedby the BIOS.
[    0.402374] SMP motherboard not detected.
[    0.402379] Local APIC not detected. Using dummy APIC emulation.
[    0.402382] SMP disabled
[    0.402506] Brought up 1 CPUs
[    0.402510] Total of 1 processors activated (3710.19 BogoMIPS).
[    0.402532] CPU0 attaching sched-domain:
[    0.402538]  domain 0: span 0 level CPU
[    0.402542]   groups: 0
[    0.402974] net_namespace: 840 bytes
[    0.402991] Booting paravirtualized kernel on bare hardware
[    0.403237] Time: 20:13:18  Date: 01/22/09
[    0.403292] NET: Registered protocol family 16
[    0.403801] EISA bus registered
[    0.403826] ACPI: bus type pci registered
[    0.416405] PCI: PCI BIOS revision 2.10 entry at 0xfd87b, last bus=2
[    0.416409] PCI: Using configuration type 1 for base access
[    0.418870] ACPI: EC: Look up EC in DSDT
[    0.428907] ACPI: Interpreter enabled
[    0.428912] ACPI: (supports S0 S3 S4 S5)
[    0.428932] ACPI: Using PIC for interrupt routing
[    0.429262] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.456907] ACPI: EC: GPE = 0x18, I/O: command/status = 0x66, data = 0x62
[    0.456911] ACPI: EC: driver started in interrupt mode
[    0.456975] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.457073] PCI: 0000:00:00.0 reg 10 32bit mmio: [d4000000, d7ffffff]
[    0.457080] PCI: 0000:00:00.0 reg 14 32bit mmio: [d0500000, d0500fff]
[    0.457087] PCI: 0000:00:00.0 reg 18 io port: [8090, 8093]
[    0.457147] PCI: 0000:00:02.0 reg 10 32bit mmio: [d0000000, d0000fff]
[    0.457177] pci 0000:00:02.0: PME# supported from D3cold
[    0.457183] pci 0000:00:02.0: PME# disabled
[    0.457206] PCI: 0000:00:06.0 reg 10 io port: [8400, 84ff]
[    0.457212] PCI: 0000:00:06.0 reg 14 32bit mmio: [d0001000, d0001fff]
[    0.457238] pci 0000:00:06.0: supports D1
[    0.457241] pci 0000:00:06.0: supports D2
[    0.457243] pci 0000:00:06.0: PME# supported from D2 D3hot D3cold
[    0.457247] pci 0000:00:06.0: PME# disabled
[    0.457319] PCI: 0000:00:08.0 reg 10 32bit mmio: [d0002000, d0002fff]
[    0.457326] PCI: 0000:00:08.0 reg 14 io port: [8800, 88ff]
[    0.460033] pci 0000:00:08.0: PME# supported from D3hot D3cold
[    0.460038] pci 0000:00:08.0: PME# disabled
[    0.460062] PCI: 0000:00:0a.0 reg 10 32bit mmio: [80000000, 80000fff]
[    0.460073] pci 0000:00:0a.0: supports D1
[    0.460075] pci 0000:00:0a.0: supports D2
[    0.460078] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.460082] pci 0000:00:0a.0: PME# disabled
[    0.460118] PCI: 0000:00:10.0 reg 20 io port: [8080, 808f]
[    0.460177] pci 0000:00:11.0: quirk: region 8000-803f claimed by ali7101 ACPI
[    0.460181] pci 0000:00:11.0: quirk: region 8040-805f claimed by ali7101 SMB
[    0.460204] PCI: 0000:00:12.0 reg 10 io port: [8c00, 8cff]
[    0.460210] PCI: 0000:00:12.0 reg 14 32bit mmio: [d0004000, d0004fff]
[    0.460229] PCI: 0000:00:12.0 reg 30 32bit mmio: [0, ffff]
[    0.460240] pci 0000:00:12.0: supports D1
[    0.460242] pci 0000:00:12.0: supports D2
[    0.460245] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.460249] pci 0000:00:12.0: PME# disabled
[    0.460293] PCI: 0000:01:05.0 reg 10 32bit mmio: [e0000000, efffffff]
[    0.460299] PCI: 0000:01:05.0 reg 14 io port: [9000, 90ff]
[    0.460305] PCI: 0000:01:05.0 reg 18 32bit mmio: [d0100000, d010ffff]
[    0.460319] PCI: 0000:01:05.0 reg 30 32bit mmio: [0, 1ffff]
[    0.460332] pci 0000:01:05.0: supports D1
[    0.460334] pci 0000:01:05.0: supports D2
[    0.460360] PCI: bridge 0000:00:01.0 io port: [9000, 9fff]
[    0.460364] PCI: bridge 0000:00:01.0 32bit mmio: [d0100000, d01fffff]
[    0.460368] PCI: bridge 0000:00:01.0 32bit mmio pref: [e0000000, efffffff]
[    0.460388] bus 00 -> node 0
[    0.460397] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.460510] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
[    0.463269] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 *10)
[    0.463509] ACPI: PCI Interrupt Link [LNKB] (IRQs 7 *11)
[    0.463745] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 10) *0, disabled.
[    0.463982] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 10) *0, disabled.
[    0.464244] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 10) *0, disabled.
[    0.464482] ACPI: PCI Interrupt Link [LNKF] (IRQs 7 *11)
[    0.464718] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 6 10)
[    0.464954] ACPI: PCI Interrupt Link [LNKH] (IRQs *5 7)
[    0.465189] ACPI: PCI Interrupt Link [LNKU] (IRQs 3 4 6 10) *9
[    0.465446] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.465503] pnp: PnP ACPI init
[    0.465513] ACPI: bus type pnp registered
[    0.467114] pnp 00:07: mem resource (0xe0500000-0xe0500fff) overlaps 0000:00:01.0 BAR 9 (0xe0000000-0xefffffff), disabling
[    0.467131] pnp 00:07: io resource (0x8004-0x8005) overlaps 0000:00:11.0 BAR 7 (0x8000-0x803f), disabling
[    0.467139] pnp 00:07: mem resource (0xe0500000-0xe0500fff) overlaps 0000:01:05.0 BAR 0 (0xe0000000-0xefffffff), disabling
[    0.471956] pnp: PnP ACPI: found 11 devices
[    0.471959] ACPI: ACPI bus type pnp unregistered
[    0.471965] PnPBIOS: Disabled by ACPI PNP
[    0.472614] PCI: Using ACPI for IRQ routing
[    0.472771] NET: Registered protocol family 8
[    0.472771] NET: Registered protocol family 20
[    0.472771] NetLabel: Initializing
[    0.472771] NetLabel:  domain hash size = 128
[    0.472771] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.472771] NetLabel:  unlabeled traffic allowed by default
[    0.472771] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.472771]    actual entries 65620
[    0.472900] AppArmor: AppArmor Filesystem Enabled
[    0.472929] system 00:07: ioport range 0x40b-0x40b has been reserved
[    0.472929] system 00:07: ioport range 0x480-0x48f has been reserved
[    0.472929] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
[    0.472929] system 00:07: ioport range 0x4d6-0x4d6 has been reserved
[    0.472929] system 00:07: ioport range 0x8000-0x807f could not be reserved
[    0.472929] system 00:07: ioport range 0xff00-0xff01 has been reserved
[    0.472929] system 00:07: ioport range 0xfe00-0xfefe has been reserved
[    0.472929] system 00:07: iomem range 0xd0500000-0xd0500fff has been reserved
[    0.509233] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.509237] pci 0000:00:01.0:   IO window: 0x9000-0x9fff
[    0.509243] pci 0000:00:01.0:   MEM window: 0xd0100000-0xd01fffff
[    0.509247] pci 0000:00:01.0:   PREFETCH window: 0x000000e0000000-0x000000efffffff
[    0.509254] pci 0000:00:0a.0: CardBus bridge, secondary bus 0000:02
[    0.509258] pci 0000:00:0a.0:   IO window: 0x001000-0x0010ff
[    0.509262] pci 0000:00:0a.0:   IO window: 0x001400-0x0014ff
[    0.509267] pci 0000:00:0a.0:   PREFETCH window: 0x10000000-0x13ffffff
[    0.509271] pci 0000:00:0a.0:   MEM window: 0x14000000-0x17ffffff
[    0.509716] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 11
[    0.509722] PCI: setting IRQ 11 as level-triggered
[    0.509728] pci 0000:00:0a.0: PCI INT A -> Link[LNKF] -> GSI 11 (level, low) -> IRQ 11
[    0.509735] bus: 00 index 0 io port: [0, ffff]
[    0.509737] bus: 00 index 1 mmio: [0, ffffffff]
[    0.509740] bus: 01 index 0 io port: [9000, 9fff]
[    0.509743] bus: 01 index 1 mmio: [d0100000, d01fffff]
[    0.509745] bus: 01 index 2 mmio: [e0000000, efffffff]
[    0.509748] bus: 01 index 3 mmio: [0, 0]
[    0.509750] bus: 02 index 0 io port: [1000, 10ff]
[    0.509753] bus: 02 index 1 io port: [1400, 14ff]
[    0.509755] bus: 02 index 2 mmio: [10000000, 13ffffff]
[    0.509758] bus: 02 index 3 mmio: [14000000, 17ffffff]
[    0.509776] NET: Registered protocol family 2
[    0.509964] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.510292] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.510461] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.510632] TCP: Hash tables configured (established 8192 bind 8192)
[    0.510637] TCP reno registered
[    0.510736] NET: Registered protocol family 1
[    0.510930] checking if image is initramfs... it is
[    1.012135] Switched to high resolution mode on CPU 0
[    1.332139] Freeing initrd memory: 8014k freed
[    1.332489] Simple Boot Flag at 0x36 set to 0x1
[    1.333412] audit: initializing netlink socket (disabled)
[    1.333446] type=2000 audit(1232655199.332:1): initialized
[    1.339836] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.343644] VFS: Disk quotas dquot_6.5.1
[    1.343786] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.343971] msgmni has been set to 367
[    1.344207] io scheduler noop registered
[    1.344211] io scheduler anticipatory registered
[    1.344214] io scheduler deadline registered
[    1.344229] io scheduler cfq registered (default)
[    1.344247] pci 0000:00:00.0: ATI Northbridge, reserving I/O ports 0x3b0 to 0x3bb
[    1.560063] pci 0000:00:07.0: Activating ISA DMA hang workarounds
[    1.560097] pci 0000:01:05.0: Boot video device
[    1.560604] isapnp: Scanning for PnP cards...
[    1.827540] isapnp: No Plug & Play device found
[    1.889642] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.889863] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.891035] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.891730] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 3
[    1.891736] PCI: setting IRQ 3 as level-triggered
[    1.891742] serial 0000:00:08.0: PCI INT A -> Link[LNKG] -> GSI 3 (level, low) -> IRQ 3
[    1.891751] serial 0000:00:08.0: PCI INT A disabled
[    1.894593] brd: module loaded
[    1.894720] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.894929] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    1.899076] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.899087] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.899723] mice: PS/2 mouse device common for all mice
[    1.899951] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.899982] rtc0: alarms up to one month, y3k
[    1.900208] EISA: Probing bus 0 at eisa.0
[    1.900222] Cannot allocate resource for EISA slot 1
[    1.900250] Cannot allocate resource for EISA slot 8
[    1.900253] EISA: Detected 0 cards.
[    1.900260] cpuidle: using governor ladder
[    1.900262] cpuidle: using governor menu
[    1.900985] TCP cubic registered
[    1.901029] Using IPI No-Shortcut mode
[    1.901335] registered taskstats version 1
[    1.901476]   Magic number: 9:910:245
[    1.901574] tty ttyw1: hash matches
[    1.901900] rtc_cmos 00:02: setting system clock to 2009-01-22 20:13:22 UTC (1232655202)
[    1.901906] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.901908] EDD information not available.
[    1.902770] Freeing unused kernel memory: 424k freed
[    1.902837] Write protecting the kernel text: 2576k
[    1.902882] Write protecting the kernel read-only data: 936k
[    1.937395] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.193346] fuse init (API version 7.9)
[    2.431856] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    2.436930] processor ACPI0007:00: registered as cooling_device0
[    2.466722] thermal LNXTHERM:01: registered as thermal_zone0
[    2.468357] ACPI: Thermal Zone [THRM] (39 C)
[    3.675937] usbcore: registered new interface driver usbfs
[    3.675995] usbcore: registered new interface driver hub
[    3.691271] No dock devices found.
[    3.724650] usbcore: registered new device driver usb
[    3.784266] SCSI subsystem initialized
[    3.784411] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.784903] ACPI: PCI Interrupt Link [LNKU] enabled at IRQ 10
[    3.784908] PCI: setting IRQ 10 as level-triggered
[    3.784915] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LNKU] -> GSI 10 (level, low) -> IRQ 10
[    3.784938] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    3.785037] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[    3.785064] ohci_hcd 0000:00:02.0: irq 10, io mem 0xd0000000
[    3.791724] natsemi dp8381x driver, version 2.1, Sept 11, 2006
[    3.791727]   originally by Donald Becker <becker@scyld.com>
[    3.791729]   2.4.x kernel port by Jeff Garzik, Tjeerd Mulder
[    3.842452] usb usb1: configuration #1 chosen from 1 choice
[    3.842515] hub 1-0:1.0: USB hub found
[    3.842538] hub 1-0:1.0: 4 ports detected
[    3.874454] libata version 3.00 loaded.
[    4.049758] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[    4.049769] natsemi 0000:00:12.0: PCI INT A -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[    4.051792] natsemi eth0: NatSemi DP8381[56] at 0xd0004000 (0000:00:12.0), 00:0d:9d:c8:d1:e4, IRQ 11, port TP.
[    4.058003] pata_ali 0000:00:10.0: can't derive routing for PCI INT A
[    4.058732] scsi0 : pata_ali
[    4.058954] scsi1 : pata_ali
[    4.059319] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8080 irq 14
[    4.059325] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8088 irq 15
[    4.220695] ata1.00: ATA-6: FUJITSU MHT2030AT, 009B, max UDMA/100
[    4.220703] ata1.00: 58605120 sectors, multi 16: LBA 
[    4.232087] usb 1-2: new full speed USB device using ohci_hcd and address 2
[    4.236571] ata1.00: configured for UDMA/100
[    4.400415] ata2.00: ATAPI: SD-R2512, 1A04, max MWDMA2
[    4.400430] ata2.00: WARNING: ATAPI DMA disabled for reliablity issues.  It can be enabled
[    4.400434] ata2.00: WARNING: via pata_ali.atapi_dma modparam or corresponding sysfs node.
[    4.416360] ata2.00: configured for MWDMA2
[    4.416615] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHT2030A 009B PQ: 0 ANSI: 5
[    4.422442] scsi 1:0:0:0: CD-ROM            TOSHIBA  DVD-ROM SD-R2512 1A04 PQ: 0 ANSI: 5
[    4.679383] usb 1-2: configuration #1 chosen from 1 choice
[    4.855107] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    4.855170] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    4.887285] Driver 'sd' needs updating - please use bus_type methods
[    4.890220] sd 0:0:0:0: [sda] 58605120 512-byte hardware sectors (30006 MB)
[    4.890255] sd 0:0:0:0: [sda] Write Protect is off
[    4.890260] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.890304] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.890445] sd 0:0:0:0: [sda] 58605120 512-byte hardware sectors (30006 MB)
[    4.890467] sd 0:0:0:0: [sda] Write Protect is off
[    4.890471] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.890509] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.890516]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    4.942207] Marking TSC unstable due to TSC halts in idle
[    4.972821]  sda1 sda2 < sda5 >
[    4.997701] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.045908] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    5.045919] Uniform CD-ROM driver Revision: 3.20
[    5.046147] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    5.210681] PM: Starting manual resume from disk
[    5.210689] PM: Resume from partition 8:5
[    5.210691] PM: Checking hibernation image.
[    5.211023] PM: Resume from disk failed.
[    5.286158] kjournald starting.  Commit interval 5 seconds
[    5.286193] EXT3-fs: mounted filesystem with ordered data mode.
[   14.400223] udevd version 124 started
[   15.575953] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   15.634133] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   15.699764] Linux agpgart interface v0.103
[   15.772714] agpgart-ati 0000:00:00.0: Ati IGP320/M chipset
[   15.782959] agpgart-ati 0000:00:00.0: AGP aperture is 64M @ 0xd4000000
[   16.116511] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   16.178920] ACPI: AC Adapter [ACAD] (on-line)
[   16.265760] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[   16.271681] ACPI: Battery Slot [BAT1] (battery present)
[   16.276087] ACPI: Power Button (FF) [PWRF]
[   16.276704] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
[   16.292157] ACPI: Power Button (CM) [PWRB]
[   16.292475] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input5
[   16.302298] ACPI: Lid Switch [LID]
[   16.360658] ali15x3_smbus 0000:00:11.0: ALI15X3_smb region uninitialized - upgrade BIOS or use force_addr=0xaddr
[   16.360670] ali15x3_smbus 0000:00:11.0: ALI15X3 not detected, module not inserted.
[   16.422344] Yenta: CardBus bridge found at 0000:00:0a.0 [103c:0024]
[   16.422367] Yenta O2: res at 0x94/0xD4: 00/ea
[   16.422370] Yenta O2: enabling read prefetch/write burst
[   16.548796] Yenta: ISA IRQ mask 0x00b8, PCI irq 11
[   16.548803] Socket status: 30000829
[   16.854484] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/device:02/input/input6
[   16.868121] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   17.248066] pccard: CardBus card inserted into slot 0
[   17.248121] PCI: 0000:02:00.0 reg 10 32bit mmio: [0, ffff]
[   17.487506] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input7
[   17.604236] atkbd.c: Unknown key pressed (translated set 2, code 0xee on isa0060/serio0).
[   17.604245] atkbd.c: Use 'setkeycodes e06e <keycode>' to make it known.
[   17.614376] atkbd.c: Unknown key released (translated set 2, code 0xee on isa0060/serio0).
[   17.614383] atkbd.c: Use 'setkeycodes e06e <keycode>' to make it known.
[   17.821111] parport_pc 00:09: reported by Plug and Play ACPI
[   17.821188] parport0: PC-style at 0x378 (0x778), irq 7, dma 0 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   18.332652] Linux video capture interface: v2.00
[   18.483565] uvcvideo: Found UVC 1.00 device Live! Cam Optia (041e:4057)
[   18.492824] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 5
[   18.492832] PCI: setting IRQ 5 as level-triggered
[   18.492839] ALI 5451 0000:00:06.0: PCI INT A -> Link[LNKH] -> GSI 5 (level, low) -> IRQ 5
[   18.765341] input: Live! Cam Optia as /devices/pci0000:00/0000:00:02.0/usb1/1-2/1-2:1.0/input/input8
[   18.780622] usbcore: registered new interface driver uvcvideo
[   18.780632] USB Video Class driver (v0.1.0)
[   21.013266] ath_hal: module license 'Proprietary' taints kernel.
[   21.027517] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   21.111556] wlan: 0.9.4
[   21.167899] ath_pci: 0.9.4
[   21.183670] cs: IO port probe 0x100-0x3af: excluding 0x200-0x207 0x220-0x22f 0x330-0x337 0x388-0x38f
[   21.185910] cs: IO port probe 0x3e0-0x4ff: clean.
[   21.186772] cs: IO port probe 0x820-0x8ff: clean.
[   21.187613] cs: IO port probe 0xc00-0xcf7: clean.
[   21.188694] cs: IO port probe 0xa00-0xaff: clean.
[   21.236133] AC'97 1 does not respond - RESET
[   21.252142] AC'97 1 access is not valid [0xffffffff], removing mixer.
[   21.252157] ali mixer 1 creating error.
[   21.254732] ath_pci 0000:02:00.0: enabling device (0000 -> 0002)
[   21.254755] ath_pci 0000:02:00.0: PCI INT A -> Link[LNKF] -> GSI 11 (level, low) -> IRQ 11
[   21.872340] ath_rate_sample: 1.2 (0.9.4)
[   21.873273] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   21.873281] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   21.873294] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   21.873300] wifi0: mac 7.8 phy 4.5 radio 5.6
[   21.873307] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   21.873309] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   21.873312] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   21.873315] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   21.873318] wifi0: Use hw queue 8 for CAB traffic
[   21.873321] wifi0: Use hw queue 9 for beacons
[   21.890377] wifi0: Atheros 5212: mem=0x14000000, irq=11
[   22.427882] lp0: using parport0 (interrupt-driven).
[   22.604296] Adding 554200k swap on /dev/sda5.  Priority:-1 extents:1 across:554200k
[   23.338806] EXT3 FS on sda1, internal journal
[   24.653770] type=1505 audit(1232655225.417:2): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3802
[   24.654380] type=1505 audit(1232655225.417:3): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3802
[   24.883330] ip_tables: (C) 2000-2006 Netfilter Core Team
[   25.833998] ACPI: WMI: Mapper loaded
[   26.258507] powernow: PowerNOW! Technology present. Can scale: frequency and voltage.
[   26.264870] powernow: No PST tables match this cpuid (0x7a0)
[   26.264873] powernow: This is indicative of a broken BIOS.
[   26.264876] powernow: Trying ACPI perflib
[   26.266639] powernow: Minimum speed 530 MHz. Maximum speed 1855 MHz.
[   27.200230] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   27.320773] apm: BIOS not found.
[   27.552408] ppdev: user-space parallel port driver
[   28.508096] Clocksource tsc unstable (delta = -135061452 ns)
[   30.004288] Bluetooth: Core ver 2.13
[   30.008647] NET: Registered protocol family 31
[   30.008680] Bluetooth: HCI device and connection manager initialized
[   30.008688] Bluetooth: HCI socket layer initialized
[   30.037216] Bluetooth: L2CAP ver 2.11
[   30.037227] Bluetooth: L2CAP socket layer initialized
[   30.054698] Bluetooth: SCO (Voice Link) ver 0.6
[   30.054709] Bluetooth: SCO socket layer initialized
[   30.077233] Bluetooth: RFCOMM socket layer initialized
[   30.077830] Bluetooth: RFCOMM TTY layer initialized
[   30.077839] Bluetooth: RFCOMM ver 1.10
[   30.087708] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   30.087720] Bluetooth: BNEP filters: protocol multicast
[   30.130850] Bridge firewalling registered
[   30.131583] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   32.547943] pci 0000:01:05.0: power state changed by ACPI to D0
[   32.552397] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[   32.552432] pci 0000:01:05.0: PCI INT A -> Link[LNKC] -> GSI 10 (level, low) -> IRQ 10
[   32.938055] [drm] Initialized drm 1.1.0 20060810
[   33.022762] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[   33.583065] agpgart-ati 0000:00:00.0: AGP 2.0 bridge
[   33.583122] agpgart-ati 0000:00:00.0: putting AGP V2 device into 4x mode
[   33.583159] pci 0000:01:05.0: putting AGP V2 device into 4x mode
[   33.981550] [drm] Setting GART location based on new memory map
[   33.981572] [drm] Loading R100 Microcode
[   33.981621] [drm] writeback test succeeded in 1 usecs
[   34.269676] eth0: DSPCFG accepted after 0 usec.
[   34.355155] NET: Registered protocol family 17
[   56.109890] NET: Registered protocol family 10
[   56.113681] lo: Disabled Privacy Extensions
[   56.115451] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   66.468068] ath0: no IPv6 routers present
[  195.005084] ppdev0: registered pardevice
[  195.138371] ppdev0: unregistered pardevice
[  196.988475] ppdev0: registered pardevice
[  197.040190] ppdev0: unregistered pardevice
[  199.090735] ppdev0: registered pardevice
[  199.140770] ppdev0: unregistered pardevice
[ 2922.446204] usb 1-2: USB disconnect, address 2
[ 2922.992118] usb 1-2: new full speed USB device using ohci_hcd and address 3
[ 2923.451375] usb 1-2: configuration #1 chosen from 1 choice
[ 2923.457981] uvcvideo: Found UVC 1.00 device Live! Cam Optia (041e:4057)
[ 2923.544002] input: Live! Cam Optia as /devices/pci0000:00/0000:00:02.0/usb1/1-2/1-2:1.0/input/input9
[ 2924.029246] usb 1-2: USB disconnect, address 3
[ 2929.944160] usb 1-1: new full speed USB device using ohci_hcd and address 4
[ 2930.246949] usb 1-1: configuration #1 chosen from 1 choice
[ 2930.507351] usblp0: USB Bidirectional printer dev 4 if 0 alt 0 proto 2 vid 0x04B8 pid 0x0005
[ 2930.509628] usbcore: registered new interface driver usblp
[ 2933.792137] usb 1-2: new full speed USB device using ohci_hcd and address 5
[ 2934.300640] usb 1-2: configuration #1 chosen from 1 choice
[ 2934.305155] uvcvideo: Found UVC 1.00 device Live! Cam Optia (041e:4057)
[ 2934.589105] input: Live! Cam Optia as /devices/pci0000:00/0000:00:02.0/usb1/1-2/1-2:1.0/input/input10
[ 5007.526231] usb 1-1: USB disconnect, address 4
[ 5007.529665] usblp0: removed
[ 5016.012102] usb 1-1: new full speed USB device using ohci_hcd and address 6
[ 5016.244522] usb 1-1: configuration #1 chosen from 1 choice
[ 5016.259766] usblp0: USB Bidirectional printer dev 6 if 0 alt 0 proto 2 vid 0x04B8 pid 0x0005
tom@tom-laptop:~$

---

### Post by notquitemichael on 2009-01-22
well dmesg seems to suggest that it reconises the printer (see the last 4 lines.) i use kde no so i cannot remember exactly where it is, but in gnome there will be a 'cups' or 'install printers' menu in the administration menu. you'll have to add the printer using that first, but i do not see that you should have any other problems then that. :-)

---

### Post by Daveth on 2009-01-22
and if you type

[HTML]http://127.0.0.1:631/[/HTML]

into your browser, it will open the CUPS dialogue page for you to poke about in.

---

