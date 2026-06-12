---
title: "[SOLVED] Huawei E172 Mobile Broadband on Vodafone"
date: 2008-07-28
forum: Networking &amp; Wireless
---

### Post by wheezy-weasel on 2008-07-28
Hi,

I just bought a new Asus U6S and immediately installed Ubuntu 8.04, then ordered a Huawei E172 from Vodafone.

I installed the driver: vodafone-mobile-connect-card-driver-for-linux_1.99.17_i386.deb however when I launch it the splash comes up and freezes. The only way to get rid of it is to reboot.

The blue light on the card flashes intermittently.

(E172 works fine, though ***much slower than advertised***, on my works XP laptop).

Linux understanding level: beginner

I have tried connecting with wvdial, using the tutorial [here]("http://ubuntuforums.org/showthread.php?t=843973") but it caused the system to freeze and I had to do a hard reset. Also tried using gnome-ppp with no joy.

I posted over at Vodafone Betavine forums but no replies yet.

Please can someone provide troubleshooting steps/advice that I can follow to diagnose the issue.

Cheers

---

### Post by wheezy-weasel on 2008-07-29
*<shameless bump>*

---

### Post by p221072 on 2008-07-29
You should give some more details.
Please post the output of the dmesg command after you plugin the device and post your wvdial.conf file so maybe we can help you.

---

### Post by wheezy-weasel on 2008-07-29
Hi,

dmesg output

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Fri Jul 11 23:41:49 UTC 2008 (Ubuntu 2.6.24-19.36-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e3000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bffa0000 (usable)
[    0.000000]  BIOS-e820: 00000000bffa0000 - 00000000bffae000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bffae000 - 00000000bfff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfff0000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] Warning only 4GB will be used.
[    0.000000] Use a HIGHMEM64G enabled kernel.
[    0.000000] 3200MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 1048576) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->  1048576
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->  1048576
[    0.000000] On node 0 totalpages: 1048576
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 6400 pages used for memmap
[    0.000000]   HighMem zone: 812800 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F81D0 checksum 0
[    0.000000] ACPI: RSDP 000F81D0, 0024 (r2 ACPIAM)
[    0.000000] ACPI: XSDT BFFA0100, 0084 (r1 _ASUS_ Notebook  4000801 MSFT       97)
[    0.000000] ACPI: FACP BFFA0290, 00F4 (r3 A_M_I_ OEMFACP   4000801 MSFT       97)
[    0.000000] ACPI: DSDT BFFA0680, C3E0 (r1  U6S00 U6S00000        0 INTL 20051117)
[    0.000000] ACPI: FACS BFFAE000, 0040
[    0.000000] ACPI: APIC BFFA0390, 005C (r1 A_M_I_ OEMAPIC   4000801 MSFT       97)
[    0.000000] ACPI: MCFG BFFA0430, 003C (r1 A_M_I_ OEMMCFG   4000801 MSFT       97)
[    0.000000] ACPI: SLIC BFFA0470, 0176 (r1 _ASUS_ Notebook  4000801 MSFT       97)
[    0.000000] ACPI: DBGP BFFA03F0, 0034 (r1 A_M_I_ OEMDBGP   4000801 MSFT       97)
[    0.000000] ACPI: BOOT BFFA05F0, 0028 (r1 A_M_I_ OEMBOOT   4000801 MSFT       97)
[    0.000000] ACPI: ECDT BFFA0620, 0054 (r1 A_M_I_ OEMECDT   4000801 MSFT       97)
[    0.000000] ACPI: OEMB BFFAE040, 0060 (r1 A_M_I_ AMI_OEM   4000801 MSFT       97)
[    0.000000] ACPI: HPET BFFACA60, 0038 (r1 A_M_I_ OEMHPET   4000801 MSFT       97)
[    0.000000] ACPI: TCPA BFFACB40, 0032 (r2 A_M_I_ TBLOEMID        1 MSFT       97)
[    0.000000] ACPI: ATKG BFFC15D0, 8024 (r1 A_M_I_  OEMATKG  5000702 MSFT       97)
[    0.000000] ACPI: SSDT BFFCA110, 04E6 (r1  PmRef    CpuPm     3000 INTL 20051117)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:15 APIC version 20
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at c4000000 (gap: c0000000:3ee00000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e3000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e3000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1040384
[    0.000000] Kernel command line: root=UUID=eeecf82a-8e94-4dd1-86c6-beee8a2b8615 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1995.212 MHz processor.
[   14.012228] Console: colour VGA+ 80x25
[   14.012231] console [tty0] enabled
[   14.012467] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   14.012717] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   14.184079] Memory: 3098976k/4194304k available (2177k kernel code, 45104k reserved, 1006k data, 368k init, 2227840k highmem)
[   14.184085] virtual kernel memory layout:
[   14.184085]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   14.184086]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   14.184087]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   14.184088]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   14.184089]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   14.184090]       .data : 0xc0320474 - 0xc041bdc4   (1006 kB)
[   14.184091]       .text : 0xc0100000 - 0xc0320474   (2177 kB)
[   14.184093] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   14.184129] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   14.184255] hpet clockevent registered
[   14.264218] Calibrating delay using timer specific routine.. 3994.62 BogoMIPS (lpj=7989254)
[   14.264236] Security Framework initialized
[   14.264241] SELinux:  Disabled at boot.
[   14.264253] AppArmor: AppArmor initialized
[   14.264256] Failure registering capabilities with primary security module.
[   14.264263] Mount-cache hash table entries: 512
[   14.264368] Initializing cgroup subsys ns
[   14.264372] Initializing cgroup subsys cpuacct
[   14.264381] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001 00000001
[   14.264387] monitor/mwait feature present.
[   14.264388] using mwait in idle threads.
[   14.264392] CPU: L1 I cache: 32K, L1 D cache: 32K
[   14.264394] CPU: L2 cache: 2048K
[   14.264396] CPU: Physical Processor ID: 0
[   14.264397] CPU: Processor Core ID: 0
[   14.264399] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001 00000001
[   14.264407] Compat vDSO mapped to ffffe000.
[   14.264417] Checking 'hlt' instruction... OK.
[   14.280544] SMP alternatives: switching to UP code
[   14.281945] Early unpacking initramfs... done
[   14.568815] ACPI: Core revision 20070126
[   14.568868] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   14.623077] CPU0: Intel(R) Core(TM)2 Duo CPU     T7250  @ 2.00GHz stepping 0d
[   14.623091] SMP alternatives: switching to SMP code
[   14.623704] Booting processor 1/1 eip 3000
[   14.633887] Initializing CPU#1
[   14.711962] Calibrating delay using timer specific routine.. 3990.07 BogoMIPS (lpj=7980151)
[   14.711968] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001 00000001
[   14.711972] monitor/mwait feature present.
[   14.711975] CPU: L1 I cache: 32K, L1 D cache: 32K
[   14.711976] CPU: L2 cache: 2048K
[   14.711978] CPU: Physical Processor ID: 0
[   14.711979] CPU: Processor Core ID: 1
[   14.711980] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001 00000001
[   14.712452] CPU1: Intel(R) Core(TM)2 Duo CPU     T7250  @ 2.00GHz stepping 0d
[   14.712472] Total of 2 processors activated (7984.70 BogoMIPS).
[   14.712644] ENABLING IO-APIC IRQs
[   14.712829] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   14.859975] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   14.879979] Brought up 2 CPUs
[   14.880000] CPU0 attaching sched-domain:
[   14.880002]  domain 0: span 03
[   14.880003]   groups: 01 02
[   14.880006] CPU1 attaching sched-domain:
[   14.880007]  domain 0: span 03
[   14.880009]   groups: 02 01
[   14.880190] net_namespace: 64 bytes
[   14.880201] Booting paravirtualized kernel on bare hardware
[   14.880593] Time:  9:20:18  Date: 07/29/08
[   14.880616] NET: Registered protocol family 16
[   14.880768] EISA bus registered
[   14.880772] ACPI: bus type pci registered
[   14.881004] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=7
[   14.881006] PCI: Using configuration type 1
[   14.881029] Setting up standard PCI resources
[   14.884254] ACPI: EC: EC description table is found, configuring boot EC
[   14.979069] ACPI: Interpreter enabled
[   14.979072] ACPI: (supports S0 S1 S3 S4 S5)
[   14.979089] ACPI: Using IOAPIC for interrupt routing
[   14.980655] Error attaching device data
[   14.980690] Error attaching device data
[   14.988738] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[   14.988740] ACPI: EC: driver started in poll mode
[   14.989139] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   14.990099] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[   14.990103] PCI quirk: region 0500-053f claimed by ICH6 GPIO
[   14.991151] PCI: Transparent bridge - 0000:00:1e.0
[   14.991205] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   14.991367] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   14.991506] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[   14.991620] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[   14.991750] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[   14.991870] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[   14.991986] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[   15.009894] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12)
[   15.010057] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 10 12)
[   15.010220] ACPI: PCI Interrupt Link [LNKC] (IRQs *3)
[   15.010378] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 *7 10 12)
[   15.010537] ACPI: PCI Interrupt Link [LNKE] (IRQs *6)
[   15.010694] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 *4 5 6 7 10 12)
[   15.010854] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *10 12)
[   15.011013] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 12)
[   15.011171] ACPI Warning (tbutils-0217): Incorrect checksum in table [ATKG] -  FC, should be 59 [20070126]
[   15.011178] Linux Plug and Play Support v0.97 (c) Adam Belay
[   15.011202] pnp: PnP ACPI init
[   15.011208] ACPI: bus type pnp registered
[   15.013585] pnp: PnP ACPI: found 14 devices
[   15.013587] ACPI: ACPI bus type pnp unregistered
[   15.013590] PnPBIOS: Disabled by ACPI PNP
[   15.013767] PCI: Using ACPI for IRQ routing
[   15.013769] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   15.059877] NET: Registered protocol family 8
[   15.059879] NET: Registered protocol family 20
[   15.059905] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   15.059909] hpet0: 3 64-bit timers, 14318180 Hz
[   15.060937] AppArmor: AppArmor Filesystem Enabled
[   15.063770] Time: tsc clocksource has been installed.
[   15.063778] Switched to high resolution mode on CPU 0
[   15.063872] Switched to high resolution mode on CPU 1
[   15.076756] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
[   15.076764] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   15.076766] system 00:08: ioport range 0x800-0x87f has been reserved
[   15.076769] system 00:08: ioport range 0x400-0x41f has been reserved
[   15.076771] system 00:08: ioport range 0x500-0x53f has been reserved
[   15.076773] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[   15.076775] system 00:08: iomem range 0xfed20000-0xfed3ffff has been reserved
[   15.076778] system 00:08: iomem range 0xfed45000-0xfed89fff has been reserved
[   15.076782] system 00:08: iomem range 0xffb00000-0xffbfffff could not be reserved
[   15.076784] system 00:08: iomem range 0xfff00000-0xffffffff could not be reserved
[   15.076789] system 00:0a: ioport range 0x250-0x253 has been reserved
[   15.076791] system 00:0a: ioport range 0x256-0x25f has been reserved
[   15.076794] system 00:0a: iomem range 0xfec00000-0xfec00fff has been reserved
[   15.076796] system 00:0a: iomem range 0xfee00000-0xfee00fff could not be reserved
[   15.076802] system 00:0c: iomem range 0xc0000000-0xcfffffff has been reserved
[   15.076807] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[   15.076809] system 00:0d: iomem range 0xc0000-0xcffff could not be reserved
[   15.076811] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
[   15.076813] system 00:0d: iomem range 0x100000-0xbfffffff could not be reserved
[   15.076816] system 00:0d: iomem range 0x0-0x0 could not be reserved
[   15.107154] PCI: Bridge: 0000:00:01.0
[   15.107156]   IO window: a000-afff
[   15.107160]   MEM window: f8000000-fe0fffff
[   15.107163]   PREFETCH window: d5f00000-f5efffff
[   15.107166] PCI: Bridge: 0000:00:1c.0
[   15.107167]   IO window: disabled.
[   15.107172]   MEM window: disabled.
[   15.107176]   PREFETCH window: disabled.
[   15.107182] PCI: Bridge: 0000:00:1c.1
[   15.107185]   IO window: b000-bfff
[   15.107190]   MEM window: fe100000-fe8fffff
[   15.107195]   PREFETCH window: f5f00000-f7efffff
[   15.107200] PCI: Bridge: 0000:00:1c.2
[   15.107203]   IO window: c000-cfff
[   15.107209]   MEM window: fe900000-fe9fffff
[   15.107213]   PREFETCH window: disabled.
[   15.107218] PCI: Bridge: 0000:00:1c.3
[   15.107219]   IO window: disabled.
[   15.107225]   MEM window: fea00000-feafffff
[   15.107229]   PREFETCH window: disabled.
[   15.107235] PCI: Bridge: 0000:00:1e.0
[   15.107236]   IO window: disabled.
[   15.107241]   MEM window: disabled.
[   15.107245]   PREFETCH window: disabled.
[   15.107262] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   15.107266] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   15.107289] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   15.107295] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   15.107319] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
[   15.107324] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   15.107348] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[   15.107354] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   15.107378] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 19
[   15.107383] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   15.107397] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   15.107406] NET: Registered protocol family 2
[   15.144743] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   15.144926] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   15.145284] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   15.145461] TCP: Hash tables configured (established 131072 bind 65536)
[   15.145463] TCP reno registered
[   15.156799] checking if image is initramfs... it is
[   15.721965] Freeing initrd memory: 7312k freed
[   15.722096] Simple Boot Flag at 0x52 set to 0x1
[   15.722607] audit: initializing netlink socket (disabled)
[   15.722618] audit(1217323218.284:1): initialized
[   15.722831] highmem bounce pool size: 64 pages
[   15.724438] VFS: Disk quotas dquot_6.5.1
[   15.724504] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   15.724612] io scheduler noop registered
[   15.724614] io scheduler anticipatory registered
[   15.724615] io scheduler deadline registered
[   15.724624] io scheduler cfq registered (default)
[   15.951716] Boot video device is 0000:01:00.0
[   15.951804] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   15.951838] assign_interrupt_mode Found MSI capability
[   15.951866] Allocate Port Service[0000:00:01.0:pcie00]
[   15.951892] Allocate Port Service[0000:00:01.0:pcie02]
[   15.951964] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   15.952023] assign_interrupt_mode Found MSI capability
[   15.952069] Allocate Port Service[0000:00:1c.0:pcie00]
[   15.952094] Allocate Port Service[0000:00:1c.0:pcie02]
[   15.952187] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   15.952246] assign_interrupt_mode Found MSI capability
[   15.952292] Allocate Port Service[0000:00:1c.1:pcie00]
[   15.952321] Allocate Port Service[0000:00:1c.1:pcie02]
[   15.952418] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   15.952477] assign_interrupt_mode Found MSI capability
[   15.952523] Allocate Port Service[0000:00:1c.2:pcie00]
[   15.952548] Allocate Port Service[0000:00:1c.2:pcie02]
[   15.952641] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   15.952700] assign_interrupt_mode Found MSI capability
[   15.952746] Allocate Port Service[0000:00:1c.3:pcie00]
[   15.952771] Allocate Port Service[0000:00:1c.3:pcie02]
[   15.952981] isapnp: Scanning for PnP cards...
[   16.307206] isapnp: No Plug & Play device found
[   16.327234] Real Time Clock Driver v1.12ac
[   16.327403] hpet_resources: 0xfed00000 is busy
[   16.327446] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   16.328757] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   16.328810] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   16.328891] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   16.331196] i8042.c: Detected active multiplexing controller, rev 1.1.
[   16.331852] serio: i8042 KBD port at 0x60,0x64 irq 1
[   16.331856] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   16.331858] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   16.331860] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   16.331861] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   16.347176] mice: PS/2 mouse device common for all mice
[   16.347266] EISA: Probing bus 0 at eisa.0
[   16.347303] EISA: Detected 0 cards.
[   16.347306] cpuidle: using governor ladder
[   16.347307] cpuidle: using governor menu
[   16.347375] NET: Registered protocol family 1
[   16.347398] Using IPI No-Shortcut mode
[   16.347421] registered taskstats version 1
[   16.347516]   Magic number: 0:410:324
[   16.347524]   hash matches device ttyyd
[   16.347559]   hash matches device tty49
[   16.347576]   hash matches device PNP0B00:00
[   16.347578] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   16.347580] EDD information not available.
[   16.347744] Freeing unused kernel memory: 368k freed
[   16.379099] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   17.535394] fuse init (API version 7.9)
[   17.551722] ACPI: SSDT BFFC96D0, 0286 (r1  PmRef  Cpu0Ist     3000 INTL 20051117)
[   17.551991] ACPI: SSDT BFFC99F0, 0712 (r1  PmRef  Cpu0Cst     3001 INTL 20051117)
[   17.552991] Monitor-Mwait will be used to enter C-1 state
[   17.552994] Monitor-Mwait will be used to enter C-2 state
[   17.552996] Monitor-Mwait will be used to enter C-3 state
[   17.553101] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   17.553106] ACPI: Processor [P001] (supports 8 throttling states)
[   17.553313] ACPI: SSDT BFFC9600, 00C8 (r1  PmRef  Cpu1Ist     3000 INTL 20051117)
[   17.553568] ACPI: SSDT BFFC9960, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20051117)
[   17.554811] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   17.554816] ACPI: Processor [P002] (supports 8 throttling states)
[   17.555932] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   17.559157] ACPI: Thermal Zone [THRM] (37 C)
[   17.938085] usbcore: registered new interface driver usbfs
[   17.938112] usbcore: registered new interface driver hub
[   17.938136] usbcore: registered new device driver usb
[   17.951408] r8169 Gigabit Ethernet driver 2.2LK loaded
[   17.951439] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[   17.951459] PCI: Setting latency timer of device 0000:05:00.0 to 64
[   17.951781] eth0: RTL8168b/8111b at 0xf8880000, 00:1f:c6:e8:58:d0, XID 38000000 IRQ 218
[   17.965500] SCSI subsystem initialized
[   17.967066] USB Universal Host Controller Interface driver v3.0
[   17.967101] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
[   17.967113] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   17.967117] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   17.967337] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[   17.967369] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000e080
[   17.967483] usb usb1: configuration #1 chosen from 1 choice
[   17.967503] hub 1-0:1.0: USB hub found
[   17.967507] hub 1-0:1.0: 2 ports detected
[   17.992940] libata version 3.00 loaded.
[   18.071380] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 20
[   18.071391] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   18.071396] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   18.071416] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[   18.071448] uhci_hcd 0000:00:1a.1: irq 20, io base 0x0000e000
[   18.071543] usb usb2: configuration #1 chosen from 1 choice
[   18.071562] hub 2-0:1.0: USB hub found
[   18.071566] hub 2-0:1.0: 2 ports detected
[   18.175323] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 21
[   18.175334] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   18.175338] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   18.175359] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
[   18.175389] uhci_hcd 0000:00:1d.0: irq 21, io base 0x0000dc00
[   18.175485] usb usb3: configuration #1 chosen from 1 choice
[   18.175505] hub 3-0:1.0: USB hub found
[   18.175509] hub 3-0:1.0: 2 ports detected
[   18.279260] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[   18.279270] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   18.279274] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   18.279293] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
[   18.279323] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d880
[   18.279420] usb usb4: configuration #1 chosen from 1 choice
[   18.279441] hub 4-0:1.0: USB hub found
[   18.279445] hub 4-0:1.0: 2 ports detected
[   18.382241] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   18.382260] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   18.382264] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   18.382283] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
[   18.382314] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d800
[   18.382410] usb usb5: configuration #1 chosen from 1 choice
[   18.382429] hub 5-0:1.0: USB hub found
[   18.382433] hub 5-0:1.0: 2 ports detected
[   18.414117] usb 2-2: new full speed USB device using uhci_hcd and address 2
[   18.434103] Clocksource tsc unstable (delta = -1471966442 ns)
[   18.438161] Time: hpet clocksource has been installed.
[   18.443479] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 18
[   18.443489] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   18.443493] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   18.443512] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
[   18.447421] ehci_hcd 0000:00:1a.7: debug port 1
[   18.447429] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   18.447434] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfebff400

[   18.493654] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   18.493804] usb usb6: configuration #1 chosen from 1 choice
[   18.493825] hub 6-0:1.0: USB hub found
[   18.493830] hub 6-0:1.0: 4 ports detected
[   18.500849] ahci 0000:00:1f.2: version 3.0
[   18.500889] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 20 (level, low) -> IRQ 22
[   18.520442] usb 2-2: device not accepting address 2, error -71
[   18.539411] usb 3-2: new low speed USB device using uhci_hcd and address 2
[   18.553562] usb 3-2: configuration #1 chosen from 1 choice
[   18.584918] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[   18.584923] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck stag pm led clo pmp pio slum part 
[   18.584931] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   18.585179] scsi0 : ahci
[   18.585345] scsi1 : ahci
[   18.585477] scsi2 : ahci
[   18.585576] ata1: SATA max UDMA/133 abar m2048@0xfebff800 port 0xfebff900 irq 217
[   18.585580] ata2: SATA max UDMA/133 abar m2048@0xfebff800 port 0xfebff980 irq 217
[   18.585583] ata3: SATA max UDMA/133 abar m2048@0xfebff800 port 0xfebffa00 irq 217
[   18.588345] usb 4-2: new full speed USB device using uhci_hcd and address 2
[   18.600841] usb 4-2: configuration #1 chosen from 1 choice
[   18.630458] usb 5-1: new full speed USB device using uhci_hcd and address 2
[   18.646844] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   18.647608] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[   18.647711] ata1.00: ACPI cmd ef/10:06:00:00:00:a0 succeeded
[   18.647814] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 succeeded
[   18.648475] ata1.00: ATA-8: ST9250827AS, 3.AAA, max UDMA/133
[   18.648477] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   18.649613] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[   18.649719] ata1.00: ACPI cmd ef/10:06:00:00:00:a0 succeeded
[   18.649840] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 succeeded
[   18.650069] ata1.00: configured for UDMA/133
[   18.650341] usb 5-1: not running at top speed; connect to a high speed hub
[   18.656528] usb 5-1: configuration #1 chosen from 1 choice
[   18.691916] usb 5-2: new full speed USB device using uhci_hcd and address 3
[   18.693035] ata2: SATA link down (SStatus 0 SControl 300)
[   18.710047] usb 5-2: configuration #1 chosen from 1 choice
[   18.743630] ata3: SATA link down (SStatus 0 SControl 300)
[   18.743739] scsi 0:0:0:0: Direct-Access     ATA      ST9250827AS      3.AA PQ: 0 ANSI: 5
[   18.743961] ata_piix 0000:00:1f.1: version 2.12
[   18.743977] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   18.744008] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   18.744280] scsi3 : ata_piix
[   18.744410] scsi4 : ata_piix
[   18.744939] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   18.744942] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   18.751268] Driver 'sd' needs updating - please use bus_type methods
[   18.753031] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   18.753048] sd 0:0:0:0: [sda] Write Protect is off
[   18.753052] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   18.753075] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   18.753133] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   18.753142] sd 0:0:0:0: [sda] Write Protect is off
[   18.753143] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   18.753157] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   18.753159]  sda: sda1 sda2 sda3
[   18.758913] sd 0:0:0:0: [sda] Attached SCSI disk
[   18.763656] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   18.792045] usb 6-4: new high speed USB device using ehci_hcd and address 2
[   18.903765] Attempting manual resume
[   18.903768] swsusp: Resume From Partition 8:2
[   18.903769] PM: Checking swsusp image.
[   18.903938] PM: Resume from disk failed.
[   18.936206] usb 6-4: configuration #1 chosen from 1 choice
[   18.937825] usbcore: registered new interface driver hiddev
[   18.939449] kjournald starting.  Commit interval 5 seconds
[   18.939488] EXT3-fs: mounted filesystem with ordered data mode.
[   18.952554] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb3/3-2/3-2:1.0/input/input2
[   18.965374] ata4.00: ATAPI: MATSHITADVD-RAM UJ-852S, 1.00, max UDMA/33
[   18.979831] input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-2
[   19.009457] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb3/3-2/3-2:1.1/input/input3
[   19.036866] input,hiddev96,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.0-2
[   19.036897] usbcore: registered new interface driver usbhid
[   19.036901] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   19.090664] ata4.00: configured for UDMA/33
[   19.090752] ata5: port disabled. ignoring.
[   19.092098] scsi 3:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-852S  1.00 PQ: 0 ANSI: 5
[   19.092193] scsi 3:0:0:0: Attached scsi generic sg1 type 5
[   19.092263] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 21
[   19.092275] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   19.092278] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   19.092303] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[   19.096225] ehci_hcd 0000:00:1d.7: debug port 1
[   19.096231] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   19.096237] ehci_hcd 0000:00:1d.7: irq 21, io mem 0xfebff000
[   19.103078] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   19.103229] usb usb7: configuration #1 chosen from 1 choice
[   19.103248] hub 7-0:1.0: USB hub found
[   19.103253] hub 7-0:1.0: 6 ports detected
[   19.116388] usb 3-2: USB disconnect, address 2
[   19.139793] usb 4-2: USB disconnect, address 2
[   19.163646] usb 5-1: USB disconnect, address 2
[   19.186993] usb 5-2: USB disconnect, address 3
[   19.312590] usb 7-5: new high speed USB device using ehci_hcd and address 4
[   19.548862] usb 7-5: configuration #1 chosen from 1 choice
[   19.743467] usb 3-2: new low speed USB device using uhci_hcd and address 3
[   19.829325] usb 3-2: configuration #1 chosen from 1 choice
[   19.852495] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb3/3-2/3-2:1.0/input/input4
[   19.878504] input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-2
[   19.905294] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb3/3-2/3-2:1.1/input/input5
[   19.926414] input,hiddev96,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.0-2
[   20.122599] usb 4-2: new full speed USB device using uhci_hcd and address 3
[   20.255308] usb 4-2: configuration #1 chosen from 1 choice
[   20.303655] usb 5-2: new full speed USB device using uhci_hcd and address 4
[   20.379870] usb 5-2: configuration #1 chosen from 1 choice
[   22.199196] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   22.256229] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   22.356208] input: Power Button (FF) as /devices/virtual/input/input6
[   22.380329] Linux agpgart interface v0.102
[   22.384428] ACPI: Power Button (FF) [PWRF]
[   22.384525] input: Sleep Button (CM) as /devices/virtual/input/input7
[   22.420427] ACPI: Sleep Button (CM) [SLPB]
[   22.420491] input: Lid Switch as /devices/virtual/input/input8
[   22.424405] ACPI: Lid Switch [LID]
[   22.524432] asus-laptop: Asus Laptop Support version 0.42
[   22.525099] asus-laptop: BSTS called, 0x7f7f returned
[   22.525150] asus-laptop:   U6Sg model detected
[   22.528153] Registered led device: asus:mail
[   22.585059] ACPI: AC Adapter [AC0] (off-line)
[   22.702119] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/LNXVIDEO:00/input/input9
[   22.719228] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   22.720854] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input10
[   22.740205] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   22.832687] ACPI: Battery Slot [BAT0] (battery present)
[   23.206299] nvidia: module license 'NVIDIA' taints kernel.
[   23.212033] usbcore: registered new interface driver libusual
[   23.534612] Initializing USB Mass Storage driver...
[   23.535810] scsi5 : SCSI emulation for USB Mass Storage devices
[   23.535900] usbcore: registered new interface driver usb-storage
[   23.535903] USB Mass Storage support registered.
[   23.535905] usb-storage: device found at 2
[   23.535907] usb-storage: waiting for device to settle before scanning
[   23.535969] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   23.535978] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   23.536072] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   23.576866] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 23
[   23.576891] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   23.612518] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   23.663670] iTCO_vendor_support: vendor-support=0
[   23.688213] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   23.688285] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[   23.688294] iTCO_wdt: No card detected
[   23.765214] Bluetooth: Core ver 2.11
[   23.784937] NET: Registered protocol family 31
[   23.784940] Bluetooth: HCI device and connection manager initialized
[   23.784944] Bluetooth: HCI socket layer initialized
[   23.892276] iwl4965: Intel(R) Wireless WiFi Link 4965AGN driver for Linux, 1.2.0
[   23.892279] iwl4965: Copyright(c) 2003-2007 Intel Corporation
[   23.892389] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 19 (level, low) -> IRQ 19
[   23.892401] PCI: Setting latency timer of device 0000:06:00.0 to 64
[   23.892432] iwl4965: Detected Intel Wireless WiFi Link 4965AGN
[   23.939337] Bluetooth: HCI USB driver ver 2.9
[   23.942380] usbcore: registered new interface driver hci_usb
[   24.031448] Driver 'sr' needs updating - please use bus_type methods
[   24.038519] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   24.038523] Uniform CD-ROM driver Revision: 3.20
[   24.038571] sr 3:0:0:0: Attached scsi CD-ROM sr0
[   24.167408] Linux video capture interface: v2.00
[   24.227885] input: PC Speaker as /devices/platform/pcspkr/input/input11
[   24.280482] uvcvideo: Found UVC 1.00 device USB2.0 0.3M UVC WebCam (04f2:b036)
[   24.283962] usbcore: registered new interface driver uvcvideo
[   24.283966] USB Video Class driver (v0.1.0)
[   24.413644] tpm_inf_pnp 00:0b: Found TPM with ID IFX0102
[   24.413700] tpm_inf_pnp 00:0b: TPM found: config base 0x254, data base 0x4700, chip version 0x000b, vendor id 0x15d1 (Infineon), product id 0x000b (SLB 9635 TT 1.2)
[   24.806749] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04711/0x200000
[   24.846479] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input12
[   25.431320] lp: driver loaded but no devices found
[   25.458160] iwl4965: Tunable channels: 13 802.11bg, 19 802.11a channels
[   25.466543] wmaster0: Selected rate control algorithm 'iwl-4965-rs'
[   25.561630] Adding 1951888k swap on /dev/sda2.  Priority:-1 extents:1 across:1951888k
[   25.584611] EXT3 FS on sda1, internal journal
[   25.655424] kjournald starting.  Commit interval 5 seconds
[   25.655722] EXT3 FS on sda3, internal journal
[   25.655727] EXT3-fs: mounted filesystem with ordered data mode.
[   25.922747] ip_tables: (C) 2000-2006 Netfilter Core Team
[   26.172486] No dock devices found.
[   26.952423] usb-storage: device scan complete
[   26.955624] scsi 5:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[   26.962555] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[   26.962593] sd 5:0:0:0: Attached scsi generic sg2 type 0
[   28.277282] apm: BIOS not found.
[   28.329270] ppdev: user-space parallel port driver
[   28.347448] audit(1217323244.449:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5292 profile="/usr/sbin/cupsd" namespace="default"
[   29.479424] r8169: eth0: link up
[   29.479437] r8169: eth0: link up
[   29.528038] Bluetooth: L2CAP ver 2.9
[   29.528047] Bluetooth: L2CAP socket layer initialized
[   29.660331] Bluetooth: RFCOMM socket layer initialized
[   29.660353] Bluetooth: RFCOMM TTY layer initialized
[   29.660356] Bluetooth: RFCOMM ver 1.8
[   31.983518] NET: Registered protocol family 17
[   32.842986] /dev/vmmon[5777]: Module vmmon: registered with major=10 minor=165
[   32.843019] /dev/vmmon[5777]: Module vmmon: initialized
[   33.256441] /dev/vmnet: open called by PID 5815 (vmnet-bridge)
[   33.256449] /dev/vmnet: hub 0 does not exist, allocating memory.
[   33.256457] /dev/vmnet: port on hub 0 successfully opened
[   33.256469] bridge-eth0: enabling the bridge
[   33.256474] bridge-eth0: up
[   33.256475] bridge-eth0: already up
[   33.256477] bridge-eth0: attached
[   33.260472] /dev/vmnet: open called by PID 5825 (vmnet-bridge)
[   33.260486] /dev/vmnet: hub 2 does not exist, allocating memory.
[   33.260495] /dev/vmnet: port on hub 2 successfully opened
[   33.260507] bridge-wlan0: enabling the bridge
[   33.260510] bridge-wlan0: up
[   33.260512] bridge-wlan0: already up
[   33.260514] bridge-wlan0: attached
[   33.268750] /dev/vmnet: open called by PID 5827 (vmnet-netifup)
[   33.268760] /dev/vmnet: hub 1 does not exist, allocating memory.
[   33.268769] /dev/vmnet: port on hub 1 successfully opened
[   33.270176] /dev/vmnet: open called by PID 5834 (vmnet-netifup)
[   33.270184] /dev/vmnet: hub 8 does not exist, allocating memory.
[   33.270194] /dev/vmnet: port on hub 8 successfully opened
[   33.293007] /dev/vmnet: open called by PID 5836 (vmnet-natd)
[   33.293032] /dev/vmnet: port on hub 8 successfully opened
[   33.325638] /dev/vmnet: open called by PID 5857 (vmnet-dhcpd)
[   33.325664] /dev/vmnet: port on hub 8 successfully opened
[   33.325980] /dev/vmnet: open called by PID 5858 (vmnet-dhcpd)
[   33.325996] /dev/vmnet: port on hub 1 successfully opened
[   37.313733] NET: Registered protocol family 10
[   37.314276] lo: Disabled Privacy Extensions
[   37.316371] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   37.750281] vmnet8: no IPv6 routers present
[   37.766700] vmnet1: no IPv6 routers present
[   37.774075] eth0: no IPv6 routers present
[   60.698036] CPU0 attaching NULL sched-domain.
[   60.698042] CPU1 attaching NULL sched-domain.
[   60.713708] CPU0 attaching sched-domain:
[   60.713713]  domain 0: span 03
[   60.713715]   groups: 01 02
[   60.713718]   domain 1: span 03
[   60.713720]    groups: 03
[   60.713722] CPU1 attaching sched-domain:
[   60.713723]  domain 0: span 03
[   60.713725]   groups: 02 01
[   60.713728]   domain 1: span 03
[   60.713729]    groups: 03
[   68.612765] CPU0 attaching NULL sched-domain.
[   68.612776] CPU1 attaching NULL sched-domain.
[   68.616385] CPU0 attaching sched-domain:
[   68.616391]  domain 0: span 03
[   68.616393]   groups: 01 02
[   68.616398] CPU1 attaching sched-domain:
[   68.616401]  domain 0: span 03
[   68.616403]   groups: 02 01
[   69.643703] Monitor-Mwait will be used to enter C-2 state
[  127.156295] usb 1-2: new full speed USB device using uhci_hcd and address 2
[  127.195584] usb 1-2: configuration #1 chosen from 1 choice
[  127.201556] scsi6 : SCSI emulation for USB Mass Storage devices
[  127.202267] usb-storage: device found at 2
[  127.202274] usb-storage: waiting for device to settle before scanning
[  127.242385] usb 1-2: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 18 ret -71
[  127.244387] usb 1-2: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 9 ret -71
[  127.246373] usb 1-2: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 32 ret -71
[  127.248375] usb 1-2: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 0 rq 3 len 0 ret -71
[  127.255361] usb 1-2: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 18 ret -71
[  127.257355] usb 1-2: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 9 ret -71
[  127.259361] usb 1-2: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 32 ret -71
[  127.261337] usb 1-2: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 0 rq 3 len 0 ret -71
[  127.300247] usb 1-2: USB disconnect, address 2
[  127.360373] usbcore: registered new interface driver usbserial
[  127.360412] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[  127.360464] usbcore: registered new interface driver usbserial_generic
[  127.360468] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial Driver core
[  127.366005] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for airprime
[  127.366033] usbcore: registered new interface driver airprime
[  127.767351] usb 1-2: new full speed USB device using uhci_hcd and address 3
[  127.808407] usb 1-2: configuration #1 chosen from 1 choice
[  127.818784] usb-storage: probe of 1-2:1.0 failed with error -5
[  127.818824] airprime 1-2:1.0: airprime converter detected
[  127.819017] usb 1-2: airprime converter now attached to ttyUSB0
[  127.819125] usb 1-2: airprime converter now attached to ttyUSB1
[  127.819227] usb 1-2: airprime converter now attached to ttyUSB2
[  127.824735] usb-storage: probe of 1-2:1.1 failed with error -5
[  127.824773] airprime 1-2:1.1: airprime converter detected
[  127.824960] usb 1-2: airprime converter now attached to ttyUSB3
[  127.825064] usb 1-2: airprime converter now attached to ttyUSB4
[  127.825165] usb 1-2: airprime converter now attached to ttyUSB5
[  127.830313] scsi9 : SCSI emulation for USB Mass Storage devices
[  127.833651] usb-storage: device found at 3
[  127.833660] usb-storage: waiting for device to settle before scanning
[  127.923101] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for GSM modem (1-port)
[  127.923342] usbcore: registered new interface driver option
[  127.923345] /build/buildd/linux-2.6.24/drivers/usb/serial/option.c: USB Driver for GSM modems: v0.7.1
[  129.193874] usb-storage: device scan complete
[  129.196855] scsi 9:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[  129.229219] sr1: scsi-1 drive
[  129.229331] sr 9:0:0:0: Attached scsi CD-ROM sr1
[  129.229408] sr 9:0:0:0: Attached scsi generic sg3 type 5
```

wvdial.conf

```
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Baud = 9600
New PPPD = yes
Modem = /dev/ttyUSB0
ISDN = 0
Phone = *99#
Password = web
Username = web
```

Cheers

---

### Post by p221072 on 2008-07-29
The device seems to be recognized correctly.
You should modify the wvdial.conf setting the Access Point with a string this:
Init3 = AT+CGDCONT=1,"IP","internet"
*internet *is the AP of Vodacom SouthAfrica, every operator defines its own, you should look for this information on the operator customer's support site
and increase the baud:
Baud = 460800
then launch the dialer
sudo wvdial
I don't think this will fix the freezing problem, but you definetly need these changes to make it work.

---

### Post by wheezy-weasel on 2008-07-29
Hi,

Above changes to wvdial.conf applied. Output follows:

```
sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","internet"
AT+CGDCONT=1,"IP","internet"
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
--> Carrier detected.  Waiting for prompt.
--> Connected, but carrier signal lost!  Retrying...
--> Sending: ATDT*99#
--> Waiting for carrier.
--> Timed out while dialing.  Trying again.
--> Sending: ATDT*99#
--> Waiting for carrier.
--> Timed out while dialing.  Trying again.
--> Sending: ATDT*99#
--> Waiting for carrier.
--> Timed out while dialing.  Trying again.
--> Sending: ATDT*99#
--> Waiting for carrier.
--> Timed out while dialing.  Trying again.
...
...
Caught signal 2:  Attempting to exit gracefully...
--> Disconnecting at Tue Jul 29 11:05:01 2008


```

---

### Post by p221072 on 2008-07-29
try to add
Carrier Check = no
and change the access point, what is your operator and country?

---

### Post by wheezy-weasel on 2008-07-29
vodafone UK

---

### Post by wheezy-weasel on 2008-07-29
Hi,

Cheers for all you help.

Some kind of progress perhaps? Getting an IP address.

```
sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","internet"
AT+CGDCONT=1,"IP","internet"
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
--> Carrier detected.  Waiting for prompt.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Tue Jul 29 13:20:29 2008
--> Pid of pppd: 15612
--> Using interface ppp0
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08] &#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08] &#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08] &#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08] &#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08] &#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08] &#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08] &#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08] &#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08] &#65533;[06][08]
--> local  IP address 10.47.46.188
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08] &#65533;[06][08]
--> remote IP address 10.64.64.64
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08] &#65533;[06][08]
--> primary   DNS address 10.203.129.68
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08] &#65533;[06][08]
--> secondary DNS address 10.203.129.68
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08] &#65533;[06][08]

```

Have solid blue light on modem.
Unfortunately not loading pages though.

---

### Post by wheezy-weasel on 2008-07-29
How to stop wvdial/pppd?

Ignore above request.
^C

---

### Post by Sealbhach on 2008-07-29
When I had my Huawei E220, I used Gnome-PPP. It's a GUI dial-up modem inteface.

Works very well.

```
sudo apt-get install gnome-ppp
```

Is your modem connecting to the interweb now?


.

---

### Post by wheezy-weasel on 2008-07-29
Hi,

I have installed and tried gnome-ppp

Output from log:

```
--> Ignoring malformed input line: ";Do NOT edit this file by hand!"
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATM1L3DT*99#
--> Waiting for carrier.
ATM1L3DT*99#
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Tue Jul 29 13:49:02 2008
--> Pid of pppd: 17314
--> Using interface ppp0
--> local  IP address 10.49.119.99
--> remote IP address 10.64.64.64
--> primary   DNS address 10.203.65.68
--> secondary DNS address 10.203.65.68
```

Not loading pages.
Tried to ping google by name and by IP - network unreachable.

---

### Post by wheezy-weasel on 2008-07-29
Hi,

I just rebooted and tried again with gnome-pppd and it connected immediately and I could ping  google, however I still could not display any pages in my browser.

Obviously I'm now just doing something very stupid. Any advice for the simpleton :)

Cheers,

---

### Post by p221072 on 2008-07-29
This is what I found for the AP ([here]("http://www.filesaveas.com/gprs.html")):
Access Point (APN) address : internet (Contract)
Access Point (APN) address : pp.vodafone.co.uk(PAYG)
Looking at the stream it seems you are connected! Just leave the terminal open in background and as you already found out, press ^C to close the connection.

---

### Post by wheezy-weasel on 2008-07-29
Thanks P221072 - I am replying connected via wvdial!

Solved.

Cheers

---

### Post by p221072 on 2008-07-29
I'm happy you made it!
Please mark the thread as SOLVED from the Thread Tools link in the upper right side of the page, this might help other people.
Cheers
Paolo

---

### Post by wheezy-weasel on 2008-07-30
Ok, I know I marked this solved, however, I brought my ubuntu box into work today and just tried to connect with wvdial as before, and it just keeps repeating 'carrier not found'.

I have just re-tested the modem on my xp box and it worked fine.

Any suggestions?

Update:

I have just tried again at home and the modem connected first time - I am using it now. Can't understand why it didn't work earlier, in the centre of London, when it worked fine on xp box.

---

### Post by Sealbhach on 2008-07-31
> **wheezy-weasel said:**
> 
I have just tried again at home and the modem connected first time - I am using it now. Can't understand why it didn't work earlier, in the centre of London, when it worked fine on xp box.

Weird.:confused:


.

---

### Post by wheezy-weasel on 2008-07-31
Weird is right - I have brought laptop into work to test again and this time, after several attempts it connected on 3g ok.

Will accept temperamental nature of this beast and shut up now.

Cheers

---

### Post by wheezy-weasel on 2008-07-31
I have had some help from the betavine forums, in this [thread]("http://www.betavine.net/bvportal/auth/forums/index.html?threadId=ff8080811b2fbbfd011b63d3ccd6245f").

In essence, it seems there is a driver conflict. The steps taken to  overcome it were:

```
sudo echo "blacklist airprime" > /etc/modprobe.d/blacklist-airprime
```

Then reboot.

Remove the ~/.vmc2 directory

Run vodafone-mobile-connect-card-driver-for-linux again

He presto, it works (sometimes... other times doesn't get nameserver?)

---

### Post by mundo on 2008-08-03
Hi,

I have the same issues with the E172 Vodafone Stick but have not yet been successful in getting this to work.  I have followed this thread and tried out all the suggestions so I was wondering if you could post your current wvdial.conf file so that I can check this against mine.

I have another thread open over at [http://ubuntuforums.org/showthread.php?p=5515804#post5515804]("http://ubuntuforums.org/showthread.php?p=5515804#post5515804")

---

### Post by monkley on 2008-08-07
I wanted to report back that the Huwei E172 is auto detected and connects with default settings to Vodafone UK UMTS HSDPA mobile broadband if you install the latest network manager

See here for instructions
[http://ubuntuforums.org/showthread.php?t=797059](http://ubuntuforums.org/showthread.php?t=797059)

Perhaps someone can change the subject of this thread to solved

---

### Post by wheezy-weasel on 2008-08-07
> **monkley said:**
> I wanted to report back that the Huwei E172 is auto detected and connects with default settings to Vodafone UK UMTS HSDPA mobile broadband if you install the latest network manager

See here for instructions
[http://ubuntuforums.org/showthread.php?t=797059](http://ubuntuforums.org/showthread.php?t=797059)

Perhaps someone can change the subject of this thread to solved

Thanks for the update.

Thread marked solved.

---

