---
title: "madwifi signal low!!!!"
date: 2008-11-14
forum: Networking &amp; Wireless
---

### Post by markg48 on 2008-11-14
is there any way to boost madwifi singal its getting very low even though im not that far away im using atheros 5007 wireless card

---

### Post by markg48 on 2008-11-14
singal 50 percent should be  atleast 80

---

### Post by joffe on 2008-11-14
Please post the output of dmesg

---

### Post by markg48 on 2008-11-14
sorry to be a pain but how do i do that ?

---

### Post by joffe on 2008-11-14
open up a terminal and run the command
```
dmesg
```

---

### Post by markg48 on 2008-11-14
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257308
[    0.000000] Kernel command line: root=UUID=7288D52E88D4F199 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 1994.959 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 1014820k/1038824k available (2572k kernel code, 23192k reserved, 1160k data, 424k init, 121248k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.004000]       .init : 0xc04ab000 - 0xc0515000   ( 424 kB)
[    0.004000]       .data : 0xc038329a - 0xc04a5680   (1160 kB)
[    0.004000]       .text : 0xc0100000 - 0xc038329a   (2572 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3989.91 BogoMIPS (lpj=7979836)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 1024K
[    0.004000] using mwait in idle threads.
[    0.004000] Checking 'hlt' instruction... OK.
[    0.016496] SMP alternatives: switching to UP code
[    0.021596] ACPI: Core revision 20080609
[    0.024943] ACPI: Checking initramfs for custom DSDT
[    0.376264] ENABLING IO-APIC IRQs
[    0.376455] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.416322] CPU0: Intel(R) Celeron(R) CPU          550  @ 2.00GHz stepping 01
[    0.420026] Brought up 1 CPUs
[    0.420026] Total of 1 processors activated (3989.91 BogoMIPS).
[    0.420026] CPU0 attaching sched-domain:
[    0.420026]  domain 0: span 0 level CPU
[    0.420026]   groups: 0
[    0.420026] net_namespace: 840 bytes
[    0.420026] Booting paravirtualized kernel on bare hardware
[    0.420026] Time:  3:59:52  Date: 11/14/08
[    0.420026] NET: Registered protocol family 16
[    0.420026] EISA bus registered
[    0.420026] ACPI: bus type pci registered
[    0.420026] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.420026] PCI: MCFG area at e0000000 reserved in E820
[    0.420026] PCI: Using MMCONFIG for extended config space
[    0.420026] PCI: Using configuration type 1 for base access
[    0.420026] ACPI: EC: Look up EC in DSDT
[    0.442781] ACPI: BIOS _OSI(Linux) query ignored via DMI
[    0.444266] ACPI: Interpreter enabled
[    0.444269] ACPI: (supports S0 S3 S4 S5)
[    0.444286] ACPI: Using IOAPIC for interrupt routing
[    0.444598] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.624391] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[    0.624394] ACPI: EC: driver started in interrupt mode
[    0.624448] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.624565] PCI: 0000:00:02.0 reg 10 64bit mmio: [51000000, 510fffff]
[    0.624570] PCI: 0000:00:02.0 reg 18 32bit mmio: [40000000, 4fffffff]
[    0.624578] PCI: 0000:00:02.0 reg 20 io port: [30b0, 30b7]
[    0.624615] PCI: 0000:00:02.1 reg 10 64bit mmio: [51100000, 511fffff]
[    0.624738] PCI: 0000:00:1b.0 reg 10 64bit mmio: [52400000, 52403fff]
[    0.624795] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.624800] pci 0000:00:1b.0: PME# disabled
[    0.624877] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.624881] pci 0000:00:1c.0: PME# disabled
[    0.624941] PCI: 0000:00:1d.0 reg 20 io port: [3060, 307f]
[    0.625008] PCI: 0000:00:1d.1 reg 20 io port: [3040, 305f]
[    0.625075] PCI: 0000:00:1d.2 reg 20 io port: [3020, 303f]
[    0.625149] PCI: 0000:00:1d.7 reg 10 32bit mmio: [52404000, 524043ff]
[    0.625210] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.625215] pci 0000:00:1d.7: PME# disabled
[    0.625384] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[    0.625389] pci 0000:00:1f.0: quirk: region 0500-053f claimed by ICH6 GPIO
[    0.625436] PCI: 0000:00:1f.2 reg 10 io port: [30a8, 30af]
[    0.625444] PCI: 0000:00:1f.2 reg 14 io port: [30bc, 30bf]
[    0.625452] PCI: 0000:00:1f.2 reg 18 io port: [30a0, 30a7]
[    0.625461] PCI: 0000:00:1f.2 reg 1c io port: [30b8, 30bb]
[    0.625469] PCI: 0000:00:1f.2 reg 20 io port: [3090, 309f]
[    0.625477] PCI: 0000:00:1f.2 reg 24 io port: [3080, 308f]
[    0.625504] pci 0000:00:1f.2: PME# supported from D3hot
[    0.625509] pci 0000:00:1f.2: PME# disabled
[    0.625531] PCI: 0000:00:1f.3 reg 10 32bit mmio: [52404400, 524044ff]
[    0.625558] PCI: 0000:00:1f.3 reg 20 io port: [3000, 301f]
[    0.625659] PCI: 0000:01:00.0 reg 10 64bit mmio: [51300000, 5130ffff]
[    0.625796] PCI: bridge 0000:00:1c.0 io port: [2000, 2fff]
[    0.625802] PCI: bridge 0000:00:1c.0 32bit mmio: [51300000, 523fffff]
[    0.625810] PCI: bridge 0000:00:1c.0 64bit mmio pref: [50000000, 50ffffff]
[    0.625862] PCI: 0000:02:01.0 reg 10 io port: [1000, 10ff]
[    0.625871] PCI: 0000:02:01.0 reg 14 32bit mmio: [51200000, 512000ff]
[    0.625930] pci 0000:02:01.0: supports D1
[    0.625932] pci 0000:02:01.0: supports D2
[    0.625933] pci 0000:02:01.0: PME# supported from D1 D2 D3hot D3cold
[    0.625939] pci 0000:02:01.0: PME# disabled
[    0.625999] pci 0000:00:1e.0: transparent bridge
[    0.626005] PCI: bridge 0000:00:1e.0 io port: [1000, 1fff]
[    0.626010] PCI: bridge 0000:00:1e.0 32bit mmio: [51200000, 512fffff]
[    0.626033] bus 00 -> node 0
[    0.626041] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.626514] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
[    0.626645] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[    0.632999] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[    0.633143] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 *10 11 12)
[    0.633283] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
[    0.633423] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
[    0.633562] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 *11 12)
[    0.633701] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 *11 12)
[    0.633840] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 *11 12)
[    0.633979] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 *11 12)
[    0.634394] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.634427] pnp: PnP ACPI init
[    0.634434] ACPI: bus type pnp registered
[    0.693165] pnp 00:01: io resource (0x164e-0x164f) overlaps 0000:00:1e.0 BAR 7 (0x1000-0x1fff), disabling
[    0.694018] pnp: PnP ACPI: found 9 devices
[    0.694021] ACPI: ACPI bus type pnp unregistered
[    0.694025] PnPBIOS: Disabled by ACPI PNP
[    0.694354] PCI: Using ACPI for IRQ routing
[    0.694469] NET: Registered protocol family 8
[    0.694469] NET: Registered protocol family 20
[    0.694469] NetLabel: Initializing
[    0.694469] NetLabel:  domain hash size = 128
[    0.694469] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.694469] NetLabel:  unlabeled traffic allowed by default
[    0.694469] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.694469] hpet0: 3 64-bit timers, 14318180 Hz
[    0.694469] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.694469]    actual entries 65620
[    0.696044] Switched to high resolution mode on CPU 0
[    0.696121] AppArmor: AppArmor Filesystem Enabled
[    0.696151] ACPI: RTC can wake from S4
[    0.696195] system 00:01: ioport range 0x600-0x60f has been reserved
[    0.696199] system 00:01: ioport range 0x610-0x610 has been reserved
[    0.696201] system 00:01: ioport range 0x800-0x80f has been reserved
[    0.696204] system 00:01: ioport range 0x810-0x817 has been reserved
[    0.696207] system 00:01: ioport range 0x400-0x47f has been reserved
[    0.696209] system 00:01: ioport range 0x500-0x53f has been reserved
[    0.696212] system 00:01: ioport range 0xff2c-0xff2f has been reserved
[    0.696216] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[    0.696219] system 00:01: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[    0.696222] system 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
[    0.696224] system 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
[    0.696227] system 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
[    0.696230] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.696233] system 00:01: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.731284] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01
[    0.731288] pci 0000:00:1c.0:   IO window: 0x2000-0x2fff
[    0.731295] pci 0000:00:1c.0:   MEM window: 0x51300000-0x523fffff
[    0.731301] pci 0000:00:1c.0:   PREFETCH window: 0x00000050000000-0x00000050ffffff
[    0.731310] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.731313] pci 0000:00:1e.0:   IO window: 0x1000-0x1fff
[    0.731320] pci 0000:00:1e.0:   MEM window: 0x51200000-0x512fffff
[    0.731325] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.731346] pci 0000:00:1c.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.731352] pci 0000:00:1c.0: setting latency timer to 64
[    0.731362] pci 0000:00:1e.0: setting latency timer to 64
[    0.731366] bus: 00 index 0 io port: [0, ffff]
[    0.731368] bus: 00 index 1 mmio: [0, ffffffff]
[    0.731370] bus: 01 index 0 io port: [2000, 2fff]
[    0.731371] bus: 01 index 1 mmio: [51300000, 523fffff]
[    0.731373] bus: 01 index 2 mmio: [50000000, 50ffffff]
[    0.731375] bus: 01 index 3 mmio: [0, 0]
[    0.731377] bus: 02 index 0 io port: [1000, 1fff]
[    0.731379] bus: 02 index 1 mmio: [51200000, 512fffff]
[    0.731380] bus: 02 index 2 mmio: [0, 0]
[    0.731382] bus: 02 index 3 io port: [0, ffff]
[    0.731384] bus: 02 index 4 mmio: [0, ffffffff]
[    0.731393] NET: Registered protocol family 2
[    0.731519] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.731758] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.732343] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.732702] TCP: Hash tables configured (established 131072 bind 65536)
[    0.732706] TCP reno registered
[    0.732874] NET: Registered protocol family 1
[    0.732997] checking if image is initramfs... it is
[    1.445394] Freeing initrd memory: 8236k freed
[    1.445595] Simple Boot Flag value 0x5 read from CMOS RAM was invalid
[    1.445598] Simple Boot Flag at 0x44 set to 0x1
[    1.446184] audit: initializing netlink socket (disabled)
[    1.446205] type=2000 audit(1226635193.444:1): initialized
[    1.452072] highmem bounce pool size: 64 pages
[    1.452078] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.454149] VFS: Disk quotas dquot_6.5.1
[    1.454229] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.454325] msgmni has been set to 1762
[    1.454432] io scheduler noop registered
[    1.454435] io scheduler anticipatory registered
[    1.454437] io scheduler deadline registered
[    1.454448] io scheduler cfq registered (default)
[    1.454464] pci 0000:00:02.0: Boot video device
[    1.454733] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.454786] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.454840] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.454882] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.454918] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.455227] isapnp: Scanning for PnP cards...
[    1.809318] isapnp: No Plug & Play device found
[    1.842144] hpet_resources: 0xfed00000 is busy
[    1.842217] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.844339] brd: module loaded
[    1.844405] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.844522] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    1.880994] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.881000] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.881311] mice: PS/2 mouse device common for all mice
[    1.882122] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.882158] rtc0: alarms up to one month, hpet irqs
[    1.882269] EISA: Probing bus 0 at eisa.0
[    1.882277] Cannot allocate resource for EISA slot 1
[    1.882279] Cannot allocate resource for EISA slot 2
[    1.882281] Cannot allocate resource for EISA slot 3
[    1.882302] EISA: Detected 0 cards.
[    1.882305] cpuidle: using governor ladder
[    1.882308] cpuidle: using governor menu
[    1.882722] TCP cubic registered
[    1.882751] Using IPI No-Shortcut mode
[    1.882938] registered taskstats version 1
[    1.883032]   Magic number: 0:839:967
[    1.883051] tty ttyb8: hash matches
[    1.883178] rtc_cmos 00:03: setting system clock to 2008-11-14 03:59:54 UTC (1226635194)
[    1.883181] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.883183] EDD information not available.
[    1.883426] Freeing unused kernel memory: 424k freed
[    1.883461] Write protecting the kernel text: 2576k
[    1.883490] Write protecting the kernel read-only data: 936k
[    1.902777] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.062110] fuse init (API version 7.9)
[    2.333254] Monitor-Mwait will be used to enter C-1 state
[    2.333258] Monitor-Mwait will be used to enter C-2 state
[    2.333261] Monitor-Mwait will be used to enter C-3 state
[    2.336741] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    2.336795] processor ACPI0007:00: registered as cooling_device0
[    2.336799] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.340405] Marking TSC unstable due to TSC halts in idle
[    2.343765] thermal LNXTHERM:01: registered as thermal_zone0
[    2.357547] ACPI: Thermal Zone [TZ01] (55 C)
[    2.850224] usbcore: registered new interface driver usbfs
[    2.850249] usbcore: registered new interface driver hub
[    2.850561] usbcore: registered new device driver usb
[    2.853023] USB Universal Host Controller Interface driver v3.0
[    2.853079] uhci_hcd 0000:00:1d.0: PCI INT D -> GSI 21 (level, low) -> IRQ 21
[    2.853088] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.853093] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.853133] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    2.853171] uhci_hcd 0000:00:1d.0: irq 21, io base 0x00003060
[    2.853311] usb usb1: configuration #1 chosen from 1 choice
[    2.853340] hub 1-0:1.0: USB hub found
[    2.853348] hub 1-0:1.0: 2 ports detected
[    2.924230] 8139too Fast Ethernet driver 0.9.28
[    2.937973] No dock devices found.
[    2.986522] SCSI subsystem initialized
[    3.026762] libata version 3.00 loaded.
[    3.060336] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    3.060346] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.060351] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.060374] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    3.060418] uhci_hcd 0000:00:1d.1: irq 20, io base 0x00003040
[    3.060511] usb usb2: configuration #1 chosen from 1 choice
[    3.060535] hub 2-0:1.0: USB hub found
[    3.060542] hub 2-0:1.0: 2 ports detected
[    3.164289] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    3.164300] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.164304] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.164327] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    3.164366] uhci_hcd 0000:00:1d.2: irq 19, io base 0x00003020
[    3.164460] usb usb3: configuration #1 chosen from 1 choice
[    3.164485] hub 3-0:1.0: USB hub found
[    3.164492] hub 3-0:1.0: 2 ports detected
[    3.172117] usb 1-1: new low speed USB device using uhci_hcd and address 2
[    3.268439] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.268457] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.268460] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.268485] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[    3.272401] ehci_hcd 0000:00:1d.7: debug port 1
[    3.272408] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.272422] ehci_hcd 0000:00:1d.7: irq 23, io mem 0x52404000
[    3.300048] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.300202] usb usb4: configuration #1 chosen from 1 choice
[    3.300228] hub 4-0:1.0: USB hub found
[    3.300237] hub 4-0:1.0: 6 ports detected
[    3.508318] ata_piix 0000:00:1f.2: version 2.12
[    3.508340] ata_piix 0000:00:1f.2: PCI INT C -> GSI 17 (level, low) -> IRQ 17
[    3.508344] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    3.664084] ata_piix 0000:00:1f.2: setting latency timer to 64
[    3.664164] scsi0 : ata_piix
[    3.664502] scsi1 : ata_piix
[    3.665682] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x3090 irq 14
[    3.665685] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x3098 irq 15
[    3.696069] usb 1-1: device not accepting address 2, error -71
[    3.752106] hub 1-0:1.0: unable to enumerate USB device on port 1
[    3.828364] ata1.00: ATA-7: ST980811AS, 3.BHE, max UDMA/100
[    3.828367] ata1.00: 156301488 sectors, multi 16: LBA48 
[    3.844373] ata1.00: configured for UDMA/100
[    4.000065] Clocksource tsc unstable (delta = -483337442 ns)
[    4.024516] ata2.00: ATAPI: TSSTcorp CDDVDW TS-L632H, HS02, max MWDMA2
[    4.048072] usb 4-5: new high speed USB device using ehci_hcd and address 3
[    4.056450] ata2.00: configured for MWDMA2
[    4.056564] scsi 0:0:0:0: Direct-Access     ATA      ST980811AS       3.BH PQ: 0 ANSI: 5
[    4.060373] scsi 1:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-L632H  HS02 PQ: 0 ANSI: 5
[    4.060755] 8139too 0000:02:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.060766] 8139too 0000:02:01.0: setting latency timer to 64
[    4.061754] eth0: RealTek RTL8139 at 0x1000, 00:1e:ec:23:c8:85, IRQ 16
[    4.061756] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    4.064670] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    4.093854] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    4.093890] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    4.115411] Driver 'sd' needs updating - please use bus_type methods
[    4.115521] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    4.115541] sd 0:0:0:0: [sda] Write Protect is off
[    4.115543] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.115577] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.115648] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    4.115667] sd 0:0:0:0: [sda] Write Protect is off
[    4.115670] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.115704] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.115708]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    4.127794]  sda1
[    4.127899] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.150105] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.150111] Uniform CD-ROM driver Revision: 3.20
[    4.150213] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.740047] usb 4-5: configuration #1 chosen from 1 choice
[    4.808682] loop: module loaded
[    4.830076] EXT3-fs: INFO: recovery required on readonly filesystem.
[    4.830080] EXT3-fs: write access will be enabled during recovery.
[    4.984057] usb 1-1: new low speed USB device using uhci_hcd and address 4
[    5.159505] usb 1-1: configuration #1 chosen from 1 choice
[    5.166728] usbcore: registered new interface driver libusual
[    5.178145] Initializing USB Mass Storage driver...
[    5.185022] scsi2 : SCSI emulation for USB Mass Storage devices
[    5.188878] usbcore: registered new interface driver usb-storage
[    5.188883] USB Mass Storage support registered.
[    5.188895] usb-storage: device found at 3
[    5.188897] usb-storage: waiting for device to settle before scanning
[    5.194744] usbcore: registered new interface driver hiddev
[    5.212604] input: Logitech USB RECEIVER as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/input/input2
[    5.212986] input,hidraw0: USB HID v1.11 Mouse [Logitech USB RECEIVER] on usb-0000:00:1d.0-1
[    5.213007] usbcore: registered new interface driver usbhid
[    5.213010] usbhid: v2.6:USB HID core driver
[    5.564806] kjournald starting.  Commit interval 5 seconds
[    5.564825] EXT3-fs: recovery complete.
[    5.565011] EXT3-fs: mounted filesystem with ordered data mode.
[   10.188282] usb-storage: device scan complete
[   10.194639] scsi 2:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[   10.196026] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   10.196155] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   10.533048] udevd version 124 started
[   11.246398] iTCO_vendor_support: vendor-support=0
[   11.257620] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   11.258048] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x0460)
[   11.258204] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   11.403858] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   11.480308] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   11.604257] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   11.672499] Linux agpgart interface v0.103
[   11.711364] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input4
[   11.724047] ACPI: Power Button (FF) [PWRF]
[   11.724168] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input5
[   11.740033] ACPI: Power Button (CM) [PWRB]
[   11.740165] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input6
[   11.740237] ACPI: Lid Switch [LID0]
[   11.740320] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input7
[   11.756041] ACPI: Sleep Button (CM) [SLPB]
[   11.775816] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
[   11.775996] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
[   11.790197] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0x40000000
[   11.920956] ACPI: Battery Slot [BAT0] (battery present)
[   12.000192] ACPI: AC Adapter [AC] (off-line)
[   12.000405] ACPI: WMI: Mapper loaded
[   12.725595] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   12.871146] acpi device:17: registered as cooling_device1
[   12.871548] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:14/input/input8
[   12.880023] ACPI: Video Device [OVGA] (multi-head: yes  rom: no  post: no)
[   12.935043] usbcore: registered new interface driver ndiswrapper
[   13.051805] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   13.051834] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   13.146419] usbcore: registered new interface driver lmpcm_usb
[   13.146423] lmpcm_usb: v0.5.5:USB Logitech MediaPlay Cordless Mouse driver
[   13.567237] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input9
[   13.620526] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input10
[   15.674276] lp: driver loaded but no devices found
[   15.713115] AR5210, AR5211, AR5212, AR5416, RF5111, RF5112, RF2413, RF5413, RF2133, RF2425, REGOPS_FUNC, DFS, XR)
[   15.798827] ath_pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.798844] ath_pci 0000:01:00.0: setting latency timer to 64
[   15.798891] Atheros HAL provided by OpenWrt, DD-WRT and MakSat Technologies
[   16.290890] MadWifi: ath_attach: Switching rfkill capability off.
[   16.354598] wifi0: Atheros AR2425 chip found (MAC 14.2, PHY SChip 7.0, Radio 10.2)
[   16.370973] ath_pci: wifi0: Atheros 5424/2424: mem=0x51300000, irq=16
[   16.654269] EXT3 FS on loop0, internal journal
[   26.610389] Adding 976552k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:976552k
[   26.830843] type=1505 audit(1226653219.342:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4082
[   26.995628] type=1505 audit(1226653219.506:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4087
[   26.995846] type=1505 audit(1226653219.506:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4087
[   27.178353] ip_tables: (C) 2000-2006 Netfilter Core Team
[   28.468272] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   28.505349] apm: BIOS not found.
[   28.591078] ppdev: user-space parallel port driver
[   30.816228] Bluetooth: Core ver 2.13
[   30.818298] NET: Registered protocol family 31
[   30.818305] Bluetooth: HCI device and connection manager initialized
[   30.818308] Bluetooth: HCI socket layer initialized
[   30.851332] Bluetooth: L2CAP ver 2.11
[   30.851339] Bluetooth: L2CAP socket layer initialized
[   30.882527] Bluetooth: RFCOMM socket layer initialized
[   30.882744] Bluetooth: RFCOMM TTY layer initialized
[   30.882750] Bluetooth: RFCOMM ver 1.10
[   30.883451] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   30.883458] Bluetooth: BNEP filters: protocol multicast
[   30.918932] Bridge firewalling registered
[   30.919726] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   30.938327] Bluetooth: SCO (Voice Link) ver 0.6
[   30.938335] Bluetooth: SCO socket layer initialized
[   34.721393] [drm] Initialized drm 1.1.0 20060810
[   34.729135] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   34.729145] pci 0000:00:02.0: setting latency timer to 64
[   34.729302] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   35.008388] eth0: link down
[   35.167927] NET: Registered protocol family 17
[   60.502356] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[  136.731352] type=1503 audit(1226653329.242:5): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/6071/net/" pid=6071 profile="/usr/sbin/cupsd"
[  137.800049] type=1503 audit(1226653330.314:6): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/6075/net/" pid=6075 profile="/usr/sbin/cupsd"
[  137.876045] NET: Registered protocol family 10
[  137.877685] lo: Disabled Privacy Extensions
[  137.878881] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  137.881011] type=1503 audit(1226653330.394:7): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=6075 profile="/usr/sbin/cupsd"
[  137.881024] type=1503 audit(1226653330.394:8): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=6075 profile="/usr/sbin/cupsd"
[  137.881030] type=1503 audit(1226653330.394:9): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=6075 profile="/usr/sbin/cupsd"
[  137.881036] type=1503 audit(1226653330.394:10): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=6075 profile="/usr/sbin/cupsd"
[  137.881041] type=1503 audit(1226653330.394:11): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=6075 profile="/usr/sbin/cupsd"
[  137.881047] type=1503 audit(1226653330.394:12): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=6075 profile="/usr/sbin/cupsd"
[  137.881053] type=1503 audit(1226653330.394:13): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=6075 profile="/usr/sbin/cupsd"
[  137.881059] type=1503 audit(1226653330.394:14): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=6075 profile="/usr/sbin/cupsd"
[  148.700053] ath0: no IPv6 routers present
[ 4645.419163] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 4645.453821] ISO 9660 Extensions: RRIP_1991A

---

### Post by joffe on 2008-11-14
I'm at work right now but if you are running the 64-bit version of intrepid you might have a look at this thread:
[COLOR="Blue"][MadWifi Support for AR2425 (AR5007EG) on 64bit Ubuntu !!!]("http://ubuntuforums.org/showthread.php?t=816780")[/COLOR]

It worked great for me but your mileage may vary...

---

### Post by markg48 on 2008-11-14
i think im using 32 bit tho....

---

### Post by markg48 on 2008-11-14
thanks but i already have that version installed as a deb package

for some reason madwifi is only using 24 mb of speed wen my box is capable of 54 mb

---

### Post by markg48 on 2008-11-15
still need a solution

---

