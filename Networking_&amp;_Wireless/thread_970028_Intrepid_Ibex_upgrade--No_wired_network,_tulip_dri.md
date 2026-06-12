---
title: "Intrepid Ibex upgrade--No wired network, tulip driver"
date: 2008-11-03
forum: Networking &amp; Wireless
---

### Post by Mothinator on 2008-11-03
Hello.

This weekend I upgraded my computer from Ubuntu i386 Hardy to Intrepid using the alternate CD.

The problem I am now having is that my computer refuses to get an IP address via DHCP. 

Typing sudo dhclient only shows time outs. Also, looking at the blinking lights on my router, I see my computer send the request, but no reply.

If I boot back to Hardy using a liveCD, I connect fine. I have also tried the Intrepid liveCD, which doesn't connect.(I wish I would have tried the liveCD before the upgrade...)

My ethernet card is an old DECchip 21140 using the tulip driver.

Also, since I saw other people with network problems trace it back to network manager, I removed network-manager and network-manager-gnome, but that didn't help, and of course I can't reinstall from synaptic. 

Has anyone seen this before or know of a fix?

Thanks!

Here is some more info about my computer:
/etc/network/interfaces:
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
#iface eth0 inet static
#address 192.168.0.2
#netmask 255.255.255.0
#network 192.168.0.0
#broadcast 192.168.0.255
#gateway 192.168.0.1


#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

```

lshw -c network:
```

  *-network
       description: Ethernet interface
       product: DECchip 21140 [FasterNet]
       vendor: Digital Equipment Corporation
       physical id: 5
       bus info: pci@0000:00:05.0
       logical name: eth0
       version: 22
       serial: 00:e0:c5:f4:01:7e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.15 latency=64 maxlatency=40 mingnt=20 module=tulip multicast=yes
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 4e:69:8e:a6:6c:2c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

dmesg:
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-7-generic (buildd@palmer) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Oct 30 04:18:38 UTC 2008 (Ubuntu 2.6.27-7.15-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
[    0.000000]  BIOS-e820: 000000001fff0000 - 000000001fff8000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001fff8000 - 0000000020000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] last_pfn = 0x1fff0 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 1fff0000 @ 7000-d000
[    0.000000] RAMDISK: 1f7dd000 - 1ffdfe20
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP 000FA610, 0014 (r0 AMI   )
[    0.000000] ACPI: RSDT 1FFF0000, 002C (r1 AMIINT VIA_K7         10 MSFT       97)
[    0.000000] ACPI: FACP 1FFF0030, 0081 (r1 AMIINT VIA_K7         11 MSFT       97)
[    0.000000] ACPI: DSDT 1FFF0120, 319A (r1    VIA   VIA_K7     1000 MSFT  100000D)
[    0.000000] ACPI: FACS 1FFF8000, 0040
[    0.000000] ACPI: APIC 1FFF00C0, 0054 (r1 AMIINT VIA_K7          9 MSFT       97)
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
[    0.000000]   #4 [001f7dd000 - 001ffdfe20]          RAMDISK ==> [001f7dd000 - 001ffdfe20]
[    0.000000]   #5 [00005c1000 - 00005c4000]    INIT_PG_TABLE ==> [00005c1000 - 00005c4000]
[    0.000000]   #6 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #7 [0000007000 - 0000009000]          PGTABLE ==> [0000007000 - 0000009000]
[    0.000000]   #8 [0000002000 - 0000006000]          BOOTMAP ==> [0000002000 - 0000006000]
[    0.000000] found SMP MP-table at [c00fb880] 000fb880
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0001fff0
[    0.000000]   HighMem  0x0001fff0 -> 0x0001fff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0001fff0
[    0.000000] On node 0 totalpages: 130959
[    0.000000] free_area_init_node: node 0, pgdat c048a500, node_mem_map c1000000
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 125844 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 129807
[    0.000000] Kernel command line: root=UUID=bac88e9f-c369-4070-b18f-5f901d20ef8f ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PMTIMER calibration value
[    0.000000] Detected 1399.748 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.004000] Memory: 505412k/524224k available (2572k kernel code, 18180k reserved, 1160k data, 424k init, 0k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xe0800000 - 0xff3fe000   ( 491 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xdfff0000   ( 511 MB)
[    0.004000]       .init : 0xc04ab000 - 0xc0515000   ( 424 kB)
[    0.004000]       .data : 0xc03832aa - 0xc04a5680   (1160 kB)
[    0.004000]       .text : 0xc0100000 - 0xc03832aa   (2572 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004018] Calibrating delay loop (skipped), value calculated using timer frequency.. 2799.49 BogoMIPS (lpj=5598992)
[    0.004052] Security Framework initialized
[    0.004064] SELinux:  Disabled at boot.
[    0.004105] AppArmor: AppArmor initialized
[    0.004118] Mount-cache hash table entries: 512
[    0.004382] Initializing cgroup subsys ns
[    0.004390] Initializing cgroup subsys cpuacct
[    0.004394] Initializing cgroup subsys memory
[    0.004417] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004421] CPU: L2 Cache: 256K (64 bytes/line)
[    0.004441] Checking 'hlt' instruction... OK.
[    0.020427] SMP alternatives: switching to UP code
[    0.027919] Freeing SMP alternatives: 11k freed
[    0.027926] ACPI: Core revision 20080609
[    0.029970] ACPI: Checking initramfs for custom DSDT
[    0.514807] ENABLING IO-APIC IRQs
[    0.515120] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.554816] CPU0: AMD Athlon(tm) XP 1600+ stepping 02
[    0.556031] Brought up 1 CPUs
[    0.556031] Total of 1 processors activated (2799.49 BogoMIPS).
[    0.556031] CPU0 attaching sched-domain:
[    0.556031]  domain 0: span 0 level CPU
[    0.556031]   groups: 0
[    0.556031] net_namespace: 840 bytes
[    0.556031] Booting paravirtualized kernel on bare hardware
[    0.556031] Time: 15:48:15  Date: 11/03/08
[    0.556031] NET: Registered protocol family 16
[    0.556031] EISA bus registered
[    0.556031] ACPI: bus type pci registered
[    0.556031] PCI: PCI BIOS revision 2.10 entry at 0xfdb21, last bus=1
[    0.556031] PCI: Using configuration type 1 for base access
[    0.557774] ACPI: EC: Look up EC in DSDT
[    0.566427] ACPI: Interpreter enabled
[    0.566433] ACPI: (supports S0 S3 S4 S5)
[    0.566457] ACPI: Using IOAPIC for interrupt routing
[    0.573064] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.573210] PCI: 0000:00:00.0 reg 10 32bit mmio: [e0000000, e3ffffff]
[    0.573294] pci 0000:00:01.0: supports D1
[    0.573317] PCI: 0000:00:05.0 reg 10 io port: [e800, e87f]
[    0.573326] PCI: 0000:00:05.0 reg 14 32bit mmio: [dfffff80, dfffffff]
[    0.573351] PCI: 0000:00:05.0 reg 30 32bit mmio: [dff80000, dffbffff]
[    0.573386] PCI: 0000:00:07.0 reg 10 io port: [e400, e41f]
[    0.573425] pci 0000:00:07.0: supports D1
[    0.573428] pci 0000:00:07.0: supports D2
[    0.573456] PCI: 0000:00:07.1 reg 10 io port: [ec00, ec07]
[    0.573495] pci 0000:00:07.1: supports D1
[    0.573498] pci 0000:00:07.1: supports D2
[    0.573624] PCI: 0000:00:11.1 reg 20 io port: [fc00, fc0f]
[    0.573695] PCI: 0000:00:11.2 reg 20 io port: [d800, d81f]
[    0.573761] PCI: 0000:00:11.3 reg 20 io port: [dc00, dc1f]
[    0.573825] PCI: 0000:00:11.4 reg 20 io port: [e000, e01f]
[    0.573904] PCI: 0000:01:00.0 reg 10 32bit mmio: [d0000000, d7ffffff]
[    0.573911] PCI: 0000:01:00.0 reg 14 io port: [a800, a8ff]
[    0.573919] PCI: 0000:01:00.0 reg 18 32bit mmio: [dfef0000, dfefffff]
[    0.573936] PCI: 0000:01:00.0 reg 30 32bit mmio: [dfec0000, dfedffff]
[    0.573953] pci 0000:01:00.0: supports D1
[    0.573955] pci 0000:01:00.0: supports D2
[    0.573978] PCI: 0000:01:00.1 reg 10 32bit mmio: [c8000000, cfffffff]
[    0.573986] PCI: 0000:01:00.1 reg 14 32bit mmio: [dfee0000, dfeeffff]
[    0.574015] pci 0000:01:00.1: supports D1
[    0.574018] pci 0000:01:00.1: supports D2
[    0.574057] PCI: bridge 0000:00:01.0 io port: [a000, afff]
[    0.574063] PCI: bridge 0000:00:01.0 32bit mmio: [dfe00000, dfefffff]
[    0.574069] PCI: bridge 0000:00:01.0 32bit mmio pref: [bfc00000, dfcfffff]
[    0.574078] bus 00 -> node 0
[    0.574090] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.594325] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.594536] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.594742] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.594946] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.595158] ACPI: Power Resource [URP1] (off)
[    0.595224] ACPI: Power Resource [URP2] (off)
[    0.595287] ACPI: Power Resource [FDDP] (off)
[    0.595351] ACPI: Power Resource [LPTP] (off)
[    0.595491] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.595563] pnp: PnP ACPI init
[    0.595578] ACPI: bus type pnp registered
[    0.598864] pnp: PnP ACPI: found 8 devices
[    0.598869] ACPI: ACPI bus type pnp unregistered
[    0.598876] PnPBIOS: Disabled by ACPI PNP
[    0.599639] PCI: Using ACPI for IRQ routing
[    0.599836] NET: Registered protocol family 8
[    0.599836] NET: Registered protocol family 20
[    0.600045] NetLabel: Initializing
[    0.600049] NetLabel:  domain hash size = 128
[    0.600052] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.600080] NetLabel:  unlabeled traffic allowed by default
[    0.600520] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.600524]    actual entries 65620
[    0.600890] AppArmor: AppArmor Filesystem Enabled
[    0.600917] ACPI: RTC can wake from S4
[    0.636631] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.636637] pci 0000:00:01.0:   IO window: 0xa000-0xafff
[    0.636645] pci 0000:00:01.0:   MEM window: 0xdfe00000-0xdfefffff
[    0.636651] pci 0000:00:01.0:   PREFETCH window: 0x000000bfc00000-0x000000dfcfffff
[    0.636672] pci 0000:00:01.0: setting latency timer to 64
[    0.636678] bus: 00 index 0 io port: [0, ffff]
[    0.636681] bus: 00 index 1 mmio: [0, ffffffff]
[    0.636685] bus: 01 index 0 io port: [a000, afff]
[    0.636689] bus: 01 index 1 mmio: [dfe00000, dfefffff]
[    0.636692] bus: 01 index 2 mmio: [bfc00000, dfcfffff]
[    0.636695] bus: 01 index 3 mmio: [0, 0]
[    0.636718] NET: Registered protocol family 2
[    0.636940] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.637327] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.637594] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.637860] TCP: Hash tables configured (established 16384 bind 16384)
[    0.637865] TCP reno registered
[    0.638067] NET: Registered protocol family 1
[    0.638299] checking if image is initramfs... it is
[    1.140098] Switched to high resolution mode on CPU 0
[    1.696900] Freeing initrd memory: 8203k freed
[    1.698487] audit: initializing netlink socket (disabled)
[    1.698525] type=2000 audit(1225727295.696:1): initialized
[    1.706910] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.711423] VFS: Disk quotas dquot_6.5.1
[    1.711616] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.711826] msgmni has been set to 1003
[    1.712676] io scheduler noop registered
[    1.712684] io scheduler anticipatory registered
[    1.712687] io scheduler deadline registered
[    1.712730] io scheduler cfq registered (default)
[    1.712754] PCI: VIA PCI bridge detected.Disabling DAC.
[    1.712814] pci 0000:01:00.0: Boot video device
[    1.713476] isapnp: Scanning for PnP cards...
[    2.066886] isapnp: No Plug & Play device found
[    2.145769] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.150023] brd: module loaded
[    2.150165] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    2.150400] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.152739] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.152753] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.153617] mice: PS/2 mouse device common for all mice
[    2.153907] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    2.153946] rtc0: alarms up to one year, y3k
[    2.154197] EISA: Probing bus 0 at eisa.0
[    2.154239] EISA: Detected 0 cards.
[    2.154247] cpuidle: using governor ladder
[    2.154250] cpuidle: using governor menu
[    2.155123] TCP cubic registered
[    2.155172] Using IPI No-Shortcut mode
[    2.155626] registered taskstats version 1
[    2.155797]   Magic number: 0:633:840
[    2.155982] tty ptyu6: hash matches
[    2.156141] rtc_cmos 00:03: setting system clock to 2008-11-03 15:48:16 UTC (1225727296)
[    2.156147] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.156150] EDD information not available.
[    2.157003] Freeing unused kernel memory: 424k freed
[    2.157093] Write protecting the kernel text: 2576k
[    2.157151] Write protecting the kernel read-only data: 936k
[    2.183473] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.456699] fuse init (API version 7.9)
[    2.689019] processor ACPI0007:00: registered as cooling_device0
[    2.689028] ACPI: Processor [CPU1] (supports 16 throttling states)
[    3.390173] Linux Tulip driver version 1.1.15 (Feb 27, 2007)
[    3.390240] tulip 0000:00:05.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.395061] tulip0:  EEPROM default media type Autosense.
[    3.395068] tulip0:  Index #0 - Media 10baseT (#0) described by a 21140 non-MII (0) block.
[    3.395073] tulip0:  Index #1 - Media 100baseTx (#3) described by a 21140 non-MII (0) block.
[    3.395078] tulip0:  Index #2 - Media 10baseT-FDX (#4) described by a 21140 non-MII (0) block.
[    3.395083] tulip0:  Index #3 - Media 100baseTx-FDX (#5) described by a 21140 non-MII (0) block.
[    3.395553] tulip0:  MII transceiver #1 config 3100 status 782d advertising 05e1.
[    3.428656] eth0: Digital DS21140 Tulip rev 34 at Port 0xe800, 00:e0:c5:f4:01:7e, IRQ 16.
[    3.981899] No dock devices found.
[    4.111793] SCSI subsystem initialized
[    4.156968] usbcore: registered new interface driver usbfs
[    4.157018] usbcore: registered new interface driver hub
[    4.157133] usbcore: registered new device driver usb
[    4.209498] USB Universal Host Controller Interface driver v3.0
[    4.209612] uhci_hcd 0000:00:11.2: PCI INT D -> GSI 5 (level, low) -> IRQ 5
[    4.209632] uhci_hcd 0000:00:11.2: UHCI Host Controller
[    4.209714] uhci_hcd 0000:00:11.2: new USB bus registered, assigned bus number 1
[    4.209757] uhci_hcd 0000:00:11.2: irq 5, io base 0x0000d800
[    4.210066] usb usb1: configuration #1 chosen from 1 choice
[    4.210115] hub 1-0:1.0: USB hub found
[    4.210132] hub 1-0:1.0: 2 ports detected
[    4.222025] libata version 3.00 loaded.
[    4.416569] uhci_hcd 0000:00:11.3: PCI INT D -> GSI 5 (level, low) -> IRQ 5
[    4.416591] uhci_hcd 0000:00:11.3: UHCI Host Controller
[    4.416642] uhci_hcd 0000:00:11.3: new USB bus registered, assigned bus number 2
[    4.416677] uhci_hcd 0000:00:11.3: irq 5, io base 0x0000dc00
[    4.416883] usb usb2: configuration #1 chosen from 1 choice
[    4.416929] hub 2-0:1.0: USB hub found
[    4.416946] hub 2-0:1.0: 2 ports detected
[    4.530391] usb 1-2: new full speed USB device using uhci_hcd and address 2
[    4.624501] uhci_hcd 0000:00:11.4: PCI INT D -> GSI 5 (level, low) -> IRQ 5
[    4.624521] uhci_hcd 0000:00:11.4: UHCI Host Controller
[    4.624564] uhci_hcd 0000:00:11.4: new USB bus registered, assigned bus number 3
[    4.624598] uhci_hcd 0000:00:11.4: irq 5, io base 0x0000e000
[    4.624776] usb usb3: configuration #1 chosen from 1 choice
[    4.624826] hub 3-0:1.0: USB hub found
[    4.624842] hub 3-0:1.0: 2 ports detected
[    4.691071] usb 1-2: configuration #1 chosen from 1 choice
[    4.692880] hub 1-2:1.0: USB hub found
[    4.694790] hub 1-2:1.0: 4 ports detected
[    4.832556] pata_via 0000:00:11.1: version 0.3.3
[    4.834526] scsi0 : pata_via
[    4.834840] scsi1 : pata_via
[    4.837925] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[    4.837931] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[    5.001381] ata1.00: ATA-4: WDC WD153BA, 16.13Q16, max UDMA/66
[    5.001389] ata1.00: 30043440 sectors, multi 16: LBA 
[    5.001726] usb 1-2.2: new full speed USB device using uhci_hcd and address 3
[    5.017154] ata1.00: configured for UDMA/66
[    5.148990] usb 1-2.2: configuration #1 chosen from 1 choice
[    5.180533] ata2.00: ATAPI: TOSHIBA DVD-ROM SD-M1612, 1004, max UDMA/33
[    5.196410] ata2.00: configured for UDMA/33
[    5.196640] scsi 0:0:0:0: Direct-Access     ATA      WDC WD153BA      16.1 PQ: 0 ANSI: 5
[    5.202895] scsi 1:0:0:0: CD-ROM            TOSHIBA  DVD-ROM SD-M1612 1004 PQ: 0 ANSI: 5
[    5.616489] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    5.616565] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    5.656082] usbcore: registered new interface driver libusual
[    5.673699] Initializing USB Mass Storage driver...
[    5.674804] scsi2 : SCSI emulation for USB Mass Storage devices
[    5.675364] usbcore: registered new interface driver usb-storage
[    5.675373] USB Mass Storage support registered.
[    5.675631] usb-storage: device found at 3
[    5.675636] usb-storage: waiting for device to settle before scanning
[    5.696772] Driver 'sd' needs updating - please use bus_type methods
[    5.700238] sd 0:0:0:0: [sda] 30043440 512-byte hardware sectors (15382 MB)
[    5.700281] sd 0:0:0:0: [sda] Write Protect is off
[    5.700287] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.700342] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.700514] sd 0:0:0:0: [sda] 30043440 512-byte hardware sectors (15382 MB)
[    5.700545] sd 0:0:0:0: [sda] Write Protect is off
[    5.700550] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.700602] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.700610]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    5.720569]  sda1 sda2
[    5.742843] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.755864] sr0: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
[    5.755874] Uniform CD-ROM driver Revision: 3.20
[    5.756105] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   10.673857] usb-storage: device scan complete
[   10.676835] scsi 2:0:0:0: Direct-Access     Generic  Flash R/W        2002 PQ: 0 ANSI: 2
[   10.679798] scsi 2:0:0:1: Direct-Access     Generic  Flash R/W        2002 PQ: 0 ANSI: 2
[   10.682797] scsi 2:0:0:2: Direct-Access     Generic  Flash R/W        2002 PQ: 0 ANSI: 2
[   10.685796] scsi 2:0:0:3: Direct-Access     Generic  Flash R/W        2002 PQ: 0 ANSI: 2
[   10.705116] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   10.705385] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   10.724994] sd 2:0:0:1: [sdc] 2014992 512-byte hardware sectors (1032 MB)
[   10.730985] sd 2:0:0:1: [sdc] Write Protect is off
[   10.730993] sd 2:0:0:1: [sdc] Mode Sense: 03 00 00 00
[   10.730997] sd 2:0:0:1: [sdc] Assuming drive cache: write through
[   10.747820] sd 2:0:0:1: [sdc] 2014992 512-byte hardware sectors (1032 MB)
[   10.750773] sd 2:0:0:1: [sdc] Write Protect is off
[   10.750779] sd 2:0:0:1: [sdc] Mode Sense: 03 00 00 00
[   10.750783] sd 2:0:0:1: [sdc] Assuming drive cache: write through
[   10.750796]  sdc: sdc1
[   10.760913] sd 2:0:0:1: [sdc] Attached SCSI removable disk
[   10.761209] sd 2:0:0:1: Attached scsi generic sg3 type 0
[   10.766065] sd 2:0:0:2: [sdd] Attached SCSI removable disk
[   10.766337] sd 2:0:0:2: Attached scsi generic sg4 type 0
[   10.771051] sd 2:0:0:3: [sde] Attached SCSI removable disk
[   10.771319] sd 2:0:0:3: Attached scsi generic sg5 type 0
[   11.111199] PM: Marking nosave pages: 000000000009f000 - 0000000000100000
[   11.111213] PM: Basic memory bitmaps created
[   11.124184] PM: Basic memory bitmaps freed
[   11.219726] kjournald starting.  Commit interval 5 seconds
[   11.219767] EXT3-fs: mounted filesystem with ordered data mode.
[   23.776950] udevd version 124 started
[   25.383857] Linux agpgart interface v0.103
[   25.459511] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   25.513504] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   25.648864] irda_init()
[   25.648896] NET: Registered protocol family 23
[   25.881619] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   25.931043] agpgart: Detected VIA KT266/KY266x/KT333 chipset
[   25.936948] agpgart-via 0000:00:00.0: AGP aperture is 64M @ 0xe0000000
[   26.004059] gameport: EMU10K1 is pci0000:00:07.1/gameport0, io 0xec00, speed 1193kHz
[   26.060347] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[   26.072073] ACPI: Power Button (FF) [PWRF]
[   26.072345] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
[   26.084042] ACPI: Power Button (CM) [PWRB]
[   26.084318] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input5
[   26.100052] ACPI: Sleep Button (CM) [SLPB]
[   27.259337] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input6
[   28.437692] EMU10K1_Audigy 0000:00:07.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   32.944895] lp: driver loaded but no devices found
[   33.687850] Adding 1349452k swap on /dev/sda2.  Priority:-1 extents:1 across:1349452k
[   34.168495] EXT3 FS on sda1, internal journal
[   34.905528] type=1505 audit(1225727329.505:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4038
[   35.255018] type=1505 audit(1225727329.853:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4043
[   35.255566] type=1505 audit(1225727329.853:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4043
[   35.430469] ip_tables: (C) 2000-2006 Netfilter Core Team
[   36.812541] NET: Registered protocol family 17
[   40.924354] eth0: Setting full-duplex based on MII#1 link partner capability of 45e1.
[  109.954775] NET: Registered protocol family 10
[  109.955517] lo: Disabled Privacy Extensions
[  111.273125] ACPI: WMI: Mapper loaded
[  113.017367] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[  113.228782] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  113.228797] apm: overridden by ACPI.
[  113.456714] ppdev: user-space parallel port driver
[  114.692377] RPC: Registered udp transport module.
[  114.692392] RPC: Registered tcp transport module.
[  114.921130] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[  114.941082] type=1503 audit(1225727409.541:5): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=0 name="/proc/4779/net/" pid=4779 profile="/usr/sbin/cupsd"
[  115.047682] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[  115.074701] NFSD: starting 90-second grace period
[  119.031622] Bluetooth: Core ver 2.13
[  119.035226] NET: Registered protocol family 31
[  119.035237] Bluetooth: HCI device and connection manager initialized
[  119.035245] Bluetooth: HCI socket layer initialized
[  119.061738] Bluetooth: L2CAP ver 2.11
[  119.061750] Bluetooth: L2CAP socket layer initialized
[  119.107287] Bluetooth: RFCOMM socket layer initialized
[  119.107794] Bluetooth: RFCOMM TTY layer initialized
[  119.107804] Bluetooth: RFCOMM ver 1.10
[  119.115336] Bluetooth: SCO (Voice Link) ver 0.6
[  119.115353] Bluetooth: SCO socket layer initialized
[  119.144818] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  119.144834] Bluetooth: BNEP filters: protocol multicast
[  119.210087] Bridge firewalling registered
[  119.211479] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[  120.263112] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  120.708046] eth0: no IPv6 routers present
[  120.730390] [drm] Initialized drm 1.1.0 20060810
[  120.851088] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[  121.231936] agpgart-via 0000:00:00.0: AGP 2.0 bridge
[  121.231987] agpgart-via 0000:00:00.0: putting AGP V2 device into 4x mode
[  121.232069] pci 0000:01:00.0: putting AGP V2 device into 4x mode
[  121.645490] [drm] Setting GART location based on new memory map
[  121.645516] [drm] Loading R200 Microcode
[  121.645563] [drm] writeback test succeeded in 1 usecs
[  221.955531] type=1503 audit(1225727516.553:6): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/5804/net/" pid=5804 profile="/usr/sbin/cupsd"
[  223.027099] type=1503 audit(1225727517.625:7): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/5810/net/" pid=5810 profile="/usr/sbin/cupsd"
[  223.030485] type=1503 audit(1225727517.629:8): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=5810 profile="/usr/sbin/cupsd"
[  223.033076] type=1503 audit(1225727517.633:9): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=5810 profile="/usr/sbin/cupsd"
[  223.035672] type=1503 audit(1225727517.633:10): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=5810 profile="/usr/sbin/cupsd"
[  223.038228] type=1503 audit(1225727517.637:11): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=5810 profile="/usr/sbin/cupsd"
[  223.040784] type=1503 audit(1225727517.641:12): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=5810 profile="/usr/sbin/cupsd"
[  223.040801] type=1503 audit(1225727517.641:13): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=5810 profile="/usr/sbin/cupsd"
[  223.040812] type=1503 audit(1225727517.641:14): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=5810 profile="/usr/sbin/cupsd"
[  272.228013] pan0: no IPv6 routers present

```

---

