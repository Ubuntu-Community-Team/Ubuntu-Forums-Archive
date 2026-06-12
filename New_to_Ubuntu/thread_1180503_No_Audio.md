---
title: "No Audio"
date: 2009-06-06
forum: New to Ubuntu
---

### Post by Marko723 on 2009-06-06
I'm not geting sound on my installation. I'm currently running a ASUS P5KPL-CM motherboard with built in audio. ASUS does supply drivers, (VIA Audio Drivers) But I get a few FATAL errors when running their install script.

FATAL: Module snd_hda_intel is in use.
FATAL: Could not open '/lib/modules/2.6.28-11-generic/kernel/sound/pci/hda/snd-hda-intel.ko': No such file or directory


I just ran the command aplay -l and it came back with;

ers@Lucian:/etc$ aplay -l
aplay: device_list:217: no soundcards found...

It makes me think I need to have the audio drivers from ASUS installed before a sound card is detected.

Any suggestions? I've been wondering if I need to give the install script access to the snd_hda_intel, but I'm not sure how to do that. Some messages indicate it's built in to the kernel and not possible with out a re-compile.

Thanks

Mark

---

### Post by jonobr on 2009-06-06
Im no audio or driver genius

Whilst providing you a bump I was going to recommend providing the output of lspci

Also, results from Dmesg may also show something

---

### Post by Marko723 on 2009-06-07
From lspci I have this output, which appears to have an audio device listed.  The output from dmesg is huge... any particular part I can focus on besides audio?

Thanks

Mark

```
ers@Lucian:/etc$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 10)
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
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7300 GT] (rev a1)
02:00.0 Ethernet controller: Attansic Technology Corp. L1e Gigabit Ethernet Adapter (rev b0)

```

---

### Post by jonobr on 2009-06-07
looks as if it sees the audio device 

for finding in the desg you should be able to

dmesg | grep audio

or dmesg | grep -i audio

Hopefully that will pull out everything that references audio in it.

Maybe it will filter out the result so you can post here.

---

### Post by Marko723 on 2009-06-07
No luck with the grep, null return.  :( 

Here's the full dmesg, apologies on the size.

Mark

```
ers@Lucian:/etc$ dmesg
[    0.000000] BIOS EBDA/lowmem at: 0009fc00/0009fc00
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-11-generic (buildd@crested) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 (Ubuntu 2.6.28-11.42-generic)
[    0.000000] Command line: root=UUID=034c396f-5676-4d4c-bccf-f6011717d5f4 ro quiet splash 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000dff90000 (usable)
[    0.000000]  BIOS-e820: 00000000dff90000 - 00000000dff9e000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000dff9e000 - 00000000dffd0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000dffd0000 - 00000000dffde000 (reserved)
[    0.000000]  BIOS-e820: 00000000dffe0000 - 00000000e0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000120000000 (usable)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0x120000 max_arch_pfn = 0x3ffffffff
[    0.000000] last_pfn = 0xdff90 max_arch_pfn = 0x3ffffffff
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000dff90000 (usable)
[    0.000000]  modified: 00000000dff90000 - 00000000dff9e000 (ACPI data)
[    0.000000]  modified: 00000000dff9e000 - 00000000dffd0000 (ACPI NVS)
[    0.000000]  modified: 00000000dffd0000 - 00000000dffde000 (reserved)
[    0.000000]  modified: 00000000dffe0000 - 00000000e0000000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000120000000 (usable)
[    0.000000] init_memory_mapping: 0000000000000000-00000000dff90000
[    0.000000]  0000000000 - 00dfe00000 page 2M
[    0.000000]  00dfe00000 - 00dff90000 page 4k
[    0.000000] kernel direct mapping tables up to dff90000 @ 10000-16000
[    0.000000] last_map_addr: dff90000 end: dff90000
[    0.000000] init_memory_mapping: 0000000100000000-0000000120000000
[    0.000000]  0100000000 - 0120000000 page 2M
[    0.000000] kernel direct mapping tables up to 120000000 @ 14000-1a000
[    0.000000] last_map_addr: 120000000 end: 120000000
[    0.000000] RAMDISK: 3785c000 - 37fef52e
[    0.000000] ACPI: RSDP 000FB7B0, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT DFF90000, 003C (r1 A_M_I_ OEMRSDT  10000830 MSFT       97)
[    0.000000] ACPI: FACP DFF90200, 0084 (r2 A_M_I_ OEMFACP  10000830 MSFT       97)
[    0.000000] ACPI: DSDT DFF905C0, 7C10 (r1  A0968 A0968000        0 INTL 20051117)
[    0.000000] ACPI: FACS DFF9E000, 0040
[    0.000000] ACPI: APIC DFF90390, 006C (r1 A_M_I_ OEMAPIC  10000830 MSFT       97)
[    0.000000] ACPI: MCFG DFF90400, 003C (r1 A_M_I_ OEMMCFG  10000830 MSFT       97)
[    0.000000] ACPI: OEMB DFF9E040, 0080 (r1 A_M_I_ AMI_OEM  10000830 MSFT       97)
[    0.000000] ACPI: HPET DFF981D0, 0038 (r1 A_M_I_ OEMHPET  10000830 MSFT       97)
[    0.000000] ACPI: GSCI DFF9E0C0, 2024 (r1 A_M_I_ GMCHSCI  10000830 MSFT       97)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] (7 early reservations) ==> bootmem [0000000000 - 0120000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0000200000 - 0000b854b0]    TEXT DATA BSS ==> [0000200000 - 0000b854b0]
[    0.000000]   #3 [003785c000 - 0037fef52e]          RAMDISK ==> [003785c000 - 0037fef52e]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [0000010000 - 0000014000]          PGTABLE ==> [0000010000 - 0000014000]
[    0.000000]   #6 [0000014000 - 0000015000]          PGTABLE ==> [0000014000 - 0000015000]
[    0.000000] found SMP MP-table at [ffff8800000ff780] 000ff780
[    0.000000]  [ffffe20000000000-ffffe20003ffffff] PMD -> [ffff880028200000-ffff88002c1fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00120000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000dff90
[    0.000000]     0: 0x00100000 -> 0x00120000
[    0.000000] On node 0 totalpages: 1048351
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 2543 pages reserved
[    0.000000]   DMA zone: 1384 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 899016 pages, LIFO batch:31
[    0.000000]   Normal zone: 1792 pages used for memmap
[    0.000000]   Normal zone: 129280 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 0, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000dff90000 - 00000000dff9e000
[    0.000000] PM: Registered nosave memory: 00000000dff9e000 - 00000000dffd0000
[    0.000000] PM: Registered nosave memory: 00000000dffd0000 - 00000000dffde000
[    0.000000] PM: Registered nosave memory: 00000000dffde000 - 00000000dffe0000
[    0.000000] PM: Registered nosave memory: 00000000dffe0000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000fff00000
[    0.000000] PM: Registered nosave memory: 00000000fff00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at e2000000 (gap: e0000000:1ee00000)
[    0.000000] PERCPU: Allocating 69632 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1029680
[    0.000000] Kernel command line: root=UUID=034c396f-5676-4d4c-bccf-f6011717d5f4 ro quiet splash 
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] TSC: PIT calibration matches PMTIMER. 1 loops
[    0.000000] Detected 2520.657 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.004000] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.004000] allocated 47185920 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Checking aperture...
[    0.004000] No AGP bridge found
[    0.004000] Calgary: detecting Calgary via BIOS EBDA area
[    0.004000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.004000] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.004000] Placing software IO TLB between 0x20000000 - 0x24000000
[    0.004000] Memory: 3990780k/4718592k available (4760k kernel code, 525188k absent, 201716k reserved, 2540k data, 536k init)
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 5041.31 BogoMIPS (lpj=10082628)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 256
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] Initializing cgroup subsys freezer
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using mwait in idle threads.
[    0.004000] ACPI: Core revision 20080926
[    0.004797] ACPI: Checking initramfs for custom DSDT
[    0.269807] Setting APIC routing to flat
[    0.270155] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.309847] CPU0: Intel Pentium(R) Dual-Core  CPU      E5200  @ 2.50GHz stepping 06
[    0.312001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 5041.23 BogoMIPS (lpj=10082477)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.396402] CPU1: Intel Pentium(R) Dual-Core  CPU      E5200  @ 2.50GHz stepping 06
[    0.396421] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.400037] Brought up 2 CPUs
[    0.400039] Total of 2 processors activated (10082.55 BogoMIPS).
[    0.400082] CPU0 attaching sched-domain:
[    0.400084]  domain 0: span 0-1 level MC
[    0.400085]   groups: 0 1
[    0.400090] CPU1 attaching sched-domain:
[    0.400091]  domain 0: span 0-1 level MC
[    0.400092]   groups: 1 0
[    0.400147] net_namespace: 1400 bytes
[    0.400147] Booting paravirtualized kernel on bare hardware
[    0.400226] Time: 23:23:27  Date: 06/06/09
[    0.400226] regulator: core version 0.5
[    0.400226] NET: Registered protocol family 16
[    0.400226] ACPI: bus type pci registered
[    0.400226] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
[    0.400226] PCI: Not using MMCONFIG.
[    0.400226] PCI: Using configuration type 1 for base access
[    0.400696] ACPI: EC: Look up EC in DSDT
[    0.409828] ACPI: Interpreter enabled
[    0.409830] ACPI: (supports S0 S1 S3 S4 S5)
[    0.409847] ACPI: Using IOAPIC for interrupt routing
[    0.409895] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
[    0.412926] PCI: MCFG area at f0000000 reserved in ACPI motherboard resources
[    0.414892] PCI: Using MMCONFIG at f0000000 - f3ffffff
[    0.421590] ACPI: No dock devices found.
[    0.421646] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.421717] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.421719] pci 0000:00:01.0: PME# disabled
[    0.421769] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfbffc000-0xfbffffff]
[    0.421793] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.421796] pci 0000:00:1b.0: PME# disabled
[    0.421833] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.421836] pci 0000:00:1c.0: PME# disabled
[    0.421876] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.421878] pci 0000:00:1c.1: PME# disabled
[    0.421919] pci 0000:00:1d.0: reg 20 io port: [0xb480-0xb49f]
[    0.421957] pci 0000:00:1d.1: reg 20 io port: [0xb800-0xb81f]
[    0.421996] pci 0000:00:1d.2: reg 20 io port: [0xb880-0xb89f]
[    0.422035] pci 0000:00:1d.3: reg 20 io port: [0xbc00-0xbc1f]
[    0.422078] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfbffbc00-0xfbffbfff]
[    0.422110] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.422114] pci 0000:00:1d.7: PME# disabled
[    0.422209] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[    0.422212] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO
[    0.422235] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.422240] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.422245] pci 0000:00:1f.1: reg 18 io port: [0x8f0-0x8f7]
[    0.422251] pci 0000:00:1f.1: reg 1c io port: [0x8f8-0x8fb]
[    0.422256] pci 0000:00:1f.1: reg 20 io port: [0xffa0-0xffaf]
[    0.422287] pci 0000:00:1f.2: reg 10 io port: [0xb400-0xb407]
[    0.422291] pci 0000:00:1f.2: reg 14 io port: [0xb080-0xb083]
[    0.422296] pci 0000:00:1f.2: reg 18 io port: [0xb000-0xb007]
[    0.422300] pci 0000:00:1f.2: reg 1c io port: [0xac00-0xac03]
[    0.422304] pci 0000:00:1f.2: reg 20 io port: [0xa880-0xa88f]
[    0.422318] pci 0000:00:1f.2: PME# supported from D3hot
[    0.422320] pci 0000:00:1f.2: PME# disabled
[    0.422359] pci 0000:00:1f.3: reg 20 io port: [0x400-0x41f]
[    0.422398] pci 0000:01:00.0: reg 10 32bit mmio: [0xfd000000-0xfdffffff]
[    0.422405] pci 0000:01:00.0: reg 14 64bit mmio: [0xe0000000-0xefffffff]
[    0.422412] pci 0000:01:00.0: reg 1c 64bit mmio: [0xfc000000-0xfcffffff]
[    0.422416] pci 0000:01:00.0: reg 24 io port: [0xcc00-0xcc7f]
[    0.422420] pci 0000:01:00.0: reg 30 32bit mmio: [0xfe9e0000-0xfe9fffff]
[    0.422458] pci 0000:00:01.0: bridge io port: [0xc000-0xcfff]
[    0.422460] pci 0000:00:01.0: bridge 32bit mmio: [0xfc000000-0xfe9fffff]
[    0.422463] pci 0000:00:01.0: bridge 64bit mmio pref: [0xe0000000-0xefffffff]
[    0.422545] pci 0000:02:00.0: reg 10 64bit mmio: [0xfeac0000-0xfeafffff]
[    0.422552] pci 0000:02:00.0: reg 18 io port: [0xdc00-0xdc7f]
[    0.422584] pci 0000:02:00.0: PME# supported from D3hot D3cold
[    0.422588] pci 0000:02:00.0: PME# disabled
[    0.422629] pci 0000:00:1c.1: bridge io port: [0xd000-0xdfff]
[    0.422632] pci 0000:00:1c.1: bridge 32bit mmio: [0xfea00000-0xfeafffff]
[    0.422665] pci 0000:04:01.0: reg 10 io port: [0xec00-0xec7f]
[    0.422675] pci 0000:04:01.0: reg 18 io port: [0xe800-0xe8ff]
[    0.422681] pci 0000:04:01.0: reg 1c 32bit mmio: [0xfebff000-0xfebfffff]
[    0.422687] pci 0000:04:01.0: reg 20 32bit mmio: [0xfebc0000-0xfebdffff]
[    0.422697] pci 0000:04:01.0: reg 30 32bit mmio: [0xfeba0000-0xfebbffff]
[    0.422705] pci 0000:04:01.0: supports D1
[    0.422743] pci 0000:00:1e.0: transparent bridge
[    0.422746] pci 0000:00:1e.0: bridge io port: [0xe000-0xefff]
[    0.422749] pci 0000:00:1e.0: bridge 32bit mmio: [0xfeb00000-0xfebfffff]
[    0.422766] bus 00 -> node 0
[    0.422771] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.422930] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.423042] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.423127] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[    0.430508] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.430618] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.430726] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.430835] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.430944] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.431054] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.431163] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.431272] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.431374] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - 47, should be 42 [20080926]
[    0.432069] ACPI: WMI: Mapper loaded
[    0.432100] SCSI subsystem initialized
[    0.432100] libata version 3.00 loaded.
[    0.432100] usbcore: registered new interface driver usbfs
[    0.432100] usbcore: registered new interface driver hub
[    0.432100] usbcore: registered new device driver usb
[    0.432100] PCI: Using ACPI for IRQ routing
[    0.448013] Bluetooth: Core ver 2.13
[    0.448030] NET: Registered protocol family 31
[    0.448030] Bluetooth: HCI device and connection manager initialized
[    0.448030] Bluetooth: HCI socket layer initialized
[    0.448030] NET: Registered protocol family 8
[    0.448030] NET: Registered protocol family 20
[    0.448037] NetLabel: Initializing
[    0.448038] NetLabel:  domain hash size = 128
[    0.448039] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.448050] NetLabel:  unlabeled traffic allowed by default
[    0.448069] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.448072] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.452080] AppArmor: AppArmor Filesystem Enabled
[    0.464014] pnp: PnP ACPI init
[    0.464026] ACPI: bus type pnp registered
[    0.467490] pnp: PnP ACPI: found 18 devices
[    0.467492] ACPI: ACPI bus type pnp unregistered
[    0.467499] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
[    0.467504] system 00:07: ioport range 0x290-0x297 has been reserved
[    0.467508] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.467510] system 00:08: ioport range 0x800-0x87f has been reserved
[    0.467511] system 00:08: ioport range 0x480-0x4bf has been reserved
[    0.467513] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.467515] system 00:08: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.467519] system 00:0b: iomem range 0xffc00000-0xffefffff has been reserved
[    0.467523] system 00:0c: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.467526] system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.467531] system 00:10: iomem range 0xf0000000-0xf3ffffff has been reserved
[    0.467535] system 00:11: iomem range 0x0-0x9ffff could not be reserved
[    0.467536] system 00:11: iomem range 0xc0000-0xcffff has been reserved
[    0.467538] system 00:11: iomem range 0xe0000-0xfffff could not be reserved
[    0.467540] system 00:11: iomem range 0x100000-0xdfffffff could not be reserved
[    0.472167] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.472169] pci 0000:00:01.0:   IO window: 0xc000-0xcfff
[    0.472172] pci 0000:00:01.0:   MEM window: 0xfc000000-0xfe9fffff
[    0.472174] pci 0000:00:01.0:   PREFETCH window: 0x000000e0000000-0x000000efffffff
[    0.472177] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:03
[    0.472178] pci 0000:00:1c.0:   IO window: disabled
[    0.472182] pci 0000:00:1c.0:   MEM window: disabled
[    0.472185] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.472189] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:02
[    0.472191] pci 0000:00:1c.1:   IO window: 0xd000-0xdfff
[    0.472195] pci 0000:00:1c.1:   MEM window: 0xfea00000-0xfeafffff
[    0.472198] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.472202] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:04
[    0.472204] pci 0000:00:1e.0:   IO window: 0xe000-0xefff
[    0.472208] pci 0000:00:1e.0:   MEM window: 0xfeb00000-0xfebfffff
[    0.472211] pci 0000:00:1e.0:   PREFETCH window: 0x000000f4000000-0x000000f40fffff
[    0.472222] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.472224] pci 0000:00:01.0: setting latency timer to 64
[    0.472229] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.472232] pci 0000:00:1c.0: setting latency timer to 64
[    0.472238] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.472241] pci 0000:00:1c.1: setting latency timer to 64
[    0.472246] pci 0000:00:1e.0: setting latency timer to 64
[    0.472249] bus: 00 index 0 io port: [0x00-0xffff]
[    0.472250] bus: 00 index 1 mmio: [0x000000-0xffffffffffffffff]
[    0.472251] bus: 01 index 0 io port: [0xc000-0xcfff]
[    0.472253] bus: 01 index 1 mmio: [0xfc000000-0xfe9fffff]
[    0.472254] bus: 01 index 2 mmio: [0xe0000000-0xefffffff]
[    0.472255] bus: 01 index 3 mmio: [0x0-0x0]
[    0.472256] bus: 03 index 0 mmio: [0x0-0x0]
[    0.472257] bus: 03 index 1 mmio: [0x0-0x0]
[    0.472258] bus: 03 index 2 mmio: [0x0-0x0]
[    0.472259] bus: 03 index 3 mmio: [0x0-0x0]
[    0.472260] bus: 02 index 0 io port: [0xd000-0xdfff]
[    0.472261] bus: 02 index 1 mmio: [0xfea00000-0xfeafffff]
[    0.472262] bus: 02 index 2 mmio: [0x0-0x0]
[    0.472263] bus: 02 index 3 mmio: [0x0-0x0]
[    0.472265] bus: 04 index 0 io port: [0xe000-0xefff]
[    0.472266] bus: 04 index 1 mmio: [0xfeb00000-0xfebfffff]
[    0.472267] bus: 04 index 2 mmio: [0xf4000000-0xf40fffff]
[    0.472268] bus: 04 index 3 io port: [0x00-0xffff]
[    0.472270] bus: 04 index 4 mmio: [0x000000-0xffffffffffffffff]
[    0.472276] NET: Registered protocol family 2
[    0.500464] Switched to high resolution mode on CPU 1
[    0.504013] Switched to high resolution mode on CPU 0
[    0.508082] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.508514] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.510375] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.510878] TCP: Hash tables configured (established 262144 bind 65536)
[    0.510880] TCP reno registered
[    0.520140] NET: Registered protocol family 1
[    0.520236] checking if image is initramfs... it is
[    1.052632] Freeing initrd memory: 7757k freed
[    1.056054] audit: initializing netlink socket (disabled)
[    1.056078] type=2000 audit(1244330607.052:1): initialized
[    1.062698] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.063604] VFS: Disk quotas dquot_6.5.1
[    1.063641] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.064050] fuse init (API version 7.10)
[    1.064105] msgmni has been set to 7811
[    1.064227] alg: No test for stdrng (krng)
[    1.064234] io scheduler noop registered
[    1.064236] io scheduler anticipatory registered
[    1.064237] io scheduler deadline registered
[    1.064266] io scheduler cfq registered (default)
[    1.064363] pci 0000:01:00.0: Boot video device
[    1.067172] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.067197] pcieport-driver 0000:00:01.0: found MSI capability
[    1.067215] pcieport-driver 0000:00:01.0: irq 2303 for MSI/MSI-X
[    1.067222] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.067231] pci_express 0000:00:01.0:pcie03: allocate port service
[    1.067266] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.067292] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.067311] pcieport-driver 0000:00:1c.0: irq 2302 for MSI/MSI-X
[    1.067319] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.067328] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.067336] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.067381] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    1.067407] pcieport-driver 0000:00:1c.1: found MSI capability
[    1.067426] pcieport-driver 0000:00:1c.1: irq 2301 for MSI/MSI-X
[    1.067434] pci_express 0000:00:1c.1:pcie00: allocate port service
[    1.067443] pci_express 0000:00:1c.1:pcie02: allocate port service
[    1.067452] pci_express 0000:00:1c.1:pcie03: allocate port service
[    1.067500] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.067741] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.067839] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.067840] ACPI: Power Button (FF) [PWRF]
[    1.067878] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.067880] ACPI: Power Button (CM) [PWRB]
[    1.068319] ACPI: SSDT DFFA00F0, 0256 (r1    AMI   CPU1PM        1 INTL 20060113)
[    1.068561] processor ACPI_CPU:00: registered as cooling_device0
[    1.068798] ACPI: SSDT DFFA0350, 0143 (r1    AMI   CPU2PM        1 INTL 20060113)
[    1.069022] processor ACPI_CPU:01: registered as cooling_device1
[    1.096685] Linux agpgart interface v0.103
[    1.096692] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.096774] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.097092] 00:0f: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.097616] brd: module loaded
[    1.097838] loop: module loaded
[    1.097883] Fixed MDIO Bus: probed
[    1.097887] PPP generic driver version 2.4.2
[    1.097928] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.097946] Driver 'sd' needs updating - please use bus_type methods
[    1.097953] Driver 'sr' needs updating - please use bus_type methods
[    1.098001] ata_piix 0000:00:1f.1: version 2.12
[    1.098011] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.098037] ata_piix 0000:00:1f.1: setting latency timer to 64
[    1.098102] scsi0 : ata_piix
[    1.098160] scsi1 : ata_piix
[    1.099240] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    1.099242] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    1.260323] ata1.00: ATAPI: TSSTcorp CDDVDW SH-S222A, SB00, max UDMA/66
[    1.276258] ata1.00: configured for UDMA/66
[    1.443347] scsi 0:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S222A  SB00 PQ: 0 ANSI: 5
[    1.446939] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.446943] Uniform CD-ROM driver Revision: 3.20
[    1.447024] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.447053] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.447069] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.447071] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    1.447098] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.447143] scsi2 : ata_piix
[    1.447185] scsi3 : ata_piix
[    1.448524] ata3: SATA max UDMA/133 cmd 0xb400 ctl 0xb080 bmdma 0xa880 irq 19
[    1.448526] ata4: SATA max UDMA/133 cmd 0xb000 ctl 0xac00 bmdma 0xa888 irq 19
[    1.620781] ata3.00: ATA-8: WDC WD6400AAKS-00A7B0, 01.03B01, max UDMA/133
[    1.620785] ata3.00: 1250263728 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.621043] ata3.01: ATA-8: Hitachi HDT721010SLA360, ST6OA31B, max UDMA/133
[    1.621047] ata3.01: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.636805] ata3.00: configured for UDMA/133
[    1.652431] ata3.01: configured for UDMA/133
[    1.856355] ata4.00: ATA-8: Hitachi HDT721010SLA360, ST6OA31B, max UDMA/133
[    1.856358] ata4.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.856585] ata4.01: ATA-8: Hitachi HDT721010SLA360, ST6OA31B, max UDMA/133
[    1.856589] ata4.01: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.872380] ata4.00: configured for UDMA/133
[    1.888380] ata4.01: configured for UDMA/133
[    1.888448] scsi 2:0:0:0: Direct-Access     ATA      WDC WD6400AAKS-0 01.0 PQ: 0 ANSI: 5
[    1.888513] sd 2:0:0:0: [sda] 1250263728 512-byte hardware sectors: (640 GB/596 GiB)
[    1.888525] sd 2:0:0:0: [sda] Write Protect is off
[    1.888527] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.888546] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.888586] sd 2:0:0:0: [sda] 1250263728 512-byte hardware sectors: (640 GB/596 GiB)
[    1.888597] sd 2:0:0:0: [sda] Write Protect is off
[    1.888599] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.888617] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.888619]  sda: sda1 sda2 < sda5 >
[    1.915745] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.915773] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.915817] scsi 2:0:1:0: Direct-Access     ATA      Hitachi HDT72101 ST6O PQ: 0 ANSI: 5
[    1.915874] sd 2:0:1:0: [sdb] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
[    1.915885] sd 2:0:1:0: [sdb] Write Protect is off
[    1.915886] sd 2:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    1.915904] sd 2:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.915941] sd 2:0:1:0: [sdb] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
[    1.915952] sd 2:0:1:0: [sdb] Write Protect is off
[    1.915953] sd 2:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    1.915971] sd 2:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.915973]  sdb: sdb1
[    1.925154] sd 2:0:1:0: [sdb] Attached SCSI disk
[    1.925179] sd 2:0:1:0: Attached scsi generic sg2 type 0
[    1.925225] scsi 3:0:0:0: Direct-Access     ATA      Hitachi HDT72101 ST6O PQ: 0 ANSI: 5
[    1.925282] sd 3:0:0:0: [sdc] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
[    1.925293] sd 3:0:0:0: [sdc] Write Protect is off
[    1.925295] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    1.925313] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.925354] sd 3:0:0:0: [sdc] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
[    1.925364] sd 3:0:0:0: [sdc] Write Protect is off
[    1.925366] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    1.925384] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.925386]  sdc: sdc1
[    1.943170] sd 3:0:0:0: [sdc] Attached SCSI disk
[    1.943196] sd 3:0:0:0: Attached scsi generic sg3 type 0
[    1.943239] scsi 3:0:1:0: Direct-Access     ATA      Hitachi HDT72101 ST6O PQ: 0 ANSI: 5
[    1.943295] sd 3:0:1:0: [sdd] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
[    1.943305] sd 3:0:1:0: [sdd] Write Protect is off
[    1.943307] sd 3:0:1:0: [sdd] Mode Sense: 00 3a 00 00
[    1.943324] sd 3:0:1:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.943359] sd 3:0:1:0: [sdd] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
[    1.943369] sd 3:0:1:0: [sdd] Write Protect is off
[    1.943371] sd 3:0:1:0: [sdd] Mode Sense: 00 3a 00 00
[    1.943388] sd 3:0:1:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.943391]  sdd: unknown partition table
[    1.962567] sd 3:0:1:0: [sdd] Attached SCSI disk
[    1.962616] sd 3:0:1:0: Attached scsi generic sg4 type 0
[    1.962636] sata_promise 0000:04:01.0: version 2.12
[    1.962645] sata_promise 0000:04:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.962754] scsi4 : sata_promise
[    1.962800] scsi5 : sata_promise
[    1.962841] scsi6 : sata_promise
[    1.962877] scsi7 : sata_promise
[    1.962902] ata5: SATA max UDMA/133 mmio m4096@0xfebff000 ata 0xfebff380 irq 16
[    1.962905] ata6: SATA max UDMA/133 mmio m4096@0xfebff000 ata 0xfebff280 irq 16
[    1.962907] ata7: SATA max UDMA/133 mmio m4096@0xfebff000 ata 0xfebff200 irq 16
[    1.962910] ata8: SATA max UDMA/133 mmio m4096@0xfebff000 ata 0xfebff300 irq 16
[    2.280024] ata5: SATA link down (SStatus 0 SControl 300)
[    2.600023] ata6: SATA link down (SStatus 0 SControl 300)
[    2.920023] ata7: SATA link down (SStatus 0 SControl 300)
[    3.240023] ata8: SATA link down (SStatus 0 SControl 300)
[    3.240434] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.240450] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.240458] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.240460] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.240509] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    3.244411] ehci_hcd 0000:00:1d.7: debug port 1
[    3.244416] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.244425] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfbffbc00
[    3.256012] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    3.256087] usb usb1: configuration #1 chosen from 1 choice
[    3.256107] hub 1-0:1.0: USB hub found
[    3.256113] hub 1-0:1.0: 8 ports detected
[    3.256189] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.256198] uhci_hcd: USB Universal Host Controller Interface driver
[    3.256218] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.256223] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.256226] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.256254] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    3.256273] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000b480
[    3.256331] usb usb2: configuration #1 chosen from 1 choice
[    3.256347] hub 2-0:1.0: USB hub found
[    3.256352] hub 2-0:1.0: 2 ports detected
[    3.256408] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.256412] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.256414] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.256443] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    3.256462] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000b800
[    3.256515] usb usb3: configuration #1 chosen from 1 choice
[    3.256534] hub 3-0:1.0: USB hub found
[    3.256538] hub 3-0:1.0: 2 ports detected
[    3.256593] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.256597] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.256599] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.256629] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    3.256653] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000b880
[    3.256704] usb usb4: configuration #1 chosen from 1 choice
[    3.256722] hub 4-0:1.0: USB hub found
[    3.256726] hub 4-0:1.0: 2 ports detected
[    3.256781] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    3.256785] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    3.256787] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.256814] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    3.256833] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000bc00
[    3.256884] usb usb5: configuration #1 chosen from 1 choice
[    3.256900] hub 5-0:1.0: USB hub found
[    3.256904] hub 5-0:1.0: 2 ports detected
[    3.256992] usbcore: registered new interface driver libusual
[    3.257015] usbcore: registered new interface driver usbserial
[    3.257024] USB Serial support registered for generic
[    3.257037] usbcore: registered new interface driver usbserial_generic
[    3.257038] usbserial: USB Serial Driver core
[    3.257076] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    3.259726] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.259730] serio: i8042 AUX port at 0x60,0x64 irq 12
[    3.268550] mice: PS/2 mouse device common for all mice
[    3.304576] rtc_cmos 00:03: RTC can wake from S4
[    3.304599] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    3.304620] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    3.304667] device-mapper: uevent: version 1.0.3
[    3.304728] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    3.304782] device-mapper: multipath: version 1.0.5 loaded
[    3.304784] device-mapper: multipath round-robin: version 1.0.0 loaded
[    3.304849] cpuidle: using governor ladder
[    3.304851] cpuidle: using governor menu
[    3.305147] TCP cubic registered
[    3.305194] NET: Registered protocol family 10
[    3.305487] lo: Disabled Privacy Extensions
[    3.305689] NET: Registered protocol family 17
[    3.305702] Bluetooth: L2CAP ver 2.11
[    3.305703] Bluetooth: L2CAP socket layer initialized
[    3.305705] Bluetooth: SCO (Voice Link) ver 0.6
[    3.305706] Bluetooth: SCO socket layer initialized
[    3.305727] Bluetooth: RFCOMM socket layer initialized
[    3.305733] Bluetooth: RFCOMM TTY layer initialized
[    3.305734] Bluetooth: RFCOMM ver 1.10
[    3.306217] registered taskstats version 1
[    3.306304]   Magic number: 13:712:402
[    3.306378] rtc_cmos 00:03: setting system clock to 2009-06-06 23:23:30 UTC (1244330610)
[    3.306380] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.306381] EDD information not available.
[    3.306412] Freeing unused kernel memory: 536k freed
[    3.306591] Write protecting the kernel read-only data: 6708k
[    3.322433] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    3.428026] ATL1E 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.428038] ATL1E 0000:02:00.0: setting latency timer to 64
[    3.747346] PM: Starting manual resume from disk
[    3.747349] PM: Resume from partition 8:5
[    3.747350] PM: Checking hibernation image.
[    3.747516] PM: Resume from disk failed.
[    3.782370] kjournald starting.  Commit interval 5 seconds
[    3.782384] EXT3-fs: mounted filesystem with ordered data mode.
[    7.305176] udev: starting version 141
[    7.873871] nvidia: module license 'NVIDIA' taints kernel.
[    8.125879] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.125885] nvidia 0000:01:00.0: setting latency timer to 64
[    8.126562] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  180.44  Tue Mar 24 05:46:32 PST 2009
[    8.154116] parport_pc 00:06: reported by Plug and Play ACPI
[    8.154217] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[    8.169263] input: PC Speaker as /devices/platform/pcspkr/input/input4
[    8.183331] intel_rng: FWH not detected
[    8.200028] ppdev: user-space parallel port driver
[    8.225298] iTCO_vendor_support: vendor-support=0
[    8.226781] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[    8.226860] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, TCOBASE=0x0860)
[    8.226903] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[    8.247809] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[    8.303293] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.303339] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    8.423952] lp0: using parport0 (interrupt-driven).
[    8.515931] Adding 11711344k swap on /dev/sda5.  Priority:-1 extents:1 across:11711344k
[    8.760753] logips2pp: Detected unknown logitech mouse model 104
[    9.042425] EXT3 FS on sda1, internal journal
[    9.238655] input: ImExPS/2 Logitech Explorer Mouse as /devices/platform/i8042/serio1/input/input5
[    9.792323] kjournald starting.  Commit interval 5 seconds
[    9.792597] EXT3 FS on sdb1, internal journal
[    9.792603] EXT3-fs: mounted filesystem with ordered data mode.
[    9.813399] kjournald starting.  Commit interval 5 seconds
[    9.813677] EXT3 FS on sdc1, internal journal
[    9.813683] EXT3-fs: mounted filesystem with ordered data mode.
[   10.015561] type=1505 audit(1244330617.205:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2089
[   10.043959] type=1505 audit(1244330617.233:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2093
[   10.044064] type=1505 audit(1244330617.237:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2093
[   10.044093] type=1505 audit(1244330617.237:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2093
[   10.044123] type=1505 audit(1244330617.237:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2093
[   10.124442] type=1505 audit(1244330617.317:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2098
[   10.124591] type=1505 audit(1244330617.317:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2098
[   10.142794] type=1505 audit(1244330617.333:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2102
[   15.574078] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   15.574080] Bluetooth: BNEP filters: protocol multicast
[   15.580770] Bridge firewalling registered
[   20.807928] ATL1E 0000:02:00.0: irq 2300 for MSI/MSI-X
[   20.808081] ATL1E 0000:02:00.0: ATL1E: eth0 NIC Link is Up<1000 Mbps Full Duplex>
[   20.808574] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.810107] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   30.836010] eth0: no IPv6 routers present
[  192.030925] sd 3:0:1:0: [sdd] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
[  192.030949] sd 3:0:1:0: [sdd] Write Protect is off
[  192.030952] sd 3:0:1:0: [sdd] Mode Sense: 00 3a 00 00
[  192.030989] sd 3:0:1:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  192.030995]  sdd: sdd1
[  708.172925] kjournald starting.  Commit interval 5 seconds
[  708.173293] EXT3 FS on sdd1, internal journal
[  708.173299] EXT3-fs: mounted filesystem with ordered data mode.
[ 5848.056605] ppdev0: registered pardevice
[ 5848.104552] ppdev0: unregistered pardevice
[ 5848.404311] ppdev0: registered pardevice
[ 5848.468756] ppdev0: unregistered pardevice
[ 5851.552260] ppdev0: registered pardevice
[ 5851.600206] ppdev0: unregistered pardevice
[ 5973.917386] python[16326]: segfault at 0 ip 00007ffc7ea099d4 sp 00007fff92afe8a8 error 6 in libdbus-1.so.3.4.0[7ffc7e9e4000+3c000]


```

---

### Post by Marko723 on 2009-06-07
I did notice this towards the end.  

[    8.169263] input: PC Speaker as /devices/platform/pcspkr/input/input4
[    8.183331] intel_rng: FWH not detected


I've been trying google the *FWH not detected*, but nothing conclusive...


EDIT:  Okay, this appears to a Random Number Generation bug....

---

