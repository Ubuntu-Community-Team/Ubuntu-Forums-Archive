---
title: "ndiswrapper with mrv8k51 causes freeze upon login"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by noead01 on 2008-12-03
Hi,

I just installed ubuntu 8.10, and I followed the instructions to install the windows driver for my wireless card (Marvell chipset) into ndiswrapper.

Everything works a treat, and I can even connect to the network.

The issue is that when I restart my PC, ubuntu will freeze just after I enter my credentials in the login screen.

I then have to (forcibly) reboot, enter recovery mode, run "ndiswrapper -r mrv8k51", and then reboot again so it will let me log in without freezing.

I then have to run ndisgtk again to install the ndiswrapper driver again.

I read in older threads that this might be linked to a driver conflict and I try to blacklist every possible wireless driver, to no avail.

Has anyone seen that issue? Is there a solution to this?

Thanks in advance.

---

### Post by adult swim on 2008-12-03
if you run ```
dmesg
``` from a terminal what does it return?

---

### Post by noead01 on 2008-12-04
Here's the output from dmesg:

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-9-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Nov 20 21:57:00 UTC 2008 (Ubuntu 2.6.27-9.19-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
[    0.000000]  BIOS-e820: 000000001fff0000 - 000000001fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001fff3000 - 0000000020000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] last_pfn = 0x1fff0 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 1fff0000 @ 7000-d000
[    0.000000] RAMDISK: 1f80e000 - 1ffdf1d5
[    0.000000] DMI 2.2 present.
[    0.000000] ACPI: RSDP 000F6DA0, 0014 (r0 IntelR)
[    0.000000] ACPI: RSDT 1FFF3000, 002C (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 1FFF3040, 0074 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 1FFF30C0, 4045 (r1 INTELR AWRDACPI     1000 MSFT  100000C)
[    0.000000] ACPI: FACS 1FFF0000, 0040
[    0.000000] ACPI: APIC 1FFF7140, 0054 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 1fff0000
[    0.000000]   low ram: 00000000 - 1fff0000
[    0.000000]   bootmap 00002000 - 00006000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 001fff0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c0a20]    TEXT DATA BSS ==> [0000100000 - 00005c0a20]
[    0.000000]   #4 [001f80e000 - 001ffdf1d5]          RAMDISK ==> [001f80e000 - 001ffdf1d5]
[    0.000000]   #5 [00005c1000 - 00005c4000]    INIT_PG_TABLE ==> [00005c1000 - 00005c4000]
[    0.000000]   #6 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #7 [0000007000 - 0000009000]          PGTABLE ==> [0000007000 - 0000009000]
[    0.000000]   #8 [0000002000 - 0000006000]          BOOTMAP ==> [0000002000 - 0000006000]
[    0.000000] found SMP MP-table at [c00f53b0] 000f53b0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0001fff0
[    0.000000]   HighMem  0x0001fff0 -> 0x0001fff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x000000a0
[    0.000000]     0: 0x00000100 -> 0x0001fff0
[    0.000000] On node 0 totalpages: 130960
[    0.000000] free_area_init_node: node 0, pgdat c048a580, node_mem_map c1000000
[    0.000000]   DMA zone: 3964 pages, LIFO batch:0
[    0.000000]   Normal zone: 125844 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dfb00000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 129808
[    0.000000] Kernel command line: root=UUID=efcfdc98-6175-4ee7-938a-fc43a52c927d ro  single
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 1808.371 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.004000] Memory: 505668k/524224k available (2572k kernel code, 17984k reserved, 1160k data, 424k init, 0k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xe0800000 - 0xff3fe000   ( 491 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xdfff0000   ( 511 MB)
[    0.004000]       .init : 0xc04ab000 - 0xc0515000   ( 424 kB)
[    0.004000]       .data : 0xc038335a - 0xc04a5680   (1160 kB)
[    0.004000]       .text : 0xc0100000 - 0xc038335a   (2572 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=128, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004014] Calibrating delay loop (skipped), value calculated using timer frequency.. 3616.74 BogoMIPS (lpj=7233484)
[    0.004150] Security Framework initialized
[    0.004213] SELinux:  Disabled at boot.
[    0.004297] AppArmor: AppArmor initialized
[    0.004366] Mount-cache hash table entries: 512
[    0.004707] Initializing cgroup subsys ns
[    0.004766] Initializing cgroup subsys cpuacct
[    0.004823] Initializing cgroup subsys memory
[    0.004901] CPU: Trace cache: 12K uops, L1 D cache: 8K
[    0.004999] CPU: L2 cache: 512K
[    0.005053] CPU: Hyper-Threading is disabled
[    0.005125] Checking 'hlt' instruction... OK.
[    0.020862] SMP alternatives: switching to UP code
[    0.032030] Freeing SMP alternatives: 11k freed
[    0.032092] ACPI: Core revision 20080609
[    0.037269] ACPI: Checking initramfs for custom DSDT
[    0.596247] ENABLING IO-APIC IRQs
[    0.596496] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.636979] CPU0: Intel(R) Pentium(R) 4 CPU 1.80GHz stepping 04
[    0.640031] Brought up 1 CPUs
[    0.640031] Total of 1 processors activated (3616.74 BogoMIPS).
[    0.640031] CPU0 attaching sched-domain:
[    0.640031]  domain 0: span 0 level CPU
[    0.640031]   groups: 0
[    0.640031] net_namespace: 840 bytes
[    0.640031] Booting paravirtualized kernel on bare hardware
[    0.640031] Time: 21:10:15  Date: 12/04/08
[    0.640031] NET: Registered protocol family 16
[    0.640031] EISA bus registered
[    0.640031] ACPI: bus type pci registered
[    0.663012] PCI: PCI BIOS revision 2.10 entry at 0xfb070, last bus=2
[    0.663073] PCI: Using configuration type 1 for base access
[    0.665969] ACPI: EC: Look up EC in DSDT
[    0.677306] ACPI: Interpreter enabled
[    0.677366] ACPI: (supports S0 S1 S4 S5)
[    0.677595] ACPI: Using IOAPIC for interrupt routing
[    0.688344] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.688536] PCI: 0000:00:00.0 reg 10 32bit mmio: [d8000000, dbffffff]
[    0.688742] pci 0000:00:1f.0: quirk: region 4000-407f claimed by ICH4 ACPI/GPIO/TCO
[    0.688813] pci 0000:00:1f.0: quirk: region 4080-40bf claimed by ICH4 GPIO
[    0.688917] PCI: 0000:00:1f.1 reg 20 io port: [f000, f00f]
[    0.688987] PCI: 0000:00:1f.2 reg 20 io port: [d000, d01f]
[    0.689058] PCI: 0000:00:1f.3 reg 20 io port: [5000, 500f]
[    0.689125] PCI: 0000:00:1f.4 reg 20 io port: [d400, d41f]
[    0.689169] PCI: 0000:00:1f.5 reg 10 io port: [d800, d8ff]
[    0.689179] PCI: 0000:00:1f.5 reg 14 io port: [dc00, dc3f]
[    0.689264] PCI: 0000:01:00.0 reg 10 32bit mmio: [dc000000, dcffffff]
[    0.689274] PCI: 0000:01:00.0 reg 14 32bit mmio: [d0000000, d7ffffff]
[    0.689301] PCI: 0000:01:00.0 reg 30 32bit mmio: [0, ffff]
[    0.689363] PCI: bridge 0000:00:01.0 32bit mmio: [dc000000, ddffffff]
[    0.689370] PCI: bridge 0000:00:01.0 32bit mmio pref: [d0000000, d7ffffff]
[    0.689422] PCI: 0000:02:01.0 reg 10 32bit mmio: [de000000, de00ffff]
[    0.689434] PCI: 0000:02:01.0 reg 14 32bit mmio: [de010000, de01ffff]
[    0.689520] PCI: 0000:02:02.0 reg 10 32bit mmio: [de020000, de020fff]
[    0.689572] pci 0000:02:02.0: supports D1
[    0.689575] pci 0000:02:02.0: supports D2
[    0.689579] pci 0000:02:02.0: PME# supported from D0 D1 D2 D3hot
[    0.689640] pci 0000:02:02.0: PME# disabled
[    0.689728] PCI: 0000:02:02.1 reg 10 32bit mmio: [de021000, de021fff]
[    0.689780] pci 0000:02:02.1: supports D1
[    0.689783] pci 0000:02:02.1: supports D2
[    0.689787] pci 0000:02:02.1: PME# supported from D0 D1 D2 D3hot
[    0.689846] pci 0000:02:02.1: PME# disabled
[    0.689932] PCI: 0000:02:02.2 reg 10 32bit mmio: [de022000, de0220ff]
[    0.689984] pci 0000:02:02.2: supports D1
[    0.689987] pci 0000:02:02.2: supports D2
[    0.689990] pci 0000:02:02.2: PME# supported from D0 D1 D2 D3hot
[    0.690049] pci 0000:02:02.2: PME# disabled
[    0.690154] pci 0000:00:1e.0: transparent bridge
[    0.690214] PCI: bridge 0000:00:1e.0 32bit mmio: [de000000, de0fffff]
[    0.690234] bus 00 -> node 0
[    0.690250] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.690682] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.720745] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.721506] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.722259] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.723017] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 12 14 15) *9
[    0.723821] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.724646] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.725488] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.726332] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11 *12 14 15)
[    0.727183] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.727313] pnp: PnP ACPI init
[    0.727381] ACPI: bus type pnp registered
[    0.735971] pnp: PnP ACPI: found 15 devices
[    0.736037] ACPI: ACPI bus type pnp unregistered
[    0.736096] PnPBIOS: Disabled by ACPI PNP
[    0.736878] PCI: Using ACPI for IRQ routing
[    0.737129] NET: Registered protocol family 8
[    0.737129] NET: Registered protocol family 20
[    0.737129] NetLabel: Initializing
[    0.737129] NetLabel:  domain hash size = 128
[    0.737129] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.737129] NetLabel:  unlabeled traffic allowed by default
[    0.737129] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.737129]    actual entries 65620
[    0.737309] AppArmor: AppArmor Filesystem Enabled
[    0.737390] ACPI: RTC can wake from S4
[    0.737460] system 00:00: iomem range 0xf0000-0xf3fff could not be reserved
[    0.737460] system 00:00: iomem range 0xf4000-0xf7fff could not be reserved
[    0.737460] system 00:00: iomem range 0xf8000-0xfbfff could not be reserved
[    0.737460] system 00:00: iomem range 0xfc000-0xfffff could not be reserved
[    0.737460] system 00:00: iomem range 0x1fff0000-0x1fffffff could not be reserved
[    0.737460] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.737460] system 00:00: iomem range 0x100000-0x1ffeffff could not be reserved
[    0.737460] system 00:00: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.737460] system 00:00: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.737460] system 00:00: iomem range 0xffb00000-0xffb7ffff could not be reserved
[    0.737460] system 00:00: iomem range 0xfff00000-0xffffffff could not be reserved
[    0.737460] system 00:00: iomem range 0xe0000-0xeffff has been reserved
[    0.737460] system 00:03: ioport range 0xa78-0xa7b has been reserved
[    0.737460] system 00:03: ioport range 0xb78-0xb7b has been reserved
[    0.737460] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
[    0.737460] system 00:03: ioport range 0x290-0x29f has been reserved
[    0.775298] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.775360] pci 0000:00:01.0:   IO window: disabled
[    0.775419] pci 0000:00:01.0:   MEM window: 0xdc000000-0xddffffff
[    0.775478] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000d7ffffff
[    0.775549] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.775605] pci 0000:00:1e.0:   IO window: disabled
[    0.775664] pci 0000:00:1e.0:   MEM window: 0xde000000-0xde0fffff
[    0.776562] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.776640] pci 0000:00:1e.0: setting latency timer to 64
[    0.776648] bus: 00 index 0 io port: [0, ffff]
[    0.776702] bus: 00 index 1 mmio: [0, ffffffff]
[    0.776756] bus: 01 index 0 mmio: [0, 0]
[    0.776809] bus: 01 index 1 mmio: [dc000000, ddffffff]
[    0.776864] bus: 01 index 2 mmio: [d0000000, d7ffffff]
[    0.776918] bus: 01 index 3 mmio: [0, 0]
[    0.776971] bus: 02 index 0 mmio: [0, 0]
[    0.777024] bus: 02 index 1 mmio: [de000000, de0fffff]
[    0.777078] bus: 02 index 2 mmio: [0, 0]
[    0.777131] bus: 02 index 3 io port: [0, ffff]
[    0.777184] bus: 02 index 4 mmio: [0, ffffffff]
[    0.777255] NET: Registered protocol family 2
[    0.777558] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.778024] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.778183] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.778330] TCP: Hash tables configured (established 16384 bind 16384)
[    0.778388] TCP reno registered
[    0.778591] NET: Registered protocol family 1
[    0.778852] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[    1.323922]  it is
[    1.923028] Freeing initrd memory: 8004k freed
[    1.924322] audit: initializing netlink socket (disabled)
[    1.924404] type=2000 audit(1228425015.924:1): initialized
[    1.932045] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.936889] VFS: Disk quotas dquot_6.5.1
[    1.937138] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.937384] msgmni has been set to 1003
[    1.937683] io scheduler noop registered
[    1.937739] io scheduler anticipatory registered
[    1.937794] io scheduler deadline registered
[    1.937874] io scheduler cfq registered (default)
[    1.938004] pci 0000:01:00.0: Boot video device
[    1.938703] isapnp: Scanning for PnP cards...
[    2.292787] isapnp: No Plug & Play device found
[    2.376826] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.377071] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.377423] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    2.378755] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.379459] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    2.383123] brd: module loaded
[    2.383319] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    2.383629] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    2.383688] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    2.384369] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.385327] mice: PS/2 mouse device common for all mice
[    2.385693] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    2.385779] rtc0: alarms up to one month
[    2.386092] EISA: Probing bus 0 at eisa.0
[    2.386168] Cannot allocate resource for EISA slot 4
[    2.386223] Cannot allocate resource for EISA slot 5
[    2.386291] EISA: Detected 0 cards.
[    2.386345] cpuidle: using governor ladder
[    2.386400] cpuidle: using governor menu
[    2.387422] TCP cubic registered
[    2.387531] Using IPI No-Shortcut mode
[    2.388101] registered taskstats version 1
[    2.388324]   Magic number: 4:182:196
[    2.388436] tty ttys8: hash matches
[    2.388499] tty ttypb: hash matches
[    2.388678] rtc_cmos 00:05: setting system clock to 2008-12-04 21:10:17 UTC (1228425017)
[    2.388746] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.388802] EDD information not available.
[    2.389427] Freeing unused kernel memory: 424k freed
[    2.389567] Write protecting the kernel text: 2576k
[    2.389669] Write protecting the kernel read-only data: 936k
[    2.412698] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.575369] fuse init (API version 7.9)
[    2.606758] fan PNP0C0B:00: registered as cooling_device0
[    2.606830] ACPI: Fan [FAN] (on)
[    2.622118] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    2.622390] processor ACPI0007:00: registered as cooling_device1
[    2.622453] ACPI: Processor [CPU0] (supports 2 throttling states)
[    2.628498] thermal LNXTHERM:01: registered as thermal_zone0
[    2.629990] ACPI: Thermal Zone [THRM] (38 C)
[    3.471594] No dock devices found.
[    3.617356] SCSI subsystem initialized
[    3.693743] usbcore: registered new interface driver usbfs
[    3.693850] usbcore: registered new interface driver hub
[    3.704813] usbcore: registered new device driver usb
[    3.731262] USB Universal Host Controller Interface driver v3.0
[    3.731410] uhci_hcd 0000:00:1f.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    3.731481] uhci_hcd 0000:00:1f.2: setting latency timer to 64
[    3.731487] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[    3.731619] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[    3.731725] uhci_hcd 0000:00:1f.2: irq 19, io base 0x0000d000
[    3.732105] usb usb1: configuration #1 chosen from 1 choice
[    3.732216] hub 1-0:1.0: USB hub found
[    3.732283] hub 1-0:1.0: 2 ports detected
[    3.746798] libata version 3.00 loaded.
[    3.748162] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.940552] uhci_hcd 0000:00:1f.4: PCI INT C -> GSI 23 (level, low) -> IRQ 23
[    3.940630] uhci_hcd 0000:00:1f.4: setting latency timer to 64
[    3.940636] uhci_hcd 0000:00:1f.4: UHCI Host Controller
[    3.940741] uhci_hcd 0000:00:1f.4: new USB bus registered, assigned bus number 2
[    3.940847] uhci_hcd 0000:00:1f.4: irq 23, io base 0x0000d400
[    3.941119] usb usb2: configuration #1 chosen from 1 choice
[    3.941227] hub 2-0:1.0: USB hub found
[    3.941296] hub 2-0:1.0: 2 ports detected
[    4.044535] ata_piix 0000:00:1f.1: version 2.12
[    4.044615] ata_piix 0000:00:1f.1: setting latency timer to 64
[    4.045885] scsi0 : ata_piix
[    4.046152] scsi1 : ata_piix
[    4.047864] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    4.047925] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    4.052066] usb 1-1: new low speed USB device using uhci_hcd and address 2
[    4.220897] ata1.00: ATA-4: ST328040A, 3.07, max UDMA/66
[    4.220963] ata1.00: 55704096 sectors, multi 16: LBA 
[    4.221222] ata1.01: ATA-5: MAXTOR 6L040J2, AR1.0400, max UDMA/133
[    4.221282] ata1.01: 78177792 sectors, multi 16: LBA 
[    4.226128] usb 1-1: configuration #1 chosen from 1 choice
[    4.236310] ata1.00: configured for UDMA/66
[    4.252527] ata1.01: configured for UDMA/100
[    4.416406] ata2.00: ATAPI: LITEON  DVD-ROM LTD122, IL6J, max UDMA/33
[    4.424358] ata2.00: configured for UDMA/33
[    4.424620] scsi 0:0:0:0: Direct-Access     ATA      ST328040A        3.07 PQ: 0 ANSI: 5
[    4.424935] scsi 0:0:1:0: Direct-Access     ATA      MAXTOR 6L040J2   AR1. PQ: 0 ANSI: 5
[    4.425516] scsi 1:0:0:0: CD-ROM            LITEON   DVD-ROM LTD122   IL6J PQ: 0 ANSI: 5
[    4.425845] ehci_hcd 0000:02:02.2: PCI INT C -> GSI 16 (level, low) -> IRQ 16
[    4.425924] ehci_hcd 0000:02:02.2: EHCI Host Controller
[    4.426032] ehci_hcd 0000:02:02.2: new USB bus registered, assigned bus number 3
[    4.448123] ehci_hcd 0000:02:02.2: irq 16, io mem 0xde022000
[    4.460046] ehci_hcd 0000:02:02.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.460404] usb usb3: configuration #1 chosen from 1 choice
[    4.460512] hub 3-0:1.0: USB hub found
[    4.460579] hub 3-0:1.0: 5 ports detected
[    4.564495] ohci_hcd 0000:02:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    4.564581] ohci_hcd 0000:02:02.0: OHCI Host Controller
[    4.564700] ohci_hcd 0000:02:02.0: new USB bus registered, assigned bus number 4
[    4.564797] ohci_hcd 0000:02:02.0: irq 18, io mem 0xde020000
[    4.654356] usb usb4: configuration #1 chosen from 1 choice
[    4.654471] hub 4-0:1.0: USB hub found
[    4.654540] hub 4-0:1.0: 3 ports detected
[    4.756478] ohci_hcd 0000:02:02.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    4.756563] ohci_hcd 0000:02:02.1: OHCI Host Controller
[    4.756671] ohci_hcd 0000:02:02.1: new USB bus registered, assigned bus number 5
[    4.756761] ohci_hcd 0000:02:02.1: irq 19, io mem 0xde021000
[    4.865847] usbcore: registered new interface driver hiddev
[    4.866214] usb usb5: configuration #1 chosen from 1 choice
[    4.866321] hub 5-0:1.0: USB hub found
[    4.866390] hub 5-0:1.0: 2 ports detected
[    4.881439] input: Dell Dell USB Mouse as /devices/pci0000:00/0000:00:1f.2/usb1/1-1/1-1:1.0/input/input2
[    4.882202] input,hidraw0: USB HID v1.10 Mouse [Dell Dell USB Mouse] on usb-0000:00:1f.2-1
[    4.882464] usbcore: registered new interface driver usbhid
[    4.882524] usbhid: v2.6:USB HID core driver
[    4.907954] Marking TSC unstable due to TSC halts in idle
[    5.005562] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    5.005699] scsi 0:0:1:0: Attached scsi generic sg1 type 0
[    5.005832] scsi 1:0:0:0: Attached scsi generic sg2 type 5
[    5.088949] Driver 'sd' needs updating - please use bus_type methods
[    5.094454] sd 0:0:0:0: [sda] 55704096 512-byte hardware sectors (28520 MB)
[    5.094558] sd 0:0:0:0: [sda] Write Protect is off
[    5.094615] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.094685] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.094914] sd 0:0:0:0: [sda] 55704096 512-byte hardware sectors (28520 MB)
[    5.095008] sd 0:0:0:0: [sda] Write Protect is off
[    5.095065] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.095132] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.095204]  sda: sda1
[    5.108856] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.109090] sd 0:0:1:0: [sdb] 78177792 512-byte hardware sectors (40027 MB)
[    5.110024] sd 0:0:1:0: [sdb] Write Protect is off
[    5.110080] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    5.110159] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.110368] sd 0:0:1:0: [sdb] 78177792 512-byte hardware sectors (40027 MB)
[    5.110466] sd 0:0:1:0: [sdb] Write Protect is off
[    5.110523] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    5.110600] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.110672]  sdb:<4>Driver 'sr' needs updating - please use bus_type methods
[    5.122467]  sdb1 sdb2 < sdb5 >
[    5.141409] sd 0:0:1:0: [sdb] Attached SCSI disk
[    5.152351] sr0: scsi3-mmc drive: 0x/40x cd/rw xa/form2 cdda tray
[    5.152419] Uniform CD-ROM driver Revision: 3.20
[    5.152663] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    5.606838] PM: Starting manual resume from disk
[    5.606898] PM: Resume from partition 8:21
[    5.606901] PM: Checking hibernation image.
[    5.607266] PM: Resume from disk failed.
[    5.667889] EXT3-fs: INFO: recovery required on readonly filesystem.
[    5.667956] EXT3-fs: write access will be enabled during recovery.
[    5.761371] kjournald starting.  Commit interval 5 seconds
[    5.761457] EXT3-fs: recovery complete.
[    5.762355] EXT3-fs: mounted filesystem with ordered data mode.
[   12.026591] udevd version 124 started
[   13.008203] Linux agpgart interface v0.103
[   13.130789] agpgart-intel 0000:00:00.0: Intel i850 Chipset
[   13.140655] agpgart-intel 0000:00:00.0: AGP aperture is 64M @ 0xd8000000
[   13.182404] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   13.253140] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.314012] intel_rng: FWH not detected
[   13.449692] iTCO_vendor_support: vendor-support=0
[   13.506097] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   13.509065] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[   13.509153] iTCO_wdt: No card detected
[   13.986174] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[   13.996267] ACPI: Power Button (FF) [PWRF]
[   13.996554] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
[   14.012061] ACPI: Power Button (CM) [PWRB]
[   14.012339] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input5
[   14.028060] ACPI: Sleep Button (CM) [SLPB]
[   14.209439] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   14.426345] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   14.852484] ndiswrapper: driver mrv8k51 (PLANET Technology Corp.,01/19/2004,2.3.0.3) loaded
[   14.852962] ndiswrapper 0000:02:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   14.853889] ndiswrapper: using IRQ 17
[   15.240743] wlan0: ethernet device xx:xx:xx:xx:xx:xx using NDIS driver: mrv8k51, version: 0x2030001, NDIS version: 0x501, vendor: 'Marvell 802.11 Driver', 11AB:1FA6.5.conf
[   15.240851] ndiswrapper (set_iw_encr_mode:708): setting encryption mode to 6 failed (C00000BB)
[   15.240925] wlan0: encryption modes supported: WEP; TKIP with WPA
[   15.241133] usbcore: registered new interface driver ndiswrapper
[   15.472378] parport_pc 00:0b: reported by Plug and Play ACPI
[   15.472540] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   16.250441] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   16.250531] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   16.572057] intel8x0_measure_ac97_clock: measured 55255 usecs
[   16.572122] intel8x0: clocking to 48000
[   21.018640] lp0: using parport0 (interrupt-driven).
[   21.232170] Adding 1502036k swap on /dev/sdb5.  Priority:-1 extents:1 across:1502036k
[   21.655034] EXT3 FS on sdb1, internal journal
[   22.496118] type=1505 audit(1228443037.638:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=3927
[   22.797392] type=1505 audit(1228443037.938:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3932
[   22.797759] type=1505 audit(1228443037.938:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3932
[   22.938771] ip_tables: (C) 2000-2006 Netfilter Core Team

```

---

### Post by earle79 on 2008-12-16
Hey did you get this issue fixed, having very similar issue, with dlink card.

---

### Post by noead01 on 2008-12-17
Unfortunately, no solution yet.
Looking at the output from dmesg, it looks like the IRQ 17 is used by 2 different drivers. But I don't know if that would be the cause of the problem, let alone how to fix it.

If you do find a solution, please let me know.

---

### Post by cdtech on 2008-12-17
It looks as though you have two instances of ndiswrapper running. If you use more than one driver this will cause a lock up. Do you or did you have a USB wireless device connected at one time?

When you go into the recovery mode and disable the "ndiswrapper -r mrv8k51" driver, check "ndiswrapper -l" and see if any other drivers are loaded.

---

### Post by noead01 on 2008-12-18
Thanks for your reply.

No I never had any USB wireless device connected.
Once I boot in recovery mode, remove the driver with ndiswrapper -r, and then reboot again, I am able to log in normally.

Then, when I run ndis-gtk, it shows there are no drivers installed (the list is empty). I can then add the mrv8k51 to ndis-gtk, and then connect to the wireless network without any problems, until the next reboot, where I have to perform the same maneuver again.

---

### Post by Rick_ hen on 2009-01-03
I have the exact same problem, when i add my driver with ndis-gtk it all works. I tested logging in and out a few times, but that all worked. Until i restarted my pc. Then when i log in the system hangs. I then did ctrl-alt-backspace which returned me to the login screen. After that i was able to log in normally, but pulseaudio was down from the start, nautilus kept crashing etc. the only thing that didnt crash was the terminal, so i manually removed the file from /etc/ndiswrapper and after a reboot the pc would work normally again. 
I did once have an usb-wireless card attached, but it didn't work. I have a dual boot system so i tested it in windows after failing to install it under Linux Mint 6 and it didn't work there either so i returned it to the shop. But i only just removed the driver i found for that.
I am looking forward to a solution because it sucks having to roll a cable to my pc all the time. By the way, i am using an Asus Wl-138g with a marvell chipset on a dell gx270 running linux mint 6.
lspci says: 
01:0a.0 Ethernet controller: Marvell Technology Group Ltd. Marvell W8300 802.11 Adapter (rev 07)

---

### Post by Rick_ hen on 2009-01-03
this is my output of dmesg right after installing the driver. i only selected the last few lines.

[ 2938.401519] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[ 2938.465497] ndiswrapper: driver mrv8k51 (D-Link,1/09/2004,2.3.0.1) loaded
[ 2938.466363] ndiswrapper 0000:01:0a.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[ 2938.467044] ndiswrapper: using IRQ 19
[ 2938.737871] wlan0: ethernet device 00:11:2f:50:a0:59 using NDIS driver: mrv8k51, version: 0x2030001, NDIS version: 0x501, vendor: 'Marvell 802.11 Driver', 11AB:1FA6.5.conf
[ 2938.738418] ndiswrapper (set_iw_encr_mode:715): setting encryption mode to 6 failed (C00000BB)
[ 2938.738693] wlan0: encryption modes supported: WEP; TKIP with WPA
[ 2938.738988] usbcore: registered new interface driver ndiswrapper
[ 2944.937190] ndiswrapper (set_essid:59): setting essid failed (C0000001)
[ 2946.256435] ndiswrapper (set_essid:59): setting essid failed (C0000001)

---

### Post by Rick_ hen on 2009-01-03
This is the output of dmesg right after reboot (****** up system)
```

[   20.471745] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   20.912737] ndiswrapper: driver mrv8k51 (D-Link,1/09/2004,2.3.0.1) loaded
[   20.913026] ndiswrapper 0000:01:0a.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   20.913588] ndiswrapper: using IRQ 19
[   21.118313] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   21.204546] wlan0: ethernet device 00:11:2f:50:a0:59 using NDIS driver: mrv8k51, version: 0x2030001, NDIS version: 0x501, vendor: 'Marvell 802.11 Driver', 11AB:1FA6.5.conf
[   21.204563] ndiswrapper (set_iw_encr_mode:715): setting encryption mode to 6 failed (C00000BB)
[   21.204580] wlan0: encryption modes supported: WEP; TKIP with WPA
```
This is what i did in the command line
```

rick@RickPC ~/Desktop $ ndiswrapper -l
mrv8k51 : driver installed
	device (11AB:1FA6) present
rick@RickPC ~/Desktop $ ndiswrapper
install/manage Windows drivers for ndiswrapper

usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid' (dangerous)
-r driver        remove 'driver'
-l               list installed drivers
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information

where 'devid' is either PCIID or USBID of the form XXXX:XXXX,
as reported by 'lspci -n' or 'lsusb' for the card
rick@RickPC ~/Desktop $ ndiswrapper -r mrv8k51
cannot unlink file for /etc/ndiswrapper/mrv8k51/11AB:1FA6.5.conf: Permission denied at /usr/sbin/ndiswrapper-1.9 line 126
cannot restore permissions to 0120777 for /etc/ndiswrapper/mrv8k51/11AB:1FA6.5.conf: Bad file descriptor at /usr/sbin/ndiswrapper-1.9 line 126
couldn't delete /etc/ndiswrapper/mrv8k51: Bad file descriptor
rick@RickPC ~/Desktop $ sudo ndiswrapper -r mrv8k51
^C^C^C^C^Cqqq^C^C^C^[^[^[
// sudo must have failed as well, at least this terminal window is dead

// After opening a new terminal :

rick@RickPC ~/Desktop $ su
Password: 
RickPC Desktop # ndiswrapper -r mrv8k51
RickPC Desktop # ndiswrapper -l
RickPC Desktop #
```
I solved it, my (temporary)solution is on page 2

---

### Post by Rick_ hen on 2009-01-03
I found a solution!:D

It is not a great solution, but it works...
open a gedit window, and insert this text:
```

sudo ndiswrapper -r mrv8k51
sudo shutdown -P 0
```

then open a command line and use ```
chmod 755 shutdownscriptfilename
```
then right click on the desktop and click "create launcher". Click browse and select your script. Now when you want to shut down your computer ALWAYS use THIS link! That way you will be able to start your pc again normally. 
You do however have to use ndis-gtk every time you restart your computer to have wireless internet. This is a temporary solution, so it is not perfect but it works for me.:)

---

### Post by noead01 on 2009-01-04
I am starting to suspect that NetworkManager might be the root cause.
I will attempt a few things by creating the network config files manually and disbling NetworkManager altogether and keep you posted.

---

### Post by Rick_ hen on 2009-01-05
Can you even connect to a hidden wireless network without the network manager?:confused:

---

### Post by noead01 on 2009-01-05
I have never done it, but I would think it is possible to configure the /etc/network/interfaces file manually if you know the SSID of the wireless network, and bypass networkmanager completely.

When I find the time, I will give it a shot.

---

