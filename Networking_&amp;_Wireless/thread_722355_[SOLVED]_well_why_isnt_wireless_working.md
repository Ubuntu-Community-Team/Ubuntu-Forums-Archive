---
title: "[SOLVED] well why isnt wireless working?"
date: 2008-03-12
forum: Networking &amp; Wireless
---

### Post by jrockpunk1 on 2008-03-12
ok so before you say oh go to [http://www.justfuckinggoogleit.com/](http://www.justfuckinggoogleit.com/) , hear me out. ive read multiple tutorials (some off this site) to no avail. i just cant figure it out. so ive set up my belkin router on another computer, copied its name, WEP key etc etc. ive gone to system > administration > network, and entered in the SSID, the hex password and assigned it to DHCP (ive also tried static and entered all the info for that as well). i enable it and tick the box, but still when i go on the internet it says "cannot connect to server". ive also read tuts on how to enable wireless card, and ive dont that to no avail. anyone help me with this? oh and this is the result of lspci:

```

jay@jay-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
06:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

any help very much appreciated

jrockpunk1

---

### Post by azimuth on 2008-03-12
I don't see your wireless card on your pci buss. What does dmesg show?

---

### Post by jrockpunk1 on 2008-03-12
dmesg shows:

```

[    0.000000]  BIOS-e820: 000000001f700000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 502MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f7860
[    0.000000] Entering add_active_range(0, 0, 128656) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   128656
[    0.000000]   HighMem    128656 ->   128656
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   128656
[    0.000000] On node 0 totalpages: 128656
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 973 pages used for memmap
[    0.000000]   Normal zone: 123587 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F77B0 checksum 0
[    0.000000] ACPI: RSDP 000F77B0, 0014 (r0 DSGLTD)
[    0.000000] ACPI: RSDT 1F697E56, 0050 (r1 DSGLTD DSGVISTA  6040000  LTP        0)
[    0.000000] ACPI: FACP 1F69DCB8, 0074 (r1 INTEL  CALISTGA  6040000 LOHR       5A)
[    0.000000] ACPI: DSDT 1F699243, 4A75 (r1 UW____ FUW_____  6040000 INTL 20050624)
[    0.000000] ACPI: FACS 1F69EFC0, 0040
[    0.000000] ACPI: APIC 1F69DD2C, 0068 (r1 INTEL  CALISTGA  6040000 LOHR       5A)
[    0.000000] ACPI: HPET 1F69DD94, 0038 (r1 INTEL  CALISTGA  6040000 LOHR       5A)
[    0.000000] ACPI: MCFG 1F69DDCC, 003C (r1 INTEL  CALISTGA  6040000 LOHR       5A)
[    0.000000] ACPI: APIC 1F69DE08, 005A (r1 DSGLTD DSGVISTA  6040000  LTP        0)
[    0.000000] ACPI: SLIC 1F69DE62, 0176 (r1 DSGLTD DSGVISTA  6040000  LTP        0)
[    0.000000] ACPI: BOOT 1F69DFD8, 0028 (r1 MSTEST TESTONLY  6040000  LTP        1)
[    0.000000] ACPI: SSDT 1F698BF4, 064F (r1 SataRe  SataPri     1000 INTL 20050624)
[    0.000000] ACPI: SSDT 1F698562, 0692 (r1 SataRe  SataSec     1000 INTL 20050624)
[    0.000000] ACPI: SSDT 1F69839C, 01C6 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[    0.000000] ACPI: SSDT 1F697EA6, 04F6 (r1  PmRef    CpuPm     3000 INTL 20050624)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:14 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
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
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:c0000000)
[    0.000000] Built 1 zonelists.  Total pages: 127651
[    0.000000] Kernel command line: root=UUID=1ac7bca8-cd76-48fc-b59c-837a1ff50cd9 ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 1600.212 MHz processor.
[   14.577823] Console: colour VGA+ 80x25
[   14.577983] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   14.578187] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   14.590846] Memory: 498964k/514624k available (1929k kernel code, 15096k reserved, 876k data, 348k init, 0k highmem)
[   14.590856] virtual kernel memory layout:
[   14.590857]     fixmap  : 0xfffa8000 - 0xfffff000   ( 348 kB)
[   14.590859]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   14.590860]     vmalloc : 0xe0000000 - 0xff7fe000   ( 503 MB)
[   14.590862]     lowmem  : 0xc0000000 - 0xdf690000   ( 502 MB)
[   14.590863]       .init : 0xc03c0000 - 0xc0417000   ( 348 kB)
[   14.590864]       .data : 0xc02e2655 - 0xc03bda04   ( 876 kB)
[   14.590866]       .text : 0xc0100000 - 0xc02e2655   (1929 kB)
[   14.590869] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   14.590910] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   14.591060] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   14.591066] hpet0: 3 64-bit timers, 14318180 Hz
[   14.671960] Calibrating delay using timer specific routine.. 3203.62 BogoMIPS (lpj=6407247)
[   14.671981] Security Framework v1.0.0 initialized
[   14.671988] SELinux:  Disabled at boot.
[   14.671994] Mount-cache hash table entries: 512
[   14.672086] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 0000c109 00000000 00000000
[   14.672095] monitor/mwait feature present.
[   14.672097] using mwait in idle threads.
[   14.672101] CPU: L1 I cache: 32K, L1 D cache: 32K
[   14.672104] CPU: L2 cache: 1024K
[   14.672106] CPU: After all inits, caps: afe9fbff 00100000 00000000 00002940 0000c109 00000000 00000000
[   14.672113] Compat vDSO mapped to ffffe000.
[   14.672124] CPU: Intel(R) Celeron(R) M CPU        420  @ 1.60GHz stepping 08
[   14.672130] Checking 'hlt' instruction... OK.
[   14.688453] Early unpacking initramfs... done
[   15.043836] ACPI: Core revision 20070126
[   15.043898] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   15.074035] ENABLING IO-APIC IRQs
[   15.074237] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   15.219190] Booting paravirtualized kernel on bare hardware
[   15.219279] Time: 15:34:27  Date: 02/12/108
[   15.219298] NET: Registered protocol family 16
[   15.219373] EISA bus registered
[   15.219378] ACPI: bus type pci registered
[   15.258184] PCI: PCI BIOS revision 2.10 entry at 0xfd843, last bus=6
[   15.258187] PCI: Using configuration type 1
[   15.258189] Setting up standard PCI resources
[   15.262078] ACPI: EC: Look up EC in DSDT
[   15.262673] ACPI: EC: GPE=0x19, ports=0x66, 0x62
[   15.264028] ACPI: System BIOS is requesting _OSI(Linux)
[   15.264030] ACPI: Please test with "acpi_osi=!Linux"
[   15.264032] Please send dmidecode to linux-acpi@vger.kernel.org
[   15.264593] ACPI: Interpreter enabled
[   15.264596] ACPI: (supports S0 S3 S4 S5)
[   15.264612] ACPI: Using IOAPIC for interrupt routing
[   15.270141] ACPI: EC: GPE=0x19, ports=0x66, 0x62
[   15.270195] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   15.270205] PCI: Probing PCI hardware (bus 00)
[   15.270935] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   15.270940] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[   15.271581] PCI: Transparent bridge - 0000:00:1e.0
[   15.271656] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   15.271980] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[   15.272116] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[   15.272250] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[   15.272399] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   15.275129] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   15.275232] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[   15.275332] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 *3 4 5 6 7 10 12 14 15)
[   15.275431] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   15.275530] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[   15.275629] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[   15.275728] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[   15.275826] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[   15.275928] Linux Plug and Play Support v0.97 (c) Adam Belay
[   15.275941] pnp: PnP ACPI init
[   15.275949] ACPI: bus type pnp registered
[   15.277693] pnp: PnP ACPI: found 11 devices
[   15.277696] ACPI: ACPI bus type pnp unregistered
[   15.277700] PnPBIOS: Disabled by ACPI PNP
[   15.277742] PCI: Using ACPI for IRQ routing
[   15.277745] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   15.292704] NET: Registered protocol family 8
[   15.292706] NET: Registered protocol family 20
[   15.292759] pnp: 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[   15.292763] pnp: 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
[   15.292767] pnp: 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
[   15.292770] pnp: 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
[   15.292777] pnp: 00:04: iomem range 0xfed00000-0xfed003ff could not be reserved
[   15.292784] pnp: 00:07: ioport range 0x6a0-0x6af has been reserved
[   15.292787] pnp: 00:07: ioport range 0x6b0-0x6ff has been reserved
[   15.295008] Time: tsc clocksource has been installed.
[   15.295025] Switched to high resolution mode on CPU 0
[   15.323016] PCI: Bridge: 0000:00:1c.0
[   15.323020]   IO window: f000-ffff
[   15.323026]   MEM window: fac00000-febfffff
[   15.323031]   PREFETCH window: disabled.
[   15.323036] PCI: Bridge: 0000:00:1c.1
[   15.323038]   IO window: disabled.
[   15.323044]   MEM window: disabled.
[   15.323048]   PREFETCH window: disabled.
[   15.323054] PCI: Bridge: 0000:00:1c.2
[   15.323055]   IO window: disabled.
[   15.323061]   MEM window: f7000000-f70fffff
[   15.323066]   PREFETCH window: disabled.
[   15.323072] PCI: Bridge: 0000:00:1e.0
[   15.323075]   IO window: 2000-2fff
[   15.323081]   MEM window: f0200000-f02fffff
[   15.323085]   PREFETCH window: disabled.
[   15.323113] PCI: Enabling device 0000:00:1c.0 (0000 -> 0003)
[   15.323120] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 16
[   15.323129] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   15.323152] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 17
[   15.323160] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   15.323182] PCI: Enabling device 0000:00:1c.2 (0000 -> 0002)
[   15.323186] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[   15.323194] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   15.323208] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   15.323220] NET: Registered protocol family 2
[   15.498698] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   15.498731] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   15.498833] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[   15.498890] TCP: Hash tables configured (established 16384 bind 16384)
[   15.498892] TCP reno registered
[   15.510773] checking if image is initramfs... it is
[   16.215448] Freeing initrd memory: 7096k freed
[   16.215581] Simple Boot Flag at 0x35 set to 0x1
[   16.215901] audit: initializing netlink socket (disabled)
[   16.215915] audit(1205336067.488:1): initialized
[   16.217658] VFS: Disk quotas dquot_6.5.1
[   16.217670] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   16.217762] io scheduler noop registered
[   16.217764] io scheduler anticipatory registered
[   16.217766] io scheduler deadline registered
[   16.217782] io scheduler cfq registered (default)
[   16.217796] Boot video device is 0000:00:02.0
[   16.217953] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   16.218009] assign_interrupt_mode Found MSI capability
[   16.218012] Allocate Port Service[0000:00:1c.0:pcie00]
[   16.218044] Allocate Port Service[0000:00:1c.0:pcie02]
[   16.218137] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   16.218193] assign_interrupt_mode Found MSI capability
[   16.218196] Allocate Port Service[0000:00:1c.1:pcie00]
[   16.218225] Allocate Port Service[0000:00:1c.1:pcie02]
[   16.218315] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   16.218370] assign_interrupt_mode Found MSI capability
[   16.218373] Allocate Port Service[0000:00:1c.2:pcie00]
[   16.218403] Allocate Port Service[0000:00:1c.2:pcie02]
[   16.218547] isapnp: Scanning for PnP cards...
[   16.572397] isapnp: No Plug & Play device found
[   16.594811] hpet_resources: 0xfed00000 is busy
[   16.594838] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   16.595920] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   16.596100] input: Macintosh mouse button emulation as /class/input/input0
[   16.596171] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   16.598726] i8042.c: Detected active multiplexing controller, rev 1.1.
[   16.600203] serio: i8042 KBD port at 0x60,0x64 irq 1
[   16.600208] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   16.600211] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   16.600213] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   16.600216] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   16.600397] mice: PS/2 mouse device common for all mice
[   16.600576] EISA: Probing bus 0 at eisa.0
[   16.600584] Cannot allocate resource for EISA slot 1
[   16.600587] Cannot allocate resource for EISA slot 2
[   16.600613] EISA: Detected 0 cards.
[   16.600709] TCP cubic registered
[   16.600721] NET: Registered protocol family 1
[   16.600746] Using IPI Shortcut mode
[   16.600902]   Magic number: 0:502:588
[   16.600989]   hash matches device ptyc6
[   16.601287] Freeing unused kernel memory: 348k freed
[   16.676863] input: AT Translated Set 2 keyboard as /class/input/input1
[   17.799871] AppArmor: AppArmor initialized<5>audit(1205336069.076:2):  type=1505 info="AppArmor initialized" pid=1245
[   17.807845] fuse init (API version 7.8)
[   17.813075] Failure registering capabilities with primary security module.
[   17.828389] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   17.828396] ACPI: Processor [CPU0] (supports 8 throttling states)
[   17.829648] ACPI: Thermal Zone [THRM] (59 C)
[   18.271832] usbcore: registered new interface driver usbfs
[   18.271856] usbcore: registered new interface driver hub
[   18.271878] usbcore: registered new device driver usb
[   18.272614] USB Universal Host Controller Interface driver v3.0
[   18.272680] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[   18.272691] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   18.272695] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   18.272900] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   18.272934] uhci_hcd 0000:00:1d.0: irq 19, io base 0x00001820
[   18.273046] usb usb1: configuration #1 chosen from 1 choice
[   18.273070] hub 1-0:1.0: USB hub found
[   18.273075] hub 1-0:1.0: 2 ports detected
[   18.373523] SCSI subsystem initialized
[   18.378970] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 20
[   18.378982] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   18.378987] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   18.379009] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   18.379043] uhci_hcd 0000:00:1d.1: irq 20, io base 0x00001840
[   18.379140] usb usb2: configuration #1 chosen from 1 choice
[   18.379164] hub 2-0:1.0: USB hub found
[   18.379170] hub 2-0:1.0: 2 ports detected
[   18.379245] libata version 2.21 loaded.
[   18.418495] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   18.482397] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   18.482410] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   18.482414] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   18.482437] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   18.482472] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[   18.482571] usb usb3: configuration #1 chosen from 1 choice
[   18.482596] hub 3-0:1.0: USB hub found
[   18.482602] hub 3-0:1.0: 2 ports detected
[    3.864000] Marking TSC unstable due to: possible TSC halt in C2.
[    3.868000] Time: hpet clocksource has been installed.
[    3.868000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 17
[    3.868000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    3.868000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.868000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    3.868000] uhci_hcd 0000:00:1d.3: irq 17, io base 0x00001880
[    3.868000] usb usb4: configuration #1 chosen from 1 choice
[    3.868000] hub 4-0:1.0: USB hub found
[    3.868000] hub 4-0:1.0: 2 ports detected
[    3.972000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[    3.972000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    3.972000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.972000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    3.972000] ehci_hcd 0000:00:1d.7: debug port 1
[    3.972000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    3.972000] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xf0004000
[    4.004000] usb 2-1: new full speed USB device using uhci_hcd and address 2
[    4.004000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.004000] usb usb5: configuration #1 chosen from 1 choice
[    4.004000] hub 5-0:1.0: USB hub found
[    4.004000] hub 5-0:1.0: 8 ports detected
[    4.108000] ata_piix 0000:00:1f.1: version 2.11
[    4.108000] ACPI: PCI Interrupt 0000:00:1f.1[B] -> GSI 19 (level, low) -> IRQ 20
[    4.108000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    4.108000] scsi0 : ata_piix
[    4.108000] scsi1 : ata_piix
[    4.108000] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011810 irq 14
[    4.108000] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011818 irq 15
[    4.348000] usb 5-3: new high speed USB device using ehci_hcd and address 2
[    4.420000] ata1.00: ATAPI: Optiarc DVD RW AD-5530A, AX23, max UDMA/33
[    4.500000] Clocksource tsc unstable (delta = -228307783 ns)
[    4.592000] ata1.00: configured for UDMA/33
[    4.592000] ata2: port disabled. ignoring.
[    4.592000] scsi 0:0:0:0: CD-ROM            Optiarc  DVD RW AD-5530A  AX23 PQ: 0 ANSI: 5
[    4.592000] ata_piix 0000:00:1f.2: MAP [ P0 P2 XX XX ]
[    4.592000] ata_piix 0000:00:1f.2: invalid MAP value 0
[    4.616000] usb 5-3: configuration #1 chosen from 1 choice
[    4.748000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 20
[    4.748000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    4.748000] scsi2 : ata_piix
[    4.748000] scsi3 : ata_piix
[    4.748000] ata3: SATA max UDMA/133 cmd 0x000118d0 ctl 0x000118c6 bmdma 0x000118b0 irq 20
[    4.748000] ata4: SATA max UDMA/133 cmd 0x000118c8 ctl 0x000118c2 bmdma 0x000118b8 irq 20
[    4.912000] ata3.00: ATA-7: TOSHIBA MK4034GSX, AH401A, max UDMA/100
[    4.912000] ata3.00: 78140160 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    4.920000] ata3.00: configured for UDMA/100
[    5.084000] scsi 2:0:0:0: Direct-Access     ATA      TOSHIBA MK4034GS AH40 PQ: 0 ANSI: 5
[    5.084000] 8139cp 0000:06:05.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[    5.084000] 8139cp 0000:06:05.0: Try the "8139too" driver instead.
[    5.088000] 8139too Fast Ethernet driver 0.9.28
[    5.088000] ACPI: PCI Interrupt 0000:06:05.0[A] -> GSI 16 (level, low) -> IRQ 17
[    5.088000] eth0: RealTek RTL8139 at 0xe00ac000, 00:03:0d:57:71:b4, IRQ 17
[    5.088000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    5.120000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    5.120000] Uniform CD-ROM driver Revision: 3.20
[    5.120000] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    5.124000] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    5.124000] scsi 2:0:0:0: Attached scsi generic sg1 type 0
[    5.128000] sd 2:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[    5.128000] sd 2:0:0:0: [sda] Write Protect is off
[    5.128000] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.128000] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.128000] sd 2:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[    5.128000] sd 2:0:0:0: [sda] Write Protect is off
[    5.128000] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.128000] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.128000]  sda: sda1 sda2 < sda5 >
[    5.180000] sd 2:0:0:0: [sda] Attached SCSI disk
[    5.460000] Attempting manual resume
[    5.460000] swsusp: Resume From Partition 8:5
[    5.460000] PM: Checking swsusp image.
[    5.464000] PM: Resume from disk failed.
[    5.476000] EXT3-fs: INFO: recovery required on readonly filesystem.
[    5.476000] EXT3-fs: write access will be enabled during recovery.
[    7.348000] kjournald starting.  Commit interval 5 seconds
[    7.348000] EXT3-fs: recovery complete.
[    7.352000] EXT3-fs: mounted filesystem with ordered data mode.
[   14.580000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   15.636000] Linux agpgart interface v0.102 (c) Dave Jones
[   15.640000] agpgart: Detected an Intel 945GM Chipset.
[   15.640000] agpgart: Detected 7932K stolen memory.
[   15.656000] agpgart: AGP aperture is 256M @ 0xc0000000
[   16.240000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   16.244000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.452000] iTCO_vendor_support: vendor-support=0
[   16.640000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   16.644000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   16.644000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   16.652000] NET: Registered protocol family 17
[   16.908000] intel_rng: FWH not detected
[   17.040000] Real Time Clock Driver v1.12ac
[   17.504000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x200000
[   17.540000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[   18.092000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 21
[   18.092000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   18.472000] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   18.644000] ieee80211_init: failed to initialize WME (err=-17)
[   18.656000] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_unregister
[   18.656000] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_put
[   18.656000] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_get
[   18.656000] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_register
[   18.660000] wmaster0: Selected rate control algorithm 'simple'
[   18.812000] usbcore: registered new interface driver rt73usb
[   28.388000] lp: driver loaded but no devices found
[   28.460000] Adding 1485972k swap on /dev/sda5.  Priority:-1 extents:1 across:1485972k
[   28.704000] EXT3 FS on sda1, internal journal
[   29.336000] NET: Registered protocol family 10
[   29.336000] lo: Disabled Privacy Extensions
[   29.812000] ACPI: AC Adapter [AC0] (on-line)
[   29.856000] ACPI: Battery Slot [BAT0] (battery present)
[   29.872000] No dock devices found.
[   29.956000] input: Power Button (FF) as /class/input/input3
[   29.960000] ACPI: Power Button (FF) [PWRF]
[   30.004000] input: Lid Switch as /class/input/input4
[   30.008000] ACPI: Lid Switch [LID0]
[   30.052000] input: Power Button (CM) as /class/input/input5
[   30.056000] ACPI: Power Button (CM) [PWRB]
[   30.104000] input: Sleep Button (CM) as /class/input/input6
[   30.104000] ACPI: Sleep Button (CM) [SLPB]
[   30.208000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   30.208000] ACPI: Video Device [IGD] (multi-head: yes  rom: no  post: no)
[   31.888000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   33.216000] ppdev: user-space parallel port driver
[   33.632000] audit(1205336101.180:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5023 profile="/usr/sbin/cupsd"
[   33.680000] apm: BIOS not found.
[   35.484000] [drm] Initialized drm 1.1.0 20060810
[   35.548000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
[   35.552000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   35.732000] Failure registering capabilities with primary security module.
[   36.428000] Bluetooth: Core ver 2.11
[   36.428000] NET: Registered protocol family 31
[   36.428000] Bluetooth: HCI device and connection manager initialized
[   36.428000] Bluetooth: HCI socket layer initialized
[   36.444000] Bluetooth: L2CAP ver 2.8
[   36.444000] Bluetooth: L2CAP socket layer initialized
[   36.512000] Bluetooth: RFCOMM socket layer initialized
[   36.512000] Bluetooth: RFCOMM TTY layer initialized
[   36.512000] Bluetooth: RFCOMM ver 1.8
[   39.464000] eth0: no IPv6 routers present
[ 9394.900000] usb 1-2: new low speed USB device using uhci_hcd and address 2
[ 9395.064000] usb 1-2: configuration #1 chosen from 1 choice
[ 9395.408000] usbcore: registered new interface driver hiddev
[ 9395.420000] input: PS/2+USB Mouse as /class/input/input7
[ 9395.420000] input: USB HID v1.11 Mouse [PS/2+USB Mouse] on usb-0000:00:1d.0-2
[ 9395.420000] usbcore: registered new interface driver usbhid
[ 9395.420000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver

```

do i need to install the driver or something cuz i thought i had :/

---

### Post by azimuth on 2008-03-12
I still don't see a wireless adaptor. What do you get with the ifconfig and iwconfig commands? Do you know your make and model of wireless? Also, is it internal or external, usb or whatnot?

---

### Post by jrockpunk1 on 2008-03-13
> **azimuth said:**
> I still don't see a wireless adaptor. What do you get with the ifconfig and iwconfig commands? Do you know your make and model of wireless? Also, is it internal or external, usb or whatnot?

i have no idea about my wireless. i dont know what wireless card i have, or whether its external etc. the only thing i know is when i had XP on it, i got wireless working easily enough. and ifconfig shows:

```

eth0      Link encap:Ethernet  HWaddr 00:03:0D:57:71:B4  
          inet addr:82.47.83.162  Bcast:255.255.255.255  Mask:255.255.254.0
          inet6 addr: fe80::203:dff:fe57:71b4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21239 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2926 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5121324 (4.8 MB)  TX bytes:377353 (368.5 KB)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:19:DB:01:5C:AA  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wmaster0  Link encap:UNSPEC  HWaddr 00-19-DB-01-5C-AA-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

iwconfig shows:

```

jay@jay-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by burnclouds on 2008-03-13
What model is your laptop? and is your wireless a PCMCI card, USB or internal?

---

### Post by jrockpunk1 on 2008-03-13
my laptop is an E-System laptop, and if u mean do i have to plug a USB in to get wireless? then its internal. i just flip a switch on the side of the laptop to enable wireless (or i did to get it to work with XP)

---

### Post by mohaakilla51 on 2008-03-13
yes, that would make it internal...
pretty funny actually, I am having wireless connection issues, my ifconfig and iwconfig look EXACTLY like yours... I was told that I should manually set the access point for wlan0.

try
```

iwlist scan

```
and if it gives you an access point, do 
```

sudo iwconfig wlan0 ap xx:xx:xx:xx:xx:xx

```
and then maybe it will connect. at least, that was the help I was given. It didn't work for me, but might for you, who knows.

---

### Post by jrockpunk1 on 2008-03-13
it says no scan results for wlan0 :/ meh. anyone?

---

### Post by azimuth on 2008-03-13
Let's try to identify your wireless card. Knowing which card we are working with may make it easier to get it going. Use the command " lshw -C network"

---

### Post by jrockpunk1 on 2008-03-13
ok this is the output:

```

jay@jay-laptop:~$ sudo lshw -C network
[sudo] password for jay:
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:06:05.0
       logical name: eth0
       version: 10
       serial: 00:03:0d:57:71:b4
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=82.47.83.162 latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:19:db:01:5c:aa
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
jay@jay-laptop:~$ 

```

and thanks for helping me with this one

---

### Post by azimuth on 2008-03-13
In the configuration line it does not show a driver is loaded for wlan0. Did you manually add the mac address for your card?  Without a driver module, I wouldn't think It could talk to the card to get a mac. There is still nothing to identify the card or what chips it is using. We are way beyond my experience here. Hopefully someone with more experience will see our feeble attempts and jump in to help.  If they don't, we'll just keep slugging along.

---

### Post by jrockpunk1 on 2008-03-13
ok thanks. i have no idea what ive done or what ive installed etc. hopefully someone will be able to give an answer.

---

### Post by azimuth on 2008-03-13
Let's try to nail down what card we are working with. Try this command   > lspci -nn | grep Network

We are looking for something like this
> wayne@junk:~$ lspci -nn | grep Network
05:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11a/b/g [14e4:4312] (rev 01)
wayne@junk:~$

---

### Post by azimuth on 2008-03-13
I think I may have found what is going on. I am not sure if there is a fix. Look at the bug report [https://bugs.launchpad.net/ubuntu/+bug/144239](https://bugs.launchpad.net/ubuntu/+bug/144239)

Their examples of the dmesg output matches yours.

---

### Post by jrockpunk1 on 2008-03-13
ok well ive got it connected to a network, but it says a passphrase is required. i have no idea what the passphrase is. is there any way to find out?

---

### Post by azimuth on 2008-03-13
A passphrase is used as a substitute for the hexadecimal password. You may need some of the setup in this link [Manual Network Configuration]("http://ubuntuforums.org/showthread.php?t=571188")

---

### Post by jrockpunk1 on 2008-03-14
meh. i scroll down to WEP 64/128 bit hex password or whatever, and enter the network's password, and it still doesnt connect. i might have to wait until hardy heron is out and try upgrading, as someone says its gutsy. ill wait and see. for now i can just about deal with a wired connection.

---

### Post by jrockpunk1 on 2008-03-14
sorry for double post, but i think i might have enabled the driver or something. Ill go through all those commands again and display the output, and hopw it has changed:

lspci:

```

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
06:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

dmesg:

```

[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 502MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f7860
[    0.000000] Entering add_active_range(0, 0, 128656) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   128656
[    0.000000]   HighMem    128656 ->   128656
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   128656
[    0.000000] On node 0 totalpages: 128656
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 973 pages used for memmap
[    0.000000]   Normal zone: 123587 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F77B0 checksum 0
[    0.000000] ACPI: RSDP 000F77B0, 0014 (r0 DSGLTD)
[    0.000000] ACPI: RSDT 1F697E56, 0050 (r1 DSGLTD DSGVISTA  6040000  LTP        0)
[    0.000000] ACPI: FACP 1F69DCB8, 0074 (r1 INTEL  CALISTGA  6040000 LOHR       5A)
[    0.000000] ACPI: DSDT 1F699243, 4A75 (r1 UW____ FUW_____  6040000 INTL 20050624)
[    0.000000] ACPI: FACS 1F69EFC0, 0040
[    0.000000] ACPI: APIC 1F69DD2C, 0068 (r1 INTEL  CALISTGA  6040000 LOHR       5A)
[    0.000000] ACPI: HPET 1F69DD94, 0038 (r1 INTEL  CALISTGA  6040000 LOHR       5A)
[    0.000000] ACPI: MCFG 1F69DDCC, 003C (r1 INTEL  CALISTGA  6040000 LOHR       5A)
[    0.000000] ACPI: APIC 1F69DE08, 005A (r1 DSGLTD DSGVISTA  6040000  LTP        0)
[    0.000000] ACPI: SLIC 1F69DE62, 0176 (r1 DSGLTD DSGVISTA  6040000  LTP        0)
[    0.000000] ACPI: BOOT 1F69DFD8, 0028 (r1 MSTEST TESTONLY  6040000  LTP        1)
[    0.000000] ACPI: SSDT 1F698BF4, 064F (r1 SataRe  SataPri     1000 INTL 20050624)
[    0.000000] ACPI: SSDT 1F698562, 0692 (r1 SataRe  SataSec     1000 INTL 20050624)
[    0.000000] ACPI: SSDT 1F69839C, 01C6 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[    0.000000] ACPI: SSDT 1F697EA6, 04F6 (r1  PmRef    CpuPm     3000 INTL 20050624)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:14 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
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
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:c0000000)
[    0.000000] Built 1 zonelists.  Total pages: 127651
[    0.000000] Kernel command line: root=UUID=1ac7bca8-cd76-48fc-b59c-837a1ff50cd9 ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 1600.111 MHz processor.
[   13.628396] Console: colour VGA+ 80x25
[   13.628555] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   13.628759] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   13.641382] Memory: 498964k/514624k available (1929k kernel code, 15096k reserved, 876k data, 348k init, 0k highmem)
[   13.641392] virtual kernel memory layout:
[   13.641393]     fixmap  : 0xfffa8000 - 0xfffff000   ( 348 kB)
[   13.641395]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   13.641396]     vmalloc : 0xe0000000 - 0xff7fe000   ( 503 MB)
[   13.641398]     lowmem  : 0xc0000000 - 0xdf690000   ( 502 MB)
[   13.641399]       .init : 0xc03c0000 - 0xc0417000   ( 348 kB)
[   13.641400]       .data : 0xc02e2655 - 0xc03bda04   ( 876 kB)
[   13.641402]       .text : 0xc0100000 - 0xc02e2655   (1929 kB)
[   13.641405] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   13.641447] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   13.641598] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   13.641603] hpet0: 3 64-bit timers, 14318180 Hz
[   13.722497] Calibrating delay using timer specific routine.. 3203.59 BogoMIPS (lpj=6407198)
[   13.722518] Security Framework v1.0.0 initialized
[   13.722525] SELinux:  Disabled at boot.
[   13.722531] Mount-cache hash table entries: 512
[   13.722624] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 0000c109 00000000 00000000
[   13.722633] monitor/mwait feature present.
[   13.722635] using mwait in idle threads.
[   13.722639] CPU: L1 I cache: 32K, L1 D cache: 32K
[   13.722641] CPU: L2 cache: 1024K
[   13.722644] CPU: After all inits, caps: afe9fbff 00100000 00000000 00002940 0000c109 00000000 00000000
[   13.722651] Compat vDSO mapped to ffffe000.
[   13.722662] CPU: Intel(R) Celeron(R) M CPU        420  @ 1.60GHz stepping 08
[   13.722668] Checking 'hlt' instruction... OK.
[   13.738988] Early unpacking initramfs... done
[   14.094211] ACPI: Core revision 20070126
[   14.094273] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   14.124993] ENABLING IO-APIC IRQs
[   14.125194] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   14.269728] Booting paravirtualized kernel on bare hardware
[   14.269817] Time: 15:13:24  Date: 02/14/108
[   14.269837] NET: Registered protocol family 16
[   14.269911] EISA bus registered
[   14.269916] ACPI: bus type pci registered
[   14.308722] PCI: PCI BIOS revision 2.10 entry at 0xfd843, last bus=6
[   14.308725] PCI: Using configuration type 1
[   14.308727] Setting up standard PCI resources
[   14.312611] ACPI: EC: Look up EC in DSDT
[   14.313206] ACPI: EC: GPE=0x19, ports=0x66, 0x62
[   14.314560] ACPI: System BIOS is requesting _OSI(Linux)
[   14.314563] ACPI: Please test with "acpi_osi=!Linux"
[   14.314565] Please send dmidecode to linux-acpi@vger.kernel.org
[   14.315125] ACPI: Interpreter enabled
[   14.315128] ACPI: (supports S0 S3 S4 S5)
[   14.315143] ACPI: Using IOAPIC for interrupt routing
[   14.320796] ACPI: EC: GPE=0x19, ports=0x66, 0x62
[   14.320848] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   14.320858] PCI: Probing PCI hardware (bus 00)
[   14.321595] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   14.321600] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[   14.322235] PCI: Transparent bridge - 0000:00:1e.0
[   14.322309] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   14.322632] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[   14.322768] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[   14.322902] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[   14.323052] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   14.325785] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   14.325888] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[   14.325988] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 *3 4 5 6 7 10 12 14 15)
[   14.326087] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   14.326185] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[   14.326284] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[   14.326383] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[   14.326482] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[   14.326582] Linux Plug and Play Support v0.97 (c) Adam Belay
[   14.326595] pnp: PnP ACPI init
[   14.326601] ACPI: bus type pnp registered
[   14.328353] pnp: PnP ACPI: found 11 devices
[   14.328356] ACPI: ACPI bus type pnp unregistered
[   14.328360] PnPBIOS: Disabled by ACPI PNP
[   14.328403] PCI: Using ACPI for IRQ routing
[   14.328407] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   14.343294] NET: Registered protocol family 8
[   14.343297] NET: Registered protocol family 20
[   14.343349] pnp: 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[   14.343353] pnp: 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
[   14.343357] pnp: 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
[   14.343360] pnp: 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
[   14.343367] pnp: 00:04: iomem range 0xfed00000-0xfed003ff could not be reserved
[   14.343374] pnp: 00:07: ioport range 0x6a0-0x6af has been reserved
[   14.343376] pnp: 00:07: ioport range 0x6b0-0x6ff has been reserved
[   14.345543] Time: tsc clocksource has been installed.
[   14.345561] Switched to high resolution mode on CPU 0
[   14.373606] PCI: Bridge: 0000:00:1c.0
[   14.373609]   IO window: f000-ffff
[   14.373616]   MEM window: fac00000-febfffff
[   14.373621]   PREFETCH window: disabled.
[   14.373627] PCI: Bridge: 0000:00:1c.1
[   14.373628]   IO window: disabled.
[   14.373634]   MEM window: disabled.
[   14.373638]   PREFETCH window: disabled.
[   14.373644] PCI: Bridge: 0000:00:1c.2
[   14.373645]   IO window: disabled.
[   14.373651]   MEM window: f7000000-f70fffff
[   14.373656]   PREFETCH window: disabled.
[   14.373662] PCI: Bridge: 0000:00:1e.0
[   14.373665]   IO window: 2000-2fff
[   14.373671]   MEM window: f0200000-f02fffff
[   14.373676]   PREFETCH window: disabled.
[   14.373703] PCI: Enabling device 0000:00:1c.0 (0000 -> 0003)
[   14.373710] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 16
[   14.373719] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   14.373742] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 17
[   14.373750] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   14.373772] PCI: Enabling device 0000:00:1c.2 (0000 -> 0002)
[   14.373776] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[   14.373784] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   14.373798] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   14.373810] NET: Registered protocol family 2
[   14.549223] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   14.549258] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   14.549359] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[   14.549416] TCP: Hash tables configured (established 16384 bind 16384)
[   14.549419] TCP reno registered
[   14.561298] checking if image is initramfs... it is
[   15.266153] Freeing initrd memory: 7096k freed
[   15.266285] Simple Boot Flag at 0x35 set to 0x1
[   15.266604] audit: initializing netlink socket (disabled)
[   15.266618] audit(1205507604.488:1): initialized
[   15.268363] VFS: Disk quotas dquot_6.5.1
[   15.268376] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   15.268467] io scheduler noop registered
[   15.268469] io scheduler anticipatory registered
[   15.268471] io scheduler deadline registered
[   15.268487] io scheduler cfq registered (default)
[   15.268500] Boot video device is 0000:00:02.0
[   15.268657] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   15.268713] assign_interrupt_mode Found MSI capability
[   15.268717] Allocate Port Service[0000:00:1c.0:pcie00]
[   15.268746] Allocate Port Service[0000:00:1c.0:pcie02]
[   15.268840] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   15.268896] assign_interrupt_mode Found MSI capability
[   15.268898] Allocate Port Service[0000:00:1c.1:pcie00]
[   15.268926] Allocate Port Service[0000:00:1c.1:pcie02]
[   15.269016] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   15.269072] assign_interrupt_mode Found MSI capability
[   15.269074] Allocate Port Service[0000:00:1c.2:pcie00]
[   15.269105] Allocate Port Service[0000:00:1c.2:pcie02]
[   15.269249] isapnp: Scanning for PnP cards...
[   15.623108] isapnp: No Plug & Play device found
[   15.645669] hpet_resources: 0xfed00000 is busy
[   15.645693] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   15.646776] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   15.646957] input: Macintosh mouse button emulation as /class/input/input0
[   15.647027] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   15.650097] i8042.c: Detected active multiplexing controller, rev 1.1.
[   15.651259] serio: i8042 KBD port at 0x60,0x64 irq 1
[   15.651264] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   15.651267] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   15.651270] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   15.651272] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   15.651451] mice: PS/2 mouse device common for all mice
[   15.651647] EISA: Probing bus 0 at eisa.0
[   15.651655] Cannot allocate resource for EISA slot 1
[   15.651657] Cannot allocate resource for EISA slot 2
[   15.651683] EISA: Detected 0 cards.
[   15.651779] TCP cubic registered
[   15.651792] NET: Registered protocol family 1
[   15.651816] Using IPI Shortcut mode
[   15.651972]   Magic number: 0:790:234
[   15.652016]   hash matches device ttyv4
[   15.652337] Freeing unused kernel memory: 348k freed
[   15.763893] input: AT Translated Set 2 keyboard as /class/input/input1
[   16.850268] AppArmor: AppArmor initialized<5>audit(1205507606.076:2):  type=1505 info="AppArmor initialized" pid=1245
[   16.858238] fuse init (API version 7.8)
[   16.863420] Failure registering capabilities with primary security module.
[   16.878722] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   16.878729] ACPI: Processor [CPU0] (supports 8 throttling states)
[   16.879978] ACPI: Thermal Zone [THRM] (59 C)
[   17.338630] usbcore: registered new interface driver usbfs
[   17.338654] usbcore: registered new interface driver hub
[   17.338676] usbcore: registered new device driver usb
[   17.339420] USB Universal Host Controller Interface driver v3.0
[   17.339485] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[   17.339496] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   17.339500] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   17.339704] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   17.339738] uhci_hcd 0000:00:1d.0: irq 19, io base 0x00001820
[   17.339852] usb usb1: configuration #1 chosen from 1 choice
[   17.339876] hub 1-0:1.0: USB hub found
[   17.339882] hub 1-0:1.0: 2 ports detected
[   17.415417] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   17.440860] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 20
[   17.440873] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   17.440877] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   17.440900] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   17.440932] uhci_hcd 0000:00:1d.1: irq 20, io base 0x00001840
[   17.441029] usb usb2: configuration #1 chosen from 1 choice
[   17.441053] hub 2-0:1.0: USB hub found
[   17.441058] hub 2-0:1.0: 2 ports detected
[   17.464146] SCSI subsystem initialized
[   17.469615] libata version 2.21 loaded.
[   17.544715] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   17.544728] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   17.544732] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   17.544755] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   17.544790] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[   17.544892] usb usb3: configuration #1 chosen from 1 choice
[   17.544918] hub 3-0:1.0: USB hub found
[   17.544923] hub 3-0:1.0: 2 ports detected
[    3.852000] Marking TSC unstable due to: possible TSC halt in C2.
[    3.856000] Time: hpet clocksource has been installed.
[    3.880000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 17
[    3.880000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    3.880000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.880000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    3.880000] uhci_hcd 0000:00:1d.3: irq 17, io base 0x00001880
[    3.880000] usb usb4: configuration #1 chosen from 1 choice
[    3.880000] hub 4-0:1.0: USB hub found
[    3.880000] hub 4-0:1.0: 2 ports detected
[    3.984000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[    3.984000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    3.984000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.984000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    3.984000] ehci_hcd 0000:00:1d.7: debug port 1
[    3.984000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    3.984000] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xf0004000
[    4.000000] Clocksource tsc unstable (delta = -80160092 ns)
[    4.016000] usb 2-1: new full speed USB device using uhci_hcd and address 2
[    4.016000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.016000] usb usb5: configuration #1 chosen from 1 choice
[    4.016000] hub 5-0:1.0: USB hub found
[    4.016000] hub 5-0:1.0: 8 ports detected
[    4.120000] 8139cp 0000:06:05.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[    4.120000] 8139cp 0000:06:05.0: Try the "8139too" driver instead.
[    4.120000] 8139too Fast Ethernet driver 0.9.28
[    4.120000] ACPI: PCI Interrupt 0000:06:05.0[A] -> GSI 16 (level, low) -> IRQ 17
[    4.120000] eth0: RealTek RTL8139 at 0xe006e000, 00:03:0d:57:71:b4, IRQ 17
[    4.120000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    4.124000] ata_piix 0000:00:1f.1: version 2.11
[    4.124000] ACPI: PCI Interrupt 0000:00:1f.1[B] -> GSI 19 (level, low) -> IRQ 20
[    4.124000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    4.124000] scsi0 : ata_piix
[    4.124000] scsi1 : ata_piix
[    4.124000] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011810 irq 14
[    4.124000] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011818 irq 15
[    4.360000] usb 5-3: new high speed USB device using ehci_hcd and address 2
[    4.444000] ata1.00: ATAPI: Optiarc DVD RW AD-5530A, AX23, max UDMA/33
[    4.616000] ata1.00: configured for UDMA/33
[    4.616000] ata2: port disabled. ignoring.
[    4.616000] scsi 0:0:0:0: CD-ROM            Optiarc  DVD RW AD-5530A  AX23 PQ: 0 ANSI: 5
[    4.616000] ata_piix 0000:00:1f.2: MAP [ P0 P2 XX XX ]
[    4.616000] ata_piix 0000:00:1f.2: invalid MAP value 0
[    4.628000] usb 5-3: configuration #1 chosen from 1 choice
[    4.772000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 20
[    4.772000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    4.772000] scsi2 : ata_piix
[    4.772000] scsi3 : ata_piix
[    4.772000] ata3: SATA max UDMA/133 cmd 0x000118d0 ctl 0x000118c6 bmdma 0x000118b0 irq 20
[    4.772000] ata4: SATA max UDMA/133 cmd 0x000118c8 ctl 0x000118c2 bmdma 0x000118b8 irq 20
[    4.936000] ata3.00: ATA-7: TOSHIBA MK4034GSX, AH401A, max UDMA/100
[    4.936000] ata3.00: 78140160 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    4.944000] ata3.00: configured for UDMA/100
[    5.108000] scsi 2:0:0:0: Direct-Access     ATA      TOSHIBA MK4034GS AH40 PQ: 0 ANSI: 5
[    5.120000] sd 2:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[    5.120000] sd 2:0:0:0: [sda] Write Protect is off
[    5.120000] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.120000] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.120000] sd 2:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[    5.120000] sd 2:0:0:0: [sda] Write Protect is off
[    5.120000] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.120000] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.120000]  sda:sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    5.144000] Uniform CD-ROM driver Revision: 3.20
[    5.144000] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    5.148000]  sda1 sda2 < sda5 >
[    5.168000] sd 2:0:0:0: [sda] Attached SCSI disk
[    5.172000] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    5.172000] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    5.380000] Attempting manual resume
[    5.380000] swsusp: Resume From Partition 8:5
[    5.380000] PM: Checking swsusp image.
[    5.380000] PM: Resume from disk failed.
[    5.392000] EXT3-fs: INFO: recovery required on readonly filesystem.
[    5.392000] EXT3-fs: write access will be enabled during recovery.
[   11.288000] kjournald starting.  Commit interval 5 seconds
[   11.288000] EXT3-fs: recovery complete.
[   11.288000] EXT3-fs: mounted filesystem with ordered data mode.
[   18.592000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   19.664000] Linux agpgart interface v0.102 (c) Dave Jones
[   19.672000] agpgart: Detected an Intel 945GM Chipset.
[   19.672000] agpgart: Detected 7932K stolen memory.
[   19.688000] agpgart: AGP aperture is 256M @ 0xc0000000
[   19.940000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   20.056000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   20.232000] NET: Registered protocol family 17
[   20.760000] iTCO_vendor_support: vendor-support=0
[   20.864000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   20.876000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   20.876000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   21.264000] intel_rng: FWH not detected
[   21.436000] Real Time Clock Driver v1.12ac
[   21.868000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x200000
[   21.896000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[   22.424000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 21
[   22.424000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   22.780000] ieee80211_init: failed to initialize WME (err=-17)
[   22.792000] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_unregister
[   22.792000] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_put
[   22.792000] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_get
[   22.792000] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_register
[   22.796000] wmaster0: Selected rate control algorithm 'simple'
[   22.804000] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   22.904000] usbcore: registered new interface driver rt73usb
[   31.600000] lp: driver loaded but no devices found
[   31.672000] Adding 1485972k swap on /dev/sda5.  Priority:-1 extents:1 across:1485972k
[   31.832000] EXT3 FS on sda1, internal journal
[   32.416000] NET: Registered protocol family 10
[   32.416000] lo: Disabled Privacy Extensions
[   32.936000] ACPI: AC Adapter [AC0] (on-line)
[   32.980000] ACPI: Battery Slot [BAT0] (battery present)
[   32.996000] No dock devices found.
[   33.080000] input: Power Button (FF) as /class/input/input3
[   33.084000] ACPI: Power Button (FF) [PWRF]
[   33.128000] input: Lid Switch as /class/input/input4
[   33.132000] ACPI: Lid Switch [LID0]
[   33.176000] input: Power Button (CM) as /class/input/input5
[   33.180000] ACPI: Power Button (CM) [PWRB]
[   33.228000] input: Sleep Button (CM) as /class/input/input6
[   33.232000] ACPI: Sleep Button (CM) [SLPB]
[   33.336000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   33.336000] ACPI: Video Device [IGD] (multi-head: yes  rom: no  post: no)
[   34.944000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   36.184000] ppdev: user-space parallel port driver
[   36.612000] audit(1205507642.493:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5031 profile="/usr/sbin/cupsd"
[   36.660000] apm: BIOS not found.
[   38.320000] [drm] Initialized drm 1.1.0 20060810
[   38.344000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
[   38.348000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   38.548000] Failure registering capabilities with primary security module.
[   39.208000] Bluetooth: Core ver 2.11
[   39.208000] NET: Registered protocol family 31
[   39.208000] Bluetooth: HCI device and connection manager initialized
[   39.208000] Bluetooth: HCI socket layer initialized
[   39.220000] Bluetooth: L2CAP ver 2.8
[   39.220000] Bluetooth: L2CAP socket layer initialized
[   39.284000] Bluetooth: RFCOMM socket layer initialized
[   39.284000] Bluetooth: RFCOMM TTY layer initialized
[   39.284000] Bluetooth: RFCOMM ver 1.8
[   43.104000] eth0: no IPv6 routers present
[  106.672000] usb 1-2: new low speed USB device using uhci_hcd and address 2
[  106.836000] usb 1-2: configuration #1 chosen from 1 choice
[  107.324000] usbcore: registered new interface driver hiddev
[  107.340000] input: PS/2+USB Mouse as /class/input/input7
[  107.340000] input: USB HID v1.11 Mouse [PS/2+USB Mouse] on usb-0000:00:1d.0-2
[  107.340000] usbcore: registered new interface driver usbhid
[  107.340000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[ 1536.804000] ieee80211_crypt: registered algorithm 'NULL'
[ 1536.808000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[ 1536.808000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[ 1536.836000] bcm43xx driver
[ 2409.968000] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

ifconfig:

```

eth0      Link encap:Ethernet  HWaddr 00:03:0D:57:71:B4  
          inet addr:82.47.83.162  Bcast:255.255.255.255  Mask:255.255.254.0
          inet6 addr: fe80::203:dff:fe57:71b4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:121523 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11555 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:28181445 (26.8 MB)  TX bytes:1158767 (1.1 MB)
          Interrupt:17 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:19:DB:01:5C:AA  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wmaster0  Link encap:UNSPEC  HWaddr 00-19-DB-01-5C-AA-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 

```

iwconfig:

```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

lshw -C network:

```

jay@jay-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:06:05.0
       logical name: eth0
       version: 10
       serial: 00:03:0d:57:71:b4
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=82.47.83.162 latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:19:db:01:5c:aa
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

```

any changes?

---

### Post by jrockpunk1 on 2008-03-14
soory for TRIPLE post, ut theres another problem. i finally got wireless working, and i could go on the internet. however, i restarted it, and it wouldnt connect. so i went to system>admin>network, and there want even an option for wireless! just wired and modem. whats gone wrong? it was all working fine and then capoof! gone!

---

### Post by azimuth on 2008-03-14
There is no Network Controller listed on your pci buss. Dmesg shows an error when the wireless is being setup
> **jrockpunk1 said:**
> 
[   22.780000] ieee80211_init: failed to initialize WME (err=-17)
[   22.792000] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_unregister
[   22.792000] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_put
[   22.792000] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_get
[   22.792000] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_register


There is no driver for the wireless in the hardware list (lshw -C network)

All indications are that your hardware has not been picked up by the kernal. If we knew exactly what wireless card your laptop used, we maybe could force a driver for it with the modprobe command. Most pc manufacturers have detailed lists of what is in each computer they sell. You can usually enter your model and serial number in the support section of their websites to get a build list for your individual computer. 

One option is a usb wireless dongle that is known to work on linux. These can be as cheap as $20. Beyond these two, I am out of ideas.

---

### Post by jimmyridge on 2008-03-14
jrock i saw this in your dmesg output

[   18.812000] usbcore: registered new interface driver rt73usb

is that a usb wifi you put in? if not its possible the manufacturer stuck that card in there on the usb bus ? anyway i found this googling for that device

[http://www.aircrack-ng.org/doku.php?id=rt73](http://www.aircrack-ng.org/doku.php?id=rt73)

dunno good luck if that is the internal card you have your in luck realtek makes some great wifi cards most support injection ;)

---

### Post by azimuth on 2008-03-14
jimmyridge, I missed that completely. Always helps to have more eyes watching. It's not usual to wire a usb internally. Glad you saw it. We have more to work with now.

---

### Post by azimuth on 2008-03-14
Jay, The first thing we need to check is a lsusb and see if we get more info on the Ralink card. It will make a difference whether your wifi switch is on or off.

ps. besides "lsusb" you might also try "lshw -C usb"

---

### Post by jrockpunk1 on 2008-03-14
ok ill try all that tomorrow. but know that those outputs of dmesg etc were before it bost, and there was no option for wireless. ill print dmesg again tomorrow.

---

### Post by jrockpunk1 on 2008-03-14
that is freaky. its working now. i logged on and i was connected to the network :D thanks everyone for your help, especially you azimuth.

---

### Post by azimuth on 2008-03-15
Sorry I was so long getting back here, my wireless broadband went down in a storm and has just come back after 24 hrs. Glad to hear yours is working. While it is working is a good time to check the lsusb and lshw -C network to see what they say when all is well.

ps ...If you are satisfied that your problem is solved, please mark the thread solved.

---

### Post by jrockpunk1 on 2008-03-15
ok ill do those commands tomorrow. and yeah its solved, but sometimes it doesnt work and i have to log out and in again. I'll mark it as solved, and get backto you with those commands :D thanks again.
by the way, the way i got it working, was when i did the ifconfig command, i noticed the line:

```

wlan0     Link encap:Ethernet  HWaddr 00:19:DB:01:5C:AA  

```

i remembered someone saying to do:

```

sudo wlan0 ap xx:xx:xx:xx:xx:xx

```

or something, so i just added the "00:19:DB:01:5C:AA" in, and enabled roaming mode. i then entered my network name and password and it connected :D i hope this helps other people as well.

---

