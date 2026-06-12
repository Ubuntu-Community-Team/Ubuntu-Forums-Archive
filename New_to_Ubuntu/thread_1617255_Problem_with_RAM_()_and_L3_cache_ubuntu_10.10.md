---
title: "Problem with RAM (?) and L3 cache ubuntu 10.10"
date: 2010-11-09
forum: New to Ubuntu
---

### Post by Blyme on 2010-11-09
Hi all,
Installed Ubuntu 10.10 to try it out but stumbled on some weird memory related errors in the logs. Also, when I look up my system specs it doesnt show the L3 cache for my AMD Phenom II x4 955.

This is my first Linux install, always worked with Windows in the past, but I like Ubuntu so far, exept for those weird messages and not showing my Phenom II L3 cache. Not noticed any errors so far, my system is fast viewing dvd's/flash movies and played World of Warcraft with Whine and that went well also, though it seems a tad slower with WOW in compare with Windows 7 but thats the emulation part I guess..

I ran Mem86+, which I used in the past for my other system because it would freeze in windows 7 and turned out to be a bad ram stick. But this system worked fine in Windows playing World of Warcraft and dvd's with it without any issues at all so doubt it's a ram issue. Resetted the CMOS and flashed the bios to the latest version just in case because the bios corrupt part doesnt sound nice to me but the error is still there.

My system:
Motherboard M4A785TD-V EVO
CPU: AMD Phenom II x4 955
RAM: 2x2 Gb OCZ 1066 mhz ddr3 (checked in mobo manual, its compatible with the board)
HDD Samsung 320 gb sata II
cheap generic dvd player/burner

Not having a videocard in it yet, so using the onboard Radeon HD 4200, and sharing 512 mb ram with it. Turned off the 128 mb sideport ram but that didnt make any difference.

Here is the kernel log I noticed the memory errors from boot up. After the system is running I dont see any errors in it so not sure if its an issue.

Nov  9 09:49:17 POS kernel: imklog 4.2.0, log source = /proc/kmsg started.
Nov  9 09:49:17 POS rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="782" x-info="http://www.rsyslog.com"] (re)start
Nov  9 09:49:17 POS rsyslogd: rsyslogd's groupid changed to 103
Nov  9 09:49:17 POS rsyslogd: rsyslogd's userid changed to 101
Nov  9 09:49:17 POS kernel: [    0.000000] Initializing cgroup subsys cpuset
Nov  9 09:49:17 POS kernel: [    0.000000] Initializing cgroup subsys cpu
Nov  9 09:49:17 POS kernel: [    0.000000] Linux version 2.6.35-22-generic (buildd@yellow) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #35-Ubuntu SMP Sat Oct 16 20:45:36 UTC 2010 (Ubuntu 2.6.35-22.35-generic 2.6.35.4)
Nov  9 09:49:17 POS kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=0a70e1fc-73dc-492e-a80c-5e5644d910ba ro quiet splash
Nov  9 09:49:17 POS kernel: [    0.000000] BIOS-provided physical RAM map:
Nov  9 09:49:17 POS kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Nov  9 09:49:17 POS kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Nov  9 09:49:17 POS kernel: [    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
Nov  9 09:49:17 POS kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000cfe90000 (usable)
Nov  9 09:49:17 POS kernel: [    0.000000]  BIOS-e820: 00000000cfe90000 - 00000000cfea8000 (ACPI data)
Nov  9 09:49:17 POS kernel: [    0.000000]  BIOS-e820: 00000000cfea8000 - 00000000cfed0000 (ACPI NVS)
Nov  9 09:49:17 POS kernel: [    0.000000]  BIOS-e820: 00000000cfed0000 - 00000000cff00000 (reserved)
Nov  9 09:49:17 POS kernel: [    0.000000]  BIOS-e820: 00000000ff700000 - 0000000100000000 (reserved)
Nov  9 09:49:17 POS kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000110000000 (usable)
Nov  9 09:49:17 POS kernel: [    0.000000] NX (Execute Disable) protection: active
Nov  9 09:49:17 POS kernel: [    0.000000] DMI present.
Nov  9 09:49:17 POS kernel: [    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
Nov  9 09:49:17 POS kernel: [    0.000000] No AGP bridge found
Nov  9 09:49:17 POS kernel: [    0.000000] last_pfn = 0x110000 max_arch_pfn = 0x400000000
Nov  9 09:49:17 POS kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Nov  9 09:49:17 POS kernel: [    0.000000] last_pfn = 0xcfe90 max_arch_pfn = 0x400000000
Nov  9 09:49:17 POS kernel: [    0.000000] Scanning 0 areas for low memory corruption
Nov  9 09:49:17 POS kernel: [    0.000000] modified physical RAM map:
Nov  9 09:49:17 POS kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Nov  9 09:49:17 POS kernel: [    0.000000]  modified: 0000000000010000 - 000000000009f000 (usable)
Nov  9 09:49:17 POS kernel: [    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
Nov  9 09:49:17 POS kernel: [    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
Nov  9 09:49:17 POS kernel: [    0.000000]  modified: 0000000000100000 - 00000000cfe90000 (usable)
Nov  9 09:49:17 POS kernel: [    0.000000]  modified: 00000000cfe90000 - 00000000cfea8000 (ACPI data)
Nov  9 09:49:17 POS kernel: [    0.000000]  modified: 00000000cfea8000 - 00000000cfed0000 (ACPI NVS)
Nov  9 09:49:17 POS kernel: [    0.000000]  modified: 00000000cfed0000 - 00000000cff00000 (reserved)
Nov  9 09:49:17 POS kernel: [    0.000000]  modified: 00000000ff700000 - 0000000100000000 (reserved)
Nov  9 09:49:17 POS kernel: [    0.000000]  modified: 0000000100000000 - 0000000110000000 (usable)
Nov  9 09:49:17 POS kernel: [    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
Nov  9 09:49:17 POS kernel: [    0.000000] Using GB pages for direct mapping
Nov  9 09:49:17 POS kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000cfe90000
Nov  9 09:49:17 POS kernel: [    0.000000] init_memory_mapping: 0000000100000000-0000000110000000
Nov  9 09:49:17 POS kernel: [    0.000000] RAMDISK: 37571000 - 37ff0000
Nov  9 09:49:17 POS kernel: [    0.000000] ACPI: RSDP 00000000000fb4e0 00024 (v02 ACPIAM)
Nov  9 09:49:17 POS kernel: [    0.000000] ACPI: XSDT 00000000cfe90100 00054 (v01 072310 XSDT1710 20100723 MSFT 00000097)
Nov  9 09:49:17 POS kernel: [    0.000000] ACPI: FACP 00000000cfe90290 000F4 (v03 072310 FACP1710 20100723 MSFT 00000097)
Nov  9 09:49:17 POS kernel: [    0.000000] ACPI Warning: Optional field Pm2ControlBlock has zero address or length: 0x0000000000000000/0x1 (20100428/tbfadt-557)
Nov  9 09:49:17 POS kernel: [    0.000000] ACPI: DSDT 00000000cfe90450 0E712 (v01  A1392 A1392001 00000001 INTL 20060113)
Nov  9 09:49:17 POS kernel: [    0.000000] ACPI: FACS 00000000cfea8000 00040
Nov  9 09:49:17 POS kernel: [    0.000000] ACPI: APIC 00000000cfe90390 0007C (v01 072310 APIC1710 20100723 MSFT 00000097)
Nov  9 09:49:17 POS kernel: [    0.000000] ACPI: MCFG 00000000cfe90410 0003C (v01 072310 OEMMCFG  20100723 MSFT 00000097)
Nov  9 09:49:17 POS kernel: [    0.000000] ACPI: OEMB 00000000cfea8040 00072 (v01 072310 OEMB1710 20100723 MSFT 00000097)
Nov  9 09:49:17 POS kernel: [    0.000000] ACPI: SRAT 00000000cfe9f450 000E8 (v01 AMD    FAM_F_10 00000002 AMD  00000001)
Nov  9 09:49:17 POS kernel: [    0.000000] ACPI: HPET 00000000cfe9f540 00038 (v01 072310 OEMHPET  20100723 MSFT 00000097)
Nov  9 09:49:17 POS kernel: [    0.000000] SRAT: PXM 0 -> APIC 0x00 -> Node 0
Nov  9 09:49:17 POS kernel: [    0.000000] SRAT: PXM 0 -> APIC 0x01 -> Node 0
Nov  9 09:49:17 POS kernel: [    0.000000] SRAT: PXM 0 -> APIC 0x02 -> Node 0
Nov  9 09:49:17 POS kernel: [    0.000000] SRAT: PXM 0 -> APIC 0x03 -> Node 0
Nov  9 09:49:17 POS kernel: [    0.000000] SRAT: Node 0 PXM 0 0-a0000
Nov  9 09:49:17 POS kernel: [    0.000000] SRAT: Node 0 PXM 0 100000-d0000000
Nov  9 09:49:17 POS kernel: [    0.000000] SRAT: Node 0 PXM 0 100000000-130000000
Nov  9 09:49:17 POS kernel: [    0.000000] SRAT: Node 0 [0,a0000) + [100000,d0000000) -> [0,d0000000)
Nov  9 09:49:17 POS kernel: [    0.000000] SRAT: Node 0 [0,d0000000) + [100000000,130000000) -> [0,130000000)
Nov  9 09:49:17 POS kernel: [    0.000000] Initmem setup node 0 0000000000000000-0000000110000000
Nov  9 09:49:17 POS kernel: [    0.000000]   NODE_DATA [0000000100000000 - 0000000100004fff]
Nov  9 09:49:17 POS kernel: [    0.000000] Zone PFN ranges:
Nov  9 09:49:17 POS kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Nov  9 09:49:17 POS kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Nov  9 09:49:17 POS kernel: [    0.000000]   Normal   0x00100000 -> 0x00110000
Nov  9 09:49:17 POS kernel: [    0.000000] Movable zone start PFN for each node
Nov  9 09:49:17 POS kernel: [    0.000000] early_node_map[3] active PFN ranges
Nov  9 09:49:17 POS kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Nov  9 09:49:17 POS kernel: [    0.000000]     0: 0x00000100 -> 0x000cfe90
Nov  9 09:49:17 POS kernel: [    0.000000]     0: 0x00100000 -> 0x00110000
Nov  9 09:49:17 POS kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Nov  9 09:49:17 POS kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Nov  9 09:49:17 POS kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Nov  9 09:49:17 POS kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
Nov  9 09:49:17 POS kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
Nov  9 09:49:17 POS kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x84] disabled)
Nov  9 09:49:17 POS kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x85] disabled)
Nov  9 09:49:17 POS kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Nov  9 09:49:17 POS kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
Nov  9 09:49:17 POS kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Nov  9 09:49:17 POS kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Nov  9 09:49:17 POS kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Nov  9 09:49:17 POS kernel: [    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
Nov  9 09:49:17 POS kernel: [    0.000000] SMP: Allowing 6 CPUs, 2 hotplug CPUs
Nov  9 09:49:17 POS kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Nov  9 09:49:17 POS kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
Nov  9 09:49:17 POS kernel: [    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
Nov  9 09:49:17 POS kernel: [    0.000000] PM: Registered nosave memory: 00000000cfe90000 - 00000000cfea8000
Nov  9 09:49:17 POS kernel: [    0.000000] PM: Registered nosave memory: 00000000cfea8000 - 00000000cfed0000
Nov  9 09:49:17 POS kernel: [    0.000000] PM: Registered nosave memory: 00000000cfed0000 - 00000000cff00000
Nov  9 09:49:17 POS kernel: [    0.000000] PM: Registered nosave memory: 00000000cff00000 - 00000000ff700000
Nov  9 09:49:17 POS kernel: [    0.000000] PM: Registered nosave memory: 00000000ff700000 - 0000000100000000
Nov  9 09:49:17 POS kernel: [    0.000000] Allocating PCI resources starting at cff00000 (gap: cff00000:2f800000)
Nov  9 09:49:17 POS kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Nov  9 09:49:17 POS kernel: [    0.000000] setup_percpu: NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:6 nr_node_ids:1
Nov  9 09:49:17 POS kernel: [    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001e00000 s91520 r8192 d23168 u262144
Nov  9 09:49:17 POS kernel: [    0.000000] pcpu-alloc: s91520 r8192 d23168 u262144 alloc=1*2097152
Nov  9 09:49:17 POS kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 - - 
Nov  9 09:49:17 POS kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 901791
Nov  9 09:49:17 POS kernel: [    0.000000] Policy zone: Normal
Nov  9 09:49:17 POS kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=0a70e1fc-73dc-492e-a80c-5e5644d910ba ro quiet splash
Nov  9 09:49:17 POS kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Nov  9 09:49:17 POS kernel: [    0.000000] Checking aperture...
Nov  9 09:49:17 POS kernel: [    0.000000] No AGP bridge found
Nov  9 09:49:17 POS kernel: [    0.000000] Node 0: aperture @ 4272000000 size 32 MB
Nov  9 09:49:17 POS kernel: [    0.000000] Aperture beyond 4GB. Ignoring.
Nov  9 09:49:17 POS kernel: [    0.000000] Your BIOS doesn't leave a aperture memory hole
Nov  9 09:49:17 POS kernel: [    0.000000] Please enable the IOMMU option in the BIOS setup
Nov  9 09:49:17 POS kernel: [    0.000000] This costs you 64 MB of RAM
Nov  9 09:49:17 POS kernel: [    0.000000] Mapping aperture over 65536 KB of RAM @ 20000000
Nov  9 09:49:17 POS kernel: [    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000024000000
Nov  9 09:49:17 POS kernel: [    0.000000] Subtract (59 early reservations)
Nov  9 09:49:17 POS kernel: [    0.000000]   #1 [0001000000 - 0001d17114]   TEXT DATA BSS
Nov  9 09:49:17 POS kernel: [    0.000000]   #2 [0037571000 - 0037ff0000]         RAMDISK
Nov  9 09:49:17 POS kernel: [    0.000000]   #3 [0001d18000 - 0001d18340]             BRK
Nov  9 09:49:17 POS kernel: [    0.000000]   #4 [00000ff790 - 0000100000]   BIOS reserved
Nov  9 09:49:17 POS kernel: [    0.000000]   #5 [00000ff780 - 00000ff790]    MP-table mpf
Nov  9 09:49:17 POS kernel: [    0.000000]   #6 [000009f000 - 00000f0900]   BIOS reserved
Nov  9 09:49:17 POS kernel: [    0.000000]   #7 [00000f0a7c - 00000ff780]   BIOS reserved
Nov  9 09:49:17 POS kernel: [    0.000000]   #8 [00000f0900 - 00000f0a7c]    MP-table mpc
Nov  9 09:49:17 POS kernel: [    0.000000]   #9 [0000010000 - 0000012000]      TRAMPOLINE
Nov  9 09:49:17 POS kernel: [    0.000000]   #10 [0000012000 - 0000016000]     ACPI WAKEUP
Nov  9 09:49:17 POS kernel: [    0.000000]   #11 [0000016000 - 0000018000]         PGTABLE
Nov  9 09:49:17 POS kernel: [    0.000000]   #12 [0000018000 - 0000019000]         PGTABLE
Nov  9 09:49:17 POS kernel: [    0.000000]   #13 [0100000000 - 0100005000]       NODE_DATA
Nov  9 09:49:17 POS kernel: [    0.000000]   #14 [0001d18340 - 0001d19340]         BOOTMEM
Nov  9 09:49:17 POS kernel: [    0.000000]   #15 [0001d17140 - 0001d173e0]         BOOTMEM
Nov  9 09:49:17 POS kernel: [    0.000000]   #16 [0100005000 - 0100006000]         BOOTMEM
Nov  9 09:49:17 POS kernel: [    0.000000]   #17 [0100006000 - 0100007000]         BOOTMEM
Nov  9 09:49:17 POS kernel: [    0.000000]   #18 [0100200000 - 0103400000]        MEMMAP 0
Nov  9 09:49:17 POS kernel: [    0.000000]   #19 [0001d17400 - 0001d17580]         BOOTMEM
Nov  9 09:49:17 POS kernel: [    0.000000]   #20 [0001d19340 - 0001d31340]         BOOTMEM
Nov  9 09:49:17 POS kernel: [    0.000000]   #21 [0001d31340 - 0001d32b40]         BOOTMEM
Nov  9 09:49:17 POS kernel: [    0.000000]   #22 [0001d33000 - 0001d34000]         BOOTMEM
Nov  9 09:49:17 POS kernel: [    0.000000]   #23 [0001d17580 - 0001d175c1]         BOOTMEM
Nov  9 09:49:17 POS kernel: [    0.000000]   #24 [0001d17600 - 0001d17643]         BOOTMEM
Nov  9 09:49:17 POS kernel: [    0.000000]   #25 [0001d17680 - 0001d178b0]         BOOTMEM
Nov  9 09:49:17 POS kernel: [    0.000000]   #26 [0001d178c0 - 0001d17928]         BOOTMEM
Nov  9 09:49:17 POS kernel: [    0.000000]   #27 [0001d17940 - 0001d179a8]         BOOTMEM
Nov  9 09:49:17 POS kernel: [    0.000000]   #28 [0001d179c0 - 0001d17a28]         BOOTMEM
Nov  9 09:49:17 POS kernel: [    0.000000]   #29 [0001d17a40 - 0001d17aa8]         BOOTMEM
Nov  9 09:49:17 POS kernel: [    0.000000]   #30 [0001d17ac0 - 0001d17b28]         BOOTMEM
Nov  9 09:49:17 POS kernel: [    0.000000]   #31 [0001d17b40 - 0001d17ba8]         BOOTMEM
Nov  9 09:49:17 POS kernel: [    0.000000]   #32 [0001d17bc0 - 0001d17c28]         BOOTMEM
Nov  9 09:49:17 POS kernel: [    0.000000]   #33 [0001d17c40 - 0001d17ca8]         BOOTMEM
Nov  9 09:49:17 POS kernel: [    0.000000]   #34 [0001d17cc0 - 0001d17d28]         BOOTMEM
Nov  9 09:49:17 POS kernel: [    0.000000]   #35 [0001d17d40 - 0001d17d60]         BOOTMEM
Nov  9 09:49:17 POS kernel: [    0.000000]   #36 [0001d17d80 - 0001d17da0]         BOOTMEM
Nov  9 09:49:17 POS kernel: [    0.000000]   #37 [0001d17dc0 - 0001d17e2a]         BOOTMEM
Nov  9 09:49:17 POS kernel: [    0.000000]   #38 [0001d17e40 - 0001d17eaa]         BOOTMEM
Nov  9 09:49:17 POS kernel: [    0.000000]   #39 [0001e00000 - 0001e1e000]         BOOTMEM
Nov  9 09:49:17 POS kernel: [    0.000000]   #40 [0001e40000 - 0001e5e000]         BOOTMEM
Nov  9 09:49:17 POS kernel: [    0.000000]   #41 [0001e80000 - 0001e9e000]         BOOTMEM
Nov  9 09:49:17 POS kernel: [    0.000000]   #42 [0001ec0000 - 0001ede000]         BOOTMEM
Nov  9 09:49:17 POS kernel: [    0.000000]   #43 [0001f00000 - 0001f1e000]         BOOTMEM
Nov  9 09:49:17 POS kernel: [    0.000000]   #44 [0001f40000 - 0001f5e000]         BOOTMEM
Nov  9 09:49:17 POS kernel: [    0.000000]   #45 [0001d17ec0 - 0001d17ec8]         BOOTMEM
Nov  9 09:49:17 POS kernel: [    0.000000]   #46 [0001d17f00 - 0001d17f08]         BOOTMEM
Nov  9 09:49:17 POS kernel: [    0.000000]   #47 [0001d17f40 - 0001d17f58]         BOOTMEM
Nov  9 09:49:17 POS kernel: [    0.000000]   #48 [0001d17f80 - 0001d17fb0]         BOOTMEM
Nov  9 09:49:17 POS kernel: [    0.000000]   #49 [0001d32b40 - 0001d32c60]         BOOTMEM
Nov  9 09:49:17 POS kernel: [    0.000000]   #50 [0001d32c80 - 0001d32cc8]         BOOTMEM
Nov  9 09:49:17 POS kernel: [    0.000000]   #51 [0001d32d00 - 0001d32d48]         BOOTMEM
Nov  9 09:49:17 POS kernel: [    0.000000]   #52 [0001d34000 - 0001d3c000]         BOOTMEM
Nov  9 09:49:17 POS kernel: [    0.000000]   #53 [0020000000 - 0024000000]         BOOTMEM
Nov  9 09:49:17 POS kernel: [    0.000000]   #54 [0001d17fc0 - 0001d17fe0]         BOOTMEM
Nov  9 09:49:17 POS kernel: [    0.000000]   #55 [0001f5e000 - 0005f5e000]         BOOTMEM
Nov  9 09:49:17 POS kernel: [    0.000000]   #56 [0001d3c000 - 0001d5c000]         BOOTMEM
Nov  9 09:49:17 POS kernel: [    0.000000]   #57 [0001d5c000 - 0001d9c000]         BOOTMEM
Nov  9 09:49:17 POS kernel: [    0.000000]   #58 [000001a800 - 0000022800]         BOOTMEM
Nov  9 09:49:17 POS kernel: [    0.000000] Memory: 3460316k/4456448k available (5708k kernel code, 788356k absent, 207776k reserved, 5382k data, 908k init)
Nov  9 09:49:17 POS kernel: [    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=6, Nodes=1
Nov  9 09:49:17 POS kernel: [    0.000000] Hierarchical RCU implementation.
Nov  9 09:49:17 POS kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
Nov  9 09:49:17 POS kernel: [    0.000000]     RCU-based detection of stalled CPUs is disabled.
Nov  9 09:49:17 POS kernel: [    0.000000]     Verbose stalled-CPUs detection is disabled.
Nov  9 09:49:17 POS kernel: [    0.000000] NR_IRQS:4352 nr_irqs:728
Nov  9 09:49:17 POS kernel: [    0.000000] Extended CMOS year: 2000
Nov  9 09:49:17 POS kernel: [    0.000000] Console: colour VGA+ 80x25
Nov  9 09:49:17 POS kernel: [    0.000000] console [tty0] enabled
Nov  9 09:49:17 POS kernel: [    0.000000] allocated 36700160 bytes of page_cgroup
Nov  9 09:49:17 POS kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Nov  9 09:49:17 POS kernel: [    0.000000] Fast TSC calibration using PIT
Nov  9 09:49:17 POS kernel: [    0.000000] Detected 3200.225 MHz processor.
Nov  9 09:49:17 POS kernel: [    0.020007] Calibrating delay loop (skipped), value calculated using timer frequency.. 6400.44 BogoMIPS (lpj=32002210)
Nov  9 09:49:17 POS kernel: [    0.020011] pid_max: default: 32768 minimum: 301
Nov  9 09:49:17 POS kernel: [    0.020026] Security Framework initialized
Nov  9 09:49:17 POS kernel: [    0.020039] AppArmor: AppArmor initialized
Nov  9 09:49:17 POS kernel: [    0.020040] Yama: becoming mindful.
Nov  9 09:49:17 POS kernel: [    0.020352] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
Nov  9 09:49:17 POS kernel: [    0.021523] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
Nov  9 09:49:17 POS kernel: [    0.022026] Mount-cache hash table entries: 256
Nov  9 09:49:17 POS kernel: [    0.022111] Initializing cgroup subsys ns
Nov  9 09:49:17 POS kernel: [    0.022114] Initializing cgroup subsys cpuacct
Nov  9 09:49:17 POS kernel: [    0.022117] Initializing cgroup subsys memory
Nov  9 09:49:17 POS kernel: [    0.022124] Initializing cgroup subsys devices
Nov  9 09:49:17 POS kernel: [    0.022125] Initializing cgroup subsys freezer
Nov  9 09:49:17 POS kernel: [    0.022127] Initializing cgroup subsys net_cls
Nov  9 09:49:17 POS kernel: [    0.022155] CPU: Physical Processor ID: 0
Nov  9 09:49:17 POS kernel: [    0.022156] CPU: Processor Core ID: 0
Nov  9 09:49:17 POS kernel: [    0.022157] mce: CPU supports 6 MCE banks
Nov  9 09:49:17 POS kernel: [    0.022164] Performance Events: AMD PMU driver.
Nov  9 09:49:17 POS kernel: [    0.022168] ... version:                0
Nov  9 09:49:17 POS kernel: [    0.022169] ... bit width:              48
Nov  9 09:49:17 POS kernel: [    0.022170] ... generic registers:      4
Nov  9 09:49:17 POS kernel: [    0.022171] ... value mask:             0000ffffffffffff
Nov  9 09:49:17 POS kernel: [    0.022172] ... max period:             00007fffffffffff
Nov  9 09:49:17 POS kernel: [    0.022173] ... fixed-purpose events:   0
Nov  9 09:49:17 POS kernel: [    0.022174] ... event mask:             000000000000000f
Nov  9 09:49:17 POS kernel: [    0.023374] ACPI: Core revision 20100428
Nov  9 09:49:17 POS kernel: [    0.040006] ftrace: converting mcount calls to 0f 1f 44 00 00
Nov  9 09:49:17 POS kernel: [    0.040009] ftrace: allocating 22680 entries in 89 pages
Nov  9 09:49:17 POS kernel: [    0.044759] Setting APIC routing to flat
Nov  9 09:49:17 POS kernel: [    0.045054] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Nov  9 09:49:17 POS kernel: [    0.145349] CPU0: AMD Phenom(tm) II X4 955 Processor stepping 03
Nov  9 09:49:17 POS kernel: [    0.150000] Booting Node   0, Processors  #1 #2 #3
Nov  9 09:49:17 POS kernel: [    0.650004] Brought up 4 CPUs
Nov  9 09:49:17 POS kernel: [    0.650006] Total of 4 processors activated (25601.93 BogoMIPS).
Nov  9 09:49:17 POS kernel: [    0.651712] devtmpfs: initialized
Nov  9 09:49:17 POS kernel: [    0.651712] regulator: core version 0.5
Nov  9 09:49:17 POS kernel: [    0.651712] Time:  8:49:09  Date: 11/09/10
Nov  9 09:49:17 POS kernel: [    0.651712] NET: Registered protocol family 16
Nov  9 09:49:17 POS kernel: [    0.651712] TOM: 00000000d0000000 aka 3328M
Nov  9 09:49:17 POS kernel: [    0.651712] TOM2: 0000000130000000 aka 4864M
Nov  9 09:49:17 POS kernel: [    0.651712] ACPI: bus type pci registered
Nov  9 09:49:17 POS kernel: [    0.651712] Trying to unpack rootfs image as initramfs...
Nov  9 09:49:17 POS kernel: [    0.651712] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Nov  9 09:49:17 POS kernel: [    0.651712] PCI: not using MMCONFIG
Nov  9 09:49:17 POS kernel: [    0.651712] PCI: Using configuration type 1 for base access
Nov  9 09:49:17 POS kernel: [    0.651712] PCI: Using configuration type 1 for extended access
Nov  9 09:49:17 POS kernel: [    0.651712] bio: create slab <bio-0> at 0
Nov  9 09:49:17 POS kernel: [    0.652599] ACPI: Executed 3 blocks of module-level executable AML code
Nov  9 09:49:17 POS kernel: [    0.782182] ACPI: Interpreter enabled
Nov  9 09:49:17 POS kernel: [    0.782186] ACPI: (supports S0 S1 S3 S4 S5)
Nov  9 09:49:17 POS kernel: [    0.782204] ACPI: Using IOAPIC for interrupt routing
Nov  9 09:49:17 POS kernel: [    0.782255] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Nov  9 09:49:17 POS kernel: [    0.784640] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
Nov  9 09:49:17 POS kernel: [    0.806500] ACPI Warning: Incorrect checksum in table [OEMB] - 0xF5, should be 0xF0 (20100428/tbutils-314)
Nov  9 09:49:17 POS kernel: [    0.806610] ACPI: No dock devices found.
Nov  9 09:49:17 POS kernel: [    0.806613] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Nov  9 09:49:17 POS kernel: [    0.806730] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Nov  9 09:49:17 POS kernel: [    0.806961] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
Nov  9 09:49:17 POS kernel: [    0.806963] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
Nov  9 09:49:17 POS kernel: [    0.806964] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
Nov  9 09:49:17 POS kernel: [    0.806966] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff]
Nov  9 09:49:17 POS kernel: [    0.806968] pci_root PNP0A03:00: host bridge window [mem 0xcff00000-0xdfffffff]
Nov  9 09:49:17 POS kernel: [    0.806969] pci_root PNP0A03:00: host bridge window [mem 0xf0000000-0xfebfffff]
Nov  9 09:49:17 POS kernel: [    0.808004] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Nov  9 09:49:17 POS kernel: [    0.815900] Freeing initrd memory: 10748k freed
Nov  9 09:49:17 POS kernel: [    0.820022] pci 0000:00:0a.0: PCI bridge to [bus 02-02]
Nov  9 09:49:17 POS kernel: [    0.820094] pci 0000:00:14.4: PCI bridge to [bus 03-03] (subtractive decode)
Nov  9 09:49:17 POS kernel: [    0.823836] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 7 *10 11 12 14 15)
Nov  9 09:49:17 POS kernel: [    0.823922] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 7 10 *11 12 14 15)
Nov  9 09:49:17 POS kernel: [    0.824010] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 7 *10 11 12 14 15)
Nov  9 09:49:17 POS kernel: [    0.824091] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 7 *10 11 12 14 15)
Nov  9 09:49:17 POS kernel: [    0.824172] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 7 10 11 12 14 15) *0, disabled.
Nov  9 09:49:17 POS kernel: [    0.824254] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 7 10 11 12 14 15) *0, disabled.
Nov  9 09:49:17 POS kernel: [    0.824336] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 7 10 *11 12 14 15)
Nov  9 09:49:17 POS kernel: [    0.824418] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 12 14 15) *0, disabled.
Nov  9 09:49:17 POS kernel: [    0.824449] HEST: Table is not found!
Nov  9 09:49:17 POS kernel: [    0.824500] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
Nov  9 09:49:17 POS kernel: [    0.824502] vgaarb: loaded
Nov  9 09:49:17 POS kernel: [    0.824588] SCSI subsystem initialized
Nov  9 09:49:17 POS kernel: [    0.824606] usbcore: registered new interface driver usbfs
Nov  9 09:49:17 POS kernel: [    0.824606] usbcore: registered new interface driver hub
Nov  9 09:49:17 POS kernel: [    0.824606] usbcore: registered new device driver usb
Nov  9 09:49:17 POS kernel: [    0.824606] ACPI: WMI: Mapper loaded
Nov  9 09:49:17 POS kernel: [    0.824606] PCI: Using ACPI for IRQ routing
Nov  9 09:49:17 POS kernel: [    0.824606] NetLabel: Initializing
Nov  9 09:49:17 POS kernel: [    0.824606] NetLabel:  domain hash size = 128
Nov  9 09:49:17 POS kernel: [    0.824606] NetLabel:  protocols = UNLABELED CIPSOv4
Nov  9 09:49:17 POS kernel: [    0.824606] NetLabel:  unlabeled traffic allowed by default
Nov  9 09:49:17 POS kernel: [    0.824606] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Nov  9 09:49:17 POS kernel: [    0.824606] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
Nov  9 09:49:17 POS kernel: [    0.824606] Switching to clocksource tsc
Nov  9 09:49:17 POS kernel: [    0.825146] AppArmor: AppArmor Filesystem Enabled
Nov  9 09:49:17 POS kernel: [    0.825146] pnp: PnP ACPI init
Nov  9 09:49:17 POS kernel: [    0.825146] ACPI: bus type pnp registered
Nov  9 09:49:17 POS kernel: [    0.828539] pnp: PnP ACPI: found 14 devices
Nov  9 09:49:17 POS kernel: [    0.828541] ACPI: ACPI bus type pnp unregistered
Nov  9 09:49:17 POS kernel: [    0.828550] system 00:09: [mem 0xfec00000-0xfec00fff] could not be reserved
Nov  9 09:49:17 POS kernel: [    0.828552] system 00:09: [mem 0xfee00000-0xfee00fff] has been reserved
Nov  9 09:49:17 POS kernel: [    0.828555] system 00:0a: [io  0x04d0-0x04d1] has been reserved
Nov  9 09:49:17 POS kernel: [    0.828557] system 00:0a: [io  0x040b] has been reserved
Nov  9 09:49:17 POS kernel: [    0.828559] system 00:0a: [io  0x04d6] has been reserved
Nov  9 09:49:17 POS kernel: [    0.828560] system 00:0a: [io  0x0c00-0x0c01] has been reserved
Nov  9 09:49:17 POS kernel: [    0.828562] system 00:0a: [io  0x0c14] has been reserved
Nov  9 09:49:17 POS kernel: [    0.828563] system 00:0a: [io  0x0c50-0x0c51] has been reserved
Nov  9 09:49:17 POS kernel: [    0.828565] system 00:0a: [io  0x0c52] has been reserved
Nov  9 09:49:17 POS kernel: [    0.828567] system 00:0a: [io  0x0c6c] has been reserved
Nov  9 09:49:17 POS kernel: [    0.828568] system 00:0a: [io  0x0c6f] has been reserved
Nov  9 09:49:17 POS kernel: [    0.828570] system 00:0a: [io  0x0cd0-0x0cd1] has been reserved
Nov  9 09:49:17 POS kernel: [    0.828571] system 00:0a: [io  0x0cd2-0x0cd3] has been reserved
Nov  9 09:49:17 POS kernel: [    0.828573] system 00:0a: [io  0x0cd4-0x0cd5] has been reserved
Nov  9 09:49:17 POS kernel: [    0.828575] system 00:0a: [io  0x0cd6-0x0cd7] has been reserved
Nov  9 09:49:17 POS kernel: [    0.828576] system 00:0a: [io  0x0cd8-0x0cdf] has been reserved
Nov  9 09:49:17 POS kernel: [    0.828578] system 00:0a: [io  0x0b00-0x0b3f] has been reserved
Nov  9 09:49:17 POS kernel: [    0.828580] system 00:0a: [io  0x0800-0x089f] has been reserved
Nov  9 09:49:17 POS kernel: [    0.828581] system 00:0a: [io  0x0b00-0x0b0f] has been reserved
Nov  9 09:49:17 POS kernel: [    0.828583] system 00:0a: [io  0x0b20-0x0b3f] has been reserved
Nov  9 09:49:17 POS kernel: [    0.828585] system 00:0a: [io  0x0900-0x090f] has been reserved
Nov  9 09:49:17 POS kernel: [    0.828586] system 00:0a: [io  0x0910-0x091f] has been reserved
Nov  9 09:49:17 POS kernel: [    0.828588] system 00:0a: [io  0xfe00-0xfefe] has been reserved
Nov  9 09:49:17 POS kernel: [    0.828590] system 00:0a: [mem 0xcff00000-0xcfffffff] has been reserved
Nov  9 09:49:17 POS kernel: [    0.828592] system 00:0a: [mem 0xffb80000-0xffbfffff] has been reserved
Nov  9 09:49:17 POS kernel: [    0.828594] system 00:0a: [mem 0xfec10000-0xfec1001f] has been reserved
Nov  9 09:49:17 POS kernel: [    0.828596] system 00:0a: [mem 0xfed40000-0xfed44fff] has been reserved
Nov  9 09:49:17 POS kernel: [    0.828599] system 00:0b: [io  0x0230-0x023f] has been reserved
Nov  9 09:49:17 POS kernel: [    0.828600] system 00:0b: [io  0x0290-0x029f] has been reserved
Nov  9 09:49:17 POS kernel: [    0.828602] system 00:0b: [io  0x0300-0x030f] has been reserved
Nov  9 09:49:17 POS kernel: [    0.828604] system 00:0b: [io  0x0a30-0x0a3f] has been reserved
Nov  9 09:49:17 POS kernel: [    0.828606] system 00:0c: [mem 0xe0000000-0xefffffff] has been reserved
Nov  9 09:49:17 POS kernel: [    0.828610] system 00:0d: [mem 0x00000000-0x0009ffff] could not be reserved
Nov  9 09:49:17 POS kernel: [    0.828611] system 00:0d: [mem 0x000c0000-0x000cffff] has been reserved
Nov  9 09:49:17 POS kernel: [    0.828615] system 00:0d: [mem 0x000e0000-0x000fffff] could not be reserved
Nov  9 09:49:17 POS kernel: [    0.828617] system 00:0d: [mem 0x00100000-0xcfefffff] could not be reserved
Nov  9 09:49:17 POS kernel: [    0.828618] system 00:0d: [mem 0xfec00000-0xffffffff] could not be reserved
Nov  9 09:49:17 POS kernel: [    0.833940] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Nov  9 09:49:17 POS kernel: [    0.833943] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
Nov  9 09:49:17 POS kernel: [    0.833945] pci 0000:00:01.0:   bridge window [mem 0xfe900000-0xfeafffff]
Nov  9 09:49:17 POS kernel: [    0.833947] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
Nov  9 09:49:17 POS kernel: [    0.833950] pci 0000:00:0a.0: PCI bridge to [bus 02-02]
Nov  9 09:49:17 POS kernel: [    0.833952] pci 0000:00:0a.0:   bridge window [io  0xe000-0xefff]
Nov  9 09:49:17 POS kernel: [    0.833954] pci 0000:00:0a.0:   bridge window [mem 0xfeb00000-0xfebfffff]
Nov  9 09:49:17 POS kernel: [    0.833956] pci 0000:00:0a.0:   bridge window [mem 0xfdf00000-0xfdffffff 64bit pref]
Nov  9 09:49:17 POS kernel: [    0.833959] pci 0000:00:14.4: PCI bridge to [bus 03-03]
Nov  9 09:49:17 POS kernel: [    0.833960] pci 0000:00:14.4:   bridge window [io  disabled]
Nov  9 09:49:17 POS kernel: [    0.833964] pci 0000:00:14.4:   bridge window [mem disabled]
Nov  9 09:49:17 POS kernel: [    0.833967] pci 0000:00:14.4:   bridge window [mem pref disabled]
Nov  9 09:49:17 POS kernel: [    0.833985] pci 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Nov  9 09:49:17 POS kernel: [    0.834041] NET: Registered protocol family 2
Nov  9 09:49:17 POS kernel: [    0.834145] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
Nov  9 09:49:17 POS kernel: [    0.834981] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Nov  9 09:49:17 POS kernel: [    0.837081] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Nov  9 09:49:17 POS kernel: [    0.837342] TCP: Hash tables configured (established 524288 bind 65536)
Nov  9 09:49:17 POS kernel: [    0.837344] TCP reno registered
Nov  9 09:49:17 POS kernel: [    0.837352] UDP hash table entries: 2048 (order: 4, 65536 bytes)
Nov  9 09:49:17 POS kernel: [    0.837377] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
Nov  9 09:49:17 POS kernel: [    0.837460] NET: Registered protocol family 1
Nov  9 09:49:17 POS kernel: [    0.837471] pci 0000:00:01.0: MSI quirk detected; subordinate MSI disabled
Nov  9 09:49:17 POS kernel: [    1.003511] PCI-DMA: Disabling AGP.
Nov  9 09:49:17 POS kernel: [    1.003597] PCI-DMA: aperture base @ 20000000 size 65536 KB
Nov  9 09:49:17 POS kernel: [    1.003599] PCI-DMA: using GART IOMMU.
Nov  9 09:49:17 POS kernel: [    1.003601] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
Nov  9 09:49:17 POS kernel: [    1.006726] Scanning for low memory corruption every 60 seconds
Nov  9 09:49:17 POS kernel: [    1.006813] audit: initializing netlink socket (disabled)
Nov  9 09:49:17 POS kernel: [    1.006826] type=2000 audit(1289292550.000:1): initialized
Nov  9 09:49:17 POS kernel: [    1.015453] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Nov  9 09:49:17 POS kernel: [    1.016364] VFS: Disk quotas dquot_6.5.2
Nov  9 09:49:17 POS kernel: [    1.016397] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Nov  9 09:49:17 POS kernel: [    1.016775] fuse init (API version 7.14)
Nov  9 09:49:17 POS kernel: [    1.016824] msgmni has been set to 6908
Nov  9 09:49:17 POS kernel: [    1.018371] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Nov  9 09:49:17 POS kernel: [    1.018373] io scheduler noop registered
Nov  9 09:49:17 POS kernel: [    1.018374] io scheduler deadline registered
Nov  9 09:49:17 POS kernel: [    1.018396] io scheduler cfq registered (default)
Nov  9 09:49:17 POS kernel: [    1.018585] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Nov  9 09:49:17 POS kernel: [    1.018599] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Nov  9 09:49:17 POS kernel: [    1.018701] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Nov  9 09:49:17 POS kernel: [    1.018704] ACPI: Power Button [PWRB]
Nov  9 09:49:17 POS kernel: [    1.018729] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Nov  9 09:49:17 POS kernel: [    1.018731] ACPI: Power Button [PWRF]
Nov  9 09:49:17 POS kernel: [    1.021678] ERST: Table is not found!
Nov  9 09:49:17 POS kernel: [    1.021793] Linux agpgart interface v0.103
Nov  9 09:49:17 POS kernel: [    1.021795] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Nov  9 09:49:17 POS kernel: [    1.021893] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Nov  9 09:49:17 POS kernel: [    1.022112] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Nov  9 09:49:17 POS kernel: [    1.022722] brd: module loaded
Nov  9 09:49:17 POS kernel: [    1.023018] loop: module loaded
Nov  9 09:49:17 POS kernel: [    1.023167] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov  9 09:49:17 POS kernel: [    1.023389] Fixed MDIO Bus: probed
Nov  9 09:49:17 POS kernel: [    1.023408] PPP generic driver version 2.4.2
Nov  9 09:49:17 POS kernel: [    1.023438] tun: Universal TUN/TAP device driver, 1.6
Nov  9 09:49:17 POS kernel: [    1.023439] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Nov  9 09:49:17 POS kernel: [    1.023491] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Nov  9 09:49:17 POS kernel: [    1.023521] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Nov  9 09:49:17 POS kernel: [    1.023542] ehci_hcd 0000:00:12.2: EHCI Host Controller
Nov  9 09:49:17 POS kernel: [    1.023568] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
Nov  9 09:49:17 POS kernel: [    1.023595] ehci_hcd 0000:00:12.2: debug port 1
Nov  9 09:49:17 POS kernel: [    1.023612] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfe8ff800
Nov  9 09:49:17 POS kernel: [    1.042885] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
Nov  9 09:49:17 POS kernel: [    1.042971] hub 1-0:1.0: USB hub found
Nov  9 09:49:17 POS kernel: [    1.042974] hub 1-0:1.0: 6 ports detected
Nov  9 09:49:17 POS kernel: [    1.043059] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Nov  9 09:49:17 POS kernel: [    1.043071] ehci_hcd 0000:00:13.2: EHCI Host Controller
Nov  9 09:49:17 POS kernel: [    1.043092] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
Nov  9 09:49:17 POS kernel: [    1.043115] ehci_hcd 0000:00:13.2: debug port 1
Nov  9 09:49:17 POS kernel: [    1.043133] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfe8ff400
Nov  9 09:49:17 POS kernel: [    1.060018] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
Nov  9 09:49:17 POS kernel: [    1.060086] hub 2-0:1.0: USB hub found
Nov  9 09:49:17 POS kernel: [    1.060089] hub 2-0:1.0: 6 ports detected
Nov  9 09:49:17 POS kernel: [    1.060152] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Nov  9 09:49:17 POS kernel: [    1.060184] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov  9 09:49:17 POS kernel: [    1.060196] ohci_hcd 0000:00:12.0: OHCI Host Controller
Nov  9 09:49:17 POS kernel: [    1.060217] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
Nov  9 09:49:17 POS kernel: [    1.060239] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfe8fe000
Nov  9 09:49:17 POS kernel: [    1.124095] hub 3-0:1.0: USB hub found
Nov  9 09:49:17 POS kernel: [    1.124101] hub 3-0:1.0: 3 ports detected
Nov  9 09:49:17 POS kernel: [    1.124189] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov  9 09:49:17 POS kernel: [    1.124200] ohci_hcd 0000:00:12.1: OHCI Host Controller
Nov  9 09:49:17 POS kernel: [    1.124220] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
Nov  9 09:49:17 POS kernel: [    1.124235] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfe8fd000
Nov  9 09:49:17 POS kernel: [    1.184083] hub 4-0:1.0: USB hub found
Nov  9 09:49:17 POS kernel: [    1.184088] hub 4-0:1.0: 3 ports detected
Nov  9 09:49:17 POS kernel: [    1.184176] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Nov  9 09:49:17 POS kernel: [    1.184188] ohci_hcd 0000:00:13.0: OHCI Host Controller
Nov  9 09:49:17 POS kernel: [    1.184208] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
Nov  9 09:49:17 POS kernel: [    1.184228] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfe8fc000
Nov  9 09:49:17 POS kernel: [    1.244093] hub 5-0:1.0: USB hub found
Nov  9 09:49:17 POS kernel: [    1.244098] hub 5-0:1.0: 3 ports detected
Nov  9 09:49:17 POS kernel: [    1.244184] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Nov  9 09:49:17 POS kernel: [    1.244195] ohci_hcd 0000:00:13.1: OHCI Host Controller
Nov  9 09:49:17 POS kernel: [    1.244215] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
Nov  9 09:49:17 POS kernel: [    1.244230] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfe8fb000
Nov  9 09:49:17 POS kernel: [    1.304084] hub 6-0:1.0: USB hub found
Nov  9 09:49:17 POS kernel: [    1.304090] hub 6-0:1.0: 3 ports detected
Nov  9 09:49:17 POS kernel: [    1.304178] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Nov  9 09:49:17 POS kernel: [    1.304190] ohci_hcd 0000:00:14.5: OHCI Host Controller
Nov  9 09:49:17 POS kernel: [    1.304211] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
Nov  9 09:49:17 POS kernel: [    1.304225] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfe8fa000
Nov  9 09:49:17 POS kernel: [    1.364083] hub 7-0:1.0: USB hub found
Nov  9 09:49:17 POS kernel: [    1.364088] hub 7-0:1.0: 2 ports detected
Nov  9 09:49:17 POS kernel: [    1.364157] uhci_hcd: USB Universal Host Controller Interface driver
Nov  9 09:49:17 POS kernel: [    1.364220] PNP: No PS/2 controller found. Probing ports directly.
Nov  9 09:49:17 POS kernel: [    1.364570] serio: i8042 KBD port at 0x60,0x64 irq 1
Nov  9 09:49:17 POS kernel: [    1.364579] serio: i8042 AUX port at 0x60,0x64 irq 12
Nov  9 09:49:17 POS kernel: [    1.364646] mice: PS/2 mouse device common for all mice
Nov  9 09:49:17 POS kernel: [    1.364707] rtc_cmos 00:03: RTC can wake from S4
Nov  9 09:49:17 POS kernel: [    1.364729] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
Nov  9 09:49:17 POS kernel: [    1.364751] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
Nov  9 09:49:17 POS kernel: [    1.364815] device-mapper: uevent: version 1.0.3
Nov  9 09:49:17 POS kernel: [    1.364871] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
Nov  9 09:49:17 POS kernel: [    1.364949] device-mapper: multipath: version 1.1.1 loaded
Nov  9 09:49:17 POS kernel: [    1.364951] device-mapper: multipath round-robin: version 1.0.0 loaded
Nov  9 09:49:17 POS kernel: [    1.365117] cpuidle: using governor ladder
Nov  9 09:49:17 POS kernel: [    1.365118] cpuidle: using governor menu
Nov  9 09:49:17 POS kernel: [    1.365280] TCP cubic registered
Nov  9 09:49:17 POS kernel: [    1.365357] NET: Registered protocol family 10
Nov  9 09:49:17 POS kernel: [    1.365583] lo: Disabled Privacy Extensions
Nov  9 09:49:17 POS kernel: [    1.365713] NET: Registered protocol family 17
Nov  9 09:49:17 POS kernel: [    1.365754] powernow-k8: Found 1 AMD Phenom(tm) II X4 955 Processor (4 cpu cores) (version 2.20.00)
Nov  9 09:49:17 POS kernel: [    1.365820] registered taskstats version 1
Nov  9 09:49:17 POS kernel: [    1.365975]   Magic number: 2:341:826
Nov  9 09:49:17 POS kernel: [    1.366025] rtc_cmos 00:03: setting system clock to 2010-11-09 08:49:10 UTC (1289292550)
Nov  9 09:49:17 POS kernel: [    1.366027] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Nov  9 09:49:17 POS kernel: [    1.366029] EDD information not available.
Nov  9 09:49:17 POS kernel: [    1.366066] Freeing unused kernel memory: 908k freed
Nov  9 09:49:17 POS kernel: [    1.366236] Write protecting the kernel read-only data: 10240k
Nov  9 09:49:17 POS kernel: [    1.366333] Freeing unused kernel memory: 416k freed
Nov  9 09:49:17 POS kernel: [    1.366494] Freeing unused kernel memory: 1644k freed
Nov  9 09:49:17 POS kernel: [    1.376922] udev[132]: starting version 163
Nov  9 09:49:17 POS kernel: [    1.398977] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Nov  9 09:49:17 POS kernel: [    1.398990] r8169 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Nov  9 09:49:17 POS kernel: [    1.399396] r8169 0000:02:00.0: eth0: RTL8168d/8111d at 0xffffc900110d2000, 20:cf:30:9e:83:b1, XID 083000c0 IRQ 41
Nov  9 09:49:17 POS kernel: [    1.444110] scsi0 : pata_atiixp
Nov  9 09:49:17 POS kernel: [    1.444205] scsi1 : pata_atiixp
Nov  9 09:49:17 POS kernel: [    1.445137] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
Nov  9 09:49:17 POS kernel: [    1.445139] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
Nov  9 09:49:17 POS kernel: [    1.445303] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Nov  9 09:49:17 POS kernel: [    1.445416] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
Nov  9 09:49:17 POS kernel: [    1.445419] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
Nov  9 09:49:17 POS kernel: [    1.445709] scsi2 : ahci
Nov  9 09:49:17 POS kernel: [    1.445762] scsi3 : ahci
Nov  9 09:49:17 POS kernel: [    1.445806] scsi4 : ahci
Nov  9 09:49:17 POS kernel: [    1.445845] scsi5 : ahci
Nov  9 09:49:17 POS kernel: [    1.445882] scsi6 : ahci
Nov  9 09:49:17 POS kernel: [    1.445920] scsi7 : ahci
Nov  9 09:49:17 POS kernel: [    1.445951] ata3: SATA max UDMA/133 abar m1024@0xfe8ffc00 port 0xfe8ffd00 irq 22
Nov  9 09:49:17 POS kernel: [    1.445954] ata4: SATA max UDMA/133 abar m1024@0xfe8ffc00 port 0xfe8ffd80 irq 22
Nov  9 09:49:17 POS kernel: [    1.445957] ata5: SATA max UDMA/133 abar m1024@0xfe8ffc00 port 0xfe8ffe00 irq 22
Nov  9 09:49:17 POS kernel: [    1.445959] ata6: SATA max UDMA/133 abar m1024@0xfe8ffc00 port 0xfe8ffe80 irq 22
Nov  9 09:49:17 POS kernel: [    1.445962] ata7: SATA max UDMA/133 abar m1024@0xfe8ffc00 port 0xfe8fff00 irq 22
Nov  9 09:49:17 POS kernel: [    1.445964] ata8: SATA max UDMA/133 abar m1024@0xfe8ffc00 port 0xfe8fff80 irq 22
Nov  9 09:49:17 POS kernel: [    1.630463] ata1.01: ATAPI: TSSTcorpDVD-ROM SH-D162C, TS04, max UDMA/33
Nov  9 09:49:17 POS kernel: [    1.670415] ata1.01: configured for UDMA/33
Nov  9 09:49:17 POS kernel: [    1.671216] scsi 0:0:1:0: CD-ROM            TSSTcorp DVD-ROM SH-D162C TS04 PQ: 0 ANSI: 5
Nov  9 09:49:17 POS kernel: [    1.673169] sr0: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
Nov  9 09:49:17 POS kernel: [    1.673172] Uniform CD-ROM driver Revision: 3.20
Nov  9 09:49:17 POS kernel: [    1.673282] sr 0:0:1:0: Attached scsi generic sg0 type 5
Nov  9 09:49:17 POS kernel: [    1.790077] ata8: SATA link down (SStatus 0 SControl 300)
Nov  9 09:49:17 POS kernel: [    1.790080] ata4: SATA link down (SStatus 0 SControl 300)
Nov  9 09:49:17 POS kernel: [    1.790134] ata7: SATA link down (SStatus 0 SControl 300)
Nov  9 09:49:17 POS kernel: [    1.790140] ata6: SATA link down (SStatus 0 SControl 300)
Nov  9 09:49:17 POS kernel: [    1.790169] ata5: SATA link down (SStatus 0 SControl 300)
Nov  9 09:49:17 POS kernel: [    1.810062] usb 4-2: new full speed USB device using ohci_hcd and address 2
Nov  9 09:49:17 POS kernel: [    1.970030] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Nov  9 09:49:17 POS kernel: [    1.976417] ata3.00: ATA-7: SAMSUNG HD322HJ, 1AC01118, max UDMA7
Nov  9 09:49:17 POS kernel: [    1.976420] ata3.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Nov  9 09:49:17 POS kernel: [    1.982868] ata3.00: configured for UDMA/133
Nov  9 09:49:17 POS kernel: [    2.002594] scsi 2:0:0:0: Direct-Access     ATA      SAMSUNG HD322HJ  1AC0 PQ: 0 ANSI: 5
Nov  9 09:49:17 POS kernel: [    2.002690] sd 2:0:0:0: Attached scsi generic sg1 type 0
Nov  9 09:49:17 POS kernel: [    2.002693] sd 2:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
Nov  9 09:49:17 POS kernel: [    2.002750] sd 2:0:0:0: [sda] Write Protect is off
Nov  9 09:49:17 POS kernel: [    2.002774] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  9 09:49:17 POS kernel: [    2.002894]  sda: sda1 sda2 < sda5 sda6 sda7 >
Nov  9 09:49:17 POS kernel: [    2.042558] usbcore: registered new interface driver hiddev
Nov  9 09:49:17 POS kernel: [    2.047186] input: Razer Razer Lycosa as /devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2:1.0/input/input2
Nov  9 09:49:17 POS kernel: [    2.047234] generic-usb 0003:1532:0109.0001: input,hidraw0: USB HID v1.10 Keyboard [Razer Razer Lycosa] on usb-0000:00:12.1-2/input0
Nov  9 09:49:17 POS kernel: [    2.051264] sd 2:0:0:0: [sda] Attached SCSI disk
Nov  9 09:49:17 POS kernel: [    2.055100] input: Razer Razer Lycosa as /devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2:1.1/input/input3
Nov  9 09:49:17 POS kernel: [    2.055186] generic-usb 0003:1532:0109.0002: input,hidraw1: USB HID v1.10 Device [Razer Razer Lycosa] on usb-0000:00:12.1-2/input1
Nov  9 09:49:17 POS kernel: [    2.055196] usbcore: registered new interface driver usbhid
Nov  9 09:49:17 POS kernel: [    2.055197] usbhid: USB HID core driver
Nov  9 09:49:17 POS kernel: [    2.302519] usb 3-2: new full speed USB device using ohci_hcd and address 2
Nov  9 09:49:17 POS kernel: [    2.368910] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
Nov  9 09:49:17 POS kernel: [    2.506181] input: Razer Razer DeathAdder as /devices/pci0000:00/0000:00:12.0/usb3/3-2/3-2:1.0/input/input4
Nov  9 09:49:17 POS kernel: [    2.506230] generic-usb 0003:1532:0016.0003: input,hidraw2: USB HID v1.11 Mouse [Razer Razer DeathAdder] on usb-0000:00:12.0-2/input0
Nov  9 09:49:17 POS kernel: [    4.176970] Adding 6324220k swap on /dev/sda1.  Priority:-1 extents:1 across:6324220k 
Nov  9 09:49:17 POS kernel: [    5.045844] udev[402]: starting version 163
Nov  9 09:49:17 POS kernel: [    5.543833] EXT4-fs (sda7): re-mounted. Opts: errors=remount-ro
Nov  9 09:49:17 POS kernel: [    5.810416] type=1400 audit(1289292554.924:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=548 comm="apparmor_parser"
Nov  9 09:49:17 POS kernel: [    5.810609] type=1400 audit(1289292554.924:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=548 comm="apparmor_parser"
Nov  9 09:49:17 POS kernel: [    5.810711] type=1400 audit(1289292554.924:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=548 comm="apparmor_parser"
Nov  9 09:49:17 POS kernel: [    6.542875] lp: driver loaded but no devices found
Nov  9 09:49:17 POS kernel: [    6.611998] parport_pc 00:06: reported by Plug and Play ACPI
Nov  9 09:49:17 POS kernel: [    6.612049] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Nov  9 09:49:17 POS kernel: [    6.630028] ppdev: user-space parallel port driver
Nov  9 09:49:17 POS kernel: [    6.700105] lp0: using parport0 (interrupt-driven).
Nov  9 09:49:17 POS kernel: [    7.367086] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Nov  9 09:49:17 POS kernel: [    7.426546] ACPI: resource piix4_smbus [io  0x0b00-0x0b07] conflicts with ACPI region SOR1 [io  0x0b00-0x0b0f 64bit pref]
Nov  9 09:49:17 POS kernel: [    7.426548] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Nov  9 09:49:17 POS kernel: [    7.439575] EDAC MC: Ver: 2.1.0 Oct 16 2010
Nov  9 09:49:17 POS kernel: [    7.615329] EDAC amd64_edac:  Ver: 3.3.0 Oct 16 2010
Nov  9 09:49:17 POS kernel: [    7.615404] EDAC amd64: This node reports that Memory ECC is currently disabled, set F3x44[22] (0000:00:18.3).
Nov  9 09:49:17 POS kernel: [    7.615411] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
Nov  9 09:49:17 POS kernel: [    7.615412]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
Nov  9 09:49:17 POS kernel: [    7.615413]  (Note that use of the override may cause unknown side effects.)
Nov  9 09:49:17 POS kernel: [    7.615422] amd64_edac: probe of 0000:00:18.2 failed with error -22
Nov  9 09:49:17 POS kernel: [    8.020325] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Nov  9 09:49:17 POS kernel: [    8.020329] Disabling lock debugging due to kernel taint
Nov  9 09:49:17 POS kernel: [    8.043898] [fglrx] Maximum main memory to use for locked dma buffers: 3304 MBytes.
Nov  9 09:49:17 POS kernel: [    8.043927] [fglrx]   vendor: 1002 device: 9710 count: 1
Nov  9 09:49:17 POS kernel: [    8.044169] [fglrx] ioport: bar 1, base 0xd000, size: 0x100
Nov  9 09:49:17 POS kernel: [    8.044179] pci 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Nov  9 09:49:17 POS kernel: [    8.044424] [fglrx] Kernel PAT support is enabled
Nov  9 09:49:17 POS kernel: [    8.044440] [fglrx] module loaded - fglrx 8.78.30 [Sep 20 2010] with 1 minors
Nov  9 09:49:18 POS kernel: [    9.218100] type=1400 audit(1289292558.344:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=832 comm="apparmor_parser"
Nov  9 09:49:18 POS kernel: [    9.218286] type=1400 audit(1289292558.344:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=832 comm="apparmor_parser"
Nov  9 09:49:18 POS kernel: [    9.218392] type=1400 audit(1289292558.344:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=832 comm="apparmor_parser"
Nov  9 09:49:18 POS kernel: [    9.245624] type=1400 audit(1289292558.374:8): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=831 comm="apparmor_parser"
Nov  9 09:49:18 POS kernel: [    9.261116] type=1400 audit(1289292558.384:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=833 comm="apparmor_parser"
Nov  9 09:49:18 POS kernel: [    9.263417] type=1400 audit(1289292558.394:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=833 comm="apparmor_parser"
Nov  9 09:49:18 POS kernel: [    9.264864] type=1400 audit(1289292558.394:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=833 comm="apparmor_parser"
Nov  9 09:49:18 POS kernel: [    9.278019] type=1400 audit(1289292558.404:12): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=835 comm="apparmor_parser"
Nov  9 09:49:18 POS kernel: [    9.278252] type=1400 audit(1289292558.404:13): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=835 comm="apparmor_parser"
Nov  9 09:49:18 POS kernel: [    9.319130] type=1400 audit(1289292558.444:14): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=836 comm="apparmor_parser"
Nov  9 09:49:18 POS kernel: [    9.332468] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov  9 09:49:21 POS kernel: [   12.778437] r8169 0000:02:00.0: eth0: link up
Nov  9 09:49:21 POS kernel: [   12.778447] r8169 0000:02:00.0: eth0: link up
Nov  9 09:49:24 POS kernel: [   14.881631] [fglrx] GART Table is not in FRAME_BUFFER range 
Nov  9 09:49:24 POS kernel: [   14.881749] [fglrx] Could not enable MSI; System prevented initialization
Nov  9 09:49:24 POS kernel: [   14.882167] [fglrx] Firegl kernel thread PID: 1235
Nov  9 09:49:24 POS kernel: [   14.882418] [fglrx] IRQ 18 Enabled
Nov  9 09:49:24 POS kernel: [   15.618785] EXT4-fs (sda7): re-mounted. Opts: errors=remount-ro,commit=0
Nov  9 09:49:25 POS pulseaudio[1289]: lock-autospawn.c: Cannot access autospawn lock.
Nov  9 09:49:25 POS kernel: [   16.596729] [fglrx] Gart USWC size:1080 M.
Nov  9 09:49:25 POS kernel: [   16.596732] [fglrx] Gart cacheable size:428 M.
Nov  9 09:49:25 POS kernel: [   16.596735] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
Nov  9 09:49:25 POS kernel: [   16.596737] [fglrx] Reserved FB block: Unshared offset:1fffb000, size:5000 
Nov  9 09:49:33 POS kernel: [   21.861020] EXT4-fs (sda7): re-mounted. Opts: errors=remount-ro,commit=0
Nov  9 10:23:36 POS rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="782" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.

Best regards
Blyme

---

### Post by Blyme on 2010-11-09
Nobody? :confused:

---

