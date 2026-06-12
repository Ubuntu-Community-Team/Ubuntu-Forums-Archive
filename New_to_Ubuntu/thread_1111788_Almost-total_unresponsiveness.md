---
title: "Almost-total unresponsiveness"
date: 2009-03-31
forum: New to Ubuntu
---

### Post by alanwalterthomas on 2009-03-31
Ubuntu 8.04
This has been happening every couple days. Maybe someone can diagnose the problem through the symptoms below:

What happens:
Lose ndiswrapper wireless internet connection (so I can't ssh to find out)
Keyboard stop working (cannot even turn numlock on/off) The mouse still works
Some programs will not start

It happens when using firefox & skype, but I can't be sure that these programs are related to the problem

Programs that start immediately:
Manage Print Jobs

Programs that start after a few seconds where "Starting [program] appears in the lower taskbar":
Calculator
Character Map
Dictionary
Gscrot (screen selector utility, but it doesn't work now)
GShutdown (but won't turn off the computer)


Programs that show Starting [program] in the bottom toolbar but fail to start:
Disk Usage Analyser
Revelation Password Manager
Terminal
Text Editor
Five or More, Four in a Row, Gnometris, etc.


Programs that don't seem to start at all:
Clicking on the top right red power button (so I can't logout or reboot normally)
Tomboy Notes
Firefox, but I could open a new window from it when it was already open.
System Monitor (I really wish I could have gotten this one!)

& Finally my mouse froze half an hour later when testing whether SuperTux would start (it didn't)
Before that I could resize, minimize & minimize windows with the mouse, switch desktops, etc.

Finally I find that the keyboard wasn't totally dead since Alt+SysReq+REISUB rebooted the computer.

Can someone please explain this behaviour & suggest a fix, or at least tell me how I might provide more useful information?
Thanks,

---

### Post by cariboo on 2009-03-31
Check your hard drive free space. Open an Applicatins-->Accessories-->Terminal and type:

```
df -h
```

If you are running out of free space in the same terminal type:

```
sudo apt-get clean
```

and

```
sudo apt-get autoremove
```

The first command wil remove the archived packages in /var/cache/apt/archives, and the second command removes unsed dependencies.

Jim

---

### Post by alanwalterthomas on 2009-04-02
nope, I have several hundred GB free.
Any other ideas, or a way to find the error in a log I don't know about?
Thanks,

---

### Post by CLomax on 2009-04-02
I came across problems similar to this after installing Ubuntu on my brother's computer. It turned out that the motherboard didn't seem to like Ubuntu at all.

This happens to older Dell computers as far as I'm aware but it could be the case with others too.

---

### Post by mikechant on 2009-04-02
Try running one of the problem apps from the terminal and see it there are any errors generated.
E.g. ALT-F2 to open terminal then just type firefox

---

### Post by linux_tech on 2009-04-02
after the next error, go to terminal and type ```
dmesg 
```
Look torwards end of output for error, or reply with output

---

### Post by night_fox on 2009-04-02
Ubuntu 8.04 was inexcusably bad in that sense - it kept crashing every other time I tried to use totem. You could try upgrading to 8.10 which only crashed for me when I ran out of memory.

---

### Post by alanwalterthomas on 2009-04-06
It's happened again, right on schedule, so right after I rebooted I ran dmesg:

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-23-generic (buildd@vernadsky) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Mon Jan 26 00:13:11 UTC 2009 (Ubuntu 2.6.24-23.48-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fde0000 (usable)
[    0.000000]  BIOS-e820: 000000007fde0000 - 000000007fde3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fde3000 - 000000007fdf0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007fdf0000 - 000000007fe00000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 1149MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f57f0
[    0.000000] Entering add_active_range(0, 0, 523744) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   523744
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   523744
[    0.000000] On node 0 totalpages: 523744
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2299 pages used for memmap
[    0.000000]   HighMem zone: 292069 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7170 checksum 0
[    0.000000] ACPI: RSDP 000F7170, 0014 (r0 GBT   )
[    0.000000] ACPI: RSDT 7FDE3000, 0038 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: FACP 7FDE3040, 0074 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: DSDT 7FDE30C0, 64A2 (r1 GBT    GBTUACPI     1000 MSFT  3000000)
[    0.000000] ACPI: FACS 7FDE0000, 0040
[    0.000000] ACPI: SSDT 7FDE9640, 028A (r1 PTLTD  POWERNOW        1  LTP        1)
[    0.000000] ACPI: HPET 7FDE9900, 0038 (r1 GBT    GBTUACPI 42302E31 GBTU       98)
[    0.000000] ACPI: MCFG 7FDE9940, 003C (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: APIC 7FDE9580, 0084 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:11 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:11 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x10b9a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 7fe00000:60200000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519653
[    0.000000] Kernel command line: root=UUID=ff73a34a-37a3-44d5-9a60-c33ede9b9246 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2505.438 MHz processor.
[   24.682314] Console: colour VGA+ 80x25
[   24.682317] console [tty0] enabled
[   24.682581] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   24.682861] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   24.750976] Memory: 2064948k/2094976k available (2179k kernel code, 28716k reserved, 1008k data, 368k init, 1177472k highmem)
[   24.750982] virtual kernel memory layout:
[   24.750983]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   24.750984]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   24.750985]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   24.750985]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   24.750986]       .init : 0xc0423000 - 0xc047f000   ( 368 kB)
[   24.750987]       .data : 0xc0320c08 - 0xc041cdc4   (1008 kB)
[   24.750988]       .text : 0xc0100000 - 0xc0320c08   (2179 kB)
[   24.750990] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   24.751018] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   24.751133] hpet clockevent registered
[   24.830992] Calibrating delay using timer specific routine.. 5014.53 BogoMIPS (lpj=10029072)
[   24.831008] Security Framework initialized
[   24.831013] SELinux:  Disabled at boot.
[   24.831024] AppArmor: AppArmor initialized
[   24.831027] Failure registering capabilities with primary security module.
[   24.831033] Mount-cache hash table entries: 512
[   24.831122] Initializing cgroup subsys ns
[   24.831125] Initializing cgroup subsys cpuacct
[   24.831132] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000011f 00000000
[   24.831139] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   24.831141] CPU: L2 Cache: 512K (64 bytes/line)
[   24.831143] CPU 0(2) -> Core 0
[   24.831145] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00020410 00002001 00000000 0000011f 00000000
[   24.831152] Compat vDSO mapped to ffffe000.
[   24.831160] Checking 'hlt' instruction... OK.
[   24.847176] SMP alternatives: switching to UP code
[   24.848103] Early unpacking initramfs... done
[   25.090994] ACPI: Core revision 20070126
[   25.091049] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   25.103012] CPU0: AMD Athlon(tm) Dual Core Processor 4850e stepping 02
[   25.103027] SMP alternatives: switching to SMP code
[   25.103355] Booting processor 1/1 eip 3000
[   25.113792] Initializing CPU#1
[   25.190808] Calibrating delay using timer specific routine.. 5010.72 BogoMIPS (lpj=10021447)
[   25.190814] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000011f 00000000
[   25.190819] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   25.190820] CPU: L2 Cache: 512K (64 bytes/line)
[   25.190822] CPU 1(2) -> Core 1
[   25.190823] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00020410 00002001 00000000 0000011f 00000000
[   25.190505] CPU1: AMD Athlon(tm) Dual Core Processor 4850e stepping 02
[   25.190517] Total of 2 processors activated (10025.25 BogoMIPS).
[   25.190817] ENABLING IO-APIC IRQs
[   25.191035] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   25.338166] Brought up 2 CPUs
[   25.338216] CPU0 attaching sched-domain:
[   25.338218]  domain 0: span 03
[   25.338219]   groups: 01 02
[   25.338222] CPU1 attaching sched-domain:
[   25.338223]  domain 0: span 03
[   25.338224]   groups: 02 01
[   25.338373] net_namespace: 64 bytes
[   25.338380] Booting paravirtualized kernel on bare hardware
[   25.338716] Time: 17:40:54  Date: 04/04/09
[   25.338735] NET: Registered protocol family 16
[   25.338872] EISA bus registered
[   25.338876] ACPI: bus type pci registered
[   25.339804] PCI: PCI BIOS revision 3.00 entry at 0xfb4d0, last bus=2
[   25.339805] PCI: Using configuration type 1
[   25.339814] Setting up standard PCI resources
[   25.343591] ACPI: EC: Look up EC in DSDT
[   25.347498] ACPI: Interpreter enabled
[   25.347503] ACPI: (supports S0 S1 S4 S5)
[   25.347516] ACPI: Using IOAPIC for interrupt routing
[   25.351107] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   25.352141] PCI: Transparent bridge - 0000:00:14.4
[   25.352162] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   25.352351] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[   25.352431] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
[   25.365035] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   25.365119] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   25.365199] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   25.365279] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   25.365359] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   25.365439] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   25.365520] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   25.365600] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   25.365693] Linux Plug and Play Support v0.97 (c) Adam Belay
[   25.365715] pnp: PnP ACPI init
[   25.365720] ACPI: bus type pnp registered
[   25.367609] pnp: PnP ACPI: found 12 devices
[   25.367610] ACPI: ACPI bus type pnp unregistered
[   25.367613] PnPBIOS: Disabled by ACPI PNP
[   25.367765] PCI: Using ACPI for IRQ routing
[   25.367767] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   25.367774] PCI: Cannot allocate resource region 3 of device 0000:00:00.0
[   25.421942] NET: Registered protocol family 8
[   25.421943] NET: Registered protocol family 20
[   25.421971] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[   25.421975] hpet0: 4 32-bit timers, 14318180 Hz
[   25.423008] AppArmor: AppArmor Filesystem Enabled
[   25.425930] Time: hpet clocksource has been installed.
[   25.425942] Switched to high resolution mode on CPU 0
[   25.426484] Switched to high resolution mode on CPU 1
[   25.433914] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[   25.433917] system 00:01: ioport range 0x220-0x225 has been reserved
[   25.433919] system 00:01: ioport range 0x290-0x294 has been reserved
[   25.433923] system 00:02: ioport range 0x4100-0x411f has been reserved
[   25.433926] system 00:02: ioport range 0x228-0x22f has been reserved
[   25.433928] system 00:02: ioport range 0x238-0x23f has been reserved
[   25.433930] system 00:02: ioport range 0x40b-0x40b has been reserved
[   25.433932] system 00:02: ioport range 0x4d6-0x4d6 has been reserved
[   25.433934] system 00:02: ioport range 0xc00-0xc01 has been reserved
[   25.433936] system 00:02: ioport range 0xc14-0xc14 has been reserved
[   25.433938] system 00:02: ioport range 0xc50-0xc52 has been reserved
[   25.433940] system 00:02: ioport range 0xc6c-0xc6d has been reserved
[   25.433941] system 00:02: ioport range 0xc6f-0xc6f has been reserved
[   25.433943] system 00:02: ioport range 0xcd0-0xcd1 has been reserved
[   25.433945] system 00:02: ioport range 0xcd2-0xcd3 has been reserved
[   25.433947] system 00:02: ioport range 0xcd4-0xcdf has been reserved
[   25.433949] system 00:02: ioport range 0x4000-0x40fe has been reserved
[   25.433951] system 00:02: ioport range 0x4210-0x4217 has been reserved
[   25.433953] system 00:02: ioport range 0xb00-0xb0f has been reserved
[   25.433955] system 00:02: ioport range 0xb10-0xb1f has been reserved
[   25.433957] system 00:02: ioport range 0xb20-0xb3f has been reserved
[   25.433963] system 00:0a: iomem range 0xe0000000-0xefffffff could not be reserved
[   25.433967] system 00:0b: iomem range 0xd1a00-0xd3fff has been reserved
[   25.433969] system 00:0b: iomem range 0xf0000-0xf7fff could not be reserved
[   25.433971] system 00:0b: iomem range 0xf8000-0xfbfff could not be reserved
[   25.433973] system 00:0b: iomem range 0xfc000-0xfffff could not be reserved
[   25.433975] system 00:0b: iomem range 0x7fde0000-0x7fdfffff could not be reserved
[   25.433978] system 00:0b: iomem range 0xffff0000-0xffffffff could not be reserved
[   25.433980] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
[   25.433982] system 00:0b: iomem range 0x100000-0x7fddffff could not be reserved
[   25.433984] system 00:0b: iomem range 0x0-0x0 could not be reserved
[   25.433986] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
[   25.433988] system 00:0b: iomem range 0xfee00000-0xfee00fff could not be reserved
[   25.433990] system 00:0b: iomem range 0xfff80000-0xfffeffff could not be reserved
[   25.464244] PCI: Bridge: 0000:00:02.0
[   25.464246]   IO window: e000-efff
[   25.464249]   MEM window: fdd00000-fddfffff
[   25.464251]   PREFETCH window: d0000000-dfffffff
[   25.464253] PCI: Bridge: 0000:00:14.4
[   25.464256]   IO window: d000-dfff
[   25.464261]   MEM window: fdf00000-fdffffff
[   25.464264]   PREFETCH window: fde00000-fdefffff
[   25.464283] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 18 (level, low) -> IRQ 16
[   25.464287] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   25.464300] NET: Registered protocol family 2
[   25.501821] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   25.502040] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   25.502616] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   25.502865] TCP: Hash tables configured (established 131072 bind 65536)
[   25.502867] TCP reno registered
[   25.513858] checking if image is initramfs... it is
[   25.982924] Freeing initrd memory: 7327k freed
[   25.984035] audit: initializing netlink socket (disabled)
[   25.984046] audit(1238866854.120:1): initialized
[   25.984187] highmem bounce pool size: 64 pages
[   25.985646] VFS: Disk quotas dquot_6.5.1
[   25.985700] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   25.985788] io scheduler noop registered
[   25.985790] io scheduler anticipatory registered
[   25.985791] io scheduler deadline registered
[   25.985799] io scheduler cfq registered (default)
[   26.125141] Boot video device is 0000:01:00.0
[   26.125259] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   26.125281] assign_interrupt_mode Found MSI capability
[   26.125302] Allocate Port Service[0000:00:02.0:pcie00]
[   26.125482] isapnp: Scanning for PnP cards...
[   26.478680] isapnp: No Plug & Play device found
[   26.500192] Real Time Clock Driver v1.12ac
[   26.500336] hpet_resources: 0xfed00000 is busy
[   26.500360] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   26.501508] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   26.501556] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   26.501624] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   26.501626] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[   26.501726] serio: i8042 KBD port at 0x60,0x64 irq 1
[   26.517459] mice: PS/2 mouse device common for all mice
[   26.517555] EISA: Probing bus 0 at eisa.0
[   26.517573] Cannot allocate resource for EISA slot 4
[   26.517589] EISA: Detected 0 cards.
[   26.517591] cpuidle: using governor ladder
[   26.517593] cpuidle: using governor menu
[   26.517657] NET: Registered protocol family 1
[   26.517677] Using IPI No-Shortcut mode
[   26.517703] registered taskstats version 1
[   26.517780]   Magic number: 5:223:693
[   26.517903] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   26.517904] EDD information not available.
[   26.518102] Freeing unused kernel memory: 368k freed
[   26.518123] Write protecting the kernel read-only data: 806k
[   26.552349] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   27.665508] fuse init (API version 7.9)
[   27.680148] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
[   27.680159] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
[   27.777844] SCSI subsystem initialized
[   27.813122] libata version 3.00 loaded.
[   27.814545] ahci 0000:00:11.0: version 3.0
[   27.814578] ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 22 (level, low) -> IRQ 17
[   27.814627] ahci 0000:00:11.0: controller can't do PMP, turning off CAP_PMP
[   27.872749] usbcore: registered new interface driver usbfs
[   27.872768] usbcore: registered new interface driver hub
[   27.872788] usbcore: registered new device driver usb
[   27.873622] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   27.961553] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   27.961625] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   28.021566] Floppy drive(s): fd0 is 1.44M
[   28.042451] FDC 0 is a post-1991 82077
[   28.815758] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[   28.815762] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pio slum part 
[   28.816212] scsi0 : ahci
[   28.816264] scsi1 : ahci
[   28.816292] scsi2 : ahci
[   28.816324] scsi3 : ahci
[   28.816350] scsi4 : ahci
[   28.816379] scsi5 : ahci
[   28.816446] ata1: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f100 irq 222
[   28.816449] ata2: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 222
[   28.816452] ata3: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f200 irq 222
[   28.816455] ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 222
[   28.816458] ata5: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f300 irq 222
[   28.816461] ata6: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f380 irq 222
[   29.290840] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   29.292720] ata1.00: ATA-8: ST3500320AS, SD15, max UDMA/133
[   29.292724] ata1.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[   29.294478] ata1.00: configured for UDMA/133
[   29.602265] ata2: SATA link down (SStatus 0 SControl 300)
[   30.077392] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   30.234225] ata3.00: ATAPI: TSSTcorp CDDVDW SH-S223Q, SB00, max UDMA/100, ATAPI AN
[   30.389947] ata3.00: configured for UDMA/100
[   30.700243] ata4: SATA link down (SStatus 0 SControl 300)
[   31.011669] ata5: SATA link down (SStatus 0 SControl 300)
[   31.323096] ata6: SATA link down (SStatus 0 SControl 300)
[   31.323181] scsi 0:0:0:0: Direct-Access     ATA      ST3500320AS      SD15 PQ: 0 ANSI: 5
[   31.324154] scsi 2:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S223Q  SB00 PQ: 0 ANSI: 5
[   31.323783] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 16 (level, low) -> IRQ 18
[   31.323797] ohci_hcd 0000:00:12.0: OHCI Host Controller
[   31.324032] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 1
[   31.324053] ohci_hcd 0000:00:12.0: irq 18, io mem 0xfe02e000
[   31.332197] Driver 'sd' needs updating - please use bus_type methods
[   31.334782] Driver 'sr' needs updating - please use bus_type methods
[   31.340112] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[   31.340121] sd 0:0:0:0: [sda] Write Protect is off
[   31.340123] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   31.340135] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   31.340173] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[   31.340180] sd 0:0:0:0: [sda] Write Protect is off
[   31.340181] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   31.340191] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   31.340193]  sda: sda1 sda2
[   31.380935] sd 0:0:0:0: [sda] Attached SCSI disk
[   31.383066] usb usb1: configuration #1 chosen from 1 choice
[   31.383084] hub 1-0:1.0: USB hub found
[   31.383092] hub 1-0:1.0: 3 ports detected
[   31.384614] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   31.384628] sr 2:0:0:0: Attached scsi generic sg1 type 5
[   31.387693] sr0: scsi3-mmc drive: 125x/125x writer dvd-ram cd/rw xa/form2 cdda tray
[   31.387697] Uniform CD-ROM driver Revision: 3.20
[   31.387740] sr 2:0:0:0: Attached scsi CD-ROM sr0
[   31.486868] ACPI: PCI Interrupt 0000:00:12.1[A] -> GSI 16 (level, low) -> IRQ 18
[   31.486882] ohci_hcd 0000:00:12.1: OHCI Host Controller
[   31.486900] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 2
[   31.486915] ohci_hcd 0000:00:12.1: irq 18, io mem 0xfe02d000
[   31.546753] usb usb2: configuration #1 chosen from 1 choice
[   31.546771] hub 2-0:1.0: USB hub found
[   31.546778] hub 2-0:1.0: 3 ports detected
[   31.650541] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 18 (level, low) -> IRQ 16
[   31.650552] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   31.650571] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 3
[   31.650588] ohci_hcd 0000:00:13.0: irq 16, io mem 0xfe02b000
[   31.710420] usb usb3: configuration #1 chosen from 1 choice
[   31.710434] hub 3-0:1.0: USB hub found
[   31.710440] hub 3-0:1.0: 3 ports detected
[   31.798212] usb 1-2: new full speed USB device using ohci_hcd and address 2
[   31.814233] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 18 (level, low) -> IRQ 16
[   31.814240] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   31.814259] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 4
[   31.814270] ohci_hcd 0000:00:13.1: irq 16, io mem 0xfe02a000
[   31.874127] usb usb4: configuration #1 chosen from 1 choice
[   31.874141] hub 4-0:1.0: USB hub found
[   31.874147] hub 4-0:1.0: 3 ports detected
[   31.977932] ACPI: PCI Interrupt 0000:00:14.5[C] -> GSI 18 (level, low) -> IRQ 16
[   31.977940] ohci_hcd 0000:00:14.5: OHCI Host Controller
[   31.977953] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 5
[   31.977965] ohci_hcd 0000:00:14.5: irq 16, io mem 0xfe028000
[   32.013459] usb 1-2: configuration #1 chosen from 1 choice
[   32.015398] hub 1-2:1.0: USB hub found
[   32.017378] hub 1-2:1.0: 2 ports detected
[   32.037819] usb usb5: configuration #1 chosen from 1 choice
[   32.037835] hub 5-0:1.0: USB hub found
[   32.037840] hub 5-0:1.0: 2 ports detected
[   32.141897] ACPI: PCI Interrupt 0000:00:12.2[B] -> GSI 17 (level, low) -> IRQ 19
[   32.141907] ehci_hcd 0000:00:12.2: EHCI Host Controller
[   32.141924] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 6
[   32.141956] ehci_hcd 0000:00:12.2: debug port 1
[   32.141971] ehci_hcd 0000:00:12.2: irq 19, io mem 0xfe02c000
[   32.153566] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   32.153669] usb usb6: configuration #1 chosen from 1 choice
[   32.153688] hub 6-0:1.0: USB hub found
[   32.153693] hub 6-0:1.0: 6 ports detected
[   32.257457] ACPI: PCI Interrupt 0000:00:13.2[B] -> GSI 19 (level, low) -> IRQ 20
[   32.257471] ehci_hcd 0000:00:13.2: EHCI Host Controller
[   32.257490] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 7
[   32.257523] ehci_hcd 0000:00:13.2: debug port 1
[   32.257538] ehci_hcd 0000:00:13.2: irq 20, io mem 0xfe029000
[   32.269345] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   32.269414] usb usb7: configuration #1 chosen from 1 choice
[   32.269430] hub 7-0:1.0: USB hub found
[   32.269434] hub 7-0:1.0: 6 ports detected
[   32.373281] ATIIXP: IDE controller (0x1002:0x439c rev 0x00) at  PCI slot 0000:00:14.1
[   32.373294] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 18
[   32.373301] ATIIXP: not 100% native mode: will probe irqs later
[   32.373308]     ide0: BM-DMA at 0xfa00-0xfa07, BIOS settings: hda:pio, hdb:pio
[   32.373319] ATIIXP: simplex device: DMA disabled
[   32.373320] ide1: ATIIXP Bus-Master DMA disabled (BIOS)
[   32.373323] Probing IDE interface ide0...
[   32.414596] usb 1-2: USB disconnect, address 2
[   32.940120] Probing IDE interface ide1...
[   33.563337] Attempting manual resume
[   33.563340] swsusp: Resume From Partition 8:2
[   33.563341] PM: Checking swsusp image.
[   33.563722] PM: Resume from disk failed.
[   33.582246] EXT3-fs: INFO: recovery required on readonly filesystem.
[   33.582249] EXT3-fs: write access will be enabled during recovery.
[   33.700209] usb 7-5: new high speed USB device using ehci_hcd and address 3
[   34.091179] usb 7-5: configuration #1 chosen from 1 choice
[   34.331129] usb 7-6: new high speed USB device using ehci_hcd and address 4
[   34.463602] usb 7-6: configuration #1 chosen from 1 choice
[   34.463288] usbcore: registered new interface driver libusual
[   34.466525] Initializing USB Mass Storage driver...
[   34.774233] usb 1-2: new full speed USB device using ohci_hcd and address 3
[   34.993238] usb 1-2: configuration #1 chosen from 1 choice
[   34.995066] hub 1-2:1.0: USB hub found
[   34.997508] hub 1-2:1.0: 2 ports detected
[   35.105947] scsi6 : SCSI emulation for USB Mass Storage devices
[   35.106444] usbcore: registered new interface driver usb-storage
[   35.106448] USB Mass Storage support registered.
[   35.106526] usb-storage: device found at 3
[   35.106527] usb-storage: waiting for device to settle before scanning
[   35.416326] usb 2-1: new low speed USB device using ohci_hcd and address 2
[   35.636027] usb 2-1: configuration #1 chosen from 1 choice
[   35.951074] usb 3-1: new full speed USB device using ohci_hcd and address 2
[   36.163060] usb 3-1: configuration #1 chosen from 1 choice
[   36.165100] usbcore: registered new interface driver hiddev
[   36.169168] input: USB Optical Wheel Mouse as /devices/pci0000:00/0000:00:12.1/usb2/2-1/2-1:1.0/input/input2
[   36.199641] input,hidraw0: USB HID v1.10 Mouse [USB Optical Wheel Mouse] on usb-0000:00:12.1-1
[   36.199656] usbcore: registered new interface driver usbhid
[   36.199659] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   36.371648] usb 1-2.1: new full speed USB device using ohci_hcd and address 4
[   36.479536] usb 1-2.1: configuration #1 chosen from 1 choice
[   36.639964] kjournald starting.  Commit interval 5 seconds
[   36.640451] EXT3-fs: sda1: orphan cleanup on readonly fs
[   36.690092] usb 1-2.2: new full speed USB device using ohci_hcd and address 5
[   36.707837] ext3_orphan_cleanup: deleting unreferenced inode 26796824
[   36.797863] ext3_orphan_cleanup: deleting unreferenced inode 25756279
[   36.797901] ext3_orphan_cleanup: deleting unreferenced inode 27082756
[   36.797907] EXT3-fs: sda1: 3 orphan inodes deleted
[   36.797909] EXT3-fs: recovery complete.
[   36.797990] usb 1-2.2: configuration #1 chosen from 1 choice
[   37.112515] EXT3-fs: mounted filesystem with ordered data mode.
[   40.095585] usb-storage: device scan complete
[   40.101341] scsi 6:0:0:0: Direct-Access     Generic- Compact Flash    1.00 PQ: 0 ANSI: 0 CCS
[   40.107571] scsi 6:0:0:1: Direct-Access     Generic- SM/xD-Picture    1.00 PQ: 0 ANSI: 0 CCS
[   40.113809] scsi 6:0:0:2: Direct-Access     Generic- SD/MMC           1.00 PQ: 0 ANSI: 0 CCS
[   40.120046] scsi 6:0:0:3: Direct-Access     Generic- MS/MS-Pro        1.00 PQ: 0 ANSI: 0 CCS
[   40.481123] sd 6:0:0:0: [sdb] 31808 512-byte hardware sectors (16 MB)
[   40.481999] sd 6:0:0:0: [sdb] Write Protect is off
[   40.482001] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   40.482002] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   40.484491] sd 6:0:0:0: [sdb] 31808 512-byte hardware sectors (16 MB)
[   40.485366] sd 6:0:0:0: [sdb] Write Protect is off
[   40.485368] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   40.485369] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   40.485372]  sdb: sdb1
[   40.487408] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[   40.487429] sd 6:0:0:0: Attached scsi generic sg2 type 0
[   40.488504] sd 6:0:0:1: [sdc] Attached SCSI removable disk
[   40.488523] sd 6:0:0:1: Attached scsi generic sg3 type 0
[   41.011157] sd 6:0:0:2: [sdd] 3842048 512-byte hardware sectors (1967 MB)
[   41.012032] sd 6:0:0:2: [sdd] Write Protect is off
[   41.012034] sd 6:0:0:2: [sdd] Mode Sense: 03 00 00 00
[   41.012035] sd 6:0:0:2: [sdd] Assuming drive cache: write through
[   41.014525] sd 6:0:0:2: [sdd] 3842048 512-byte hardware sectors (1967 MB)
[   41.015401] sd 6:0:0:2: [sdd] Write Protect is off
[   41.015402] sd 6:0:0:2: [sdd] Mode Sense: 03 00 00 00
[   41.015404] sd 6:0:0:2: [sdd] Assuming drive cache: write through
[   41.015406]  sdd: sdd1
[   41.016179] sd 6:0:0:2: [sdd] Attached SCSI removable disk
[   41.016198] sd 6:0:0:2: Attached scsi generic sg4 type 0
[   41.017163] sd 6:0:0:3: [sde] Attached SCSI removable disk
[   41.017186] sd 6:0:0:3: Attached scsi generic sg5 type 0
[   42.219684] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   42.243706] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   42.397577] input: Power Button (FF) as /devices/virtual/input/input3
[   42.426744] ACPI: Power Button (FF) [PWRF]
[   42.426819] input: Power Button (CM) as /devices/virtual/input/input4
[   42.458682] ACPI: Power Button (CM) [PWRB]
[   42.528453] ACPI: WMI-Acer: Mapper loaded
[   42.757049] Linux agpgart interface v0.102
[   43.176340] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   43.212963] [fglrx] Maximum main memory to use for locked dma buffers: 1897 MBytes.
[   43.213003] [fglrx]   vendor: 1002 device: 9490 count: 1
[   43.213051] [fglrx] ioport: bar 4, base 0xee00, size: 0x100
[   43.213068] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 18 (level, low) -> IRQ 16
[   43.213074] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   43.213345] [fglrx] Driver built-in PAT support is enabled successfully
[   43.213367] [fglrx] module loaded - fglrx 8.59.2 [Mar 13 2009] with 1 minors
[   43.417550] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   43.444372] usblp0: USB Bidirectional printer dev 5 if 0 alt 0 proto 2 vid 0x043D pid 0x007B
[   43.444385] usbcore: registered new interface driver usblp
[   43.603209] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   43.685857] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   43.687917] Linux video capture interface: v2.00
[   43.931963] usb 7-6: reset high speed USB device using ehci_hcd and address 4
[   43.961751] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 18
[   43.995175] hda_codec: Unknown model for ALC882, trying auto-probe from BIOS...
[   44.031469] ACPI: PCI Interrupt 0000:01:00.1[B] -> GSI 19 (level, low) -> IRQ 20
[   44.031488] PCI: Setting latency timer of device 0000:01:00.1 to 64
[   44.079294] ndiswrapper: driver sis163u (TRENDnet,11/02/2005,5.1.1039.1050) loaded
[   44.509774] wlan0: ethernet device 00:18:e7:0a:9d:f9 using NDIS driver: sis163u, version: 0x1000000, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0457:0163.F.conf
[   44.510939] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   44.512177] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: USB GSPCA camera found. SONIX sn9c10[1 2]
[   44.513318] usbcore: registered new interface driver ndiswrapper
[   44.513434] usbcore: registered new interface driver gspca
[   44.513437] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: gspca driver 01.00.20 registered
[   44.653745] sn9c102: V4L2 driver for SN9C1xx PC Camera Controllers v1:1.47
[   44.653781] usbcore: registered new interface driver sn9c102
[   44.856264] lp: driver loaded but no devices found
[   44.945912] Adding 2441872k swap on /dev/sda2.  Priority:-1 extents:1 across:2441872k
[   45.497474] EXT3 FS on sda1, internal journal
[   45.867832] NET: Registered protocol family 17
[   46.880134] ip_tables: (C) 2000-2006 Netfilter Core Team
[   47.193004] No dock devices found.
[   47.627706] powernow-k8: Found 1 AMD Athlon(tm) Dual Core Processor 4850e processors (2 cpu cores) (version 2.20.00)
[   47.627284] powernow-k8:    0 : fid 0x11 (2500 MHz), vid 0xe
[   47.627288] powernow-k8:    1 : fid 0x10 (2400 MHz), vid 0xf
[   47.627290] powernow-k8:    2 : fid 0xe (2200 MHz), vid 0x11
[   47.627292] powernow-k8:    3 : fid 0xc (2000 MHz), vid 0x13
[   47.627293] powernow-k8:    4 : fid 0xa (1800 MHz), vid 0x15
[   47.627295] powernow-k8:    5 : fid 0x2 (1000 MHz), vid 0x16
[   48.236804] NET: Registered protocol family 10
[   48.236993] lo: Disabled Privacy Extensions
[   48.649498] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   48.649503] apm: disabled - APM is not SMP safe.
[   48.788405] ppdev: user-space parallel port driver
[   48.898632] audit(1238866877.221:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5232 profile="/usr/sbin/cupsd" namespace="default"
[   51.976774] Clocksource tsc unstable (delta = -300120605 ns)
[   54.349285] wlan0: no IPv6 routers present
[   57.968389] [fglrx] Firegl kernel thread PID: 6111
[   57.981092] [fglrx] Gart USWC size:948 M.
[   57.981098] [fglrx] Gart cacheable size:60 M.
[   57.981103] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   57.981105] [fglrx] Reserved FB block: Unshared offset:fdfb000, size:205000 
[   57.981107] [fglrx] Reserved FB block: Unshared offset:1fffb000, size:5000 
[   62.411109] hda-intel: Invalid position buffer, using LPIB read method instead.
[   64.438172] wlan0: no IPv6 routers present
[   70.000364] UDF-fs: No VRS found
[   70.051115] ISO 9660 Extensions: Microsoft Joliet Level 3
[   70.051927] ISOFS: changing to secondary root

So that's what I have from dmesg.

---

### Post by alanwalterthomas on 2009-04-06
I'm not sure if this is related, but I have another problem that occurs about as frequently - wireless internet drops & I can't get it back. I'm using a trendnet TEW-424UB usb stick with the windows 2000 driver running through ndiswrapper. No effects besides the lost internet connection. Tried to restart, then did dmesg.

alan@alan-desktop:~$ sudo /etc/init.d/networking restart
[sudo] password for alan: 
 * Reconfiguring network interfaces...                                    RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.wlan0.pid with pid 5255
removed stale PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:18:e7:0a:9d:f9
Sending on   LPF/wlan0/00:18:e7:0a:9d:f9
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.0.1 port 67
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:18:e7:0a:9d:f9
Sending on   LPF/wlan0/00:18:e7:0a:9d:f9
Sending on   Socket/fallback
receive_packet failed on wlan0: Network is down
Terminated
Failed to bring up wlan0.



Now for the dmesg I ran after trying to get the internet back:


[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-23-generic (buildd@vernadsky) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Mon Jan 26 00:13:11 UTC 2009 (Ubuntu 2.6.24-23.48-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fde0000 (usable)
[    0.000000]  BIOS-e820: 000000007fde0000 - 000000007fde3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fde3000 - 000000007fdf0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007fdf0000 - 000000007fe00000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 1149MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f57f0
[    0.000000] Entering add_active_range(0, 0, 523744) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   523744
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   523744
[    0.000000] On node 0 totalpages: 523744
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2299 pages used for memmap
[    0.000000]   HighMem zone: 292069 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7170 checksum 0
[    0.000000] ACPI: RSDP 000F7170, 0014 (r0 GBT   )
[    0.000000] ACPI: RSDT 7FDE3000, 0038 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: FACP 7FDE3040, 0074 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: DSDT 7FDE30C0, 64A2 (r1 GBT    GBTUACPI     1000 MSFT  3000000)
[    0.000000] ACPI: FACS 7FDE0000, 0040
[    0.000000] ACPI: SSDT 7FDE9640, 028A (r1 PTLTD  POWERNOW        1  LTP        1)
[    0.000000] ACPI: HPET 7FDE9900, 0038 (r1 GBT    GBTUACPI 42302E31 GBTU       98)
[    0.000000] ACPI: MCFG 7FDE9940, 003C (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: APIC 7FDE9580, 0084 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:11 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:11 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x10b9a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 7fe00000:60200000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519653
[    0.000000] Kernel command line: root=UUID=ff73a34a-37a3-44d5-9a60-c33ede9b9246 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2505.438 MHz processor.
[   24.682314] Console: colour VGA+ 80x25
[   24.682317] console [tty0] enabled
[   24.682581] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   24.682861] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   24.750976] Memory: 2064948k/2094976k available (2179k kernel code, 28716k reserved, 1008k data, 368k init, 1177472k highmem)
[   24.750982] virtual kernel memory layout:
[   24.750983]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   24.750984]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   24.750985]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   24.750985]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   24.750986]       .init : 0xc0423000 - 0xc047f000   ( 368 kB)
[   24.750987]       .data : 0xc0320c08 - 0xc041cdc4   (1008 kB)
[   24.750988]       .text : 0xc0100000 - 0xc0320c08   (2179 kB)
[   24.750990] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   24.751018] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   24.751133] hpet clockevent registered
[   24.830992] Calibrating delay using timer specific routine.. 5014.53 BogoMIPS (lpj=10029072)
[   24.831008] Security Framework initialized
[   24.831013] SELinux:  Disabled at boot.
[   24.831024] AppArmor: AppArmor initialized
[   24.831027] Failure registering capabilities with primary security module.
[   24.831033] Mount-cache hash table entries: 512
[   24.831122] Initializing cgroup subsys ns
[   24.831125] Initializing cgroup subsys cpuacct
[   24.831132] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000011f 00000000
[   24.831139] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   24.831141] CPU: L2 Cache: 512K (64 bytes/line)
[   24.831143] CPU 0(2) -> Core 0
[   24.831145] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00020410 00002001 00000000 0000011f 00000000
[   24.831152] Compat vDSO mapped to ffffe000.
[   24.831160] Checking 'hlt' instruction... OK.
[   24.847176] SMP alternatives: switching to UP code
[   24.848103] Early unpacking initramfs... done
[   25.090994] ACPI: Core revision 20070126
[   25.091049] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   25.103012] CPU0: AMD Athlon(tm) Dual Core Processor 4850e stepping 02
[   25.103027] SMP alternatives: switching to SMP code
[   25.103355] Booting processor 1/1 eip 3000
[   25.113792] Initializing CPU#1
[   25.190808] Calibrating delay using timer specific routine.. 5010.72 BogoMIPS (lpj=10021447)
[   25.190814] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000011f 00000000
[   25.190819] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   25.190820] CPU: L2 Cache: 512K (64 bytes/line)
[   25.190822] CPU 1(2) -> Core 1
[   25.190823] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00020410 00002001 00000000 0000011f 00000000
[   25.190505] CPU1: AMD Athlon(tm) Dual Core Processor 4850e stepping 02
[   25.190517] Total of 2 processors activated (10025.25 BogoMIPS).
[   25.190817] ENABLING IO-APIC IRQs
[   25.191035] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   25.338166] Brought up 2 CPUs
[   25.338216] CPU0 attaching sched-domain:
[   25.338218]  domain 0: span 03
[   25.338219]   groups: 01 02
[   25.338222] CPU1 attaching sched-domain:
[   25.338223]  domain 0: span 03
[   25.338224]   groups: 02 01
[   25.338373] net_namespace: 64 bytes
[   25.338380] Booting paravirtualized kernel on bare hardware
[   25.338716] Time: 17:40:54  Date: 04/04/09
[   25.338735] NET: Registered protocol family 16
[   25.338872] EISA bus registered
[   25.338876] ACPI: bus type pci registered
[   25.339804] PCI: PCI BIOS revision 3.00 entry at 0xfb4d0, last bus=2
[   25.339805] PCI: Using configuration type 1
[   25.339814] Setting up standard PCI resources
[   25.343591] ACPI: EC: Look up EC in DSDT
[   25.347498] ACPI: Interpreter enabled
[   25.347503] ACPI: (supports S0 S1 S4 S5)
[   25.347516] ACPI: Using IOAPIC for interrupt routing
[   25.351107] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   25.352141] PCI: Transparent bridge - 0000:00:14.4
[   25.352162] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   25.352351] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[   25.352431] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
[   25.365035] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   25.365119] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   25.365199] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   25.365279] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   25.365359] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   25.365439] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   25.365520] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   25.365600] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   25.365693] Linux Plug and Play Support v0.97 (c) Adam Belay
[   25.365715] pnp: PnP ACPI init
[   25.365720] ACPI: bus type pnp registered
[   25.367609] pnp: PnP ACPI: found 12 devices
[   25.367610] ACPI: ACPI bus type pnp unregistered
[   25.367613] PnPBIOS: Disabled by ACPI PNP
[   25.367765] PCI: Using ACPI for IRQ routing
[   25.367767] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   25.367774] PCI: Cannot allocate resource region 3 of device 0000:00:00.0
[   25.421942] NET: Registered protocol family 8
[   25.421943] NET: Registered protocol family 20
[   25.421971] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[   25.421975] hpet0: 4 32-bit timers, 14318180 Hz
[   25.423008] AppArmor: AppArmor Filesystem Enabled
[   25.425930] Time: hpet clocksource has been installed.
[   25.425942] Switched to high resolution mode on CPU 0
[   25.426484] Switched to high resolution mode on CPU 1
[   25.433914] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[   25.433917] system 00:01: ioport range 0x220-0x225 has been reserved
[   25.433919] system 00:01: ioport range 0x290-0x294 has been reserved
[   25.433923] system 00:02: ioport range 0x4100-0x411f has been reserved
[   25.433926] system 00:02: ioport range 0x228-0x22f has been reserved
[   25.433928] system 00:02: ioport range 0x238-0x23f has been reserved
[   25.433930] system 00:02: ioport range 0x40b-0x40b has been reserved
[   25.433932] system 00:02: ioport range 0x4d6-0x4d6 has been reserved
[   25.433934] system 00:02: ioport range 0xc00-0xc01 has been reserved
[   25.433936] system 00:02: ioport range 0xc14-0xc14 has been reserved
[   25.433938] system 00:02: ioport range 0xc50-0xc52 has been reserved
[   25.433940] system 00:02: ioport range 0xc6c-0xc6d has been reserved
[   25.433941] system 00:02: ioport range 0xc6f-0xc6f has been reserved
[   25.433943] system 00:02: ioport range 0xcd0-0xcd1 has been reserved
[   25.433945] system 00:02: ioport range 0xcd2-0xcd3 has been reserved
[   25.433947] system 00:02: ioport range 0xcd4-0xcdf has been reserved
[   25.433949] system 00:02: ioport range 0x4000-0x40fe has been reserved
[   25.433951] system 00:02: ioport range 0x4210-0x4217 has been reserved
[   25.433953] system 00:02: ioport range 0xb00-0xb0f has been reserved
[   25.433955] system 00:02: ioport range 0xb10-0xb1f has been reserved
[   25.433957] system 00:02: ioport range 0xb20-0xb3f has been reserved
[   25.433963] system 00:0a: iomem range 0xe0000000-0xefffffff could not be reserved
[   25.433967] system 00:0b: iomem range 0xd1a00-0xd3fff has been reserved
[   25.433969] system 00:0b: iomem range 0xf0000-0xf7fff could not be reserved
[   25.433971] system 00:0b: iomem range 0xf8000-0xfbfff could not be reserved
[   25.433973] system 00:0b: iomem range 0xfc000-0xfffff could not be reserved
[   25.433975] system 00:0b: iomem range 0x7fde0000-0x7fdfffff could not be reserved
[   25.433978] system 00:0b: iomem range 0xffff0000-0xffffffff could not be reserved
[   25.433980] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
[   25.433982] system 00:0b: iomem range 0x100000-0x7fddffff could not be reserved
[   25.433984] system 00:0b: iomem range 0x0-0x0 could not be reserved
[   25.433986] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
[   25.433988] system 00:0b: iomem range 0xfee00000-0xfee00fff could not be reserved
[   25.433990] system 00:0b: iomem range 0xfff80000-0xfffeffff could not be reserved
[   25.464244] PCI: Bridge: 0000:00:02.0
[   25.464246]   IO window: e000-efff
[   25.464249]   MEM window: fdd00000-fddfffff
[   25.464251]   PREFETCH window: d0000000-dfffffff
[   25.464253] PCI: Bridge: 0000:00:14.4
[   25.464256]   IO window: d000-dfff
[   25.464261]   MEM window: fdf00000-fdffffff
[   25.464264]   PREFETCH window: fde00000-fdefffff
[   25.464283] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 18 (level, low) -> IRQ 16
[   25.464287] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   25.464300] NET: Registered protocol family 2
[   25.501821] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   25.502040] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   25.502616] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   25.502865] TCP: Hash tables configured (established 131072 bind 65536)
[   25.502867] TCP reno registered
[   25.513858] checking if image is initramfs... it is
[   25.982924] Freeing initrd memory: 7327k freed
[   25.984035] audit: initializing netlink socket (disabled)
[   25.984046] audit(1238866854.120:1): initialized
[   25.984187] highmem bounce pool size: 64 pages
[   25.985646] VFS: Disk quotas dquot_6.5.1
[   25.985700] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   25.985788] io scheduler noop registered
[   25.985790] io scheduler anticipatory registered
[   25.985791] io scheduler deadline registered
[   25.985799] io scheduler cfq registered (default)
[   26.125141] Boot video device is 0000:01:00.0
[   26.125259] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   26.125281] assign_interrupt_mode Found MSI capability
[   26.125302] Allocate Port Service[0000:00:02.0:pcie00]
[   26.125482] isapnp: Scanning for PnP cards...
[   26.478680] isapnp: No Plug & Play device found
[   26.500192] Real Time Clock Driver v1.12ac
[   26.500336] hpet_resources: 0xfed00000 is busy
[   26.500360] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   26.501508] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   26.501556] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   26.501624] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   26.501626] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[   26.501726] serio: i8042 KBD port at 0x60,0x64 irq 1
[   26.517459] mice: PS/2 mouse device common for all mice
[   26.517555] EISA: Probing bus 0 at eisa.0
[   26.517573] Cannot allocate resource for EISA slot 4
[   26.517589] EISA: Detected 0 cards.
[   26.517591] cpuidle: using governor ladder
[   26.517593] cpuidle: using governor menu
[   26.517657] NET: Registered protocol family 1
[   26.517677] Using IPI No-Shortcut mode
[   26.517703] registered taskstats version 1
[   26.517780]   Magic number: 5:223:693
[   26.517903] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   26.517904] EDD information not available.
[   26.518102] Freeing unused kernel memory: 368k freed
[   26.518123] Write protecting the kernel read-only data: 806k
[   26.552349] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   27.665508] fuse init (API version 7.9)
[   27.680148] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
[   27.680159] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
[   27.777844] SCSI subsystem initialized
[   27.813122] libata version 3.00 loaded.
[   27.814545] ahci 0000:00:11.0: version 3.0
[   27.814578] ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 22 (level, low) -> IRQ 17
[   27.814627] ahci 0000:00:11.0: controller can't do PMP, turning off CAP_PMP
[   27.872749] usbcore: registered new interface driver usbfs
[   27.872768] usbcore: registered new interface driver hub
[   27.872788] usbcore: registered new device driver usb
[   27.873622] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   27.961553] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   27.961625] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   28.021566] Floppy drive(s): fd0 is 1.44M
[   28.042451] FDC 0 is a post-1991 82077
[   28.815758] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[   28.815762] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pio slum part 
[   28.816212] scsi0 : ahci
[   28.816264] scsi1 : ahci
[   28.816292] scsi2 : ahci
[   28.816324] scsi3 : ahci
[   28.816350] scsi4 : ahci
[   28.816379] scsi5 : ahci
[   28.816446] ata1: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f100 irq 222
[   28.816449] ata2: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 222
[   28.816452] ata3: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f200 irq 222
[   28.816455] ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 222
[   28.816458] ata5: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f300 irq 222
[   28.816461] ata6: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f380 irq 222
[   29.290840] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   29.292720] ata1.00: ATA-8: ST3500320AS, SD15, max UDMA/133
[   29.292724] ata1.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[   29.294478] ata1.00: configured for UDMA/133
[   29.602265] ata2: SATA link down (SStatus 0 SControl 300)
[   30.077392] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   30.234225] ata3.00: ATAPI: TSSTcorp CDDVDW SH-S223Q, SB00, max UDMA/100, ATAPI AN
[   30.389947] ata3.00: configured for UDMA/100
[   30.700243] ata4: SATA link down (SStatus 0 SControl 300)
[   31.011669] ata5: SATA link down (SStatus 0 SControl 300)
[   31.323096] ata6: SATA link down (SStatus 0 SControl 300)
[   31.323181] scsi 0:0:0:0: Direct-Access     ATA      ST3500320AS      SD15 PQ: 0 ANSI: 5
[   31.324154] scsi 2:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S223Q  SB00 PQ: 0 ANSI: 5
[   31.323783] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 16 (level, low) -> IRQ 18
[   31.323797] ohci_hcd 0000:00:12.0: OHCI Host Controller
[   31.324032] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 1
[   31.324053] ohci_hcd 0000:00:12.0: irq 18, io mem 0xfe02e000
[   31.332197] Driver 'sd' needs updating - please use bus_type methods
[   31.334782] Driver 'sr' needs updating - please use bus_type methods
[   31.340112] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[   31.340121] sd 0:0:0:0: [sda] Write Protect is off
[   31.340123] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   31.340135] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   31.340173] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[   31.340180] sd 0:0:0:0: [sda] Write Protect is off
[   31.340181] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   31.340191] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   31.340193]  sda: sda1 sda2
[   31.380935] sd 0:0:0:0: [sda] Attached SCSI disk
[   31.383066] usb usb1: configuration #1 chosen from 1 choice
[   31.383084] hub 1-0:1.0: USB hub found
[   31.383092] hub 1-0:1.0: 3 ports detected
[   31.384614] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   31.384628] sr 2:0:0:0: Attached scsi generic sg1 type 5
[   31.387693] sr0: scsi3-mmc drive: 125x/125x writer dvd-ram cd/rw xa/form2 cdda tray
[   31.387697] Uniform CD-ROM driver Revision: 3.20
[   31.387740] sr 2:0:0:0: Attached scsi CD-ROM sr0
[   31.486868] ACPI: PCI Interrupt 0000:00:12.1[A] -> GSI 16 (level, low) -> IRQ 18
[   31.486882] ohci_hcd 0000:00:12.1: OHCI Host Controller
[   31.486900] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 2
[   31.486915] ohci_hcd 0000:00:12.1: irq 18, io mem 0xfe02d000
[   31.546753] usb usb2: configuration #1 chosen from 1 choice
[   31.546771] hub 2-0:1.0: USB hub found
[   31.546778] hub 2-0:1.0: 3 ports detected
[   31.650541] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 18 (level, low) -> IRQ 16
[   31.650552] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   31.650571] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 3
[   31.650588] ohci_hcd 0000:00:13.0: irq 16, io mem 0xfe02b000
[   31.710420] usb usb3: configuration #1 chosen from 1 choice
[   31.710434] hub 3-0:1.0: USB hub found
[   31.710440] hub 3-0:1.0: 3 ports detected
[   31.798212] usb 1-2: new full speed USB device using ohci_hcd and address 2
[   31.814233] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 18 (level, low) -> IRQ 16
[   31.814240] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   31.814259] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 4
[   31.814270] ohci_hcd 0000:00:13.1: irq 16, io mem 0xfe02a000
[   31.874127] usb usb4: configuration #1 chosen from 1 choice
[   31.874141] hub 4-0:1.0: USB hub found
[   31.874147] hub 4-0:1.0: 3 ports detected
[   31.977932] ACPI: PCI Interrupt 0000:00:14.5[C] -> GSI 18 (level, low) -> IRQ 16
[   31.977940] ohci_hcd 0000:00:14.5: OHCI Host Controller
[   31.977953] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 5
[   31.977965] ohci_hcd 0000:00:14.5: irq 16, io mem 0xfe028000
[   32.013459] usb 1-2: configuration #1 chosen from 1 choice
[   32.015398] hub 1-2:1.0: USB hub found
[   32.017378] hub 1-2:1.0: 2 ports detected
[   32.037819] usb usb5: configuration #1 chosen from 1 choice
[   32.037835] hub 5-0:1.0: USB hub found
[   32.037840] hub 5-0:1.0: 2 ports detected
[   32.141897] ACPI: PCI Interrupt 0000:00:12.2[B] -> GSI 17 (level, low) -> IRQ 19
[   32.141907] ehci_hcd 0000:00:12.2: EHCI Host Controller
[   32.141924] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 6
[   32.141956] ehci_hcd 0000:00:12.2: debug port 1
[   32.141971] ehci_hcd 0000:00:12.2: irq 19, io mem 0xfe02c000
[   32.153566] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   32.153669] usb usb6: configuration #1 chosen from 1 choice
[   32.153688] hub 6-0:1.0: USB hub found
[   32.153693] hub 6-0:1.0: 6 ports detected
[   32.257457] ACPI: PCI Interrupt 0000:00:13.2[B] -> GSI 19 (level, low) -> IRQ 20
[   32.257471] ehci_hcd 0000:00:13.2: EHCI Host Controller
[   32.257490] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 7
[   32.257523] ehci_hcd 0000:00:13.2: debug port 1
[   32.257538] ehci_hcd 0000:00:13.2: irq 20, io mem 0xfe029000
[   32.269345] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   32.269414] usb usb7: configuration #1 chosen from 1 choice
[   32.269430] hub 7-0:1.0: USB hub found
[   32.269434] hub 7-0:1.0: 6 ports detected
[   32.373281] ATIIXP: IDE controller (0x1002:0x439c rev 0x00) at  PCI slot 0000:00:14.1
[   32.373294] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 18
[   32.373301] ATIIXP: not 100% native mode: will probe irqs later
[   32.373308]     ide0: BM-DMA at 0xfa00-0xfa07, BIOS settings: hda:pio, hdb:pio
[   32.373319] ATIIXP: simplex device: DMA disabled
[   32.373320] ide1: ATIIXP Bus-Master DMA disabled (BIOS)
[   32.373323] Probing IDE interface ide0...
[   32.414596] usb 1-2: USB disconnect, address 2
[   32.940120] Probing IDE interface ide1...
[   33.563337] Attempting manual resume
[   33.563340] swsusp: Resume From Partition 8:2
[   33.563341] PM: Checking swsusp image.
[   33.563722] PM: Resume from disk failed.
[   33.582246] EXT3-fs: INFO: recovery required on readonly filesystem.
[   33.582249] EXT3-fs: write access will be enabled during recovery.
[   33.700209] usb 7-5: new high speed USB device using ehci_hcd and address 3
[   34.091179] usb 7-5: configuration #1 chosen from 1 choice
[   34.331129] usb 7-6: new high speed USB device using ehci_hcd and address 4
[   34.463602] usb 7-6: configuration #1 chosen from 1 choice
[   34.463288] usbcore: registered new interface driver libusual
[   34.466525] Initializing USB Mass Storage driver...
[   34.774233] usb 1-2: new full speed USB device using ohci_hcd and address 3
[   34.993238] usb 1-2: configuration #1 chosen from 1 choice
[   34.995066] hub 1-2:1.0: USB hub found
[   34.997508] hub 1-2:1.0: 2 ports detected
[   35.105947] scsi6 : SCSI emulation for USB Mass Storage devices
[   35.106444] usbcore: registered new interface driver usb-storage
[   35.106448] USB Mass Storage support registered.
[   35.106526] usb-storage: device found at 3
[   35.106527] usb-storage: waiting for device to settle before scanning
[   35.416326] usb 2-1: new low speed USB device using ohci_hcd and address 2
[   35.636027] usb 2-1: configuration #1 chosen from 1 choice
[   35.951074] usb 3-1: new full speed USB device using ohci_hcd and address 2
[   36.163060] usb 3-1: configuration #1 chosen from 1 choice
[   36.165100] usbcore: registered new interface driver hiddev
[   36.169168] input: USB Optical Wheel Mouse as /devices/pci0000:00/0000:00:12.1/usb2/2-1/2-1:1.0/input/input2
[   36.199641] input,hidraw0: USB HID v1.10 Mouse [USB Optical Wheel Mouse] on usb-0000:00:12.1-1
[   36.199656] usbcore: registered new interface driver usbhid
[   36.199659] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   36.371648] usb 1-2.1: new full speed USB device using ohci_hcd and address 4
[   36.479536] usb 1-2.1: configuration #1 chosen from 1 choice
[   36.639964] kjournald starting.  Commit interval 5 seconds
[   36.640451] EXT3-fs: sda1: orphan cleanup on readonly fs
[   36.690092] usb 1-2.2: new full speed USB device using ohci_hcd and address 5
[   36.707837] ext3_orphan_cleanup: deleting unreferenced inode 26796824
[   36.797863] ext3_orphan_cleanup: deleting unreferenced inode 25756279
[   36.797901] ext3_orphan_cleanup: deleting unreferenced inode 27082756
[   36.797907] EXT3-fs: sda1: 3 orphan inodes deleted
[   36.797909] EXT3-fs: recovery complete.
[   36.797990] usb 1-2.2: configuration #1 chosen from 1 choice
[   37.112515] EXT3-fs: mounted filesystem with ordered data mode.
[   40.095585] usb-storage: device scan complete
[   40.101341] scsi 6:0:0:0: Direct-Access     Generic- Compact Flash    1.00 PQ: 0 ANSI: 0 CCS
[   40.107571] scsi 6:0:0:1: Direct-Access     Generic- SM/xD-Picture    1.00 PQ: 0 ANSI: 0 CCS
[   40.113809] scsi 6:0:0:2: Direct-Access     Generic- SD/MMC           1.00 PQ: 0 ANSI: 0 CCS
[   40.120046] scsi 6:0:0:3: Direct-Access     Generic- MS/MS-Pro        1.00 PQ: 0 ANSI: 0 CCS
[   40.481123] sd 6:0:0:0: [sdb] 31808 512-byte hardware sectors (16 MB)
[   40.481999] sd 6:0:0:0: [sdb] Write Protect is off
[   40.482001] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   40.482002] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   40.484491] sd 6:0:0:0: [sdb] 31808 512-byte hardware sectors (16 MB)
[   40.485366] sd 6:0:0:0: [sdb] Write Protect is off
[   40.485368] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   40.485369] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   40.485372]  sdb: sdb1
[   40.487408] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[   40.487429] sd 6:0:0:0: Attached scsi generic sg2 type 0
[   40.488504] sd 6:0:0:1: [sdc] Attached SCSI removable disk
[   40.488523] sd 6:0:0:1: Attached scsi generic sg3 type 0
[   41.011157] sd 6:0:0:2: [sdd] 3842048 512-byte hardware sectors (1967 MB)
[   41.012032] sd 6:0:0:2: [sdd] Write Protect is off
[   41.012034] sd 6:0:0:2: [sdd] Mode Sense: 03 00 00 00
[   41.012035] sd 6:0:0:2: [sdd] Assuming drive cache: write through
[   41.014525] sd 6:0:0:2: [sdd] 3842048 512-byte hardware sectors (1967 MB)
[   41.015401] sd 6:0:0:2: [sdd] Write Protect is off
[   41.015402] sd 6:0:0:2: [sdd] Mode Sense: 03 00 00 00
[   41.015404] sd 6:0:0:2: [sdd] Assuming drive cache: write through
[   41.015406]  sdd: sdd1
[   41.016179] sd 6:0:0:2: [sdd] Attached SCSI removable disk
[   41.016198] sd 6:0:0:2: Attached scsi generic sg4 type 0
[   41.017163] sd 6:0:0:3: [sde] Attached SCSI removable disk
[   41.017186] sd 6:0:0:3: Attached scsi generic sg5 type 0
[   42.219684] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   42.243706] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   42.397577] input: Power Button (FF) as /devices/virtual/input/input3
[   42.426744] ACPI: Power Button (FF) [PWRF]
[   42.426819] input: Power Button (CM) as /devices/virtual/input/input4
[   42.458682] ACPI: Power Button (CM) [PWRB]
[   42.528453] ACPI: WMI-Acer: Mapper loaded
[   42.757049] Linux agpgart interface v0.102
[   43.176340] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   43.212963] [fglrx] Maximum main memory to use for locked dma buffers: 1897 MBytes.
[   43.213003] [fglrx]   vendor: 1002 device: 9490 count: 1
[   43.213051] [fglrx] ioport: bar 4, base 0xee00, size: 0x100
[   43.213068] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 18 (level, low) -> IRQ 16
[   43.213074] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   43.213345] [fglrx] Driver built-in PAT support is enabled successfully
[   43.213367] [fglrx] module loaded - fglrx 8.59.2 [Mar 13 2009] with 1 minors
[   43.417550] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   43.444372] usblp0: USB Bidirectional printer dev 5 if 0 alt 0 proto 2 vid 0x043D pid 0x007B
[   43.444385] usbcore: registered new interface driver usblp
[   43.603209] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   43.685857] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   43.687917] Linux video capture interface: v2.00
[   43.931963] usb 7-6: reset high speed USB device using ehci_hcd and address 4
[   43.961751] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 18
[   43.995175] hda_codec: Unknown model for ALC882, trying auto-probe from BIOS...
[   44.031469] ACPI: PCI Interrupt 0000:01:00.1[B] -> GSI 19 (level, low) -> IRQ 20
[   44.031488] PCI: Setting latency timer of device 0000:01:00.1 to 64
[   44.079294] ndiswrapper: driver sis163u (TRENDnet,11/02/2005,5.1.1039.1050) loaded
[   44.509774] wlan0: ethernet device 00:18:e7:0a:9d:f9 using NDIS driver: sis163u, version: 0x1000000, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0457:0163.F.conf
[   44.510939] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   44.512177] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: USB GSPCA camera found. SONIX sn9c10[1 2]
[   44.513318] usbcore: registered new interface driver ndiswrapper
[   44.513434] usbcore: registered new interface driver gspca
[   44.513437] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: gspca driver 01.00.20 registered
[   44.653745] sn9c102: V4L2 driver for SN9C1xx PC Camera Controllers v1:1.47
[   44.653781] usbcore: registered new interface driver sn9c102
[   44.856264] lp: driver loaded but no devices found
[   44.945912] Adding 2441872k swap on /dev/sda2.  Priority:-1 extents:1 across:2441872k
[   45.497474] EXT3 FS on sda1, internal journal
[   45.867832] NET: Registered protocol family 17
[   46.880134] ip_tables: (C) 2000-2006 Netfilter Core Team
[   47.193004] No dock devices found.
[   47.627706] powernow-k8: Found 1 AMD Athlon(tm) Dual Core Processor 4850e processors (2 cpu cores) (version 2.20.00)
[   47.627284] powernow-k8:    0 : fid 0x11 (2500 MHz), vid 0xe
[   47.627288] powernow-k8:    1 : fid 0x10 (2400 MHz), vid 0xf
[   47.627290] powernow-k8:    2 : fid 0xe (2200 MHz), vid 0x11
[   47.627292] powernow-k8:    3 : fid 0xc (2000 MHz), vid 0x13
[   47.627293] powernow-k8:    4 : fid 0xa (1800 MHz), vid 0x15
[   47.627295] powernow-k8:    5 : fid 0x2 (1000 MHz), vid 0x16
[   48.236804] NET: Registered protocol family 10
[   48.236993] lo: Disabled Privacy Extensions
[   48.649498] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   48.649503] apm: disabled - APM is not SMP safe.
[   48.788405] ppdev: user-space parallel port driver
[   48.898632] audit(1238866877.221:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5232 profile="/usr/sbin/cupsd" namespace="default"
[   51.976774] Clocksource tsc unstable (delta = -300120605 ns)
[   54.349285] wlan0: no IPv6 routers present
[   57.968389] [fglrx] Firegl kernel thread PID: 6111
[   57.981092] [fglrx] Gart USWC size:948 M.
[   57.981098] [fglrx] Gart cacheable size:60 M.
[   57.981103] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   57.981105] [fglrx] Reserved FB block: Unshared offset:fdfb000, size:205000 
[   57.981107] [fglrx] Reserved FB block: Unshared offset:1fffb000, size:5000 
[   62.411109] hda-intel: Invalid position buffer, using LPIB read method instead.
[   64.438172] wlan0: no IPv6 routers present
[   70.000364] UDF-fs: No VRS found
[   70.051115] ISO 9660 Extensions: Microsoft Joliet Level 3
[   70.051927] ISOFS: changing to secondary root
[  161.241618] process `skype' is using obsolete setsockopt SO_BSDCOMPAT




Terminal output may as well be Greek to me. Are there instructions anywhere for how to diagnose a problem from dmesg, or is that just for our beloved supergeeks? I hope someone can make sense out of what I just posted to work out either problem. Thanks a lot.

---

