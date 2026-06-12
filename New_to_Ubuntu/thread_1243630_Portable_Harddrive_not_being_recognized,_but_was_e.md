---
title: "Portable Harddrive not being recognized, but was earlier."
date: 2009-08-18
forum: New to Ubuntu
---

### Post by tmurph on 2009-08-18
I have my music library on my portable harddrive. Yesterday it was working fine, i had all of the library on rhythmbox when it was plugged in. Today, the drive appears to not even being recognized by my computer, and thus when I later opened rhythm box, the library promptly dwindled down to nothing. 

My question is: Why isn't it being recognized anymore? How can i fix it? etc.

Chances are the answer is something completley obvious in nature, but keep in mind i'm somewhat of a newbie here!:) If anyone needs additional details, please don't hesitate to ask. Thanks!

:guitar:

---

### Post by kayvortex on 2009-08-18
So, you can't open the external hard drive when you plug it in?

Plug it in and type:
```
sudo fdisk -l
```
into a terminal and post what comes up.

---

### Post by tmurph on 2009-08-18
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xed1f86f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18720   150368368+  83  Linux
/dev/sda2           18721       19457     5919952+   5  Extended
/dev/sda5           18721       19457     5919921   82  Linux swap / Solaris


thanks, hope this helps

---

### Post by kayvortex on 2009-08-18
Well, it's not showing up on there. You're sure it's plugged in and on? Could you post the output of:
```
lsusb
```

---

### Post by tmurph on 2009-08-18
I made sure it was plugged in and ran that first command again
sudo fdisk -l


I got this:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xed1f86f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18720   150368368+  83  Linux
/dev/sda2           18721       19457     5919952+   5  Extended
/dev/sda5           18721       19457     5919921   82  Linux swap / Solaris


For the 
lsusb
I got this:

Bus 002 Device 002: ID 162f:4003 WiQuest Communications, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0a5c:2110 Broadcom Corp. Bluetooth Controller
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by kayvortex on 2009-08-18
It's not that WiQuest Communications device is it? If not, then it really doesn't seem to be detected. Could you go to System -> Administration -> Log File Viewer, click on "dmesg" and post its contents. I'll try to see if I spot anything in there.

Have you tried rebooting, or changing which USB port you connect the HD to? It might be worth giving it a go.

---

### Post by tmurph on 2009-08-18
Thank you again for your help! I have tried plugging it into some of the alternate USB ports but still no luck. Are you supposed to designate a certain port for a portable hd? Very weird because it was working fine earlier. I may or may not have tried mounting and un mounting to disconnect, could this of had an effect?

These are the contents of dmesg:

```
 [    0.000000] BIOS EBDA/lowmem at: 0009d800/0009d800
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-15-generic (buildd@rothera) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #48-Ubuntu SMP Wed Jul 29 08:54:56 UTC 2009 (Ubuntu 2.6.28-15.48-generic)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d800 (usable)
[    0.000000]  BIOS-e820: 000000000009d800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007d6b0000 (usable)
[    0.000000]  BIOS-e820: 000000007d6b0000 - 000000007d6cc000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007d6cc000 - 000000007d700000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007d700000 - 000000007e000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0x7d6b0 max_arch_pfn = 0x100000
[    0.000000] Scanning 2 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 0000000000007000 (usable)
[    0.000000]  modified: 0000000000007000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 0000000000090800 (usable)
[    0.000000]  modified: 000000000009d800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007d6b0000 (usable)
[    0.000000]  modified: 000000007d6b0000 - 000000007d6cc000 (ACPI data)
[    0.000000]  modified: 000000007d6cc000 - 000000007d700000 (ACPI NVS)
[    0.000000]  modified: 000000007d700000 - 000000007e000000 (reserved)
[    0.000000]  modified: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  modified: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  modified: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000
[    0.000000] RAMDISK: 378bb000 - 37fefb3b
[    0.000000] Allocated new RAMDISK: 0087d000 - 00fb1b3b
[    0.000000] Move RAMDISK from 00000000378bb000 - 0000000037fefb3a to 0087d000 - 00fb1b3a
[    0.000000] ACPI: RSDP 000F68D0, 0024 (r2 LENOVO)
[    0.000000] ACPI: XSDT 7D6BB731, 0094 (r1 LENOVO TP-7L        2100  LTP        0)
[    0.000000] ACPI: FACP 7D6BB800, 00F4 (r3 LENOVO TP-7L        2100 LNVO        1)
[    0.000000] ACPI Warning (tbfadt-0460): Optional field "Gpe1Block" has zero address or length: 000000000000102C/0 [20080926]
[    0.000000] ACPI: DSDT 7D6BBC1D, FF1F (r1 LENOVO TP-7L        2100 MSFT  3000000)
[    0.000000] ACPI: FACS 7D6E4000, 0040
[    0.000000] ACPI: SSDT 7D6BB9B4, 0269 (r1 LENOVO TP-7L        2100 MSFT  3000000)
[    0.000000] ACPI: ECDT 7D6CBB3C, 0052 (r1 LENOVO TP-7L        2100 LNVO        1)
[    0.000000] ACPI: TCPA 7D6CBB8E, 0032 (r2 LENOVO TP-7L        2100 LNVO        1)
[    0.000000] ACPI: APIC 7D6CBBC0, 0068 (r1 LENOVO TP-7L        2100 LNVO        1)
[    0.000000] ACPI: MCFG 7D6CBC28, 003C (r1 LENOVO TP-7L        2100 LNVO        1)
[    0.000000] ACPI: HPET 7D6CBC64, 0038 (r1 LENOVO TP-7L        2100 LNVO        1)
[    0.000000] ACPI: SLIC 7D6CBDF0, 0176 (r1 LENOVO TP-7L        2100  LTP        0)
[    0.000000] ACPI: BOOT 7D6CBF66, 0028 (r1 LENOVO TP-7L        2100  LTP        1)
[    0.000000] ACPI: ASF! 7D6CBF8E, 0072 (r16 LENOVO TP-7L        2100 PTL         1)
[    0.000000] ACPI: SSDT 7D6E271B, 025F (r1 LENOVO TP-7L        2100 INTL 20050513)
[    0.000000] ACPI: SSDT 7D6E297A, 00A6 (r1 LENOVO TP-7L        2100 INTL 20050513)
[    0.000000] ACPI: SSDT 7D6E2A20, 04F7 (r1 LENOVO TP-7L        2100 INTL 20050513)
[    0.000000] ACPI: SSDT 7D6E2F17, 01D8 (r1 LENOVO TP-7L        2100 INTL 20050513)
[    0.000000] ACPI: DMI detected: Lenovo ThinkPad T61
[    0.000000] ACPI: Added _OSI(Linux)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1122MB HIGHMEM available.
[    0.000000] 883MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 373fe000
[    0.000000]   low ram: 00000000 - 373fe000
[    0.000000]   bootmap 00012000 - 00018e80
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00373fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008780ac]    TEXT DATA BSS ==> [0000100000 - 00008780ac]
[    0.000000]   #4 [0000879000 - 000087d000]    INIT_PG_TABLE ==> [0000879000 - 000087d000]
[    0.000000]   #5 [000009d800 - 0000100000]    BIOS reserved ==> [000009d800 - 0000100000]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [000087d000 - 0000fb1b3b]      NEW RAMDISK ==> [000087d000 - 0000fb1b3b]
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
[    0.000000] found SMP MP-table at [c00f6900] 000f6900
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000373fe
[    0.000000]   HighMem  0x000373fe -> 0x0007d6b0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x00000007
[    0.000000]     0: 0x00000010 -> 0x00000090
[    0.000000]     0: 0x00000100 -> 0x0007d6b0
[    0.000000] On node 0 totalpages: 513587
[    0.000000] free_area_init_node: node 0, pgdat c06cb500, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3939 pages, LIFO batch:0
[    0.000000]   Normal zone: 1736 pages used for memmap
[    0.000000]   Normal zone: 220470 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2246 pages used for memmap
[    0.000000]   HighMem zone: 285164 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 0000000000007000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 0000000000090000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
[    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 7e000000:72000000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 509573
[    0.000000] Kernel command line: root=UUID=c771e946-e54c-40c6-82d3-859980adbc64 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2393.878 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] allocated 10274240 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 2011348k/2054848k available (4115k kernel code, 42104k reserved, 2199k data, 532k init, 1149640k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
[    0.004000]       .init : 0xc0733000 - 0xc07b8000   ( 532 kB)
[    0.004000]       .data : 0xc0504f5f - 0xc072ae60   (2199 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0504f5f   (4115 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 4787.75 BogoMIPS (lpj=9575512)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] Initializing cgroup subsys freezer
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 3072K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using mwait in idle threads.
[    0.004000] Checking 'hlt' instruction... OK.
[    0.018017] ACPI: Core revision 20080926
[    0.023370] ACPI: Checking initramfs for custom DSDT
[    0.264476] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.305048] CPU0: Intel(R) Core(TM)2 Duo CPU     T8300  @ 2.40GHz stepping 06
[    0.308001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 4787.93 BogoMIPS (lpj=9575877)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 3072K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.392618] CPU1: Intel(R) Core(TM)2 Duo CPU     T8300  @ 2.40GHz stepping 06
[    0.392634] checking TSC synchronization [CPU#0 -> CPU#1]:
[    0.396001] Measured 1349472 cycles TSC warp between CPUs, turning off TSC clock.
[    0.396001] Marking TSC unstable due to check_tsc_sync_source failed
[    0.396034] Brought up 2 CPUs
[    0.396037] Total of 2 processors activated (9575.69 BogoMIPS).
[    0.396093] CPU0 attaching sched-domain:
[    0.396095]  domain 0: span 0-1 level MC
[    0.396098]   groups: 0 1
[    0.396103] CPU1 attaching sched-domain:
[    0.396104]  domain 0: span 0-1 level MC
[    0.396106]   groups: 1 0
[    0.396166] net_namespace: 776 bytes
[    0.396166] Booting paravirtualized kernel on bare hardware
[    0.396263] Time:  0:25:23  Date: 08/19/09
[    0.396263] regulator: core version 0.5
[    0.396263] NET: Registered protocol family 16
[    0.396263] EISA bus registered
[    0.396263] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.396263] ACPI: bus type pci registered
[    0.396263] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
[    0.396263] PCI: MCFG area at f0000000 reserved in E820
[    0.396263] PCI: Using MMCONFIG for extended config space
[    0.396263] PCI: Using configuration type 1 for base access
[    0.397296] ACPI: EC: EC description table is found, configuring boot EC
[    0.405433] ACPI: BIOS _OSI(Linux) query honored via DMI
[    0.404023] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.416835] ACPI: Interpreter enabled
[    0.416839] ACPI: (supports S0 S3 S4 S5)
[    0.416855] ACPI: Using IOAPIC for interrupt routing
[    0.432842] ACPI: EC: GPE = 0x12, I/O: command/status = 0x66, data = 0x62
[    0.432844] ACPI: EC: driver started in interrupt mode
[    0.433458] ACPI: ACPI Dock Station Driver: 3 docks/bays found
[    0.433458] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.433458] pci 0000:00:02.0: reg 10 64bit mmio: [0xf8100000-0xf81fffff]
[    0.433458] pci 0000:00:02.0: reg 18 64bit mmio: [0xe0000000-0xefffffff]
[    0.433458] pci 0000:00:02.0: reg 20 io port: [0x1800-0x1807]
[    0.433458] pci 0000:00:02.1: reg 10 64bit mmio: [0xf8200000-0xf82fffff]
[    0.433498] pci 0000:00:19.0: reg 10 32bit mmio: [0xfe000000-0xfe01ffff]
[    0.433507] pci 0000:00:19.0: reg 14 32bit mmio: [0xfe025000-0xfe025fff]
[    0.433516] pci 0000:00:19.0: reg 18 io port: [0x1840-0x185f]
[    0.433577] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.433585] pci 0000:00:19.0: PME# disabled
[    0.433687] pci 0000:00:1a.0: reg 20 io port: [0x1860-0x187f]
[    0.433814] pci 0000:00:1a.1: reg 20 io port: [0x1880-0x189f]
[    0.433920] pci 0000:00:1a.7: reg 10 32bit mmio: [0xfe226c00-0xfe226fff]
[    0.433992] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.433999] pci 0000:00:1a.7: PME# disabled
[    0.434084] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfe020000-0xfe023fff]
[    0.434148] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.434154] pci 0000:00:1b.0: PME# disabled
[    0.434251] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.434259] pci 0000:00:1c.0: PME# disabled
[    0.434344] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.434353] pci 0000:00:1c.1: PME# disabled
[    0.436073] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.436079] pci 0000:00:1c.2: PME# disabled
[    0.436177] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.436184] pci 0000:00:1c.3: PME# disabled
[    0.436276] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.436284] pci 0000:00:1c.4: PME# disabled
[    0.436401] pci 0000:00:1d.0: reg 20 io port: [0x18a0-0x18bf]
[    0.436521] pci 0000:00:1d.1: reg 20 io port: [0x18c0-0x18df]
[    0.436641] pci 0000:00:1d.2: reg 20 io port: [0x18e0-0x18ff]
[    0.436758] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfe227000-0xfe2273ff]
[    0.436830] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.436839] pci 0000:00:1d.7: PME# disabled
[    0.437053] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.437059] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH6 GPIO
[    0.437128] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.437142] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.437158] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.437172] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.437184] pci 0000:00:1f.1: reg 20 io port: [0x1c00-0x1c0f]
[    0.437285] pci 0000:00:1f.2: reg 10 io port: [0x1c50-0x1c57]
[    0.437294] pci 0000:00:1f.2: reg 14 io port: [0x1c44-0x1c47]
[    0.437303] pci 0000:00:1f.2: reg 18 io port: [0x1c48-0x1c4f]
[    0.437319] pci 0000:00:1f.2: reg 1c io port: [0x1c40-0x1c43]
[    0.437333] pci 0000:00:1f.2: reg 20 io port: [0x1c20-0x1c3f]
[    0.437349] pci 0000:00:1f.2: reg 24 32bit mmio: [0xfe226000-0xfe2267ff]
[    0.437371] pci 0000:00:1f.2: PME# supported from D3hot
[    0.437379] pci 0000:00:1f.2: PME# disabled
[    0.437431] pci 0000:00:1f.3: reg 10 32bit mmio: [0xfe227400-0xfe2274ff]
[    0.437459] pci 0000:00:1f.3: reg 20 io port: [0x1c60-0x1c7f]
[    0.437570] pci 0000:00:1c.0: bridge io port: [0x2000-0x2fff]
[    0.437576] pci 0000:00:1c.0: bridge 32bit mmio: [0xfc000000-0xfdffffff]
[    0.437588] pci 0000:00:1c.0: bridge 64bit mmio pref: [0xf8000000-0xf80fffff]
[    0.437779] pci 0000:03:00.0: reg 10 32bit mmio: [0xdf3ff000-0xdf3fffff]
[    0.437944] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    0.437956] pci 0000:03:00.0: PME# disabled
[    0.438062] pci 0000:00:1c.1: bridge io port: [0x3000-0x3fff]
[    0.438067] pci 0000:00:1c.1: bridge 32bit mmio: [0xdc000000-0xdf3fffff]
[    0.438074] pci 0000:00:1c.1: bridge 64bit mmio pref: [0xdfe00000-0xdfefffff]
[    0.438138] pci 0000:00:1c.2: bridge io port: [0x4000-0x4fff]
[    0.438144] pci 0000:00:1c.2: bridge 32bit mmio: [0xd8000000-0xd9ffffff]
[    0.438160] pci 0000:00:1c.2: bridge 64bit mmio pref: [0xdfb00000-0xdfbfffff]
[    0.438246] pci 0000:00:1c.3: bridge io port: [0x5000-0x5fff]
[    0.438254] pci 0000:00:1c.3: bridge 32bit mmio: [0xd4000000-0xd5ffffff]
[    0.438268] pci 0000:00:1c.3: bridge 64bit mmio pref: [0xdf800000-0xdf8fffff]
[    0.438335] pci 0000:00:1c.4: bridge io port: [0x6000-0x6fff]
[    0.438343] pci 0000:00:1c.4: bridge 32bit mmio: [0xd0000000-0xd1ffffff]
[    0.438357] pci 0000:00:1c.4: bridge 64bit mmio pref: [0xdf500000-0xdf5fffff]
[    0.438440] pci 0000:15:00.0: reg 10 32bit mmio: [0xf8300000-0xf8300fff]
[    0.438461] pci 0000:15:00.0: supports D1 D2
[    0.438462] pci 0000:15:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.438469] pci 0000:15:00.0: PME# disabled
[    0.438556] pci 0000:15:00.1: reg 10 32bit mmio: [0xf8301000-0xf83017ff]
[    0.438650] pci 0000:15:00.1: supports D1 D2
[    0.438651] pci 0000:15:00.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.438660] pci 0000:15:00.1: PME# disabled
[    0.438740] pci 0000:15:00.2: reg 10 32bit mmio: [0xf8301800-0xf83018ff]
[    0.438835] pci 0000:15:00.2: supports D1 D2
[    0.438837] pci 0000:15:00.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.438844] pci 0000:15:00.2: PME# disabled
[    0.438927] pci 0000:15:00.3: reg 10 32bit mmio: [0xf8301c00-0xf8301cff]
[    0.439021] pci 0000:15:00.3: supports D1 D2
[    0.439023] pci 0000:15:00.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.439032] pci 0000:15:00.3: PME# disabled
[    0.439117] pci 0000:15:00.4: reg 10 32bit mmio: [0xf8302000-0xf83020ff]
[    0.439209] pci 0000:15:00.4: supports D1 D2
[    0.439210] pci 0000:15:00.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.439219] pci 0000:15:00.4: PME# disabled
[    0.439297] pci 0000:15:00.5: reg 10 32bit mmio: [0xf8302400-0xf83024ff]
[    0.439383] pci 0000:15:00.5: supports D1 D2
[    0.439385] pci 0000:15:00.5: PME# supported from D0 D1 D2 D3hot D3cold
[    0.439392] pci 0000:15:00.5: PME# disabled
[    0.439508] pci 0000:00:1e.0: transparent bridge
[    0.439515] pci 0000:00:1e.0: bridge io port: [0x7000-0xafff]
[    0.439521] pci 0000:00:1e.0: bridge 32bit mmio: [0xf8300000-0xfbffffff]
[    0.439535] pci 0000:00:1e.0: bridge 64bit mmio pref: [0xf4000000-0xf7ffffff]
[    0.439620] bus 00 -> node 0
[    0.439627] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.439856] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP0._PRT]
[    0.439979] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[    0.440113] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[    0.440237] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP3._PRT]
[    0.440361] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP4._PRT]
[    0.440486] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    0.443945] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11)
[    0.444158] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
[    0.444361] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
[    0.444563] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[    0.444764] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11)
[    0.444966] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11)
[    0.445168] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11)
[    0.445369] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11)
[    0.444074] ACPI: Power Resource [PUBS] (on)
[    0.444289] ACPI: WMI: Mapper loaded
[    0.444404] SCSI subsystem initialized
[    0.445479] libata version 3.00 loaded.
[    0.445479] usbcore: registered new interface driver usbfs
[    0.445479] usbcore: registered new interface driver hub
[    0.445479] usbcore: registered new device driver usb
[    0.445479] PCI: Using ACPI for IRQ routing
[    0.452008] Bluetooth: Core ver 2.13
[    0.452018] NET: Registered protocol family 31
[    0.452018] Bluetooth: HCI device and connection manager initialized
[    0.452018] Bluetooth: HCI socket layer initialized
[    0.452018] NET: Registered protocol family 8
[    0.452018] NET: Registered protocol family 20
[    0.452026] NetLabel: Initializing
[    0.452028] NetLabel:  domain hash size = 128
[    0.452029] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.452039] NetLabel:  unlabeled traffic allowed by default
[    0.452056] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.452059] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.456047] AppArmor: AppArmor Filesystem Enabled
[    0.460013] Switched to high resolution mode on CPU 0
[    0.460679] Switched to high resolution mode on CPU 1
[    0.464018] pnp: PnP ACPI init
[    0.464024] ACPI: bus type pnp registered
[    0.469319] pnp: PnP ACPI: found 11 devices
[    0.469320] ACPI: ACPI bus type pnp unregistered
[    0.469323] PnPBIOS: Disabled by ACPI PNP
[    0.469330] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.469333] system 00:00: iomem range 0xc0000-0xc3fff could not be reserved
[    0.469335] system 00:00: iomem range 0xc4000-0xc7fff could not be reserved
[    0.469337] system 00:00: iomem range 0xc8000-0xcbfff has been reserved
[    0.469339] system 00:00: iomem range 0xcc000-0xcffff has been reserved
[    0.469341] system 00:00: iomem range 0xd0000-0xd3fff could not be reserved
[    0.469343] system 00:00: iomem range 0xe0000-0xe3fff could not be reserved
[    0.469345] system 00:00: iomem range 0xe4000-0xe7fff could not be reserved
[    0.469348] system 00:00: iomem range 0xe8000-0xebfff could not be reserved
[    0.469350] system 00:00: iomem range 0xec000-0xeffff could not be reserved
[    0.469352] system 00:00: iomem range 0xf0000-0xfffff could not be reserved
[    0.469354] system 00:00: iomem range 0x100000-0x7dffffff could not be reserved
[    0.469356] system 00:00: iomem range 0xfec00000-0xfed3ffff could not be reserved
[    0.469359] system 00:00: iomem range 0xfed4c000-0xffffffff could not be reserved
[    0.469364] system 00:02: ioport range 0x164e-0x164f has been reserved
[    0.469367] system 00:02: ioport range 0x1000-0x107f has been reserved
[    0.469369] system 00:02: ioport range 0x1180-0x11bf has been reserved
[    0.469371] system 00:02: ioport range 0x800-0x80f has been reserved
[    0.469373] system 00:02: ioport range 0x15e0-0x15ef has been reserved
[    0.469375] system 00:02: ioport range 0x1600-0x165f could not be reserved
[    0.469377] system 00:02: iomem range 0xf0000000-0xf3ffffff has been reserved
[    0.469380] system 00:02: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.469382] system 00:02: iomem range 0xfed14000-0xfed17fff has been reserved
[    0.469384] system 00:02: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.469386] system 00:02: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.469388] system 00:02: iomem range 0xfed45000-0xfed4bfff has been reserved
[    0.504110] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.504116] pci 0000:00:1c.0:   IO window: 0x2000-0x2fff
[    0.504128] pci 0000:00:1c.0:   MEM window: 0xfc000000-0xfdffffff
[    0.504135] pci 0000:00:1c.0:   PREFETCH window: 0x000000f8000000-0x000000f80fffff
[    0.504144] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
[    0.504149] pci 0000:00:1c.1:   IO window: 0x3000-0x3fff
[    0.504160] pci 0000:00:1c.1:   MEM window: 0xdc000000-0xdf3fffff
[    0.504166] pci 0000:00:1c.1:   PREFETCH window: 0x000000dfe00000-0x000000dfefffff
[    0.504175] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:04
[    0.504180] pci 0000:00:1c.2:   IO window: 0x4000-0x4fff
[    0.504188] pci 0000:00:1c.2:   MEM window: 0xd8000000-0xd9ffffff
[    0.504194] pci 0000:00:1c.2:   PREFETCH window: 0x000000dfb00000-0x000000dfbfffff
[    0.504203] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:05
[    0.504208] pci 0000:00:1c.3:   IO window: 0x5000-0x5fff
[    0.504216] pci 0000:00:1c.3:   MEM window: 0xd4000000-0xd5ffffff
[    0.504224] pci 0000:00:1c.3:   PREFETCH window: 0x000000df800000-0x000000df8fffff
[    0.504233] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:0d
[    0.504238] pci 0000:00:1c.4:   IO window: 0x6000-0x6fff
[    0.504246] pci 0000:00:1c.4:   MEM window: 0xd0000000-0xd1ffffff
[    0.504252] pci 0000:00:1c.4:   PREFETCH window: 0x000000df500000-0x000000df5fffff
[    0.504264] pci 0000:15:00.0: CardBus bridge, secondary bus 0000:16
[    0.504266] pci 0000:15:00.0:   IO window: 0x007000-0x0070ff
[    0.504275] pci 0000:15:00.0:   IO window: 0x007400-0x0074ff
[    0.504284] pci 0000:15:00.0:   PREFETCH window: 0xf4000000-0xf7ffffff
[    0.504291] pci 0000:15:00.0:   MEM window: 0x80000000-0x83ffffff
[    0.504299] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:15
[    0.504304] pci 0000:00:1e.0:   IO window: 0x7000-0xafff
[    0.504316] pci 0000:00:1e.0:   MEM window: 0xf8300000-0xfbffffff
[    0.504325] pci 0000:00:1e.0:   PREFETCH window: 0x000000f4000000-0x000000f7ffffff
[    0.504356] pci 0000:00:1c.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.504363] pci 0000:00:1c.0: setting latency timer to 64
[    0.504381] pci 0000:00:1c.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.504386] pci 0000:00:1c.1: setting latency timer to 64
[    0.504396] pci 0000:00:1c.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.504400] pci 0000:00:1c.2: setting latency timer to 64
[    0.504415] pci 0000:00:1c.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.504422] pci 0000:00:1c.3: setting latency timer to 64
[    0.504437] pci 0000:00:1c.4: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.504443] pci 0000:00:1c.4: setting latency timer to 64
[    0.504450] pci 0000:00:1e.0: enabling device (0005 -> 0007)
[    0.504457] pci 0000:00:1e.0: setting latency timer to 64
[    0.504473] pci 0000:15:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.504481] pci 0000:15:00.0: setting latency timer to 64
[    0.504487] bus: 00 index 0 io port: [0x00-0xffff]
[    0.504489] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.504491] bus: 02 index 0 io port: [0x2000-0x2fff]
[    0.504493] bus: 02 index 1 mmio: [0xfc000000-0xfdffffff]
[    0.504494] bus: 02 index 2 mmio: [0xf8000000-0xf80fffff]
[    0.504496] bus: 02 index 3 mmio: [0x0-0x0]
[    0.504498] bus: 03 index 0 io port: [0x3000-0x3fff]
[    0.504499] bus: 03 index 1 mmio: [0xdc000000-0xdf3fffff]
[    0.504501] bus: 03 index 2 mmio: [0xdfe00000-0xdfefffff]
[    0.504502] bus: 03 index 3 mmio: [0x0-0x0]
[    0.504504] bus: 04 index 0 io port: [0x4000-0x4fff]
[    0.504505] bus: 04 index 1 mmio: [0xd8000000-0xd9ffffff]
[    0.504507] bus: 04 index 2 mmio: [0xdfb00000-0xdfbfffff]
[    0.504509] bus: 04 index 3 mmio: [0x0-0x0]
[    0.504510] bus: 05 index 0 io port: [0x5000-0x5fff]
[    0.504512] bus: 05 index 1 mmio: [0xd4000000-0xd5ffffff]
[    0.504514] bus: 05 index 2 mmio: [0xdf800000-0xdf8fffff]
[    0.504515] bus: 05 index 3 mmio: [0x0-0x0]
[    0.504516] bus: 0d index 0 io port: [0x6000-0x6fff]
[    0.504518] bus: 0d index 1 mmio: [0xd0000000-0xd1ffffff]
[    0.504520] bus: 0d index 2 mmio: [0xdf500000-0xdf5fffff]
[    0.504521] bus: 0d index 3 mmio: [0x0-0x0]
[    0.504523] bus: 15 index 0 io port: [0x7000-0xafff]
[    0.504525] bus: 15 index 1 mmio: [0xf8300000-0xfbffffff]
[    0.504526] bus: 15 index 2 mmio: [0xf4000000-0xf7ffffff]
[    0.504528] bus: 15 index 3 io port: [0x00-0xffff]
[    0.504529] bus: 15 index 4 mmio: [0x000000-0xffffffff]
[    0.504531] bus: 16 index 0 io port: [0x7000-0x70ff]
[    0.504533] bus: 16 index 1 io port: [0x7400-0x74ff]
[    0.504534] bus: 16 index 2 mmio: [0xf4000000-0xf7ffffff]
[    0.504536] bus: 16 index 3 mmio: [0x80000000-0x83ffffff]
[    0.504542] NET: Registered protocol family 2
[    0.517052] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.517243] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.517534] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.517686] TCP: Hash tables configured (established 131072 bind 65536)
[    0.517689] TCP reno registered
[    0.521062] NET: Registered protocol family 1
[    0.521159] checking if image is initramfs... it is
[    1.027995] Freeing initrd memory: 7378k freed
[    1.028037] Simple Boot Flag at 0x35 set to 0x1
[    1.028199] cpufreq: No nForce2 chipset.
[    1.028314] audit: initializing netlink socket (disabled)
[    1.028331] type=2000 audit(1250641523.025:1): initialized
[    1.034534] highmem bounce pool size: 64 pages
[    1.034538] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.035623] VFS: Disk quotas dquot_6.5.1
[    1.035669] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.036172] fuse init (API version 7.10)
[    1.036236] msgmni has been set to 1699
[    1.036411] alg: No test for stdrng (krng)
[    1.036423] io scheduler noop registered
[    1.036425] io scheduler anticipatory registered
[    1.036427] io scheduler deadline registered
[    1.036437] io scheduler cfq registered (default)
[    1.036448] pci 0000:00:02.0: Boot video device
[    1.045269] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.045344] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.045399] pcieport-driver 0000:00:1c.0: irq 2303 for MSI/MSI-X
[    1.045420] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.045431] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.045440] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.045542] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    1.045615] pcieport-driver 0000:00:1c.1: found MSI capability
[    1.045666] pcieport-driver 0000:00:1c.1: irq 2302 for MSI/MSI-X
[    1.045687] pci_express 0000:00:1c.1:pcie00: allocate port service
[    1.045696] pci_express 0000:00:1c.1:pcie02: allocate port service
[    1.045708] pci_express 0000:00:1c.1:pcie03: allocate port service
[    1.045806] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    1.045875] pcieport-driver 0000:00:1c.2: found MSI capability
[    1.045926] pcieport-driver 0000:00:1c.2: irq 2301 for MSI/MSI-X
[    1.045956] pci_express 0000:00:1c.2:pcie00: allocate port service
[    1.045966] pci_express 0000:00:1c.2:pcie02: allocate port service
[    1.045975] pci_express 0000:00:1c.2:pcie03: allocate port service
[    1.046060] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    1.046123] pcieport-driver 0000:00:1c.3: found MSI capability
[    1.046172] pcieport-driver 0000:00:1c.3: irq 2300 for MSI/MSI-X
[    1.046195] pci_express 0000:00:1c.3:pcie00: allocate port service
[    1.046205] pci_express 0000:00:1c.3:pcie02: allocate port service
[    1.046219] pci_express 0000:00:1c.3:pcie03: allocate port service
[    1.046316] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    1.046386] pcieport-driver 0000:00:1c.4: found MSI capability
[    1.046440] pcieport-driver 0000:00:1c.4: irq 2299 for MSI/MSI-X
[    1.046456] pci_express 0000:00:1c.4:pcie00: allocate port service
[    1.046466] pci_express 0000:00:1c.4:pcie02: allocate port service
[    1.046475] pci_express 0000:00:1c.4:pcie03: allocate port service
[    1.046567] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.047171] pciehp 0000:00:1c.0:pcie02: HPC vendor_id 8086 device_id 283f ss_vid 0 ss_did 0
[    1.047232] pciehp 0000:00:1c.0:pcie02: service driver pciehp loaded
[    1.047809] pciehp 0000:00:1c.1:pcie02: HPC vendor_id 8086 device_id 2841 ss_vid 0 ss_did 0
[    1.047860] pciehp 0000:00:1c.1:pcie02: service driver pciehp loaded
[    1.048450] pciehp 0000:00:1c.2:pcie02: HPC vendor_id 8086 device_id 2843 ss_vid 0 ss_did 0
[    1.048508] pciehp 0000:00:1c.2:pcie02: service driver pciehp loaded
[    1.049086] pciehp 0000:00:1c.3:pcie02: HPC vendor_id 8086 device_id 2845 ss_vid 0 ss_did 0
[    1.049141] pciehp 0000:00:1c.3:pcie02: service driver pciehp loaded
[    1.049725] pciehp 0000:00:1c.4:pcie02: HPC vendor_id 8086 device_id 2847 ss_vid 0 ss_did 0
[    1.049779] pciehp 0000:00:1c.4:pcie02: service driver pciehp loaded
[    1.049786] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.050203] ACPI: AC Adapter [AC] (on-line)
[    1.084491] ACPI: Battery Slot [BAT0] (battery present)
[    1.084554] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.084557] ACPI: Power Button (FF) [PWRF]
[    1.084591] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    1.085159] ACPI: Lid Switch [LID]
[    1.085194] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.085201] ACPI: Sleep Button (CM) [SLPB]
[    1.085671] ACPI: SSDT 7D6E1B32, 0306 (r1  PmRef  Cpu0Ist      100 INTL 20050513)
[    1.086151] ACPI: SSDT 7D6E1EBD, 085E (r1  PmRef  Cpu0Cst      100 INTL 20050513)
[    1.089003] Monitor-Mwait will be used to enter C-1 state
[    1.089006] Monitor-Mwait will be used to enter C-2 state
[    1.089008] Monitor-Mwait will be used to enter C-3 state
[    1.089019] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.089037] processor ACPI_CPU:00: registered as cooling_device0
[    1.089040] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.089368] ACPI: SSDT 7D6E1A6A, 00C8 (r1  PmRef  Cpu1Ist      100 INTL 20050513)
[    1.089793] ACPI: SSDT 7D6E1E38, 0085 (r1  PmRef  Cpu1Cst      100 INTL 20050513)
[    1.093905] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    1.093919] processor ACPI_CPU:01: registered as cooling_device1
[    1.093922] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.100067] thermal LNXTHERM:01: registered as thermal_zone0
[    1.102828] ACPI: Thermal Zone [THM0] (49 C)
[    1.103745] thermal LNXTHERM:02: registered as thermal_zone1
[    1.104963] ACPI: Thermal Zone [THM1] (39 C)
[    1.105004] isapnp: Scanning for PnP cards...
[    1.462568] isapnp: No Plug & Play device found
[    1.472127] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.472955] brd: module loaded
[    1.473198] loop: module loaded
[    1.473252] Fixed MDIO Bus: probed
[    1.473256] PPP generic driver version 2.4.2
[    1.473298] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    1.473320] Driver 'sd' needs updating - please use bus_type methods
[    1.473330] Driver 'sr' needs updating - please use bus_type methods
[    1.473362] ahci 0000:00:1f.2: version 3.0
[    1.473377] ahci 0000:00:1f.2: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    1.473425] ahci 0000:00:1f.2: irq 2298 for MSI/MSI-X
[    1.473497] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 1.5 Gbps 0x1 impl SATA mode
[    1.473499] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part 
[    1.473508] ahci 0000:00:1f.2: setting latency timer to 64
[    1.473641] scsi0 : ahci
[    1.473714] scsi1 : ahci
[    1.473771] scsi2 : ahci
[    1.473824] ata1: SATA max UDMA/133 abar m2048@0xfe226000 port 0xfe226100 irq 2298
[    1.473826] ata2: DUMMY
[    1.473827] ata3: DUMMY
[    1.792037] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.792659] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 succeeded
[    1.792662] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[    1.792664] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    1.842573] ata1.00: ATA-7: WDC WD1600BEVS-08RST2, 08.01G08, max UDMA/133
[    1.842575] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.843517] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 succeeded
[    1.843519] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[    1.843522] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    1.844214] ata1.00: configured for UDMA/133
[    1.861563] ata1.00: configured for UDMA/133
[    1.861565] ata1: EH complete
[    1.861690] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600BEVS-0 08.0 PQ: 0 ANSI: 5
[    1.861760] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[    1.861773] sd 0:0:0:0: [sda] Write Protect is off
[    1.861775] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.861795] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.861838] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[    1.861849] sd 0:0:0:0: [sda] Write Protect is off
[    1.861851] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.861870] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.861874]  sda: sda1 sda2 < sda5 >
[    1.900618] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.900652] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.900690] ata_piix 0000:00:1f.1: version 2.12
[    1.900698] ata_piix 0000:00:1f.1: PCI INT C -> GSI 16 (level, low) -> IRQ 16
[    1.900737] ata_piix 0000:00:1f.1: setting latency timer to 64
[    1.900824] scsi3 : ata_piix
[    1.900902] scsi4 : ata_piix
[    1.901603] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1c00 irq 14
[    1.901606] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1c08 irq 15
[    2.064561] ata4.00: ATAPI: DVD/CDRW UJDA775, CB03, max UDMA/33
[    2.080450] ata4.00: configured for UDMA/33
[    2.080776] ata5: port disabled. ignoring.
[    2.082199] scsi 3:0:0:0: CD-ROM            MATSHITA DVD/CDRW UJDA775 CB03 PQ: 0 ANSI: 5
[    2.085269] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    2.085271] Uniform CD-ROM driver Revision: 3.20
[    2.085336] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    2.085362] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    2.085904] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.086429] ehci_hcd 0000:00:1a.7: power state changed by ACPI to D0
[    2.086435] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    2.086446] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    2.086449] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    2.086493] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    2.090404] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    2.090417] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xfe226c00
[    2.104027] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    2.104081] usb usb1: configuration #1 chosen from 1 choice
[    2.104107] hub 1-0:1.0: USB hub found
[    2.104113] hub 1-0:1.0: 4 ports detected
[    2.104683] ehci_hcd 0000:00:1d.7: power state changed by ACPI to D0
[    2.104692] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    2.104702] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.104705] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.104740] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    2.108652] ehci_hcd 0000:00:1d.7: debug port 1
[    2.108661] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    2.108674] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xfe227000
[    2.124026] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    2.124068] usb usb2: configuration #1 chosen from 1 choice
[    2.124088] hub 2-0:1.0: USB hub found
[    2.124093] hub 2-0:1.0: 6 ports detected
[    2.124171] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.124185] uhci_hcd: USB Universal Host Controller Interface driver
[    2.124203] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.124211] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    2.124216] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    2.124254] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    2.124291] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00001860
[    2.124353] usb usb3: configuration #1 chosen from 1 choice
[    2.124374] hub 3-0:1.0: USB hub found
[    2.124380] hub 3-0:1.0: 2 ports detected
[    2.124804] uhci_hcd 0000:00:1a.1: power state changed by ACPI to D0
[    2.124809] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.124815] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    2.124818] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    2.124853] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    2.124890] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001880
[    2.124949] usb usb4: configuration #1 chosen from 1 choice
[    2.124968] hub 4-0:1.0: USB hub found
[    2.124973] hub 4-0:1.0: 2 ports detected
[    2.125510] uhci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[    2.125515] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.125521] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.125524] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.125561] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    2.125600] uhci_hcd 0000:00:1d.0: irq 16, io base 0x000018a0
[    2.125659] usb usb5: configuration #1 chosen from 1 choice
[    2.125678] hub 5-0:1.0: USB hub found
[    2.125683] hub 5-0:1.0: 2 ports detected
[    2.125754] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.125764] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.125769] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.125800] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    2.125836] uhci_hcd 0000:00:1d.1: irq 17, io base 0x000018c0
[    2.125894] usb usb6: configuration #1 chosen from 1 choice
[    2.125916] hub 6-0:1.0: USB hub found
[    2.125921] hub 6-0:1.0: 2 ports detected
[    2.126469] uhci_hcd 0000:00:1d.2: power state changed by ACPI to D0
[    2.126475] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.126480] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.126483] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.126516] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    2.126554] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018e0
[    2.126617] usb usb7: configuration #1 chosen from 1 choice
[    2.126636] hub 7-0:1.0: USB hub found
[    2.126641] hub 7-0:1.0: 2 ports detected
[    2.126750] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    2.135048] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.135052] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.140079] mice: PS/2 mouse device common for all mice
[    2.156069] rtc_cmos 00:07: RTC can wake from S4
[    2.156094] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    2.156127] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    2.156172] device-mapper: uevent: version 1.0.3
[    2.156246] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    2.156336] device-mapper: multipath: version 1.0.5 loaded
[    2.156338] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.156411] EISA: Probing bus 0 at eisa.0
[    2.156419] Cannot allocate resource for EISA slot 1
[    2.156421] Cannot allocate resource for EISA slot 2
[    2.156423] Cannot allocate resource for EISA slot 3
[    2.156424] Cannot allocate resource for EISA slot 4
[    2.156426] Cannot allocate resource for EISA slot 5
[    2.156428] Cannot allocate resource for EISA slot 6
[    2.156429] Cannot allocate resource for EISA slot 7
[    2.156431] Cannot allocate resource for EISA slot 8
[    2.156433] EISA: Detected 0 cards.
[    2.156557] cpuidle: using governor ladder
[    2.156651] cpuidle: using governor menu
[    2.157041] TCP cubic registered
[    2.157116] NET: Registered protocol family 10
[    2.157446] lo: Disabled Privacy Extensions
[    2.157701] NET: Registered protocol family 17
[    2.157714] Bluetooth: L2CAP ver 2.11
[    2.157715] Bluetooth: L2CAP socket layer initialized
[    2.157717] Bluetooth: SCO (Voice Link) ver 0.6
[    2.157718] Bluetooth: SCO socket layer initialized
[    2.157792] Bluetooth: RFCOMM socket layer initialized
[    2.157799] Bluetooth: RFCOMM TTY layer initialized
[    2.157800] Bluetooth: RFCOMM ver 1.10
[    2.158608] Using IPI No-Shortcut mode
[    2.158665] registered taskstats version 1
[    2.158776]   Magic number: 5:809:405
[    2.158875] rtc_cmos 00:07: setting system clock to 2009-08-19 00:25:24 UTC (1250641524)
[    2.158877] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.158879] EDD information not available.
[    2.159137] Freeing unused kernel memory: 532k freed
[    2.159283] Write protecting the kernel text: 4116k
[    2.159343] Write protecting the kernel read-only data: 1528k
[    2.161633] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    2.323030] e1000e: Intel(R) PRO/1000 Network Driver - 0.3.3.3-k6
[    2.323033] e1000e: Copyright (c) 1999-2008 Intel Corporation.
[    2.323105] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.323120] e1000e 0000:00:19.0: setting latency timer to 64
[    2.323352] e1000e 0000:00:19.0: irq 2297 for MSI/MSI-X
[    2.367988] ohci1394 0000:15:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.368025] ohci1394 0000:15:00.1: setting latency timer to 64
[    2.420422] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[f8301000-f83017ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    2.536172] usb 2-6: new high speed USB device using ehci_hcd and address 2
[    2.570780] 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:1e:37:8e:2a:5a
[    2.570783] 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    2.570820] 0000:00:19.0: eth0: MAC: 5, PHY: 6, PBA No: 1008ff-0ff
[    2.668724] usb 2-6: configuration #1 chosen from 1 choice
[    2.674306] PM: Starting manual resume from disk
[    2.674309] PM: Resume from partition 8:5
[    2.674310] PM: Checking hibernation image.
[    2.674508] PM: Resume from disk failed.
[    2.724796] kjournald starting.  Commit interval 5 seconds
[    2.724839] EXT3-fs: mounted filesystem with ordered data mode.
[    2.908082] usb 3-1: new full speed USB device using uhci_hcd and address 2
[    3.000316] Clocksource tsc unstable (delta = -228838628 ns)
[    3.069427] usb 3-1: configuration #1 chosen from 1 choice
[    3.724160] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00061b032a1fea68]
[    9.744081] udev: starting version 141
[    9.919039] cfg80211: Calling CRDA to update world regulatory domain
[    9.961930] iTCO_vendor_support: vendor-support=0
[    9.964093] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[    9.964408] iTCO_wdt: Found a ICH8M-E TCO device (Version=2, TCOBASE=0x1060)
[    9.964490] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   10.004659] Linux agpgart interface v0.103
[   10.008147] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
[   10.008969] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
[   10.011916] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[   10.156525] HDA Intel 0000:00:1b.0: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   10.156529] hda_intel: probe_mask set to 0x1 for device 17aa:20ac
[   10.156571] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   10.169664] yenta_cardbus 0000:15:00.0: CardBus bridge found [17aa:20c6]
[   10.177006] Bluetooth: Generic Bluetooth USB driver ver 0.3
[   10.177103] usbcore: registered new interface driver btusb
[   10.187926] Non-volatile memory driver v1.2
[   10.196867] acpi device:03: registered as cooling_device2
[   10.197057] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/input/input5
[   10.200134] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   10.205279] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   10.206542] sdhci: Secure Digital Host Controller Interface driver
[   10.206543] sdhci: Copyright(c) Pierre Ossman
[   10.208282] ricoh-mmc: Ricoh MMC Controller disabling driver
[   10.208284] ricoh-mmc: Copyright(c) Philip Langdale
[   10.241849] thinkpad_acpi: ThinkPad ACPI Extras v0.21
[   10.241852] thinkpad_acpi: http://ibm-acpi.sf.net/
[   10.241853] thinkpad_acpi: ThinkPad BIOS 7LETB0WW (2.10 ), EC 7KHT24WW-1.08
[   10.241855] thinkpad_acpi: Lenovo ThinkPad T61, model 6465CTO
[   10.245289] thinkpad_acpi: ACPI backlight control delay disabled
[   10.246166] thinkpad_acpi: radio switch found; radios are enabled
[   10.246250] thinkpad_acpi: This ThinkPad has standard ACPI backlight brightness control, supported by the ACPI video driver
[   10.246252] thinkpad_acpi: Disabling thinkpad-acpi brightness events by default...
[   10.261176] Registered led device: tpacpi::thinklight
[   10.261210] Registered led device: tpacpi::power
[   10.261222] Registered led device: tpacpi:orange:batt
[   10.261234] Registered led device: tpacpi:green:batt
[   10.261261] Registered led device: tpacpi::dock_active
[   10.261273] Registered led device: tpacpi::bay_active
[   10.261285] Registered led device: tpacpi::dock_batt
[   10.261297] Registered led device: tpacpi::unknown_led
[   10.261309] Registered led device: tpacpi::standby
[   10.264334] thinkpad_acpi: Standard ACPI backlight interface available, not loading native one.
[   10.264662] input: ThinkPad Extra Buttons as /devices/virtual/input/input7
[   10.297268] yenta_cardbus 0000:15:00.0: ISA IRQ mask 0x0cb8, PCI irq 16
[   10.297274] yenta_cardbus 0000:15:00.0: Socket status: 30000006
[   10.297278] yenta_cardbus 0000:15:00.0: pcmcia: parent PCI bridge I/O window: 0x7000 - 0xafff
[   10.297280] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x7000-0xafff: clean.
[   10.298002] yenta_cardbus 0000:15:00.0: pcmcia: parent PCI bridge Memory window: 0xf8300000 - 0xfbffffff
[   10.298004] yenta_cardbus 0000:15:00.0: pcmcia: parent PCI bridge Memory window: 0xf4000000 - 0xf7ffffff
[   10.298486] sdhci-pci 0000:15:00.2: SDHCI controller found [1180:0822] (rev 21)
[   10.298510] sdhci-pci 0000:15:00.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   10.298588] sdhci-pci 0000:15:00.2: Will use DMA mode even though HW doesn't fully claim to support it.
[   10.298594] sdhci-pci 0000:15:00.2: setting latency timer to 64
[   10.300622] mmc0: SDHCI controller on PCI [0000:15:00.2] using DMA
[   10.300649] ricoh-mmc: Ricoh MMC controller found at 0000:15:00.3 [1180:0843] (rev 11)
[   10.300686] ricoh-mmc: Controller is now disabled.
[   10.303815] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   10.303818] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[   10.303911] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   10.303924] iwl3945 0000:03:00.0: setting latency timer to 64
[   10.303952] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[   10.306492] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   10.307017] iwl3945 0000:03:00.0: irq 2296 for MSI/MSI-X
[   10.363022] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   10.364481] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   10.444469] cfg80211: World regulatory domain updated:
[   10.444472]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   10.444473]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.444475]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.444477]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.444478]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.444480]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.651847] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   10.653397] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   10.654045] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   10.654586] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   10.655266] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   11.191143] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x81a0b1, caps: 0xa04793/0x300000
[   11.191148] serio: Synaptics pass-through port at isa0060/serio1/input0
[   11.233688] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[   11.569010] hda_intel: azx_get_response timeout, switching to polling mode: last cmd=0x002f0d00
[   11.718392] lp: driver loaded but no devices found
[   11.797345] Adding 5919912k swap on /dev/sda5.  Priority:-1 extents:1 across:5919912k
[   12.326508] EXT3 FS on sda1, internal journal
[   12.477715] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   13.436080] type=1505 audit(1250641535.774:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2170
[   13.469762] type=1505 audit(1250641535.810:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2174
[   13.469829] type=1505 audit(1250641535.810:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2174
[   13.469859] type=1505 audit(1250641535.810:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2174
[   13.469888] type=1505 audit(1250641535.810:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2174
[   13.563543] type=1505 audit(1250641535.902:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2179
[   13.563685] type=1505 audit(1250641535.902:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2179
[   13.583842] type=1505 audit(1250641535.922:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2183
[   13.895320] psmouse serio2: ID: 10 00 64<6>IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   17.561836] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input9
[   17.804480] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   17.804482] vboxdrv: Successfully done.
[   17.804483] vboxdrv: Found 2 processor cores.
[   17.804565] vboxdrv: fAsync=1 offMin=0x1495f8 offMax=0x1495f8
[   17.804605] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
[   17.804607] vboxdrv: Successfully loaded version 2.1.4_OSE (interface 0x000a0009).
[   19.455741] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.455744] Bluetooth: BNEP filters: protocol multicast
[   19.473246] Bridge firewalling registered
[   20.902006] ppdev: user-space parallel port driver
 
```

---

### Post by kayvortex on 2009-08-18
Well, don't thank me just yet!

No, which USB port you plug it into shouldn't matter: I thought it would be best to rule out the possibility that the problem lay with a faulty port; but, that's not it. I also can't think of anything to do with (un)mounting that would have caused it to stop working.

That dmesg is from *after* plugging the HD in, right? You didn't reboot, not plug the HD in and then post the dmesg contents did you? Because I don't see anything in there about your HD, which means something very odd is going on. 

Can you tell me the make and model of your HD. There might be known problems with it on the internet somewhere that I can check for. Could you also tell me how you use it (do you just plug it in and switch it on? Or, is there something unusual that you have to do?), and if you can remember doing anything unusual between it working and not.

In the mean time, do you have another operating system that you can use so that you can check whether the HD is working OK on that? It may be that your HD might have bit the dust.

---

### Post by tmurph on 2009-08-18
Well I can at least thank you for your patience and attemp!

That dmesg is from earlier when the harddrive was already plugged in and not being recognized. I just rebooted and will post the new dmesg below.

The make is a simpledrive 320: [http://www.simpletech.com/parts/s320u.htm](http://www.simpletech.com/parts/s320u.htm)
To use it, you plug it into the wall and then to the computer and it automatically turns on. It only has some music folers, and a copy of some of my iTunes library in an .xml format.

The only fiddling I was doing was trying to sync the harddrive to the rythm box library. I was trying to adjust where rhythm box was locating music libraries. I was using a guide on a website (dont have the address) to help me. I was using gconf-editor to do this. I just retraced my steps back there and the locations I set are missing.

Another weird thing is happening that I forgot to mention. If I search for any music on GNOME-do it still comes up, with the album art as if it was there, but when you would try to play it nothing happens besides rythm box opening to a empty library.

Here is the new dmesg after reboot and new plugin:

```
 [    0.000000] BIOS EBDA/lowmem at: 0009d800/0009d800
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-15-generic (buildd@rothera) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #48-Ubuntu SMP Wed Jul 29 08:54:56 UTC 2009 (Ubuntu 2.6.28-15.48-generic)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d800 (usable)
[    0.000000]  BIOS-e820: 000000000009d800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007d6b0000 (usable)
[    0.000000]  BIOS-e820: 000000007d6b0000 - 000000007d6cc000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007d6cc000 - 000000007d700000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007d700000 - 000000007e000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0x7d6b0 max_arch_pfn = 0x100000
[    0.000000] Scanning 2 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 0000000000007000 (usable)
[    0.000000]  modified: 0000000000007000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 0000000000090800 (usable)
[    0.000000]  modified: 000000000009d800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007d6b0000 (usable)
[    0.000000]  modified: 000000007d6b0000 - 000000007d6cc000 (ACPI data)
[    0.000000]  modified: 000000007d6cc000 - 000000007d700000 (ACPI NVS)
[    0.000000]  modified: 000000007d700000 - 000000007e000000 (reserved)
[    0.000000]  modified: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  modified: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  modified: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000
[    0.000000] RAMDISK: 378bb000 - 37fefb3b
[    0.000000] Allocated new RAMDISK: 0087d000 - 00fb1b3b
[    0.000000] Move RAMDISK from 00000000378bb000 - 0000000037fefb3a to 0087d000 - 00fb1b3a
[    0.000000] ACPI: RSDP 000F68D0, 0024 (r2 LENOVO)
[    0.000000] ACPI: XSDT 7D6BB731, 0094 (r1 LENOVO TP-7L        2100  LTP        0)
[    0.000000] ACPI: FACP 7D6BB800, 00F4 (r3 LENOVO TP-7L        2100 LNVO        1)
[    0.000000] ACPI Warning (tbfadt-0460): Optional field "Gpe1Block" has zero address or length: 000000000000102C/0 [20080926]
[    0.000000] ACPI: DSDT 7D6BBC1D, FF1F (r1 LENOVO TP-7L        2100 MSFT  3000000)
[    0.000000] ACPI: FACS 7D6E4000, 0040
[    0.000000] ACPI: SSDT 7D6BB9B4, 0269 (r1 LENOVO TP-7L        2100 MSFT  3000000)
[    0.000000] ACPI: ECDT 7D6CBB3C, 0052 (r1 LENOVO TP-7L        2100 LNVO        1)
[    0.000000] ACPI: TCPA 7D6CBB8E, 0032 (r2 LENOVO TP-7L        2100 LNVO        1)
[    0.000000] ACPI: APIC 7D6CBBC0, 0068 (r1 LENOVO TP-7L        2100 LNVO        1)
[    0.000000] ACPI: MCFG 7D6CBC28, 003C (r1 LENOVO TP-7L        2100 LNVO        1)
[    0.000000] ACPI: HPET 7D6CBC64, 0038 (r1 LENOVO TP-7L        2100 LNVO        1)
[    0.000000] ACPI: SLIC 7D6CBDF0, 0176 (r1 LENOVO TP-7L        2100  LTP        0)
[    0.000000] ACPI: BOOT 7D6CBF66, 0028 (r1 LENOVO TP-7L        2100  LTP        1)
[    0.000000] ACPI: ASF! 7D6CBF8E, 0072 (r16 LENOVO TP-7L        2100 PTL         1)
[    0.000000] ACPI: SSDT 7D6E271B, 025F (r1 LENOVO TP-7L        2100 INTL 20050513)
[    0.000000] ACPI: SSDT 7D6E297A, 00A6 (r1 LENOVO TP-7L        2100 INTL 20050513)
[    0.000000] ACPI: SSDT 7D6E2A20, 04F7 (r1 LENOVO TP-7L        2100 INTL 20050513)
[    0.000000] ACPI: SSDT 7D6E2F17, 01D8 (r1 LENOVO TP-7L        2100 INTL 20050513)
[    0.000000] ACPI: DMI detected: Lenovo ThinkPad T61
[    0.000000] ACPI: Added _OSI(Linux)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1122MB HIGHMEM available.
[    0.000000] 883MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 373fe000
[    0.000000]   low ram: 00000000 - 373fe000
[    0.000000]   bootmap 00012000 - 00018e80
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00373fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008780ac]    TEXT DATA BSS ==> [0000100000 - 00008780ac]
[    0.000000]   #4 [0000879000 - 000087d000]    INIT_PG_TABLE ==> [0000879000 - 000087d000]
[    0.000000]   #5 [000009d800 - 0000100000]    BIOS reserved ==> [000009d800 - 0000100000]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [000087d000 - 0000fb1b3b]      NEW RAMDISK ==> [000087d000 - 0000fb1b3b]
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
[    0.000000] found SMP MP-table at [c00f6900] 000f6900
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000373fe
[    0.000000]   HighMem  0x000373fe -> 0x0007d6b0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x00000007
[    0.000000]     0: 0x00000010 -> 0x00000090
[    0.000000]     0: 0x00000100 -> 0x0007d6b0
[    0.000000] On node 0 totalpages: 513587
[    0.000000] free_area_init_node: node 0, pgdat c06cb500, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3939 pages, LIFO batch:0
[    0.000000]   Normal zone: 1736 pages used for memmap
[    0.000000]   Normal zone: 220470 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2246 pages used for memmap
[    0.000000]   HighMem zone: 285164 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 0000000000007000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 0000000000090000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
[    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 7e000000:72000000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 509573
[    0.000000] Kernel command line: root=UUID=c771e946-e54c-40c6-82d3-859980adbc64 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] TSC: PIT calibration matches PMTIMER. 1 loops
[    0.000000] Detected 2393.565 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] allocated 10274240 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 2011348k/2054848k available (4115k kernel code, 42104k reserved, 2199k data, 532k init, 1149640k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
[    0.004000]       .init : 0xc0733000 - 0xc07b8000   ( 532 kB)
[    0.004000]       .data : 0xc0504f5f - 0xc072ae60   (2199 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0504f5f   (4115 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 4787.13 BogoMIPS (lpj=9574260)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] Initializing cgroup subsys freezer
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 3072K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using mwait in idle threads.
[    0.004000] Checking 'hlt' instruction... OK.
[    0.020008] ACPI: Core revision 20080926
[    0.032191] ACPI: Checking initramfs for custom DSDT
[    0.800654] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.843693] CPU0: Intel(R) Core(TM)2 Duo CPU     T8300  @ 2.40GHz stepping 06
[    0.844002] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 4788.02 BogoMIPS (lpj=9576055)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 3072K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.929412] CPU1: Intel(R) Core(TM)2 Duo CPU     T8300  @ 2.40GHz stepping 06
[    0.929446] checking TSC synchronization [CPU#0 -> CPU#1]:
[    0.932002] Measured 1238184 cycles TSC warp between CPUs, turning off TSC clock.
[    0.932002] Marking TSC unstable due to check_tsc_sync_source failed
[    0.932061] Brought up 2 CPUs
[    0.932067] Total of 2 processors activated (9575.15 BogoMIPS).
[    0.932178] CPU0 attaching sched-domain:
[    0.932183]  domain 0: span 0-1 level MC
[    0.932190]   groups: 0 1
[    0.932203] CPU1 attaching sched-domain:
[    0.932207]  domain 0: span 0-1 level MC
[    0.932212]   groups: 1 0
[    0.932350] net_namespace: 776 bytes
[    0.932350] Booting paravirtualized kernel on bare hardware
[    0.932688] Time:  2:41:34  Date: 08/19/09
[    0.932688] regulator: core version 0.5
[    0.932688] NET: Registered protocol family 16
[    0.932688] EISA bus registered
[    0.932688] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.932688] ACPI: bus type pci registered
[    0.932688] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
[    0.932688] PCI: MCFG area at f0000000 reserved in E820
[    0.932688] PCI: Using MMCONFIG for extended config space
[    0.932688] PCI: Using configuration type 1 for base access
[    0.941207] ACPI: EC: EC description table is found, configuring boot EC
[    0.957036] ACPI: BIOS _OSI(Linux) query honored via DMI
[    0.956040] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.973855] ACPI: Interpreter enabled
[    0.973865] ACPI: (supports S0 S3 S4 S5)
[    0.973911] ACPI: Using IOAPIC for interrupt routing
[    1.006491] ACPI: EC: GPE = 0x12, I/O: command/status = 0x66, data = 0x62
[    1.006498] ACPI: EC: driver started in interrupt mode
[    1.011534] ACPI: ACPI Dock Station Driver: 3 docks/bays found
[    1.011565] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    1.011755] pci 0000:00:02.0: reg 10 64bit mmio: [0xf8100000-0xf81fffff]
[    1.011773] pci 0000:00:02.0: reg 18 64bit mmio: [0xe0000000-0xefffffff]
[    1.011784] pci 0000:00:02.0: reg 20 io port: [0x1800-0x1807]
[    1.012061] pci 0000:00:02.1: reg 10 64bit mmio: [0xf8200000-0xf82fffff]
[    1.012365] pci 0000:00:19.0: reg 10 32bit mmio: [0xfe000000-0xfe01ffff]
[    1.012389] pci 0000:00:19.0: reg 14 32bit mmio: [0xfe025000-0xfe025fff]
[    1.012412] pci 0000:00:19.0: reg 18 io port: [0x1840-0x185f]
[    1.012520] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    1.012534] pci 0000:00:19.0: PME# disabled
[    1.012696] pci 0000:00:1a.0: reg 20 io port: [0x1860-0x187f]
[    1.012887] pci 0000:00:1a.1: reg 20 io port: [0x1880-0x189f]
[    1.013069] pci 0000:00:1a.7: reg 10 32bit mmio: [0xfe226c00-0xfe226fff]
[    1.013213] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    1.013227] pci 0000:00:1a.7: PME# disabled
[    1.013385] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfe020000-0xfe023fff]
[    1.013512] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    1.013525] pci 0000:00:1b.0: PME# disabled
[    1.013729] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    1.013742] pci 0000:00:1c.0: PME# disabled
[    1.013955] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    1.013969] pci 0000:00:1c.1: PME# disabled
[    1.014182] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    1.014196] pci 0000:00:1c.2: PME# disabled
[    1.014409] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    1.014423] pci 0000:00:1c.3: PME# disabled
[    1.014642] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    1.014655] pci 0000:00:1c.4: PME# disabled
[    1.014849] pci 0000:00:1d.0: reg 20 io port: [0x18a0-0x18bf]
[    1.015040] pci 0000:00:1d.1: reg 20 io port: [0x18c0-0x18df]
[    1.015231] pci 0000:00:1d.2: reg 20 io port: [0x18e0-0x18ff]
[    1.015436] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfe227000-0xfe2273ff]
[    1.015580] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    1.015594] pci 0000:00:1d.7: PME# disabled
[    1.016045] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    1.016055] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH6 GPIO
[    1.016158] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    1.016181] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    1.016204] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    1.016227] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    1.016250] pci 0000:00:1f.1: reg 20 io port: [0x1c00-0x1c0f]
[    1.016468] pci 0000:00:1f.2: reg 10 io port: [0x1c50-0x1c57]
[    1.016492] pci 0000:00:1f.2: reg 14 io port: [0x1c44-0x1c47]
[    1.016515] pci 0000:00:1f.2: reg 18 io port: [0x1c48-0x1c4f]
[    1.016538] pci 0000:00:1f.2: reg 1c io port: [0x1c40-0x1c43]
[    1.016561] pci 0000:00:1f.2: reg 20 io port: [0x1c20-0x1c3f]
[    1.016584] pci 0000:00:1f.2: reg 24 32bit mmio: [0xfe226000-0xfe2267ff]
[    1.016646] pci 0000:00:1f.2: PME# supported from D3hot
[    1.016659] pci 0000:00:1f.2: PME# disabled
[    1.016757] pci 0000:00:1f.3: reg 10 32bit mmio: [0xfe227400-0xfe2274ff]
[    1.016836] pci 0000:00:1f.3: reg 20 io port: [0x1c60-0x1c7f]
[    1.017090] pci 0000:00:1c.0: bridge io port: [0x2000-0x2fff]
[    1.017104] pci 0000:00:1c.0: bridge 32bit mmio: [0xfc000000-0xfdffffff]
[    1.017128] pci 0000:00:1c.0: bridge 64bit mmio pref: [0xf8000000-0xf80fffff]
[    1.017356] pci 0000:03:00.0: reg 10 32bit mmio: [0xdf3ff000-0xdf3fffff]
[    1.017551] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    1.017568] pci 0000:03:00.0: PME# disabled
[    1.017721] pci 0000:00:1c.1: bridge io port: [0x3000-0x3fff]
[    1.017735] pci 0000:00:1c.1: bridge 32bit mmio: [0xdc000000-0xdf3fffff]
[    1.017758] pci 0000:00:1c.1: bridge 64bit mmio pref: [0xdfe00000-0xdfefffff]
[    1.017941] pci 0000:00:1c.2: bridge io port: [0x4000-0x4fff]
[    1.017955] pci 0000:00:1c.2: bridge 32bit mmio: [0xd8000000-0xd9ffffff]
[    1.017978] pci 0000:00:1c.2: bridge 64bit mmio pref: [0xdfb00000-0xdfbfffff]
[    1.018160] pci 0000:00:1c.3: bridge io port: [0x5000-0x5fff]
[    1.018174] pci 0000:00:1c.3: bridge 32bit mmio: [0xd4000000-0xd5ffffff]
[    1.018198] pci 0000:00:1c.3: bridge 64bit mmio pref: [0xdf800000-0xdf8fffff]
[    1.018380] pci 0000:00:1c.4: bridge io port: [0x6000-0x6fff]
[    1.018393] pci 0000:00:1c.4: bridge 32bit mmio: [0xd0000000-0xd1ffffff]
[    1.018417] pci 0000:00:1c.4: bridge 64bit mmio pref: [0xdf500000-0xdf5fffff]
[    1.018554] pci 0000:15:00.0: reg 10 32bit mmio: [0xf8300000-0xf8300fff]
[    1.018589] pci 0000:15:00.0: supports D1 D2
[    1.018594] pci 0000:15:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.018608] pci 0000:15:00.0: PME# disabled
[    1.018741] pci 0000:15:00.1: reg 10 32bit mmio: [0xf8301000-0xf83017ff]
[    1.018899] pci 0000:15:00.1: supports D1 D2
[    1.018904] pci 0000:15:00.1: PME# supported from D0 D1 D2 D3hot D3cold
[    1.018918] pci 0000:15:00.1: PME# disabled
[    1.019051] pci 0000:15:00.2: reg 10 32bit mmio: [0xf8301800-0xf83018ff]
[    1.019209] pci 0000:15:00.2: supports D1 D2
[    1.019213] pci 0000:15:00.2: PME# supported from D0 D1 D2 D3hot D3cold
[    1.019227] pci 0000:15:00.2: PME# disabled
[    1.019360] pci 0000:15:00.3: reg 10 32bit mmio: [0xf8301c00-0xf8301cff]
[    1.019518] pci 0000:15:00.3: supports D1 D2
[    1.019523] pci 0000:15:00.3: PME# supported from D0 D1 D2 D3hot D3cold
[    1.019537] pci 0000:15:00.3: PME# disabled
[    1.019669] pci 0000:15:00.4: reg 10 32bit mmio: [0xf8302000-0xf83020ff]
[    1.019828] pci 0000:15:00.4: supports D1 D2
[    1.019832] pci 0000:15:00.4: PME# supported from D0 D1 D2 D3hot D3cold
[    1.019847] pci 0000:15:00.4: PME# disabled
[    1.019979] pci 0000:15:00.5: reg 10 32bit mmio: [0xf8302400-0xf83024ff]
[    1.020149] pci 0000:15:00.5: supports D1 D2
[    1.020154] pci 0000:15:00.5: PME# supported from D0 D1 D2 D3hot D3cold
[    1.020168] pci 0000:15:00.5: PME# disabled
[    1.020361] pci 0000:00:1e.0: transparent bridge
[    1.020375] pci 0000:00:1e.0: bridge io port: [0x7000-0xafff]
[    1.020389] pci 0000:00:1e.0: bridge 32bit mmio: [0xf8300000-0xfbffffff]
[    1.020412] pci 0000:00:1e.0: bridge 64bit mmio pref: [0xf4000000-0xf7ffffff]
[    1.020590] bus 00 -> node 0
[    1.020609] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.021282] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP0._PRT]
[    1.021644] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[    1.022003] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[    1.022364] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP3._PRT]
[    1.022731] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP4._PRT]
[    1.023097] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    1.033435] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11)
[    1.034002] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
[    1.034563] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
[    1.035122] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[    1.035680] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11)
[    1.036254] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11)
[    1.036812] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11)
[    1.037371] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11)
[    1.036187] ACPI: Power Resource [PUBS] (on)
[    1.040304] ACPI: WMI: Mapper loaded
[    1.040636] SCSI subsystem initialized
[    1.040750] libata version 3.00 loaded.
[    1.040845] usbcore: registered new interface driver usbfs
[    1.040880] usbcore: registered new interface driver hub
[    1.040942] usbcore: registered new device driver usb
[    1.041184] PCI: Using ACPI for IRQ routing
[    1.048019] Bluetooth: Core ver 2.13
[    1.048049] NET: Registered protocol family 31
[    1.048049] Bluetooth: HCI device and connection manager initialized
[    1.048049] Bluetooth: HCI socket layer initialized
[    1.048049] NET: Registered protocol family 8
[    1.048050] NET: Registered protocol family 20
[    1.048075] NetLabel: Initializing
[    1.048079] NetLabel:  domain hash size = 128
[    1.048083] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.048111] NetLabel:  unlabeled traffic allowed by default
[    1.048144] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    1.048155] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    1.052118] AppArmor: AppArmor Filesystem Enabled
[    1.056026] Switched to high resolution mode on CPU 0
[    1.057536] Switched to high resolution mode on CPU 1
[    1.060043] pnp: PnP ACPI init
[    1.060061] ACPI: bus type pnp registered
[    1.072613] pnp: PnP ACPI: found 11 devices
[    1.072619] ACPI: ACPI bus type pnp unregistered
[    1.072626] PnPBIOS: Disabled by ACPI PNP
[    1.072647] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    1.072654] system 00:00: iomem range 0xc0000-0xc3fff could not be reserved
[    1.072660] system 00:00: iomem range 0xc4000-0xc7fff could not be reserved
[    1.072666] system 00:00: iomem range 0xc8000-0xcbfff has been reserved
[    1.072672] system 00:00: iomem range 0xcc000-0xcffff has been reserved
[    1.072679] system 00:00: iomem range 0xd0000-0xd3fff could not be reserved
[    1.072686] system 00:00: iomem range 0xe0000-0xe3fff could not be reserved
[    1.072692] system 00:00: iomem range 0xe4000-0xe7fff could not be reserved
[    1.072698] system 00:00: iomem range 0xe8000-0xebfff could not be reserved
[    1.072704] system 00:00: iomem range 0xec000-0xeffff could not be reserved
[    1.072711] system 00:00: iomem range 0xf0000-0xfffff could not be reserved
[    1.072717] system 00:00: iomem range 0x100000-0x7dffffff could not be reserved
[    1.072725] system 00:00: iomem range 0xfec00000-0xfed3ffff could not be reserved
[    1.072731] system 00:00: iomem range 0xfed4c000-0xffffffff could not be reserved
[    1.072748] system 00:02: ioport range 0x164e-0x164f has been reserved
[    1.072754] system 00:02: ioport range 0x1000-0x107f has been reserved
[    1.072761] system 00:02: ioport range 0x1180-0x11bf has been reserved
[    1.072767] system 00:02: ioport range 0x800-0x80f has been reserved
[    1.072773] system 00:02: ioport range 0x15e0-0x15ef has been reserved
[    1.072779] system 00:02: ioport range 0x1600-0x165f could not be reserved
[    1.072786] system 00:02: iomem range 0xf0000000-0xf3ffffff has been reserved
[    1.072793] system 00:02: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    1.072799] system 00:02: iomem range 0xfed14000-0xfed17fff has been reserved
[    1.072806] system 00:02: iomem range 0xfed18000-0xfed18fff has been reserved
[    1.072813] system 00:02: iomem range 0xfed19000-0xfed19fff has been reserved
[    1.072819] system 00:02: iomem range 0xfed45000-0xfed4bfff has been reserved
[    1.107886] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    1.107897] pci 0000:00:1c.0:   IO window: 0x2000-0x2fff
[    1.107916] pci 0000:00:1c.0:   MEM window: 0xfc000000-0xfdffffff
[    1.107931] pci 0000:00:1c.0:   PREFETCH window: 0x000000f8000000-0x000000f80fffff
[    1.107955] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
[    1.107964] pci 0000:00:1c.1:   IO window: 0x3000-0x3fff
[    1.107982] pci 0000:00:1c.1:   MEM window: 0xdc000000-0xdf3fffff
[    1.107996] pci 0000:00:1c.1:   PREFETCH window: 0x000000dfe00000-0x000000dfefffff
[    1.108019] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:04
[    1.108028] pci 0000:00:1c.2:   IO window: 0x4000-0x4fff
[    1.108046] pci 0000:00:1c.2:   MEM window: 0xd8000000-0xd9ffffff
[    1.108060] pci 0000:00:1c.2:   PREFETCH window: 0x000000dfb00000-0x000000dfbfffff
[    1.108083] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:05
[    1.108092] pci 0000:00:1c.3:   IO window: 0x5000-0x5fff
[    1.108110] pci 0000:00:1c.3:   MEM window: 0xd4000000-0xd5ffffff
[    1.108125] pci 0000:00:1c.3:   PREFETCH window: 0x000000df800000-0x000000df8fffff
[    1.108147] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:0d
[    1.108156] pci 0000:00:1c.4:   IO window: 0x6000-0x6fff
[    1.108174] pci 0000:00:1c.4:   MEM window: 0xd0000000-0xd1ffffff
[    1.108189] pci 0000:00:1c.4:   PREFETCH window: 0x000000df500000-0x000000df5fffff
[    1.108220] pci 0000:15:00.0: CardBus bridge, secondary bus 0000:16
[    1.108225] pci 0000:15:00.0:   IO window: 0x007000-0x0070ff
[    1.108240] pci 0000:15:00.0:   IO window: 0x007400-0x0074ff
[    1.108254] pci 0000:15:00.0:   PREFETCH window: 0xf4000000-0xf7ffffff
[    1.108269] pci 0000:15:00.0:   MEM window: 0x80000000-0x83ffffff
[    1.108285] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:15
[    1.108294] pci 0000:00:1e.0:   IO window: 0x7000-0xafff
[    1.108312] pci 0000:00:1e.0:   MEM window: 0xf8300000-0xfbffffff
[    1.108326] pci 0000:00:1e.0:   PREFETCH window: 0x000000f4000000-0x000000f7ffffff
[    1.108373] pci 0000:00:1c.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.108389] pci 0000:00:1c.0: setting latency timer to 64
[    1.108416] pci 0000:00:1c.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.108430] pci 0000:00:1c.1: setting latency timer to 64
[    1.108456] pci 0000:00:1c.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    1.108470] pci 0000:00:1c.2: setting latency timer to 64
[    1.108496] pci 0000:00:1c.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    1.108510] pci 0000:00:1c.3: setting latency timer to 64
[    1.108534] pci 0000:00:1c.4: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.108548] pci 0000:00:1c.4: setting latency timer to 64
[    1.108562] pci 0000:00:1e.0: enabling device (0005 -> 0007)
[    1.108580] pci 0000:00:1e.0: setting latency timer to 64
[    1.108608] pci 0000:15:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.108624] pci 0000:15:00.0: setting latency timer to 64
[    1.108635] bus: 00 index 0 io port: [0x00-0xffff]
[    1.108640] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    1.108646] bus: 02 index 0 io port: [0x2000-0x2fff]
[    1.108651] bus: 02 index 1 mmio: [0xfc000000-0xfdffffff]
[    1.108656] bus: 02 index 2 mmio: [0xf8000000-0xf80fffff]
[    1.108661] bus: 02 index 3 mmio: [0x0-0x0]
[    1.108666] bus: 03 index 0 io port: [0x3000-0x3fff]
[    1.108670] bus: 03 index 1 mmio: [0xdc000000-0xdf3fffff]
[    1.108675] bus: 03 index 2 mmio: [0xdfe00000-0xdfefffff]
[    1.108680] bus: 03 index 3 mmio: [0x0-0x0]
[    1.108685] bus: 04 index 0 io port: [0x4000-0x4fff]
[    1.108689] bus: 04 index 1 mmio: [0xd8000000-0xd9ffffff]
[    1.108695] bus: 04 index 2 mmio: [0xdfb00000-0xdfbfffff]
[    1.108699] bus: 04 index 3 mmio: [0x0-0x0]
[    1.108704] bus: 05 index 0 io port: [0x5000-0x5fff]
[    1.108708] bus: 05 index 1 mmio: [0xd4000000-0xd5ffffff]
[    1.108713] bus: 05 index 2 mmio: [0xdf800000-0xdf8fffff]
[    1.108718] bus: 05 index 3 mmio: [0x0-0x0]
[    1.108722] bus: 0d index 0 io port: [0x6000-0x6fff]
[    1.108727] bus: 0d index 1 mmio: [0xd0000000-0xd1ffffff]
[    1.108732] bus: 0d index 2 mmio: [0xdf500000-0xdf5fffff]
[    1.108737] bus: 0d index 3 mmio: [0x0-0x0]
[    1.108741] bus: 15 index 0 io port: [0x7000-0xafff]
[    1.108746] bus: 15 index 1 mmio: [0xf8300000-0xfbffffff]
[    1.108752] bus: 15 index 2 mmio: [0xf4000000-0xf7ffffff]
[    1.108756] bus: 15 index 3 io port: [0x00-0xffff]
[    1.108761] bus: 15 index 4 mmio: [0x000000-0xffffffff]
[    1.108766] bus: 16 index 0 io port: [0x7000-0x70ff]
[    1.108771] bus: 16 index 1 io port: [0x7400-0x74ff]
[    1.108776] bus: 16 index 2 mmio: [0xf4000000-0xf7ffffff]
[    1.108781] bus: 16 index 3 mmio: [0x80000000-0x83ffffff]
[    1.108798] NET: Registered protocol family 2
[    1.121131] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    1.121648] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.122237] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    1.122544] TCP: Hash tables configured (established 131072 bind 65536)
[    1.122549] TCP reno registered
[    1.125145] NET: Registered protocol family 1
[    1.125402] checking if image is initramfs... it is
[    2.638649] Freeing initrd memory: 7378k freed
[    2.638721] Simple Boot Flag at 0x35 set to 0x1
[    2.639090] cpufreq: No nForce2 chipset.
[    2.639358] audit: initializing netlink socket (disabled)
[    2.639388] type=2000 audit(1250649694.636:1): initialized
[    2.657582] highmem bounce pool size: 64 pages
[    2.657593] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    2.660694] VFS: Disk quotas dquot_6.5.1
[    2.660832] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.662260] fuse init (API version 7.10)
[    2.662445] msgmni has been set to 1699
[    2.662846] alg: No test for stdrng (krng)
[    2.662873] io scheduler noop registered
[    2.662878] io scheduler anticipatory registered
[    2.662883] io scheduler deadline registered
[    2.662914] io scheduler cfq registered (default)
[    2.662936] pci 0000:00:02.0: Boot video device
[    2.685244] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    2.685397] pcieport-driver 0000:00:1c.0: found MSI capability
[    2.685503] pcieport-driver 0000:00:1c.0: irq 2303 for MSI/MSI-X
[    2.685550] pci_express 0000:00:1c.0:pcie00: allocate port service
[    2.685582] pci_express 0000:00:1c.0:pcie02: allocate port service
[    2.685609] pci_express 0000:00:1c.0:pcie03: allocate port service
[    2.685822] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    2.685973] pcieport-driver 0000:00:1c.1: found MSI capability
[    2.686072] pcieport-driver 0000:00:1c.1: irq 2302 for MSI/MSI-X
[    2.686119] pci_express 0000:00:1c.1:pcie00: allocate port service
[    2.686147] pci_express 0000:00:1c.1:pcie02: allocate port service
[    2.686175] pci_express 0000:00:1c.1:pcie03: allocate port service
[    2.686388] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    2.686538] pcieport-driver 0000:00:1c.2: found MSI capability
[    2.686638] pcieport-driver 0000:00:1c.2: irq 2301 for MSI/MSI-X
[    2.686685] pci_express 0000:00:1c.2:pcie00: allocate port service
[    2.686724] pci_express 0000:00:1c.2:pcie02: allocate port service
[    2.686752] pci_express 0000:00:1c.2:pcie03: allocate port service
[    2.686971] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    2.687121] pcieport-driver 0000:00:1c.3: found MSI capability
[    2.687220] pcieport-driver 0000:00:1c.3: irq 2300 for MSI/MSI-X
[    2.687267] pci_express 0000:00:1c.3:pcie00: allocate port service
[    2.687295] pci_express 0000:00:1c.3:pcie02: allocate port service
[    2.687323] pci_express 0000:00:1c.3:pcie03: allocate port service
[    2.687537] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    2.687687] pcieport-driver 0000:00:1c.4: found MSI capability
[    2.687786] pcieport-driver 0000:00:1c.4: irq 2299 for MSI/MSI-X
[    2.687833] pci_express 0000:00:1c.4:pcie00: allocate port service
[    2.687861] pci_express 0000:00:1c.4:pcie02: allocate port service
[    2.687889] pci_express 0000:00:1c.4:pcie03: allocate port service
[    2.688117] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.689606] pciehp 0000:00:1c.0:pcie02: HPC vendor_id 8086 device_id 283f ss_vid 0 ss_did 0
[    2.689713] pciehp 0000:00:1c.0:pcie02: service driver pciehp loaded
[    2.691077] pciehp 0000:00:1c.1:pcie02: HPC vendor_id 8086 device_id 2841 ss_vid 0 ss_did 0
[    2.691179] pciehp 0000:00:1c.1:pcie02: service driver pciehp loaded
[    2.692544] pciehp 0000:00:1c.2:pcie02: HPC vendor_id 8086 device_id 2843 ss_vid 0 ss_did 0
[    2.692642] pciehp 0000:00:1c.2:pcie02: service driver pciehp loaded
[    2.694033] pciehp 0000:00:1c.3:pcie02: HPC vendor_id 8086 device_id 2845 ss_vid 0 ss_did 0
[    2.694130] pciehp 0000:00:1c.3:pcie02: service driver pciehp loaded
[    2.695483] pciehp 0000:00:1c.4:pcie02: HPC vendor_id 8086 device_id 2847 ss_vid 0 ss_did 0
[    2.695582] pciehp 0000:00:1c.4:pcie02: service driver pciehp loaded
[    2.695602] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.696362] ACPI: AC Adapter [AC] (off-line)
[    2.731252] ACPI: Battery Slot [BAT0] (battery present)
[    2.731424] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    2.731430] ACPI: Power Button (FF) [PWRF]
[    2.731536] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    2.732158] ACPI: Lid Switch [LID]
[    2.732260] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    2.732273] ACPI: Sleep Button (CM) [SLPB]
[    2.733515] ACPI: SSDT 7D6E1B32, 0306 (r1  PmRef  Cpu0Ist      100 INTL 20050513)
[    2.734850] ACPI: SSDT 7D6E1EBD, 085E (r1  PmRef  Cpu0Cst      100 INTL 20050513)
[    2.742084] Monitor-Mwait will be used to enter C-1 state
[    2.742093] Monitor-Mwait will be used to enter C-2 state
[    2.742100] Monitor-Mwait will be used to enter C-3 state
[    2.742132] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    2.742184] processor ACPI_CPU:00: registered as cooling_device0
[    2.742193] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.742953] ACPI: SSDT 7D6E1A6A, 00C8 (r1  PmRef  Cpu1Ist      100 INTL 20050513)
[    2.744286] ACPI: SSDT 7D6E1E38, 0085 (r1  PmRef  Cpu1Cst      100 INTL 20050513)
[    2.748203] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    2.748247] processor ACPI_CPU:01: registered as cooling_device1
[    2.748256] ACPI: Processor [CPU1] (supports 8 throttling states)
[    2.763350] thermal LNXTHERM:01: registered as thermal_zone0
[    2.766903] ACPI: Thermal Zone [THM0] (39 C)
[    2.769189] thermal LNXTHERM:02: registered as thermal_zone1
[    2.771801] ACPI: Thermal Zone [THM1] (30 C)
[    2.771920] isapnp: Scanning for PnP cards...
[    3.130381] isapnp: No Plug & Play device found
[    3.141331] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    3.143627] brd: module loaded
[    3.144331] loop: module loaded
[    3.144474] Fixed MDIO Bus: probed
[    3.144486] PPP generic driver version 2.4.2
[    3.144608] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    3.144670] Driver 'sd' needs updating - please use bus_type methods
[    3.144691] Driver 'sr' needs updating - please use bus_type methods
[    3.144781] ahci 0000:00:1f.2: version 3.0
[    3.144809] ahci 0000:00:1f.2: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    3.144923] ahci 0000:00:1f.2: irq 2298 for MSI/MSI-X
[    3.145083] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 1.5 Gbps 0x1 impl SATA mode
[    3.145091] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part 
[    3.145105] ahci 0000:00:1f.2: setting latency timer to 64
[    3.145334] scsi0 : ahci
[    3.145527] scsi1 : ahci
[    3.145678] scsi2 : ahci
[    3.145817] ata1: SATA max UDMA/133 abar m2048@0xfe226000 port 0xfe226100 irq 2298
[    3.145823] ata2: DUMMY
[    3.145826] ata3: DUMMY
[    3.464071] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.465048] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 succeeded
[    3.465056] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[    3.465062] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    3.516989] ata1.00: ATA-7: WDC WD1600BEVS-08RST2, 08.01G08, max UDMA/133
[    3.516996] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    3.518398] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 succeeded
[    3.518405] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[    3.518411] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    3.519162] ata1.00: configured for UDMA/133
[    3.533761] ata1.00: configured for UDMA/133
[    3.533768] ata1: EH complete
[    3.534057] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600BEVS-0 08.0 PQ: 0 ANSI: 5
[    3.534258] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[    3.534295] sd 0:0:0:0: [sda] Write Protect is off
[    3.534301] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.534359] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.534487] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[    3.534521] sd 0:0:0:0: [sda] Write Protect is off
[    3.534527] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.534585] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.534593]  sda: sda1 sda2 < sda5 >
[    3.575206] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.575298] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.575412] ata_piix 0000:00:1f.1: version 2.12
[    3.575428] ata_piix 0000:00:1f.1: PCI INT C -> GSI 16 (level, low) -> IRQ 16
[    3.575507] ata_piix 0000:00:1f.1: setting latency timer to 64
[    3.575666] scsi3 : ata_piix
[    3.575793] scsi4 : ata_piix
[    3.577665] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1c00 irq 14
[    3.577672] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1c08 irq 15
[    3.740728] ata4.00: ATAPI: DVD/CDRW UJDA775, CB03, max UDMA/33
[    3.756643] ata4.00: configured for UDMA/33
[    3.757044] ata5: port disabled. ignoring.
[    3.758672] scsi 3:0:0:0: CD-ROM            MATSHITA DVD/CDRW UJDA775 CB03 PQ: 0 ANSI: 5
[    3.762241] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    3.762247] Uniform CD-ROM driver Revision: 3.20
[    3.762432] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    3.762516] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    3.764112] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.764851] ehci_hcd 0000:00:1a.7: power state changed by ACPI to D0
[    3.764870] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    3.764901] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    3.764910] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    3.765063] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    3.769048] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    3.769078] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xfe226c00
[    3.784052] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    3.784185] usb usb1: configuration #1 chosen from 1 choice
[    3.784245] hub 1-0:1.0: USB hub found
[    3.784260] hub 1-0:1.0: 4 ports detected
[    3.785196] ehci_hcd 0000:00:1d.7: power state changed by ACPI to D0
[    3.785220] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    3.785249] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.785258] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.785359] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    3.789310] ehci_hcd 0000:00:1d.7: debug port 1
[    3.789329] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.789358] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xfe227000
[    3.804052] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    3.804180] usb usb2: configuration #1 chosen from 1 choice
[    3.804239] hub 2-0:1.0: USB hub found
[    3.804253] hub 2-0:1.0: 6 ports detected
[    3.804474] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.804514] uhci_hcd: USB Universal Host Controller Interface driver
[    3.804559] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    3.804576] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    3.804585] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    3.804677] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    3.804747] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00001860
[    3.804908] usb usb3: configuration #1 chosen from 1 choice
[    3.804965] hub 3-0:1.0: USB hub found
[    3.804982] hub 3-0:1.0: 2 ports detected
[    3.805736] uhci_hcd 0000:00:1a.1: power state changed by ACPI to D0
[    3.805750] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    3.805767] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    3.805776] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    3.805872] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    3.805942] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001880
[    3.806106] usb usb4: configuration #1 chosen from 1 choice
[    3.806163] hub 4-0:1.0: USB hub found
[    3.806177] hub 4-0:1.0: 2 ports detected
[    3.807045] uhci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[    3.807059] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.807076] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.807085] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.807196] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    3.807265] uhci_hcd 0000:00:1d.0: irq 16, io base 0x000018a0
[    3.807429] usb usb5: configuration #1 chosen from 1 choice
[    3.807486] hub 5-0:1.0: USB hub found
[    3.807499] hub 5-0:1.0: 2 ports detected
[    3.807699] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    3.807716] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.807725] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.807814] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    3.807882] uhci_hcd 0000:00:1d.1: irq 17, io base 0x000018c0
[    3.808039] usb usb6: configuration #1 chosen from 1 choice
[    3.808094] hub 6-0:1.0: USB hub found
[    3.808107] hub 6-0:1.0: 2 ports detected
[    3.808893] uhci_hcd 0000:00:1d.2: power state changed by ACPI to D0
[    3.808909] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.808926] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.808933] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.809058] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    3.809131] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018e0
[    3.809294] usb usb7: configuration #1 chosen from 1 choice
[    3.809351] hub 7-0:1.0: USB hub found
[    3.809365] hub 7-0:1.0: 2 ports detected
[    3.809672] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    3.817793] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.817805] serio: i8042 AUX port at 0x60,0x64 irq 12
[    3.824104] mice: PS/2 mouse device common for all mice
[    3.840168] rtc_cmos 00:07: RTC can wake from S4
[    3.840234] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    3.840294] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    3.840424] device-mapper: uevent: version 1.0.3
[    3.840651] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    3.840832] device-mapper: multipath: version 1.0.5 loaded
[    3.840837] device-mapper: multipath round-robin: version 1.0.0 loaded
[    3.841025] EISA: Probing bus 0 at eisa.0
[    3.841040] Cannot allocate resource for EISA slot 1
[    3.841046] Cannot allocate resource for EISA slot 2
[    3.841051] Cannot allocate resource for EISA slot 3
[    3.841056] Cannot allocate resource for EISA slot 4
[    3.841061] Cannot allocate resource for EISA slot 5
[    3.841066] Cannot allocate resource for EISA slot 6
[    3.841071] Cannot allocate resource for EISA slot 7
[    3.841076] Cannot allocate resource for EISA slot 8
[    3.841080] EISA: Detected 0 cards.
[    3.841368] cpuidle: using governor ladder
[    3.841654] cpuidle: using governor menu
[    3.842802] TCP cubic registered
[    3.843024] NET: Registered protocol family 10
[    3.843960] lo: Disabled Privacy Extensions
[    3.844773] NET: Registered protocol family 17
[    3.844811] Bluetooth: L2CAP ver 2.11
[    3.844815] Bluetooth: L2CAP socket layer initialized
[    3.844821] Bluetooth: SCO (Voice Link) ver 0.6
[    3.844825] Bluetooth: SCO socket layer initialized
[    3.844943] Bluetooth: RFCOMM socket layer initialized
[    3.844955] Bluetooth: RFCOMM TTY layer initialized
[    3.844959] Bluetooth: RFCOMM ver 1.10
[    3.846518] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    3.846597] Using IPI No-Shortcut mode
[    3.846655] registered taskstats version 1
[    3.846760]   Magic number: 5:780:662
[    3.846768] block ram15: hash matches
[    3.846861] rtc_cmos 00:07: setting system clock to 2009-08-19 02:41:37 UTC (1250649697)
[    3.846864] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.846865] EDD information not available.
[    3.847117] Freeing unused kernel memory: 532k freed
[    3.847262] Write protecting the kernel text: 4116k
[    3.847323] Write protecting the kernel read-only data: 1528k
[    3.987195] e1000e: Intel(R) PRO/1000 Network Driver - 0.3.3.3-k6
[    3.987198] e1000e: Copyright (c) 1999-2008 Intel Corporation.
[    3.987267] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    3.987281] e1000e 0000:00:19.0: setting latency timer to 64
[    3.987530] e1000e 0000:00:19.0: irq 2297 for MSI/MSI-X
[    4.047218] ohci1394 0000:15:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    4.047230] ohci1394 0000:15:00.1: setting latency timer to 64
[    4.098942] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[f8301000-f83017ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    4.216076] usb 2-6: new high speed USB device using ehci_hcd and address 2
[    4.251195] 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:1e:37:8e:2a:5a
[    4.251198] 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    4.251237] 0000:00:19.0: eth0: MAC: 5, PHY: 6, PBA No: 1008ff-0ff
[    4.348521] usb 2-6: configuration #1 chosen from 1 choice
[    4.430516] PM: Starting manual resume from disk
[    4.430520] PM: Resume from partition 8:5
[    4.430521] PM: Checking hibernation image.
[    4.430728] PM: Resume from disk failed.
[    4.477022] kjournald starting.  Commit interval 5 seconds
[    4.477064] EXT3-fs: mounted filesystem with ordered data mode.
[    4.588084] usb 3-1: new full speed USB device using uhci_hcd and address 2
[    4.750952] usb 3-1: configuration #1 chosen from 1 choice
[    5.000121] Clocksource tsc unstable (delta = -414058368 ns)
[    5.384275] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00061b032a1fea68]
[   11.551896] udev: starting version 141
[   11.725102] cfg80211: Calling CRDA to update world regulatory domain
[   11.767060] iTCO_vendor_support: vendor-support=0
[   11.769174] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   11.769414] iTCO_wdt: Found a ICH8M-E TCO device (Version=2, TCOBASE=0x1060)
[   11.769490] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   11.984693] Bluetooth: Generic Bluetooth USB driver ver 0.3
[   11.984794] usbcore: registered new interface driver btusb
[   12.052414] cfg80211: World regulatory domain updated:
[   12.052417]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   12.052419]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.052420]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.052422]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.052423]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.052425]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.201109] Linux agpgart interface v0.103
[   12.217624] sdhci: Secure Digital Host Controller Interface driver
[   12.217626] sdhci: Copyright(c) Pierre Ossman
[   12.227089] ricoh-mmc: Ricoh MMC Controller disabling driver
[   12.227091] ricoh-mmc: Copyright(c) Philip Langdale
[   12.227125] ricoh-mmc: Ricoh MMC controller found at 0000:15:00.3 [1180:0843] (rev 11)
[   12.227155] ricoh-mmc: Controller is now disabled.
[   12.240043] Non-volatile memory driver v1.2
[   12.390736] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   12.420993] acpi device:03: registered as cooling_device2
[   12.421270] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/input/input6
[   12.424153] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   12.426717] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
[   12.427533] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
[   12.430442] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[   12.430776] sdhci-pci 0000:15:00.2: SDHCI controller found [1180:0822] (rev 21)
[   12.430797] sdhci-pci 0000:15:00.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   12.430850] sdhci-pci 0000:15:00.2: Will use DMA mode even though HW doesn't fully claim to support it.
[   12.430861] sdhci-pci 0000:15:00.2: setting latency timer to 64
[   12.432898] mmc0: SDHCI controller on PCI [0000:15:00.2] using DMA
[   12.453252] thinkpad_acpi: ThinkPad ACPI Extras v0.21
[   12.453255] thinkpad_acpi: http://ibm-acpi.sf.net/
[   12.453257] thinkpad_acpi: ThinkPad BIOS 7LETB0WW (2.10 ), EC 7KHT24WW-1.08
[   12.453258] thinkpad_acpi: Lenovo ThinkPad T61, model 6465CTO
[   12.461194] thinkpad_acpi: ACPI backlight control delay disabled
[   12.464327] thinkpad_acpi: radio switch found; radios are enabled
[   12.464423] thinkpad_acpi: This ThinkPad has standard ACPI backlight brightness control, supported by the ACPI video driver
[   12.464425] thinkpad_acpi: Disabling thinkpad-acpi brightness events by default...
[   12.478901] Registered led device: tpacpi::thinklight
[   12.478952] Registered led device: tpacpi::power
[   12.478984] Registered led device: tpacpi:orange:batt
[   12.479016] Registered led device: tpacpi:green:batt
[   12.479050] Registered led device: tpacpi::dock_active
[   12.479098] Registered led device: tpacpi::bay_active
[   12.479131] Registered led device: tpacpi::dock_batt
[   12.479164] Registered led device: tpacpi::unknown_led
[   12.479198] Registered led device: tpacpi::standby
[   12.481384] thinkpad_acpi: Standard ACPI backlight interface available, not loading native one.
[   12.481655] input: ThinkPad Extra Buttons as /devices/virtual/input/input7
[   12.508658] HDA Intel 0000:00:1b.0: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   12.508659] hda_intel: probe_mask set to 0x1 for device 17aa:20ac
[   12.508704] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   12.510562] yenta_cardbus 0000:15:00.0: CardBus bridge found [17aa:20c6]
[   12.566863] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   12.566866] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[   12.566979] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.566993] iwl3945 0000:03:00.0: setting latency timer to 64
[   12.567030] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[   12.567675] iwl3945 0000:03:00.0: irq 2296 for MSI/MSI-X
[   12.600288] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   12.624091] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   12.624882] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   12.637351] yenta_cardbus 0000:15:00.0: ISA IRQ mask 0x04b8, PCI irq 16
[   12.637356] yenta_cardbus 0000:15:00.0: Socket status: 30000006
[   12.637360] yenta_cardbus 0000:15:00.0: pcmcia: parent PCI bridge I/O window: 0x7000 - 0xafff
[   12.637363] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x7000-0xafff: clean.
[   12.638126] yenta_cardbus 0000:15:00.0: pcmcia: parent PCI bridge Memory window: 0xf8300000 - 0xfbffffff
[   12.638128] yenta_cardbus 0000:15:00.0: pcmcia: parent PCI bridge Memory window: 0xf4000000 - 0xf7ffffff
[   13.060024] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   13.061590] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   13.062224] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   13.062739] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   13.063379] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   13.203815] lp: driver loaded but no devices found
[   13.283133] Adding 5919912k swap on /dev/sda5.  Priority:-1 extents:1 across:5919912k
[   13.296696] EXT3 FS on sda1, internal journal
[   13.491287] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x81a0b1, caps: 0xa04793/0x300000
[   13.491295] serio: Synaptics pass-through port at isa0060/serio1/input0
[   13.533120] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[   13.865696] type=1505 audit(1250649707.518:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2116
[   13.900346] type=1505 audit(1250649707.550:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2120
[   13.900411] type=1505 audit(1250649707.550:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2120
[   13.900441] type=1505 audit(1250649707.550:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2120
[   13.900471] type=1505 audit(1250649707.550:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2120
[   13.993893] type=1505 audit(1250649707.646:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2125
[   13.994041] type=1505 audit(1250649707.646:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2125
[   14.014261] type=1505 audit(1250649707.666:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2129
[   14.729707] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   16.170147] psmouse serio2: ID: 10 00 64<7>vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   18.246449] vboxdrv: Successfully done.
[   18.246451] vboxdrv: Found 2 processor cores.
[   18.246536] vboxdrv: fAsync=1 offMin=0x11aa20 offMax=0x11aa20
[   18.246576] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
[   18.246578] vboxdrv: Successfully loaded version 2.1.4_OSE (interface 0x000a0009).
[   19.615209] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   19.865430] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input9
[   19.985940] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.985943] Bluetooth: BNEP filters: protocol multicast
[   20.003436] Bridge firewalling registered
[   21.440819] ppdev: user-space parallel port driver
 
```Unfortunately I don't have another computer I could plug it in to to see if it works. My desktop is a little bit out of commission right now. Tomorrow I can throw it together and test it.

---

### Post by kayvortex on 2009-08-19
I suspect the problem is probably with the hard drive: try to verify that it works OK if you can and let me know.

---

