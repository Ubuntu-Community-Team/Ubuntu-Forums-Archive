---
title: "system crash"
date: 2011-02-28
forum: New to Ubuntu
---

### Post by ben889 on 2011-02-28
System crashes a lot what logs should i be looking at?

ubuntu 10.10
acer aspire
dual core amd 1.8
2gig memory
7000m nvidia graphics


Thanks Ben

---

### Post by TechWiz2100 on 2011-02-28
Depends on the kind of crash. Can you give more information about how, why and when the crash occurs.

---

### Post by ben889 on 2011-02-28
it seems to happen when the system is being taxed i haven't pinpointed it to any one particular thing for instance i could be authoring a dvd and it will crash, or have a heavy flash web page up it will crash. the most i can say is when the system is under some load. I really don't want to keep dual booting i like ubuntu and want it as my only os.

thanks ben

---

### Post by sikander3786 on 2011-02-28
Most probably RAM or graphics or over heat.

Press and hold down <Shift> key from Bios screen until you see the Grub menu. Then select memtest and see if any errors are reported. The test might run over-night so be prepared.

Keep an eye on system temperatures including the CPU and graphics chip. Clean the vents and look for any dust blocking the fans. Also make sure all of the fans are actually spinning.

---

### Post by ben889 on 2011-02-28
but why would it only do it on ubuntu but not when i boot into windows?

also i have created a acerhdf.conf and put it in modeprobe and now ubuntu runs as cool as when i dual boot into windows

---

### Post by sikander3786 on 2011-02-28
> **ben889 said:**
> but why would it only do it on ubuntu but not when i boot into windows?
If Windows works just fine, the hardware is probably not the culprit here.

So, a test will be to boot and Ubutnu 10.10 Live CD/USB and run it for quite some time, at least that much that you expect it to crash. If it doesn't crash, your graphics drivers or compiz might be causing the problem.

---

### Post by ben889 on 2011-02-28
OK ill give that a shot thanks.

I just thought i could see in the logs where it would be failing.

as for the drivers i have tried the (recommended) drivers through the driver app and it crashed so i tried the (not recommended) 173 drivers and it still crashes. could i test it by removing compiz?

---

### Post by ben889 on 2011-03-01
live cd i havnt had it crash had it up most of the day yesterday. not sure if i was putting enough load on it to tax the system though

---

### Post by TechWiz2100 on 2011-03-01
Post your kern and dmesg logs

Sounds to me like typical symptoms if a kernel panic. Maybe a malfunctioning library or some random illegal operation.

---

### Post by hansolo4949 on 2011-03-01
I think the system IS overheating, but it isn't a hardware issue. Do you hear the fans in your computer turn on ever when you are using Ubuntu? Because that is one bug in Ubuntu, on some systems the fans won't come on, and the system will overheat.

---

### Post by ben889 on 2011-03-01
i created a acerhdf.conf for my modeprobe the fans are set to go on at 46c and off at 48c. 

i can post the kern and dmesg logs i keep getting a time out

---

### Post by TechWiz2100 on 2011-03-01
> **ben889 said:**
> i created a acerhdf.conf for my modeprobe the fans are set to go on at 46c and off at 48c. 

i can post the kern and dmesg logs i keep getting a time out

I hope you mean on at 46 and full throttle at 48?
By the way, might just be my personal preference but I feel those values are FAR to high. I personally set fans to minimal speed and then crank them up at 44c and max at 47 because normal operating temp is "40*C" and 55*C is where some components will attain some form of damage from the heat.

The 360 with crappy cooling will get upto ~58C and then the solder will begin to crack (I measured it with a laser thermo while doing repairs once)

That aside, how do you get a timeout on a non-networking command? lol

---

### Post by TechWiz2100 on 2011-03-01
> **zhouchaojie said:**
> [FONT=Times New Roman]Within European locations, men and women own several religions. Within Spain, football is additionally like a religion on most those who is because it really is its dearest activity. In the past, going to places of worship about Sundays will be the only essential matter which Spanish men and women complete even though right now they will watch football matches about Weekend nights. In the overdue 1800s, Uk immigrant workers, going to ocean adventurers in addition to Spanish foreign students very first carry modern football to Spain. Right now lots of people know several good football players within regarding Spain, this specific state is actually popular through it has the competent football clubs.[/FONT]

lol someone pasted the wrong text methinks

[edit] nvm hes just trolling us with shitty advertisements

cue the mods....

---

### Post by ben889 on 2011-03-02
no when i copy and paste the logs to post the browser timed out sorry i wasnt clear on that.
also wouldnt know how to crank them up? this is the modeprobe i created i just changed the values.

/etc/modprobe.d/acerhdf.conf
The file contains only this
 options acerhdf interval=5 fanon=58000 fanoff=53000 kernelmode=1

---

### Post by ben889 on 2011-03-02
want to post my log files but i keep getting this

**Fatal error**:  Maximum execution time of 60 seconds exceeded in **/srv/www.ubuntuforums.org/public_html/includes/functions.php** on line **1838**

how should i post my log files?

---

### Post by ben889 on 2011-03-03
just bumping his so it doesn't get to far down the link

---

### Post by sikander3786 on 2011-03-03
Were you trying to attach the files to UF? If so, try to copy/paste the text in your post in [code] tags or if you were pasting it already, try the other way I mean, attach the whole files with your post.

---

### Post by ben889 on 2011-03-04
Mar  2 19:46:36 ben-Aspire-5520 kernel: imklog 4.2.0, log source = /proc/kmsg started.
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] Initializing cgroup subsys cpuset
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] Initializing cgroup subsys cpu
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] Linux version 2.6.35-25-generic (buildd@palmer) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #44-Ubuntu SMP Fri Jan 21 17:40:48 UTC 2011 (Ubuntu 2.6.35-25.44-generic 2.6.35.10)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] BIOS-provided physical RAM map:
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e000 (usable)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]  BIOS-e820: 000000000009e000 - 00000000000a0000 (reserved)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]  BIOS-e820: 00000000000d2000 - 0000000000100000 (reserved)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000006ff50000 (usable)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]  BIOS-e820: 000000006ff50000 - 000000006ff65000 (ACPI data)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]  BIOS-e820: 000000006ff65000 - 000000006ff66000 (ACPI NVS)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]  BIOS-e820: 000000006ff66000 - 0000000080000000 (reserved)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] Notice: NX (Execute Disable) protection cannot be enabled: non-PAE kernel!
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] DMI present.
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] last_pfn = 0x6ff50 max_arch_pfn = 0x100000
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] MTRR default type: uncachable
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] MTRR fixed ranges enabled:
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   00000-9FFFF write-back
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   A0000-BFFFF uncachable
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   C0000-D3FFF write-protect
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   D4000-E3FFF uncachable
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   E4000-FFFFF write-protect
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] MTRR variable ranges enabled:
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   0 base 0000000000 mask FF80000000 write-back
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   1 disabled
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   2 disabled
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   3 disabled
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   4 disabled
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   5 disabled
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   6 disabled
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   7 disabled
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] e820 update range: 0000000000002000 - 0000000000010000 (usable) ==> (reserved)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] Scanning 1 areas for low memory corruption
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] modified physical RAM map:
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]  modified: 0000000000000000 - 0000000000001000 (reserved)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]  modified: 0000000000001000 - 0000000000002000 (usable)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]  modified: 0000000000002000 - 0000000000010000 (reserved)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]  modified: 0000000000010000 - 000000000009e000 (usable)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]  modified: 000000000009e000 - 00000000000a0000 (reserved)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]  modified: 00000000000d2000 - 0000000000100000 (reserved)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]  modified: 0000000000100000 - 000000006ff50000 (usable)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]  modified: 000000006ff50000 - 000000006ff65000 (ACPI data)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]  modified: 000000006ff65000 - 000000006ff66000 (ACPI NVS)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]  modified: 000000006ff66000 - 0000000080000000 (reserved)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]  modified: 00000000fff80000 - 0000000100000000 (reserved)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] initial memory mapped : 0 - 00c00000
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] found SMP MP-table at [c00f7c90] f7c90
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]  0000000000 - 0000400000 page 4k
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]  0000400000 - 0037400000 page 2M
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]  0037400000 - 00377fe000 page 4k
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] kernel direct mapping tables up to 377fe000 @ 15000-1a000
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] RAMDISK: 375a9000 - 37ff0000
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] Allocated new RAMDISK: 009a7000 - 013ed5d4
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] Move RAMDISK from 00000000375a9000 - 0000000037fef5d3 to 009a7000 - 013ed5d3
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] ACPI: RSDP 000f7ca0 00024 (v02 ACRSYS)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] ACPI: XSDT 6ff5e351 0005C (v01 ACRSYS ACRPRDCT 06040000  LTP 00000000)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] ACPI: SLIC 6ff64ace 00176 (v01 ACRSYS ACRPRDCT 06040000 LOHR 00000000)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] ACPI: FACP 6ff64c44 000F4 (v03 NVIDIA MCP67-M  06040000 PTL_ 000F4240)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] ACPI: DSDT 6ff5e3ad 066AD (v01 NVIDIA    MCP67 06040000 MSFT 03000000)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] ACPI: FACS 6ff65fc0 00040
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] ACPI: SSDT 6ff64d38 001C4 (v01 PTLTD  POWERNOW 06040000  LTP 00000001)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] ACPI: MCFG 6ff64efc 0003C (v01 Nvidia NVDAACPI 06040000 NVDA 00000000)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] ACPI: HPET 6ff64f38 00038 (v01 PTLTD  HPETTBL  06040000  LTP 00000001)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] ACPI: APIC 6ff64f70 00068 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] ACPI: BOOT 6ff64fd8 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] 903MB HIGHMEM available.
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] 887MB LOWMEM available.
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   low ram: 0 - 377fe000
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] Zone PFN ranges:
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   DMA      0x00000001 -> 0x00001000
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   HighMem  0x000377fe -> 0x0006ff50
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] Movable zone start PFN for each node
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] early_node_map[3] active PFN ranges
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]     0: 0x00000001 -> 0x00000002
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]     0: 0x00000010 -> 0x0000009e
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]     0: 0x00000100 -> 0x0006ff50
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] On node 0 totalpages: 458463
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] free_area_init_node: node 0, pgdat c07fffc0, node_mem_map c13ef020
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   DMA zone: 0 pages reserved
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   DMA zone: 3951 pages, LIFO batch:0
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   Normal zone: 1744 pages used for memmap
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   Normal zone: 221486 pages, LIFO batch:31
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   HighMem zone: 1807 pages used for memmap
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   HighMem zone: 229443 pages, LIFO batch:31
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] Using APIC driver default
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] Detected use of extended apic ids on hypertransport bus
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] ACPI: IRQ0 used by override.
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] ACPI: IRQ2 used by override.
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] ACPI: IRQ9 used by override.
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] nr_irqs_gsi: 40
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] early_res array is doubled to 64 at [16000 - 167ff]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000010000
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] PM: Registered nosave memory: 00000000000d2000 - 0000000000100000
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:60000000)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] PERCPU: Embedded 14 pages/cpu @c2400000 s36416 r0 d20928 u2097152
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] pcpu-alloc: s36416 r0 d20928 u2097152 alloc=1*4194304
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] pcpu-alloc: [0] 0 1 
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 454880
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-25-generic root=UUID=41dd901b-c658-4a40-87bb-89ff29a5d2c6 ro quiet splash
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] Enabling fast FPU save and restore... done.
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] Initializing CPU#0
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] allocated 9171500 bytes of page_cgroup
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] Subtract (51 early reservations)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   #2 [0000100000 - 00009a2adc]   TEXT DATA BSS
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   #3 [00009a3000 - 00009a60ed]             BRK
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   #4 [00000f7ca0 - 0000100000]   BIOS reserved
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   #5 [00000f7c90 - 00000f7ca0]    MP-table mpf
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   #6 [000009e000 - 000009e571]   BIOS reserved
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   #7 [000009e6c5 - 00000f7c90]   BIOS reserved
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   #8 [000009e571 - 000009e6c5]    MP-table mpc
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   #9 [0000010000 - 0000011000]      TRAMPOLINE
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   #10 [0000011000 - 0000015000]     ACPI WAKEUP
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   #11 [0000015000 - 0000016000]         PGTABLE
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   #12 [00009a7000 - 00013ee000]     NEW RAMDISK
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   #13 [00013ee000 - 00013ef000]         BOOTMEM
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   #14 [00013ef000 - 00021ef000]         BOOTMEM
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   #15 [00021ef000 - 00021ef004]         BOOTMEM
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   #16 [00021ef040 - 00021ef100]         BOOTMEM
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   #17 [00021ef100 - 00021ef154]         BOOTMEM
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   #18 [00021ef180 - 00021f2180]         BOOTMEM
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   #19 [00021f2180 - 00021f21d8]         BOOTMEM
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   #20 [00021f2200 - 00021f5200]         BOOTMEM
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   #21 [00021f5200 - 00021f5225]         BOOTMEM
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   #22 [00021f5240 - 00021f5267]         BOOTMEM
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   #23 [00021f5280 - 00021f5408]         BOOTMEM
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   #24 [00021f5440 - 00021f5480]         BOOTMEM
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   #25 [00021f5480 - 00021f54c0]         BOOTMEM
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   #26 [00021f54c0 - 00021f5500]         BOOTMEM
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   #27 [00021f5500 - 00021f5540]         BOOTMEM
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   #28 [00021f5540 - 00021f5580]         BOOTMEM
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   #29 [00021f5580 - 00021f55c0]         BOOTMEM
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   #30 [00021f55c0 - 00021f5600]         BOOTMEM
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   #31 [00021f5600 - 00021f5640]         BOOTMEM
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   #32 [00021f5640 - 00021f5680]         BOOTMEM
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   #33 [00021f5680 - 00021f56c0]         BOOTMEM
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   #34 [00021f56c0 - 00021f5700]         BOOTMEM
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   #35 [00021f5700 - 00021f5710]         BOOTMEM
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   #36 [00021f5740 - 00021f5750]         BOOTMEM
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   #37 [00021f5780 - 00021f57ea]         BOOTMEM
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   #38 [00021f5800 - 00021f586a]         BOOTMEM
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   #39 [0002400000 - 000240e000]         BOOTMEM
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   #40 [0002600000 - 000260e000]         BOOTMEM
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   #41 [00021f7880 - 00021f7884]         BOOTMEM
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   #42 [00021f78c0 - 00021f78c4]         BOOTMEM
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   #43 [00021f7900 - 00021f7908]         BOOTMEM
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   #44 [00021f7940 - 00021f7948]         BOOTMEM
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   #45 [00021f7980 - 00021f7a28]         BOOTMEM
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   #46 [00021f7a40 - 00021f7aa8]         BOOTMEM
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   #47 [00021f7ac0 - 00021fbac0]         BOOTMEM
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   #48 [00021fbac0 - 000227bac0]         BOOTMEM
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   #49 [000227bac0 - 00022bbac0]         BOOTMEM
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]   #50 [000260e000 - 0002ecd22c]         BOOTMEM
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:0006ff50)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] Memory: 1790212k/1834304k available (4933k kernel code, 43640k reserved, 2331k data, 688k init, 925000k highmem)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] virtual kernel memory layout:
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]       .init : 0xc0819000 - 0xc08c5000   ( 688 kB)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]       .data : 0xc05d17ce - 0xc08187a8   (2331 kB)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]       .text : 0xc0100000 - 0xc05d17ce   (4933 kB)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] Hierarchical RCU implementation.
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]     RCU-based detection of stalled CPUs is disabled.
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000]     Verbose stalled-CPUs detection is disabled.
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] NR_IRQS:2304 nr_irqs:512
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] Extended CMOS year: 2000
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] spurious 8259A interrupt: IRQ7.
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] Console: colour VGA+ 80x25
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] console [tty0] enabled
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] hpet clockevent registered
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] Fast TSC calibration using PIT
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.000000] Detected 1800.481 MHz processor.
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.004006] Calibrating delay loop (skipped), value calculated using timer frequency.. 3600.96 BogoMIPS (lpj=7201924)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.004014] pid_max: default: 32768 minimum: 301
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.004041] Security Framework initialized
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.004068] AppArmor: AppArmor initialized
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.004071] Yama: becoming mindful.
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.004152] Mount-cache hash table entries: 512
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.004326] Initializing cgroup subsys ns
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.004332] Initializing cgroup subsys cpuacct
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.004338] Initializing cgroup subsys memory
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.004351] Initializing cgroup subsys devices
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.004355] Initializing cgroup subsys freezer
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.004359] Initializing cgroup subsys net_cls
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.004391] CPU: Physical Processor ID: 0
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.004394] CPU: Processor Core ID: 0
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.004398] mce: CPU supports 5 MCE banks
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.004411] using C1E aware idle routine
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.004420] Performance Events: AMD PMU driver.
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.004431] ... version:                0
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.004434] ... bit width:              48
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.004437] ... generic registers:      4
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.004440] ... value mask:             0000ffffffffffff
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.004444] ... max period:             00007fffffffffff
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.004447] ... fixed-purpose events:   0
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.004451] ... event mask:             000000000000000f
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.009230] ACPI: Core revision 20100428
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.024012] ftrace: converting mcount calls to 0f 1f 44 00 00
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.024018] ftrace: allocating 21756 entries in 43 pages
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.028095] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.028583] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.068514] CPU0: AMD Athlon(tm) 64 X2 Dual-Core Processor TK-55 stepping 01
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.072000] Booting Node   0, Processors  #1 Ok.
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.008000] Initializing CPU#1
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.008000] System has AMD C1E enabled
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.008000] Switch to broadcast mode on CPU1
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.156064] Brought up 2 CPUs
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.156068] Total of 2 processors activated (7201.40 BogoMIPS).
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.156337] Switch to broadcast mode on CPU0
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.156337] devtmpfs: initialized
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.157204] regulator: core version 0.5
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.157244] Time: 19:46:15  Date: 03/02/11
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.157301] NET: Registered protocol family 16
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.157466] EISA bus registered
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.157473] node 0 link 0: io port [1000, fffff]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.157477] TOM: 0000000080000000 aka 2048M
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.157481] node 0 link 0: mmio [a0000, bffff]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.157485] node 0 link 0: mmio [80000000, dfffffff]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.157489] node 0 link 0: mmio [e0000000, efffffff]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.157493] node 0 link 0: mmio [f0000000, fe0bffff]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.157498] bus: [00, ff] on node 0 link 0
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.157501] bus: 00 index 0 [io  0x0000-0xffff]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.157505] bus: 00 index 1 [mem 0x000a0000-0x000bffff]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.157508] bus: 00 index 2 [mem 0x80000000-0xffffffff]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.157517] ACPI: bus type pci registered
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.157613] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.157618] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.157620] PCI: Using MMCONFIG for extended config space
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.157623] PCI: Using configuration type 1 for base access
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.158875] Trying to unpack rootfs image as initramfs...
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.158875] bio: create slab <bio-0> at 0
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.158875] ACPI: EC: Look up EC in DSDT
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.162771] ACPI: Interpreter enabled
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.162776] ACPI: (supports S0 S3 S4 S5)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.162797] ACPI: Using IOAPIC for interrupt routing
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.232122] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.232492] ACPI: No dock devices found.
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.232498] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.232788] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.233097] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7] (ignored)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.233100] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff] (ignored)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.233104] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.233108] pci_root PNP0A08:00: host bridge window [mem 0x000c0000-0x000c3fff] (ignored)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.233111] pci_root PNP0A08:00: host bridge window [mem 0x000c4000-0x000c7fff] (ignored)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.233114] pci_root PNP0A08:00: host bridge window [mem 0x000c8000-0x000cbfff] (ignored)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.233118] pci_root PNP0A08:00: host bridge window [mem 0x000cc000-0x000cffff] (ignored)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.233121] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff] (ignored)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.233125] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff] (ignored)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.233128] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff] (ignored)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.233132] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff] (ignored)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.233135] pci_root PNP0A08:00: host bridge window [mem 0x000e0000-0x000e3fff] (ignored)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.233138] pci_root PNP0A08:00: host bridge window [mem 0x000e4000-0x000e7fff] (ignored)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.233142] pci_root PNP0A08:00: host bridge window [mem 0x000e8000-0x000ebfff] (ignored)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.233145] pci_root PNP0A08:00: host bridge window [mem 0x000ec000-0x000effff] (ignored)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.233149] pci_root PNP0A08:00: host bridge window [mem 0x000f0000-0x000fffff] (ignored)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.233152] pci_root PNP0A08:00: host bridge window [mem 0xfed40000-0xfed44fff] (ignored)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.233156] pci_root PNP0A08:00: host bridge window [mem 0x80000000-0xfebfffff] (ignored)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.233309] pci 0000:00:01.0: reg 10: [io  0x1d00-0x1dff]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.233347] pci 0000:00:01.1: reg 10: [io  0x3080-0x30bf]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.233359] pci 0000:00:01.1: reg 20: [io  0x3040-0x307f]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.233364] pci 0000:00:01.1: reg 24: [io  0x3000-0x303f]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.233385] pci 0000:00:01.1: PME# supported from D3hot D3cold
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.233391] pci 0000:00:01.1: PME# disabled
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.233448] pci 0000:00:01.3: reg 10: [mem 0xf2400000-0xf247ffff]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.233528] pci 0000:00:02.0: reg 10: [mem 0xf2686000-0xf2686fff]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.233553] pci 0000:00:02.0: supports D1 D2
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.233556] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.233560] pci 0000:00:02.0: PME# disabled
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.233581] pci 0000:00:02.1: reg 10: [mem 0xf2689000-0xf26890ff]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.233610] pci 0000:00:02.1: supports D1 D2
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.233613] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.233617] pci 0000:00:02.1: PME# disabled
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.233644] pci 0000:00:04.0: reg 10: [mem 0xf2687000-0xf2687fff]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.233669] pci 0000:00:04.0: supports D1 D2
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.233671] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.233675] pci 0000:00:04.0: PME# disabled
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.233697] pci 0000:00:04.1: reg 10: [mem 0xf2689400-0xf26894ff]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.233727] pci 0000:00:04.1: supports D1 D2
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.233729] pci 0000:00:04.1: PME# supported from D0 D1 D2 D3hot D3cold
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.233733] pci 0000:00:04.1: PME# disabled
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.233768] pci 0000:00:06.0: reg 20: [io  0x30c0-0x30cf]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.233805] pci 0000:00:07.0: reg 10: [mem 0xf2680000-0xf2683fff]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.233834] pci 0000:00:07.0: PME# supported from D3hot D3cold
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.233838] pci 0000:00:07.0: PME# disabled
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.233901] pci 0000:00:09.0: reg 10: [io  0x30f0-0x30f7]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.233905] pci 0000:00:09.0: reg 14: [io  0x30e4-0x30e7]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.233910] pci 0000:00:09.0: reg 18: [io  0x30e8-0x30ef]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.233914] pci 0000:00:09.0: reg 1c: [io  0x30e0-0x30e3]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.233919] pci 0000:00:09.0: reg 20: [io  0x30d0-0x30df]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.233924] pci 0000:00:09.0: reg 24: [mem 0xf2684000-0xf2685fff]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.233969] pci 0000:00:0a.0: reg 10: [mem 0xf2688000-0xf2688fff]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.233974] pci 0000:00:0a.0: reg 14: [io  0x30f8-0x30ff]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.233979] pci 0000:00:0a.0: reg 18: [mem 0xf2689c00-0xf2689cff]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.233984] pci 0000:00:0a.0: reg 1c: [mem 0xf2689800-0xf268980f]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.234007] pci 0000:00:0a.0: supports D1 D2
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.234009] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.234014] pci 0000:00:0a.0: PME# disabled
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.234056] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.234059] pci 0000:00:0c.0: PME# disabled
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.234095] pci 0000:00:0d.0: PME# supported from D0 D1 D2 D3hot D3cold
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.234098] pci 0000:00:0d.0: PME# disabled
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.234121] pci 0000:00:12.0: reg 10: [mem 0xf1000000-0xf1ffffff]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.234128] pci 0000:00:12.0: reg 14: [mem 0xd0000000-0xdfffffff 64bit pref]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.234134] pci 0000:00:12.0: reg 1c: [mem 0xf0000000-0xf0ffffff 64bit]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.234141] pci 0000:00:12.0: reg 30: [mem 0x00000000-0x0001ffff pref]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.234241] PCI: peer root bus 00 res updated from pci conf
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.234283] pci 0000:01:04.0: proprietary Ricoh MMC controller disabled (via firewire function)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.234287] pci 0000:01:04.0: MMC cards are now supported by standard SDHCI controller
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.234295] pci 0000:01:04.0: reg 10: [mem 0xf2300000-0xf23007ff]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.234330] pci 0000:01:04.0: PME# supported from D0 D3hot D3cold
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.234334] pci 0000:01:04.0: PME# disabled
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.234358] pci 0000:01:04.1: reg 10: [mem 0xf2300800-0xf23008ff]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.234393] pci 0000:01:04.1: supports D1 D2
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.234395] pci 0000:01:04.1: PME# supported from D0 D1 D2 D3hot D3cold
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.234399] pci 0000:01:04.1: PME# disabled
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.234423] pci 0000:01:04.2: reg 10: [mem 0xf2301000-0xf23010ff]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.234458] pci 0000:01:04.2: supports D1 D2
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.234460] pci 0000:01:04.2: PME# supported from D0 D1 D2 D3hot D3cold
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.234465] pci 0000:01:04.2: PME# disabled
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.234488] pci 0000:01:04.3: reg 10: [mem 0xf2301400-0xf23014ff]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.234522] pci 0000:01:04.3: supports D1 D2
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.234525] pci 0000:01:04.3: PME# supported from D0 D1 D2 D3hot D3cold
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.234529] pci 0000:01:04.3: PME# disabled
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.234566] pci 0000:00:08.0: PCI bridge to [bus 01-01] (subtractive decode)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.234571] pci 0000:00:08.0:   bridge window [io  0xf000-0x0000] (disabled)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.234575] pci 0000:00:08.0:   bridge window [mem 0xf2300000-0xf23fffff]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.234580] pci 0000:00:08.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.234583] pci 0000:00:08.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.234587] pci 0000:00:08.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.234590] pci 0000:00:08.0:   bridge window [mem 0x80000000-0xffffffff] (subtractive decode)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.234617] pci 0000:00:0c.0: PCI bridge to [bus 03-04]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.234622] pci 0000:00:0c.0:   bridge window [io  0x4000-0x4fff]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.234625] pci 0000:00:0c.0:   bridge window [mem 0xf2000000-0xf21fffff]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.234630] pci 0000:00:0c.0:   bridge window [mem 0xf2800000-0xf29fffff 64bit pref]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.234680] pci 0000:05:00.0: reg 10: [mem 0xf2200000-0xf220ffff 64bit]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.234740] pci 0000:05:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.234750] pci 0000:00:0d.0: PCI bridge to [bus 05-05]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.234754] pci 0000:00:0d.0:   bridge window [io  0xf000-0x0000] (disabled)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.234758] pci 0000:00:0d.0:   bridge window [mem 0xf2200000-0xf22fffff]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.234763] pci 0000:00:0d.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.234772] pci_bus 0000:00: on NUMA node 0
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.234776] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.234894] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.234919] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.234955] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.269797] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 11) *10
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.270010] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 *11)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.270221] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 11) *0, disabled.
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.270430] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 11) *0, disabled.
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.270640] ACPI: PCI Interrupt Link [LK1E] (IRQs 16) *0, disabled.
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.270848] ACPI: PCI Interrupt Link [LK2E] (IRQs 17) *0, disabled.
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.271065] ACPI: PCI Interrupt Link [LK3E] (IRQs 18) *0, disabled.
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.271273] ACPI: PCI Interrupt Link [LK4E] (IRQs 19) *10
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.271482] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *10
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.271691] ACPI: PCI Interrupt Link [LUS0] (IRQs 20 21 22 23) *11
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.271901] ACPI: PCI Interrupt Link [LUS2] (IRQs 20 21 22 23) *7
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.272131] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *11
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.272341] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *10
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.272551] ACPI: PCI Interrupt Link [LGPU] (IRQs 17) *10
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.272760] ACPI: PCI Interrupt Link [LPID] (IRQs 20 21 22 23) *0, disabled.
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.272970] ACPI: PCI Interrupt Link [LSI0] (IRQs 20 21 22 23) *5
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.273185] ACPI: PCI Interrupt Link [Z00N] (IRQs 20 21 22 23) *10
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.273401] ACPI: PCI Interrupt Link [Z00O] (IRQs 20 21 22 23) *11
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.273611] ACPI: PCI Interrupt Link [LPMU] (IRQs 18) *11
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.273668] HEST: Table is not found!
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.273793] vgaarb: device added: PCI:0000:00:12.0,decodes=io+mem,owns=io+mem,locks=none
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.273802] vgaarb: loaded
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.274009] SCSI subsystem initialized
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.276287] libata version 3.00 loaded.
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.276287] usbcore: registered new interface driver usbfs
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.276287] usbcore: registered new interface driver hub
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.276287] usbcore: registered new device driver usb
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.276287] ACPI: WMI: Mapper loaded
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.276287] PCI: Using ACPI for IRQ routing
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.276287] PCI: pci_cache_line_size set to 64 bytes
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.276287] reserve RAM buffer: 0000000000002000 - 000000000000ffff 
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.276287] reserve RAM buffer: 000000000009e000 - 000000000009ffff 
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.276287] reserve RAM buffer: 000000006ff50000 - 000000006fffffff 
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.276287] NetLabel: Initializing
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.276287] NetLabel:  domain hash size = 128
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.276287] NetLabel:  protocols = UNLABELED CIPSOv4
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.276287] NetLabel:  unlabeled traffic allowed by default
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.276287] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.276287] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.276287] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.284215] Switching to clocksource hpet
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.299158] AppArmor: AppArmor Filesystem Enabled
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.299183] pnp: PnP ACPI init
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.299209] ACPI: bus type pnp registered
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.330218] pnp: PnP ACPI: found 13 devices
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.330221] ACPI: ACPI bus type pnp unregistered
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.330225] PnPBIOS: Disabled by ACPI PNP
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.330241] system 00:01: [io  0x0360-0x0361] has been reserved
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.330245] system 00:01: [io  0x04d0-0x04d1] has been reserved
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.330254] system 00:07: [mem 0xe0000000-0xefffffff] has been reserved
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.330261] system 00:0a: [io  0x1000-0x107f] has been reserved
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.330265] system 00:0a: [io  0x1080-0x10ff] has been reserved
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.330268] system 00:0a: [io  0x1400-0x147f] has been reserved
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.330272] system 00:0a: [io  0x1480-0x14ff] has been reserved
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.330275] system 00:0a: [io  0x1800-0x187f] has been reserved
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.330279] system 00:0a: [io  0x1880-0x18ff] has been reserved
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.330286] system 00:0c: [mem 0xffc00000-0xffffffff] could not be reserved
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.330290] system 00:0c: [mem 0xfec00000-0xfec00fff] could not be reserved
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.330294] system 00:0c: [mem 0xfee00000-0xfeefffff] could not be reserved
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.330298] system 00:0c: [mem 0xfed00000-0xfed00fff] has been reserved
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.330302] system 00:0c: [mem 0xfef00000-0xfef00fff] has been reserved
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.366714] pci 0000:00:12.0: BAR 6: assigned [mem 0x80000000-0x8001ffff pref]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.366720] pci 0000:00:08.0: PCI bridge to [bus 01-01]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.366723] pci 0000:00:08.0:   bridge window [io  disabled]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.366728] pci 0000:00:08.0:   bridge window [mem 0xf2300000-0xf23fffff]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.366732] pci 0000:00:08.0:   bridge window [mem pref disabled]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.366737] pci 0000:00:0c.0: PCI bridge to [bus 03-04]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.366740] pci 0000:00:0c.0:   bridge window [io  0x4000-0x4fff]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.366744] pci 0000:00:0c.0:   bridge window [mem 0xf2000000-0xf21fffff]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.366748] pci 0000:00:0c.0:   bridge window [mem 0xf2800000-0xf29fffff 64bit pref]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.366753] pci 0000:00:0d.0: PCI bridge to [bus 05-05]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.366755] pci 0000:00:0d.0:   bridge window [io  disabled]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.366759] pci 0000:00:0d.0:   bridge window [mem 0xf2200000-0xf22fffff]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.366763] pci 0000:00:0d.0:   bridge window [mem pref disabled]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.366774] pci 0000:00:08.0: setting latency timer to 64
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.366781] pci 0000:00:0c.0: setting latency timer to 64
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.366788] pci 0000:00:0d.0: setting latency timer to 64
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.366793] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.366796] pci_bus 0000:00: resource 5 [mem 0x000a0000-0x000bffff]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.366799] pci_bus 0000:00: resource 6 [mem 0x80000000-0xffffffff]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.366803] pci_bus 0000:01: resource 1 [mem 0xf2300000-0xf23fffff]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.366806] pci_bus 0000:01: resource 4 [io  0x0000-0xffff]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.366809] pci_bus 0000:01: resource 5 [mem 0x000a0000-0x000bffff]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.366812] pci_bus 0000:01: resource 6 [mem 0x80000000-0xffffffff]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.366816] pci_bus 0000:03: resource 0 [io  0x4000-0x4fff]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.366819] pci_bus 0000:03: resource 1 [mem 0xf2000000-0xf21fffff]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.366822] pci_bus 0000:03: resource 2 [mem 0xf2800000-0xf29fffff 64bit pref]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.366825] pci_bus 0000:05: resource 1 [mem 0xf2200000-0xf22fffff]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.366878] NET: Registered protocol family 2
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.366956] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.367292] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.368001] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.368361] TCP: Hash tables configured (established 131072 bind 65536)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.368365] TCP reno registered
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.368371] UDP hash table entries: 512 (order: 2, 16384 bytes)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.368383] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.368493] NET: Registered protocol family 1
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.368678] pci 0000:00:00.0: Found enabled HT MSI Mapping
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.368734] pci 0000:00:00.0: Found enabled HT MSI Mapping
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.368795] pci 0000:00:00.0: Found enabled HT MSI Mapping
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.368863] pci 0000:00:00.0: Found enabled HT MSI Mapping
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.368934] pci 0000:00:00.0: Found enabled HT MSI Mapping
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.369041] pci 0000:00:00.0: Found enabled HT MSI Mapping
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.369049] pci 0000:00:12.0: Boot video device
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.369072] PCI: CLS 64 bytes, default 64
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.369105] Simple Boot Flag at 0x36 set to 0x1
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.369340] cpufreq-nforce2: No nForce2 chipset.
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.369378] Scanning for low memory corruption every 60 seconds
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.369562] audit: initializing netlink socket (disabled)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.369575] type=2000 audit(1299095174.368:1): initialized
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.382290] highmem bounce pool size: 64 pages
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.382297] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.384393] VFS: Disk quotas dquot_6.5.2
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.384479] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.385363] fuse init (API version 7.14)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.385494] msgmni has been set to 1689
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.385882] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.385887] io scheduler noop registered
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.385889] io scheduler deadline registered
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.385915] io scheduler cfq registered (default)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.386066] pcieport 0000:00:0c.0: setting latency timer to 64
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.386089]   alloc irq_desc for 40 on node -1
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.386091]   alloc kstat_irqs on node -1
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.386102] pcieport 0000:00:0c.0: irq 40 for MSI/MSI-X
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.386164] pcieport 0000:00:0d.0: setting latency timer to 64
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.386181]   alloc irq_desc for 41 on node -1
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.386183]   alloc kstat_irqs on node -1
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.386189] pcieport 0000:00:0d.0: irq 41 for MSI/MSI-X
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.386275] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.386307] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.394303] ACPI: AC Adapter [ACAD] (on-line)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.394391] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.403788] ACPI: Lid Switch [LID]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.403842] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.403848] ACPI: Sleep Button [SLPB]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.403924] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input2
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.403929] ACPI: Power Button [PWRB]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.403980] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.403984] ACPI: Power Button [PWRF]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.404297] ACPI: acpi_idle registered with cpuidle
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.404390] ACPI: processor limited to max C-state 1
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.468297] ACPI: Invalid active0 threshold
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.480733] thermal LNXTHERM:01: registered as thermal_zone0
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.480742] ACPI: Thermal Zone [THRM] (79 C)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.480887] ERST: Table is not found!
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.481248] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.483079] brd: module loaded
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.483780] loop: module loaded
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.484171] pata_acpi 0000:00:06.0: setting latency timer to 64
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.484567] ACPI: PCI Interrupt Link [LSI0] enabled at IRQ 23
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.484573]   alloc irq_desc for 23 on node -1
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.484576]   alloc kstat_irqs on node -1
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.484588] pata_acpi 0000:00:09.0: PCI INT A -> Link[LSI0] -> GSI 23 (level, low) -> IRQ 23
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.484608] pata_acpi 0000:00:09.0: setting latency timer to 64
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.484616] pata_acpi 0000:00:09.0: PCI INT A disabled
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.485068] Fixed MDIO Bus: probed
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.485115] PPP generic driver version 2.4.2
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.485184] tun: Universal TUN/TAP device driver, 1.6
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.485187] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.485301] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.485658] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 22
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.485663]   alloc irq_desc for 22 on node -1
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.485665]   alloc kstat_irqs on node -1
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.485675] ehci_hcd 0000:00:02.1: PCI INT B -> Link[LUS2] -> GSI 22 (level, low) -> IRQ 22
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.485698] ehci_hcd 0000:00:02.1: setting latency timer to 64
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.485702] ehci_hcd 0000:00:02.1: EHCI Host Controller
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.485750] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.485779] ehci_hcd 0000:00:02.1: debug port 1
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.485787] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.485814] ehci_hcd 0000:00:02.1: irq 22, io mem 0xf2689000
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.485984] isapnp: Scanning for PnP cards...
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.507392] Freeing initrd memory: 10524k freed
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.514558] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.514777] hub 1-0:1.0: USB hub found
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.514784] hub 1-0:1.0: 5 ports detected
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.515237] ACPI: PCI Interrupt Link [Z00O] enabled at IRQ 21
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.515244]   alloc irq_desc for 21 on node -1
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.515247]   alloc kstat_irqs on node -1
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.515260] ehci_hcd 0000:00:04.1: PCI INT B -> Link[Z00O] -> GSI 21 (level, low) -> IRQ 21
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.515284] ehci_hcd 0000:00:04.1: setting latency timer to 64
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.515288] ehci_hcd 0000:00:04.1: EHCI Host Controller
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.515346] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 2
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.515374] ehci_hcd 0000:00:04.1: debug port 1
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.515383] ehci_hcd 0000:00:04.1: cache line size of 64 is not supported
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.515410] ehci_hcd 0000:00:04.1: irq 21, io mem 0xf2689400
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.524019] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.524162] hub 2-0:1.0: USB hub found
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.524168] hub 2-0:1.0: 5 ports detected
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.524260] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.524617] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 20
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.524621]   alloc irq_desc for 20 on node -1
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.524624]   alloc kstat_irqs on node -1
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.524635] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUS0] -> GSI 20 (level, low) -> IRQ 20
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.524654] ohci_hcd 0000:00:02.0: setting latency timer to 64
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.524657] ohci_hcd 0000:00:02.0: OHCI Host Controller
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.524721] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 3
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.524754] ohci_hcd 0000:00:02.0: irq 20, io mem 0xf2686000
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.540531] ACPI: EC: GPE storm detected, transactions will use polling mode
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.582156] hub 3-0:1.0: USB hub found
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.582162] hub 3-0:1.0: 5 ports detected
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.582575] ACPI: PCI Interrupt Link [Z00N] enabled at IRQ 23
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.582580] ohci_hcd 0000:00:04.0: PCI INT A -> Link[Z00N] -> GSI 23 (level, low) -> IRQ 23
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.582599] ohci_hcd 0000:00:04.0: setting latency timer to 64
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.582603] ohci_hcd 0000:00:04.0: OHCI Host Controller
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.582654] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 4
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.582688] ohci_hcd 0000:00:04.0: irq 23, io mem 0xf2687000
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.638170] hub 4-0:1.0: USB hub found
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.638178] hub 4-0:1.0: 5 ports detected
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.638271] uhci_hcd: USB Universal Host Controller Interface driver
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.638387] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.667411] serio: i8042 KBD port at 0x60,0x64 irq 1
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.667420] serio: i8042 AUX port at 0x60,0x64 irq 12
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.667511] mice: PS/2 mouse device common for all mice
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.667690] rtc_cmos 00:04: RTC can wake from S4
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.667738] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.667778] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.667949] device-mapper: uevent: version 1.0.3
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.668142] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [email]dm-devel@redhat.com[/email]
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.669534] device-mapper: multipath: version 1.1.1 loaded
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.669537] device-mapper: multipath round-robin: version 1.0.0 loaded
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.669699] EISA: Probing bus 0 at eisa.0
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.669703] EISA: Cannot allocate resource for mainboard
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.669706] Cannot allocate resource for EISA slot 1
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.669709] Cannot allocate resource for EISA slot 2
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.669712] Cannot allocate resource for EISA slot 3
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.669714] Cannot allocate resource for EISA slot 4
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.669717] Cannot allocate resource for EISA slot 5
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.669720] Cannot allocate resource for EISA slot 6
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.669723] Cannot allocate resource for EISA slot 7
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.669725] Cannot allocate resource for EISA slot 8
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.669728] EISA: Detected 0 cards.
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.669814] cpuidle: using governor ladder
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.669817] cpuidle: using governor menu
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.670179] TCP cubic registered
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.670391] NET: Registered protocol family 10
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.670842] lo: Disabled Privacy Extensions
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.671132] NET: Registered protocol family 17
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.671177] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual-Core Processor TK-55 (2 cpu cores) (version 2.20.00)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.671228] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x13
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.671231] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0x14
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.671234] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x1a
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.671287] Using IPI No-Shortcut mode
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.671421] PM: Resume from disk failed.
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.671438] registered taskstats version 1
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.671756]   Magic number: 3:382:798
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.671877] rtc_cmos 00:04: setting system clock to 2011-03-02 19:46:16 UTC (1299095176)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.671881] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.671883] EDD information not available.
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.693124] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.842655] isapnp: No Plug & Play device found
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.842684] Freeing unused kernel memory: 688k freed
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.843239] Write protecting the kernel text: 4936k
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.843284] Write protecting the kernel read-only data: 1976k
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    0.868695] udev[76]: starting version 163
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    1.072036] usb 3-2: new low speed USB device using ohci_hcd and address 2
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    1.188212] ACPI: Battery Slot [BAT1] (battery present)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    1.301375] usbcore: registered new interface driver hiddev
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    1.307610] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:02.0/usb3/3-2/3-2:1.0/input/input5
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    1.307758] generic-usb 0003:046D:C018.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:00:02.0-2/input0
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    1.307790] usbcore: registered new interface driver usbhid
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    1.307792] usbhid: USB HID core driver
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    1.567617] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    1.599667] sdhci: Secure Digital Host Controller Interface driver
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    1.599672] sdhci: Copyright(c) Pierre Ossman
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    1.601517] sdhci-pci 0000:01:04.1: SDHCI controller found [1180:0822] (rev 22)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    1.611562] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 22
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    1.611577] forcedeth 0000:00:0a.0: PCI INT A -> Link[LMAC] -> GSI 22 (level, low) -> IRQ 22
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    1.611585] forcedeth 0000:00:0a.0: setting latency timer to 64
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    1.613260] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 11
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    1.613280] sdhci-pci 0000:01:04.1: PCI INT B -> Link[LNK2] -> GSI 11 (level, low) -> IRQ 11
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    1.614322] sdhci-pci 0000:01:04.1: Will use DMA mode even though HW doesn't fully claim to support it.
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    1.615492] Registered led device: mmc0::
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    1.616604] mmc0: SDHCI controller on PCI [0000:01:04.1] using DMA
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    1.617070] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 11
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    1.617079] firewire_ohci 0000:01:04.0: PCI INT A -> Link[LNK1] -> GSI 11 (level, low) -> IRQ 11
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    1.752030] firewire_ohci: Added fw-ohci device 0000:01:04.0, OHCI v1.0, 4 IR + 4 IT contexts, quirks 0x0
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    2.133201] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1b:38:c8:3f:3f
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    2.133207] forcedeth 0000:00:0a.0: highdma pwrctl mgmt gbit lnktim msi desc-v3
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    2.133240] pata_amd 0000:00:06.0: version 0.4.1
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    2.133300] pata_amd 0000:00:06.0: setting latency timer to 64
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    2.133410] scsi0 : pata_amd
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    2.133561] scsi1 : pata_amd
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    2.134040] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x30c0 irq 14
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    2.134044] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x30c8 irq 15
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    2.134112] ahci 0000:00:09.0: version 3.0
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    2.134127] ahci 0000:00:09.0: PCI INT A -> Link[LSI0] -> GSI 23 (level, low) -> IRQ 23
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    2.134164] ahci 0000:00:09.0: controller can do NCQ, turning on CAP_NCQ
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    2.134167] ahci 0000:00:09.0: controller can't do PMP, turning off CAP_PMP
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    2.134240] ahci 0000:00:09.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl IDE mode
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    2.134246] ahci 0000:00:09.0: flags: 64bit ncq sntf led clo pio slum part 
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    2.134251] ahci 0000:00:09.0: setting latency timer to 64
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    2.135493] scsi2 : ahci
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    2.135613] scsi3 : ahci
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    2.135720] scsi4 : ahci
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    2.135830] scsi5 : ahci
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    2.135998] ata3: SATA max UDMA/133 irq_stat 0x00400040, connection status changed irq 23
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    2.136026] ata4: SATA max UDMA/133 abar m8192@0xf2684000 port 0xf2684180 irq 23
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    2.136030] ata5: SATA max UDMA/133 abar m8192@0xf2684000 port 0xf2684200 irq 23
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    2.136035] ata6: SATA max UDMA/133 abar m8192@0xf2684000 port 0xf2684280 irq 23
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    2.244155] firewire_core: created device fw0: GUID 00023f7cba405e1a, S400
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    2.296328] ata1.00: ATAPI: HL-DT-ST DVDRAM GSA-T40N, JQ01, max UDMA/33
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    2.296358] ata1: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc000c600) ACPI=0x701f (60:600:0x13)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    2.312273] ata1.00: configured for UDMA/33
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    2.317819] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T40N  JQ01 PQ: 0 ANSI: 5
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    2.321742] sr0: scsi3-mmc drive: 62x/62x writer dvd-ram cd/rw xa/form2 cdda tray
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    2.321747] Uniform CD-ROM driver Revision: 3.20
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    2.321908] sr 0:0:0:0: Attached scsi CD-ROM sr0
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    2.322003] sr 0:0:0:0: Attached scsi generic sg0 type 5
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    2.322121] ata2: port disabled. ignoring.
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    2.456034] ata5: SATA link down (SStatus 0 SControl 300)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    2.456038] ata4: SATA link down (SStatus 0 SControl 300)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    2.456065] ata6: SATA link down (SStatus 0 SControl 300)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    2.860032] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    2.860465] ata3.00: ATA-7: FUJITSU MHW2160BH PL, 891F, max UDMA/100
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    2.860470] ata3.00: 312581808 sectors, multi 16: LBA48 
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    2.861029] ata3.00: configured for UDMA/100
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    2.861201] scsi 2:0:0:0: Direct-Access     ATA      FUJITSU MHW2160B 891F PQ: 0 ANSI: 5
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    2.861411] sd 2:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    2.861422] sd 2:0:0:0: Attached scsi generic sg1 type 0
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    2.861597] sd 2:0:0:0: [sda] Write Protect is off
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    2.861601] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    2.861654] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    2.861884]  sda: sda1 sda2 sda3 < sda5 sda6 >
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    2.942913] sd 2:0:0:0: [sda] Attached SCSI disk
Mar  2 19:46:36 ben-Aspire-5520 kernel: [    3.542493] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [   19.424573] Adding 3073020k swap on /dev/sda6.  Priority:-1 extents:1 across:3073020k 
Mar  2 19:46:36 ben-Aspire-5520 kernel: [   19.451709] udev[382]: starting version 163
Mar  2 19:46:36 ben-Aspire-5520 kernel: [   19.606534] lp: driver loaded but no devices found
Mar  2 19:46:36 ben-Aspire-5520 kernel: [   19.715781] [Firmware Bug]: ACPI(IGPU) defines _DOD but not _DOS
Mar  2 19:46:36 ben-Aspire-5520 kernel: [   19.716851] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input6
Mar  2 19:46:36 ben-Aspire-5520 kernel: [   19.716975] ACPI: Video Device [IGPU] (multi-head: yes  rom: no  post: no)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [   19.718505] lirc_dev: IR Remote Control driver registered, major 249 
Mar  2 19:46:36 ben-Aspire-5520 kernel: [   19.718699] lirc_ene0100: module is from the staging directory, the quality is unknown, you have been warned.
Mar  2 19:46:36 ben-Aspire-5520 kernel: [   19.719694] enecir 00:06: lirc_dev: driver enecir registered at minor = 0
Mar  2 19:46:36 ben-Aspire-5520 kernel: [   19.719758] enecir: KB3926B detected
Mar  2 19:46:36 ben-Aspire-5520 kernel: [   19.719761] enecir: chip is 0x3909 - 0x24, 0xc0
Mar  2 19:46:36 ben-Aspire-5520 kernel: [   19.719764] enecir: driver has been succesfully loaded
Mar  2 19:46:36 ben-Aspire-5520 kernel: [   19.950648] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
Mar  2 19:46:36 ben-Aspire-5520 kernel: [   19.953435] i2c i2c-0: nForce2 SMBus adapter at 0x3040
Mar  2 19:46:36 ben-Aspire-5520 kernel: [   19.953474] i2c i2c-1: nForce2 SMBus adapter at 0x3000
Mar  2 19:46:36 ben-Aspire-5520 kernel: [   19.999261] Linux agpgart interface v0.103
Mar  2 19:46:36 ben-Aspire-5520 kernel: [   20.007317] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
Mar  2 19:46:36 ben-Aspire-5520 kernel: [   20.062624] cfg80211: Calling CRDA to update world regulatory domain
Mar  2 19:46:36 ben-Aspire-5520 kernel: [   20.070808] r852 0000:01:04.3: PCI INT B -> Link[LNK2] -> GSI 11 (level, low) -> IRQ 11
Mar  2 19:46:36 ben-Aspire-5520 kernel: [   20.118970] r852: driver loaded succesfully
Mar  2 19:46:36 ben-Aspire-5520 kernel: [   20.121537] type=1400 audit(1299113195.945:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=696 comm="apparmor_parser"
Mar  2 19:46:36 ben-Aspire-5520 kernel: [   20.121877] type=1400 audit(1299113195.945:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=696 comm="apparmor_parser"
Mar  2 19:46:36 ben-Aspire-5520 kernel: [   20.122077] type=1400 audit(1299113195.945:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=696 comm="apparmor_parser"
Mar  2 19:46:36 ben-Aspire-5520 kernel: [   20.125729] type=1400 audit(1299113195.949:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=712 comm="apparmor_parser"
Mar  2 19:46:36 ben-Aspire-5520 kernel: [   20.126077] type=1400 audit(1299113195.949:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=712 comm="apparmor_parser"
Mar  2 19:46:36 ben-Aspire-5520 kernel: [   20.126280] type=1400 audit(1299113195.949:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=712 comm="apparmor_parser"
Mar  2 19:46:36 ben-Aspire-5520 kernel: [   20.186343] ACPI: PCI Interrupt Link [LK4E] enabled at IRQ 19
Mar  2 19:46:36 ben-Aspire-5520 kernel: [   20.186352]   alloc irq_desc for 19 on node -1
Mar  2 19:46:36 ben-Aspire-5520 kernel: [   20.186355]   alloc kstat_irqs on node -1
Mar  2 19:46:36 ben-Aspire-5520 kernel: [   20.186368] ath5k 0000:05:00.0: PCI INT A -> Link[LK4E] -> GSI 19 (level, low) -> IRQ 19
Mar  2 19:46:36 ben-Aspire-5520 kernel: [   20.186378] ath5k 0000:05:00.0: setting latency timer to 64
Mar  2 19:46:36 ben-Aspire-5520 kernel: [   20.186437] ath5k 0000:05:00.0: registered as 'phy0'
Mar  2 19:46:36 ben-Aspire-5520 kernel: [   20.298434] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
Mar  2 19:46:36 ben-Aspire-5520 kernel: [   20.298443] HDA Intel 0000:00:07.0: PCI INT A -> Link[LAZA] -> GSI 21 (level, low) -> IRQ 21
Mar  2 19:46:36 ben-Aspire-5520 kernel: [   20.298447] hda_intel: Disable MSI for Nvidia chipset
Mar  2 19:46:36 ben-Aspire-5520 kernel: [   20.298490] HDA Intel 0000:00:07.0: setting latency timer to 64
Mar  2 19:46:36 ben-Aspire-5520 kernel: [   20.300123] cfg80211: World regulatory domain updated:
Mar  2 19:46:36 ben-Aspire-5520 kernel: [   20.300128]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [   20.300132]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [   20.300136]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [   20.300139]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [   20.300143]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [   20.300146]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [   20.678011] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input7
Mar  2 19:46:36 ben-Aspire-5520 kernel: [   20.681155] ath: EEPROM regdomain: 0x65
Mar  2 19:46:36 ben-Aspire-5520 kernel: [   20.681160] ath: EEPROM indicates we should expect a direct regpair map
Mar  2 19:46:36 ben-Aspire-5520 kernel: [   20.681165] ath: Country alpha2 being used: 00
Mar  2 19:46:36 ben-Aspire-5520 kernel: [   20.681167] ath: Regpair used: 0x65
Mar  2 19:46:36 ben-Aspire-5520 kernel: [   20.696572] phy0: Selected rate control algorithm 'minstrel'
Mar  2 19:46:36 ben-Aspire-5520 kernel: [   20.697488] Registered led device: ath5k-phy0::rx
Mar  2 19:46:36 ben-Aspire-5520 kernel: [   20.697512] Registered led device: ath5k-phy0::tx
Mar  2 19:46:36 ben-Aspire-5520 kernel: [   20.697517] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
Mar  2 19:46:36 ben-Aspire-5520 kernel: [   20.712749] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input8
Mar  2 19:46:36 ben-Aspire-5520 kernel: [   20.748707] nvidia: module license 'NVIDIA' taints kernel.
Mar  2 19:46:36 ben-Aspire-5520 kernel: [   20.748714] Disabling lock debugging due to kernel taint
Mar  2 19:46:37 ben-Aspire-5520 kernel: [   21.297369] type=1400 audit(1299113197.121:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=875 comm="apparmor_parser"
Mar  2 19:46:37 ben-Aspire-5520 kernel: [   21.297717] type=1400 audit(1299113197.121:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=875 comm="apparmor_parser"
Mar  2 19:46:37 ben-Aspire-5520 kernel: [   21.297914] type=1400 audit(1299113197.121:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=875 comm="apparmor_parser"
Mar  2 19:46:37 ben-Aspire-5520 kernel: [   21.300973] type=1400 audit(1299113197.121:11): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=874 comm="apparmor_parser"
Mar  2 19:46:37 ben-Aspire-5520 kernel: [   21.439614] ACPI: PCI Interrupt Link [LGPU] enabled at IRQ 17
Mar  2 19:46:37 ben-Aspire-5520 kernel: [   21.439624]   alloc irq_desc for 17 on node -1
Mar  2 19:46:37 ben-Aspire-5520 kernel: [   21.439627]   alloc kstat_irqs on node -1
Mar  2 19:46:37 ben-Aspire-5520 kernel: [   21.439640] nvidia 0000:00:12.0: PCI INT A -> Link[LGPU] -> GSI 17 (level, low) -> IRQ 17
Mar  2 19:46:37 ben-Aspire-5520 kernel: [   21.439650] nvidia 0000:00:12.0: setting latency timer to 64
Mar  2 19:46:37 ben-Aspire-5520 kernel: [   21.439657] vgaarb: device changed decodes: PCI:0000:00:12.0,olddecodes=io+mem,decodes=none:owns=io+mem
Mar  2 19:46:37 ben-Aspire-5520 kernel: [   21.440258] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.28  Wed Sep 29 09:47:25 PDT 2010
Mar  2 19:46:37 ben-Aspire-5520 kernel: [   21.519920]   alloc irq_desc for 42 on node -1
Mar  2 19:46:37 ben-Aspire-5520 kernel: [   21.519925]   alloc kstat_irqs on node -1
Mar  2 19:46:37 ben-Aspire-5520 kernel: [   21.519938] forcedeth 0000:00:0a.0: irq 42 for MSI/MSI-X
Mar  2 19:46:37 ben-Aspire-5520 kernel: [   21.548776] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar  2 19:46:37 ben-Aspire-5520 kernel: [   22.029514] ppdev: user-space parallel port driver
Mar  2 19:46:45 ben-Aspire-5520 kernel: [   28.518338] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
Mar  2 19:46:49 ben-Aspire-5520 kernel: [   31.713031] eth0: no IPv6 routers present
Mar  2 19:46:50 ben-Aspire-5520 kernel: [   32.863095] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
Mar  2 19:47:46 ben-Aspire-5520 kernel: [   89.508053] Clocksource tsc unstable (delta = -165093417 ns)
Mar  2 21:03:29 ben-Aspire-5520 kernel: [ 4632.004907] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
Mar  2 21:03:29 ben-Aspire-5520 kernel: [ 4632.012980] SGI XFS Quota Management subsystem
Mar  2 21:03:29 ben-Aspire-5520 kernel: [ 4632.048202] JFS: nTxBlock = 8192, nTxLock = 65536
Mar  2 21:03:29 ben-Aspire-5520 kernel: [ 4632.127982] NTFS driver 2.1.29 [Flags: R/O MODULE].
Mar  2 21:03:29 ben-Aspire-5520 kernel: [ 4632.219192] QNX4 filesystem 0.2.3 registered.
Mar  2 21:03:29 ben-Aspire-5520 kernel: [ 4632.352609] Btrfs loaded
Mar  2 21:59:59 ben-Aspire-5520 kernel: [ 8021.812537] ath5k phy0: gain calibration timeout (2472MHz)
Mar  2 21:59:59 ben-Aspire-5520 kernel: [ 8022.262074] ath5k phy0: gain calibration timeout (2412MHz)
Mar  2 22:00:58 ben-Aspire-5520 kernel: [ 8081.392943] ath5k phy0: gain calibration timeout (2412MHz)
Mar  2 22:00:59 ben-Aspire-5520 kernel: [ 8081.838441] ath5k phy0: gain calibration timeout (2417MHz)
Mar  2 22:00:59 ben-Aspire-5520 kernel: [ 8082.226183] ath5k phy0: gain calibration timeout (2422MHz)
Mar  2 22:00:59 ben-Aspire-5520 kernel: [ 8082.613200] ath5k phy0: gain calibration timeout (2427MHz)
Mar  2 22:01:00 ben-Aspire-5520 kernel: [ 8083.001064] ath5k phy0: gain calibration timeout (2432MHz)
Mar  2 22:01:00 ben-Aspire-5520 kernel: [ 8083.381060] ath5k phy0: gain calibration timeout (2437MHz)
Mar  2 22:01:01 ben-Aspire-5520 kernel: [ 8083.761591] ath5k phy0: gain calibration timeout (2442MHz)
Mar  2 22:01:01 ben-Aspire-5520 kernel: [ 8084.142041] ath5k phy0: gain calibration timeout (2447MHz)
Mar  2 22:01:01 ben-Aspire-5520 kernel: [ 8084.561747] ath5k phy0: gain calibration timeout (2452MHz)
Mar  2 22:01:02 ben-Aspire-5520 kernel: [ 8085.237963] ath5k phy0: gain calibration timeout (2457MHz)
Mar  2 22:01:04 ben-Aspire-5520 kernel: [ 8087.334586] net_ratelimit: 2 callbacks suppressed
Mar  2 22:01:04 ben-Aspire-5520 kernel: [ 8087.334604] ath5k phy0: gain calibration timeout (2472MHz)
Mar  2 22:01:04 ben-Aspire-5520 kernel: [ 8087.485162] ath5k phy0: gain calibration timeout (2412MHz)
Mar  2 22:01:58 ben-Aspire-5520 kernel: [ 8141.399483] ath5k phy0: gain calibration timeout (2412MHz)
Mar  2 22:01:59 ben-Aspire-5520 kernel: [ 8142.091543] ath5k phy0: gain calibration timeout (2417MHz)
Mar  2 22:01:59 ben-Aspire-5520 kernel: [ 8142.522439] ath5k phy0: gain calibration timeout (2422MHz)
Mar  2 22:02:00 ben-Aspire-5520 kernel: [ 8142.907785] ath5k phy0: gain calibration timeout (2427MHz)
Mar  2 22:02:00 ben-Aspire-5520 kernel: [ 8143.309190] ath5k phy0: gain calibration timeout (2432MHz)
Mar  2 22:02:01 ben-Aspire-5520 kernel: [ 8143.716834] ath5k phy0: gain calibration timeout (2437MHz)
Mar  2 22:02:01 ben-Aspire-5520 kernel: [ 8144.101563] ath5k phy0: gain calibration timeout (2442MHz)
Mar  2 22:02:01 ben-Aspire-5520 kernel: [ 8144.482042] ath5k phy0: gain calibration timeout (2447MHz)
Mar  2 22:02:02 ben-Aspire-5520 kernel: [ 8144.866863] ath5k phy0: gain calibration timeout (2452MHz)
Mar  2 22:02:02 ben-Aspire-5520 kernel: [ 8145.326648] ath5k phy0: gain calibration timeout (2457MHz)
Mar  2 22:02:04 ben-Aspire-5520 kernel: [ 8147.417860] net_ratelimit: 2 callbacks suppressed
Mar  2 22:02:04 ben-Aspire-5520 kernel: [ 8147.417881] ath5k phy0: gain calibration timeout (2472MHz)
Mar  2 22:02:05 ben-Aspire-5520 kernel: [ 8148.094399] ath5k phy0: gain calibration timeout (2412MHz)
Mar  2 22:02:58 ben-Aspire-5520 kernel: [ 8201.397978] ath5k phy0: gain calibration timeout (2412MHz)
Mar  2 22:02:59 ben-Aspire-5520 kernel: [ 8202.078912] ath5k phy0: gain calibration timeout (2417MHz)
Mar  2 22:03:00 ben-Aspire-5520 kernel: [ 8202.758032] ath5k phy0: gain calibration timeout (2422MHz)
Mar  2 22:03:00 ben-Aspire-5520 kernel: [ 8203.437625] ath5k phy0: gain calibration timeout (2427MHz)
Mar  2 22:03:01 ben-Aspire-5520 kernel: [ 8204.117412] ath5k phy0: gain calibration timeout (2432MHz)
Mar  2 22:03:02 ben-Aspire-5520 kernel: [ 8204.810454] ath5k phy0: gain calibration timeout (2437MHz)
Mar  2 22:03:02 ben-Aspire-5520 kernel: [ 8205.488311] ath5k phy0: gain calibration timeout (2442MHz)
Mar  2 22:03:03 ben-Aspire-5520 kernel: [ 8206.013023] ath5k phy0: gain calibration timeout (2447MHz)
Mar  2 22:03:03 ben-Aspire-5520 kernel: [ 8206.402022] ath5k phy0: gain calibration timeout (2452MHz)
Mar  2 22:03:04 ben-Aspire-5520 kernel: [ 8206.790118] ath5k phy0: gain calibration timeout (2457MHz)
Mar  2 22:03:04 ben-Aspire-5520 kernel: [ 8207.178359] ath5k phy0: gain calibration timeout (2462MHz)
Mar  2 22:03:04 ben-Aspire-5520 kernel: [ 8207.558186] ath5k phy0: gain calibration timeout (2467MHz)
Mar  2 22:03:05 ben-Aspire-5520 kernel: [ 8208.006211] ath5k phy0: gain calibration timeout (2472MHz)
Mar  2 22:03:05 ben-Aspire-5520 kernel: [ 8208.455374] ath5k phy0: gain calibration timeout (2412MHz)
Mar  2 22:03:58 ben-Aspire-5520 kernel: [ 8261.395846] ath5k phy0: gain calibration timeout (2412MHz)
Mar  2 22:03:59 ben-Aspire-5520 kernel: [ 8262.074491] ath5k phy0: gain calibration timeout (2417MHz)
Mar  2 22:04:00 ben-Aspire-5520 kernel: [ 8262.754196] ath5k phy0: gain calibration timeout (2422MHz)
Mar  2 22:04:00 ben-Aspire-5520 kernel: [ 8263.434492] ath5k phy0: gain calibration timeout (2427MHz)
Mar  2 22:04:01 ben-Aspire-5520 kernel: [ 8263.893759] ath5k phy0: gain calibration timeout (2432MHz)
Mar  2 22:04:01 ben-Aspire-5520 kernel: [ 8264.279811] ath5k phy0: gain calibration timeout (2437MHz)
Mar  2 22:04:01 ben-Aspire-5520 kernel: [ 8264.507886] ath5k phy0: gain calibration timeout (2442MHz)
Mar  2 22:04:02 ben-Aspire-5520 kernel: [ 8264.863041] ath5k phy0: gain calibration timeout (2447MHz)
Mar  2 22:04:02 ben-Aspire-5520 kernel: [ 8265.251057] ath5k phy0: gain calibration timeout (2452MHz)
Mar  2 22:04:02 ben-Aspire-5520 kernel: [ 8265.629866] ath5k phy0: gain calibration timeout (2457MHz)
Mar  2 22:04:04 ben-Aspire-5520 kernel: [ 8267.104397] net_ratelimit: 2 callbacks suppressed
Mar  2 22:04:04 ben-Aspire-5520 kernel: [ 8267.104491] ath5k phy0: gain calibration timeout (2472MHz)
Mar  2 22:04:05 ben-Aspire-5520 kernel: [ 8267.841124] ath5k phy0: gain calibration timeout (2412MHz)
Mar  2 22:04:58 ben-Aspire-5520 kernel: [ 8321.400131] ath5k phy0: gain calibration timeout (2412MHz)
Mar  2 22:04:59 ben-Aspire-5520 kernel: [ 8322.077217] ath5k phy0: gain calibration timeout (2417MHz)
Mar  2 22:05:00 ben-Aspire-5520 kernel: [ 8322.756303] ath5k phy0: gain calibration timeout (2422MHz)
Mar  2 22:05:00 ben-Aspire-5520 kernel: [ 8323.432175] ath5k phy0: gain calibration timeout (2427MHz)
Mar  2 22:05:01 ben-Aspire-5520 kernel: [ 8324.108157] ath5k phy0: gain calibration timeout (2432MHz)
Mar  2 22:05:01 ben-Aspire-5520 kernel: [ 8324.474524] ath5k phy0: gain calibration timeout (2437MHz)
Mar  2 22:05:02 ben-Aspire-5520 kernel: [ 8324.854074] ath5k phy0: gain calibration timeout (2442MHz)
Mar  2 22:05:02 ben-Aspire-5520 kernel: [ 8325.234044] ath5k phy0: gain calibration timeout (2447MHz)
Mar  2 22:05:02 ben-Aspire-5520 kernel: [ 8325.614737] ath5k phy0: gain calibration timeout (2452MHz)
Mar  2 22:05:03 ben-Aspire-5520 kernel: [ 8325.994091] ath5k phy0: gain calibration timeout (2457MHz)
Mar  2 22:05:04 ben-Aspire-5520 kernel: [ 8327.202043] net_ratelimit: 2 callbacks suppressed
Mar  2 22:05:04 ben-Aspire-5520 kernel: [ 8327.202048] ath5k phy0: gain calibration timeout (2472MHz)
Mar  2 22:05:05 ben-Aspire-5520 kernel: [ 8327.925461] ath5k phy0: gain calibration timeout (2412MHz)
Mar  2 22:05:58 ben-Aspire-5520 kernel: [ 8381.098433] ath5k phy0: gain calibration timeout (2412MHz)
Mar  2 22:05:58 ben-Aspire-5520 kernel: [ 8381.480080] ath5k phy0: gain calibration timeout (2417MHz)
Mar  2 22:05:59 ben-Aspire-5520 kernel: [ 8381.866989] ath5k phy0: gain calibration timeout (2422MHz)
Mar  2 22:05:59 ben-Aspire-5520 kernel: [ 8382.313037] ath5k phy0: gain calibration timeout (2427MHz)
Mar  2 22:06:00 ben-Aspire-5520 kernel: [ 8382.991454] ath5k phy0: gain calibration timeout (2432MHz)
Mar  2 22:06:01 ben-Aspire-5520 kernel: [ 8383.666965] ath5k phy0: gain calibration timeout (2437MHz)
Mar  2 22:06:01 ben-Aspire-5520 kernel: [ 8384.342542] ath5k phy0: gain calibration timeout (2442MHz)
Mar  2 22:06:02 ben-Aspire-5520 kernel: [ 8385.019352] ath5k phy0: gain calibration timeout (2447MHz)
Mar  2 22:06:03 ben-Aspire-5520 kernel: [ 8385.694831] ath5k phy0: gain calibration timeout (2452MHz)
Mar  2 22:06:03 ben-Aspire-5520 kernel: [ 8386.371030] ath5k phy0: gain calibration timeout (2457MHz)
Mar  2 22:06:04 ben-Aspire-5520 kernel: [ 8387.071124] ath5k phy0: gain calibration timeout (2462MHz)
Mar  2 22:06:05 ben-Aspire-5520 kernel: [ 8387.746434] ath5k phy0: gain calibration timeout (2467MHz)
Mar  2 22:06:05 ben-Aspire-5520 kernel: [ 8388.055785] ath5k phy0: gain calibration timeout (2472MHz)
Mar  2 22:06:05 ben-Aspire-5520 kernel: [ 8388.502042] ath5k phy0: gain calibration timeout (2412MHz)
Mar  2 22:06:58 ben-Aspire-5520 kernel: [ 8441.399175] ath5k phy0: gain calibration timeout (2412MHz)
Mar  2 22:06:59 ben-Aspire-5520 kernel: [ 8442.076326] ath5k phy0: gain calibration timeout (2417MHz)
Mar  2 22:07:00 ben-Aspire-5520 kernel: [ 8442.755917] ath5k phy0: gain calibration timeout (2422MHz)
Mar  2 22:07:00 ben-Aspire-5520 kernel: [ 8443.436381] ath5k phy0: gain calibration timeout (2427MHz)
Mar  2 22:07:01 ben-Aspire-5520 kernel: [ 8444.116149] ath5k phy0: gain calibration timeout (2432MHz)
Mar  2 22:07:02 ben-Aspire-5520 kernel: [ 8444.795727] ath5k phy0: gain calibration timeout (2437MHz)
Mar  2 22:07:02 ben-Aspire-5520 kernel: [ 8445.475627] ath5k phy0: gain calibration timeout (2442MHz)
Mar  2 22:07:03 ben-Aspire-5520 kernel: [ 8445.849822] ath5k phy0: gain calibration timeout (2447MHz)
Mar  2 22:07:03 ben-Aspire-5520 kernel: [ 8446.230139] ath5k phy0: gain calibration timeout (2452MHz)
Mar  2 22:07:03 ben-Aspire-5520 kernel: [ 8446.614080] ath5k phy0: gain calibration timeout (2457MHz)
Mar  2 22:07:04 ben-Aspire-5520 kernel: [ 8447.382672] net_ratelimit: 1 callbacks suppressed
Mar  2 22:07:04 ben-Aspire-5520 kernel: [ 8447.382677] ath5k phy0: gain calibration timeout (2467MHz)
Mar  2 22:07:05 ben-Aspire-5520 kernel: [ 8447.833348] ath5k phy0: gain calibration timeout (2472MHz)
Mar  2 22:07:05 ben-Aspire-5520 kernel: [ 8448.286397] ath5k phy0: gain calibration timeout (2412MHz)
Mar  2 22:07:58 ben-Aspire-5520 kernel: [ 8501.378565] ath5k phy0: gain calibration timeout (2412MHz)
Mar  2 22:07:59 ben-Aspire-5520 kernel: [ 8502.045998] ath5k phy0: gain calibration timeout (2417MHz)
Mar  2 22:08:00 ben-Aspire-5520 kernel: [ 8502.770872] ath5k phy0: gain calibration timeout (2422MHz)
Mar  2 22:08:00 ben-Aspire-5520 kernel: [ 8503.454561] ath5k phy0: gain calibration timeout (2427MHz)
Mar  2 22:08:01 ben-Aspire-5520 kernel: [ 8504.131201] ath5k phy0: gain calibration timeout (2432MHz)
Mar  2 22:08:02 ben-Aspire-5520 kernel: [ 8504.806843] ath5k phy0: gain calibration timeout (2437MHz)
Mar  2 22:08:02 ben-Aspire-5520 kernel: [ 8505.483193] ath5k phy0: gain calibration timeout (2442MHz)
Mar  2 22:08:03 ben-Aspire-5520 kernel: [ 8506.158720] ath5k phy0: gain calibration timeout (2447MHz)
Mar  2 22:08:03 ben-Aspire-5520 kernel: [ 8506.545104] ath5k phy0: gain calibration timeout (2452MHz)
Mar  2 22:08:04 ben-Aspire-5520 kernel: [ 8506.926157] ath5k phy0: gain calibration timeout (2457MHz)
Mar  2 22:08:04 ben-Aspire-5520 kernel: [ 8507.311506] ath5k phy0: gain calibration timeout (2462MHz)
Mar  2 22:08:05 ben-Aspire-5520 kernel: [ 8507.703736] ath5k phy0: gain calibration timeout (2467MHz)
Mar  2 22:08:05 ben-Aspire-5520 kernel: [ 8508.153881] ath5k phy0: gain calibration timeout (2472MHz)
Mar  2 22:08:05 ben-Aspire-5520 kernel: [ 8508.601061] ath5k phy0: gain calibration timeout (2412MHz)
Mar  2 22:08:58 ben-Aspire-5520 kernel: [ 8561.359732] ath5k phy0: gain calibration timeout (2412MHz)
Mar  2 22:08:59 ben-Aspire-5520 kernel: [ 8561.740914] ath5k phy0: gain calibration timeout (2417MHz)
Mar  2 22:08:59 ben-Aspire-5520 kernel: [ 8562.125665] ath5k phy0: gain calibration timeout (2422MHz)
Mar  2 22:08:59 ben-Aspire-5520 kernel: [ 8562.526023] ath5k phy0: gain calibration timeout (2427MHz)
Mar  2 22:08:59 ben-Aspire-5520 kernel: [ 8562.607791] ath5k phy0: gain calibration timeout (2432MHz)
Mar  2 22:09:00 ben-Aspire-5520 kernel: [ 8562.985849] ath5k phy0: gain calibration timeout (2437MHz)
Mar  2 22:09:00 ben-Aspire-5520 kernel: [ 8563.369205] ath5k phy0: gain calibration timeout (2442MHz)
Mar  2 22:09:01 ben-Aspire-5520 kernel: [ 8563.753767] ath5k phy0: gain calibration timeout (2447MHz)
Mar  2 22:09:01 ben-Aspire-5520 kernel: [ 8564.142351] ath5k phy0: gain calibration timeout (2452MHz)
Mar  2 22:09:01 ben-Aspire-5520 kernel: [ 8564.527150] ath5k phy0: gain calibration timeout (2457MHz)
Mar  2 22:09:04 ben-Aspire-5520 kernel: [ 8567.372033] net_ratelimit: 3 callbacks suppressed
Mar  2 22:09:04 ben-Aspire-5520 kernel: [ 8567.372044] ath5k phy0: gain calibration timeout (2412MHz)
Mar  2 22:09:58 ben-Aspire-5520 kernel: [ 8621.393204] ath5k phy0: gain calibration timeout (2412MHz)
Mar  2 22:09:59 ben-Aspire-5520 kernel: [ 8622.056122] ath5k phy0: gain calibration timeout (2417MHz)
Mar  2 22:09:59 ben-Aspire-5520 kernel: [ 8622.166855] ath5k phy0: gain calibration timeout (2422MHz)
Mar  2 22:09:59 ben-Aspire-5520 kernel: [ 8622.553391] ath5k phy0: gain calibration timeout (2427MHz)
Mar  2 22:10:00 ben-Aspire-5520 kernel: [ 8622.937546] ath5k phy0: gain calibration timeout (2432MHz)
Mar  2 22:10:00 ben-Aspire-5520 kernel: [ 8623.322427] ath5k phy0: gain calibration timeout (2437MHz)
Mar  2 22:10:01 ben-Aspire-5520 kernel: [ 8623.707290] ath5k phy0: gain calibration timeout (2442MHz)
Mar  2 22:10:01 ben-Aspire-5520 kernel: [ 8624.090563] ath5k phy0: gain calibration timeout (2447MHz)
Mar  2 22:10:01 ben-Aspire-5520 kernel: [ 8624.473060] ath5k phy0: gain calibration timeout (2452MHz)
Mar  2 22:10:02 ben-Aspire-5520 kernel: [ 8625.544055] ACPI Exception: AE_TIME, Returned by Handler for [EmbeddedControl] (20100428/evregion-474)
Mar  2 22:10:02 ben-Aspire-5520 kernel: [ 8625.544161] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPC0.ECOK] (Node f7020d50), AE_TIME
Mar  2 22:10:02 ben-Aspire-5520 kernel: [ 8625.544208] ACPI Error (psparse-0537): Method parse/execution failed [\_TZ_.THRM._TMP] (Node f7025d38), AE_TIME
Mar  2 22:10:02 ben-Aspire-5520 kernel: [ 8625.544325] Thermal: failed to read out thermal zone 0
Mar  2 22:10:04 ben-Aspire-5520 kernel: [ 8626.933391] net_ratelimit: 3 callbacks suppressed
Mar  2 22:10:04 ben-Aspire-5520 kernel: [ 8626.933396] ath5k phy0: gain calibration timeout (2472MHz)
Mar  2 22:10:05 ben-Aspire-5520 kernel: [ 8627.658384] ath5k phy0: gain calibration timeout (2412MHz)
Mar  2 22:10:58 ben-Aspire-5520 kernel: [ 8681.379518] ath5k phy0: gain calibration timeout (2412MHz)
Mar  2 22:10:59 ben-Aspire-5520 kernel: [ 8682.038810] ath5k phy0: gain calibration timeout (2417MHz)
Mar  2 22:11:00 ben-Aspire-5520 kernel: [ 8682.694367] ath5k phy0: gain calibration timeout (2422MHz)
Mar  2 22:11:00 ben-Aspire-5520 kernel: [ 8683.350366] ath5k phy0: gain calibration timeout (2427MHz)
Mar  2 22:11:01 ben-Aspire-5520 kernel: [ 8684.006398] ath5k phy0: gain calibration timeout (2432MHz)
Mar  2 22:11:02 ben-Aspire-5520 kernel: [ 8684.662544] ath5k phy0: gain calibration timeout (2437MHz)
Mar  2 22:11:02 ben-Aspire-5520 kernel: [ 8685.318559] ath5k phy0: gain calibration timeout (2442MHz)
Mar  2 22:11:03 ben-Aspire-5520 kernel: [ 8685.974607] ath5k phy0: gain calibration timeout (2447MHz)
Mar  2 22:11:03 ben-Aspire-5520 kernel: [ 8686.635829] ath5k phy0: gain calibration timeout (2452MHz)
Mar  2 22:11:04 ben-Aspire-5520 kernel: [ 8687.306958] ath5k phy0: gain calibration timeout (2457MHz)
Mar  2 22:11:05 ben-Aspire-5520 kernel: [ 8687.962445] ath5k phy0: gain calibration timeout (2462MHz)
Mar  2 22:11:05 ben-Aspire-5520 kernel: [ 8688.630472] ath5k phy0: gain calibration timeout (2467MHz)
Mar  2 22:11:06 ben-Aspire-5520 kernel: [ 8689.354610] ath5k phy0: gain calibration timeout (2472MHz)
Mar  2 22:11:07 ben-Aspire-5520 kernel: [ 8690.078489] ath5k phy0: gain calibration timeout (2412MHz)
Mar  4 15:38:00 ben-Aspire-5520 kernel: [ 6761.398815] net_ratelimit: 4 callbacks suppressed
Mar  4 15:38:00 ben-Aspire-5520 kernel: [ 6761.398821] ath5k phy0: gain calibration timeout (2412MHz)
Mar  4 15:38:00 ben-Aspire-5520 kernel: [ 6761.778336] ath5k phy0: gain calibration timeout (2417MHz)
Mar  4 15:38:01 ben-Aspire-5520 kernel: [ 6762.157420] ath5k phy0: gain calibration timeout (2422MHz)
Mar  4 15:38:01 ben-Aspire-5520 kernel: [ 6762.545657] ath5k phy0: gain calibration timeout (2427MHz)
Mar  4 15:38:01 ben-Aspire-5520 kernel: [ 6762.925368] ath5k phy0: gain calibration timeout (2432MHz)
Mar  4 15:38:02 ben-Aspire-5520 kernel: [ 6763.313560] ath5k phy0: gain calibration timeout (2437MHz)
Mar  4 15:38:02 ben-Aspire-5520 kernel: [ 6763.693319] ath5k phy0: gain calibration timeout (2442MHz)
Mar  4 15:38:03 ben-Aspire-5520 kernel: [ 6764.073341] ath5k phy0: gain calibration timeout (2447MHz)
Mar  4 15:38:03 ben-Aspire-5520 kernel: [ 6764.453501] ath5k phy0: gain calibration timeout (2452MHz)
Mar  4 15:38:03 ben-Aspire-5520 kernel: [ 6764.833514] ath5k phy0: gain calibration timeout (2457MHz)

---

### Post by ben889 on 2011-03-04
demsg:

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-27-generic (buildd@palmer) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #48-Ubuntu SMP Tue Feb 22 20:25:29 UTC 2011 (Ubuntu 2.6.35-27.48-generic 2.6.35.11)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e000 (usable)
[    0.000000]  BIOS-e820: 000000000009e000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000006ff50000 (usable)
[    0.000000]  BIOS-e820: 000000006ff50000 - 000000006ff65000 (ACPI data)
[    0.000000]  BIOS-e820: 000000006ff65000 - 000000006ff66000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000006ff66000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled: non-PAE kernel!
[    0.000000] DMI present.
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x6ff50 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-D3FFF write-protect
[    0.000000]   D4000-E3FFF uncachable
[    0.000000]   E4000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FF80000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000002000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (reserved)
[    0.000000]  modified: 0000000000001000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009e000 (usable)
[    0.000000]  modified: 000000000009e000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000d2000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000006ff50000 (usable)
[    0.000000]  modified: 000000006ff50000 - 000000006ff65000 (ACPI data)
[    0.000000]  modified: 000000006ff65000 - 000000006ff66000 (ACPI NVS)
[    0.000000]  modified: 000000006ff66000 - 0000000080000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] found SMP MP-table at [c00f7c90] f7c90
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 15000-1a000
[    0.000000] RAMDISK: 375a8000 - 37ff0000
[    0.000000] Allocated new RAMDISK: 009a9000 - 013f0d0e
[    0.000000] Move RAMDISK from 00000000375a8000 - 0000000037fefd0d to 009a9000 - 013f0d0d
[    0.000000] ACPI: RSDP 000f7ca0 00024 (v02 ACRSYS)
[    0.000000] ACPI: XSDT 6ff5e351 0005C (v01 ACRSYS ACRPRDCT 06040000  LTP 00000000)
[    0.000000] ACPI: SLIC 6ff64ace 00176 (v01 ACRSYS ACRPRDCT 06040000 LOHR 00000000)
[    0.000000] ACPI: FACP 6ff64c44 000F4 (v03 NVIDIA MCP67-M  06040000 PTL_ 000F4240)
[    0.000000] ACPI: DSDT 6ff5e3ad 066AD (v01 NVIDIA    MCP67 06040000 MSFT 03000000)
[    0.000000] ACPI: FACS 6ff65fc0 00040
[    0.000000] ACPI: SSDT 6ff64d38 001C4 (v01 PTLTD  POWERNOW 06040000  LTP 00000001)
[    0.000000] ACPI: MCFG 6ff64efc 0003C (v01 Nvidia NVDAACPI 06040000 NVDA 00000000)
[    0.000000] ACPI: HPET 6ff64f38 00038 (v01 PTLTD  HPETTBL  06040000  LTP 00000001)
[    0.000000] ACPI: APIC 6ff64f70 00068 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: BOOT 6ff64fd8 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 903MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000001 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0006ff50
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000001 -> 0x00000002
[    0.000000]     0: 0x00000010 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x0006ff50
[    0.000000] On node 0 totalpages: 458463
[    0.000000] free_area_init_node: node 0, pgdat c0801fc0, node_mem_map c13f2020
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 1807 pages used for memmap
[    0.000000]   HighMem zone: 229443 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] early_res array is doubled to 64 at [16000 - 167ff]
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:60000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c2400000 s36416 r0 d20928 u2097152
[    0.000000] pcpu-alloc: s36416 r0 d20928 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 454880
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-27-generic root=UUID=41dd901b-c658-4a40-87bb-89ff29a5d2c6 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 9171500 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Subtract (51 early reservations)
[    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
[    0.000000]   #2 [0000100000 - 00009a4adc]   TEXT DATA BSS
[    0.000000]   #3 [00009a5000 - 00009a80ed]             BRK
[    0.000000]   #4 [00000f7ca0 - 0000100000]   BIOS reserved
[    0.000000]   #5 [00000f7c90 - 00000f7ca0]    MP-table mpf
[    0.000000]   #6 [000009e000 - 000009e571]   BIOS reserved
[    0.000000]   #7 [000009e6bd - 00000f7c90]   BIOS reserved
[    0.000000]   #8 [000009e571 - 000009e6bd]    MP-table mpc
[    0.000000]   #9 [0000010000 - 0000011000]      TRAMPOLINE
[    0.000000]   #10 [0000011000 - 0000015000]     ACPI WAKEUP
[    0.000000]   #11 [0000015000 - 0000016000]         PGTABLE
[    0.000000]   #12 [00009a9000 - 00013f1000]     NEW RAMDISK
[    0.000000]   #13 [00013f1000 - 00013f2000]         BOOTMEM
[    0.000000]   #14 [00013f2000 - 00021f2000]         BOOTMEM
[    0.000000]   #15 [00021f2000 - 00021f2004]         BOOTMEM
[    0.000000]   #16 [00021f2040 - 00021f2100]         BOOTMEM
[    0.000000]   #17 [00021f2100 - 00021f2154]         BOOTMEM
[    0.000000]   #18 [00021f2180 - 00021f5180]         BOOTMEM
[    0.000000]   #19 [00021f5180 - 00021f51d8]         BOOTMEM
[    0.000000]   #20 [00021f5200 - 00021f8200]         BOOTMEM
[    0.000000]   #21 [00021f8200 - 00021f8225]         BOOTMEM
[    0.000000]   #22 [00021f8240 - 00021f8267]         BOOTMEM
[    0.000000]   #23 [00021f8280 - 00021f8408]         BOOTMEM
[    0.000000]   #24 [00021f8440 - 00021f8480]         BOOTMEM
[    0.000000]   #25 [00021f8480 - 00021f84c0]         BOOTMEM
[    0.000000]   #26 [00021f84c0 - 00021f8500]         BOOTMEM
[    0.000000]   #27 [00021f8500 - 00021f8540]         BOOTMEM
[    0.000000]   #28 [00021f8540 - 00021f8580]         BOOTMEM
[    0.000000]   #29 [00021f8580 - 00021f85c0]         BOOTMEM
[    0.000000]   #30 [00021f85c0 - 00021f8600]         BOOTMEM
[    0.000000]   #31 [00021f8600 - 00021f8640]         BOOTMEM
[    0.000000]   #32 [00021f8640 - 00021f8680]         BOOTMEM
[    0.000000]   #33 [00021f8680 - 00021f86c0]         BOOTMEM
[    0.000000]   #34 [00021f86c0 - 00021f8700]         BOOTMEM
[    0.000000]   #35 [00021f8700 - 00021f8710]         BOOTMEM
[    0.000000]   #36 [00021f8740 - 00021f8750]         BOOTMEM
[    0.000000]   #37 [00021f8780 - 00021f87ea]         BOOTMEM
[    0.000000]   #38 [00021f8800 - 00021f886a]         BOOTMEM
[    0.000000]   #39 [0002400000 - 000240e000]         BOOTMEM
[    0.000000]   #40 [0002600000 - 000260e000]         BOOTMEM
[    0.000000]   #41 [00021fa880 - 00021fa884]         BOOTMEM
[    0.000000]   #42 [00021fa8c0 - 00021fa8c4]         BOOTMEM
[    0.000000]   #43 [00021fa900 - 00021fa908]         BOOTMEM
[    0.000000]   #44 [00021fa940 - 00021fa948]         BOOTMEM
[    0.000000]   #45 [00021fa980 - 00021faa28]         BOOTMEM
[    0.000000]   #46 [00021faa40 - 00021faaa8]         BOOTMEM
[    0.000000]   #47 [00021faac0 - 00021feac0]         BOOTMEM
[    0.000000]   #48 [00021feac0 - 000227eac0]         BOOTMEM
[    0.000000]   #49 [000227eac0 - 00022beac0]         BOOTMEM
[    0.000000]   #50 [000260e000 - 0002ecd22c]         BOOTMEM
[    0.000000] Initializing HighMem for node 0 (000377fe:0006ff50)
[    0.000000] Memory: 1790200k/1834304k available (4935k kernel code, 43652k reserved, 2337k data, 688k init, 925000k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc081b000 - 0xc08c7000   ( 688 kB)
[    0.000000]       .data : 0xc05d1fce - 0xc081a7a8   (2337 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05d1fce   (4935 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU-based detection of stalled CPUs is disabled.
[    0.000000]     Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512
[    0.000000] Extended CMOS year: 2000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1800.221 MHz processor.
[    0.004006] Calibrating delay loop (skipped), value calculated using timer frequency.. 3600.44 BogoMIPS (lpj=7200884)
[    0.004014] pid_max: default: 32768 minimum: 301
[    0.004041] Security Framework initialized
[    0.004068] AppArmor: AppArmor initialized
[    0.004071] Yama: becoming mindful.
[    0.004151] Mount-cache hash table entries: 512
[    0.004323] Initializing cgroup subsys ns
[    0.004329] Initializing cgroup subsys cpuacct
[    0.004336] Initializing cgroup subsys memory
[    0.004348] Initializing cgroup subsys devices
[    0.004353] Initializing cgroup subsys freezer
[    0.004357] Initializing cgroup subsys net_cls
[    0.004388] CPU: Physical Processor ID: 0
[    0.004392] CPU: Processor Core ID: 0
[    0.004396] mce: CPU supports 5 MCE banks
[    0.004409] using C1E aware idle routine
[    0.004418] Performance Events: AMD PMU driver.
[    0.004428] ... version:                0
[    0.004431] ... bit width:              48
[    0.004435] ... generic registers:      4
[    0.004438] ... value mask:             0000ffffffffffff
[    0.004442] ... max period:             00007fffffffffff
[    0.004445] ... fixed-purpose events:   0
[    0.004448] ... event mask:             000000000000000f
[    0.009224] ACPI: Core revision 20100428
[    0.024012] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.024018] ftrace: allocating 21761 entries in 43 pages
[    0.028097] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.028578] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.068353] CPU0: AMD Athlon(tm) 64 X2 Dual-Core Processor TK-55 stepping 01
[    0.072000] Booting Node   0, Processors  #1 Ok.
[    0.008000] Initializing CPU#1
[    0.008000] System has AMD C1E enabled
[    0.156049] Brought up 2 CPUs
[    0.156052] Total of 2 processors activated (7200.95 BogoMIPS).
[    0.156047] Switch to broadcast mode on CPU1
[    0.156326] Switch to broadcast mode on CPU0
[    0.156326] devtmpfs: initialized
[    0.157212] regulator: core version 0.5
[    0.157253] Time: 13:45:17  Date: 03/04/11
[    0.157311] NET: Registered protocol family 16
[    0.157474] EISA bus registered
[    0.157481] node 0 link 0: io port [1000, fffff]
[    0.157485] TOM: 0000000080000000 aka 2048M
[    0.157490] node 0 link 0: mmio [a0000, bffff]
[    0.157494] node 0 link 0: mmio [80000000, dfffffff]
[    0.157497] node 0 link 0: mmio [e0000000, efffffff]
[    0.157501] node 0 link 0: mmio [f0000000, fe0bffff]
[    0.157505] bus: [00, ff] on node 0 link 0
[    0.157509] bus: 00 index 0 [io  0x0000-0xffff]
[    0.157512] bus: 00 index 1 [mem 0x000a0000-0x000bffff]
[    0.157515] bus: 00 index 2 [mem 0x80000000-0xffffffff]
[    0.157524] ACPI: bus type pci registered
[    0.157615] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.157619] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.157622] PCI: Using MMCONFIG for extended config space
[    0.157624] PCI: Using configuration type 1 for base access
[    0.158818] Trying to unpack rootfs image as initramfs...
[    0.158818] bio: create slab <bio-0> at 0
[    0.158818] ACPI: EC: Look up EC in DSDT
[    0.162694] ACPI: Interpreter enabled
[    0.162699] ACPI: (supports S0 S3 S4 S5)
[    0.162721] ACPI: Using IOAPIC for interrupt routing
[    0.231943] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[    0.232312] ACPI: No dock devices found.
[    0.232318] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.232617] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.232920] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.232924] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.232928] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.232931] pci_root PNP0A08:00: host bridge window [mem 0x000c0000-0x000c3fff] (ignored)
[    0.232935] pci_root PNP0A08:00: host bridge window [mem 0x000c4000-0x000c7fff] (ignored)
[    0.232938] pci_root PNP0A08:00: host bridge window [mem 0x000c8000-0x000cbfff] (ignored)
[    0.232942] pci_root PNP0A08:00: host bridge window [mem 0x000cc000-0x000cffff] (ignored)
[    0.232945] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff] (ignored)
[    0.232948] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff] (ignored)
[    0.232952] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff] (ignored)
[    0.232955] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff] (ignored)
[    0.232959] pci_root PNP0A08:00: host bridge window [mem 0x000e0000-0x000e3fff] (ignored)
[    0.232962] pci_root PNP0A08:00: host bridge window [mem 0x000e4000-0x000e7fff] (ignored)
[    0.232965] pci_root PNP0A08:00: host bridge window [mem 0x000e8000-0x000ebfff] (ignored)
[    0.232969] pci_root PNP0A08:00: host bridge window [mem 0x000ec000-0x000effff] (ignored)
[    0.232972] pci_root PNP0A08:00: host bridge window [mem 0x000f0000-0x000fffff] (ignored)
[    0.232976] pci_root PNP0A08:00: host bridge window [mem 0xfed40000-0xfed44fff] (ignored)
[    0.232979] pci_root PNP0A08:00: host bridge window [mem 0x80000000-0xfebfffff] (ignored)
[    0.233133] pci 0000:00:01.0: reg 10: [io  0x1d00-0x1dff]
[    0.233171] pci 0000:00:01.1: reg 10: [io  0x3080-0x30bf]
[    0.233183] pci 0000:00:01.1: reg 20: [io  0x3040-0x307f]
[    0.233188] pci 0000:00:01.1: reg 24: [io  0x3000-0x303f]
[    0.233209] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.233215] pci 0000:00:01.1: PME# disabled
[    0.233273] pci 0000:00:01.3: reg 10: [mem 0xf2400000-0xf247ffff]
[    0.233353] pci 0000:00:02.0: reg 10: [mem 0xf2686000-0xf2686fff]
[    0.233378] pci 0000:00:02.0: supports D1 D2
[    0.233380] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.233384] pci 0000:00:02.0: PME# disabled
[    0.233406] pci 0000:00:02.1: reg 10: [mem 0xf2689000-0xf26890ff]
[    0.233435] pci 0000:00:02.1: supports D1 D2
[    0.233438] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.233442] pci 0000:00:02.1: PME# disabled
[    0.233468] pci 0000:00:04.0: reg 10: [mem 0xf2687000-0xf2687fff]
[    0.233493] pci 0000:00:04.0: supports D1 D2
[    0.233496] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.233500] pci 0000:00:04.0: PME# disabled
[    0.233521] pci 0000:00:04.1: reg 10: [mem 0xf2689400-0xf26894ff]
[    0.233551] pci 0000:00:04.1: supports D1 D2
[    0.233553] pci 0000:00:04.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.233557] pci 0000:00:04.1: PME# disabled
[    0.233592] pci 0000:00:06.0: reg 20: [io  0x30c0-0x30cf]
[    0.233629] pci 0000:00:07.0: reg 10: [mem 0xf2680000-0xf2683fff]
[    0.233659] pci 0000:00:07.0: PME# supported from D3hot D3cold
[    0.233662] pci 0000:00:07.0: PME# disabled
[    0.233725] pci 0000:00:09.0: reg 10: [io  0x30f0-0x30f7]
[    0.233730] pci 0000:00:09.0: reg 14: [io  0x30e4-0x30e7]
[    0.233734] pci 0000:00:09.0: reg 18: [io  0x30e8-0x30ef]
[    0.233739] pci 0000:00:09.0: reg 1c: [io  0x30e0-0x30e3]
[    0.233743] pci 0000:00:09.0: reg 20: [io  0x30d0-0x30df]
[    0.233748] pci 0000:00:09.0: reg 24: [mem 0xf2684000-0xf2685fff]
[    0.233795] pci 0000:00:0a.0: reg 10: [mem 0xf2688000-0xf2688fff]
[    0.233799] pci 0000:00:0a.0: reg 14: [io  0x30f8-0x30ff]
[    0.233804] pci 0000:00:0a.0: reg 18: [mem 0xf2689c00-0xf2689cff]
[    0.233809] pci 0000:00:0a.0: reg 1c: [mem 0xf2689800-0xf268980f]
[    0.233832] pci 0000:00:0a.0: supports D1 D2
[    0.233835] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.233840] pci 0000:00:0a.0: PME# disabled
[    0.233882] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.233885] pci 0000:00:0c.0: PME# disabled
[    0.233921] pci 0000:00:0d.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.233925] pci 0000:00:0d.0: PME# disabled
[    0.233947] pci 0000:00:12.0: reg 10: [mem 0xf1000000-0xf1ffffff]
[    0.233954] pci 0000:00:12.0: reg 14: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.233961] pci 0000:00:12.0: reg 1c: [mem 0xf0000000-0xf0ffffff 64bit]
[    0.233967] pci 0000:00:12.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.234064] PCI: peer root bus 00 res updated from pci conf
[    0.234108] pci 0000:01:04.0: reg 10: [mem 0xf2300000-0xf23007ff]
[    0.234143] pci 0000:01:04.0: PME# supported from D0 D3hot D3cold
[    0.234147] pci 0000:01:04.0: PME# disabled
[    0.234171] pci 0000:01:04.1: reg 10: [mem 0xf2300800-0xf23008ff]
[    0.234206] pci 0000:01:04.1: supports D1 D2
[    0.234209] pci 0000:01:04.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.234213] pci 0000:01:04.1: PME# disabled
[    0.234236] pci 0000:01:04.2: reg 10: [mem 0xf2300c00-0xf2300cff]
[    0.234271] pci 0000:01:04.2: supports D1 D2
[    0.234274] pci 0000:01:04.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.234278] pci 0000:01:04.2: PME# disabled
[    0.234301] pci 0000:01:04.3: reg 10: [mem 0xf2301000-0xf23010ff]
[    0.234336] pci 0000:01:04.3: supports D1 D2
[    0.234339] pci 0000:01:04.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.234343] pci 0000:01:04.3: PME# disabled
[    0.234379] pci 0000:00:08.0: PCI bridge to [bus 01-01] (subtractive decode)
[    0.234384] pci 0000:00:08.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.234389] pci 0000:00:08.0:   bridge window [mem 0xf2300000-0xf23fffff]
[    0.234393] pci 0000:00:08.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.234397] pci 0000:00:08.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.234400] pci 0000:00:08.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.234404] pci 0000:00:08.0:   bridge window [mem 0x80000000-0xffffffff] (subtractive decode)
[    0.234431] pci 0000:00:0c.0: PCI bridge to [bus 03-04]
[    0.234435] pci 0000:00:0c.0:   bridge window [io  0x4000-0x4fff]
[    0.234439] pci 0000:00:0c.0:   bridge window [mem 0xf2000000-0xf21fffff]
[    0.234444] pci 0000:00:0c.0:   bridge window [mem 0xf2800000-0xf29fffff 64bit pref]
[    0.234493] pci 0000:05:00.0: reg 10: [mem 0xf2200000-0xf220ffff 64bit]
[    0.234554] pci 0000:05:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.234564] pci 0000:00:0d.0: PCI bridge to [bus 05-05]
[    0.234569] pci 0000:00:0d.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.234573] pci 0000:00:0d.0:   bridge window [mem 0xf2200000-0xf22fffff]
[    0.234578] pci 0000:00:0d.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.234587] pci_bus 0000:00: on NUMA node 0
[    0.234591] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.234704] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[    0.234729] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[    0.234764] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
[    0.268360] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 11) *10
[    0.268575] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 *11)
[    0.268781] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 11) *0, disabled.
[    0.268989] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 11) *0, disabled.
[    0.269197] ACPI: PCI Interrupt Link [LK1E] (IRQs 16) *0, disabled.
[    0.269402] ACPI: PCI Interrupt Link [LK2E] (IRQs 17) *0, disabled.
[    0.269613] ACPI: PCI Interrupt Link [LK3E] (IRQs 18) *0, disabled.
[    0.269819] ACPI: PCI Interrupt Link [LK4E] (IRQs 19) *10
[    0.270023] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *10
[    0.270228] ACPI: PCI Interrupt Link [LUS0] (IRQs 20 21 22 23) *11
[    0.270436] ACPI: PCI Interrupt Link [LUS2] (IRQs 20 21 22 23) *7
[    0.270649] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *11
[    0.270856] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *10
[    0.271062] ACPI: PCI Interrupt Link [LGPU] (IRQs 17) *10
[    0.271269] ACPI: PCI Interrupt Link [LPID] (IRQs 20 21 22 23) *0, disabled.
[    0.271476] ACPI: PCI Interrupt Link [LSI0] (IRQs 20 21 22 23) *5
[    0.271690] ACPI: PCI Interrupt Link [Z00N] (IRQs 20 21 22 23) *10
[    0.271903] ACPI: PCI Interrupt Link [Z00O] (IRQs 20 21 22 23) *11
[    0.272123] ACPI: PCI Interrupt Link [LPMU] (IRQs 18) *11
[    0.272179] HEST: Table is not found!
[    0.272301] vgaarb: device added: PCI:0000:00:12.0,decodes=io+mem,owns=io+mem,locks=none
[    0.272310] vgaarb: loaded
[    0.272511] SCSI subsystem initialized
[    0.276045] libata version 3.00 loaded.
[    0.276045] usbcore: registered new interface driver usbfs
[    0.276045] usbcore: registered new interface driver hub
[    0.276045] usbcore: registered new device driver usb
[    0.276045] ACPI: WMI: Mapper loaded
[    0.276045] PCI: Using ACPI for IRQ routing
[    0.276045] PCI: pci_cache_line_size set to 64 bytes
[    0.276045] reserve RAM buffer: 0000000000002000 - 000000000000ffff 
[    0.276045] reserve RAM buffer: 000000000009e000 - 000000000009ffff 
[    0.276045] reserve RAM buffer: 000000006ff50000 - 000000006fffffff 
[    0.276045] NetLabel: Initializing
[    0.276045] NetLabel:  domain hash size = 128
[    0.276045] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.276045] NetLabel:  unlabeled traffic allowed by default
[    0.276045] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.276045] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[    0.276045] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.280182] Switching to clocksource hpet
[    0.295584] AppArmor: AppArmor Filesystem Enabled
[    0.295608] pnp: PnP ACPI init
[    0.295635] ACPI: bus type pnp registered
[    0.322186] pnp: PnP ACPI: found 13 devices
[    0.322189] ACPI: ACPI bus type pnp unregistered
[    0.322194] PnPBIOS: Disabled by ACPI PNP
[    0.322209] system 00:01: [io  0x0360-0x0361] has been reserved
[    0.322213] system 00:01: [io  0x04d0-0x04d1] has been reserved
[    0.322222] system 00:07: [mem 0xe0000000-0xefffffff] has been reserved
[    0.322228] system 00:0a: [io  0x1000-0x107f] has been reserved
[    0.322232] system 00:0a: [io  0x1080-0x10ff] has been reserved
[    0.322235] system 00:0a: [io  0x1400-0x147f] has been reserved
[    0.322239] system 00:0a: [io  0x1480-0x14ff] has been reserved
[    0.322242] system 00:0a: [io  0x1800-0x187f] has been reserved
[    0.322246] system 00:0a: [io  0x1880-0x18ff] has been reserved
[    0.322253] system 00:0c: [mem 0xffc00000-0xffffffff] could not be reserved
[    0.322257] system 00:0c: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.322261] system 00:0c: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.322265] system 00:0c: [mem 0xfed00000-0xfed00fff] has been reserved
[    0.322269] system 00:0c: [mem 0xfef00000-0xfef00fff] has been reserved
[    0.358611] pci 0000:00:12.0: BAR 6: assigned [mem 0x80000000-0x8001ffff pref]
[    0.358619] pci 0000:00:08.0: PCI bridge to [bus 01-01]
[    0.358622] pci 0000:00:08.0:   bridge window [io  disabled]
[    0.358627] pci 0000:00:08.0:   bridge window [mem 0xf2300000-0xf23fffff]
[    0.358630] pci 0000:00:08.0:   bridge window [mem pref disabled]
[    0.358636] pci 0000:00:0c.0: PCI bridge to [bus 03-04]
[    0.358639] pci 0000:00:0c.0:   bridge window [io  0x4000-0x4fff]
[    0.358643] pci 0000:00:0c.0:   bridge window [mem 0xf2000000-0xf21fffff]
[    0.358647] pci 0000:00:0c.0:   bridge window [mem 0xf2800000-0xf29fffff 64bit pref]
[    0.358652] pci 0000:00:0d.0: PCI bridge to [bus 05-05]
[    0.358654] pci 0000:00:0d.0:   bridge window [io  disabled]
[    0.358658] pci 0000:00:0d.0:   bridge window [mem 0xf2200000-0xf22fffff]
[    0.358662] pci 0000:00:0d.0:   bridge window [mem pref disabled]
[    0.358676] pci 0000:00:08.0: setting latency timer to 64
[    0.358684] pci 0000:00:0c.0: setting latency timer to 64
[    0.358691] pci 0000:00:0d.0: setting latency timer to 64
[    0.358695] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    0.358698] pci_bus 0000:00: resource 5 [mem 0x000a0000-0x000bffff]
[    0.358701] pci_bus 0000:00: resource 6 [mem 0x80000000-0xffffffff]
[    0.358705] pci_bus 0000:01: resource 1 [mem 0xf2300000-0xf23fffff]
[    0.358708] pci_bus 0000:01: resource 4 [io  0x0000-0xffff]
[    0.358711] pci_bus 0000:01: resource 5 [mem 0x000a0000-0x000bffff]
[    0.358714] pci_bus 0000:01: resource 6 [mem 0x80000000-0xffffffff]
[    0.358718] pci_bus 0000:03: resource 0 [io  0x4000-0x4fff]
[    0.358721] pci_bus 0000:03: resource 1 [mem 0xf2000000-0xf21fffff]
[    0.358724] pci_bus 0000:03: resource 2 [mem 0xf2800000-0xf29fffff 64bit pref]
[    0.358727] pci_bus 0000:05: resource 1 [mem 0xf2200000-0xf22fffff]
[    0.358779] NET: Registered protocol family 2
[    0.358854] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.359190] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.359901] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.360254] TCP: Hash tables configured (established 131072 bind 65536)
[    0.360259] TCP reno registered
[    0.360264] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.360277] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.360389] NET: Registered protocol family 1
[    0.360574] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.360629] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.360690] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.360758] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.360830] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.360906] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.360914] pci 0000:00:12.0: Boot video device
[    0.360936] PCI: CLS 64 bytes, default 64
[    0.360968] Simple Boot Flag at 0x36 set to 0x1
[    0.361225] cpufreq-nforce2: No nForce2 chipset.
[    0.361262] Scanning for low memory corruption every 60 seconds
[    0.361452] audit: initializing netlink socket (disabled)
[    0.361466] type=2000 audit(1299246317.360:1): initialized
[    0.374169] highmem bounce pool size: 64 pages
[    0.374176] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.375804] VFS: Disk quotas dquot_6.5.2
[    0.375874] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.376557] fuse init (API version 7.14)
[    0.376662] msgmni has been set to 1689
[    0.506954] Freeing initrd memory: 10528k freed
[    0.517759] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.517765] io scheduler noop registered
[    0.517768] io scheduler deadline registered
[    0.517785] io scheduler cfq registered (default)
[    0.517932] pcieport 0000:00:0c.0: setting latency timer to 64
[    0.517957]   alloc irq_desc for 40 on node -1
[    0.517960]   alloc kstat_irqs on node -1
[    0.517970] pcieport 0000:00:0c.0: irq 40 for MSI/MSI-X
[    0.518032] pcieport 0000:00:0d.0: setting latency timer to 64
[    0.518050]   alloc irq_desc for 41 on node -1
[    0.518052]   alloc kstat_irqs on node -1
[    0.518058] pcieport 0000:00:0d.0: irq 41 for MSI/MSI-X
[    0.518142] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.518173] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.526878] ACPI: AC Adapter [ACAD] (on-line)
[    0.526974] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.536349] ACPI: Lid Switch [LID]
[    0.536405] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.536411] ACPI: Sleep Button [SLPB]
[    0.536493] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input2
[    0.536497] ACPI: Power Button [PWRB]
[    0.536548] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.536552] ACPI: Power Button [PWRF]
[    0.536867] ACPI: acpi_idle registered with cpuidle
[    0.536927] ACPI: processor limited to max C-state 1
[    0.596517] ACPI: Invalid active0 threshold
[    0.613177] thermal LNXTHERM:01: registered as thermal_zone0
[    0.613187] ACPI: Thermal Zone [THRM] (83 C)
[    0.613287] ERST: Table is not found!
[    0.613361] isapnp: Scanning for PnP cards...
[    0.613606] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.615227] brd: module loaded
[    0.615958] loop: module loaded
[    0.616316] pata_acpi 0000:00:06.0: setting latency timer to 64
[    0.616709] ACPI: PCI Interrupt Link [LSI0] enabled at IRQ 23
[    0.616716]   alloc irq_desc for 23 on node -1
[    0.616719]   alloc kstat_irqs on node -1
[    0.616731] pata_acpi 0000:00:09.0: PCI INT A -> Link[LSI0] -> GSI 23 (level, low) -> IRQ 23
[    0.616750] pata_acpi 0000:00:09.0: setting latency timer to 64
[    0.616758] pata_acpi 0000:00:09.0: PCI INT A disabled
[    0.617204] Fixed MDIO Bus: probed
[    0.617251] PPP generic driver version 2.4.2
[    0.617321] tun: Universal TUN/TAP device driver, 1.6
[    0.617324] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.617429] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.617778] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 22
[    0.617783]   alloc irq_desc for 22 on node -1
[    0.617785]   alloc kstat_irqs on node -1
[    0.617795] ehci_hcd 0000:00:02.1: PCI INT B -> Link[LUS2] -> GSI 22 (level, low) -> IRQ 22
[    0.617818] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    0.617822] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    0.617867] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    0.617899] ehci_hcd 0000:00:02.1: debug port 1
[    0.617908] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    0.617934] ehci_hcd 0000:00:02.1: irq 22, io mem 0xf2689000
[    0.629020] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    0.629175] hub 1-0:1.0: USB hub found
[    0.629181] hub 1-0:1.0: 5 ports detected
[    0.629603] ACPI: PCI Interrupt Link [Z00O] enabled at IRQ 21
[    0.629609]   alloc irq_desc for 21 on node -1
[    0.629612]   alloc kstat_irqs on node -1
[    0.629623] ehci_hcd 0000:00:04.1: PCI INT B -> Link[Z00O] -> GSI 21 (level, low) -> IRQ 21
[    0.629643] ehci_hcd 0000:00:04.1: setting latency timer to 64
[    0.629646] ehci_hcd 0000:00:04.1: EHCI Host Controller
[    0.629697] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 2
[    0.629724] ehci_hcd 0000:00:04.1: debug port 1
[    0.629733] ehci_hcd 0000:00:04.1: cache line size of 64 is not supported
[    0.629758] ehci_hcd 0000:00:04.1: irq 21, io mem 0xf2689400
[    0.641116] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00
[    0.641256] hub 2-0:1.0: USB hub found
[    0.641262] hub 2-0:1.0: 5 ports detected
[    0.641346] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.641812] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 20
[    0.641817]   alloc irq_desc for 20 on node -1
[    0.641819]   alloc kstat_irqs on node -1
[    0.641830] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUS0] -> GSI 20 (level, low) -> IRQ 20
[    0.641848] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    0.641851] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    0.641905] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 3
[    0.641938] ohci_hcd 0000:00:02.0: irq 20, io mem 0xf2686000
[    0.699142] hub 3-0:1.0: USB hub found
[    0.699150] hub 3-0:1.0: 5 ports detected
[    0.699553] ACPI: PCI Interrupt Link [Z00N] enabled at IRQ 23
[    0.699558] ohci_hcd 0000:00:04.0: PCI INT A -> Link[Z00N] -> GSI 23 (level, low) -> IRQ 23
[    0.699578] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    0.699581] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    0.699634] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 4
[    0.699669] ohci_hcd 0000:00:04.0: irq 23, io mem 0xf2687000
[    0.755189] hub 4-0:1.0: USB hub found
[    0.755196] hub 4-0:1.0: 5 ports detected
[    0.755283] uhci_hcd: USB Universal Host Controller Interface driver
[    0.755393] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    0.783451] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.783462] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.783599] mice: PS/2 mouse device common for all mice
[    0.785629] rtc_cmos 00:04: RTC can wake from S4
[    0.785675] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.785716] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    0.786002] device-mapper: uevent: version 1.0.3
[    0.786150] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [email]dm-devel@redhat.com[/email]
[    0.786231] device-mapper: multipath: version 1.1.1 loaded
[    0.786234] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.786375] EISA: Probing bus 0 at eisa.0
[    0.786379] EISA: Cannot allocate resource for mainboard
[    0.786382] Cannot allocate resource for EISA slot 1
[    0.786385] Cannot allocate resource for EISA slot 2
[    0.786388] Cannot allocate resource for EISA slot 3
[    0.786391] Cannot allocate resource for EISA slot 4
[    0.786393] Cannot allocate resource for EISA slot 5
[    0.786396] Cannot allocate resource for EISA slot 6
[    0.786399] Cannot allocate resource for EISA slot 7
[    0.786402] Cannot allocate resource for EISA slot 8
[    0.786404] EISA: Detected 0 cards.
[    0.786489] cpuidle: using governor ladder
[    0.786491] cpuidle: using governor menu
[    0.786840] TCP cubic registered
[    0.786992] NET: Registered protocol family 10
[    0.787433] lo: Disabled Privacy Extensions
[    0.787744] NET: Registered protocol family 17
[    0.787788] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual-Core Processor TK-55 (2 cpu cores) (version 2.20.00)
[    0.787838] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x13
[    0.787841] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0x14
[    0.787844] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x1a
[    0.792510] Using IPI No-Shortcut mode
[    0.792638] PM: Resume from disk failed.
[    0.792653] registered taskstats version 1
[    0.792946]   Magic number: 3:893:785
[    0.793066] rtc_cmos 00:04: setting system clock to 2011-03-04 13:45:18 UTC (1299246318)
[    0.793070] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.793072] EDD information not available.
[    0.810223] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.834846] ACPI: EC: GPE storm detected, transactions will use polling mode
[    0.966321] isapnp: No Plug & Play device found
[    0.966365] Freeing unused kernel memory: 688k freed
[    0.966921] Write protecting the kernel text: 4936k
[    0.966967] Write protecting the kernel read-only data: 1980k
[    0.993159] udev[75]: starting version 163
[    1.000313] ACPI: Battery Slot [BAT1] (battery present)
[    1.135952] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.187704] sdhci: Secure Digital Host Controller Interface driver
[    1.187708] sdhci: Copyright(c) Pierre Ossman
[    1.193080] usb 3-2: new low speed USB device using ohci_hcd and address 2
[    1.203822] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 22
[    1.203837] forcedeth 0000:00:0a.0: PCI INT A -> Link[LMAC] -> GSI 22 (level, low) -> IRQ 22
[    1.203844] forcedeth 0000:00:0a.0: setting latency timer to 64
[    1.211823] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 11
[    1.211842] firewire_ohci 0000:01:04.0: PCI INT A -> Link[LNK1] -> GSI 11 (level, low) -> IRQ 11
[    1.296034] firewire_ohci: Added fw-ohci device 0000:01:04.0, OHCI v1.0, 4 IR + 4 IT contexts, quirks 0x0
[    1.296075] sdhci-pci 0000:01:04.1: SDHCI controller found [1180:0822] (rev 22)
[    1.296471] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 11
[    1.296478] sdhci-pci 0000:01:04.1: PCI INT B -> Link[LNK2] -> GSI 11 (level, low) -> IRQ 11
[    1.297520] sdhci-pci 0000:01:04.1: Will use DMA mode even though HW doesn't fully claim to support it.
[    1.298569] Registered led device: mmc0::
[    1.299603] mmc0: SDHCI controller on PCI [0000:01:04.1] using DMA
[    1.422486] usbcore: registered new interface driver hiddev
[    1.428599] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:02.0/usb3/3-2/3-2:1.0/input/input5
[    1.428733] generic-usb 0003:046D:C018.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:00:02.0-2/input0
[    1.428762] usbcore: registered new interface driver usbhid
[    1.428765] usbhid: USB HID core driver
[    1.725187] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1b:38:c8:3f:3f
[    1.725194] forcedeth 0000:00:0a.0: highdma pwrctl mgmt gbit lnktim msi desc-v3
[    1.725232] pata_amd 0000:00:06.0: version 0.4.1
[    1.725292] pata_amd 0000:00:06.0: setting latency timer to 64
[    1.725399] scsi0 : pata_amd
[    1.725540] scsi1 : pata_amd
[    1.726013] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x30c0 irq 14
[    1.726017] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x30c8 irq 15
[    1.726090] ahci 0000:00:09.0: version 3.0
[    1.726103] ahci 0000:00:09.0: PCI INT A -> Link[LSI0] -> GSI 23 (level, low) -> IRQ 23
[    1.726142] ahci 0000:00:09.0: controller can do NCQ, turning on CAP_NCQ
[    1.726145] ahci 0000:00:09.0: controller can't do PMP, turning off CAP_PMP
[    1.726214] ahci 0000:00:09.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl IDE mode
[    1.726218] ahci 0000:00:09.0: flags: 64bit ncq sntf led clo pio slum part 
[    1.726224] ahci 0000:00:09.0: setting latency timer to 64
[    1.727531] scsi2 : ahci
[    1.727651] scsi3 : ahci
[    1.727732] scsi4 : ahci
[    1.727835] scsi5 : ahci
[    1.728028] ata3: SATA max UDMA/133 irq_stat 0x00400040, connection status changed irq 23
[    1.728032] ata4: SATA max UDMA/133 abar m8192@0xf2684000 port 0xf2684180 irq 23
[    1.728036] ata5: SATA max UDMA/133 abar m8192@0xf2684000 port 0xf2684200 irq 23
[    1.728039] ata6: SATA max UDMA/133 abar m8192@0xf2684000 port 0xf2684280 irq 23
[    1.788136] firewire_core: created device fw0: GUID 00023f7cba405e1a, S400
[    1.888335] ata1.00: ATAPI: HL-DT-ST DVDRAM GSA-T40N, JQ01, max UDMA/33
[    1.888366] ata1: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc000c600) ACPI=0x701f (60:600:0x13)
[    1.904275] ata1.00: configured for UDMA/33
[    1.909841] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T40N  JQ01 PQ: 0 ANSI: 5
[    1.913758] sr0: scsi3-mmc drive: 62x/62x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.913763] Uniform CD-ROM driver Revision: 3.20
[    1.913914] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.914005] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.914122] ata2: port disabled. ignoring.
[    2.048034] ata6: SATA link down (SStatus 0 SControl 300)
[    2.048055] ata4: SATA link down (SStatus 0 SControl 300)
[    2.048080] ata5: SATA link down (SStatus 0 SControl 300)
[    2.452033] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.452439] ata3.00: ATA-7: FUJITSU MHW2160BH PL, 891F, max UDMA/100
[    2.452443] ata3.00: 312581808 sectors, multi 16: LBA48 
[    2.453016] ata3.00: configured for UDMA/100
[    2.453188] scsi 2:0:0:0: Direct-Access     ATA      FUJITSU MHW2160B 891F PQ: 0 ANSI: 5
[    2.453413] sd 2:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    2.453418] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    2.453499] sd 2:0:0:0: [sda] Write Protect is off
[    2.453503] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.453555] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.453794]  sda: sda1 sda2 sda3 < sda5 sda6 >
[    2.534630] sd 2:0:0:0: [sda] Attached SCSI disk
[    3.134189] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   19.260625] Adding 3073020k swap on /dev/sda6.  Priority:-1 extents:1 across:3073020k 
[   19.343224] udev[443]: starting version 163
[   19.697730] lp: driver loaded but no devices found
[   19.700681] lirc_dev: IR Remote Control driver registered, major 249 
[   19.753805] lirc_ene0100: module is from the staging directory, the quality is unknown, you have been warned.
[   19.754680] enecir 00:06: lirc_dev: driver enecir registered at minor = 0
[   19.754743] enecir: KB3926B detected
[   19.754746] enecir: chip is 0x3909 - 0x24, 0xc0
[   19.754749] enecir: driver has been succesfully loaded
[   19.778719] [Firmware Bug]: ACPI(IGPU) defines _DOD but not _DOS
[   19.778995] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input6
[   19.779067] ACPI: Video Device [IGPU] (multi-head: yes  rom: no  post: no)
[   20.007284] i2c i2c-0: nForce2 SMBus adapter at 0x3040
[   20.007312] i2c i2c-1: nForce2 SMBus adapter at 0x3000
[   20.029807] cfg80211: Calling CRDA to update world regulatory domain
[   20.047690] cfg80211: World regulatory domain updated:
[   20.047696]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   20.047700]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.047704]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.047707]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.047710]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.047714]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.117077] Linux agpgart interface v0.103
[   20.122386] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   20.144856] type=1400 audit(1299264337.847:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=725 comm="apparmor_parser"
[   20.145038] type=1400 audit(1299264337.847:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=727 comm="apparmor_parser"
[   20.145205] type=1400 audit(1299264337.851:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=725 comm="apparmor_parser"
[   20.145391] type=1400 audit(1299264337.851:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=727 comm="apparmor_parser"
[   20.145406] type=1400 audit(1299264337.851:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=725 comm="apparmor_parser"
[   20.145598] type=1400 audit(1299264337.851:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=727 comm="apparmor_parser"
[   20.151488] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   20.277873] ACPI: PCI Interrupt Link [LK4E] enabled at IRQ 19
[   20.277883]   alloc irq_desc for 19 on node -1
[   20.277886]   alloc kstat_irqs on node -1
[   20.277900] ath5k 0000:05:00.0: PCI INT A -> Link[LK4E] -> GSI 19 (level, low) -> IRQ 19
[   20.277911] ath5k 0000:05:00.0: setting latency timer to 64
[   20.277977] ath5k 0000:05:00.0: registered as 'phy0'
[   20.592125] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input7
[   20.632729] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input8
[   20.772425] ath: EEPROM regdomain: 0x65
[   20.772430] ath: EEPROM indicates we should expect a direct regpair map
[   20.772435] ath: Country alpha2 being used: 00
[   20.772438] ath: Regpair used: 0x65
[   20.782671] r852 0000:01:04.3: PCI INT B -> Link[LNK2] -> GSI 11 (level, low) -> IRQ 11
[   20.782789] r852: driver loaded succesfully
[   21.278055] phy0: Selected rate control algorithm 'minstrel'
[   21.278788] Registered led device: ath5k-phy0::rx
[   21.278819] Registered led device: ath5k-phy0::tx
[   21.278823] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   21.342122] type=1400 audit(1299264339.047:8): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=881 comm="apparmor_parser"
[   21.342606] type=1400 audit(1299264339.047:9): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=882 comm="apparmor_parser"
[   21.342958] type=1400 audit(1299264339.047:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=882 comm="apparmor_parser"
[   21.343162] type=1400 audit(1299264339.047:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=882 comm="apparmor_parser"
[   21.448776]   alloc irq_desc for 42 on node -1
[   21.448782]   alloc kstat_irqs on node -1
[   21.448795] forcedeth 0000:00:0a.0: irq 42 for MSI/MSI-X
[   21.779927] ath5k phy0: gain calibration timeout (2412MHz)
[   22.121170] ath5k phy0: gain calibration timeout (2412MHz)
[   22.121762] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.621057] ath5k phy0: gain calibration timeout (2412MHz)
[   22.662265] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
[   22.662275] HDA Intel 0000:00:07.0: PCI INT A -> Link[LAZA] -> GSI 21 (level, low) -> IRQ 21
[   22.662280] hda_intel: Disable MSI for Nvidia chipset
[   22.662320] HDA Intel 0000:00:07.0: setting latency timer to 64
[   22.892726] nvidia: module license 'NVIDIA' taints kernel.
[   22.892732] Disabling lock debugging due to kernel taint
[   23.001062] ath5k phy0: gain calibration timeout (2417MHz)

---

### Post by colmesany on 2011-03-04
Please post up the error message or print screen (using your mobile), the specs are not usually the culprit.

---

### Post by ben889 on 2011-03-07
Sorry for the delay in resonse but i was told to post these 2 logs, what logs should i be posting? so far i haven't gotten a crash report or message.


Thanks Ben

---

### Post by TechWiz2100 on 2011-03-07
> **ben889 said:**
> want to post my log files but i keep getting this

**Fatal error**:  Maximum execution time of 60 seconds exceeded in **/srv/www.ubuntuforums.org/public_html/includes/functions.php** on line **1838**

how should i post my log files?

Post them into a text file and upload the text file instead.

Oh and bumping this for you lol

---

### Post by ben889 on 2011-03-07
I had successfully posted 2 logs but i was told they were the wrong ones so which ones do i post what are the error logs?

---

### Post by ben889 on 2011-03-08
bump

---

### Post by ben889 on 2011-03-09
bump

---

### Post by ben889 on 2011-03-10
anyone?

---

### Post by ben889 on 2011-03-11
Someone should be able to answer this

---

### Post by TechWiz2100 on 2011-03-12
Alright I'll take a crack at it then...

System > Administration > Log File Viewer

Post a file for each of the following logs:
all the dmesg
debug
kern.log
messages (last crash)

---

### Post by ben889 on 2011-04-10
Ubuntu works good now apparently i was crashing due to heat. when i opened my laptop i couldnt see any dust so i figured my CPU heat sink was clean apparently it wasn't

---

