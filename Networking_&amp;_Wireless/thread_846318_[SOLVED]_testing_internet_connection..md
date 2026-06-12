---
title: "[SOLVED] testing internet connection."
date: 2008-07-01
forum: Networking &amp; Wireless
---

### Post by Louis de Broglie on 2008-07-01
Hello,

I would like to test if my internet is configured properly as the speed is slower than it was in windows. I am using realtake network adapter and my connection is wired connection.

---

### Post by pytheas22 on 2008-07-01
What is the output of these commands:
```

ifconfig
lspci
```

and how much slower is it?  i.e. is it unbearably slow, or does it just "feel" slower than it was in Windows?  Are you unable to get the same download and upload speeds that you see in Windows (I mean concrete numbers, not just what seems to be faster or slower)?  Is it only the web that's slow, or other services too (like ftp, instant messaging, ssh)?  It could also be your web browser that's rendering slowly for some reason; have you tried using a different browser?

---

### Post by Louis de Broglie on 2008-07-01
Output of ifconfig :
> 
eth0      Link encap:Ethernet  HWaddr 00:1d:0f:0e:12:82  
          inet addr:192.168.100.59  Bcast:192.168.100.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:59455 errors:4 dropped:0 overruns:0 frame:0
          TX packets:19651 errors:0 dropped:0 overruns:0 carrier:0
          collisions:1637 txqueuelen:1000 
          RX bytes:39394850 (37.5 MB)  TX bytes:1772845 (1.6 MB)
          Interrupt:21 Base address:0xc800 

eth1      Link encap:Ethernet  HWaddr 00:1b:fc:cb:e3:43  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:dffc0000-e0000000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1600 (1.5 KB)  TX bytes:1600 (1.5 KB)


Output of lspci:

> 
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 Multimedia audio controller: Creative Labs SB Audigy LS
01:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:00.0 Ethernet controller: Attansic Technology Corp. L2 100 Mbit Ethernet Adapter (rev a0)



Well, I used to get ~20 kbps in windows and in ubuntu in varies a lot (from 0 to 30 kbps). And sometimes it becomes totally 0 for quite some time.:(

And not to mention that, I can download packages with synaptic( speed mentioned above ). But firefox loads page then says done but shows nothing but a blank white page:(. Sometimes firefox works though.:)

I did not try any other web browsers.

---

### Post by pytheas22 on 2008-07-01
First of all, it looks like you have two ethernet cards (with different chipsets but similar MAC addresses, which is weird).  If you plug into the second one, do you have the same speed problems?
> 
Well, I used to get ~20 kbps in windows and in ubuntu in varies a lot (from 0 to 30 kbps). And sometimes it becomes totally 0 for quite some time.

From this it sounds like the card may be flaking out for some reason.  The next time your connection speed starts dropping down to 0, please run the command:
```

dmesg
```

and post the output here.  If the driver or interface is crashing for some reason, dmesg should tell more about it.

---

### Post by Louis de Broglie on 2008-07-01
Yes, I am using eth0. My isp recommended that one.

Quite a lot of output ::)

> 
[    0.000000] Linux version 2.6.24-16-generic (buildd@yellow) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 12:47:45 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
[    0.000000] Command line: root=UUID=270e04b2-c2e8-41cf-9510-e7ed223361af ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f7a0000 (usable)
[    0.000000]  BIOS-e820: 000000003f7a0000 - 000000003f7ae000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003f7ae000 - 000000003f7e0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f7e0000 - 000000003f800000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 260000) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000FB040 checksum 0
[    0.000000] ACPI: RSDP 000FB040, 0024 (r2 ACPIAM)
[    0.000000] ACPI: XSDT 3F7A0100, 0054 (r1 &#65533;&#65533;&#65533;&#65533;&#65533;&#65533; &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;  5000721 MSFT       97)
[    0.000000] ACPI: FACP 3F7A0290, 00F4 (r3 A_M_I_ OEMFACP   5000721 MSFT       97)
[    0.000000] ACPI: DSDT 3F7A05C0, 682B (r1  A0798 A0798000        0 INTL 20051117)
[    0.000000] ACPI: FACS 3F7AE000, 0040
[    0.000000] ACPI: APIC 3F7A0390, 006C (r1 A_M_I_ OEMAPIC   5000721 MSFT       97)
[    0.000000] ACPI: MCFG 3F7A0400, 003C (r1 A_M_I_ OEMMCFG   5000721 MSFT       97)
[    0.000000] ACPI: SLIC 3F7A0440, 0176 (r1 &#65533;&#65533;&#65533;&#65533;&#65533;&#65533; &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;  5000721 MSFT       97)
[    0.000000] ACPI: OEMB 3F7AE040, 0080 (r1 A_M_I_ AMI_OEM   5000721 MSFT       97)
[    0.000000] ACPI: HPET 3F7A6DF0, 0038 (r1 A_M_I_ OEMHPET   5000721 MSFT       97)
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000003f7a0000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 260000) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000003f7a0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   260000
[    0.000000] On node 0 totalpages: 259903
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1207 pages reserved
[    0.000000]   DMA zone: 2736 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 3498 pages used for memmap
[    0.000000]   DMA32 zone: 252406 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e4000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3f800000:c0780000)
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 255142
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=UUID=270e04b2-c2e8-41cf-9510-e7ed223361af ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] hpet clockevent registered
[    0.000000] TSC calibrated against HPET
[   20.240942] time.c: Detected 1599.979 MHz processor.
[   20.242047] Console: colour VGA+ 80x25
[   20.242051] console [tty0] enabled
[   20.242070] Checking aperture...
[   20.242081] Calgary: detecting Calgary via BIOS EBDA area
[   20.242084] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[   20.255551] Memory: 1012100k/1040000k available (2466k kernel code, 27512k reserved, 1309k data, 316k init)
[   20.255595] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=4, Nodes=1
[   20.334928] Calibrating delay using timer specific routine.. 3202.51 BogoMIPS (lpj=6405032)
[   20.334969] Security Framework initialized
[   20.334977] SELinux:  Disabled at boot.
[   20.334991] AppArmor: AppArmor initialized
[   20.334995] Failure registering capabilities with primary security module.
[   20.335140] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   20.335894] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[   20.336340] Mount-cache hash table entries: 256
[   20.336535] CPU: L1 I cache: 32K, L1 D cache: 32K
[   20.336539] CPU: L2 cache: 1024K
[   20.336541] CPU 0/0 -> Node 0
[   20.336543] using mwait in idle threads.
[   20.336545] CPU: Physical Processor ID: 0
[   20.336547] CPU: Processor Core ID: 0
[   20.336555] CPU0: Thermal monitoring enabled (TM2)
[   20.336571] SMP alternatives: switching to UP code
[   20.337490] Early unpacking initramfs... done
[   20.797136] ACPI: Core revision 20070126
[   20.797190] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   20.840575] Using local APIC timer interrupts.
[   20.903080] APIC timer calibration result 12499829
[   20.903082] Detected 12.499 MHz APIC timer.
[   20.903171] SMP alternatives: switching to SMP code
[   20.903966] Booting processor 1/2 APIC 0x1
[   20.914180] Initializing CPU#1
[   20.991085] Calibrating delay using timer specific routine.. 3199.98 BogoMIPS (lpj=6399960)
[   20.991093] CPU: L1 I cache: 32K, L1 D cache: 32K
[   20.991094] CPU: L2 cache: 1024K
[   20.991097] CPU 1/1 -> Node 0
[   20.991098] CPU: Physical Processor ID: 0
[   20.991100] CPU: Processor Core ID: 1
[   20.991106] CPU1: Thermal monitoring enabled (TM2)
[   20.991348] Intel(R) Pentium(R) Dual  CPU  E2140  @ 1.60GHz stepping 0d
[   20.991395] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   21.011426] Brought up 2 CPUs
[   21.011505] CPU0 attaching sched-domain:
[   21.011508]  domain 0: span 03
[   21.011509]   groups: 01 02
[   21.011512]   domain 1: span 03
[   21.011514]    groups: 03
[   21.011516] CPU1 attaching sched-domain:
[   21.011518]  domain 0: span 03
[   21.011520]   groups: 02 01
[   21.011522]   domain 1: span 03
[   21.011524]    groups: 03
[   21.011774] net_namespace: 120 bytes
[   21.012203] Time: 17:35:00  Date: 07/01/08
[   21.012234] NET: Registered protocol family 16
[   21.012452] ACPI: bus type pci registered
[   21.012536] PCI: Using configuration type 1
[   21.015952] ACPI: EC: Look up EC in DSDT
[   21.021627] ACPI: Interpreter enabled
[   21.021631] ACPI: (supports S0 S1 S3 S4 S5)
[   21.021649] ACPI: Using IOAPIC for interrupt routing
[   21.030070] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   21.030663] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[   21.030667] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
[   21.031240] PCI: Transparent bridge - 0000:00:1e.0
[   21.031269] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   21.031452] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[   21.031576] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[   21.031675] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[   21.034396] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   21.034535] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   21.034671] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 *6 7 10 11 12 14 15)
[   21.034806] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   21.034942] ACPI: PCI Interrupt Link [LNKE] (IRQs *3 4 5 6 7 10 11 12 14 15)
[   21.035077] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   21.035260] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   21.035397] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   21.035564] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] -  6C, should be 67 [20070126]
[   21.035573] Linux Plug and Play Support v0.97 (c) Adam Belay
[   21.035607] pnp: PnP ACPI init
[   21.035615] ACPI: bus type pnp registered
[   21.040297] pnp: PnP ACPI: found 18 devices
[   21.040301] ACPI: ACPI bus type pnp unregistered
[   21.040571] PCI: Using ACPI for IRQ routing
[   21.040573] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   21.051212] NET: Registered protocol family 8
[   21.051215] NET: Registered protocol family 20
[   21.051265] PCI-GART: No AMD northbridge found.
[   21.051271] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   21.051276] hpet0: 3 64-bit timers, 14318180 Hz
[   21.052322] AppArmor: AppArmor Filesystem Enabled
[   21.055144] Time: tsc clocksource has been installed.
[   21.055159] Switched to high resolution mode on CPU 0
[   21.055485] Switched to high resolution mode on CPU 1
[   21.063182] system 00:01: iomem range 0xfed13000-0xfed19fff has been reserved
[   21.063196] system 00:07: ioport range 0x290-0x297 has been reserved
[   21.063204] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   21.063208] system 00:08: ioport range 0x800-0x87f has been reserved
[   21.063212] system 00:08: ioport range 0x480-0x4bf has been reserved
[   21.063215] system 00:08: ioport range 0x900-0x91f has been reserved
[   21.063221] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[   21.063224] system 00:08: iomem range 0xfed20000-0xfed8ffff has been reserved
[   21.063228] system 00:08: iomem range 0xffb00000-0xffbfffff has been reserved
[   21.063237] system 00:08: iomem range 0xfff00000-0xffffffff could not be reserved
[   21.063245] system 00:0c: iomem range 0xfec00000-0xfec00fff has been reserved
[   21.063248] system 00:0c: iomem range 0xfee00000-0xfee00fff could not be reserved
[   21.063256] system 00:0f: iomem range 0xffc00000-0xfff7ffff has been reserved
[   21.063262] system 00:10: iomem range 0xf0000000-0xf3ffffff has been reserved
[   21.063268] system 00:11: iomem range 0x0-0x9ffff could not be reserved
[   21.063271] system 00:11: iomem range 0xc0000-0xdffff has been reserved
[   21.063274] system 00:11: iomem range 0xe0000-0xfffff could not be reserved
[   21.063276] system 00:11: iomem range 0x100000-0x3f7fffff could not be reserved
[   21.063279] system 00:11: iomem range 0x0-0x0 could not be reserved
[   21.063728] PCI: Bridge: 0000:00:1c.0
[   21.063731]   IO window: e000-efff
[   21.063736]   MEM window: disabled.
[   21.063739]   PREFETCH window: disabled.
[   21.063744] PCI: Bridge: 0000:00:1c.1
[   21.063746]   IO window: d000-dfff
[   21.063750]   MEM window: dff00000-dfffffff
[   21.063754]   PREFETCH window: disabled.
[   21.063761] PCI: Bridge: 0000:00:1e.0
[   21.063763]   IO window: c000-cfff
[   21.063767]   MEM window: dfe00000-dfefffff
[   21.063771]   PREFETCH window: disabled.
[   21.063800] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   21.063806] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   21.063824] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
[   21.063829] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   21.063839] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   21.063851] NET: Registered protocol family 2
[   21.099246] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[   21.099745] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[   21.101247] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   21.102079] TCP: Hash tables configured (established 131072 bind 65536)
[   21.102083] TCP reno registered
[   21.111364] checking if image is initramfs... it is
[   22.016664] Freeing initrd memory: 8209k freed
[   22.022337] audit: initializing netlink socket (disabled)
[   22.022363] audit(1214933701.708:1): initialized
[   22.024616] VFS: Disk quotas dquot_6.5.1
[   22.024694] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   22.024831] io scheduler noop registered
[   22.024833] io scheduler anticipatory registered
[   22.024835] io scheduler deadline registered
[   22.024948] io scheduler cfq registered (default)
[   22.024962] Boot video device is 0000:00:02.0
[   22.025820] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   22.025861] assign_interrupt_mode Found MSI capability
[   22.025896] Allocate Port Service[0000:00:1c.0:pcie00]
[   22.025932] Allocate Port Service[0000:00:1c.0:pcie02]
[   22.026013] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   22.026051] assign_interrupt_mode Found MSI capability
[   22.026083] Allocate Port Service[0000:00:1c.1:pcie00]
[   22.053557] Real Time Clock Driver v1.12ac
[   22.053767] hpet_resources: 0xfed00000 is busy
[   22.053809] Linux agpgart interface v0.102
[   22.053812] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   22.053944] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   22.054647] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   22.055409] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   22.055478] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   22.055592] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   22.058302] serio: i8042 KBD port at 0x60,0x64 irq 1
[   22.058307] serio: i8042 AUX port at 0x60,0x64 irq 12
[   22.075675] mice: PS/2 mouse device common for all mice
[   22.075723] cpuidle: using governor ladder
[   22.075725] cpuidle: using governor menu
[   22.075887] NET: Registered protocol family 1
[   22.075948] registered taskstats version 1
[   22.076061]   Magic number: 0:911:591
[   22.076113]   hash matches device ptyc9
[   22.076188] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   22.076191] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   22.076193] EDD information not available.
[   22.076203] Freeing unused kernel memory: 316k freed
[   22.094803] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   23.297363] fuse init (API version 7.9)
[   23.318651] ACPI: SSDT 3F7AE0C0, 01D2 (r1    AMI   CPU1PM        1 INTL 20060113)
[   23.319185] ACPI: Processor [CPU1] (supports 8 throttling states)
[   23.319368] ACPI: SSDT 3F7AE2A0, 0143 (r1    AMI   CPU2PM        1 INTL 20060113)
[   23.319881] ACPI: Processor [CPU2] (supports 8 throttling states)
[   23.319899] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   23.319911] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   23.630475] usbcore: registered new interface driver usbfs
[   23.630499] usbcore: registered new interface driver hub
[   23.630525] usbcore: registered new device driver usb
[   23.631375] USB Universal Host Controller Interface driver v3.0
[   23.631428] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 20
[   23.631439] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   23.631443] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   23.631694] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   23.631726] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00009000
[   23.631856] usb usb1: configuration #1 chosen from 1 choice
[   23.631879] hub 1-0:1.0: USB hub found
[   23.631885] hub 1-0:1.0: 2 ports detected
[   23.678040] SCSI subsystem initialized
[   23.726339] 8139too Fast Ethernet driver 0.9.28
[   23.726442] libata version 3.00 loaded.
[   23.735566] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 17
[   23.735579] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   23.735583] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   23.735609] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   23.735640] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00009400
[   23.735751] usb usb2: configuration #1 chosen from 1 choice
[   23.735772] hub 2-0:1.0: USB hub found
[   23.735778] hub 2-0:1.0: 2 ports detected
[   23.839610] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   23.839624] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   23.839628] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   23.839658] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   23.839689] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00009800
[   23.839811] usb usb3: configuration #1 chosen from 1 choice
[   23.839836] hub 3-0:1.0: USB hub found
[   23.839842] hub 3-0:1.0: 2 ports detected
[   23.943559] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 19
[   23.943572] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   23.943576] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   23.943603] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   23.943630] uhci_hcd 0000:00:1d.3: irq 19, io base 0x0000a000
[   23.943739] usb usb4: configuration #1 chosen from 1 choice
[   23.943762] hub 4-0:1.0: USB hub found
[   23.943767] hub 4-0:1.0: 2 ports detected
[   24.047606] ACPI: PCI Interrupt 0000:01:01.0[A] -> GSI 21 (level, low) -> IRQ 21
[   24.048355] eth0: RealTek RTL8139 at 0xc800, 00:1d:0f:0e:12:82, IRQ 21
[   24.048358] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   24.052262] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 20
[   24.052565] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   24.052572] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   24.052622] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   24.056550] ehci_hcd 0000:00:1d.7: debug port 1
[   24.056558] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   24.056568] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xdfdffc00
[   24.060501] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   24.070935] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   24.071077] usb usb5: configuration #1 chosen from 1 choice
[   24.071103] hub 5-0:1.0: USB hub found
[   24.071111] hub 5-0:1.0: 8 ports detected
[   24.175315] ata_piix 0000:00:1f.1: version 2.12
[   24.175346] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 22 (level, low) -> IRQ 22
[   24.175393] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   24.175960] scsi0 : ata_piix
[   24.176028] scsi1 : ata_piix
[   24.177486] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   24.177491] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   24.931776] ata1.00: ATAPI: ASUS DVD-ROM DVD-E616P              0104, E1.04, max UDMA/66
[   24.931797] ata1.01: ATAPI: ASUS    CRW-5232AS, 1.0, max UDMA/33
[   25.103193] ata1.00: configured for UDMA/66
[   25.267754] ata1.01: configured for UDMA/33
[   25.435770] scsi 0:0:0:0: CD-ROM            ASUS     DVD-E616P        1.04 PQ: 0 ANSI: 5
[   25.436634] scsi 0:0:1:0: CD-ROM            ASUS     CRW-5232AS       1.0  PQ: 0 ANSI: 5
[   25.436718] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   25.436762] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 23 (level, low) -> IRQ 23
[   25.436793] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   25.437108] scsi2 : ata_piix
[   25.437270] scsi3 : ata_piix
[   25.438579] ata3: SATA max UDMA/133 cmd 0xb800 ctl 0xb400 bmdma 0xa400 irq 23
[   25.438582] ata4: SATA max UDMA/133 cmd 0xb000 ctl 0xa800 bmdma 0xa408 irq 23
[   25.599143] ata3.00: ATA-7: SAMSUNG HD160JJ, ZM100-47, max UDMA7
[   25.599149] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   25.631132] ata3.00: configured for UDMA/133
[   25.798193] scsi 2:0:0:0: Direct-Access     ATA      SAMSUNG HD160JJ  ZM10 PQ: 0 ANSI: 5
[   25.807067] Driver 'sr' needs updating - please use bus_type methods
[   25.813769] sr0: scsi3-mmc drive: 24x/24x cd/rw xa/form2 cdda tray
[   25.813774] Uniform CD-ROM driver Revision: 3.20
[   25.813827] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   25.814167] Driver 'sd' needs updating - please use bus_type methods
[   25.816468] sr1: scsi3-mmc drive: 52x/52x writer cd/rw xa/form2 cdda tray
[   25.816532] sr 0:0:1:0: Attached scsi CD-ROM sr1
[   25.819432] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   25.819447] sd 2:0:0:0: [sda] Write Protect is off
[   25.819450] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   25.819467] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   25.819521] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   25.819538] sd 2:0:0:0: [sda] Write Protect is off
[   25.819540] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   25.819559] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   25.819563]  sda:<5>sr 0:0:0:0: Attached scsi generic sg0 type 5
[   25.821090] sr 0:0:1:0: Attached scsi generic sg1 type 5
[   25.821110] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   25.834052]  sda1 sda2 < sda5 sda6 sda7 sda8 > sda3
[   25.886487] sd 2:0:0:0: [sda] Attached SCSI disk
[   26.229430] Attempting manual resume
[   26.229434] swsusp: Resume From Partition 8:3
[   26.229435] PM: Checking swsusp image.
[   26.229636] PM: Resume from disk failed.
[   26.264761] kjournald starting.  Commit interval 5 seconds
[   26.264783] EXT3-fs: mounted filesystem with ordered data mode.
[   31.735570] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   31.792059] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   31.935068] iTCO_vendor_support: vendor-support=0
[   31.970937] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   31.971051] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, TCOBASE=0x0860)
[   31.971083] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   32.018980] agpgart: Detected an Intel 945G Chipset.
[   32.019543] agpgart: Detected 7932K stolen memory.
[   32.034358] agpgart: AGP aperture is 256M @ 0xe0000000
[   32.063019] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   32.186258] intel_rng: FWH not detected
[   32.246998] parport_pc 00:06: reported by Plug and Play ACPI
[   32.247110] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   32.361144] input: Power Button (FF) as /devices/virtual/input/input3
[   32.378864] ACPI: Power Button (FF) [PWRF]
[   32.378979] input: Power Button (CM) as /devices/virtual/input/input4
[   32.410892] ACPI: Power Button (CM) [PWRB]
[   32.658930] Attansic(R) L2 Ethernet Network Driver - version 1.0.40.2
[   32.658934] Copyright (c) 2006 Attansic Corporation.
[   32.659010] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   32.659022] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   32.970699] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   32.970720] snd-ca0106: Model 1012 Rev 00000000 Serial 10121102
[   33.054428] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 19 (level, low) -> IRQ 19
[   33.054731] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   33.080153] hda_codec: Unknown model for ALC662, trying auto-probe from BIOS...
[   34.010797] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input5
[   36.139059] lp0: using parport0 (interrupt-driven).
[   36.223150] Adding 1646652k swap on /dev/sda3.  Priority:-1 extents:1 across:1646652k
[   36.769468] EXT3 FS on sda1, internal journal
[   37.865180] ip_tables: (C) 2000-2006 Netfilter Core Team
[   38.225415] No dock devices found.
[   39.359693] ppdev: user-space parallel port driver
[   39.486540] audit(1214933719.422:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5006 profile="/usr/sbin/cupsd" namespace="default"
[   40.476932] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[   40.591204] Bluetooth: Core ver 2.11
[   40.591326] NET: Registered protocol family 31
[   40.591329] Bluetooth: HCI device and connection manager initialized
[   40.591335] Bluetooth: HCI socket layer initialized
[   40.603356] Bluetooth: L2CAP ver 2.9
[   40.603362] Bluetooth: L2CAP socket layer initialized
[   40.642995] Bluetooth: RFCOMM socket layer initialized
[   40.643015] Bluetooth: RFCOMM TTY layer initialized
[   40.643018] Bluetooth: RFCOMM ver 1.8
[   43.335028] [drm] Initialized drm 1.1.0 20060810
[   43.338936] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   43.338949] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   43.339062] [drm] Initialized i915 1.6.0 20060119 on minor 0



---

### Post by pytheas22 on 2008-07-01
Thanks for all the information.  I'm not positive, but I'm wondering if maybe your second ethernet card is interfering with the first.  Try this, which should make the second ethernet device become invisible to your computer:
```

sudo ifconfig eth0 down
sudo ifconfig eth1 down
sudo rmmod atl1
sudo rmmod atl2
sudo ifconfig eth0 up
```

then please see if the problem is still occurring.
> 
Yes, I am using eth0. My isp recommended that one.

That's fine, but have you tried using eth1 temporarily to see if you still have speed problems?  This would at least help to narrow down the source of the problem--if it only occurs with eth0, then we know it's something specific to that device, not the system in general.

---

### Post by Louis de Broglie on 2008-07-01
I typed those codes u mentioned. 

sudo rmmod atl1 gave me an error message. Then i made a reboot as after that whatever i typed in firefox, i received no connection.

Now everything is so far faster than windows.:D

Let's just hope the problem is over.:)

Thank you for your support.

P.S. I have also tried the other card before ( same problems persisted )

---

### Post by pytheas22 on 2008-07-01
Actually those commands shouldn't have fixed anything permanently...after a reboot you should be back to where you were.  So if the problem does occur again, please let me know.  But let's hope it really has just disappeared.

---

### Post by Louis de Broglie on 2008-07-03
Yes, it happened again. and what's worst that i had to install windows to connect to the internet.:(

I removed eth0 card from pci slot. Then tried to use the one with motherboard but that one did not even gave me any ping:(( i click ping on network tools, nothing happens:confused:(not even trying to request)).

Then i installed the eth0 card in pci slot again and in windows, the internet works. in ubuntu it does not.:(

Please help. i don't like using windows.

---

### Post by Louis de Broglie on 2008-07-03
Ok. I reinstalled ubuntu. And the first thing I did was :

sudo ifconfig eth1 down

And this gives me stable internet connection. So should i keep doing this every time i start my pc?

Is there any method to completely turn eth1 off?:)

---

### Post by pytheas22 on 2008-07-03
You may be able to disable eth1 in your system BIOS (i.e., there might be an option to disable the onboard LAN controller).  Otherwise, if you post the output of:
```

lshw -C Network
```

it will say which driver eth1 is using.  Then you can blacklist that driver and eth1 should no longer exist in Ubuntu.

---

### Post by Louis de Broglie on 2008-07-03
Well, I have just experienced no internet. And now it came back to life.
As you said, I am pasting the output of dmesg now. Hope this will help find the source of the problem.

> 
3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 12:47:45 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
[    0.000000] Command line: root=UUID=546ad748-84e7-4a31-aa81-04a864af7ce0 ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f7a0000 (usable)
[    0.000000]  BIOS-e820: 000000003f7a0000 - 000000003f7ae000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003f7ae000 - 000000003f7e0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f7e0000 - 000000003f800000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 260000) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000FB040 checksum 0
[    0.000000] ACPI: RSDP 000FB040, 0024 (r2 ACPIAM)
[    0.000000] ACPI: XSDT 3F7A0100, 0054 (r1 &#65533;&#65533;&#65533;&#65533;&#65533;&#65533; &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;  5000721 MSFT       97)
[    0.000000] ACPI: FACP 3F7A0290, 00F4 (r3 A_M_I_ OEMFACP   5000721 MSFT       97)
[    0.000000] ACPI: DSDT 3F7A05C0, 682B (r1  A0798 A0798000        0 INTL 20051117)
[    0.000000] ACPI: FACS 3F7AE000, 0040
[    0.000000] ACPI: APIC 3F7A0390, 006C (r1 A_M_I_ OEMAPIC   5000721 MSFT       97)
[    0.000000] ACPI: MCFG 3F7A0400, 003C (r1 A_M_I_ OEMMCFG   5000721 MSFT       97)
[    0.000000] ACPI: SLIC 3F7A0440, 0176 (r1 &#65533;&#65533;&#65533;&#65533;&#65533;&#65533; &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;  5000721 MSFT       97)
[    0.000000] ACPI: OEMB 3F7AE040, 0080 (r1 A_M_I_ AMI_OEM   5000721 MSFT       97)
[    0.000000] ACPI: HPET 3F7A6DF0, 0038 (r1 A_M_I_ OEMHPET   5000721 MSFT       97)
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000003f7a0000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 260000) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000003f7a0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   260000
[    0.000000] On node 0 totalpages: 259903
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1207 pages reserved
[    0.000000]   DMA zone: 2736 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 3498 pages used for memmap
[    0.000000]   DMA32 zone: 252406 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e4000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3f800000:c0780000)
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 255142
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=UUID=546ad748-84e7-4a31-aa81-04a864af7ce0 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] hpet clockevent registered
[    0.000000] TSC calibrated against HPET
[   20.163158] time.c: Detected 1599.980 MHz processor.
[   20.164263] Console: colour VGA+ 80x25
[   20.164267] console [tty0] enabled
[   20.164286] Checking aperture...
[   20.164296] Calgary: detecting Calgary via BIOS EBDA area
[   20.164298] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[   20.177765] Memory: 1012104k/1040000k available (2466k kernel code, 27508k reserved, 1309k data, 316k init)
[   20.177808] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=4, Nodes=1
[   20.257143] Calibrating delay using timer specific routine.. 3202.52 BogoMIPS (lpj=6405055)
[   20.257184] Security Framework initialized
[   20.257192] SELinux:  Disabled at boot.
[   20.257207] AppArmor: AppArmor initialized
[   20.257211] Failure registering capabilities with primary security module.
[   20.257356] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   20.258112] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[   20.258559] Mount-cache hash table entries: 256
[   20.258751] CPU: L1 I cache: 32K, L1 D cache: 32K
[   20.258754] CPU: L2 cache: 1024K
[   20.258757] CPU 0/0 -> Node 0
[   20.258759] using mwait in idle threads.
[   20.258761] CPU: Physical Processor ID: 0
[   20.258763] CPU: Processor Core ID: 0
[   20.258770] CPU0: Thermal monitoring enabled (TM2)
[   20.258787] SMP alternatives: switching to UP code
[   20.259706] Early unpacking initramfs... done
[   20.719884] ACPI: Core revision 20070126
[   20.719941] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   20.763327] Using local APIC timer interrupts.
[   20.825832] APIC timer calibration result 12499840
[   20.825833] Detected 12.499 MHz APIC timer.
[   20.825924] SMP alternatives: switching to SMP code
[   20.826723] Booting processor 1/2 APIC 0x1
[   20.836918] Initializing CPU#1
[   20.913837] Calibrating delay using timer specific routine.. 3199.99 BogoMIPS (lpj=6399984)
[   20.913845] CPU: L1 I cache: 32K, L1 D cache: 32K
[   20.913846] CPU: L2 cache: 1024K
[   20.913849] CPU 1/1 -> Node 0
[   20.913850] CPU: Physical Processor ID: 0
[   20.913852] CPU: Processor Core ID: 1
[   20.913859] CPU1: Thermal monitoring enabled (TM2)
[   20.914099] Intel(R) Pentium(R) Dual  CPU  E2140  @ 1.60GHz stepping 0d
[   20.914151] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   20.934182] Brought up 2 CPUs
[   20.934261] CPU0 attaching sched-domain:
[   20.934264]  domain 0: span 03
[   20.934266]   groups: 01 02
[   20.934269]   domain 1: span 03
[   20.934270]    groups: 03
[   20.934273] CPU1 attaching sched-domain:
[   20.934275]  domain 0: span 03
[   20.934276]   groups: 02 01
[   20.934279]   domain 1: span 03
[   20.934280]    groups: 03
[   20.934532] net_namespace: 120 bytes
[   20.934964] Time: 15:51:34  Date: 07/03/08
[   20.934996] NET: Registered protocol family 16
[   20.935210] ACPI: bus type pci registered
[   20.935294] PCI: Using configuration type 1
[   20.938712] ACPI: EC: Look up EC in DSDT
[   20.944388] ACPI: Interpreter enabled
[   20.944391] ACPI: (supports S0 S1 S3 S4 S5)
[   20.944410] ACPI: Using IOAPIC for interrupt routing
[   20.952852] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   20.953451] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[   20.953455] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
[   20.954026] PCI: Transparent bridge - 0000:00:1e.0
[   20.954057] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   20.954239] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[   20.954362] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[   20.954462] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[   20.957186] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   20.957324] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   20.957460] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 *6 7 10 11 12 14 15)
[   20.957596] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   20.957733] ACPI: PCI Interrupt Link [LNKE] (IRQs *3 4 5 6 7 10 11 12 14 15)
[   20.957913] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   20.958050] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   20.958186] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   20.958354] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] -  6C, should be 67 [20070126]
[   20.958363] Linux Plug and Play Support v0.97 (c) Adam Belay
[   20.958396] pnp: PnP ACPI init
[   20.958405] ACPI: bus type pnp registered
[   20.963085] pnp: PnP ACPI: found 18 devices
[   20.963089] ACPI: ACPI bus type pnp unregistered
[   20.963357] PCI: Using ACPI for IRQ routing
[   20.963360] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   20.973960] NET: Registered protocol family 8
[   20.973963] NET: Registered protocol family 20
[   20.974015] PCI-GART: No AMD northbridge found.
[   20.974020] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   20.974024] hpet0: 3 64-bit timers, 14318180 Hz
[   20.975070] AppArmor: AppArmor Filesystem Enabled
[   20.977896] Time: tsc clocksource has been installed.
[   20.977910] Switched to high resolution mode on CPU 0
[   20.978242] Switched to high resolution mode on CPU 1
[   20.985933] system 00:01: iomem range 0xfed13000-0xfed19fff has been reserved
[   20.985946] system 00:07: ioport range 0x290-0x297 has been reserved
[   20.985955] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   20.985959] system 00:08: ioport range 0x800-0x87f has been reserved
[   20.985962] system 00:08: ioport range 0x480-0x4bf has been reserved
[   20.985966] system 00:08: ioport range 0x900-0x91f has been reserved
[   20.985970] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[   20.985974] system 00:08: iomem range 0xfed20000-0xfed8ffff has been reserved
[   20.985977] system 00:08: iomem range 0xffb00000-0xffbfffff has been reserved
[   20.985987] system 00:08: iomem range 0xfff00000-0xffffffff could not be reserved
[   20.985996] system 00:0c: iomem range 0xfec00000-0xfec00fff has been reserved
[   20.985999] system 00:0c: iomem range 0xfee00000-0xfee00fff could not be reserved
[   20.986007] system 00:0f: iomem range 0xffc00000-0xfff7ffff has been reserved
[   20.986012] system 00:10: iomem range 0xf0000000-0xf3ffffff has been reserved
[   20.986018] system 00:11: iomem range 0x0-0x9ffff could not be reserved
[   20.986021] system 00:11: iomem range 0xc0000-0xdffff has been reserved
[   20.986024] system 00:11: iomem range 0xe0000-0xfffff could not be reserved
[   20.986027] system 00:11: iomem range 0x100000-0x3f7fffff could not be reserved
[   20.986029] system 00:11: iomem range 0x0-0x0 could not be reserved
[   20.986482] PCI: Bridge: 0000:00:1c.0
[   20.986484]   IO window: e000-efff
[   20.986489]   MEM window: disabled.
[   20.986493]   PREFETCH window: disabled.
[   20.986497] PCI: Bridge: 0000:00:1c.1
[   20.986499]   IO window: d000-dfff
[   20.986504]   MEM window: dff00000-dfffffff
[   20.986507]   PREFETCH window: disabled.
[   20.986513] PCI: Bridge: 0000:00:1e.0
[   20.986516]   IO window: c000-cfff
[   20.986520]   MEM window: dfe00000-dfefffff
[   20.986524]   PREFETCH window: disabled.
[   20.986552] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   20.986558] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   20.986576] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
[   20.986580] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   20.986591] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   20.986603] NET: Registered protocol family 2
[   21.021997] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[   21.022499] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[   21.024029] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   21.024892] TCP: Hash tables configured (established 131072 bind 65536)
[   21.024896] TCP reno registered
[   21.034117] checking if image is initramfs... it is
[   21.940851] Freeing initrd memory: 8207k freed
[   21.946489] audit: initializing netlink socket (disabled)
[   21.946513] audit(1215100295.712:1): initialized
[   21.948730] VFS: Disk quotas dquot_6.5.1
[   21.948808] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   21.948943] io scheduler noop registered
[   21.948945] io scheduler anticipatory registered
[   21.948947] io scheduler deadline registered
[   21.949059] io scheduler cfq registered (default)
[   21.949073] Boot video device is 0000:00:02.0
[   21.949938] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   21.949979] assign_interrupt_mode Found MSI capability
[   21.950014] Allocate Port Service[0000:00:1c.0:pcie00]
[   21.950050] Allocate Port Service[0000:00:1c.0:pcie02]
[   21.950131] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   21.950169] assign_interrupt_mode Found MSI capability
[   21.950201] Allocate Port Service[0000:00:1c.1:pcie00]
[   21.977868] Real Time Clock Driver v1.12ac
[   21.978081] hpet_resources: 0xfed00000 is busy
[   21.978121] Linux agpgart interface v0.102
[   21.978123] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   21.978255] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   21.978961] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   21.979714] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   21.979786] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   21.979894] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   21.982569] serio: i8042 KBD port at 0x60,0x64 irq 1
[   21.982574] serio: i8042 AUX port at 0x60,0x64 irq 12
[   21.997931] mice: PS/2 mouse device common for all mice
[   21.997981] cpuidle: using governor ladder
[   21.997983] cpuidle: using governor menu
[   21.998148] NET: Registered protocol family 1
[   21.998211] registered taskstats version 1
[   21.998323]   Magic number: 0:161:891
[   21.998389]   hash matches device ptyy1
[   21.998452] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   21.998455] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   21.998457] EDD information not available.
[   21.998465] Freeing unused kernel memory: 316k freed
[   22.017220] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   23.220888] fuse init (API version 7.9)
[   23.241829] ACPI: SSDT 3F7AE0C0, 01D2 (r1    AMI   CPU1PM        1 INTL 20060113)
[   23.242346] ACPI: Processor [CPU1] (supports 8 throttling states)
[   23.242528] ACPI: SSDT 3F7AE2A0, 0143 (r1    AMI   CPU2PM        1 INTL 20060113)
[   23.243042] ACPI: Processor [CPU2] (supports 8 throttling states)
[   23.243058] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   23.243072] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   23.555008] usbcore: registered new interface driver usbfs
[   23.555033] usbcore: registered new interface driver hub
[   23.555822] usbcore: registered new device driver usb
[   23.566267] USB Universal Host Controller Interface driver v3.0
[   23.566352] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 20
[   23.566364] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   23.566368] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   23.566642] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   23.566674] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00009000
[   23.566836] usb usb1: configuration #1 chosen from 1 choice
[   23.566861] hub 1-0:1.0: USB hub found
[   23.566868] hub 1-0:1.0: 2 ports detected
[   23.606186] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   23.611423] SCSI subsystem initialized
[   23.660685] libata version 3.00 loaded.
[   23.670321] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 17
[   23.670334] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   23.670338] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   23.670365] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   23.670394] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00009400
[   23.670511] usb usb2: configuration #1 chosen from 1 choice
[   23.670537] hub 2-0:1.0: USB hub found
[   23.670542] hub 2-0:1.0: 2 ports detected
[   23.774321] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   23.774334] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   23.774338] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   23.774361] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   23.774389] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00009800
[   23.774498] usb usb3: configuration #1 chosen from 1 choice
[   23.774523] hub 3-0:1.0: USB hub found
[   23.774529] hub 3-0:1.0: 2 ports detected
[   23.878317] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 19
[   23.878334] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   23.878337] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   23.878362] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   23.878391] uhci_hcd 0000:00:1d.3: irq 19, io base 0x0000a000
[   23.878516] usb usb4: configuration #1 chosen from 1 choice
[   23.878541] hub 4-0:1.0: USB hub found
[   23.878547] hub 4-0:1.0: 2 ports detected
[   23.982470] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 20
[   23.982774] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   23.982781] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   23.982834] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   23.986742] ehci_hcd 0000:00:1d.7: debug port 1
[   23.986750] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   23.986758] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xdfdffc00
[   24.002187] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   24.002322] usb usb5: configuration #1 chosen from 1 choice
[   24.002350] hub 5-0:1.0: USB hub found
[   24.002357] hub 5-0:1.0: 8 ports detected
[   24.106354] 8139cp 0000:01:01.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   24.106362] 8139cp 0000:01:01.0: Try the "8139too" driver instead.
[   24.107892] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 22 (level, low) -> IRQ 22
[   24.107936] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   24.107950] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[   24.107982] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 23 (level, low) -> IRQ 23
[   24.108004] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   24.108014] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[   24.109038] 8139too Fast Ethernet driver 0.9.28
[   24.109102] ACPI: PCI Interrupt 0000:01:01.0[A] -> GSI 21 (level, low) -> IRQ 21
[   24.116085] eth0: RealTek RTL8139 at 0xc800, 00:1d:0f:0e:12:82, IRQ 21
[   24.116089] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   24.116932] ata_piix 0000:00:1f.1: version 2.12
[   24.116957] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 22 (level, low) -> IRQ 22
[   24.116996] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   24.119384] scsi0 : ata_piix
[   24.120107] scsi1 : ata_piix
[   24.121608] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   24.121612] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   24.878527] ata1.00: ATAPI: ASUS DVD-ROM DVD-E616P              0104, E1.04, max UDMA/66
[   24.878547] ata1.01: ATAPI: ASUS    CRW-5232AS, 1.0, max UDMA/33
[   25.049945] ata1.00: configured for UDMA/66
[   25.213995] ata1.01: configured for UDMA/33
[   25.382494] scsi 0:0:0:0: CD-ROM            ASUS     DVD-E616P        1.04 PQ: 0 ANSI: 5
[   25.383363] scsi 0:0:1:0: CD-ROM            ASUS     CRW-5232AS       1.0  PQ: 0 ANSI: 5
[   25.383453] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   25.383483] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 23 (level, low) -> IRQ 23
[   25.383515] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   25.383818] scsi2 : ata_piix
[   25.383982] scsi3 : ata_piix
[   25.385300] ata3: SATA max UDMA/133 cmd 0xb800 ctl 0xb400 bmdma 0xa400 irq 23
[   25.385304] ata4: SATA max UDMA/133 cmd 0xb000 ctl 0xa800 bmdma 0xa408 irq 23
[   25.546395] ata3.00: ATA-7: SAMSUNG HD160JJ, ZM100-47, max UDMA7
[   25.546400] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   25.577884] ata3.00: configured for UDMA/133
[   25.744961] scsi 2:0:0:0: Direct-Access     ATA      SAMSUNG HD160JJ  ZM10 PQ: 0 ANSI: 5
[   25.757614] Driver 'sd' needs updating - please use bus_type methods
[   25.758867] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   25.758882] sd 2:0:0:0: [sda] Write Protect is off
[   25.758884] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   25.758903] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   25.758956] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   25.758967] sd 2:0:0:0: [sda] Write Protect is off
[   25.758969] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   25.758986] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   25.758990]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   25.764891] sr0: scsi3-mmc drive: 24x/24x cd/rw xa/form2 cdda tray
[   25.764896] Uniform CD-ROM driver Revision: 3.20
[   25.764959] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   25.765465]  sda1 sda2 <sr1: scsi3-mmc drive: 52x/52x writer cd/rw xa/form2 cdda tray
[   25.767610] sr 0:0:1:0: Attached scsi CD-ROM sr1
[   25.775741]  sda5 sda6 sda7 sda8 > sda3
[   25.822072] sd 2:0:0:0: [sda] Attached SCSI disk
[   25.826184] sr 0:0:0:0: Attached scsi generic sg0 type 5
[   25.826210] sr 0:0:1:0: Attached scsi generic sg1 type 5
[   25.826235] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   26.182062] Attempting manual resume
[   26.182065] swsusp: Resume From Partition 8:3
[   26.182067] PM: Checking swsusp image.
[   26.182260] PM: Resume from disk failed.
[   26.217050] kjournald starting.  Commit interval 5 seconds
[   26.217066] EXT3-fs: mounted filesystem with ordered data mode.
[   31.721727] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   31.769749] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   31.817811] agpgart: Detected an Intel 945G Chipset.
[   31.818407] agpgart: Detected 7932K stolen memory.
[   31.832698] agpgart: AGP aperture is 256M @ 0xe0000000
[   31.865731] iTCO_vendor_support: vendor-support=0
[   31.889747] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   31.889856] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, TCOBASE=0x0860)
[   31.889893] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   31.949782] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   32.019793] parport_pc 00:06: reported by Plug and Play ACPI
[   32.019917] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   32.057677] intel_rng: FWH not detected
[   32.101819] input: Power Button (FF) as /devices/virtual/input/input3
[   32.125627] ACPI: Power Button (FF) [PWRF]
[   32.125732] input: Power Button (CM) as /devices/virtual/input/input4
[   32.157620] ACPI: Power Button (CM) [PWRB]
[   32.673721] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   32.673744] snd-ca0106: Model 1012 Rev 00000000 Serial 10121102
[   32.878552] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 19 (level, low) -> IRQ 19
[   32.878856] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   32.901044] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[   32.906904] hda_codec: Unknown model for ALC662, trying auto-probe from BIOS...
[   32.909181] Attansic(R) L2 Ethernet Network Driver - version 1.0.40.2
[   32.909187] Copyright (c) 2006 Attansic Corporation.
[   32.943164] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   32.943177] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   33.735092] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input5
[   36.062093] lp0: using parport0 (interrupt-driven).
[   36.141816] Adding 1646652k swap on /dev/sda3.  Priority:-1 extents:1 across:1646652k
[   36.683469] EXT3 FS on sda1, internal journal
[   37.811130] ip_tables: (C) 2000-2006 Netfilter Core Team
[   38.123969] No dock devices found.
[   39.213826] ppdev: user-space parallel port driver
[   39.303444] audit(1215100313.321:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5052 profile="/usr/sbin/cupsd" namespace="default"
[   40.379712] Bluetooth: Core ver 2.11
[   40.379834] NET: Registered protocol family 31
[   40.379838] Bluetooth: HCI device and connection manager initialized
[   40.379843] Bluetooth: HCI socket layer initialized
[   40.418590] Bluetooth: L2CAP ver 2.9
[   40.418596] Bluetooth: L2CAP socket layer initialized
[   40.473217] Bluetooth: RFCOMM socket layer initialized
[   40.473238] Bluetooth: RFCOMM TTY layer initialized
[   40.473240] Bluetooth: RFCOMM ver 1.8
[   43.062731] [drm] Initialized drm 1.1.0 20060810
[   43.066464] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   43.066474] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   43.066560] [drm] Initialized i915 1.6.0 20060119 on minor 0


One issue : I have noticed something like "connection time out values" in the control panel when I used suse and fedora. Does this have anything to do with this problem?

---

### Post by pytheas22 on 2008-07-03
> Well, I have just experienced no internet. And now it came back to life.
As you said, I am pasting the output of dmesg now. Hope this will help find the source of the problem.

Did it break suddenly (like when you were in the middle of work) or do you mean that after you rebooted the computer, it didn't work?

Try this:
```

sudo -s
echo 'blacklist atl2' >> /etc/modprobe.d/blacklist
echo 'blacklist atl1' >> /etc/modprobe.d/blacklist
```

Then reboot.  eth1 should no longer exist, and hopefully your Internet will work reliably as a result.
> 
I have noticed something like "connection time out values" in the control panel when I used suse and fedora. Does this have anything to do with this problem?

I've never seen anything like that and am not sure what it means.  Maybe it means that the ethernet connection gets shut down after a certain period of time.  Do you notice your Internet breaking at fixed intervals, or does it seem to be random?

---

### Post by Louis de Broglie on 2008-07-03
It did not work after rebooting.It seems random. 

Anyway, those commands worked and eth1 is disabled now.:)

One more thing, when i typed sudo reboot, i receive messages among them some were warnings and some were errors. But the pc quickly restarts and I fail to note them down. Is there any way to keep track of them?:)

---

### Post by pytheas22 on 2008-07-03
> 
One more thing, when i typed sudo reboot, i receive messages among them some were warnings and some were errors. But the pc quickly restarts and I fail to note them down. Is there any way to keep track of them?

You can try pressing the pause/break button on your computer, but I don't know if it will work.  Otherwise those messages should be getting copied into the system logs, which you can view via the utility System>Administration>System Log.  Look in daemon.log, kern.log and syslog.  The logs show the date and time for each entry, so it should be easy enough to find the messages you're looking for.

---

### Post by Louis de Broglie on 2008-07-03
Ok. I have found those messages. Some r warning. some debug. 

Internet is working now. thanks for all your help.:)

Let's enjoy surfing.:popcorn:

---

### Post by Louis de Broglie on 2008-07-15
Thank you very much for all your effort. But the key reason behind that problem has been found :

[http://ubuntuforums.org/showthread.php?t=860155](http://ubuntuforums.org/showthread.php?t=860155)

Enjoy!:popcorn:

---

