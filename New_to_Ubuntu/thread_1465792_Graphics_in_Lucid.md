---
title: "Graphics in Lucid"
date: 2010-04-29
forum: New to Ubuntu
---

### Post by herbertportillo on 2010-04-29
I downloaded the Lucid .iso image today. I checked the MD5 checksum and it was perfectly fine.

Then I burned the .iso to a blank CD using the slowest possible speed. The CD burned perfectly with no problems.

Then I restarted the computer and booted to the CD and did a clean install of Lucid onto my computer. No problems, and the installation completed perfectly.

I restarted the computer, and the graphics SUCK. I can't see a thing. I'm assuming that it's due to the stupid nouveau driver. How can I disable the dumbass nouveau driver so that it'll log in at least into a crappy resolution so that I can install one of the proprietary restricted drivers?

By the way, I have a crappy nVidia GeForce 6150 LE. Any help is appreciated. Thanks.

---

### Post by Kafubie on 2010-04-29
**I'll bump for knowledge!**

---

### Post by herbertportillo on 2010-04-29
Screw it. I'm sticking with Karmic.

I hope that whoever helped design nouveau chokes on a pretzel, has a shoe thrown at his head, gets stuck inside a Chinese palace for the rest of his life, gets mocked whenever he dances, and has a stupid ugly mom named Barbara.

---

### Post by herbertportillo on 2010-04-29
Fixed it.

Did a clean install of Karmic, and then went to the Update Manager and simply did an upgrade from there to Lucid. Works flawlessly, and Lucid is really fast. :)

Thanks to me!!!!

---

### Post by CharlesA on 2010-04-29
I wonder if it would have been possible to use ngvey-ng to install the proprietary drivers from the command line.

Just a thought.

---

### Post by herbertportillo on 2010-05-05
So, I suppose I spoke prematurely as I am now having problems with the graphics display.

Sometimes when I turn on the computer, the correct resolution is displayed and everything is gravity. But about half of the time, I get an error saying that the the driver couldn't be loaded. I've tried deleting xorg.conf files and creating new ones and backing them up and nothing works. I don't know what to do.

Here are some screenshots. Any and all help is appreciated. Thanks.

---

### Post by cavh on 2010-05-05
See my Nvidia driver discussion at [http://ubuntuforums.org/showthread.php?t=1472440]("http://ubuntuforums.org/showthread.php?t=1472440")

---

### Post by sandyd on 2010-05-05
can you attach /var/log/syslog here?

---

### Post by herbertportillo on 2010-05-05
Hmm. I'm trying to upload the syslog but it seems to be too big. Oops.

Well, the computer seems to be fine right now. Sometimes all it takes is a restart and the graphics driver seems to get loaded. I'll wait and see when the next time the error message pops up (it will, guaranteed) and I'll upload the syslog for everyone to look at. Thanks.

:-)

---

### Post by herbertportillo on 2010-05-05
OK, it did it again.

Here's the syslog.
```
May  5 15:25:00 herbert-desktop kernel: imklog 4.2.0, log source = /proc/kmsg started.
May  5 15:25:00 herbert-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="759" x-info="http://www.rsyslog.com"] (re)start
May  5 15:25:00 herbert-desktop rsyslogd: rsyslogd's groupid changed to 103
May  5 15:25:00 herbert-desktop rsyslogd: rsyslogd's userid changed to 101
May  5 15:25:00 herbert-desktop rsyslogd-2039: Could no open output file '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
May  5 15:25:00 herbert-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
May  5 15:25:00 herbert-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
May  5 15:25:00 herbert-desktop kernel: [    0.000000] Linux version 2.6.32-22-generic (buildd@yellow) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 (Ubuntu 2.6.32-22.33-generic 2.6.32.11+drm33.2)
May  5 15:25:00 herbert-desktop kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=14f62bd4-0637-4b04-a069-24a12a3f6fa0 ro quiet splash
May  5 15:25:00 herbert-desktop kernel: [    0.000000] KERNEL supported cpus:
May  5 15:25:00 herbert-desktop kernel: [    0.000000]   Intel GenuineIntel
May  5 15:25:00 herbert-desktop kernel: [    0.000000]   AMD AuthenticAMD
May  5 15:25:00 herbert-desktop kernel: [    0.000000]   Centaur CentaurHauls
May  5 15:25:00 herbert-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
May  5 15:25:00 herbert-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
May  5 15:25:00 herbert-desktop kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
May  5 15:25:00 herbert-desktop kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
May  5 15:25:00 herbert-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000b7ee0000 (usable)
May  5 15:25:00 herbert-desktop kernel: [    0.000000]  BIOS-e820: 00000000b7ee0000 - 00000000b7ee3000 (ACPI NVS)
May  5 15:25:00 herbert-desktop kernel: [    0.000000]  BIOS-e820: 00000000b7ee3000 - 00000000b7ef0000 (ACPI data)
May  5 15:25:00 herbert-desktop kernel: [    0.000000]  BIOS-e820: 00000000b7ef0000 - 00000000b7f00000 (reserved)
May  5 15:25:00 herbert-desktop kernel: [    0.000000]  BIOS-e820: 00000000b8000000 - 00000000c0000000 (reserved)
May  5 15:25:00 herbert-desktop kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
May  5 15:25:00 herbert-desktop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
May  5 15:25:00 herbert-desktop kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000180000000 (usable)
May  5 15:25:00 herbert-desktop kernel: [    0.000000] DMI 2.4 present.
May  5 15:25:00 herbert-desktop kernel: [    0.000000] last_pfn = 0x180000 max_arch_pfn = 0x400000000
May  5 15:25:00 herbert-desktop kernel: [    0.000000] MTRR default type: uncachable
May  5 15:25:00 herbert-desktop kernel: [    0.000000] MTRR fixed ranges enabled:
May  5 15:25:00 herbert-desktop kernel: [    0.000000]   00000-9FFFF write-back
May  5 15:25:00 herbert-desktop kernel: [    0.000000]   A0000-BFFFF uncachable
May  5 15:25:00 herbert-desktop kernel: [    0.000000]   C0000-C7FFF write-protect
May  5 15:25:00 herbert-desktop kernel: [    0.000000]   C8000-FFFFF uncachable
May  5 15:25:00 herbert-desktop kernel: [    0.000000] MTRR variable ranges enabled:
May  5 15:25:00 herbert-desktop kernel: [    0.000000]   0 base 0000000000 mask FF80000000 write-back
May  5 15:25:00 herbert-desktop kernel: [    0.000000]   1 base 0080000000 mask FFE0000000 write-back
May  5 15:25:00 herbert-desktop kernel: [    0.000000]   2 base 00A0000000 mask FFF0000000 write-back
May  5 15:25:00 herbert-desktop kernel: [    0.000000]   3 base 00B0000000 mask FFF8000000 write-back
May  5 15:25:00 herbert-desktop kernel: [    0.000000]   4 base 00B7F00000 mask FFFFF00000 uncachable
May  5 15:25:00 herbert-desktop kernel: [    0.000000]   5 base 0100000000 mask FF80000000 write-back
May  5 15:25:00 herbert-desktop kernel: [    0.000000]   6 disabled
May  5 15:25:00 herbert-desktop kernel: [    0.000000]   7 disabled
May  5 15:25:00 herbert-desktop kernel: [    0.000000] TOM2: 0000000180000000 aka 6144M
May  5 15:25:00 herbert-desktop kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
May  5 15:25:00 herbert-desktop kernel: [    0.000000] e820 update range: 00000000b7f00000 - 0000000100000000 (usable) ==> (reserved)
May  5 15:25:00 herbert-desktop kernel: [    0.000000] last_pfn = 0xb7ee0 max_arch_pfn = 0x400000000
May  5 15:25:00 herbert-desktop kernel: [    0.000000] e820 update range: 0000000000001000 - 0000000000006000 (usable) ==> (reserved)
May  5 15:25:00 herbert-desktop kernel: [    0.000000] Scanning 1 areas for low memory corruption
May  5 15:25:00 herbert-desktop kernel: [    0.000000] modified physical RAM map:
May  5 15:25:00 herbert-desktop kernel: [    0.000000]  modified: 0000000000000000 - 0000000000001000 (usable)
May  5 15:25:00 herbert-desktop kernel: [    0.000000]  modified: 0000000000001000 - 0000000000006000 (reserved)
May  5 15:25:00 herbert-desktop kernel: [    0.000000]  modified: 0000000000006000 - 000000000009f000 (usable)
May  5 15:25:00 herbert-desktop kernel: [    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
May  5 15:25:00 herbert-desktop kernel: [    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
May  5 15:25:00 herbert-desktop kernel: [    0.000000]  modified: 0000000000100000 - 00000000b7ee0000 (usable)
May  5 15:25:00 herbert-desktop kernel: [    0.000000]  modified: 00000000b7ee0000 - 00000000b7ee3000 (ACPI NVS)
May  5 15:25:00 herbert-desktop kernel: [    0.000000]  modified: 00000000b7ee3000 - 00000000b7ef0000 (ACPI data)
May  5 15:25:00 herbert-desktop kernel: [    0.000000]  modified: 00000000b7ef0000 - 00000000b7f00000 (reserved)
May  5 15:25:00 herbert-desktop kernel: [    0.000000]  modified: 00000000b8000000 - 00000000c0000000 (reserved)
May  5 15:25:00 herbert-desktop kernel: [    0.000000]  modified: 00000000f0000000 - 00000000f4000000 (reserved)
May  5 15:25:00 herbert-desktop kernel: [    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
May  5 15:25:00 herbert-desktop kernel: [    0.000000]  modified: 0000000100000000 - 0000000180000000 (usable)
May  5 15:25:00 herbert-desktop kernel: [    0.000000] initial memory mapped : 0 - 20000000
May  5 15:25:00 herbert-desktop kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000b7ee0000
May  5 15:25:00 herbert-desktop kernel: [    0.000000] NX (Execute Disable) protection: active
May  5 15:25:00 herbert-desktop kernel: [    0.000000]  0000000000 - 00b7e00000 page 2M
May  5 15:25:00 herbert-desktop kernel: [    0.000000]  00b7e00000 - 00b7ee0000 page 4k
May  5 15:25:00 herbert-desktop kernel: [    0.000000] kernel direct mapping tables up to b7ee0000 @ 8000-d000
May  5 15:25:00 herbert-desktop kernel: [    0.000000] init_memory_mapping: 0000000100000000-0000000180000000
May  5 15:25:00 herbert-desktop kernel: [    0.000000] NX (Execute Disable) protection: active
May  5 15:25:00 herbert-desktop kernel: [    0.000000]  0100000000 - 0180000000 page 2M
May  5 15:25:00 herbert-desktop kernel: [    0.000000] kernel direct mapping tables up to 180000000 @ b000-12000
May  5 15:25:00 herbert-desktop kernel: [    0.000000] RAMDISK: 377fe000 - 37fef5aa
May  5 15:25:00 herbert-desktop kernel: [    0.000000] ACPI: RSDP 00000000000f8410 00014 (v00 DELL  )
May  5 15:25:00 herbert-desktop kernel: [    0.000000] ACPI: RSDT 00000000b7ee3040 00040 (v01 DELL    bMk     42302E31 AWRD 00000000)
May  5 15:25:00 herbert-desktop kernel: [    0.000000] ACPI: FACP 00000000b7ee3100 00074 (v01 DELL    bMk     42302E31 AWRD 00000000)
May  5 15:25:00 herbert-desktop kernel: [    0.000000] ACPI: DSDT 00000000b7ee31c0 0592F (v01 DELL    BMK     00001000 MSFT 0100000E)
May  5 15:25:00 herbert-desktop kernel: [    0.000000] ACPI: FACS 00000000b7ee0000 00040
May  5 15:25:00 herbert-desktop kernel: [    0.000000] ACPI: BOOT 00000000b7ee8b40 00028 (v01 DELL    bMk     42302E31 AWRD 00000000)
May  5 15:25:00 herbert-desktop kernel: [    0.000000] ACPI: SSDT 00000000b7ee8c80 001C4 (v01 PTLTD  POWERNOW 00000001  LTP 00000001)
May  5 15:25:00 herbert-desktop kernel: [    0.000000] ACPI: HPET 00000000b7ee8ec0 00038 (v01 DELL    bMk     42302E31 AWRD 00000098)
May  5 15:25:00 herbert-desktop kernel: [    0.000000] ACPI: MCFG 00000000b7ee8f40 0003C (v01 DELL    bMk     42302E31 AWRD 00000000)
May  5 15:25:00 herbert-desktop kernel: [    0.000000] ACPI: SLIC 00000000b7ee8fc0 00176 (v01 DELL    bMk     42302E31 AWRD 0100000E)
May  5 15:25:00 herbert-desktop kernel: [    0.000000] ACPI: APIC 00000000b7ee8bc0 00072 (v01 DELL    bMk     42302E31 AWRD 00000000)
May  5 15:25:00 herbert-desktop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
May  5 15:25:00 herbert-desktop kernel: [    0.000000] Scanning NUMA topology in Northbridge 24
May  5 15:25:00 herbert-desktop kernel: [    0.000000] No NUMA configuration found
May  5 15:25:00 herbert-desktop kernel: [    0.000000] Faking a node at 0000000000000000-0000000180000000
May  5 15:25:00 herbert-desktop kernel: [    0.000000] Bootmem setup node 0 0000000000000000-0000000180000000
May  5 15:25:00 herbert-desktop kernel: [    0.000000]   NODE_DATA [000000000000d000 - 0000000000011fff]
May  5 15:25:00 herbert-desktop kernel: [    0.000000]   bootmap [0000000000012000 -  0000000000041fff] pages 30
May  5 15:25:00 herbert-desktop kernel: [    0.000000] (8 early reservations) ==> bootmem [0000000000 - 0180000000]
May  5 15:25:00 herbert-desktop kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
May  5 15:25:00 herbert-desktop kernel: [    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
May  5 15:25:00 herbert-desktop kernel: [    0.000000]   #2 [0001000000 - 0001a29e64]    TEXT DATA BSS ==> [0001000000 - 0001a29e64]
May  5 15:25:00 herbert-desktop kernel: [    0.000000]   #3 [00377fe000 - 0037fef5aa]          RAMDISK ==> [00377fe000 - 0037fef5aa]
May  5 15:25:00 herbert-desktop kernel: [    0.000000]   #4 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
May  5 15:25:00 herbert-desktop kernel: [    0.000000]   #5 [0001a2a000 - 0001a2a228]              BRK ==> [0001a2a000 - 0001a2a228]
May  5 15:25:00 herbert-desktop kernel: [    0.000000]   #6 [0000008000 - 000000b000]          PGTABLE ==> [0000008000 - 000000b000]
May  5 15:25:00 herbert-desktop kernel: [    0.000000]   #7 [000000b000 - 000000d000]          PGTABLE ==> [000000b000 - 000000d000]
May  5 15:25:00 herbert-desktop kernel: [    0.000000] found SMP MP-table at [ffff8800000f3cf0] f3cf0
May  5 15:25:00 herbert-desktop kernel: [    0.000000]  [ffffea0000000000-ffffea00053fffff] PMD -> [ffff880028600000-ffff88002cbfffff] on node 0
May  5 15:25:00 herbert-desktop kernel: [    0.000000] Zone PFN ranges:
May  5 15:25:00 herbert-desktop kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
May  5 15:25:00 herbert-desktop kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
May  5 15:25:00 herbert-desktop kernel: [    0.000000]   Normal   0x00100000 -> 0x00180000
May  5 15:25:00 herbert-desktop kernel: [    0.000000] Movable zone start PFN for each node
May  5 15:25:00 herbert-desktop kernel: [    0.000000] early_node_map[4] active PFN ranges
May  5 15:25:00 herbert-desktop kernel: [    0.000000]     0: 0x00000000 -> 0x00000001
May  5 15:25:00 herbert-desktop kernel: [    0.000000]     0: 0x00000006 -> 0x0000009f
May  5 15:25:00 herbert-desktop kernel: [    0.000000]     0: 0x00000100 -> 0x000b7ee0
May  5 15:25:00 herbert-desktop kernel: [    0.000000]     0: 0x00100000 -> 0x00180000
May  5 15:25:00 herbert-desktop kernel: [    0.000000] On node 0 totalpages: 1277562
May  5 15:25:00 herbert-desktop kernel: [    0.000000]   DMA zone: 56 pages used for memmap
May  5 15:25:00 herbert-desktop kernel: [    0.000000]   DMA zone: 105 pages reserved
May  5 15:25:00 herbert-desktop kernel: [    0.000000]   DMA zone: 3833 pages, LIFO batch:0
May  5 15:25:00 herbert-desktop kernel: [    0.000000]   DMA32 zone: 14280 pages used for memmap
May  5 15:25:00 herbert-desktop kernel: [    0.000000]   DMA32 zone: 735000 pages, LIFO batch:31
May  5 15:25:00 herbert-desktop kernel: [    0.000000]   Normal zone: 7168 pages used for memmap
May  5 15:25:00 herbert-desktop kernel: [    0.000000]   Normal zone: 517120 pages, LIFO batch:31
May  5 15:25:00 herbert-desktop kernel: [    0.000000] Detected use of extended apic ids on hypertransport bus
May  5 15:25:00 herbert-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
May  5 15:25:00 herbert-desktop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
May  5 15:25:00 herbert-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
May  5 15:25:00 herbert-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
May  5 15:25:00 herbert-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
May  5 15:25:00 herbert-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
May  5 15:25:00 herbert-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
May  5 15:25:00 herbert-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
May  5 15:25:00 herbert-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
May  5 15:25:00 herbert-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
May  5 15:25:00 herbert-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
May  5 15:25:00 herbert-desktop kernel: [    0.000000] ACPI: IRQ9 used by override.
May  5 15:25:00 herbert-desktop kernel: [    0.000000] ACPI: IRQ14 used by override.
May  5 15:25:00 herbert-desktop kernel: [    0.000000] ACPI: IRQ15 used by override.
May  5 15:25:00 herbert-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
May  5 15:25:00 herbert-desktop kernel: [    0.000000] ACPI: HPET id: 0x10b9a201 base: 0xfeff0000
May  5 15:25:00 herbert-desktop kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
May  5 15:25:00 herbert-desktop kernel: [    0.000000] nr_irqs_gsi: 24
May  5 15:25:00 herbert-desktop kernel: [    0.000000] PM: Registered nosave memory: 0000000000001000 - 0000000000006000
May  5 15:25:00 herbert-desktop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
May  5 15:25:00 herbert-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
May  5 15:25:00 herbert-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
May  5 15:25:00 herbert-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000b7ee0000 - 00000000b7ee3000
May  5 15:25:00 herbert-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000b7ee3000 - 00000000b7ef0000
May  5 15:25:00 herbert-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000b7ef0000 - 00000000b7f00000
May  5 15:25:00 herbert-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000b7f00000 - 00000000b8000000
May  5 15:25:00 herbert-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000b8000000 - 00000000c0000000
May  5 15:25:00 herbert-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000c0000000 - 00000000f0000000
May  5 15:25:00 herbert-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000f4000000
May  5 15:25:00 herbert-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000f4000000 - 00000000fec00000
May  5 15:25:00 herbert-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000fec00000 - 0000000100000000
May  5 15:25:00 herbert-desktop kernel: [    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:30000000)
May  5 15:25:00 herbert-desktop kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
May  5 15:25:00 herbert-desktop kernel: [    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:2 nr_node_ids:1
May  5 15:25:00 herbert-desktop kernel: [    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880028200000 s91544 r8192 d23144 u1048576
May  5 15:25:00 herbert-desktop kernel: [    0.000000] pcpu-alloc: s91544 r8192 d23144 u1048576 alloc=1*2097152
May  5 15:25:00 herbert-desktop kernel: [    0.000000] pcpu-alloc: [0] 0 1 
May  5 15:25:00 herbert-desktop kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1255953
May  5 15:25:00 herbert-desktop kernel: [    0.000000] Policy zone: Normal
May  5 15:25:00 herbert-desktop kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=14f62bd4-0637-4b04-a069-24a12a3f6fa0 ro quiet splash
May  5 15:25:00 herbert-desktop kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
May  5 15:25:00 herbert-desktop kernel: [    0.000000] Initializing CPU#0
May  5 15:25:00 herbert-desktop kernel: [    0.000000] Checking aperture...
May  5 15:25:00 herbert-desktop kernel: [    0.000000] No AGP bridge found
May  5 15:25:00 herbert-desktop kernel: [    0.000000] Node 0: aperture @ 813e000000 size 32 MB
May  5 15:25:00 herbert-desktop kernel: [    0.000000] Aperture beyond 4GB. Ignoring.
May  5 15:25:00 herbert-desktop kernel: [    0.000000] Your BIOS doesn't leave a aperture memory hole
May  5 15:25:00 herbert-desktop kernel: [    0.000000] Please enable the IOMMU option in the BIOS setup
May  5 15:25:00 herbert-desktop kernel: [    0.000000] This costs you 64 MB of RAM
May  5 15:25:00 herbert-desktop kernel: [    0.000000] Mapping aperture over 65536 KB of RAM @ 20000000
May  5 15:25:00 herbert-desktop kernel: [    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000024000000
May  5 15:25:00 herbert-desktop kernel: [    0.000000] Memory: 4953956k/6291456k available (5409k kernel code, 1181208k absent, 156292k reserved, 2976k data, 876k init)
May  5 15:25:00 herbert-desktop kernel: [    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
May  5 15:25:00 herbert-desktop kernel: [    0.000000] Hierarchical RCU implementation.
May  5 15:25:00 herbert-desktop kernel: [    0.000000] NR_IRQS:4352 nr_irqs:424
May  5 15:25:00 herbert-desktop kernel: [    0.000000] spurious 8259A interrupt: IRQ7.
May  5 15:25:00 herbert-desktop kernel: [    0.000000] Console: colour VGA+ 80x25
May  5 15:25:00 herbert-desktop kernel: [    0.000000] console [tty0] enabled
May  5 15:25:00 herbert-desktop kernel: [    0.000000] allocated 51118080 bytes of page_cgroup
May  5 15:25:00 herbert-desktop kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
May  5 15:25:00 herbert-desktop kernel: [    0.000000] hpet clockevent registered
May  5 15:25:00 herbert-desktop kernel: [    0.000000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
May  5 15:25:00 herbert-desktop kernel: [    0.000000] Fast TSC calibration using PIT
May  5 15:25:00 herbert-desktop kernel: [    0.000000] Detected 2004.182 MHz processor.
May  5 15:25:00 herbert-desktop kernel: [    0.010006] Calibrating delay loop (skipped), value calculated using timer frequency.. 4008.36 BogoMIPS (lpj=20041820)
May  5 15:25:00 herbert-desktop kernel: [    0.010034] Security Framework initialized
May  5 15:25:00 herbert-desktop kernel: [    0.010057] AppArmor: AppArmor initialized
May  5 15:25:00 herbert-desktop kernel: [    0.010821] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
May  5 15:25:00 herbert-desktop kernel: [    0.016315] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
May  5 15:25:00 herbert-desktop kernel: [    0.020322] Mount-cache hash table entries: 256
May  5 15:25:00 herbert-desktop kernel: [    0.020482] Initializing cgroup subsys ns
May  5 15:25:00 herbert-desktop kernel: [    0.020486] Initializing cgroup subsys cpuacct
May  5 15:25:00 herbert-desktop kernel: [    0.020490] Initializing cgroup subsys memory
May  5 15:25:00 herbert-desktop kernel: [    0.020500] Initializing cgroup subsys devices
May  5 15:25:00 herbert-desktop kernel: [    0.020502] Initializing cgroup subsys freezer
May  5 15:25:00 herbert-desktop kernel: [    0.020505] Initializing cgroup subsys net_cls
May  5 15:25:00 herbert-desktop kernel: [    0.020525] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
May  5 15:25:00 herbert-desktop kernel: [    0.020528] CPU: L2 Cache: 512K (64 bytes/line)
May  5 15:25:00 herbert-desktop kernel: [    0.020531] CPU 0/0x0 -> Node 0
May  5 15:25:00 herbert-desktop kernel: [    0.020533] tseg: 00b7f00000
May  5 15:25:00 herbert-desktop kernel: [    0.020535] CPU: Physical Processor ID: 0
May  5 15:25:00 herbert-desktop kernel: [    0.020536] CPU: Processor Core ID: 0
May  5 15:25:00 herbert-desktop kernel: [    0.020539] mce: CPU supports 5 MCE banks
May  5 15:25:00 herbert-desktop kernel: [    0.020551] using C1E aware idle routine
May  5 15:25:00 herbert-desktop kernel: [    0.020553] Performance Events: AMD PMU driver.
May  5 15:25:00 herbert-desktop kernel: [    0.020558] ... version:                0
May  5 15:25:00 herbert-desktop kernel: [    0.020560] ... bit width:              48
May  5 15:25:00 herbert-desktop kernel: [    0.020561] ... generic registers:      4
May  5 15:25:00 herbert-desktop kernel: [    0.020563] ... value mask:             0000ffffffffffff
May  5 15:25:00 herbert-desktop kernel: [    0.020565] ... max period:             00007fffffffffff
May  5 15:25:00 herbert-desktop kernel: [    0.020567] ... fixed-purpose events:   0
May  5 15:25:00 herbert-desktop kernel: [    0.020569] ... event mask:             000000000000000f
May  5 15:25:00 herbert-desktop kernel: [    0.022335] ACPI: Core revision 20090903
May  5 15:25:00 herbert-desktop kernel: [    0.032302] ftrace: converting mcount calls to 0f 1f 44 00 00
May  5 15:25:00 herbert-desktop kernel: [    0.032307] ftrace: allocating 22518 entries in 89 pages
May  5 15:25:00 herbert-desktop kernel: [    0.040100] Setting APIC routing to flat
May  5 15:25:00 herbert-desktop kernel: [    0.040623] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
May  5 15:25:00 herbert-desktop kernel: [    0.060000] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
May  5 15:25:00 herbert-desktop kernel: [    0.060000] ...trying to set up timer (IRQ0) through the 8259A ...
May  5 15:25:00 herbert-desktop kernel: [    0.060000] ..... (found apic 0 pin 0) ...
May  5 15:25:00 herbert-desktop kernel: [    0.080000] ....... failed.
May  5 15:25:00 herbert-desktop kernel: [    0.080000] ...trying to set up timer as Virtual Wire IRQ...
May  5 15:25:00 herbert-desktop kernel: [    0.080000] ..... failed.
May  5 15:25:00 herbert-desktop kernel: [    0.080000] ...trying to set up timer as ExtINT IRQ...
May  5 15:25:00 herbert-desktop kernel: [    0.187914] ..... works.
May  5 15:25:00 herbert-desktop kernel: [    0.187916] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ stepping 02
May  5 15:25:00 herbert-desktop kernel: [    0.190000] Booting processor 1 APIC 0x1 ip 0x6000
May  5 15:25:00 herbert-desktop kernel: [    0.020000] Initializing CPU#1
May  5 15:25:00 herbert-desktop kernel: [    0.020000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
May  5 15:25:00 herbert-desktop kernel: [    0.020000] CPU: L2 Cache: 512K (64 bytes/line)
May  5 15:25:00 herbert-desktop kernel: [    0.020000] CPU 1/0x1 -> Node 0
May  5 15:25:00 herbert-desktop kernel: [    0.020000] CPU: Physical Processor ID: 0
May  5 15:25:00 herbert-desktop kernel: [    0.020000] CPU: Processor Core ID: 1
May  5 15:25:00 herbert-desktop kernel: [    0.340073] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ stepping 02
May  5 15:25:00 herbert-desktop kernel: [    0.340100] Brought up 2 CPUs
May  5 15:25:00 herbert-desktop kernel: [    0.340102] Total of 2 processors activated (8016.74 BogoMIPS).
May  5 15:25:00 herbert-desktop kernel: [    0.340320] CPU0 attaching sched-domain:
May  5 15:25:00 herbert-desktop kernel: [    0.340323]  domain 0: span 0-1 level MC
May  5 15:25:00 herbert-desktop kernel: [    0.340326]   groups: 0 1
May  5 15:25:00 herbert-desktop kernel: [    0.340331] CPU1 attaching sched-domain:
May  5 15:25:00 herbert-desktop kernel: [    0.340333]  domain 0: span 0-1 level MC
May  5 15:25:00 herbert-desktop kernel: [    0.340336]   groups: 1 0
May  5 15:25:00 herbert-desktop kernel: [    0.340424] devtmpfs: initialized
May  5 15:25:00 herbert-desktop kernel: [    0.340424] regulator: core version 0.5
May  5 15:25:00 herbert-desktop kernel: [    0.340424] Time: 22:24:49  Date: 05/05/10
May  5 15:25:00 herbert-desktop kernel: [    0.340424] NET: Registered protocol family 16
May  5 15:25:00 herbert-desktop kernel: [    0.340424] Trying to unpack rootfs image as initramfs...
May  5 15:25:00 herbert-desktop kernel: [    0.340424] node 0 link 0: io port [8000, ffff]
May  5 15:25:00 herbert-desktop kernel: [    0.340424] TOM: 00000000c0000000 aka 3072M
May  5 15:25:00 herbert-desktop kernel: [    0.340424] node 0 link 0: mmio [a0000, bffff]
May  5 15:25:00 herbert-desktop kernel: [    0.340424] node 0 link 0: mmio [c0000000, efffffff]
May  5 15:25:00 herbert-desktop kernel: [    0.340424] node 0 link 0: mmio [f4000000, fe02ffff]
May  5 15:25:00 herbert-desktop kernel: [    0.340424] node 0 link 0: mmio [f0000000, f04fffff]
May  5 15:25:00 herbert-desktop kernel: [    0.340424] TOM2: 0000000180000000 aka 6144M
May  5 15:25:00 herbert-desktop kernel: [    0.340424] bus: [00,04] on node 0 link 0
May  5 15:25:00 herbert-desktop kernel: [    0.340424] bus: 00 index 0 io port: [0, ffff]
May  5 15:25:00 herbert-desktop kernel: [    0.340424] bus: 00 index 1 mmio: [a0000, bffff]
May  5 15:25:00 herbert-desktop kernel: [    0.340424] bus: 00 index 2 mmio: [c0000000, f3ffffff]
May  5 15:25:00 herbert-desktop kernel: [    0.340424] bus: 00 index 3 mmio: [f4000000, ffffffff]
May  5 15:25:00 herbert-desktop kernel: [    0.340424] bus: 00 index 4 mmio: [180000000, fcffffffff]
May  5 15:25:00 herbert-desktop kernel: [    0.340424] ACPI: bus type pci registered
May  5 15:25:00 herbert-desktop kernel: [    0.340424] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
May  5 15:25:00 herbert-desktop kernel: [    0.340424] PCI: MCFG area at f0000000 reserved in E820
May  5 15:25:00 herbert-desktop kernel: [    0.343363] PCI: Using MMCONFIG at f0000000 - f3ffffff
May  5 15:25:00 herbert-desktop kernel: [    0.343365] PCI: Using configuration type 1 for base access
May  5 15:25:00 herbert-desktop kernel: [    0.350131] bio: create slab <bio-0> at 0
May  5 15:25:00 herbert-desktop kernel: [    0.351087] ACPI: EC: Look up EC in DSDT
May  5 15:25:00 herbert-desktop kernel: [    0.358308] ACPI: Interpreter enabled
May  5 15:25:00 herbert-desktop kernel: [    0.358313] ACPI: (supports S0 S1 S3 S4 S5)
May  5 15:25:00 herbert-desktop kernel: [    0.358341] ACPI: Using IOAPIC for interrupt routing
May  5 15:25:00 herbert-desktop kernel: [    0.367339] ACPI: No dock devices found.
May  5 15:25:00 herbert-desktop kernel: [    0.368385] ACPI: PCI Root Bridge [PCI0] (0000:00)
May  5 15:25:00 herbert-desktop kernel: [    0.368657] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
May  5 15:25:00 herbert-desktop kernel: [    0.368661] pci 0000:00:02.0: PME# disabled
May  5 15:25:00 herbert-desktop kernel: [    0.368696] pci 0000:00:03.0: PME# supported from D0 D1 D2 D3hot D3cold
May  5 15:25:00 herbert-desktop kernel: [    0.368699] pci 0000:00:03.0: PME# disabled
May  5 15:25:00 herbert-desktop kernel: [    0.368736] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
May  5 15:25:00 herbert-desktop kernel: [    0.368739] pci 0000:00:04.0: PME# disabled
May  5 15:25:00 herbert-desktop kernel: [    0.368758] pci 0000:00:05.0: reg 10 32bit mmio: [0xfc000000-0xfcffffff]
May  5 15:25:00 herbert-desktop kernel: [    0.368764] pci 0000:00:05.0: reg 14 64bit mmio pref: [0xe0000000-0xefffffff]
May  5 15:25:00 herbert-desktop kernel: [    0.368769] pci 0000:00:05.0: reg 1c 64bit mmio: [0xfb000000-0xfbffffff]
May  5 15:25:00 herbert-desktop kernel: [    0.368774] pci 0000:00:05.0: reg 30 32bit mmio pref: [0x000000-0x01ffff]
May  5 15:25:00 herbert-desktop kernel: [    0.369013] pci 0000:00:0a.1: reg 20 io port: [0x1c00-0x1c3f]
May  5 15:25:00 herbert-desktop kernel: [    0.369019] pci 0000:00:0a.1: reg 24 io port: [0x1c40-0x1c7f]
May  5 15:25:00 herbert-desktop kernel: [    0.369043] pci 0000:00:0a.1: PME# supported from D3hot D3cold
May  5 15:25:00 herbert-desktop kernel: [    0.369048] pci 0000:00:0a.1: PME# disabled
May  5 15:25:00 herbert-desktop kernel: [    0.369114] pci 0000:00:0b.0: reg 10 32bit mmio: [0xfe02f000-0xfe02ffff]
May  5 15:25:00 herbert-desktop kernel: [    0.369142] pci 0000:00:0b.0: supports D1 D2
May  5 15:25:00 herbert-desktop kernel: [    0.369144] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
May  5 15:25:00 herbert-desktop kernel: [    0.369148] pci 0000:00:0b.0: PME# disabled
May  5 15:25:00 herbert-desktop kernel: [    0.369175] pci 0000:00:0b.1: reg 10 32bit mmio: [0xfe02e000-0xfe02e0ff]
May  5 15:25:00 herbert-desktop kernel: [    0.369205] pci 0000:00:0b.1: supports D1 D2
May  5 15:25:00 herbert-desktop kernel: [    0.369207] pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot D3cold
May  5 15:25:00 herbert-desktop kernel: [    0.369210] pci 0000:00:0b.1: PME# disabled
May  5 15:25:00 herbert-desktop kernel: [    0.369251] pci 0000:00:0e.0: reg 10 io port: [0x9f0-0x9f7]
May  5 15:25:00 herbert-desktop kernel: [    0.369256] pci 0000:00:0e.0: reg 14 io port: [0xbf0-0xbf3]
May  5 15:25:00 herbert-desktop kernel: [    0.369261] pci 0000:00:0e.0: reg 18 io port: [0x970-0x977]
May  5 15:25:00 herbert-desktop kernel: [    0.369266] pci 0000:00:0e.0: reg 1c io port: [0xb70-0xb73]
May  5 15:25:00 herbert-desktop kernel: [    0.369270] pci 0000:00:0e.0: reg 20 io port: [0xe000-0xe00f]
May  5 15:25:00 herbert-desktop kernel: [    0.369275] pci 0000:00:0e.0: reg 24 32bit mmio: [0xfe02d000-0xfe02dfff]
May  5 15:25:00 herbert-desktop kernel: [    0.369322] pci 0000:00:0f.0: reg 10 io port: [0x9e0-0x9e7]
May  5 15:25:00 herbert-desktop kernel: [    0.369327] pci 0000:00:0f.0: reg 14 io port: [0xbe0-0xbe3]
May  5 15:25:00 herbert-desktop kernel: [    0.369331] pci 0000:00:0f.0: reg 18 io port: [0x960-0x967]
May  5 15:25:00 herbert-desktop kernel: [    0.369336] pci 0000:00:0f.0: reg 1c io port: [0xb60-0xb63]
May  5 15:25:00 herbert-desktop kernel: [    0.369341] pci 0000:00:0f.0: reg 20 io port: [0xcc00-0xcc0f]
May  5 15:25:00 herbert-desktop kernel: [    0.369346] pci 0000:00:0f.0: reg 24 32bit mmio: [0xfe02c000-0xfe02cfff]
May  5 15:25:00 herbert-desktop kernel: [    0.369433] pci 0000:00:10.1: reg 10 32bit mmio: [0xfe024000-0xfe027fff]
May  5 15:25:00 herbert-desktop kernel: [    0.369466] pci 0000:00:10.1: PME# supported from D3hot D3cold
May  5 15:25:00 herbert-desktop kernel: [    0.369470] pci 0000:00:10.1: PME# disabled
May  5 15:25:00 herbert-desktop kernel: [    0.369608] pci 0000:00:02.0: bridge io port: [0xa000-0xafff]
May  5 15:25:00 herbert-desktop kernel: [    0.369611] pci 0000:00:02.0: bridge 32bit mmio: [0xfd800000-0xfd8fffff]
May  5 15:25:00 herbert-desktop kernel: [    0.369616] pci 0000:00:02.0: bridge 64bit mmio pref: [0xfd700000-0xfd7fffff]
May  5 15:25:00 herbert-desktop kernel: [    0.369661] pci 0000:00:03.0: bridge io port: [0x8000-0x8fff]
May  5 15:25:00 herbert-desktop kernel: [    0.369664] pci 0000:00:03.0: bridge 32bit mmio: [0xfde00000-0xfdefffff]
May  5 15:25:00 herbert-desktop kernel: [    0.369668] pci 0000:00:03.0: bridge 64bit mmio pref: [0xfdd00000-0xfddfffff]
May  5 15:25:00 herbert-desktop kernel: [    0.369707] pci 0000:00:04.0: bridge io port: [0xb000-0xbfff]
May  5 15:25:00 herbert-desktop kernel: [    0.369710] pci 0000:00:04.0: bridge 32bit mmio: [0xfdc00000-0xfdcfffff]
May  5 15:25:00 herbert-desktop kernel: [    0.369714] pci 0000:00:04.0: bridge 64bit mmio pref: [0xfd900000-0xfd9fffff]
May  5 15:25:00 herbert-desktop kernel: [    0.369752] pci 0000:04:07.0: reg 10 32bit mmio: [0xfdbfe000-0xfdbfffff]
May  5 15:25:00 herbert-desktop kernel: [    0.369786] pci 0000:04:07.0: supports D1 D2
May  5 15:25:00 herbert-desktop kernel: [    0.369788] pci 0000:04:07.0: PME# supported from D0 D1 D2 D3hot D3cold
May  5 15:25:00 herbert-desktop kernel: [    0.369792] pci 0000:04:07.0: PME# disabled
May  5 15:25:00 herbert-desktop kernel: [    0.369819] pci 0000:04:08.0: reg 10 32bit mmio: [0xfdbe0000-0xfdbeffff]
May  5 15:25:00 herbert-desktop kernel: [    0.369825] pci 0000:04:08.0: reg 14 io port: [0x9c00-0x9c07]
May  5 15:25:00 herbert-desktop kernel: [    0.369856] pci 0000:04:08.0: PME# supported from D3hot D3cold
May  5 15:25:00 herbert-desktop kernel: [    0.369859] pci 0000:04:08.0: PME# disabled
May  5 15:25:00 herbert-desktop kernel: [    0.369889] pci 0000:00:10.0: transparent bridge
May  5 15:25:00 herbert-desktop kernel: [    0.369893] pci 0000:00:10.0: bridge io port: [0x9000-0x9fff]
May  5 15:25:00 herbert-desktop kernel: [    0.369896] pci 0000:00:10.0: bridge 32bit mmio: [0xfdb00000-0xfdbfffff]
May  5 15:25:00 herbert-desktop kernel: [    0.369900] pci 0000:00:10.0: bridge 32bit mmio pref: [0xfda00000-0xfdafffff]
May  5 15:25:00 herbert-desktop kernel: [    0.369914] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
May  5 15:25:00 herbert-desktop kernel: [    0.370192] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
May  5 15:25:00 herbert-desktop kernel: [    0.456554] ACPI: PCI Interrupt Link [LNK1] (IRQs *5 7 9 10 11 14 15)
May  5 15:25:00 herbert-desktop kernel: [    0.456723] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
May  5 15:25:00 herbert-desktop kernel: [    0.456894] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
May  5 15:25:00 herbert-desktop kernel: [    0.457069] ACPI: PCI Interrupt Link [LNK4] (IRQs *5 7 9 10 11 14 15)
May  5 15:25:00 herbert-desktop kernel: [    0.457236] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
May  5 15:25:00 herbert-desktop kernel: [    0.457405] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
May  5 15:25:00 herbert-desktop kernel: [    0.457574] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 *7 9 10 11 14 15)
May  5 15:25:00 herbert-desktop kernel: [    0.457742] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
May  5 15:25:00 herbert-desktop kernel: [    0.457911] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 10 11 14 *15)
May  5 15:25:00 herbert-desktop kernel: [    0.458079] ACPI: PCI Interrupt Link [LUBB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
May  5 15:25:00 herbert-desktop kernel: [    0.458248] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 *10 11 14 15)
May  5 15:25:00 herbert-desktop kernel: [    0.458416] ACPI: PCI Interrupt Link [LACI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
May  5 15:25:00 herbert-desktop kernel: [    0.458586] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 *11 14 15)
May  5 15:25:00 herbert-desktop kernel: [    0.458754] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 *7 9 10 11 14 15)
May  5 15:25:00 herbert-desktop kernel: [    0.458921] ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
May  5 15:25:00 herbert-desktop kernel: [    0.459091] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 *10 11 14 15)
May  5 15:25:00 herbert-desktop kernel: [    0.459260] ACPI: PCI Interrupt Link [LUB2] (IRQs *5 7 9 10 11 14 15)
May  5 15:25:00 herbert-desktop kernel: [    0.459428] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
May  5 15:25:00 herbert-desktop kernel: [    0.459599] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 *10 11 14 15)
May  5 15:25:00 herbert-desktop kernel: [    0.459768] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 10 *11 14 15)
May  5 15:25:00 herbert-desktop kernel: [    0.460012] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0
May  5 15:25:00 herbert-desktop kernel: [    0.460228] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
May  5 15:25:00 herbert-desktop kernel: [    0.460445] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
May  5 15:25:00 herbert-desktop kernel: [    0.460660] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0
May  5 15:25:00 herbert-desktop kernel: [    0.460873] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
May  5 15:25:00 herbert-desktop kernel: [    0.461089] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
May  5 15:25:00 herbert-desktop kernel: [    0.461305] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0
May  5 15:25:00 herbert-desktop kernel: [    0.461520] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
May  5 15:25:00 herbert-desktop kernel: [    0.461736] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
May  5 15:25:00 herbert-desktop kernel: [    0.461957] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
May  5 15:25:00 herbert-desktop kernel: [    0.462173] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
May  5 15:25:00 herbert-desktop kernel: [    0.462387] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
May  5 15:25:00 herbert-desktop kernel: [    0.462605] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0
May  5 15:25:00 herbert-desktop kernel: [    0.462820] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
May  5 15:25:00 herbert-desktop kernel: [    0.463037] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
May  5 15:25:00 herbert-desktop kernel: [    0.463254] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
May  5 15:25:00 herbert-desktop kernel: [    0.463471] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
May  5 15:25:00 herbert-desktop kernel: [    0.463687] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
May  5 15:25:00 herbert-desktop kernel: [    0.463905] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
May  5 15:25:00 herbert-desktop kernel: [    0.464120] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
May  5 15:25:00 herbert-desktop kernel: [    0.464336] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0
May  5 15:25:00 herbert-desktop kernel: [    0.464473] vgaarb: device added: PCI:0000:00:05.0,decodes=io+mem,owns=io+mem,locks=none
May  5 15:25:00 herbert-desktop kernel: [    0.464485] vgaarb: loaded
May  5 15:25:00 herbert-desktop kernel: [    0.464612] SCSI subsystem initialized
May  5 15:25:00 herbert-desktop kernel: [    0.464725] libata version 3.00 loaded.
May  5 15:25:00 herbert-desktop kernel: [    0.464801] usbcore: registered new interface driver usbfs
May  5 15:25:00 herbert-desktop kernel: [    0.464813] usbcore: registered new interface driver hub
May  5 15:25:00 herbert-desktop kernel: [    0.464840] usbcore: registered new device driver usb
May  5 15:25:00 herbert-desktop kernel: [    0.465006] ACPI: WMI: Mapper loaded
May  5 15:25:00 herbert-desktop kernel: [    0.465008] PCI: Using ACPI for IRQ routing
May  5 15:25:00 herbert-desktop kernel: [    0.465188] NetLabel: Initializing
May  5 15:25:00 herbert-desktop kernel: [    0.465190] NetLabel:  domain hash size = 128
May  5 15:25:00 herbert-desktop kernel: [    0.465192] NetLabel:  protocols = UNLABELED CIPSOv4
May  5 15:25:00 herbert-desktop kernel: [    0.465210] NetLabel:  unlabeled traffic allowed by default
May  5 15:25:00 herbert-desktop kernel: [    0.465250] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
May  5 15:25:00 herbert-desktop kernel: [    0.465255] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
May  5 15:25:00 herbert-desktop kernel: [    0.470168] Switching to clocksource hpet
May  5 15:25:00 herbert-desktop kernel: [    0.471789] AppArmor: AppArmor Filesystem Enabled
May  5 15:25:00 herbert-desktop kernel: [    0.471813] pnp: PnP ACPI init
May  5 15:25:00 herbert-desktop kernel: [    0.471836] ACPI: bus type pnp registered
May  5 15:25:00 herbert-desktop kernel: [    0.476680] pnp: PnP ACPI: found 9 devices
May  5 15:25:00 herbert-desktop kernel: [    0.476683] ACPI: ACPI bus type pnp unregistered
May  5 15:25:00 herbert-desktop kernel: [    0.476696] system 00:01: ioport range 0x1000-0x107f has been reserved
May  5 15:25:00 herbert-desktop kernel: [    0.476699] system 00:01: ioport range 0x1080-0x10ff has been reserved
May  5 15:25:00 herbert-desktop kernel: [    0.476702] system 00:01: ioport range 0x1400-0x147f has been reserved
May  5 15:25:00 herbert-desktop kernel: [    0.476705] system 00:01: ioport range 0x1480-0x14ff has been reserved
May  5 15:25:00 herbert-desktop kernel: [    0.476708] system 00:01: ioport range 0x1800-0x187f has been reserved
May  5 15:25:00 herbert-desktop kernel: [    0.476711] system 00:01: ioport range 0x1880-0x18ff has been reserved
May  5 15:25:00 herbert-desktop kernel: [    0.476714] system 00:01: ioport range 0x2000-0x207f has been reserved
May  5 15:25:00 herbert-desktop kernel: [    0.476718] system 00:01: ioport range 0x2080-0x20ff has been reserved
May  5 15:25:00 herbert-desktop kernel: [    0.476722] system 00:01: iomem range 0xfec80000-0xfecbffff has been reserved
May  5 15:25:00 herbert-desktop kernel: [    0.476725] system 00:01: iomem range 0xfefe0000-0xfefe01ff has been reserved
May  5 15:25:00 herbert-desktop kernel: [    0.476728] system 00:01: iomem range 0xb8000000-0xbfffffff has been reserved
May  5 15:25:00 herbert-desktop kernel: [    0.476734] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
May  5 15:25:00 herbert-desktop kernel: [    0.476737] system 00:02: ioport range 0x800-0x87f has been reserved
May  5 15:25:00 herbert-desktop kernel: [    0.476744] system 00:07: iomem range 0xf0000000-0xf3ffffff has been reserved
May  5 15:25:00 herbert-desktop kernel: [    0.476750] system 00:08: iomem range 0xcec00-0xcffff has been reserved
May  5 15:25:00 herbert-desktop kernel: [    0.476753] system 00:08: iomem range 0xf0000-0xf7fff could not be reserved
May  5 15:25:00 herbert-desktop kernel: [    0.476756] system 00:08: iomem range 0xf8000-0xfbfff could not be reserved
May  5 15:25:00 herbert-desktop kernel: [    0.476759] system 00:08: iomem range 0xfc000-0xfffff could not be reserved
May  5 15:25:00 herbert-desktop kernel: [    0.476762] system 00:08: iomem range 0xb7ee0000-0xb7efffff could not be reserved
May  5 15:25:00 herbert-desktop kernel: [    0.476765] system 00:08: iomem range 0xffff0000-0xffffffff has been reserved
May  5 15:25:00 herbert-desktop kernel: [    0.476768] system 00:08: iomem range 0x0-0x9ffff could not be reserved
May  5 15:25:00 herbert-desktop kernel: [    0.476771] system 00:08: iomem range 0x100000-0xb7edffff could not be reserved
May  5 15:25:00 herbert-desktop kernel: [    0.476774] system 00:08: iomem range 0xb7f00000-0xbfefffff could not be reserved
May  5 15:25:00 herbert-desktop kernel: [    0.476778] system 00:08: iomem range 0xfec00000-0xfec00fff could not be reserved
May  5 15:25:00 herbert-desktop kernel: [    0.476781] system 00:08: iomem range 0xfee00000-0xfeefffff has been reserved
May  5 15:25:00 herbert-desktop kernel: [    0.476784] system 00:08: iomem range 0xfefff000-0xfeffffff has been reserved
May  5 15:25:00 herbert-desktop kernel: [    0.476788] system 00:08: iomem range 0xfff80000-0xfff80fff has been reserved
May  5 15:25:00 herbert-desktop kernel: [    0.476791] system 00:08: iomem range 0xfff90000-0xfffbffff has been reserved
May  5 15:25:00 herbert-desktop kernel: [    0.476794] system 00:08: iomem range 0xfffed000-0xfffeffff has been reserved
May  5 15:25:00 herbert-desktop kernel: [    0.481565] pci 0000:00:02.0: PCI bridge, secondary bus 0000:01
May  5 15:25:00 herbert-desktop kernel: [    0.481568] pci 0000:00:02.0:   IO window: 0xa000-0xafff
May  5 15:25:00 herbert-desktop kernel: [    0.481571] pci 0000:00:02.0:   MEM window: 0xfd800000-0xfd8fffff
May  5 15:25:00 herbert-desktop kernel: [    0.481575] pci 0000:00:02.0:   PREFETCH window: 0x000000fd700000-0x000000fd7fffff
May  5 15:25:00 herbert-desktop kernel: [    0.481579] pci 0000:00:03.0: PCI bridge, secondary bus 0000:02
May  5 15:25:00 herbert-desktop kernel: [    0.481581] pci 0000:00:03.0:   IO window: 0x8000-0x8fff
May  5 15:25:00 herbert-desktop kernel: [    0.481584] pci 0000:00:03.0:   MEM window: 0xfde00000-0xfdefffff
May  5 15:25:00 herbert-desktop kernel: [    0.481588] pci 0000:00:03.0:   PREFETCH window: 0x000000fdd00000-0x000000fddfffff
May  5 15:25:00 herbert-desktop kernel: [    0.481591] pci 0000:00:04.0: PCI bridge, secondary bus 0000:03
May  5 15:25:00 herbert-desktop kernel: [    0.481594] pci 0000:00:04.0:   IO window: 0xb000-0xbfff
May  5 15:25:00 herbert-desktop kernel: [    0.481597] pci 0000:00:04.0:   MEM window: 0xfdc00000-0xfdcfffff
May  5 15:25:00 herbert-desktop kernel: [    0.481600] pci 0000:00:04.0:   PREFETCH window: 0x000000fd900000-0x000000fd9fffff
May  5 15:25:00 herbert-desktop kernel: [    0.481605] pci 0000:00:10.0: PCI bridge, secondary bus 0000:04
May  5 15:25:00 herbert-desktop kernel: [    0.481607] pci 0000:00:10.0:   IO window: 0x9000-0x9fff
May  5 15:25:00 herbert-desktop kernel: [    0.481611] pci 0000:00:10.0:   MEM window: 0xfdb00000-0xfdbfffff
May  5 15:25:00 herbert-desktop kernel: [    0.481615] pci 0000:00:10.0:   PREFETCH window: 0xfda00000-0xfdafffff
May  5 15:25:00 herbert-desktop kernel: [    0.481626] pci 0000:00:02.0: setting latency timer to 64
May  5 15:25:00 herbert-desktop kernel: [    0.481631] pci 0000:00:03.0: setting latency timer to 64
May  5 15:25:00 herbert-desktop kernel: [    0.481636] pci 0000:00:04.0: setting latency timer to 64
May  5 15:25:00 herbert-desktop kernel: [    0.481641] pci 0000:00:10.0: setting latency timer to 64
May  5 15:25:00 herbert-desktop kernel: [    0.481646] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
May  5 15:25:00 herbert-desktop kernel: [    0.481649] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
May  5 15:25:00 herbert-desktop kernel: [    0.481651] pci_bus 0000:01: resource 0 io:  [0xa000-0xafff]
May  5 15:25:00 herbert-desktop kernel: [    0.481654] pci_bus 0000:01: resource 1 mem: [0xfd800000-0xfd8fffff]
May  5 15:25:00 herbert-desktop kernel: [    0.481657] pci_bus 0000:01: resource 2 pref mem [0xfd700000-0xfd7fffff]
May  5 15:25:00 herbert-desktop kernel: [    0.481660] pci_bus 0000:02: resource 0 io:  [0x8000-0x8fff]
May  5 15:25:00 herbert-desktop kernel: [    0.481662] pci_bus 0000:02: resource 1 mem: [0xfde00000-0xfdefffff]
May  5 15:25:00 herbert-desktop kernel: [    0.481665] pci_bus 0000:02: resource 2 pref mem [0xfdd00000-0xfddfffff]
May  5 15:25:00 herbert-desktop kernel: [    0.481667] pci_bus 0000:03: resource 0 io:  [0xb000-0xbfff]
May  5 15:25:00 herbert-desktop kernel: [    0.481670] pci_bus 0000:03: resource 1 mem: [0xfdc00000-0xfdcfffff]
May  5 15:25:00 herbert-desktop kernel: [    0.481673] pci_bus 0000:03: resource 2 pref mem [0xfd900000-0xfd9fffff]
May  5 15:25:00 herbert-desktop kernel: [    0.481675] pci_bus 0000:04: resource 0 io:  [0x9000-0x9fff]
May  5 15:25:00 herbert-desktop kernel: [    0.481678] pci_bus 0000:04: resource 1 mem: [0xfdb00000-0xfdbfffff]
May  5 15:25:00 herbert-desktop kernel: [    0.481681] pci_bus 0000:04: resource 2 pref mem [0xfda00000-0xfdafffff]
May  5 15:25:00 herbert-desktop kernel: [    0.481683] pci_bus 0000:04: resource 3 io:  [0x00-0xffff]
May  5 15:25:00 herbert-desktop kernel: [    0.481686] pci_bus 0000:04: resource 4 mem: [0x000000-0xffffffffffffffff]
May  5 15:25:00 herbert-desktop kernel: [    0.481728] NET: Registered protocol family 2
May  5 15:25:00 herbert-desktop kernel: [    0.482029] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
May  5 15:25:00 herbert-desktop kernel: [    0.484763] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
May  5 15:25:00 herbert-desktop kernel: [    0.490619] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
May  5 15:25:00 herbert-desktop kernel: [    0.491308] TCP: Hash tables configured (established 524288 bind 65536)
May  5 15:25:00 herbert-desktop kernel: [    0.491311] TCP reno registered
May  5 15:25:00 herbert-desktop kernel: [    0.491423] NET: Registered protocol family 1
May  5 15:25:00 herbert-desktop kernel: [    0.491455] pci 0000:00:00.0: Found disabled HT MSI Mapping
May  5 15:25:00 herbert-desktop kernel: [    0.491460] pci 0000:00:00.0: Enabling HT MSI Mapping
May  5 15:25:00 herbert-desktop kernel: [    0.491498] pci 0000:00:00.0: Found enabled HT MSI Mapping
May  5 15:25:00 herbert-desktop kernel: [    0.491520] pci 0000:00:00.0: Found enabled HT MSI Mapping
May  5 15:25:00 herbert-desktop kernel: [    0.491547] pci 0000:00:00.0: Found enabled HT MSI Mapping
May  5 15:25:00 herbert-desktop kernel: [    0.491553] pci 0000:00:05.0: Boot video device
May  5 15:25:00 herbert-desktop kernel: [    0.510101] pci 0000:00:09.0: Found disabled HT MSI Mapping
May  5 15:25:00 herbert-desktop kernel: [    0.510108] pci 0000:00:0e.0: Enabling HT MSI Mapping
May  5 15:25:00 herbert-desktop kernel: [    0.510162] pci 0000:00:09.0: Found disabled HT MSI Mapping
May  5 15:25:00 herbert-desktop kernel: [    0.510170] pci 0000:00:0f.0: Enabling HT MSI Mapping
May  5 15:25:00 herbert-desktop kernel: [    0.510226] pci 0000:00:09.0: Found disabled HT MSI Mapping
May  5 15:25:00 herbert-desktop kernel: [    0.510232] pci 0000:00:10.0: Enabling HT MSI Mapping
May  5 15:25:00 herbert-desktop kernel: [    0.510290] pci 0000:00:09.0: Found disabled HT MSI Mapping
May  5 15:25:00 herbert-desktop kernel: [    0.510298] pci 0000:00:10.1: Enabling HT MSI Mapping
May  5 15:25:00 herbert-desktop kernel: [    0.510479] PCI-DMA: Disabling AGP.
May  5 15:25:00 herbert-desktop kernel: [    0.510581] PCI-DMA: aperture base @ 20000000 size 65536 KB
May  5 15:25:00 herbert-desktop kernel: [    0.510583] PCI-DMA: using GART IOMMU.
May  5 15:25:00 herbert-desktop kernel: [    0.510587] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
May  5 15:25:00 herbert-desktop kernel: [    0.511265] Simple Boot Flag at 0x3a set to 0x80
May  5 15:25:00 herbert-desktop kernel: [    0.511477] Scanning for low memory corruption every 60 seconds
May  5 15:25:00 herbert-desktop kernel: [    0.511649] audit: initializing netlink socket (disabled)
May  5 15:25:00 herbert-desktop kernel: [    0.511662] type=2000 audit(1273098288.510:1): initialized
May  5 15:25:00 herbert-desktop kernel: [    0.521345] HugeTLB registered 2 MB page size, pre-allocated 0 pages
May  5 15:25:00 herbert-desktop kernel: [    0.522781] VFS: Disk quotas dquot_6.5.2
May  5 15:25:00 herbert-desktop kernel: [    0.522844] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
May  5 15:25:00 herbert-desktop kernel: [    0.523512] fuse init (API version 7.13)
May  5 15:25:00 herbert-desktop kernel: [    0.523601] msgmni has been set to 9675
May  5 15:25:00 herbert-desktop kernel: [    0.523849] alg: No test for stdrng (krng)
May  5 15:25:00 herbert-desktop kernel: [    0.523906] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
May  5 15:25:00 herbert-desktop kernel: [    0.523910] io scheduler noop registered
May  5 15:25:00 herbert-desktop kernel: [    0.523912] io scheduler anticipatory registered
May  5 15:25:00 herbert-desktop kernel: [    0.523914] io scheduler deadline registered
May  5 15:25:00 herbert-desktop kernel: [    0.523952] io scheduler cfq registered (default)
May  5 15:25:00 herbert-desktop kernel: [    0.524134]   alloc irq_desc for 24 on node 0
May  5 15:25:00 herbert-desktop kernel: [    0.524137]   alloc kstat_irqs on node 0
May  5 15:25:00 herbert-desktop kernel: [    0.524147] pcieport 0000:00:02.0: irq 24 for MSI/MSI-X
May  5 15:25:00 herbert-desktop kernel: [    0.524152] pcieport 0000:00:02.0: setting latency timer to 64
May  5 15:25:00 herbert-desktop kernel: [    0.524255]   alloc irq_desc for 25 on node 0
May  5 15:25:00 herbert-desktop kernel: [    0.524257]   alloc kstat_irqs on node 0
May  5 15:25:00 herbert-desktop kernel: [    0.524261] pcieport 0000:00:03.0: irq 25 for MSI/MSI-X
May  5 15:25:00 herbert-desktop kernel: [    0.524265] pcieport 0000:00:03.0: setting latency timer to 64
May  5 15:25:00 herbert-desktop kernel: [    0.524358]   alloc irq_desc for 26 on node 0
May  5 15:25:00 herbert-desktop kernel: [    0.524360]   alloc kstat_irqs on node 0
May  5 15:25:00 herbert-desktop kernel: [    0.524365] pcieport 0000:00:04.0: irq 26 for MSI/MSI-X
May  5 15:25:00 herbert-desktop kernel: [    0.524369] pcieport 0000:00:04.0: setting latency timer to 64
May  5 15:25:00 herbert-desktop kernel: [    0.524430] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
May  5 15:25:00 herbert-desktop kernel: [    0.524457] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
May  5 15:25:00 herbert-desktop kernel: [    0.524576] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
May  5 15:25:00 herbert-desktop kernel: [    0.524580] ACPI: Power Button [PWRB]
May  5 15:25:00 herbert-desktop kernel: [    0.524646] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
May  5 15:25:00 herbert-desktop kernel: [    0.524649] ACPI: Power Button [PWRF]
May  5 15:25:00 herbert-desktop kernel: [    0.525231] processor LNXCPU:00: registered as cooling_device0
May  5 15:25:00 herbert-desktop kernel: [    0.525272] processor LNXCPU:01: registered as cooling_device1
May  5 15:25:00 herbert-desktop kernel: [    0.530621] Linux agpgart interface v0.103
May  5 15:25:00 herbert-desktop kernel: [    0.530661] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
May  5 15:25:00 herbert-desktop kernel: [    0.531841] brd: module loaded
May  5 15:25:00 herbert-desktop kernel: [    0.532295] loop: module loaded
May  5 15:25:00 herbert-desktop kernel: [    0.532401] input: Macintosh mouse button emulation as /devices/virtual/input/input2
May  5 15:25:00 herbert-desktop kernel: [    0.533064] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
May  5 15:25:00 herbert-desktop kernel: [    0.533070]   alloc irq_desc for 23 on node 0
May  5 15:25:00 herbert-desktop kernel: [    0.533072]   alloc kstat_irqs on node 0
May  5 15:25:00 herbert-desktop kernel: [    0.533084] pata_acpi 0000:00:0e.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
May  5 15:25:00 herbert-desktop kernel: [    0.533124] pata_acpi 0000:00:0e.0: setting latency timer to 64
May  5 15:25:00 herbert-desktop kernel: [    0.533140] pata_acpi 0000:00:0e.0: PCI INT A disabled
May  5 15:25:00 herbert-desktop kernel: [    0.533536] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 22
May  5 15:25:00 herbert-desktop kernel: [    0.533539]   alloc irq_desc for 22 on node 0
May  5 15:25:00 herbert-desktop kernel: [    0.533541]   alloc kstat_irqs on node 0
May  5 15:25:00 herbert-desktop kernel: [    0.533549] pata_acpi 0000:00:0f.0: PCI INT A -> Link[APSJ] -> GSI 22 (level, low) -> IRQ 22
May  5 15:25:00 herbert-desktop kernel: [    0.533572] pata_acpi 0000:00:0f.0: setting latency timer to 64
May  5 15:25:00 herbert-desktop kernel: [    0.533581] pata_acpi 0000:00:0f.0: PCI INT A disabled
May  5 15:25:00 herbert-desktop kernel: [    0.533974] Fixed MDIO Bus: probed
May  5 15:25:00 herbert-desktop kernel: [    0.534008] PPP generic driver version 2.4.2
May  5 15:25:00 herbert-desktop kernel: [    0.534058] tun: Universal TUN/TAP device driver, 1.6
May  5 15:25:00 herbert-desktop kernel: [    0.534060] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
May  5 15:25:00 herbert-desktop kernel: [    0.534153] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
May  5 15:25:00 herbert-desktop kernel: [    0.534551] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 21
May  5 15:25:00 herbert-desktop kernel: [    0.534554]   alloc irq_desc for 21 on node 0
May  5 15:25:00 herbert-desktop kernel: [    0.534556]   alloc kstat_irqs on node 0
May  5 15:25:00 herbert-desktop kernel: [    0.534565] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[APCL] -> GSI 21 (level, low) -> IRQ 21
May  5 15:25:00 herbert-desktop kernel: [    0.534588] ehci_hcd 0000:00:0b.1: setting latency timer to 64
May  5 15:25:00 herbert-desktop kernel: [    0.534592] ehci_hcd 0000:00:0b.1: EHCI Host Controller
May  5 15:25:00 herbert-desktop kernel: [    0.534628] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
May  5 15:25:00 herbert-desktop kernel: [    0.534662] ehci_hcd 0000:00:0b.1: debug port 1
May  5 15:25:00 herbert-desktop kernel: [    0.534670] ehci_hcd 0000:00:0b.1: cache line size of 64 is not supported
May  5 15:25:00 herbert-desktop kernel: [    0.534695] ehci_hcd 0000:00:0b.1: irq 21, io mem 0xfe02e000
May  5 15:25:00 herbert-desktop kernel: [    0.550023] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00
May  5 15:25:00 herbert-desktop kernel: [    0.550111] usb usb1: configuration #1 chosen from 1 choice
May  5 15:25:00 herbert-desktop kernel: [    0.550145] hub 1-0:1.0: USB hub found
May  5 15:25:00 herbert-desktop kernel: [    0.550154] hub 1-0:1.0: 8 ports detected
May  5 15:25:00 herbert-desktop kernel: [    0.550225] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
May  5 15:25:00 herbert-desktop kernel: [    0.550648] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 20
May  5 15:25:00 herbert-desktop kernel: [    0.550652]   alloc irq_desc for 20 on node 0
May  5 15:25:00 herbert-desktop kernel: [    0.550654]   alloc kstat_irqs on node 0
May  5 15:25:00 herbert-desktop kernel: [    0.550664] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[APCF] -> GSI 20 (level, low) -> IRQ 20
May  5 15:25:00 herbert-desktop kernel: [    0.550681] ohci_hcd 0000:00:0b.0: setting latency timer to 64
May  5 15:25:00 herbert-desktop kernel: [    0.550684] ohci_hcd 0000:00:0b.0: OHCI Host Controller
May  5 15:25:00 herbert-desktop kernel: [    0.550724] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
May  5 15:25:00 herbert-desktop kernel: [    0.550753] ohci_hcd 0000:00:0b.0: irq 20, io mem 0xfe02f000
May  5 15:25:00 herbert-desktop kernel: [    0.559134] Freeing initrd memory: 8133k freed
May  5 15:25:00 herbert-desktop kernel: [    0.612098] usb usb2: configuration #1 chosen from 1 choice
May  5 15:25:00 herbert-desktop kernel: [    0.612129] hub 2-0:1.0: USB hub found
May  5 15:25:00 herbert-desktop kernel: [    0.612139] hub 2-0:1.0: 8 ports detected
May  5 15:25:00 herbert-desktop kernel: [    0.612205] uhci_hcd: USB Universal Host Controller Interface driver
May  5 15:25:00 herbert-desktop kernel: [    0.612304] PNP: No PS/2 controller found. Probing ports directly.
May  5 15:25:00 herbert-desktop kernel: [    0.615000] serio: i8042 KBD port at 0x60,0x64 irq 1
May  5 15:25:00 herbert-desktop kernel: [    0.615006] serio: i8042 AUX port at 0x60,0x64 irq 12
May  5 15:25:00 herbert-desktop kernel: [    0.615133] mice: PS/2 mouse device common for all mice
May  5 15:25:00 herbert-desktop kernel: [    0.615251] rtc_cmos 00:04: RTC can wake from S4
May  5 15:25:00 herbert-desktop kernel: [    0.615299] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
May  5 15:25:00 herbert-desktop kernel: [    0.615336] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
May  5 15:25:00 herbert-desktop kernel: [    0.615478] device-mapper: uevent: version 1.0.3
May  5 15:25:00 herbert-desktop kernel: [    0.615614] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
May  5 15:25:00 herbert-desktop kernel: [    0.615714] device-mapper: multipath: version 1.1.0 loaded
May  5 15:25:00 herbert-desktop kernel: [    0.615718] device-mapper: multipath round-robin: version 1.0.0 loaded
May  5 15:25:00 herbert-desktop kernel: [    0.615936] cpuidle: using governor ladder
May  5 15:25:00 herbert-desktop kernel: [    0.615938] cpuidle: using governor menu
May  5 15:25:00 herbert-desktop kernel: [    0.616332] TCP cubic registered
May  5 15:25:00 herbert-desktop kernel: [    0.616464] NET: Registered protocol family 10
May  5 15:25:00 herbert-desktop kernel: [    0.616977] lo: Disabled Privacy Extensions
May  5 15:25:00 herbert-desktop kernel: [    0.617312] NET: Registered protocol family 17
May  5 15:25:00 herbert-desktop kernel: [    0.617353] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ processors (2 cpu cores) (version 2.20.00)
May  5 15:25:00 herbert-desktop kernel: [    0.617406] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0xc
May  5 15:25:00 herbert-desktop kernel: [    0.617409] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0xe
May  5 15:25:00 herbert-desktop kernel: [    0.617411] powernow-k8:    2 : fid 0x2 (1000 MHz), vid 0x12
May  5 15:25:00 herbert-desktop kernel: [    0.617550] PM: Resume from disk failed.
May  5 15:25:00 herbert-desktop kernel: [    0.617562] registered taskstats version 1
May  5 15:25:00 herbert-desktop kernel: [    0.617905]   Magic number: 10:78:451
May  5 15:25:00 herbert-desktop kernel: [    0.618013] rtc_cmos 00:04: setting system clock to 2010-05-05 22:24:50 UTC (1273098290)
May  5 15:25:00 herbert-desktop kernel: [    0.618016] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
May  5 15:25:00 herbert-desktop kernel: [    0.618018] EDD information not available.
May  5 15:25:00 herbert-desktop kernel: [    0.618088] Freeing unused kernel memory: 876k freed
May  5 15:25:00 herbert-desktop kernel: [    0.618503] Write protecting the kernel read-only data: 7680k
May  5 15:25:00 herbert-desktop kernel: [    0.639215] udev: starting version 151
May  5 15:25:00 herbert-desktop kernel: [    0.762071] sata_nv 0000:00:0e.0: version 3.5
May  5 15:25:00 herbert-desktop kernel: [    0.762088] sata_nv 0000:00:0e.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
May  5 15:25:00 herbert-desktop kernel: [    0.762091] sata_nv 0000:00:0e.0: Using SWNCQ mode
May  5 15:25:00 herbert-desktop kernel: [    0.762166] sata_nv 0000:00:0e.0: setting latency timer to 64
May  5 15:25:00 herbert-desktop kernel: [    0.765792] scsi0 : sata_nv
May  5 15:25:00 herbert-desktop kernel: [    0.767573] scsi1 : sata_nv
May  5 15:25:00 herbert-desktop kernel: [    0.767850] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xe000 irq 23
May  5 15:25:00 herbert-desktop kernel: [    0.767853] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xe008 irq 23
May  5 15:25:00 herbert-desktop kernel: [    0.772858] sata_nv 0000:00:0f.0: PCI INT A -> Link[APSJ] -> GSI 22 (level, low) -> IRQ 22
May  5 15:25:00 herbert-desktop kernel: [    0.772863] sata_nv 0000:00:0f.0: Using SWNCQ mode
May  5 15:25:00 herbert-desktop kernel: [    0.772943] sata_nv 0000:00:0f.0: setting latency timer to 64
May  5 15:25:00 herbert-desktop kernel: [    0.774504] scsi2 : sata_nv
May  5 15:25:00 herbert-desktop kernel: [    0.774646] scsi3 : sata_nv
May  5 15:25:00 herbert-desktop kernel: [    0.774880] ata3: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xcc00 irq 22
May  5 15:25:00 herbert-desktop kernel: [    0.774884] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xcc08 irq 22
May  5 15:25:00 herbert-desktop kernel: [    0.870024] usb 1-4: new high speed USB device using ehci_hcd and address 2
May  5 15:25:00 herbert-desktop kernel: [    1.037580] usb 1-4: configuration #1 chosen from 1 choice
May  5 15:25:00 herbert-desktop kernel: [    1.250049] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
May  5 15:25:00 herbert-desktop kernel: [    1.260040] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
May  5 15:25:00 herbert-desktop kernel: [    1.270591] ata1.00: ATA-8: ST3500418AS, CC38, max UDMA/133
May  5 15:25:00 herbert-desktop kernel: [    1.270594] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
May  5 15:25:00 herbert-desktop kernel: [    1.307243] ata3.00: ATA-7: MAXTOR STM3500630AS, 3.AAE, max UDMA/133
May  5 15:25:00 herbert-desktop kernel: [    1.307246] ata3.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
May  5 15:25:00 herbert-desktop kernel: [    1.310447] ata1.00: configured for UDMA/133
May  5 15:25:00 herbert-desktop kernel: [    1.310568] scsi 0:0:0:0: Direct-Access     ATA      ST3500418AS      CC38 PQ: 0 ANSI: 5
May  5 15:25:00 herbert-desktop kernel: [    1.310764] sd 0:0:0:0: Attached scsi generic sg0 type 0
May  5 15:25:00 herbert-desktop kernel: [    1.310845] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
May  5 15:25:00 herbert-desktop kernel: [    1.310891] sd 0:0:0:0: [sda] Write Protect is off
May  5 15:25:00 herbert-desktop kernel: [    1.310895] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
May  5 15:25:00 herbert-desktop kernel: [    1.310917] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  5 15:25:00 herbert-desktop kernel: [    1.311077]  sda: sda1 sda2 < sda5 >
May  5 15:25:00 herbert-desktop kernel: [    1.354422] sd 0:0:0:0: [sda] Attached SCSI disk
May  5 15:25:00 herbert-desktop kernel: [    1.390558] ata3.00: configured for UDMA/133
May  5 15:25:00 herbert-desktop kernel: [    1.480022] usb 2-5: new low speed USB device using ohci_hcd and address 2
May  5 15:25:00 herbert-desktop kernel: [    1.708136] usb 2-5: configuration #1 chosen from 1 choice
May  5 15:25:00 herbert-desktop kernel: [    1.800050] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
May  5 15:25:00 herbert-desktop kernel: [    1.820182] ata2.00: ATAPI: TSSTcorp CD-RW/DVD-ROM TS-H493A, D200, max UDMA/33
May  5 15:25:00 herbert-desktop kernel: [    1.860196] ata2.00: configured for UDMA/33
May  5 15:25:00 herbert-desktop kernel: [    1.861121] scsi 1:0:0:0: CD-ROM            TSSTcorp CDRWDVD TS-H493A D200 PQ: 0 ANSI: 5
May  5 15:25:00 herbert-desktop kernel: [    1.864345] sr0: scsi3-mmc drive: 8x/48x writer cd/rw xa/form2 cdda tray
May  5 15:25:00 herbert-desktop kernel: [    1.864349] Uniform CD-ROM driver Revision: 3.20
May  5 15:25:00 herbert-desktop kernel: [    1.864473] sr 1:0:0:0: Attached scsi CD-ROM sr0
May  5 15:25:00 herbert-desktop kernel: [    1.864538] sr 1:0:0:0: Attached scsi generic sg1 type 5
May  5 15:25:00 herbert-desktop kernel: [    1.864657] scsi 2:0:0:0: Direct-Access     ATA      MAXTOR STM350063 3.AA PQ: 0 ANSI: 5
May  5 15:25:00 herbert-desktop kernel: [    1.864780] sd 2:0:0:0: Attached scsi generic sg2 type 0
May  5 15:25:00 herbert-desktop kernel: [    1.864792] sd 2:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
May  5 15:25:00 herbert-desktop kernel: [    1.864842] sd 2:0:0:0: [sdb] Write Protect is off
May  5 15:25:00 herbert-desktop kernel: [    1.864845] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
May  5 15:25:00 herbert-desktop kernel: [    1.864870] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  5 15:25:00 herbert-desktop kernel: [    1.865161]  sdb: sdb1
May  5 15:25:00 herbert-desktop kernel: [    1.880319] sd 2:0:0:0: [sdb] Attached SCSI disk
May  5 15:25:00 herbert-desktop kernel: [    2.050033] usb 2-6: new low speed USB device using ohci_hcd and address 3
May  5 15:25:00 herbert-desktop kernel: [    2.200560] ata4: SATA link down (SStatus 0 SControl 300)
May  5 15:25:00 herbert-desktop kernel: [    2.205058] usbcore: registered new interface driver hiddev
May  5 15:25:00 herbert-desktop kernel: [    2.212451] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:0b.0/usb2/2-5/2-5:1.0/input/input3
May  5 15:25:00 herbert-desktop kernel: [    2.212547] generic-usb 0003:413C:2003.0001: input,hidraw0: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:0b.0-5/input0
May  5 15:25:00 herbert-desktop kernel: [    2.212577] usbcore: registered new interface driver usbhid
May  5 15:25:00 herbert-desktop kernel: [    2.212580] usbhid: v2.6:USB HID core driver
May  5 15:25:00 herbert-desktop kernel: [    2.218374] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
May  5 15:25:00 herbert-desktop kernel: [    2.218382]   alloc irq_desc for 19 on node 0
May  5 15:25:00 herbert-desktop kernel: [    2.218385]   alloc kstat_irqs on node 0
May  5 15:25:00 herbert-desktop kernel: [    2.218397] b44 0000:04:07.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
May  5 15:25:00 herbert-desktop kernel: [    2.218406] b44 0000:04:07.0: setting latency timer to 64
May  5 15:25:00 herbert-desktop kernel: [    2.277178] usb 2-6: configuration #1 chosen from 1 choice
May  5 15:25:00 herbert-desktop kernel: [    2.287356] input: Logitech Optical USB Mouse as /devices/pci0000:00/0000:00:0b.0/usb2/2-6/2-6:1.0/input/input4
May  5 15:25:00 herbert-desktop kernel: [    2.287470] generic-usb 0003:046D:C016.0002: input,hidraw1: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:0b.0-6/input0
May  5 15:25:00 herbert-desktop kernel: [    2.330112] ssb: Sonics Silicon Backplane found on PCI device 0000:04:07.0
May  5 15:25:00 herbert-desktop kernel: [    2.330256] b44.c:v2.0
May  5 15:25:00 herbert-desktop kernel: [    2.370742] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:1a:a0:42:2f:bb
May  5 15:25:00 herbert-desktop kernel: [    2.466494] EXT4-fs (sda1): mounted filesystem with ordered data mode
May  5 15:25:00 herbert-desktop kernel: [   10.119796] udev: starting version 151
May  5 15:25:00 herbert-desktop kernel: [   10.181010] vga16fb: initializing
May  5 15:25:00 herbert-desktop kernel: [   10.181016] vga16fb: mapped to 0xffff8800000a0000
May  5 15:25:00 herbert-desktop kernel: [   10.181134] fb0: VGA16 VGA frame buffer device
May  5 15:25:00 herbert-desktop kernel: [   10.211307] lp: driver loaded but no devices found
May  5 15:25:00 herbert-desktop kernel: [   10.282701] Adding 14536696k swap on /dev/sda5.  Priority:-1 extents:1 across:14536696k 
May  5 15:25:00 herbert-desktop kernel: [   10.495799] nvidia: module license 'NVIDIA' taints kernel.
May  5 15:25:00 herbert-desktop kernel: [   10.495803] Disabling lock debugging due to kernel taint
May  5 15:25:00 herbert-desktop kernel: [   10.581423] type=1505 audit(1273098300.461:2):  operation="profile_load" pid=691 name="/sbin/dhclient3"
May  5 15:25:00 herbert-desktop kernel: [   10.581706] type=1505 audit(1273098300.461:3):  operation="profile_load" pid=691 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
May  5 15:25:00 herbert-desktop kernel: [   10.581865] type=1505 audit(1273098300.461:4):  operation="profile_load" pid=691 name="/usr/lib/connman/scripts/dhclient-script"
May  5 15:25:00 herbert-desktop kernel: [   10.785956] type=1505 audit(1273098300.661:5):  operation="profile_load" pid=786 name="/usr/share/gdm/guest-session/Xsession"
May  5 15:25:00 herbert-desktop kernel: [   10.792437] type=1505 audit(1273098300.671:6):  operation="profile_replace" pid=788 name="/sbin/dhclient3"
May  5 15:25:00 herbert-desktop kernel: [   10.792729] type=1505 audit(1273098300.671:7):  operation="profile_replace" pid=788 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
May  5 15:25:00 herbert-desktop kernel: [   10.792894] type=1505 audit(1273098300.671:8):  operation="profile_replace" pid=788 name="/usr/lib/connman/scripts/dhclient-script"
May  5 15:25:00 herbert-desktop kernel: [   10.798118] type=1505 audit(1273098300.671:9):  operation="profile_load" pid=791 name="/usr/bin/evince"
May  5 15:25:00 herbert-desktop kernel: [   10.809597] type=1505 audit(1273098300.681:10):  operation="profile_load" pid=791 name="/usr/bin/evince-previewer"
May  5 15:25:00 herbert-desktop NetworkManager: <info>  starting...
May  5 15:25:00 herbert-desktop NetworkManager: <info>  Trying to start the modem-manager...
May  5 15:25:00 herbert-desktop NetworkManager:    SCPlugin-Ifupdown: init!
May  5 15:25:00 herbert-desktop kernel: [   10.822334] type=1505 audit(1273098300.701:11):  operation="profile_load" pid=791 name="/usr/bin/evince-thumbnailer"
May  5 15:25:00 herbert-desktop NetworkManager:    SCPlugin-Ifupdown: update_system_hostname
May  5 15:25:00 herbert-desktop NetworkManager:    SCPluginIfupdown: management mode: unmanaged
May  5 15:25:00 herbert-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:10.0/0000:04:07.0/ssb0:0/net/eth0, iface: eth0)
May  5 15:25:00 herbert-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:10.0/0000:04:07.0/ssb0:0/net/eth0, iface: eth0): no ifupdown configuration found.
May  5 15:25:00 herbert-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
May  5 15:25:00 herbert-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
May  5 15:25:00 herbert-desktop NetworkManager:    SCPlugin-Ifupdown: end _init.
May  5 15:25:00 herbert-desktop NetworkManager: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
May  5 15:25:00 herbert-desktop NetworkManager: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
May  5 15:25:00 herbert-desktop avahi-daemon[798]: Found user 'avahi' (UID 104) and group 'avahi' (GID 111).
May  5 15:25:00 herbert-desktop avahi-daemon[798]: Successfully dropped root privileges.
May  5 15:25:00 herbert-desktop avahi-daemon[798]: avahi-daemon 0.6.25 starting up.
May  5 15:25:00 herbert-desktop avahi-daemon[798]: Successfully called chroot().
May  5 15:25:00 herbert-desktop avahi-daemon[798]: Successfully dropped remaining capabilities.
May  5 15:25:00 herbert-desktop NetworkManager: <info>  WiFi enabled by radio killswitch; enabled by state file
May  5 15:25:00 herbert-desktop NetworkManager: <info>  WWAN enabled by radio killswitch; enabled by state file
May  5 15:25:00 herbert-desktop NetworkManager:    SCPlugin-Ifupdown: (24783136) ... get_connections.
May  5 15:25:00 herbert-desktop NetworkManager:    SCPlugin-Ifupdown: (24783136) ... get_connections (managed=false): return empty list.
May  5 15:25:00 herbert-desktop modem-manager: Loaded plugin Sierra
May  5 15:25:00 herbert-desktop modem-manager: Loaded plugin Generic
May  5 15:25:00 herbert-desktop modem-manager: Loaded plugin Option High-Speed
May  5 15:25:00 herbert-desktop modem-manager: Loaded plugin Option
May  5 15:25:00 herbert-desktop modem-manager: Loaded plugin ZTE
May  5 15:25:00 herbert-desktop modem-manager: Loaded plugin Novatel
May  5 15:25:00 herbert-desktop modem-manager: Loaded plugin AnyData
May  5 15:25:00 herbert-desktop modem-manager: Loaded plugin Huawei
May  5 15:25:00 herbert-desktop modem-manager: Loaded plugin MotoC
May  5 15:25:00 herbert-desktop modem-manager: Loaded plugin Gobi
May  5 15:25:00 herbert-desktop modem-manager: Loaded plugin Longcheer
May  5 15:25:00 herbert-desktop modem-manager: Loaded plugin Ericsson MBM
May  5 15:25:00 herbert-desktop modem-manager: Loaded plugin Nokia
May  5 15:25:00 herbert-desktop NetworkManager:    Ifupdown: get unmanaged devices count: 0
May  5 15:25:00 herbert-desktop NetworkManager: <info>  (eth0): carrier is OFF
May  5 15:25:00 herbert-desktop NetworkManager: <info>  (eth0): new Ethernet device (driver: 'b44')
May  5 15:25:00 herbert-desktop NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
May  5 15:25:00 herbert-desktop NetworkManager: <info>  (eth0): now managed
May  5 15:25:00 herbert-desktop NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
May  5 15:25:00 herbert-desktop NetworkManager: <info>  (eth0): bringing up device.
May  5 15:25:00 herbert-desktop kernel: [   10.981617] ADDRCONF(NETDEV_UP): eth0: link is not ready
May  5 15:25:00 herbert-desktop NetworkManager: <info>  (eth0): preparing device.
May  5 15:25:00 herbert-desktop NetworkManager: <info>  (eth0): deactivating device (reason: 2).
May  5 15:25:00 herbert-desktop NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:10.0/0000:04:07.0/ssb0:0/net/eth0
May  5 15:25:00 herbert-desktop NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
May  5 15:25:00 herbert-desktop NetworkManager: <info>  modem-manager is now available
May  5 15:25:00 herbert-desktop NetworkManager: <info>  Trying to start the supplicant...
May  5 15:25:00 herbert-desktop avahi-daemon[798]: No service file found in /etc/avahi/services.
May  5 15:25:00 herbert-desktop avahi-daemon[798]: Network interface enumeration completed.
May  5 15:25:00 herbert-desktop avahi-daemon[798]: Registering HINFO record with values 'X86_64'/'LINUX'.
May  5 15:25:00 herbert-desktop avahi-daemon[798]: Server startup complete. Host name is herbert-desktop.local. Local service cookie is 2384895824.
May  5 15:25:00 herbert-desktop kernel: [   11.097301] EDAC MC: Ver: 2.1.0 Apr 28 2010
May  5 15:25:01 herbert-desktop kernel: [   11.117312] Linux video capture interface: v2.00
May  5 15:25:01 herbert-desktop kernel: [   11.126724] EDAC amd64_edac:  Ver: 3.2.0 Apr 28 2010
May  5 15:25:01 herbert-desktop kernel: [   11.140519] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
May  5 15:25:01 herbert-desktop kernel: [   11.141341] dell-wmi: No known WMI GUID found
May  5 15:25:01 herbert-desktop kernel: [   11.177083] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 23
May  5 15:25:01 herbert-desktop kernel: [   11.177090] HDA Intel 0000:00:10.1: PCI INT B -> Link[AAZA] -> GSI 23 (level, low) -> IRQ 23
May  5 15:25:01 herbert-desktop kernel: [   11.177094] hda_intel: Disable MSI for Nvidia chipset
May  5 15:25:01 herbert-desktop kernel: [   11.177260] HDA Intel 0000:00:10.1: setting latency timer to 64
May  5 15:25:01 herbert-desktop kernel: [   11.341218] Console: switching to colour frame buffer device 80x30
May  5 15:25:01 herbert-desktop init: apport pre-start process (885) terminated with status 1
May  5 15:25:01 herbert-desktop cron[892]: (CRON) INFO (pidfile fd = 3)
May  5 15:25:01 herbert-desktop anacron[909]: Anacron 2.3 started on 2010-05-05
May  5 15:25:01 herbert-desktop acpid: starting up with proc fs
May  5 15:25:01 herbert-desktop acpid: 36 rules loaded
May  5 15:25:01 herbert-desktop acpid: waiting for events: event logging is off
May  5 15:25:01 herbert-desktop init: apport post-stop process (905) terminated with status 1
May  5 15:25:01 herbert-desktop cron[917]: (CRON) STARTUP (fork ok)
May  5 15:25:01 herbert-desktop cron[917]: (CRON) INFO (Running @reboot jobs)
May  5 15:25:01 herbert-desktop kernel: [   11.506890] ppdev: user-space parallel port driver
May  5 15:25:01 herbert-desktop gdm-binary[920]: WARNING: Unable to find users: no seat-id found
May  5 15:25:01 herbert-desktop anacron[909]: Normal exit (0 jobs run)
May  5 15:25:01 herbert-desktop anacron[1109]: Anacron 2.3 started on 2010-05-05
May  5 15:25:01 herbert-desktop anacron[1109]: Normal exit (0 jobs run)
May  5 15:25:01 herbert-desktop acpid: client connected from 1123[0:0]
May  5 15:25:01 herbert-desktop acpid: 1 client rule loaded
May  5 15:25:02 herbert-desktop gdm-binary[920]: WARNING: GdmDisplay: display lasted 0.610535 seconds
May  5 15:25:02 herbert-desktop acpid: client 1123[0:0] has disconnected
May  5 15:25:02 herbert-desktop acpid: client connected from 1145[0:0]
May  5 15:25:02 herbert-desktop acpid: 1 client rule loaded
May  5 15:25:02 herbert-desktop kernel: [   12.210121] 2:3:1: cannot get freq at ep 0x82
May  5 15:25:02 herbert-desktop kernel: [   12.226869] usbcore: registered new interface driver snd-usb-audio
May  5 15:25:02 herbert-desktop kernel: [   12.227224] uvcvideo: Found UVC 1.00 device Microsoft® LifeCam Cinema(TM) (045e:075d)
May  5 15:25:02 herbert-desktop kernel: [   12.282379] input: Microsoft® LifeCam Cinema(TM) as /devices/pci0000:00/0000:00:0b.1/usb1/1-4/1-4:1.0/input/input5
May  5 15:25:02 herbert-desktop kernel: [   12.282445] usbcore: registered new interface driver uvcvideo
May  5 15:25:02 herbert-desktop kernel: [   12.282448] USB Video Class driver (v0.1.0)
May  5 15:25:02 herbert-desktop gdm-binary[920]: WARNING: GdmDisplay: display lasted 0.174679 seconds
May  5 15:25:02 herbert-desktop acpid: client 1145[0:0] has disconnected
May  5 15:25:02 herbert-desktop acpid: client connected from 1177[0:0]
May  5 15:25:02 herbert-desktop acpid: 1 client rule loaded
May  5 15:25:02 herbert-desktop gdm-binary[920]: WARNING: GdmDisplay: display lasted 0.181619 seconds
May  5 15:25:02 herbert-desktop acpid: client 1177[0:0] has disconnected
May  5 15:25:02 herbert-desktop acpid: client connected from 1185[0:0]
May  5 15:25:02 herbert-desktop acpid: 1 client rule loaded
May  5 15:25:02 herbert-desktop gdm-binary[920]: WARNING: GdmDisplay: display lasted 0.165699 seconds
May  5 15:25:02 herbert-desktop acpid: client 1185[0:0] has disconnected
May  5 15:25:02 herbert-desktop acpid: client connected from 1195[0:0]
May  5 15:25:02 herbert-desktop acpid: 1 client rule loaded
May  5 15:25:02 herbert-desktop gdm-binary[920]: WARNING: GdmDisplay: display lasted 0.167884 seconds
May  5 15:25:02 herbert-desktop acpid: client 1195[0:0] has disconnected
May  5 15:25:02 herbert-desktop acpid: client connected from 1203[0:0]
May  5 15:25:02 herbert-desktop acpid: 1 client rule loaded
May  5 15:25:02 herbert-desktop gdm-binary[920]: WARNING: GdmDisplay: display lasted 0.166461 seconds
May  5 15:25:02 herbert-desktop gdm-binary[920]: WARNING: GdmLocalDisplayFactory: maximum number of X display failures reached: check X server log for errors
May  5 15:25:02 herbert-desktop kernel: [   12.980136] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:10.1/input/input6
May  5 15:25:02 herbert-desktop init: gdm main process (920) terminated with status 1
May  5 15:25:03 herbert-desktop acpid: client 1203[0:0] has disconnected
May  5 15:25:03 herbert-desktop acpid: client connected from 1225[0:0]
May  5 15:25:03 herbert-desktop acpid: 1 client rule loaded
May  5 15:25:03 herbert-desktop kernel: [   13.820262] input: HDA NVidia Line In at Ext Rear Jack as /devices/pci0000:00/0000:00:10.1/sound/card0/input7
May  5 15:25:03 herbert-desktop kernel: [   13.820366] input: HDA NVidia Mic at Ext Front Jack as /devices/pci0000:00/0000:00:10.1/sound/card0/input8
May  5 15:25:03 herbert-desktop kernel: [   13.820436] input: HDA NVidia Mic at Ext Rear Jack as /devices/pci0000:00/0000:00:10.1/sound/card0/input9
May  5 15:25:03 herbert-desktop kernel: [   13.820510] input: HDA NVidia Speaker at Ext Rear Jack as /devices/pci0000:00/0000:00:10.1/sound/card0/input10
May  5 15:25:03 herbert-desktop kernel: [   13.820578] input: HDA NVidia Speaker at Ext Rear Jack as /devices/pci0000:00/0000:00:10.1/sound/card0/input11
May  5 15:25:03 herbert-desktop kernel: [   13.820652] input: HDA NVidia Speaker at Ext Rear Jack as /devices/pci0000:00/0000:00:10.1/sound/card0/input12
May  5 15:25:03 herbert-desktop kernel: [   13.820725] input: HDA NVidia Speaker at Ext Rear Jack as /devices/pci0000:00/0000:00:10.1/sound/card0/input13
May  5 15:25:03 herbert-desktop kernel: [   13.820794] input: HDA NVidia HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:10.1/sound/card0/input14
May  5 15:25:03 herbert-desktop kernel: [   13.880881] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
May  5 15:25:03 herbert-desktop kernel: [   13.881521] i2c i2c-0: nForce2 SMBus adapter at 0x1c00
May  5 15:25:03 herbert-desktop kernel: [   13.881653] i2c i2c-1: nForce2 SMBus adapter at 0x1c40
May  5 15:25:03 herbert-desktop kernel: [   13.919674] EDAC amd64: This node reports that Memory ECC is currently disabled, set F3x44[22] (0000:00:18.3).
May  5 15:25:03 herbert-desktop kernel: [   13.919688] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
May  5 15:25:03 herbert-desktop kernel: [   13.919690]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
May  5 15:25:03 herbert-desktop kernel: [   13.919692]  (Note that use of the override may cause unknown side effects.)
May  5 15:25:03 herbert-desktop kernel: [   13.919725] amd64_edac: probe of 0000:00:18.2 failed with error -22
May  5 15:25:03 herbert-desktop kernel: [   13.928493] ACPI: PCI Interrupt Link [APC7] enabled at IRQ 16
May  5 15:25:03 herbert-desktop kernel: [   13.928502]   alloc irq_desc for 16 on node 0
May  5 15:25:03 herbert-desktop kernel: [   13.928505]   alloc kstat_irqs on node 0
May  5 15:25:03 herbert-desktop kernel: [   13.928518] nvidia 0000:00:05.0: PCI INT A -> Link[APC7] -> GSI 16 (level, low) -> IRQ 16
May  5 15:25:03 herbert-desktop kernel: [   13.928527] nvidia 0000:00:05.0: setting latency timer to 64
May  5 15:25:03 herbert-desktop kernel: [   13.928531] vgaarb: device changed decodes: PCI:0000:00:05.0,olddecodes=io+mem,decodes=none:owns=io+mem
May  5 15:25:03 herbert-desktop kernel: [   13.928858] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  195.36.15  Fri Mar 12 00:29:13 PST 2010
May  5 15:25:03 herbert-desktop NetworkManager: <info>  (eth0): carrier now ON (device state 2)
May  5 15:25:03 herbert-desktop NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
May  5 15:25:03 herbert-desktop NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0'
May  5 15:25:03 herbert-desktop NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
May  5 15:25:03 herbert-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
May  5 15:25:03 herbert-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
May  5 15:25:03 herbert-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
May  5 15:25:03 herbert-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
May  5 15:25:03 herbert-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
May  5 15:25:03 herbert-desktop NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
May  5 15:25:03 herbert-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
May  5 15:25:03 herbert-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
May  5 15:25:03 herbert-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
May  5 15:25:03 herbert-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
May  5 15:25:03 herbert-desktop NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
May  5 15:25:03 herbert-desktop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
May  5 15:25:03 herbert-desktop NetworkManager: <info>  dhclient started with pid 1286
May  5 15:25:03 herbert-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
May  5 15:25:03 herbert-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
May  5 15:25:03 herbert-desktop dhclient: Internet Systems Consortium DHCP Client V3.1.3
May  5 15:25:03 herbert-desktop dhclient: Copyright 2004-2009 Internet Systems Consortium.
May  5 15:25:03 herbert-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
May  5 15:25:03 herbert-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
May  5 15:25:03 herbert-desktop dhclient: All rights reserved.
May  5 15:25:03 herbert-desktop dhclient: For info, please visit https://www.isc.org/software/dhcp/
May  5 15:25:03 herbert-desktop dhclient: 
May  5 15:25:03 herbert-desktop kernel: [   14.012679] b44: eth0: Link is up at 100 Mbps, full duplex.
May  5 15:25:03 herbert-desktop kernel: [   14.012683] b44: eth0: Flow control is off for TX and off for RX.
May  5 15:25:03 herbert-desktop kernel: [   14.014019] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
May  5 15:25:03 herbert-desktop NetworkManager: <info>  DHCP: device eth0 state changed (null) -> preinit
May  5 15:25:03 herbert-desktop dhclient: Listening on LPF/eth0/00:1a:a0:42:2f:bb
May  5 15:25:03 herbert-desktop dhclient: Sending on   LPF/eth0/00:1a:a0:42:2f:bb
May  5 15:25:03 herbert-desktop dhclient: Sending on   Socket/fallback
May  5 15:25:05 herbert-desktop avahi-daemon[798]: Registering new address record for fe80::21a:a0ff:fe42:2fbb on eth0.*.
May  5 15:25:07 herbert-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
May  5 15:25:07 herbert-desktop dhclient: DHCPOFFER of 192.168.2.2 from 192.168.2.1
May  5 15:25:07 herbert-desktop dhclient: DHCPREQUEST of 192.168.2.2 on eth0 to 255.255.255.255 port 67
May  5 15:25:07 herbert-desktop dhclient: DHCPACK of 192.168.2.2 from 192.168.2.1
May  5 15:25:07 herbert-desktop dhclient: bound to 192.168.2.2 -- renewal in 2147483648 seconds.
May  5 15:25:07 herbert-desktop NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound
May  5 15:25:07 herbert-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
May  5 15:25:07 herbert-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
May  5 15:25:07 herbert-desktop NetworkManager: <info>    address 192.168.2.2
May  5 15:25:07 herbert-desktop NetworkManager: <info>    prefix 24 (255.255.255.0)
May  5 15:25:07 herbert-desktop NetworkManager: <info>    gateway 192.168.2.1
May  5 15:25:07 herbert-desktop NetworkManager: <info>    nameserver '192.168.2.1'
May  5 15:25:07 herbert-desktop NetworkManager: <info>    domain name 'Belkin'
May  5 15:25:07 herbert-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
May  5 15:25:07 herbert-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
May  5 15:25:07 herbert-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
May  5 15:25:07 herbert-desktop avahi-daemon[798]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.2.2.
May  5 15:25:07 herbert-desktop avahi-daemon[798]: New relevant interface eth0.IPv4 for mDNS.
May  5 15:25:07 herbert-desktop avahi-daemon[798]: Registering new address record for 192.168.2.2 on eth0.IPv4.
May  5 15:25:08 herbert-desktop NetworkManager: <info>  (eth0): device state change: 7 -> 8 (reason 0)
May  5 15:25:08 herbert-desktop NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
May  5 15:25:08 herbert-desktop NetworkManager: <info>  Activation (eth0) successful, device activated.
May  5 15:25:08 herbert-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
May  5 15:25:09 herbert-desktop ntpdate[1327]: step time server 91.189.94.4 offset -0.628933 sec
May  5 15:25:13 herbert-desktop kernel: [   24.350015] eth0: no IPv6 routers present
May  5 15:25:59 herbert-desktop gdm-binary[1355]: WARNING: Unable to find users: no seat-id found
May  5 15:25:59 herbert-desktop gdm-binary[1355]: WARNING: GdmDisplay: display lasted 0.027882 seconds
May  5 15:25:59 herbert-desktop acpid: client 1225[0:0] has disconnected
May  5 15:25:59 herbert-desktop acpid: client connected from 1363[0:0]
May  5 15:25:59 herbert-desktop acpid: 1 client rule loaded
May  5 15:26:00 herbert-desktop gdm-session-worker[1367]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
May  5 15:26:01 herbert-desktop rtkit-daemon[1454]: Sucessfully called chroot.
May  5 15:26:01 herbert-desktop rtkit-daemon[1454]: Sucessfully dropped privileges.
May  5 15:26:01 herbert-desktop rtkit-daemon[1454]: Sucessfully limited resources.
May  5 15:26:01 herbert-desktop rtkit-daemon[1454]: Running.
May  5 15:26:01 herbert-desktop rtkit-daemon[1454]: Canary thread running.
May  5 15:26:01 herbert-desktop rtkit-daemon[1454]: Watchdog thread running.
May  5 15:26:01 herbert-desktop polkitd[1464]: started daemon version 0.96 using authority implementation `local' version `0.96'
May  5 15:26:01 herbert-desktop rtkit-daemon[1454]: Sucessfully made thread 1450 of process 1450 (n/a) owned by '1000' high priority at nice level -11.
May  5 15:26:01 herbert-desktop rtkit-daemon[1454]: Supervising 1 threads of 1 processes of 1 users.
May  5 15:26:01 herbert-desktop anacron[1509]: Anacron 2.3 started on 2010-05-05
May  5 15:26:01 herbert-desktop anacron[1509]: Normal exit (0 jobs run)
May  5 15:26:02 herbert-desktop acpid: client connected from 1606[108:114]
May  5 15:26:02 herbert-desktop acpid: 1 client rule loaded
May  5 15:26:02 herbert-desktop kernel: [   73.292623] 2:3:1: cannot get freq at ep 0x82
May  5 15:26:03 herbert-desktop kernel: [   74.010175] Clocksource tsc unstable (delta = -155527297 ns)
May  5 15:26:03 herbert-desktop kernel: [   74.420128] 2:3:1: cannot get freq at ep 0x82
May  5 15:26:03 herbert-desktop rtkit-daemon[1454]: Sucessfully made thread 1622 of process 1450 (n/a) owned by '1000' RT at priority 5.
May  5 15:26:03 herbert-desktop rtkit-daemon[1454]: Supervising 2 threads of 1 processes of 1 users.
May  5 15:26:05 herbert-desktop rtkit-daemon[1454]: Sucessfully made thread 1624 of process 1450 (n/a) owned by '1000' RT at priority 5.
May  5 15:26:05 herbert-desktop rtkit-daemon[1454]: Supervising 3 threads of 1 processes of 1 users.
May  5 15:26:05 herbert-desktop rtkit-daemon[1454]: Sucessfully made thread 1625 of process 1450 (n/a) owned by '1000' RT at priority 5.
May  5 15:26:05 herbert-desktop rtkit-daemon[1454]: Supervising 4 threads of 1 processes of 1 users.
May  5 15:26:05 herbert-desktop rtkit-daemon[1454]: Sucessfully made thread 1627 of process 1627 (n/a) owned by '1000' high priority at nice level -11.
May  5 15:26:05 herbert-desktop rtkit-daemon[1454]: Supervising 5 threads of 2 processes of 1 users.
May  5 15:26:05 herbert-desktop pulseaudio[1627]: pid.c: Daemon already running.
May  5 15:26:05 herbert-desktop rtkit-daemon[1454]: Sucessfully made thread 1630 of process 1630 (n/a) owned by '1000' high priority at nice level -11.
May  5 15:26:05 herbert-desktop rtkit-daemon[1454]: Supervising 5 threads of 2 processes of 1 users.
May  5 15:26:05 herbert-desktop pulseaudio[1630]: pid.c: Daemon already running.
May  5 15:26:27 herbert-desktop pulseaudio[1450]: ratelimit.c: 2 events suppressed
```

---

### Post by lidex on 2010-05-06
> **herbertportillo said:**
> Screw it. I'm sticking with Karmic.

I hope that whoever helped design nouveau chokes on a pretzel, has a shoe thrown at his head, gets stuck inside a Chinese palace for the rest of his life, gets mocked whenever he dances, and has a stupid ugly mom named Barbara.

Ahh...someone should develop a game...

---

### Post by herbertportillo on 2010-05-08
A booooooooo

---

### Post by herbertportillo on 2010-05-09
ahhhhhhhhh-bump!

---

### Post by herbertportillo on 2010-05-13
bump :(

---

### Post by herbertportillo on 2010-05-19
bump :cry:

---

### Post by herbertportillo on 2010-05-25
Alright.
I give up.

---

