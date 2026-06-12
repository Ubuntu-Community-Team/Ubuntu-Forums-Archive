---
title: "Sometimes my Ubuntu freezes for no reason."
date: 2008-12-30
forum: New to Ubuntu
---

### Post by shiningkenmonster on 2008-12-30
Sometimes my Ubuntu freezes.

A few times when i turn on my netbook. It loads the Dell screen, than as it processes to load into the Ubuntu logo. The whole screen turns RED, GREEN, than YELLOW. and it repeats. 

eventually, it doesn't load to the desktop.

I had to turn off the system by holding the button.

and It did the changing color screen again.

This has never happen before.

It works now. But sometimes, like 1 out of 5 times each time i use my pc. It randomly freezes. Even using the Magic Keys. SYSTEM REG/Print screen+ALT+ R+E+K+S+U+B sometimes it won't even work.

What is wrong with my Ubuntu? I just did a system restore 2 weeks ago.
IS there a way to diagnose this?

---

### Post by Ender41 on 2008-12-30
> **shiningkenmonster said:**
> Sometimes my Ubuntu freezes.

A few times when i turn on my netbook. It loads the Dell screen, than as it processes to load into the Ubuntu logo. The whole screen turns RED, GREEN, than YELLOW. and it repeats. 

eventually, it doesn't load to the desktop.

I had to turn off the system by holding the button.

and It did the changing color screen again.

This has never happen before.

It works now. But sometimes, like 1 out of 5 times each time i use my pc. It randomly freezes. Even using the Magic Keys. SYSTEM REG/Print screen+ALT+ R+E+K+S+U+B sometimes it won't even work.

What is wrong with my Ubuntu? I just did a system restore 2 weeks ago.
IS there a way to diagnose this?

 There are some things that can cause this, overheating springs to mind as does faulty ram or power supply or possibly the video chip playing up. You could try, once you get it going installing lm-sensors and gkrellm or xsensors or the gnome sensors-applet to monitor the system for overheating

---

### Post by shiningkenmonster on 2008-12-30
> **Ender41 said:**
> There are some things that can cause this, overheating springs to mind as does faulty ram or power supply or possibly the video chip playing up. You could try, once you get it going installing lm-sensors and gkrellm or xsensors or the gnome sensors-applet to monitor the system for overheating

yeah, that might be possible. my netbook doesn t have a fan spinning on my intel atom. than again its freaking small.

---

### Post by shiningkenmonster on 2008-12-30
i read somewhere where someone had the same problem. someone suggested when it freezes, after a reboot. do a:
```
dmesg
```
and post the log on the forum. 
which i will do right now. so i'll just post it.

```
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] Warning only 896MB will be used.
[    0.000000] Use a HIGHMEM enabled kernel.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f7fa0
[    0.000000] Entering add_active_range(0, 0, 229376) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   229376
[    0.000000] On node 0 totalpages: 229376
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7F70 checksum 0
[    0.000000] ACPI: RSDP 000F7F70, 0024 (r2 PTLTD )
[    0.000000] ACPI: XSDT 3F6DC22B, 006C (r1 PTLTD  	 XSDT    6040000  LTP        0)
[    0.000000] ACPI: FACP 3F6E1D48, 00F4 (r3 INTEL  CALISTGA  6040000 ALAN        1)
[    0.000000] ACPI: DSDT 3F6DD110, 4BC4 (r1 INTEL  CALISTGA  6040000 INTL 20050624)
[    0.000000] ACPI: FACS 3F6E2FC0, 0040
[    0.000000] ACPI: APIC 3F6E1E3C, 0068 (r1 INTEL  CALISTGA  6040000 LOHR       5A)
[    0.000000] ACPI: HPET 3F6E1EA4, 0038 (r1 INTEL  CALISTGA  6040000 LOHR       5A)
[    0.000000] ACPI: MCFG 3F6E1EDC, 003C (r1 INTEL  CALISTGA  6040000 LOHR       5A)
[    0.000000] ACPI: TCPA 3F6E1F18, 0032 (r1 PTLTD  CALISTGA  6040000  PTL        1)
[    0.000000] ACPI: TMOR 3F6E1F4A, 0026 (r1 PTLTD            6040000 PTL         3)
[    0.000000] ACPI: APIC 3F6E1F70, 0068 (r1 PTLTD  	 APIC    6040000  LTP        0)
[    0.000000] ACPI: BOOT 3F6E1FD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: SSDT 3F6DC297, 04F6 (r2  PmRef    CpuPm     3000 INTL 20050624)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 7:12 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 7:12 APIC version 20
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
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 227584
[    0.000000] Kernel command line: ro root=/dev/sda2 ht=on hpet=disabled quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1596.032 MHz processor.
[    8.820747] Console: colour VGA+ 80x25
[    8.820752] console [tty0] enabled
[    8.821106] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    8.821892] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    8.847862] Memory: 901260k/917504k available (2936k kernel code, 15724k reserved, 1264k data, 292k init, 0k highmem)
[    8.847876] virtual kernel memory layout:
[    8.847878]     fixmap  : 0xfffb3000 - 0xfffff000   ( 304 kB)
[    8.847880]     vmalloc : 0xf8800000 - 0xfffb1000   ( 119 MB)
[    8.847882]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    8.847884]       .init : 0xc0523000 - 0xc056c000   ( 292 kB)
[    8.847886]       .data : 0xc03de079 - 0xc051a43c   (1264 kB)
[    8.847888]       .text : 0xc0100000 - 0xc03de079   (2936 kB)
[    8.847894] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    8.847947] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[    8.927907] Calibrating delay using timer specific routine.. 3196.54 BogoMIPS (lpj=6393084)
[    8.927964] Mount-cache hash table entries: 512
[    8.928116] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0040c39d 00000000 00000001 00000000
[    8.928131] monitor/mwait feature present.
[    8.928134] using mwait in idle threads.
[    8.928139] CPU: L1 I cache: 32K, L1 D cache: 24K
[    8.928143] CPU: L2 cache: 512K
[    8.928148] CPU: Physical Processor ID: 0
[    8.928151] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00003940 0040c39d 00000000 00000001 00000000
[    8.928162] Intel machine check architecture supported.
[    8.928168] Intel machine check reporting enabled on CPU#0.
[    8.928174] Compat vDSO mapped to ffffe000.
[    8.928189] Checking 'hlt' instruction... OK.
[    8.944353] SMP alternatives: switching to UP code
[    8.946485] Early unpacking initramfs... done
[    9.141607] ACPI: Core revision 20070126
[    9.141710] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    9.149910] CPU0: Intel(R) Atom(TM) CPU N270   @ 1.60GHz stepping 02
[    9.149939] SMP alternatives: switching to SMP code
[    9.150672] Booting processor 1/1 eip 3000
[    9.160701] Initializing CPU#1
[    9.239628] Calibrating delay using timer specific routine.. 3192.20 BogoMIPS (lpj=6384418)
[    9.239642] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0040c39d 00000000 00000001 00000000
[    9.239654] monitor/mwait feature present.
[    9.239662] CPU: L1 I cache: 32K, L1 D cache: 24K
[    9.239666] CPU: L2 cache: 512K
[    9.239670] CPU: Physical Processor ID: 0
[    9.239674] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00003940 0040c39d 00000000 00000001 00000000
[    9.239685] Intel machine check architecture supported.
[    9.239691] Intel machine check reporting enabled on CPU#1.
[    9.239978] CPU1: Intel(R) Atom(TM) CPU N270   @ 1.60GHz stepping 02
[    9.240020] Total of 2 processors activated (6388.75 BogoMIPS).
[    9.240227] ENABLING IO-APIC IRQs
[    9.240450] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    9.387709] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    9.407713] Brought up 2 CPUs
[    9.407757] CPU0 attaching sched-domain:
[    9.407762]  domain 0: span 03
[    9.407765]   groups: 01 02
[    9.407771]   domain 1: span 03
[    9.407774]    groups: 03
[    9.407778] CPU1 attaching sched-domain:
[    9.407781]  domain 0: span 03
[    9.407784]   groups: 02 01
[    9.407789]   domain 1: span 03
[    9.407792]    groups: 03
[    9.408172] net_namespace: 64 bytes
[    9.408184] Booting paravirtualized kernel on bare hardware
[    9.409085] Time: 14:40:02  Date: 12/30/08
[    9.409175] NET: Registered protocol family 16
[    9.409509] No dock devices found.
[    9.409679] ACPI: bus type pci registered
[    9.410495] PCI: PCI BIOS revision 3.00 entry at 0xfde5f, last bus=5
[    9.410500] PCI: Using configuration type 1
[    9.410515] Setting up standard PCI resources
[    9.415168] ACPI: EC: Look up EC in DSDT
[    9.417686] ACPI: BIOS _OSI(Linux) query ignored
[    9.417692] ACPI: DMI System Vendor: Dell Inc.
[    9.417695] ACPI: DMI Product Name: Inspiron 910
[    9.417698] ACPI: DMI Product Version: A00
[    9.417701] ACPI: DMI Board Name: CN0J14
[    9.417704] ACPI: DMI BIOS Vendor: Dell Inc.
[    9.417707] ACPI: DMI BIOS Date: 08/05/2008
[    9.417710] ACPI: Please send DMI info above to linux-acpi@vger.kernel.org
[    9.417714] ACPI: If "acpi_osi=Linux" works better, please notify linux-acpi@vger.kernel.org
[    9.418509] ACPI: Interpreter enabled
[    9.418514] ACPI: (supports S0 S3 S4 S5)
[    9.418542] ACPI: Using IOAPIC for interrupt routing
[    9.419602] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    9.443862] ACPI: Device [J380] status [0000000a]: functional but not present; setting present
[    9.488579] ACPI: EC: GPE = 0x19, I/O: command/status = 0x66, data = 0x62
[    9.488585] ACPI: EC: driver started in interrupt mode
[    9.488667] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    9.489597] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    9.489604] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[    9.491485] PCI: Transparent bridge - 0000:00:1e.0
[    9.491540] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    9.492116] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    9.492359] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    9.492583] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    9.492832] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    9.503350] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[    9.503536] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    9.503720] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    9.503896] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    9.504072] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    9.504249] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    9.504424] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    9.504600] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[    9.504847] Linux Plug and Play Support v0.97 (c) Adam Belay
[    9.504911] pnp: PnP ACPI init
[    9.504927] ACPI: bus type pnp registered
[    9.527917] pnp: PnP ACPI: found 11 devices
[    9.527923] ACPI: ACPI bus type pnp unregistered
[    9.528269] SCSI subsystem initialized
[    9.528344] libata version 3.00 loaded.
[    9.528648] usbcore: registered new interface driver usbfs
[    9.528718] usbcore: registered new interface driver hub
[    9.528799] usbcore: registered new device driver usb
[    9.529401] PCI: Using ACPI for IRQ routing
[    9.529407] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    9.615336] NET: Registered protocol family 8
[    9.615340] NET: Registered protocol family 20
[    9.619316] Time: tsc clocksource has been installed.
[    9.635377] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[    9.635385] system 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
[    9.635391] system 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
[    9.635396] system 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
[    9.635402] system 00:01: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[    9.635408] system 00:01: iomem range 0xfed20000-0xfed3ffff could not be reserved
[    9.635414] system 00:01: iomem range 0xfed40000-0xfed44fff could not be reserved
[    9.635419] system 00:01: iomem range 0xfed45000-0xfed8ffff could not be reserved
[    9.635433] system 00:04: iomem range 0xfed00000-0xfed003ff could not be reserved
[    9.635444] system 00:06: ioport range 0x680-0x69f has been reserved
[    9.635450] system 00:06: ioport range 0x800-0x80f has been reserved
[    9.635455] system 00:06: ioport range 0x1000-0x107f has been reserved
[    9.635460] system 00:06: ioport range 0x1180-0x11bf has been reserved
[    9.635465] system 00:06: ioport range 0x1640-0x164f has been reserved
[    9.635471] system 00:06: ioport range 0xfe00-0xfe7f has been reserved
[    9.635476] system 00:06: ioport range 0xff00-0xff7f has been reserved
[    9.635485] system 00:07: ioport range 0x6a0-0x6af has been reserved
[    9.635490] system 00:07: ioport range 0x6b0-0x6ff has been reserved
[    9.666278] PCI: Bridge: 0000:00:1c.0
[    9.666282]   IO window: disabled.
[    9.666292]   MEM window: f0100000-f01fffff
[    9.666298]   PREFETCH window: 50000000-500fffff
[    9.666306] PCI: Bridge: 0000:00:1c.1
[    9.666309]   IO window: disabled.
[    9.666317]   MEM window: f0200000-f02fffff
[    9.666323]   PREFETCH window: disabled.
[    9.666331] PCI: Bridge: 0000:00:1c.2
[    9.666336]   IO window: 2000-2fff
[    9.666343]   MEM window: 50100000-501fffff
[    9.666350]   PREFETCH window: f0600000-f06fffff
[    9.666358] PCI: Bridge: 0000:00:1e.0
[    9.666360]   IO window: disabled.
[    9.666368]   MEM window: disabled.
[    9.666373]   PREFETCH window: disabled.
[    9.666422] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 16
[    9.666432] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    9.666463] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 17
[    9.666472] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    9.666502] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[    9.666511] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    9.666528] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    9.666549] NET: Registered protocol family 2
[    9.703566] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    9.704014] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    9.705049] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    9.705605] TCP: Hash tables configured (established 131072 bind 65536)
[    9.705612] TCP reno registered
[    9.715695] checking if image is initramfs... it is
[   10.096250] Freeing initrd memory: 2694k freed
[   10.096517] Simple Boot Flag at 0x36 set to 0x1
[   10.097709] audit: initializing netlink socket (disabled)
[   10.097730] audit(1230648003.128:1): initialized
[   10.101600] VFS: Disk quotas dquot_6.5.1
[   10.101740] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   10.102609] io scheduler noop registered
[   10.102614] io scheduler anticipatory registered
[   10.102618] io scheduler deadline registered
[   10.102731] io scheduler cfq registered (default)
[   10.102750] Boot video device is 0000:00:02.0
[   10.103059] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   10.103127] assign_interrupt_mode Found MSI capability
[   10.103186] Allocate Port Service[0000:00:1c.0:pcie00]
[   10.103254] Allocate Port Service[0000:00:1c.0:pcie02]
[   10.103396] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   10.103460] assign_interrupt_mode Found MSI capability
[   10.103513] Allocate Port Service[0000:00:1c.1:pcie00]
[   10.103578] Allocate Port Service[0000:00:1c.1:pcie02]
[   10.103717] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   10.103782] assign_interrupt_mode Found MSI capability
[   10.103836] Allocate Port Service[0000:00:1c.2:pcie00]
[   10.103898] Allocate Port Service[0000:00:1c.2:pcie02]
[   10.105559] ACPI: AC Adapter [ACAD] (on-line)
[   10.166846] Switched to high resolution mode on CPU 0
[   10.167041] Switched to high resolution mode on CPU 1
[   10.226948] ACPI: Battery Slot [BAT1] (battery present)
[   10.227258] input: Power Button (FF) as /devices/virtual/input/input0
[   10.227265] ACPI: Power Button (FF) [PWRF]
[   10.227378] input: Lid Switch as /devices/virtual/input/input1
[   10.227456] ACPI: Lid Switch [LID0]
[   10.227570] input: Power Button (CM) as /devices/virtual/input/input2
[   10.227576] ACPI: Power Button (CM) [PWRB]
[   10.227691] input: Sleep Button (CM) as /devices/virtual/input/input3
[   10.227697] ACPI: Sleep Button (CM) [SLPB]
[   10.228343] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input4
[   10.228351] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   10.229034] ACPI: SSDT 3F6DCDF7, 0245 (r2  PmRef  Cpu0Ist     3000 INTL 20050624)
[   10.229371] ACPI: SSDT 3F6DC78D, 05E5 (r2  PmRef  Cpu0Cst     3001 INTL 20050624)
[   10.230073] Monitor-Mwait will be used to enter C-1 state
[   10.230079] Monitor-Mwait will be used to enter C-2 state
[   10.230083] Monitor-Mwait will be used to enter C-3 state
[   10.230158] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   10.230243] ACPI: ACPI0007:00 is registered as cooling_device0
[   10.230251] ACPI: Processor [CPU0] (supports 8 throttling states)
[   10.230755] ACPI: SSDT 3F6DD03C, 00D4 (r2  PmRef  Cpu1Ist     3000 INTL 20050624)
[   10.231069] ACPI: SSDT 3F6DCD72, 0085 (r2  PmRef  Cpu1Cst     3000 INTL 20050624)
[   10.231962] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   10.232042] ACPI: ACPI0007:01 is registered as cooling_device1
[   10.232050] ACPI: Processor [CPU1] (supports 8 throttling states)
[   10.254262] ACPI: LNXTHERM:01 is registered as thermal_zone0
[   10.255972] ACPI: Thermal Zone [TZ01] (52 C)
[   10.372732] Real Time Clock Driver v1.12ac
[   10.373075] hpet_acpi_add: no address or irqs in _CRS
[   10.373103] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   10.375211] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   10.375783] loop: module loaded
[   10.375871] Driver 'sd' needs updating - please use bus_type methods
[   10.375932] Driver 'sr' needs updating - please use bus_type methods
[   10.376127] ata_piix 0000:00:1f.1: version 2.12
[   10.376158] ACPI: PCI Interrupt 0000:00:1f.1[B] -> GSI 19 (level, low) -> IRQ 19
[   10.376211] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   10.376331] scsi0 : ata_piix
[   10.376461] scsi1 : ata_piix
[   10.377355] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[   10.377361] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[   10.539022] ata1.00: ATA-6: STEC PATA 8GB, C5221-10, max UDMA/133
[   10.539028] ata1.00: 15005088 sectors, multi 1: LBA 
[   10.546893] ata1.00: configured for UDMA/100
[   10.546952] ata2: port disabled. ignoring.
[   10.547163] scsi 0:0:0:0: Direct-Access     ATA      STEC PATA 8GB    C522 PQ: 0 ANSI: 5
[   10.547417] sd 0:0:0:0: [sda] 15005088 512-byte hardware sectors (7683 MB)
[   10.547444] sd 0:0:0:0: [sda] Write Protect is off
[   10.547451] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   10.547497] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   10.547591] sd 0:0:0:0: [sda] 15005088 512-byte hardware sectors (7683 MB)
[   10.547620] sd 0:0:0:0: [sda] Write Protect is off
[   10.547626] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   10.547671] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   10.547679]  sda: sda1 sda2
[   10.548271] sd 0:0:0:0: [sda] Attached SCSI disk
[   10.548408] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   10.548906] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
[   10.548929] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   10.548936] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   10.549092] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[   10.553007] ehci_hcd 0000:00:1d.7: debug port 1
[   10.553016] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   10.553032] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xf0544000
[   10.566389] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   10.566680] usb usb1: configuration #1 chosen from 1 choice
[   10.566767] hub 1-0:1.0: USB hub found
[   10.566779] hub 1-0:1.0: 8 ports detected
[   10.670439] USB Universal Host Controller Interface driver v3.0
[   10.670545] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
[   10.670560] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   10.670566] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   10.670726] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[   10.670764] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00001820
[   10.671032] usb usb2: configuration #1 chosen from 1 choice
[   10.671115] hub 2-0:1.0: USB hub found
[   10.671127] hub 2-0:1.0: 2 ports detected
[   10.774334] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[   10.774347] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   10.774353] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   10.774500] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[   10.774542] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[   10.774801] usb usb3: configuration #1 chosen from 1 choice
[   10.774880] hub 3-0:1.0: USB hub found
[   10.774891] hub 3-0:1.0: 2 ports detected
[   10.878230] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   10.878244] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   10.878250] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   10.878405] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[   10.878445] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[   10.878708] usb usb4: configuration #1 chosen from 1 choice
[   10.878790] hub 4-0:1.0: USB hub found
[   10.878801] hub 4-0:1.0: 2 ports detected
[   10.982142] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 17
[   10.982156] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   10.982162] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   10.982308] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[   10.982349] uhci_hcd 0000:00:1d.3: irq 17, io base 0x00001880
[   10.982606] usb usb5: configuration #1 chosen from 1 choice
[   10.982691] hub 5-0:1.0: USB hub found
[   10.982702] hub 5-0:1.0: 2 ports detected
[   11.086041] Initializing USB Mass Storage driver...
[   11.086115] usbcore: registered new interface driver usb-storage
[   11.086121] USB Mass Storage support registered.
[   11.086193] usbcore: registered new interface driver libusual
[   11.086415] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   11.117977] serio: i8042 KBD port at 0x60,0x64 irq 1
[   11.117987] serio: i8042 AUX port at 0x60,0x64 irq 12
[   11.118195] mice: PS/2 mouse device common for all mice
[   11.218062] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   11.236440] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input6
[   11.287669] cpuidle: using governor ladder
[   12.289333] cpuidle: using governor menu
[   12.289401] sdhci: Secure Digital Host Controller Interface driver
[   12.289407] sdhci: Copyright(c) Pierre Ossman
[   12.289500] sdhci: SDHCI controller found at 0000:02:00.2 [197b:2381] (rev 0)
[   12.289545] ACPI: PCI Interrupt 0000:02:00.2[A] -> GSI 16 (level, low) -> IRQ 17
[   12.289582] PCI: Setting latency timer of device 0000:02:00.2 to 64
[   12.289708] mmc0: SDHCI at 0xf0100400 irq 17 DMA
[   12.290102] ACPI: PCI Interrupt 0000:02:00.3[A] -> GSI 16 (level, low) -> IRQ 17
[   12.290118] PCI: Setting latency timer of device 0000:02:00.3 to 64
[   12.290544] usbcore: registered new interface driver hiddev
[   12.290631] usbcore: registered new interface driver usbhid
[   12.290639] /root/src/hardy-netbook/debian/build/custom-source-lpia/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   12.290815] NET: Registered protocol family 1
[   12.291283] NET: Registered protocol family 10
[   12.291692] lo: Disabled Privacy Extensions
[   12.292397] NET: Registered protocol family 17
[   12.292443] Using IPI No-Shortcut mode
[   12.292678]   Magic number: 4:908:688
[   12.293022] Freeing unused kernel memory: 292k freed
[   12.451770] mmc0: new SDHC card at address d6e6
[   12.452056] mmcblk0: mmc0:d6e6 SD08G 7977472KiB 
[   12.452111]  mmcblk0: p1
[   13.159938] Clocksource tsc unstable (delta = -232069376 ns)
[   13.169399] Time: acpi_pm clocksource has been installed.
[   13.512240] Registering unionfs 1.4
[   13.512246] unionfs: debugging is not enabled
[   13.520343] squashfs: version 3.3 (2007/10/31) Phillip Lougher
[   13.608051] fuse init (API version 7.9)
[   13.974515] EXT3-fs: INFO: recovery required on readonly filesystem.
[   13.974524] EXT3-fs: write access will be enabled during recovery.
[   20.510459] kjournald starting.  Commit interval 5 seconds
[   20.510501] EXT3-fs: recovery complete.
[   20.513001] EXT3-fs: mounted filesystem with ordered data mode.
[   21.361212] ip_tables: (C) 2000-2006 Netfilter Core Team
[   21.434226] nf_conntrack version 0.5.0 (14336 buckets, 57344 max)
[   23.382518] Synaptics Touchpad, model: 1, fw: 7.0, id: 0x1c0b1, caps: 0xd04711/0xa00000
[   23.476127] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   23.688219] intel_rng: FWH not detected
[   23.754185] iTCO_vendor_support: vendor-support=0
[   23.794787] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   23.794933] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   23.794998] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   23.823012] ieee80211_crypt: registered algorithm 'NULL'
[   23.865880] r8169 Gigabit Ethernet driver 2.2LK loaded
[   23.865985] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[   23.866054] PCI: Setting latency timer of device 0000:04:00.0 to 64
[   23.869042] eth0: RTL8101e at 0xf88ba000, 00:21:70:c7:db:13, XID 24a00000 IRQ 220
[   23.995436] ieee80211_crypt: registered algorithm 'TKIP'
[   24.103346] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   24.103736] EXT3 FS on sda2, internal journal
[   25.267009] Linux agpgart interface v0.102
[   25.285166] agpgart: Detected an Intel 945GME Chipset.
[   25.285377] agpgart: Detected 7932K stolen memory.
[   25.303772] agpgart: AGP aperture is 256M @ 0xd0000000
[   25.367650] [drm] Initialized drm 1.1.0 20060810
[   25.511466] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 21
[   25.511516] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   28.142532] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
[   28.142569] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   28.148770] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   47.840584] Bluetooth: Core ver 2.11
[   47.841597] NET: Registered protocol family 31
[   47.841608] Bluetooth: HCI device and connection manager initialized
[   47.841617] Bluetooth: HCI socket layer initialized
[   47.875241] Bluetooth: HCI USB driver ver 2.9
[   47.875655] usbcore: registered new interface driver hci_usb
[   47.977413] Bluetooth: L2CAP ver 2.9
[   47.977424] Bluetooth: L2CAP socket layer initialized
[   48.214400] Bluetooth: RFCOMM socket layer initialized
[   48.214767] Bluetooth: RFCOMM TTY layer initialized
[   48.214777] Bluetooth: RFCOMM ver 1.8
[   48.554246] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   48.581881] Linux video capture interface: v2.00
[   48.595790] usbcore: registered new interface driver uvcvideo
[   48.595805] USB Video Class driver (v0.1.0)
[   48.847011] r8169: eth0: link down
[   48.848841] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   49.306281] ppdev: user-space parallel port driver
[   49.574956] wl: module license 'unspecified' taints kernel.
[   49.592965] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 16
[   49.592992] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   49.615429] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.27.9
[   59.280707] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   67.325976] Inbound IN=eth1 OUT= MAC=00:23:08:1e:4d:d3:00:1c:10:39:42:4c:08:00 SRC=192.168.1.1 DST=192.168.1.104 LEN=385 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=1900 DPT=52313 LEN=365 
[   68.379793] Inbound IN=eth1 OUT= MAC=00:23:08:1e:4d:d3:00:1c:10:39:42:4c:08:00 SRC=192.168.1.1 DST=192.168.1.104 LEN=387 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=1900 DPT=52313 LEN=367 
[   69.736493] Inbound IN=eth1 OUT= MAC=00:23:08:1e:4d:d3:00:1c:10:39:42:4c:08:00 SRC=205.188.248.130 DST=192.168.1.104 LEN=40 TOS=0x00 PREC=0x00 TTL=108 ID=61640 DF PROTO=TCP SPT=5190 DPT=45991 WINDOW=16384 RES=0x00 ACK URGP=0 
[   69.762537] Inbound IN=eth1 OUT= MAC=00:23:08:1e:4d:d3:00:1c:10:39:42:4c:08:00 SRC=205.188.179.19 DST=192.168.1.104 LEN=40 TOS=0x00 PREC=0x00 TTL=107 ID=32435 DF PROTO=TCP SPT=5190 DPT=44550 WINDOW=16384 RES=0x00 ACK URGP=0 
[   70.051311] eth1: no IPv6 routers present
[   71.796632] Inbound IN=eth1 OUT= MAC=00:23:08:1e:4d:d3:00:1c:10:39:42:4c:08:00 SRC=64.12.30.44 DST=192.168.1.104 LEN=40 TOS=0x00 PREC=0x00 TTL=107 ID=34240 DF PROTO=TCP SPT=5190 DPT=42843 WINDOW=16384 RES=0x00 ACK URGP=0 
[   72.878636] Inbound IN=eth1 OUT= MAC=00:23:08:1e:4d:d3:00:1c:10:39:42:4c:08:00 SRC=64.12.24.22 DST=192.168.1.104 LEN=120 TOS=0x00 PREC=0x00 TTL=107 ID=64596 DF PROTO=TCP SPT=5190 DPT=57872 WINDOW=16384 RES=0x00 ACK PSH URGP=0 
[   72.891567] Inbound IN=eth1 OUT= MAC=00:23:08:1e:4d:d3:00:1c:10:39:42:4c:08:00 SRC=205.188.179.19 DST=192.168.1.104 LEN=74 TOS=0x00 PREC=0x00 TTL=107 ID=34140 DF PROTO=TCP SPT=5190 DPT=44550 WINDOW=16384 RES=0x00 ACK PSH URGP=0 
[   72.944180] Inbound IN=eth1 OUT= MAC=00:23:08:1e:4d:d3:00:1c:10:39:42:4c:08:00 SRC=64.12.24.22 DST=192.168.1.104 LEN=208 TOS=0x00 PREC=0x00 TTL=107 ID=64795 DF PROTO=TCP SPT=5190 DPT=57872 WINDOW=16384 RES=0x00 ACK PSH URGP=0 
[   72.989092] Inbound IN=eth1 OUT= MAC=00:23:08:1e:4d:d3:00:1c:10:39:42:4c:08:00 SRC=64.12.24.22 DST=192.168.1.104 LEN=788 TOS=0x00 PREC=0x00 TTL=107 ID=64859 DF PROTO=TCP SPT=5190 DPT=57872 WINDOW=16384 RES=0x00 ACK PSH URGP=0 
[   73.812110] Inbound IN=eth1 OUT= MAC=00:23:08:1e:4d:d3:00:1c:10:39:42:4c:08:00 SRC=205.188.179.19 DST=192.168.1.104 LEN=74 TOS=0x00 PREC=0x00 TTL=107 ID=34715 DF PROTO=TCP SPT=5190 DPT=44550 WINDOW=16384 RES=0x00 ACK PSH URGP=0 
[   76.292183] Inbound IN=eth1 OUT= MAC=00:23:08:1e:4d:d3:00:1c:10:39:42:4c:08:00 SRC=205.188.179.19 DST=192.168.1.104 LEN=74 TOS=0x00 PREC=0x00 TTL=107 ID=35819 DF PROTO=TCP SPT=5190 DPT=44550 WINDOW=16384 RES=0x00 ACK PSH URGP=0 
[   78.722215] Inbound IN=eth1 OUT= MAC=00:23:08:1e:4d:d3:00:1c:10:39:42:4c:08:00 SRC=205.188.248.130 DST=192.168.1.104 LEN=213 TOS=0x00 PREC=0x00 TTL=108 ID=64296 DF PROTO=TCP SPT=5190 DPT=45991 WINDOW=16384 RES=0x00 ACK PSH URGP=0 
[   80.522190] Inbound IN=eth1 OUT= MAC=00:23:08:1e:4d:d3:00:1c:10:39:42:4c:08:00 SRC=205.188.248.130 DST=192.168.1.104 LEN=213 TOS=0x00 PREC=0x00 TTL=108 ID=64686 DF PROTO=TCP SPT=5190 DPT=45991 WINDOW=16384 RES=0x00 ACK PSH URGP=0 
[   82.648047] Inbound IN=eth1 OUT= MAC=00:23:08:1e:4d:d3:00:1c:10:39:42:4c:08:00 SRC=64.12.30.44 DST=192.168.1.104 LEN=450 TOS=0x00 PREC=0x00 TTL=107 ID=43217 DF PROTO=TCP SPT=5190 DPT=42843 WINDOW=16384 RES=0x00 ACK PSH URGP=0 
[   82.664841] Inbound IN=eth1 OUT= MAC=00:23:08:1e:4d:d3:00:1c:10:39:42:4c:08:00 SRC=205.188.179.19 DST=192.168.1.104 LEN=74 TOS=0x00 PREC=0x00 TTL=107 ID=38168 DF PROTO=TCP SPT=5190 DPT=44550 WINDOW=16384 RES=0x00 ACK PSH URGP=0 
[   83.431026] Inbound IN=eth1 OUT= MAC=00:23:08:1e:4d:d3:00:1c:10:39:42:4c:08:00 SRC=205.188.248.130 DST=192.168.1.104 LEN=213 TOS=0x00 PREC=0x00 TTL=108 ID=65353 DF PROTO=TCP SPT=5190 DPT=45991 WINDOW=16384 RES=0x00 ACK PSH URGP=0 
[   88.573887] Inbound IN=eth1 OUT= MAC=00:23:08:1e:4d:d3:00:1c:10:39:42:4c:08:00 SRC=64.12.30.44 DST=192.168.1.104 LEN=450 TOS=0x00 PREC=0x00 TTL=107 ID=47997 DF PROTO=TCP SPT=5190 DPT=42843 WINDOW=16384 RES=0x00 ACK PSH URGP=0 
[   89.513688] Inbound IN=eth1 OUT= MAC=00:23:08:1e:4d:d3:00:1c:10:39:42:4c:08:00 SRC=205.188.248.130 DST=192.168.1.104 LEN=213 TOS=0x00 PREC=0x00 TTL=108 ID=1217 DF PROTO=TCP SPT=5190 DPT=45991 WINDOW=16384 RES=0x00 ACK PSH URGP=0 
[   92.522523] Inbound IN=eth1 OUT= MAC=00:23:08:1e:4d:d3:00:1c:10:39:42:4c:08:00 SRC=64.12.24.22 DST=192.168.1.104 LEN=1400 TOS=0x00 PREC=0x00 TTL=107 ID=36136 DF PROTO=TCP SPT=5190 DPT=57872 WINDOW=16384 RES=0x00 ACK URGP=0 
[   94.944842] Inbound IN=eth1 OUT= MAC=00:23:08:1e:4d:d3:00:1c:10:39:42:4c:08:00 SRC=205.188.179.19 DST=192.168.1.104 LEN=74 TOS=0x00 PREC=0x00 TTL=107 ID=42649 DF PROTO=TCP SPT=5190 DPT=44550 WINDOW=16384 RES=0x00 ACK PSH URGP=0 
skenmon@skenmon:~$ 


```

what seems to be the problem?

---

