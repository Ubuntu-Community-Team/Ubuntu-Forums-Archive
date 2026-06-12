---
title: "make-kpkg fails on amd64 dual core"
date: 2010-06-01
forum: New to Ubuntu
---

### Post by robkey on 2010-06-01
Hi I built a kernel using the kernel-package. It works perfectly on any single core processor but fails as follows on a dual core (and presumably mult-core) Details:

invocation:
cd /usr/src/linux-source-2.6.32
make mrproper
make-kpkg clean (not necessary just in case)
rm -rf debian (not necessary)
make menuconfig

CONCURRENCY_LEVEL=3 make-kpkg --arch=amd64 --append-to-version='custom12' --initrd kernel_image kernel_headers > ~/out  2>~/out-error

normal output:
make[2]: Leaving directory `/usr/src/linux-source-2.6.32'
make[1]: Leaving directory `/usr/src/linux-source-2.6.32'
error code 0
( compile and link were successful) 

error output:
[: 9: -f: unexpected operator
WARNING: Couldn't open directory /usr/src/linux-source-2.6.32/debian/linux-image-/lib/modules/2.6.32-22-generic: No such file or directory
FATAL: Could not open[COLOR=Red] /usr/src/linux-source-2.6.32/debian/linux-image-/lib/modules/2.6.32-22-generic[/COLOR]/modules.dep.temp for writing: No such file or directory
make[2]: *** [_modinst_post] Error 1
make[1]: *** [debian/stamp/install/linux-image-] Error 2
make: *** [kernel_image] Error 2
( the building of the deb packages has failed)

Notice [COLOR=Blue]appendage is 'custom12'[/COLOR] but why is there_[COLOR=Red] /lib/modules/2.6.32-22-generic[/COLOR]_ there on the FATAL line?
make-kpkg must be doing a `uname -r` because my boot kernel is vmlinuz-2.6.32-22-generic?

Thanks any help would be appreciated?
Rob Key

---

### Post by -humanaut- on 2010-06-01
Are you sure your cores aren't just being tossed to an irq channel open a terminal and type: dmesg | head -100

---

### Post by robkey on 2010-06-01
I will check but thanks for the info. I will give feedback.
thanks,
  Rob
 Here is the output it doesn't say anything about IRQs.

robert@tatty:~$ dmesg | head -100
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-22-generic (buildd@yellow) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 (Ubuntu 2.6.32-22.33-generic 2.6.32.11+drm33.2)
[    0.000000] Command line: BOOT_IMAGE=/vmlinuz-2.6.32-22-generic root=UUID=02b088e4-a40d-4801-b2c5-e65dfcf2e5d7 ro noapic
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cfff0000 (usable)
[    0.000000]  BIOS-e820: 00000000cfff0000 - 00000000cfff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cfff3000 - 00000000d0000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000d0000000 - 00000000e0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f8000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000170000000 (usable)
[    0.000000] DMI 2.3 present.
[    0.000000] last_pfn = 0x170000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-through
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FF80000000 write-back
[    0.000000]   1 base 0080000000 mask FFC0000000 write-back
[    0.000000]   2 base 00C0000000 mask FFF0000000 write-back
[    0.000000]   3 base 0100000000 mask FFC0000000 write-back
[    0.000000]   4 base 0140000000 mask FFE0000000 write-back
[    0.000000]   5 base 0160000000 mask FFF0000000 write-back
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 0000000170000000 aka 5888M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000d0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xcfff0 max_arch_pfn = 0x400000000
[    0.000000] e820 update range: 0000000000001000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (usable)
[    0.000000]  modified: 0000000000001000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000cfff0000 (usable)
[    0.000000]  modified: 00000000cfff0000 - 00000000cfff3000 (ACPI NVS)
[    0.000000]  modified: 00000000cfff3000 - 00000000d0000000 (ACPI data)
[    0.000000]  modified: 00000000d0000000 - 00000000e0000000 (reserved)
[    0.000000]  modified: 00000000f0000000 - 00000000f8000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000170000000 (usable)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-00000000cfff0000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0000000000 - 00cfe00000 page 2M
[    0.000000]  00cfe00000 - 00cfff0000 page 4k
[    0.000000] kernel direct mapping tables up to cfff0000 @ 8000-e000
[    0.000000] init_memory_mapping: 0000000100000000-0000000170000000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0100000000 - 0170000000 page 2M
[    0.000000] kernel direct mapping tables up to 170000000 @ c000-13000
[    0.000000] RAMDISK: 37734000 - 37feffeb
[    0.000000] ACPI: RSDP 00000000000f6480 00014 (v00 GBT   )
[    0.000000] ACPI: RSDT 00000000cfff3000 00038 (v01 GBT    NVDAACPI 42302E31 NVDA 01010101)
[    0.000000] ACPI: FACP 00000000cfff3040 00074 (v01 GBT    NVDAACPI 42302E31 NVDA 01010101)
[    0.000000] ACPI: DSDT 00000000cfff30c0 04A61 (v01 GBT    NVDAACPI 00001000 MSFT 0100000C)
[    0.000000] ACPI: FACS 00000000cfff0000 00040
[    0.000000] ACPI: SSDT 00000000cfff7c00 0028A (v01 PTLTD  POWERNOW 00000001  LTP 00000001)
[    0.000000] ACPI: HPET 00000000cfff7ec0 00038 (v01 GBT    NVDAACPI 42302E31 NVDA 00000098)
[    0.000000] ACPI: MCFG 00000000cfff7f00 0003C (v01 GBT    NVDAACPI 42302E31 NVDA 01010101)
[    0.000000] ACPI: APIC 00000000cfff7b40 0008E (v01 GBT    NVDAACPI 42302E31 NVDA 01010101)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000170000000
[    0.000000] Bootmem setup node 0 0000000000000000-0000000170000000
[    0.000000]   NODE_DATA [000000000000e000 - 0000000000012fff]
[    0.000000]   bootmap [0000000000013000 -  0000000000040fff] pages 2e
[    0.000000] (8 early reservations) ==> bootmem [0000000000 - 0170000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 0001a29e64]    TEXT DATA BSS ==> [0001000000 - 0001a29e64]
[    0.000000]   #3 [0037734000 - 0037feffeb]          RAMDISK ==> [0037734000 - 0037feffeb]
[    0.000000]   #4 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #5 [0001a2a000 - 0001a2a08a]              BRK ==> [0001a2a000 - 0001a2a08a]
[    0.000000]   #6 [0000008000 - 000000c000]          PGTABLE ==> [0000008000 - 000000c000]
[    0.000000]   #7 [000000c000 - 000000e000]          PGTABLE ==> [000000c000 - 000000e000]
[    0.000000] found SMP MP-table at [ffff8800000f4b10] f4b10
[    0.000000]  [ffffea0000000000-ffffea00051fffff] PMD -> [ffff880028600000-ffff88002cdfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00170000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
robert@tatty:~$ 
thanks, 
  Rob

---

