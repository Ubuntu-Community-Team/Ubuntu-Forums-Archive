---
title: "No network after upgrade to Hardy"
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by sagen on 2008-04-25
Hi!

Did the upgrade through the update-manager, and now I can't get wired networking to work. I've tried the same cable with another pc, working great. 

Tried /etc/init.d/networking restart and dhclient manually, but it doesn't seem to receive anything. Also tried manually setting IP, with no luck. 

The router is receiving the requests, since the lan-light is flashing.

Any help or suggestions are greatly appreciated

Here's my ifconfig:
 
eth0      Link encap:Ethernet  HWaddr 00:1a:92:bb:41:00
          inet6 addr: fe80::21a:92ff:febb:4100/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:255 errors:0 dropped:73 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:50859 (49.6 KB)
          Interrupt:216

eth0:avahi Link encap:Ethernet  HWaddr 00:1a:92:bb:41:00
          inet addr:169.254.4.116  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:216

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:225 errors:0 dropped:0 overruns:0 frame:0
          TX packets:225 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:19868 (19.4 KB)  TX bytes:19868 (19.4 KB)

---

### Post by viceroy on 2008-04-25
post your results for 

```
dmesg
```

---

### Post by sagen on 2008-04-25
Thanks for the reply!

Here you go:

```
 [    0.000000] Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fef0000 (usable)
[    0.000000]  BIOS-e820: 000000007fef0000 - 000000007fef3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fef3000 - 000000007ff00000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000c0000000 - 00000000d0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f2000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 1150MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f6020
[    0.000000] Entering add_active_range(0, 0, 524016) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   524016
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   524016
[    0.000000] On node 0 totalpages: 524016
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2301 pages used for memmap
[    0.000000]   HighMem zone: 292339 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7AA0 checksum 0
[    0.000000] ACPI: RSDP 000F7AA0, 0024 (r2 Nvidia)
[    0.000000] ACPI: XSDT 7FEF30C0, 0044 (r1 Nvidia ASUSACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 7FEFB640, 00F4 (r3 Nvidia ASUSACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 7FEF3240, 8398 (r1 NVIDIA AWRDACPI     1000 MSFT  3000000)
[    0.000000] ACPI: FACS 7FEF0000, 0040
[    0.000000] ACPI: HPET 7FEFB880, 0038 (r1 Nvidia ASUSACPI 42302E31 AWRD       98)
[    0.000000] ACPI: MCFG 7FEFB900, 003C (r1 Nvidia ASUSACPI 42302E31 AWRD        0)
[    0.000000] ACPI: APIC 7FEFB780, 0098 (r1 Nvidia ASUSACPI 42302E31 AWRD        0)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfeff0000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 7ff00000:40100000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519923
[    0.000000] Kernel command line: root=/dev/mapper/cookiejar--desktop-root ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2666.845 MHz processor.
[   30.001373] spurious 8259A interrupt: IRQ7.
[   30.004029] Console: colour VGA+ 80x25
[   30.004031] console [tty0] enabled
[   30.004235] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   30.004436] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   30.063853] Memory: 2065336k/2096064k available (2157k kernel code, 29472k reserved, 998k data, 364k init, 1178560k highmem)
[   30.063858] virtual kernel memory layout:
[   30.063858]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   30.063859]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   30.063860]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   30.063860]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   30.063861]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
[   30.063862]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
[   30.063862]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
[   30.063864] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   30.063891] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   30.063989] hpet clockevent registered
[   30.143785] Calibrating delay using timer specific routine.. 5337.08 BogoMIPS (lpj=10674165)
[   30.143800] Security Framework initialized
[   30.143805] SELinux:  Disabled at boot.
[   30.143813] AppArmor: AppArmor initialized
[   30.143816] Failure registering capabilities with primary security module.
[   30.143821] Mount-cache hash table entries: 512
[   30.143904] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001 00000000
[   30.143910] monitor/mwait feature present.
[   30.143911] using mwait in idle threads.
[   30.143913] CPU: L1 I cache: 32K, L1 D cache: 32K
[   30.143915] CPU: L2 cache: 4096K
[   30.143916] CPU: Physical Processor ID: 0
[   30.143917] CPU: Processor Core ID: 0
[   30.143919] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001 00000000
[   30.143925] Compat vDSO mapped to ffffe000.
[   30.143933] Checking 'hlt' instruction... OK.
[   30.159983] SMP alternatives: switching to UP code
[   30.161006] Early unpacking initramfs... done
[   30.394475] ACPI: Core revision 20070126
[   30.394509] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   30.399569] CPU0: Intel(R) Core(TM)2 CPU          6700  @ 2.66GHz stepping 06
[   30.399579] SMP alternatives: switching to SMP code
[   30.399997] Booting processor 1/1 eip 3000
[   30.410346] Initializing CPU#1
[   30.486884] Calibrating delay using timer specific routine.. 5333.39 BogoMIPS (lpj=10666790)
[   30.486888] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001 00000000
[   30.486892] monitor/mwait feature present.
[   30.486893] CPU: L1 I cache: 32K, L1 D cache: 32K
[   30.486894] CPU: L2 cache: 4096K
[   30.486896] CPU: Physical Processor ID: 0
[   30.486897] CPU: Processor Core ID: 1
[   30.486898] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001 00000000
[   30.487371] CPU1: Intel(R) Core(TM)2 CPU          6700  @ 2.66GHz stepping 06
[   30.487386] Total of 2 processors activated (10670.47 BogoMIPS).
[   30.487561] ENABLING IO-APIC IRQs
[   30.487736] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   30.634570] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   30.654531] Brought up 2 CPUs
[   30.654544] CPU0 attaching sched-domain:
[   30.654546]  domain 0: span 03
[   30.654547]   groups: 01 02
[   30.654549] CPU1 attaching sched-domain:
[   30.654550]  domain 0: span 03
[   30.654551]   groups: 02 01
[   30.654713] net_namespace: 64 bytes
[   30.654720] Booting paravirtualized kernel on bare hardware
[   30.655045] Time: 11:49:48  Date: 04/25/08
[   30.655063] NET: Registered protocol family 16
[   30.655206] EISA bus registered
[   30.655209] ACPI: bus type pci registered
[   30.682947] PCI: PCI BIOS revision 3.00 entry at 0xf1e00, last bus=8
[   30.682948] PCI: Using configuration type 1
[   30.682949] Setting up standard PCI resources
[   30.684192] mtrr: your CPUs had inconsistent fixed MTRR settings
[   30.684193] mtrr: probably your BIOS does not setup all CPUs.
[   30.684194] mtrr: corrected configuration.
[   30.685402] ACPI: EC: Look up EC in DSDT
[   30.691030] ACPI: Interpreter enabled
[   30.691032] ACPI: (supports S0 S1 S3 S4 S5)
[   30.691042] ACPI: Using IOAPIC for interrupt routing
[   30.697520] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   30.699111] PCI: Transparent bridge - 0000:00:0f.0
[   30.699463] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   30.699806] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   30.771109] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   30.771247] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   30.771383] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   30.771520] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   30.771657] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 *7 9 10 11 14 15)
[   30.771792] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   30.771927] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   30.772063] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   30.772198] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   30.772333] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   30.772470] ACPI: PCI Interrupt Link [LMAC] (IRQs *5 7 9 10 11 14 15)
[   30.772605] ACPI: PCI Interrupt Link [LMC1] (IRQs 5 7 9 *10 11 14 15)
[   30.772741] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 *11 14 15)
[   30.772876] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   30.773011] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   30.773147] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   30.773282] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   30.773418] ACPI: PCI Interrupt Link [LSID] (IRQs *5 7 9 10 11 14 15)
[   30.773554] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 *10 11 14 15)
[   30.773690] ACPI: PCI Interrupt Link [LSA2] (IRQs 5 7 9 10 *11 14 15)
[   30.773850] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[   30.774005] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[   30.774159] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[   30.774316] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[   30.774470] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0
[   30.774623] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[   30.774777] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[   30.774930] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[   30.775084] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0, disabled.
[   30.775239] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[   30.775393] ACPI: PCI Interrupt Link [AMC1] (IRQs 20 21 22 23) *0
[   30.775547] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
[   30.775702] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
[   30.775856] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0, disabled.
[   30.776011] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0, disabled.
[   30.776166] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[   30.776321] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[   30.776475] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[   30.776629] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0
[   30.776785] ACPI: PCI Interrupt Link [ASA2] (IRQs 20 21 22 23) *0
[   30.776889] Linux Plug and Play Support v0.97 (c) Adam Belay
[   30.776911] pnp: PnP ACPI init
[   30.776916] ACPI: bus type pnp registered
[   30.779507] pnp: PnP ACPI: found 10 devices
[   30.779508] ACPI: ACPI bus type pnp unregistered
[   30.779511] PnPBIOS: Disabled by ACPI PNP
[   30.779673] PCI: Using ACPI for IRQ routing
[   30.779675] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   30.885850] NET: Registered protocol family 8
[   30.885851] NET: Registered protocol family 20
[   30.885876] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
[   30.885879] hpet0: 3 32-bit timers, 25000000 Hz
[   30.886899] AppArmor: AppArmor Filesystem Enabled
[   30.889836] Time: tsc clocksource has been installed.
[   30.889840] Switched to high resolution mode on CPU 0
[   30.889911] Switched to high resolution mode on CPU 1
[   30.905783] system 00:01: ioport range 0x1000-0x107f has been reserved
[   30.905785] system 00:01: ioport range 0x1080-0x10ff has been reserved
[   30.905786] system 00:01: ioport range 0x1400-0x147f has been reserved
[   30.905788] system 00:01: ioport range 0x1480-0x14ff has been reserved
[   30.905789] system 00:01: ioport range 0x1800-0x187f has been reserved
[   30.905791] system 00:01: ioport range 0x1880-0x18ff has been reserved
[   30.905793] system 00:01: iomem range 0xc0000000-0xcfffffff could not be reserved
[   30.905797] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[   30.905798] system 00:02: ioport range 0x800-0x87f has been reserved
[   30.905800] system 00:02: ioport range 0x290-0x297 has been reserved
[   30.905801] system 00:02: ioport range 0x880-0x88f has been reserved
[   30.905807] system 00:08: iomem range 0xf0000000-0xf1ffffff could not be reserved
[   30.905811] system 00:09: iomem range 0xf0000-0xf3fff could not be reserved
[   30.905813] system 00:09: iomem range 0xf4000-0xf7fff could not be reserved
[   30.905814] system 00:09: iomem range 0xf8000-0xfbfff could not be reserved
[   30.905816] system 00:09: iomem range 0xfc000-0xfffff could not be reserved
[   30.905818] system 00:09: iomem range 0xfeff0000-0xfeff00ff could not be reserved
[   30.905820] system 00:09: iomem range 0x7fef0000-0x7fefffff could not be reserved
[   30.905821] system 00:09: iomem range 0xffff0000-0xffffffff could not be reserved
[   30.905823] system 00:09: iomem range 0x0-0x9ffff could not be reserved
[   30.905825] system 00:09: iomem range 0x100000-0x7feeffff could not be reserved
[   30.905827] system 00:09: iomem range 0xfec00000-0xfec00fff could not be reserved
[   30.905829] system 00:09: iomem range 0xfee00000-0xfee00fff could not be reserved
[   30.905830] system 00:09: iomem range 0xfeff0000-0xfeff03ff could not be reserved
[   30.936059] PCI: Bridge: 0000:00:03.0
[   30.936060]   IO window: d000-dfff
[   30.936063]   MEM window: ea000000-edffffff
[   30.936065]   PREFETCH window: d0000000-dfffffff
[   30.936068] PCI: Bridge: 0000:00:0f.0
[   30.936069]   IO window: c000-cfff
[   30.936072]   MEM window: efd00000-efdfffff
[   30.936074]   PREFETCH window: efe00000-efefffff
[   30.936077] PCI: Bridge: 0000:00:13.0
[   30.936078]   IO window: b000-bfff
[   30.936081]   MEM window: efc00000-efcfffff
[   30.936083]   PREFETCH window: efb00000-efbfffff
[   30.936085] PCI: Bridge: 0000:00:14.0
[   30.936087]   IO window: a000-afff
[   30.936090]   MEM window: efa00000-efafffff
[   30.936092]   PREFETCH window: ef900000-ef9fffff
[   30.936094] PCI: Bridge: 0000:00:15.0
[   30.936096]   IO window: 9000-9fff
[   30.936098]   MEM window: ef800000-ef8fffff
[   30.936100]   PREFETCH window: ef700000-ef7fffff
[   30.936103] PCI: Bridge: 0000:00:16.0
[   30.936105]   IO window: 8000-8fff
[   30.936107]   MEM window: ef600000-ef6fffff
[   30.936109]   PREFETCH window: ef500000-ef5fffff
[   30.936112] PCI: Bridge: 0000:00:17.0
[   30.936113]   IO window: 7000-7fff
[   30.936116]   MEM window: ef400000-ef4fffff
[   30.936118]   PREFETCH window: ef300000-ef3fffff
[   30.936121] PCI: Bridge: 0000:00:18.0
[   30.936122]   IO window: 6000-6fff
[   30.936125]   MEM window: ef200000-ef2fffff
[   30.936127]   PREFETCH window: ef100000-ef1fffff
[   30.936137] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   30.936144] PCI: Setting latency timer of device 0000:00:0f.0 to 64
[   30.936152] PCI: Setting latency timer of device 0000:00:13.0 to 64
[   30.936161] PCI: Setting latency timer of device 0000:00:14.0 to 64
[   30.936169] PCI: Setting latency timer of device 0000:00:15.0 to 64
[   30.936177] PCI: Setting latency timer of device 0000:00:16.0 to 64
[   30.936185] PCI: Setting latency timer of device 0000:00:17.0 to 64
[   30.936193] PCI: Setting latency timer of device 0000:00:18.0 to 64
[   30.936200] NET: Registered protocol family 2
[   30.982595] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   30.982739] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   30.982999] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   30.983123] TCP: Hash tables configured (established 131072 bind 65536)
[   30.983124] TCP reno registered
[   30.994606] checking if image is initramfs... it is
[   31.455139] Freeing initrd memory: 8120k freed
[   31.455724] audit: initializing netlink socket (disabled)
[   31.455735] audit(1209124188.269:1): initialized
[   31.455888] highmem bounce pool size: 64 pages
[   31.457283] VFS: Disk quotas dquot_6.5.1
[   31.457335] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   31.457429] io scheduler noop registered
[   31.457430] io scheduler anticipatory registered
[   31.457432] io scheduler deadline registered
[   31.457439] io scheduler cfq registered (default)
[   31.476330] Boot video device is 0000:01:00.0
[   31.476419] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   31.476449] assign_interrupt_mode Found MSI capability
[   31.476471] Allocate Port Service[0000:00:03.0:pcie00]
[   31.476535] PCI: Setting latency timer of device 0000:00:13.0 to 64
[   31.476571] assign_interrupt_mode Found MSI capability
[   31.476594] Allocate Port Service[0000:00:13.0:pcie00]
[   31.476658] PCI: Setting latency timer of device 0000:00:14.0 to 64
[   31.476693] assign_interrupt_mode Found MSI capability
[   31.476716] Allocate Port Service[0000:00:14.0:pcie00]
[   31.476779] PCI: Setting latency timer of device 0000:00:15.0 to 64
[   31.476815] assign_interrupt_mode Found MSI capability
[   31.476838] Allocate Port Service[0000:00:15.0:pcie00]
[   31.476900] PCI: Setting latency timer of device 0000:00:16.0 to 64
[   31.476936] assign_interrupt_mode Found MSI capability
[   31.476959] Allocate Port Service[0000:00:16.0:pcie00]
[   31.477022] PCI: Setting latency timer of device 0000:00:17.0 to 64
[   31.477057] assign_interrupt_mode Found MSI capability
[   31.477080] Allocate Port Service[0000:00:17.0:pcie00]
[   31.477144] PCI: Setting latency timer of device 0000:00:18.0 to 64
[   31.477180] assign_interrupt_mode Found MSI capability
[   31.477203] Allocate Port Service[0000:00:18.0:pcie00]
[   31.477384] isapnp: Scanning for PnP cards...
[   31.829234] isapnp: No Plug & Play device found
[   31.846375] Real Time Clock Driver v1.12ac
[   31.846524] hpet_resources: 0xfeff0000 is busy
[   31.846552] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   31.847356] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   31.847402] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   31.847500] PNP: No PS/2 controller found. Probing ports directly.
[   31.847787] serio: i8042 KBD port at 0x60,0x64 irq 1
[   31.847790] serio: i8042 AUX port at 0x60,0x64 irq 12
[   31.867333] mice: PS/2 mouse device common for all mice
[   31.867417] EISA: Probing bus 0 at eisa.0
[   31.867421] Cannot allocate resource for EISA slot 1
[   31.867431] Cannot allocate resource for EISA slot 6
[   31.867432] Cannot allocate resource for EISA slot 7
[   31.867433] Cannot allocate resource for EISA slot 8
[   31.867434] EISA: Detected 0 cards.
[   31.867437] cpuidle: using governor ladder
[   31.867438] cpuidle: using governor menu
[   31.867490] NET: Registered protocol family 1
[   31.867508] Using IPI No-Shortcut mode
[   31.867528] registered taskstats version 1
[   31.867632]   Magic number: 4:818:833
[   31.867672] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   31.867673] EDD information not available.
[   31.867812] Freeing unused kernel memory: 364k freed
[   33.015605] fuse init (API version 7.9)
[   33.026233] ACPI: Fan [FAN] (on)
[   33.030069] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   33.030076] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   33.031225] ACPI: Thermal Zone [THRM] (40 C)
[   33.042563] device-mapper: uevent: version 1.0.3
[   33.042591] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: dm-devel@redhat.com
[   33.426670] usbcore: registered new interface driver usbfs
[   33.426685] usbcore: registered new interface driver hub
[   33.426708] usbcore: registered new device driver usb
[   33.435496] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 23
[   33.435501] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [APCL] -> GSI 23 (level, low) -> IRQ 16
[   33.435510] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[   33.435512] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[   33.435675] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
[   33.435693] ehci_hcd 0000:00:0b.1: debug port 1
[   33.435696] PCI: cache line size of 32 is not supported by device 0000:00:0b.1
[   33.435702] ehci_hcd 0000:00:0b.1: irq 16, io mem 0xefffe000
[   33.442915] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   33.448047] SCSI subsystem initialized
[   33.448279] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   33.448359] usb usb1: configuration #1 chosen from 1 choice
[   33.448376] hub 1-0:1.0: USB hub found
[   33.448379] hub 1-0:1.0: 10 ports detected
[   33.478456] libata version 3.00 loaded.
[   33.552051] sata_nv 0000:00:0e.0: version 3.5
[   33.552321] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 22
[   33.552325] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [APSI] -> GSI 22 (level, low) -> IRQ 17
[   33.552350] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   33.557640] scsi0 : sata_nv
[   33.557670] scsi1 : sata_nv
[   33.557775] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xf700 irq 17
[   33.557777] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xf708 irq 17
[   34.021692] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   34.069815] ata1.00: ATA-7: ST3500630AS, 3.AAK, max UDMA/133
[   34.069817] ata1.00: 976773168 sectors, multi 1: LBA48 NCQ (depth 0/32)
[   34.144584] ata1.00: configured for UDMA/133
[   34.213182] usb 1-4: new high speed USB device using ehci_hcd and address 4
[   34.346147] usb 1-4: configuration #1 chosen from 1 choice
[   34.355124] usbcore: registered new interface driver libusual
[   34.358337] Initializing USB Mass Storage driver...
[   34.358364] scsi2 : SCSI emulation for USB Mass Storage devices
[   34.358397] usbcore: registered new interface driver usb-storage
[   34.358399] USB Mass Storage support registered.
[   34.358438] usb-storage: device found at 4
[   34.358439] usb-storage: waiting for device to settle before scanning
[   34.609159] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   34.771855] ata2.00: ATAPI: Optiarc DVD RW AD-7170S, 1.00, max UDMA/66
[   34.943855] ata2.00: configured for UDMA/66
[   34.944071] scsi 0:0:0:0: Direct-Access     ATA      ST3500630AS      3.AA PQ: 0 ANSI: 5
[   34.945353] scsi 1:0:0:0: CD-ROM            Optiarc  DVD RW AD-7170S  1.00 PQ: 0 ANSI: 5
[   34.945647] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 21
[   34.945651] ACPI: PCI Interrupt 0000:00:0e.1[B] -> Link [APSJ] -> GSI 21 (level, low) -> IRQ 18
[   34.945673] PCI: Setting latency timer of device 0000:00:0e.1 to 64
[   34.945697] scsi3 : sata_nv
[   34.945781] scsi4 : sata_nv
[   34.945883] ata3: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xf200 irq 18
[   34.945885] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xf208 irq 18
[   35.255471] ata3: SATA link down (SStatus 0 SControl 300)
[   35.729247] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   35.754391] ata4.00: ATA-8: SAMSUNG HD501LJ, CR100-12, max UDMA7
[   35.754393] ata4.00: 976773168 sectors, multi 1: LBA48 NCQ (depth 0/32)
[   35.761383] ata4.00: configured for UDMA/133
[   35.761447] scsi 4:0:0:0: Direct-Access     ATA      SAMSUNG HD501LJ  CR10 PQ: 0 ANSI: 5
[   35.761713] ACPI: PCI Interrupt Link [ASA2] enabled at IRQ 20
[   35.761716] ACPI: PCI Interrupt 0000:00:0e.2[C] -> Link [ASA2] -> GSI 20 (level, low) -> IRQ 19
[   35.761735] PCI: Setting latency timer of device 0000:00:0e.2 to 64
[   35.761758] scsi5 : sata_nv
[   35.761848] scsi6 : sata_nv
[   35.761949] ata5: SATA max UDMA/133 cmd 0xf100 ctl 0xf000 bmdma 0xed00 irq 19
[   35.761951] ata6: SATA max UDMA/133 cmd 0xef00 ctl 0xee00 bmdma 0xed08 irq 19
[   36.072346] ata5: SATA link down (SStatus 0 SControl 300)
[   36.391515] ata6: SATA link down (SStatus 0 SControl 300)
[   36.402848] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   36.403087] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
[   36.403089] ACPI: PCI Interrupt 0000:00:11.0[A] -> Link [APCH] -> GSI 23 (level, low) -> IRQ 16
[   36.403093] PCI: Setting latency timer of device 0000:00:11.0 to 64
[   36.918501] forcedeth 0000:00:11.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:1a:92:bb:41:00
[   36.918504] forcedeth 0000:00:11.0: highdma csum vlan pwrctl mgmt timirq gbit lnktim msi desc-v3
[   36.918751] ACPI: PCI Interrupt Link [AMC1] enabled at IRQ 22
[   36.918753] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [AMC1] -> GSI 22 (level, low) -> IRQ 17
[   36.918757] PCI: Setting latency timer of device 0000:00:12.0 to 64
[   37.437143] forcedeth 0000:00:12.0: ifname eth1, PHY OUI 0x5043 @ 1, addr 00:1a:92:bb:4a:c9
[   37.437146] forcedeth 0000:00:12.0: highdma csum vlan pwrctl mgmt timirq gbit lnktim msi desc-v3
[   37.437174] pata_amd 0000:00:0d.0: version 0.3.10
[   37.437201] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   37.437399] scsi7 : pata_amd
[   37.437432] scsi8 : pata_amd
[   37.437756] ata7: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[   37.437757] ata8: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[   37.603299] ata8: port disabled. ignoring.
[   37.603571] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 21
[   37.603573] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [APCF] -> GSI 21 (level, low) -> IRQ 18
[   37.603578] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   37.603580] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[   37.603597] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[   37.603604] ohci_hcd 0000:00:0b.0: irq 18, io mem 0xeffff000
[   37.658284] usb usb2: configuration #1 chosen from 1 choice
[   37.658299] hub 2-0:1.0: USB hub found
[   37.658304] hub 2-0:1.0: 10 ports detected
[   37.760293] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[   37.760296] ACPI: PCI Interrupt 0000:02:0b.0[A] -> Link [APC4] -> GSI 19 (level, low) -> IRQ 20
[   37.812827] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[efdff000-efdff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   37.823192] Driver 'sd' needs updating - please use bus_type methods
[   37.823237] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[   37.823245] sd 0:0:0:0: [sda] Write Protect is off
[   37.823247] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   37.823257] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   37.823287] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[   37.823293] sd 0:0:0:0: [sda] Write Protect is off
[   37.823294] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   37.823304] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   37.823306]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   37.839858]  sda1 sda2 < sda5 >
[   37.844587] sd 0:0:0:0: [sda] Attached SCSI disk
[   37.847767] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   37.847769] Uniform CD-ROM driver Revision: 3.20
[   37.847795] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   37.847885] sd 4:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[   37.847892] sd 4:0:0:0: [sdb] Write Protect is off
[   37.847894] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   37.847904] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   37.847931] sd 4:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[   37.847937] sd 4:0:0:0: [sdb] Write Protect is off
[   37.847939] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   37.847949] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   37.847951]  sdb:<5>sd 0:0:0:0: Attached scsi generic sg0 type 0
[   37.850676] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   37.850687] sd 4:0:0:0: Attached scsi generic sg2 type 0
[   37.874305]  sdb1
[   37.874341] sd 4:0:0:0: [sdb] Attached SCSI disk
[   38.067166] usb 2-1: new low speed USB device using ohci_hcd and address 2
[   38.284664] usb 2-1: configuration #1 chosen from 1 choice
[   38.589797] usb 2-2: new full speed USB device using ohci_hcd and address 3
[   38.810284] usb 2-2: configuration #1 chosen from 1 choice
[   38.813244] hub 2-2:1.0: USB hub found
[   38.816217] hub 2-2:1.0: 3 ports detected
[   39.084583] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d8000131aa79]
[   39.146356] usb 2-2.2: new full speed USB device using ohci_hcd and address 4
[   39.274071] usb 2-2.2: configuration #1 chosen from 1 choice
[   39.343930] usb-storage: device scan complete
[   39.345307] scsi 2:0:0:0: Direct-Access     Ut161    USB2FlashStorage 0.00 PQ: 0 ANSI: 2
[   39.349534] sd 2:0:0:0: [sdc] 256000 512-byte hardware sectors (131 MB)
[   39.352399] sd 2:0:0:0: [sdc] Write Protect is off
[   39.352401] sd 2:0:0:0: [sdc] Mode Sense: 00 00 00 00
[   39.352402] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[   39.358507] sd 2:0:0:0: [sdc] 256000 512-byte hardware sectors (131 MB)
[   39.361375] sd 2:0:0:0: [sdc] Write Protect is off
[   39.361377] sd 2:0:0:0: [sdc] Mode Sense: 00 00 00 00
[   39.361378] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[   39.361380]  sdc: sdc1
[   39.429238] sd 2:0:0:0: [sdc] Attached SCSI removable disk
[   39.429260] sd 2:0:0:0: Attached scsi generic sg3 type 0
[   39.489463] usb 2-2.3: new full speed USB device using ohci_hcd and address 5
[   39.613194] usb 2-2.3: configuration #1 chosen from 1 choice
[   39.620130] usbcore: registered new interface driver hiddev
[   39.628234] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:0b.0/usb2/2-1/2-1:1.0/input/input1
[   39.651065] input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:0b.0-1
[   39.660068] input: Logitech Logitech BT Mini-Receiver as /devices/pci0000:00/0000:00:0b.0/usb2/2-2/2-2.2/2-2.2:1.0/input/input2
[   39.682965] input,hidraw1: USB HID v1.11 Keyboard [Logitech Logitech BT Mini-Receiver] on usb-0000:00:0b.0-2.2
[   39.695984] input: Logitech Logitech BT Mini-Receiver as /devices/pci0000:00/0000:00:0b.0/usb2/2-2/2-2.3/2-2.3:1.0/input/input3
[   39.722887] input,hiddev96,hidraw2: USB HID v1.11 Mouse [Logitech Logitech BT Mini-Receiver] on usb-0000:00:0b.0-2.3
[   39.722897] usbcore: registered new interface driver usbhid
[   39.722899] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   47.435053] padlock: VIA PadLock Hash Engine not detected.
[   47.909693] Attempting manual resume
[   47.909700] swsusp: Resume From Partition 254:2
[   47.909701] PM: Checking swsusp image.
[   47.910014] PM: Resume from disk failed.
[   47.953997] kjournald starting.  Commit interval 5 seconds
[   47.954001] EXT3-fs: mounted filesystem with ordered data mode.
[   55.222675] input: Power Button (FF) as /devices/virtual/input/input4
[   55.254473] ACPI: Power Button (FF) [PWRF]
[   55.254520] input: Power Button (CM) as /devices/virtual/input/input5
[   55.286377] ACPI: Power Button (CM) [PWRB]
[   55.498841] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   55.518198] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   56.123109] Linux agpgart interface v0.102
[   56.192242] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[   56.192264] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x1c80
[   56.336151] nvidia: module license 'NVIDIA' taints kernel.
[   56.684276] ACPI: PCI Interrupt Link [APC5] enabled at IRQ 16
[   56.684281] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [APC5] -> GSI 16 (level, low) -> IRQ 21
[   56.684287] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   56.684993] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   56.999733] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   57.284548] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 20
[   57.284551] ACPI: PCI Interrupt 0000:00:0f.1[B] -> Link [AAZA] -> GSI 20 (level, low) -> IRQ 19
[   57.284563] PCI: Setting latency timer of device 0000:00:0f.1 to 64
[   57.318272] hda_codec: Unknown model for AD1988, trying auto-probe from BIOS...
[   58.091110] NET: Registered protocol family 17
[   58.277610] loop: module loaded
[   58.321653] lp: driver loaded but no devices found
[   58.392479] Adding 6221816k swap on /dev/mapper/cookiejar--desktop-swap_1.  Priority:-1 extents:1 across:6221816k
[   58.922061] EXT3 FS on dm-1, internal journal
[   68.285693] kjournald starting.  Commit interval 5 seconds
[   68.292674] EXT3 FS on sda1, internal journal
[   68.292677] EXT3-fs: mounted filesystem with ordered data mode.
[   68.312548] kjournald starting.  Commit interval 5 seconds
[   68.312553] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   68.320578] EXT3 FS on dm-3, internal journal
[   68.320581] EXT3-fs: mounted filesystem with ordered data mode.
[   68.640088] ip_tables: (C) 2000-2006 Netfilter Core Team
[   68.930564] No dock devices found.
[   75.450612] ppdev: user-space parallel port driver
[   75.592411] audit(1209124233.416:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5792 profile="/usr/sbin/cupsd" namespace="default"
[   75.667250] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   75.667253] apm: disabled - APM is not SMP safe.
[   78.272712] Bluetooth: Core ver 2.11
[   78.272875] NET: Registered protocol family 31
[   78.272877] Bluetooth: HCI device and connection manager initialized
[   78.272879] Bluetooth: HCI socket layer initialized
[   78.315033] Bluetooth: L2CAP ver 2.9
[   78.315036] Bluetooth: L2CAP socket layer initialized
[   78.352542] Bluetooth: RFCOMM socket layer initialized
[   78.352551] Bluetooth: RFCOMM TTY layer initialized
[   78.352552] Bluetooth: RFCOMM ver 1.8
[   78.471681] usb 2-2.1: new full speed USB device using ohci_hcd and address 6
[   78.607397] usb 2-2.1: configuration #1 chosen from 1 choice
[   78.750271] Bluetooth: HCI USB driver ver 2.9
[   78.752266] usbcore: registered new interface driver hci_usb
[   97.693843] usb 2-2: USB disconnect, address 3
[   97.693846] usb 2-2.1: USB disconnect, address 6
[   97.947747] usb 2-2.2: USB disconnect, address 4
[   97.983471] usb 2-2.3: USB disconnect, address 5
[   98.701437] usb 2-2: new full speed USB device using ohci_hcd and address 7
[   98.922349] usb 2-2: configuration #1 chosen from 1 choice
[   98.925298] hub 2-2:1.0: USB hub found
[   98.928267] hub 2-2:1.0: 3 ports detected
[   99.257408] usb 2-2.2: new full speed USB device using ohci_hcd and address 8
[   99.381143] usb 2-2.2: configuration #1 chosen from 1 choice
[   99.397101] input: Logitech Logitech BT Mini-Receiver as /devices/pci0000:00/0000:00:0b.0/usb2/2-2/2-2.2/2-2.2:1.0/input/input7
[   99.448547] input,hidraw1: USB HID v1.11 Keyboard [Logitech Logitech BT Mini-Receiver] on usb-0000:00:0b.0-2.2
[   99.660356] usb 2-2.3: new full speed USB device using ohci_hcd and address 9
[   99.784105] usb 2-2.3: configuration #1 chosen from 1 choice
[   99.805050] input: Logitech Logitech BT Mini-Receiver as /devices/pci0000:00/0000:00:0b.0/usb2/2-2/2-2.3/2-2.3:1.0/input/input8
[   99.870447] input,hiddev96,hidraw2: USB HID v1.11 Mouse [Logitech Logitech BT Mini-Receiver] on usb-0000:00:0b.0-2.3

```

---

### Post by wareagle on 2008-05-06
Please post the output of ```
lspci
```.

---

