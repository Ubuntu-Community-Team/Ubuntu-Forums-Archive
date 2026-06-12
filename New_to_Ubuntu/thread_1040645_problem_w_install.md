---
title: "problem w install"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by tpd2049 on 2009-01-15
I have been trying to install the newest version on a Dell Dimension 2300 w/ substancial memory. I performed a clean install and it seemed to go fine. I restarted when prompted and the login came on. After a while a brown screen came up w/ the "wheel". Eventually the screen changed to blank w/ nothing but he mouse arrow, and the Hard drive stopped kicking. This is the second time I installed and the same thing happened before. Anyone know whats going on?

---

### Post by mjheagle8 on 2009-01-15
what brand and type graphics card do you have?

---

### Post by tpd2049 on 2009-01-15
i dont really know...it was stock on the dell dimension 2300 box

---

### Post by mjheagle8 on 2009-01-15
> **tpd2049 said:**
> i dont really know...it was stock on the dell dimension 2300 box

ok, you need to find out. try booting off the live cd. then start up a terminal.  please run these commands and post the output so we can ascertain what graphics card you have. 
```
lshw
```
```
lspci
```
these commands list your hardware and pci cards, respectively.

---

### Post by tpd2049 on 2009-01-15
will do...thx!!!

---

### Post by mjheagle8 on 2009-01-15
no problem. glad to be able to help!

---

### Post by tpd2049 on 2009-01-15
obviously im new to linux...how do i start terminal mode??

---

### Post by mjheagle8 on 2009-01-15
you dont need to start in terminal. just open a terminal. you can find it by going to applications>accessories>terminal.

---

### Post by tpd2049 on 2009-01-15
the same problem w/ black screen was happening in live cd...i just opened with safe graphic mode...guess that means it is a graphic card problem here is the info:
buntu@ubuntu:~$ 1shw
bash: 1shw: command not found
ubuntu@ubuntu:~$ lshw
WARNING: you should run this program as super-user.
ubuntu                    
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 766MiB
     *-cpu
          product: Intel(R) Celeron(R) CPU 1.80GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.1.3
          size: 1800MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm up pebs bts
          configuration: id=0
        *-cache
             description: L1 cache
             physical id: 0
             size: 8KiB
     *-pci
          description: Host bridge
          product: 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display UNCLAIMED
             description: VGA compatible controller
             product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
           *-communication
                description: Modem
                product: BCM4212 v.90 56k modem
                vendor: Broadcom Corporation
                physical id: 4
                bus info: pci@0000:01:04.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=serial latency=32
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 5
                bus info: pci@0000:01:05.0
                logical name: eth0
                version: 10
                serial: 00:c0:a8:8e:f6:f3
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes
        *-isa
             description: ISA bridge
             product: 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801DB (ICH4) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0 module=ata_piix
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 5e:98:9b:0d:1c:87
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:04.0 Modem: Broadcom Corporation BCM4212 v.90 56k modem (rev 02)
01:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
ubuntu@ubuntu:~$ 

Thanks again!!

---

### Post by mjheagle8 on 2009-01-15
ok, it looks like this is referring to your graphics card:
```
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
```
and 
```
*-display UNCLAIMED
description: VGA compatible controller
product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
vendor: Intel Corporation
physical id: 2
bus info: pci@0000:00:02.0
version: 01
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list
configuration: latency=0
```
the problem here looks like it comes from the first line in the second code segment, saying 'DISABLED'. that means that there is no driver allocated to it, i believe. i will look it up and reply with what i find soon.

---

### Post by mjheagle8 on 2009-01-15
it doesnt look like there should be a problem with this card. hmm. can you try booting in safe graphics mode? also, look at [https://help.ubuntu.com/community/BootOptions]("https://help.ubuntu.com/community/BootOptions") and try booting without the splash. see if there are any problems with the boot by watching to see if anything fails during the boot process.

---

### Post by tpd2049 on 2009-01-15
thanks for your time & trouble...its greatly appreciated, ive been pulling my hair out!

---

### Post by mjheagle8 on 2009-01-15
no problem, my pleasure. anything to spread ubuntu! did you try either of those? any luck?

---

### Post by tpd2049 on 2009-01-15
dont know how to boot off the hd in safe graphics mode but the only way i could get live cd to work was in safe graphics mode.  i removed splash and it seemed to boot ok but froze on brown screen after login?

---

### Post by mjheagle8 on 2009-01-15
there were no errors during boot? hmm. that complicates things. can you view your logs and see if there were any errors that may not have showed up?

---

### Post by tpd2049 on 2009-01-15
where can i view logs?

---

### Post by mjheagle8 on 2009-01-15
system>administration>system log

---

### Post by tpd2049 on 2009-01-15
wow...here it is...its way to technical for me to interpret....
Jan 16 02:43:01 ubuntu syslogd 1.5.0#2ubuntu6: restart.
Jan 16 02:43:02 ubuntu kernel: Inspecting /boot/System.map-2.6.27-7-generic
Jan 16 02:43:03 ubuntu kernel: Cannot find map file.
Jan 16 02:43:04 ubuntu kernel: Loaded 47623 symbols from 86 modules.
Jan 16 02:43:04 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpuset
Jan 16 02:43:04 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpu
Jan 16 02:43:04 ubuntu kernel: [    0.000000] Linux version 2.6.27-7-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu10) ) #1 SMP Fri Oct 24 06:42:44 UTC 2008 (Ubuntu 2.6.27-7.14-generic)
Jan 16 02:43:04 ubuntu kernel: [    0.000000] BIOS-provided physical RAM map:
Jan 16 02:43:04 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Jan 16 02:43:04 ubuntu kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Jan 16 02:43:04 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Jan 16 02:43:04 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000002fef0000 (usable)
Jan 16 02:43:04 ubuntu kernel: [    0.000000]  BIOS-e820: 000000002fef0000 - 000000002fef3000 (ACPI NVS)
Jan 16 02:43:04 ubuntu kernel: [    0.000000]  BIOS-e820: 000000002fef3000 - 000000002ff00000 (ACPI data)
Jan 16 02:43:04 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Jan 16 02:43:04 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Jan 16 02:43:04 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
Jan 16 02:43:04 ubuntu kernel: [    0.000000] last_pfn = 0x2fef0 max_arch_pfn = 0x100000
Jan 16 02:43:04 ubuntu kernel: [    0.000000] RAMDISK: 2f6b1000 - 2febf8ae
Jan 16 02:43:04 ubuntu kernel: [    0.000000] DMI 2.3 present.
Jan 16 02:43:04 ubuntu kernel: [    0.000000] ACPI: RSDP 000F6E40, 0014 (r0 IntelR)
Jan 16 02:43:04 ubuntu kernel: [    0.000000] ACPI: RSDT 2FEF3000, 0030 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
Jan 16 02:43:04 ubuntu kernel: [    0.000000] ACPI: FACP 2FEF3040, 0074 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
Jan 16 02:43:04 ubuntu kernel: [    0.000000] ACPI: DSDT 2FEF30C0, 386E (r1 INTELR AWRDACPI     1000 MSFT  100000C)
Jan 16 02:43:04 ubuntu kernel: [    0.000000] ACPI: FACS 2FEF0000, 0040
Jan 16 02:43:04 ubuntu kernel: [    0.000000] ACPI: BOOT 2FEF6940, 0028 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
Jan 16 02:43:04 ubuntu kernel: [    0.000000] ACPI: APIC 2FEF6980, 0054 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
Jan 16 02:43:04 ubuntu kernel: [    0.000000] 0MB HIGHMEM available.
Jan 16 02:43:04 ubuntu kernel: [    0.000000] 766MB LOWMEM available.
Jan 16 02:43:04 ubuntu kernel: [    0.000000]   mapped low ram: 0 - 2fef0000
Jan 16 02:43:04 ubuntu kernel: [    0.000000]   low ram: 00000000 - 2fef0000
Jan 16 02:43:04 ubuntu kernel: [    0.000000]   bootmap 00009000 - 0000efe0
Jan 16 02:43:04 ubuntu kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 002fef0000]
Jan 16 02:43:04 ubuntu kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Jan 16 02:43:04 ubuntu kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Jan 16 02:43:04 ubuntu kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Jan 16 02:43:04 ubuntu kernel: [    0.000000]   #3 [0000100000 - 00005c0a20]    TEXT DATA BSS ==> [0000100000 - 00005c0a20]
Jan 16 02:43:04 ubuntu kernel: [    0.000000]   #4 [002f6b1000 - 002febf8ae]          RAMDISK ==> [002f6b1000 - 002febf8ae]
Jan 16 02:43:04 ubuntu kernel: [    0.000000]   #5 [00005c1000 - 00005c4000]    INIT_PG_TABLE ==> [00005c1000 - 00005c4000]
Jan 16 02:43:04 ubuntu kernel: [    0.000000]   #6 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
Jan 16 02:43:04 ubuntu kernel: [    0.000000]   #7 [0000007000 - 0000009000]          PGTABLE ==> [0000007000 - 0000009000]
Jan 16 02:43:04 ubuntu kernel: [    0.000000]   #8 [0000009000 - 000000f000]          BOOTMAP ==> [0000009000 - 000000f000]
Jan 16 02:43:04 ubuntu kernel: [    0.000000] found SMP MP-table at [c00f4ca0] 000f4ca0
Jan 16 02:43:04 ubuntu kernel: [    0.000000] Zone PFN ranges:
Jan 16 02:43:04 ubuntu kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Jan 16 02:43:04 ubuntu kernel: [    0.000000]   Normal   0x00001000 -> 0x0002fef0
Jan 16 02:43:04 ubuntu kernel: [    0.000000]   HighMem  0x0002fef0 -> 0x0002fef0
Jan 16 02:43:04 ubuntu kernel: [    0.000000] Movable zone start PFN for each node
Jan 16 02:43:04 ubuntu kernel: [    0.000000] early_node_map[2] active PFN ranges
Jan 16 02:43:04 ubuntu kernel: [    0.000000]     0: 0x00000000 -> 0x0000009f
Jan 16 02:43:04 ubuntu kernel: [    0.000000]     0: 0x00000100 -> 0x0002fef0
Jan 16 02:43:04 ubuntu kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Jan 16 02:43:04 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jan 16 02:43:04 ubuntu kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Jan 16 02:43:04 ubuntu kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Jan 16 02:43:04 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jan 16 02:43:04 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jan 16 02:43:04 ubuntu kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Jan 16 02:43:04 ubuntu kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jan 16 02:43:04 ubuntu kernel: [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
Jan 16 02:43:04 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan 16 02:43:04 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Jan 16 02:43:04 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Jan 16 02:43:04 ubuntu kernel: [    0.000000] Allocating PCI resources starting at 30000000 (gap: 2ff00000:ced00000)
Jan 16 02:43:04 ubuntu kernel: [    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
Jan 16 02:43:04 ubuntu kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 194513
Jan 16 02:43:04 ubuntu kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash -- xforcevesa
Jan 16 02:43:04 ubuntu kernel: [    0.000000] Enabling fast FPU save and restore... done.
Jan 16 02:43:04 ubuntu kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Jan 16 02:43:04 ubuntu kernel: [    0.000000] Initializing CPU#0
Jan 16 02:43:04 ubuntu kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Jan 16 02:43:04 ubuntu kernel: [    0.000000] TSC: Unable to calibrate against PIT
Jan 16 02:43:04 ubuntu kernel: [    0.000000] TSC: using PMTIMER reference calibration
Jan 16 02:43:04 ubuntu kernel: [    0.000000] Detected 1794.166 MHz processor.
Jan 16 02:43:04 ubuntu kernel: [    0.004000] Console: colour VGA+ 80x25
Jan 16 02:43:04 ubuntu kernel: [    0.004000] console [tty0] enabled
Jan 16 02:43:04 ubuntu kernel: [    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jan 16 02:43:04 ubuntu kernel: [    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jan 16 02:43:04 ubuntu kernel: [    0.004000] Memory: 763844k/785344k available (2572k kernel code, 20928k reserved, 1160k data, 424k init, 0k highmem)
Jan 16 02:43:04 ubuntu kernel: [    0.004000] virtual kernel memory layout:
Jan 16 02:43:04 ubuntu kernel: [    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
Jan 16 02:43:04 ubuntu kernel: [    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
Jan 16 02:43:04 ubuntu kernel: [    0.004000]     vmalloc : 0xf0800000 - 0xff3fe000   ( 235 MB)
Jan 16 02:43:04 ubuntu kernel: [    0.004000]     lowmem  : 0xc0000000 - 0xefef0000   ( 766 MB)
Jan 16 02:43:04 ubuntu kernel: [    0.004000]       .init : 0xc04ab000 - 0xc0515000   ( 424 kB)
Jan 16 02:43:04 ubuntu kernel: [    0.004000]       .data : 0xc038329a - 0xc04a5680   (1160 kB)
Jan 16 02:43:04 ubuntu kernel: [    0.004000]       .text : 0xc0100000 - 0xc038329a   (2572 kB)
Jan 16 02:43:04 ubuntu kernel: [    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Jan 16 02:43:04 ubuntu kernel: [    0.004000] SLUB: Genslabs=12, HWalign=128, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
Jan 16 02:43:04 ubuntu kernel: [    0.004026] Calibrating delay loop (skipped), value calculated using timer frequency.. 3588.33 BogoMIPS (lpj=7176664)
Jan 16 02:43:04 ubuntu kernel: [    0.004078] Security Framework initialized
Jan 16 02:43:04 ubuntu kernel: [    0.004096] SELinux:  Disabled at boot.
Jan 16 02:43:04 ubuntu kernel: [    0.004145] AppArmor: AppArmor initialized
Jan 16 02:43:04 ubuntu kernel: [    0.004174] Mount-cache hash table entries: 512
Jan 16 02:43:04 ubuntu kernel: [    0.004652] Initializing cgroup subsys ns
Jan 16 02:43:04 ubuntu kernel: [    0.004671] Initializing cgroup subsys cpuacct
Jan 16 02:43:04 ubuntu kernel: [    0.004679] Initializing cgroup subsys memory
Jan 16 02:43:04 ubuntu kernel: [    0.004727] CPU: Trace cache: 12K uops, L1 D cache: 8K
Jan 16 02:43:04 ubuntu kernel: [    0.004734] CPU: L2 cache: 128K
Jan 16 02:43:04 ubuntu kernel: [    0.004738] CPU: Hyper-Threading is disabled
Jan 16 02:43:04 ubuntu kernel: [    0.004781] Checking 'hlt' instruction... OK.
Jan 16 02:43:04 ubuntu kernel: [    0.020945] SMP alternatives: switching to UP code
Jan 16 02:43:04 ubuntu kernel: [    0.032077] Freeing SMP alternatives: 11k freed
Jan 16 02:43:04 ubuntu kernel: [    0.032088] ACPI: Core revision 20080609
Jan 16 02:43:04 ubuntu kernel: [    0.037547] ACPI: Checking initramfs for custom DSDT
Jan 16 02:43:04 ubuntu kernel: [    0.620526] ENABLING IO-APIC IRQs
Jan 16 02:43:04 ubuntu kernel: [    0.620810] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Jan 16 02:43:04 ubuntu kernel: [    0.661341] CPU0: Intel(R) Celeron(R) CPU 1.80GHz stepping 03
Jan 16 02:43:04 ubuntu kernel: [    0.664031] Brought up 1 CPUs
Jan 16 02:43:04 ubuntu kernel: [    0.664031] Total of 1 processors activated (3588.33 BogoMIPS).
Jan 16 02:43:04 ubuntu kernel: [    0.664031] net_namespace: 840 bytes
Jan 16 02:43:04 ubuntu kernel: [    0.664031] Booting paravirtualized kernel on bare hardware
Jan 16 02:43:04 ubuntu kernel: [    0.664031] Time:  2:37:57  Date: 01/16/09
Jan 16 02:43:04 ubuntu kernel: [    0.664031] NET: Registered protocol family 16
Jan 16 02:43:04 ubuntu kernel: [    0.666341] EISA bus registered
Jan 16 02:43:04 ubuntu kernel: [    0.666443] ACPI: bus type pci registered
Jan 16 02:43:04 ubuntu kernel: [    0.710333] PCI: PCI BIOS revision 2.10 entry at 0xfaeb0, last bus=1
Jan 16 02:43:04 ubuntu kernel: [    0.710347] PCI: Using configuration type 1 for base access
Jan 16 02:43:04 ubuntu kernel: [    0.741307] ACPI: Interpreter enabled
Jan 16 02:43:04 ubuntu kernel: [    0.741334] ACPI: (supports S0 S1 S3 S4 S5)
Jan 16 02:43:04 ubuntu kernel: [    0.741416] ACPI: Using IOAPIC for interrupt routing
Jan 16 02:43:04 ubuntu kernel: [    0.775686] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jan 16 02:43:04 ubuntu kernel: [    0.777232] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Jan 16 02:43:04 ubuntu kernel: [    0.777248] pci 0000:00:1d.7: PME# disabled
Jan 16 02:43:04 ubuntu kernel: [    0.777370] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
Jan 16 02:43:04 ubuntu kernel: [    0.777376] * this clock source is slow. If you are sure your timer does not have
Jan 16 02:43:04 ubuntu kernel: [    0.777380] * this bug, please use "acpi_pm_good" to disable the workaround
Jan 16 02:43:04 ubuntu kernel: [    0.777476] HPET not enabled in BIOS. You might try hpet=force boot option
Jan 16 02:43:04 ubuntu kernel: [    0.777498] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
Jan 16 02:43:04 ubuntu kernel: [    0.777511] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH4 GPIO
Jan 16 02:43:04 ubuntu kernel: [    0.777990] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
Jan 16 02:43:04 ubuntu kernel: [    0.778005] pci 0000:00:1f.5: PME# disabled
Jan 16 02:43:04 ubuntu kernel: [    0.778229] pci 0000:01:04.0: PME# supported from D0 D1 D2 D3hot D3cold
Jan 16 02:43:04 ubuntu kernel: [    0.778242] pci 0000:01:04.0: PME# disabled
Jan 16 02:43:04 ubuntu kernel: [    0.778432] pci 0000:01:05.0: PME# supported from D1 D2 D3hot D3cold
Jan 16 02:43:04 ubuntu kernel: [    0.778445] pci 0000:01:05.0: PME# disabled
Jan 16 02:43:04 ubuntu kernel: [    0.778520] pci 0000:00:1e.0: transparent bridge
Jan 16 02:43:04 ubuntu kernel: [    0.855715] ACPI: PCI Interrupt Link [LNKA] (IRQs *3 4 5 7 9 10 11 12 14 15)
Jan 16 02:43:04 ubuntu kernel: [    0.856386] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 *11 12 14 15)
Jan 16 02:43:04 ubuntu kernel: [    0.856964] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12 14 15)
Jan 16 02:43:04 ubuntu kernel: [    0.857555] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 7 9 10 11 12 14 15)
Jan 16 02:43:04 ubuntu kernel: [    0.858120] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Jan 16 02:43:04 ubuntu kernel: [    0.858682] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Jan 16 02:43:04 ubuntu kernel: [    0.859232] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Jan 16 02:43:04 ubuntu kernel: [    0.859786] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 7 *9 10 11 12 14 15)
Jan 16 02:43:04 ubuntu kernel: [    0.861255] Linux Plug and Play Support v0.97 (c) Adam Belay
Jan 16 02:43:04 ubuntu kernel: [    0.861628] pnp: PnP ACPI init
Jan 16 02:43:04 ubuntu kernel: [    0.861685] ACPI: bus type pnp registered
Jan 16 02:43:04 ubuntu kernel: [    0.881436] pnp: PnP ACPI: found 13 devices
Jan 16 02:43:04 ubuntu kernel: [    0.881453] ACPI: ACPI bus type pnp unregistered
Jan 16 02:43:04 ubuntu kernel: [    0.881472] PnPBIOS: Disabled by ACPI PNP
Jan 16 02:43:04 ubuntu kernel: [    0.885660] PCI: Using ACPI for IRQ routing
Jan 16 02:43:04 ubuntu kernel: [    0.886452] NET: Registered protocol family 8
Jan 16 02:43:04 ubuntu kernel: [    0.886452] NET: Registered protocol family 20
Jan 16 02:43:04 ubuntu kernel: [    0.886452] NetLabel: Initializing
Jan 16 02:43:04 ubuntu kernel: [    0.886452] NetLabel:  domain hash size = 128
Jan 16 02:43:04 ubuntu kernel: [    0.886452] NetLabel:  protocols = UNLABELED CIPSOv4
Jan 16 02:43:04 ubuntu kernel: [    0.886452] NetLabel:  unlabeled traffic allowed by default
Jan 16 02:43:04 ubuntu kernel: [    0.888350] tracer: 772 pages allocated for 65536 entries of 48 bytes
Jan 16 02:43:04 ubuntu kernel: [    0.888360]    actual entries 65620
Jan 16 02:43:04 ubuntu kernel: [    0.889104] AppArmor: AppArmor Filesystem Enabled
Jan 16 02:43:04 ubuntu kernel: [    0.889178] ACPI: RTC can wake from S4
Jan 16 02:43:04 ubuntu kernel: [    0.889544] system 00:00: iomem range 0xcc000-0xcffff has been reserved
Jan 16 02:43:04 ubuntu kernel: [    0.889560] system 00:00: iomem range 0xf0000-0xf7fff could not be reserved
Jan 16 02:43:04 ubuntu kernel: [    0.889570] system 00:00: iomem range 0xf8000-0xfbfff could not be reserved
Jan 16 02:43:04 ubuntu kernel: [    0.889579] system 00:00: iomem range 0xfc000-0xfffff could not be reserved
Jan 16 02:43:04 ubuntu kernel: [    0.889589] system 00:00: iomem range 0x2fef0000-0x2fefffff could not be reserved
Jan 16 02:43:04 ubuntu kernel: [    0.889599] system 00:00: iomem range 0x0-0x9ffff could not be reserved
Jan 16 02:43:04 ubuntu kernel: [    0.889609] system 00:00: iomem range 0x100000-0x2feeffff could not be reserved
Jan 16 02:43:04 ubuntu kernel: [    0.889621] system 00:00: iomem range 0xfec00000-0xfec00fff could not be reserved
Jan 16 02:43:04 ubuntu kernel: [    0.889631] system 00:00: iomem range 0xfee00000-0xfee00fff could not be reserved
Jan 16 02:43:04 ubuntu kernel: [    0.889641] system 00:00: iomem range 0xffb00000-0xffbfffff could not be reserved
Jan 16 02:43:04 ubuntu kernel: [    0.889653] system 00:00: iomem range 0xfff00000-0xffffffff could not be reserved
Jan 16 02:43:04 ubuntu kernel: [    0.889662] system 00:00: iomem range 0xe0000-0xeffff has been reserved
Jan 16 02:43:04 ubuntu kernel: [    0.889695] system 00:02: ioport range 0x400-0x4bf could not be reserved
Jan 16 02:43:04 ubuntu kernel: [    0.889718] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
Jan 16 02:43:04 ubuntu kernel: [    0.889730] system 00:03: ioport range 0x800-0x87f has been reserved
Jan 16 02:43:04 ubuntu kernel: [    0.930239] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:01
Jan 16 02:43:04 ubuntu kernel: [    0.930259] pci 0000:00:1e.0:   IO window: 0xc000-0xcfff
Jan 16 02:43:04 ubuntu kernel: [    0.930275] pci 0000:00:1e.0:   MEM window: 0xec000000-0xec0fffff
Jan 16 02:43:04 ubuntu kernel: [    0.930288] pci 0000:00:1e.0:   PREFETCH window: disabled
Jan 16 02:43:04 ubuntu kernel: [    0.930357] bus: 00 index 0 io port: [0, ffff]
Jan 16 02:43:04 ubuntu kernel: [    0.930367] bus: 00 index 1 mmio: [0, ffffffff]
Jan 16 02:43:04 ubuntu kernel: [    0.930376] bus: 01 index 0 io port: [c000, cfff]
Jan 16 02:43:04 ubuntu kernel: [    0.930386] bus: 01 index 1 mmio: [ec000000, ec0fffff]
Jan 16 02:43:04 ubuntu kernel: [    0.930395] bus: 01 index 2 mmio: [0, 0]
Jan 16 02:43:04 ubuntu kernel: [    0.930401] bus: 01 index 3 io port: [0, ffff]
Jan 16 02:43:04 ubuntu kernel: [    0.930407] bus: 01 index 4 mmio: [0, ffffffff]
Jan 16 02:43:04 ubuntu kernel: [    0.930471] NET: Registered protocol family 2
Jan 16 02:43:04 ubuntu kernel: [    0.931172] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Jan 16 02:43:04 ubuntu kernel: [    0.932583] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Jan 16 02:43:04 ubuntu kernel: [    0.935916] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Jan 16 02:43:04 ubuntu kernel: [    0.937707] TCP: Hash tables configured (established 131072 bind 65536)
Jan 16 02:43:04 ubuntu kernel: [    0.937733] TCP reno registered
Jan 16 02:43:04 ubuntu kernel: [    0.938358] NET: Registered protocol family 1
Jan 16 02:43:04 ubuntu kernel: [    0.938889] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
Jan 16 02:43:04 ubuntu kernel: [    2.190330]  it is
Jan 16 02:43:04 ubuntu kernel: [    5.058266] Freeing initrd memory: 8250k freed
Jan 16 02:43:04 ubuntu kernel: [    5.060535] Simple Boot Flag at 0x59 set to 0x1
Jan 16 02:43:04 ubuntu kernel: [    5.070670] audit: initializing netlink socket (disabled)
Jan 16 02:43:04 ubuntu kernel: [    5.070805] type=2000 audit(1232073481.068:1): initialized
Jan 16 02:43:04 ubuntu kernel: [    5.102441] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Jan 16 02:43:04 ubuntu kernel: [    5.145446] VFS: Disk quotas dquot_6.5.1
Jan 16 02:43:04 ubuntu kernel: [    5.146884] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jan 16 02:43:04 ubuntu kernel: [    5.148954] msgmni has been set to 1508
Jan 16 02:43:04 ubuntu kernel: [    5.151120] io scheduler noop registered
Jan 16 02:43:04 ubuntu kernel: [    5.151154] io scheduler anticipatory registered
Jan 16 02:43:04 ubuntu kernel: [    5.151180] io scheduler deadline registered
Jan 16 02:43:04 ubuntu kernel: [    5.151436] io scheduler cfq registered (default)
Jan 16 02:43:05 ubuntu kernel: [    5.158704] isapnp: Scanning for PnP cards...
Jan 16 02:43:05 ubuntu kernel: [    5.521481] isapnp: No Plug & Play device found
Jan 16 02:43:05 ubuntu kernel: [    6.117810] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
Jan 16 02:43:05 ubuntu kernel: [    6.118490] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jan 16 02:43:05 ubuntu kernel: [    6.126780] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jan 16 02:43:05 ubuntu kernel: [    6.129064] serial 0000:01:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan 16 02:43:05 ubuntu kernel: [    6.153132] brd: module loaded
Jan 16 02:43:05 ubuntu kernel: [    6.153735] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Jan 16 02:43:05 ubuntu kernel: [    6.154748] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Jan 16 02:43:05 ubuntu kernel: [    6.158704] serio: i8042 KBD port at 0x60,0x64 irq 1
Jan 16 02:43:05 ubuntu kernel: [    6.158757] serio: i8042 AUX port at 0x60,0x64 irq 12
Jan 16 02:43:05 ubuntu kernel: [    6.163169] mice: PS/2 mouse device common for all mice
Jan 16 02:43:05 ubuntu kernel: [    6.165061] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
Jan 16 02:43:05 ubuntu kernel: [    6.165146] rtc0: alarms up to one month
Jan 16 02:43:05 ubuntu kernel: [    6.166496] EISA: Probing bus 0 at eisa.0
Jan 16 02:43:05 ubuntu kernel: [    6.166583] EISA: Detected 0 cards.
Jan 16 02:43:05 ubuntu kernel: [    6.166600] cpuidle: using governor ladder
Jan 16 02:43:05 ubuntu kernel: [    6.166609] cpuidle: using governor menu
Jan 16 02:43:05 ubuntu kernel: [    6.169097] TCP cubic registered
Jan 16 02:43:05 ubuntu kernel: [    6.169340] Using IPI No-Shortcut mode
Jan 16 02:43:05 ubuntu kernel: [    6.172886] registered taskstats version 1
Jan 16 02:43:05 ubuntu kernel: [    6.173332]   Magic number: 9:958:611
Jan 16 02:43:05 ubuntu kernel: [    6.173600] tty ptye1: hash matches
Jan 16 02:43:05 ubuntu kernel: [    6.173895] rtc_cmos 00:05: setting system clock to 2009-01-16 02:38:03 UTC (1232073483)
Jan 16 02:43:05 ubuntu kernel: [    6.173909] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jan 16 02:43:05 ubuntu kernel: [    6.173915] EDD information not available.
Jan 16 02:43:05 ubuntu kernel: [    6.175514] Freeing unused kernel memory: 424k freed
Jan 16 02:43:05 ubuntu kernel: [    6.175699] Write protecting the kernel text: 2576k
Jan 16 02:43:05 ubuntu kernel: [    6.175807] Write protecting the kernel read-only data: 936k
Jan 16 02:43:05 ubuntu kernel: [    6.198325] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Jan 16 02:43:05 ubuntu kernel: [    6.907081] fuse init (API version 7.9)
Jan 16 02:43:05 ubuntu kernel: [    7.200421] fan PNP0C0B:00: registered as cooling_device0
Jan 16 02:43:05 ubuntu kernel: [    7.200470] ACPI: Fan [FAN] (on)
Jan 16 02:43:05 ubuntu kernel: [    7.298849] processor ACPI0007:00: registered as cooling_device1
Jan 16 02:43:05 ubuntu kernel: [    7.298878] ACPI: Processor [CPU0] (supports 2 throttling states)
Jan 16 02:43:05 ubuntu kernel: [    7.351641] thermal LNXTHERM:01: registered as thermal_zone0
Jan 16 02:43:05 ubuntu kernel: [    7.400725] ACPI: Thermal Zone [THRM] (-116 C)
Jan 16 02:43:05 ubuntu kernel: [   11.152640] usbcore: registered new interface driver usbfs
Jan 16 02:43:05 ubuntu kernel: [   11.152894] usbcore: registered new interface driver hub
Jan 16 02:43:05 ubuntu kernel: [   11.211443] usbcore: registered new device driver usb
Jan 16 02:43:05 ubuntu kernel: [   11.269787] No dock devices found.
Jan 16 02:43:05 ubuntu kernel: [   13.099186] SCSI subsystem initialized
Jan 16 02:43:05 ubuntu kernel: [   13.159809] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Jan 16 02:43:05 ubuntu kernel: [   13.177767] USB Universal Host Controller Interface driver v3.0
Jan 16 02:43:05 ubuntu kernel: [   13.177998] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan 16 02:43:05 ubuntu kernel: [   13.178048] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Jan 16 02:43:05 ubuntu kernel: [   13.178304] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Jan 16 02:43:05 ubuntu kernel: [   13.178408] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000d800
Jan 16 02:43:05 ubuntu kernel: [   13.179342] usb usb1: configuration #1 chosen from 1 choice
Jan 16 02:43:05 ubuntu kernel: [   13.179512] hub 1-0:1.0: USB hub found
Jan 16 02:43:05 ubuntu kernel: [   13.179569] hub 1-0:1.0: 2 ports detected
Jan 16 02:43:05 ubuntu kernel: [   13.285833] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Jan 16 02:43:05 ubuntu kernel: [   13.285886] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Jan 16 02:43:05 ubuntu kernel: [   13.286073] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Jan 16 02:43:05 ubuntu kernel: [   13.286178] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d000
Jan 16 02:43:05 ubuntu kernel: [   13.287062] usb usb2: configuration #1 chosen from 1 choice
Jan 16 02:43:05 ubuntu kernel: [   13.287264] hub 2-0:1.0: USB hub found
Jan 16 02:43:05 ubuntu kernel: [   13.287323] hub 2-0:1.0: 2 ports detected
Jan 16 02:43:05 ubuntu kernel: [   13.336368] 8139too Fast Ethernet driver 0.9.28
Jan 16 02:43:05 ubuntu kernel: [   13.389938] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jan 16 02:43:05 ubuntu kernel: [   13.389994] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Jan 16 02:43:05 ubuntu kernel: [   13.390190] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Jan 16 02:43:05 ubuntu kernel: [   13.390299] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d400
Jan 16 02:43:05 ubuntu kernel: [   13.391237] usb usb3: configuration #1 chosen from 1 choice
Jan 16 02:43:05 ubuntu kernel: [   13.391413] hub 3-0:1.0: USB hub found
Jan 16 02:43:05 ubuntu kernel: [   13.391477] hub 3-0:1.0: 2 ports detected
Jan 16 02:43:05 ubuntu kernel: [   13.494185] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
Jan 16 02:43:05 ubuntu kernel: [   13.494265] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Jan 16 02:43:05 ubuntu kernel: [   13.494457] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
Jan 16 02:43:05 ubuntu kernel: [   13.498543] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xec180000
Jan 16 02:43:05 ubuntu kernel: [   13.512127] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jan 16 02:43:05 ubuntu kernel: [   13.513011] usb usb4: configuration #1 chosen from 1 choice
Jan 16 02:43:05 ubuntu kernel: [   13.513174] hub 4-0:1.0: USB hub found
Jan 16 02:43:05 ubuntu kernel: [   13.513231] hub 4-0:1.0: 6 ports detected
Jan 16 02:43:05 ubuntu kernel: [   13.623411] 8139too 0000:01:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jan 16 02:43:05 ubuntu kernel: [   13.625397] eth0: RealTek RTL8139 at 0xc400, 00:c0:a8:8e:f6:f3, IRQ 17
Jan 16 02:43:05 ubuntu kernel: [   13.649917] pata_acpi 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jan 16 02:43:05 ubuntu kernel: [   13.650140] pata_acpi 0000:00:1f.1: PCI INT A disabled
Jan 16 02:43:05 ubuntu kernel: [   13.677219] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jan 16 02:43:05 ubuntu kernel: [   13.682742] scsi0 : ata_piix
Jan 16 02:43:05 ubuntu kernel: [   13.683380] scsi1 : ata_piix
Jan 16 02:43:05 ubuntu kernel: [   13.686907] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
Jan 16 02:43:05 ubuntu kernel: [   13.686921] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
Jan 16 02:43:05 ubuntu kernel: [   13.849824] ata1.00: ATA-5: WDC WD300EB-75CPF0, 06.04G06, max UDMA/100
Jan 16 02:43:05 ubuntu kernel: [   13.849841] ata1.00: 58633344 sectors, multi 16: LBA 
Jan 16 02:43:05 ubuntu kernel: [   13.865799] ata1.00: configured for UDMA/100
Jan 16 02:43:05 ubuntu kernel: [   14.020551] ata2.01: failed to IDENTIFY (I/O error, err_mask=0x1)
Jan 16 02:43:05 ubuntu kernel: [   19.176263] ata2.01: failed to IDENTIFY (I/O error, err_mask=0x1)
Jan 16 02:43:05 ubuntu kernel: [   24.332264] ata2.01: failed to IDENTIFY (I/O error, err_mask=0x1)
Jan 16 02:43:05 ubuntu kernel: [   29.496451] ata2.00: ATAPI: SAMSUNG CD-R/RW SW-240B, BD11, max UDMA/33
Jan 16 02:43:05 ubuntu kernel: [   29.512401] ata2.00: configured for UDMA/33
Jan 16 02:43:05 ubuntu kernel: [   29.512752] scsi 0:0:0:0: Direct-Access     ATA      WDC WD300EB-75CP 06.0 PQ: 0 ANSI: 5
Jan 16 02:43:05 ubuntu kernel: [   29.516306] scsi 1:0:0:0: CD-ROM            SAMSUNG  CD-R/RW SW-240B  BD11 PQ: 0 ANSI: 5
Jan 16 02:43:05 ubuntu kernel: [   29.547400] scsi 0:0:0:0: Attached scsi generic sg0 type 0
Jan 16 02:43:05 ubuntu kernel: [   29.547731] scsi 1:0:0:0: Attached scsi generic sg1 type 5
Jan 16 02:43:05 ubuntu kernel: [   29.622589] Driver 'sd' needs updating - please use bus_type methods
Jan 16 02:43:05 ubuntu kernel: [   29.630906] sd 0:0:0:0: [sda] 58633344 512-byte hardware sectors (30020 MB)
Jan 16 02:43:05 ubuntu kernel: [   29.631009] sd 0:0:0:0: [sda] Write Protect is off
Jan 16 02:43:05 ubuntu kernel: [   29.631164] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan 16 02:43:05 ubuntu kernel: [   29.631490] sd 0:0:0:0: [sda] 58633344 512-byte hardware sectors (30020 MB)
Jan 16 02:43:05 ubuntu kernel: [   29.631584] sd 0:0:0:0: [sda] Write Protect is off
Jan 16 02:43:05 ubuntu kernel: [   29.631742] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan 16 02:43:05 ubuntu kernel: [   29.631762]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
Jan 16 02:43:05 ubuntu kernel: [   29.654286]  sda1 sda2 < sda5 >
Jan 16 02:43:05 ubuntu kernel: [   29.683669] sd 0:0:0:0: [sda] Attached SCSI disk
Jan 16 02:43:05 ubuntu kernel: [   29.690418] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
Jan 16 02:43:05 ubuntu kernel: [   29.690433] Uniform CD-ROM driver Revision: 3.20
Jan 16 02:43:05 ubuntu kernel: [   30.790867] EXT3-fs: INFO: recovery required on readonly filesystem.
Jan 16 02:43:05 ubuntu kernel: [   30.790879] EXT3-fs: write access will be enabled during recovery.
Jan 16 02:43:05 ubuntu kernel: [   31.109339] kjournald starting.  Commit interval 5 seconds
Jan 16 02:43:05 ubuntu kernel: [   31.109394] EXT3-fs: sda1: orphan cleanup on readonly fs
Jan 16 02:43:05 ubuntu kernel: [   31.109488] EXT3-fs: sda1: 1 orphan inode deleted
Jan 16 02:43:05 ubuntu kernel: [   31.109492] EXT3-fs: recovery complete.
Jan 16 02:43:05 ubuntu kernel: [   31.113342] EXT3-fs: mounted filesystem with ordered data mode.
Jan 16 02:43:05 ubuntu kernel: [   32.953916] aufs 20080922
Jan 16 02:43:05 ubuntu kernel: [   32.981720] loop: module loaded
Jan 16 02:43:05 ubuntu kernel: [   33.273263] squashfs: version 3.3 (2007/10/31) Phillip Lougher
Jan 16 02:43:05 ubuntu kernel: [  206.994880] udevd version 124 started
Jan 16 02:43:05 ubuntu kernel: [  215.153724] Linux agpgart interface v0.103
Jan 16 02:43:05 ubuntu kernel: [  216.226790] agpgart-intel 0000:00:00.0: Intel 830M Chipset
Jan 16 02:43:05 ubuntu kernel: [  216.227432] agpgart-intel 0000:00:00.0: detected 892K stolen memory
Jan 16 02:43:05 ubuntu kernel: [  217.049834] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jan 16 02:43:05 ubuntu kernel: [  217.077121] iTCO_vendor_support: vendor-support=0
Jan 16 02:43:05 ubuntu kernel: [  217.283727] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
Jan 16 02:43:05 ubuntu kernel: [  217.297790] iTCO_wdt: Found a ICH4 TCO device (Version=1, TCOBASE=0x0460)
Jan 16 02:43:05 ubuntu kernel: [  217.299609] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Jan 16 02:43:05 ubuntu kernel: [  218.884551] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xe0000000
Jan 16 02:43:05 ubuntu kernel: [  218.885880] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jan 16 02:43:05 ubuntu kernel: [  220.981776] intel_rng: FWH not detected
Jan 16 02:43:05 ubuntu kernel: [  223.201446] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
Jan 16 02:43:05 ubuntu kernel: [  223.212569] ACPI: Power Button (FF) [PWRF]
Jan 16 02:43:05 ubuntu kernel: [  223.213814] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
Jan 16 02:43:05 ubuntu kernel: [  223.231138] ACPI: Power Button (CM) [PWRB]
Jan 16 02:43:05 ubuntu kernel: [  223.893413] input: PC Speaker as /devices/platform/pcspkr/input/input4
Jan 16 02:43:05 ubuntu kernel: [  236.913342] parport_pc 00:0a: reported by Plug and Play ACPI
Jan 16 02:43:05 ubuntu kernel: [  236.913470] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
Jan 16 02:43:05 ubuntu kernel: [  240.011551] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
Jan 16 02:43:05 ubuntu kernel: [  240.941920] logips2pp: Detected unknown logitech mouse model 106
Jan 16 02:43:05 ubuntu kernel: [  241.426157] input: ImExPS/2 Logitech Explorer Mouse as /devices/platform/i8042/serio1/input/input5
Jan 16 02:43:05 ubuntu kernel: [  247.775824] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jan 16 02:43:05 ubuntu kernel: [  248.200367] intel8x0_measure_ac97_clock: measured 53994 usecs
Jan 16 02:43:05 ubuntu kernel: [  248.200395] intel8x0: clocking to 48000
Jan 16 02:43:05 ubuntu kernel: [  275.576012] Adding 1253028k swap on /dev/sda5.  Priority:-1 extents:1 across:1253028k
Jan 16 02:43:05 ubuntu kernel: [  278.091442] ip_tables: (C) 2000-2006 Netfilter Core Team
Jan 16 02:43:05 ubuntu kernel: [  297.205597] ACPI: WMI: Mapper loaded
Jan 16 02:43:07 ubuntu kernel: [  310.170389] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
Jan 16 02:43:07 ubuntu kernel: [  310.713349] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Jan 16 02:43:07 ubuntu kernel: [  310.713445] apm: overridden by ACPI.
Jan 16 02:43:08 ubuntu kernel: [  311.746465] lp0: using parport0 (interrupt-driven).
Jan 16 02:43:08 ubuntu kernel: [  312.021759] ppdev: user-space parallel port driver
Jan 16 02:43:23 ubuntu kernel: [  326.301932] Bluetooth: Core ver 2.13
Jan 16 02:43:23 ubuntu kernel: [  326.341987] NET: Registered protocol family 31
Jan 16 02:43:23 ubuntu kernel: [  326.342079] Bluetooth: HCI device and connection manager initialized
Jan 16 02:43:23 ubuntu kernel: [  326.342092] Bluetooth: HCI socket layer initialized
Jan 16 02:43:23 ubuntu kernel: [  326.718558] Bluetooth: L2CAP ver 2.11
Jan 16 02:43:23 ubuntu kernel: [  326.718653] Bluetooth: L2CAP socket layer initialized
Jan 16 02:43:23 ubuntu kernel: [  326.856809] Bluetooth: RFCOMM socket layer initialized
Jan 16 02:43:23 ubuntu kernel: [  326.859744] Bluetooth: RFCOMM TTY layer initialized
Jan 16 02:43:23 ubuntu kernel: [  326.859843] Bluetooth: RFCOMM ver 1.10
Jan 16 02:43:24 ubuntu kernel: [  327.165483] Bluetooth: SCO (Voice Link) ver 0.6
Jan 16 02:43:24 ubuntu kernel: [  327.165571] Bluetooth: SCO socket layer initialized
Jan 16 02:43:24 ubuntu kernel: [  327.841682] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Jan 16 02:43:24 ubuntu kernel: [  327.841779] Bluetooth: BNEP filters: protocol multicast
Jan 16 02:43:25 ubuntu kernel: [  328.294329] Bridge firewalling registered
Jan 16 02:43:30 ubuntu kernel: [  333.511340] eth0: link down
Jan 16 02:43:34 ubuntu kernel: [  337.715440] mtrr: base(0xe0000000) is not aligned on a size(0xd0000) boundary
Jan 16 02:43:57 ubuntu pulseaudio[6979]: ltdl-bind-now.c: Failed to find original dlopen loader.
Jan 16 02:43:57 ubuntu pulseaudio[6981]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Jan 16 02:43:57 ubuntu pulseaudio[6981]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted

---

### Post by mjheagle8 on 2009-01-15
it looks like the ata interface is not identifying in this segment of the output:
```
an 16 02:43:05 ubuntu kernel: [ 14.020551] ata2.01: failed to IDENTIFY (I/O error, err_mask=0x1)
Jan 16 02:43:05 ubuntu kernel: [ 19.176263] ata2.01: failed to IDENTIFY (I/O error, err_mask=0x1)
Jan 16 02:43:05 ubuntu kernel: [ 24.332264] ata2.01: failed to IDENTIFY (I/O error, err_mask=0x1)
```

---

### Post by tpd2049 on 2009-01-15
is there any way to correct it...or is it a hardware incompatability w the os?

---

### Post by mjheagle8 on 2009-01-15
i'd start a new thread with the name of the card in the title so someone who is familiar with your situation can help.

---

### Post by holy1crusader on 2009-01-16
I have the same setup (Dell Dimension 2300) with the same problem.  I'm hoping for a resolution soon!

---

### Post by mjheagle8 on 2009-01-16
did you try to start a new thread with a more descriptive title?

---

### Post by tpd2049 on 2009-01-16
thanks again...I started a more descriptive thread in a few places and will hope for the best.

---

### Post by tpd2049 on 2009-01-16
if i get a solution i'll send it to you
best regards.

---

### Post by mjheagle8 on 2009-01-16
good luck!

---

### Post by holy1crusader on 2009-01-19
I tried installing Fedora 10 and ended up with similar graphic issues, I then installed OpenGEU on a separate partition and it's been working like a charm.  Still hope to get a resolution for ubuntu though!

---

### Post by 62chevy on 2009-01-24
> **tpd2049 said:**
> if i get a solution i'll send it to you
best regards.

I have a Dell 2300 and had the same problem. What you need to do is open terminal and run

```


dexconf -o xorg.conf


```

Do this in your home directory. Look at the file then if satisfied move it to /etc/X11/xorg.conf

more info can be found by using the man pages. 

```


man dexconf


```

hope this helps.

---

