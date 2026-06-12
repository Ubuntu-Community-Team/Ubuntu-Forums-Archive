---
title: "No more wifi list on network manager"
date: 2008-08-24
forum: Networking &amp; Wireless
---

### Post by Despina73 on 2008-08-24
Hello ,

i have a curius stupid problem.

yesterday, everything was ok with my wifi ( connection, network manager)

Today, i boot and...nothing. No wifi listing on network manager, and not wifi at all for me.


What is this problem?

thanks

---

### Post by geezerone on 2008-08-24
What device are you using and what is the output when you type:

dmesg

iwconfig

Try typing *sudo /etc/init.d/networking restart* and what is output?

---

### Post by Despina73 on 2008-08-24
thank you !
here is the dmesg:

[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:c0000000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000dc000
[    0.000000] swsusp: Registered nosave memory region: 00000000000dc000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 127731
[    0.000000] Kernel command line: root=UUID=b6626428-2783-4a3d-941f-e837a8c53adc ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 1695.822 MHz processor.
[    7.246553] Console: colour VGA+ 80x25
[    7.246558] console [tty0] enabled
[    7.246759] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    7.247002] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    7.259063] Memory: 498436k/514944k available (2177k kernel code, 15888k reserved, 1006k data, 368k init, 0k highmem)
[    7.259071] virtual kernel memory layout:
[    7.259072]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[    7.259074]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    7.259075]     vmalloc : 0xe0000000 - 0xff7fe000   ( 503 MB)
[    7.259076]     lowmem  : 0xc0000000 - 0xdf6e0000   ( 502 MB)
[    7.259077]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[    7.259079]       .data : 0xc0320504 - 0xc041bdc4   (1006 kB)
[    7.259080]       .text : 0xc0100000 - 0xc0320504   (2177 kB)
[    7.259083] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    7.259127] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[    7.339044] Calibrating delay using timer specific routine.. 3395.42 BogoMIPS (lpj=6790859)
[    7.339070] Security Framework initialized
[    7.339081] SELinux:  Disabled at boot.
[    7.339096] AppArmor: AppArmor initialized
[    7.339101] Failure registering capabilities with primary security module.
[    7.339110] Mount-cache hash table entries: 512
[    7.339250] Initializing cgroup subsys ns
[    7.339256] Initializing cgroup subsys cpuacct
[    7.339270] CPU: After generic identify, caps: afe9fbff 00000000 00000000 00000000 00000180 00000000 00000000 00000000
[    7.339281] CPU: L1 I cache: 32K, L1 D cache: 32K
[    7.339284] CPU: L2 cache: 2048K
[    7.339287] CPU: After all inits, caps: afe9fbff 00000000 00000000 00042040 00000180 00000000 00000000 00000000
[    7.339296] Compat vDSO mapped to ffffe000.
[    7.339311] Checking 'hlt' instruction... OK.
[    7.355443] SMP alternatives: switching to UP code
[    7.357408] Freeing SMP alternatives: 11k freed
[    7.357521] Early unpacking initramfs... done
[    7.715167] ACPI: Core revision 20070126
[    7.715241] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    7.741159] CPU0: Intel(R) Pentium(R) M processor 1.70GHz stepping 08
[    7.741178] Total of 1 processors activated (3395.42 BogoMIPS).
[    7.741367] ENABLING IO-APIC IRQs
[    7.741564] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    7.886349] Brought up 1 CPUs
[    7.886378] CPU0 attaching sched-domain:
[    7.886381]  domain 0: span 01
[    7.886383]   groups: 01
[    7.886554] net_namespace: 64 bytes
[    7.886565] Booting paravirtualized kernel on bare hardware
[    7.887028] Time:  8:26:51  Date: 08/24/08
[    7.887056] NET: Registered protocol family 16
[    7.887251] EISA bus registered
[    7.887278] ACPI: bus type pci registered
[    7.887826] PCI: PCI BIOS revision 2.10 entry at 0xfd79e, last bus=7
[    7.887828] PCI: Using configuration type 1
[    7.887843] Setting up standard PCI resources
[    7.897589] ACPI: EC: Look up EC in DSDT
[    7.899825] ACPI: Interpreter enabled
[    7.899828] ACPI: (supports S0 S3 S4 S5)
[    7.899841] ACPI: Using IOAPIC for interrupt routing
[    7.903518] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    7.907747] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    7.907750] ACPI: EC: driver started in interrupt mode
[    7.907790] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    7.908494] Force enabled HPET at base address 0xfed00000
[    7.908500] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    7.908504] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[    7.909349] PCI: Transparent bridge - 0000:00:1e.0
[    7.909433] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    7.909768] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    7.909911] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    7.921123] ACPI: PCI Interrupt Link [LNKA] (IRQs *10 11)
[    7.921217] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 *11)
[    7.921308] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 *11)
[    7.921399] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 *11)
[    7.921490] ACPI: PCI Interrupt Link [LNKE] (IRQs *10 11)
[    7.921581] ACPI: PCI Interrupt Link [LNKF] (IRQs *10 11)
[    7.921672] ACPI: PCI Interrupt Link [LNKG] (IRQs 11) *10
[    7.921762] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 *11)
[    7.921878] Linux Plug and Play Support v0.97 (c) Adam Belay
[    7.921908] pnp: PnP ACPI init
[    7.921915] ACPI: bus type pnp registered
[    7.925500] pnp: PnP ACPI: found 9 devices
[    7.925502] ACPI: ACPI bus type pnp unregistered
[    7.925507] PnPBIOS: Disabled by ACPI PNP
[    7.925714] PCI: Using ACPI for IRQ routing
[    7.925717] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    7.962210] NET: Registered protocol family 8
[    7.962212] NET: Registered protocol family 20
[    7.962371] hpet clockevent registered
[    7.962377] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    7.962381] hpet0: 3 64-bit timers, 14318180 Hz
[    7.963420] AppArmor: AppArmor Filesystem Enabled
[    7.966198] Time: tsc clocksource has been installed.
[    7.974221] system 00:04: ioport range 0x800-0x80f has been reserved
[    7.974224] system 00:04: ioport range 0x1000-0x107f has been reserved
[    7.974230] system 00:04: ioport range 0x1180-0x11bf has been reserved
[    7.974233] system 00:04: ioport range 0x1200-0x1200 has been reserved
[    7.974235] system 00:04: ioport range 0x1204-0x1204 has been reserved
[    7.974239] system 00:04: iomem range 0xe0000000-0xefffffff could not be reserved
[    7.974242] system 00:04: iomem range 0xf0000000-0xf0003fff could not be reserved
[    7.974245] system 00:04: iomem range 0xf0004000-0xf0004fff could not be reserved
[    7.974248] system 00:04: iomem range 0xf0005000-0xf0005fff could not be reserved
[    7.974252] system 00:04: iomem range 0xf0008000-0xf000bfff could not be reserved
[    7.974255] system 00:04: iomem range 0xfed20000-0xfed8ffff could not be reserved
[    8.004617] PCI: Bridge: 0000:00:1c.0
[    8.004621]   IO window: 2000-2fff
[    8.004627]   MEM window: b4000000-b7ffffff
[    8.004631]   PREFETCH window: d0000000-d3ffffff
[    8.004641] PCI: Bus 7, cardbus bridge: 0000:06:09.0
[    8.004643]   IO window: 00003400-000034ff
[    8.004648]   IO window: 00003800-000038ff
[    8.004653]   PREFETCH window: 34000000-37ffffff
[    8.004659]   MEM window: 38000000-3bffffff
[    8.004664] PCI: Bridge: 0000:00:1e.0
[    8.004667]   IO window: 3000-3fff
[    8.004672]   MEM window: b8000000-b80fffff
[    8.004677]   PREFETCH window: disabled.
[    8.004709] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 16
[    8.004716] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    8.004730] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    8.004748] ACPI: PCI Interrupt 0000:06:09.0[A] -> GSI 22 (level, low) -> IRQ 17
[    8.004761] NET: Registered protocol family 2
[    8.042158] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    8.042354] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    8.042456] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    8.042558] TCP: Hash tables configured (established 16384 bind 16384)
[    8.042560] TCP reno registered
[    8.054190] checking if image is initramfs... it is
[    8.465528] Switched to high resolution mode on CPU 0
[    8.757935] Freeing initrd memory: 7312k freed
[    8.758182] Simple Boot Flag at 0x37 set to 0x1
[    8.758629] audit: initializing netlink socket (disabled)
[    8.758648] audit(1219566411.376:1): initialized
[    8.760748] VFS: Disk quotas dquot_6.5.1
[    8.760831] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    8.760989] io scheduler noop registered
[    8.760992] io scheduler anticipatory registered
[    8.760994] io scheduler deadline registered
[    8.761005] io scheduler cfq registered (default)
[    8.761021] Boot video device is 0000:00:02.0
[    8.761361] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    8.761417] assign_interrupt_mode Found MSI capability
[    8.761468] Allocate Port Service[0000:00:1c.0:pcie00]
[    8.761512] Allocate Port Service[0000:00:1c.0:pcie02]
[    8.761773] isapnp: Scanning for PnP cards...
[    9.115568] isapnp: No Plug & Play device found
[    9.142853] Real Time Clock Driver v1.12ac
[    9.142976] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    9.144192] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    9.144266] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    9.144381] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    9.147304] i8042.c: Detected active multiplexing controller, rev 1.1.
[    9.148663] serio: i8042 KBD port at 0x60,0x64 irq 1
[    9.148668] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    9.148670] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    9.148673] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    9.148675] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    9.160529] mice: PS/2 mouse device common for all mice
[    9.160642] EISA: Probing bus 0 at eisa.0
[    9.160649] Cannot allocate resource for EISA slot 1
[    9.160652] Cannot allocate resource for EISA slot 2
[    9.160654] Cannot allocate resource for EISA slot 3
[    9.160675] EISA: Detected 0 cards.
[    9.160679] cpuidle: using governor ladder
[    9.160683] cpuidle: using governor menu
[    9.160789] NET: Registered protocol family 1
[    9.160819] Using IPI No-Shortcut mode
[    9.160857] registered taskstats version 1
[    9.160984]   Magic number: 4:38:423
[    9.161097] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    9.161100] EDD information not available.
[    9.161339] Freeing unused kernel memory: 368k freed
[    9.180467] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   10.372267] fuse init (API version 7.9)
[   10.393358] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   10.393364] ACPI: Processor [CPU0] (supports 8 throttling states)
[   10.393378] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
[   10.397687] ACPI: Thermal Zone [TZS0] (41 C)
[   10.401083] ACPI: Thermal Zone [TZS1] (25 C)
[   10.961948] usbcore: registered new interface driver usbfs
[   10.961976] usbcore: registered new interface driver hub
[   10.969877] usbcore: registered new device driver usb
[   10.982050] USB Universal Host Controller Interface driver v3.0
[   10.982117] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 18
[   10.982130] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   10.982135] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   10.982545] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   10.982579] uhci_hcd 0000:00:1d.0: irq 18, io base 0x00001820
[   10.982719] usb usb1: configuration #1 chosen from 1 choice
[   10.982744] hub 1-0:1.0: USB hub found
[   10.982749] hub 1-0:1.0: 2 ports detected
[   11.085811] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 16
[   11.085827] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   11.085832] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   11.085855] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   11.085890] uhci_hcd 0000:00:1d.1: irq 16, io base 0x00001840
[   11.086007] usb usb2: configuration #1 chosen from 1 choice
[   11.086031] hub 2-0:1.0: USB hub found
[   11.086037] hub 2-0:1.0: 2 ports detected
[   11.089887] SCSI subsystem initialized
[   11.165862] libata version 3.00 loaded.
[   11.189663] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 19
[   11.189678] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   11.189683] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   11.189704] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   11.189738] uhci_hcd 0000:00:1d.2: irq 19, io base 0x00001860
[   11.189853] usb usb3: configuration #1 chosen from 1 choice
[   11.189877] hub 3-0:1.0: USB hub found
[   11.189883] hub 3-0:1.0: 2 ports detected
[   11.293524] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 20
[   11.293540] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   11.293545] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   11.293569] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   11.293603] uhci_hcd 0000:00:1d.3: irq 20, io base 0x00001880
[   11.293721] usb usb4: configuration #1 chosen from 1 choice
[   11.293745] hub 4-0:1.0: USB hub found
[   11.293751] hub 4-0:1.0: 2 ports detected
[   11.397480] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 18
[   11.397496] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   11.397501] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   11.397530] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   11.401451] ehci_hcd 0000:00:1d.7: debug port 1
[   11.401458] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   11.401465] ehci_hcd 0000:00:1d.7: irq 18, io mem 0xb0004000
[   11.417213] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   11.417323] usb usb5: configuration #1 chosen from 1 choice
[   11.417347] hub 5-0:1.0: USB hub found
[   11.417353] hub 5-0:1.0: 8 ports detected
[   11.521272] r8169 Gigabit Ethernet driver 2.2LK loaded
[   11.521369] ACPI: PCI Interrupt 0000:06:07.0[A] -> GSI 20 (level, low) -> IRQ 21
[   11.521618] eth0: RTL8169sb/8110sb at 0xe0038000, 00:0a:e4:b3:d1:f5, XID 10000000 IRQ 21
[   11.522206] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 22
[   11.522239] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   11.522253] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[   11.524415] ahci 0000:00:1f.2: version 3.0
[   11.524436] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 16
[   11.524455] ahci 0000:00:1f.2: nr_ports (4) and implemented port map (0x5) don't match, using nr_ports
[   11.524458] ahci 0000:00:1f.2: forcing PORTS_IMPL to 0xf
[   11.956432] Clocksource tsc unstable (delta = -15214872889 ns)
[   11.960482] Time: hpet clocksource has been installed.
[   11.977137] ahci 0000:00:1f.2: AHCI 0001.0000 32 slots 4 ports 1.5 Gbps 0xf impl SATA mode
[   11.977142] ahci 0000:00:1f.2: flags: 64bit ncq pm led slum part 
[   11.977148] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   11.977440] scsi0 : ahci
[   11.977644] scsi1 : ahci
[   11.977767] scsi2 : ahci
[   11.977891] scsi3 : ahci
[   11.977979] ata1: SATA max UDMA/133 abar m1024@0xb0004400 port 0xb0004500 irq 16
[   11.977983] ata2: SATA max UDMA/133 abar m1024@0xb0004400 port 0xb0004580 irq 16
[   11.977987] ata3: SATA max UDMA/133 abar m1024@0xb0004400 port 0xb0004600 irq 16
[   11.977991] ata4: SATA max UDMA/133 abar m1024@0xb0004400 port 0xb0004680 irq 16
[   11.988163] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   11.988290] ata1.00: ATA-7: FUJITSU MHV2060BH, 00000025, max UDMA/100
[   11.988293] ata1.00: 117210240 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   11.988450] ata1.00: configured for UDMA/100
[   11.995014] ata2: SATA link down (SStatus 0 SControl 0)
[   12.001543] ata3: SATA link down (SStatus 0 SControl 300)
[   12.007428] ata4: SATA link down (SStatus 0 SControl 0)
[   12.007553] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHV2060B 0000 PQ: 0 ANSI: 5
[   12.011386] ACPI: PCI Interrupt 0000:06:09.2[A] -> GSI 22 (level, low) -> IRQ 17
[   12.061119] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[b8007800-b8007fff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   12.063321] ata_piix 0000:00:1f.1: version 2.12
[   12.063337] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 22
[   12.063377] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   12.063924] scsi4 : ata_piix
[   12.064298] scsi5 : ata_piix
[   12.064817] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[   12.064820] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[   12.072947] ata5.00: ATAPI: _NEC DVD+/-RW ND-6650A, 1.42, max UDMA/33
[   12.076630] ata5.00: configured for UDMA/33
[   12.076665] ata6: port disabled. ignoring.
[   12.077097] scsi 4:0:0:0: CD-ROM            _NEC     DVD+-RW ND-6650A 1.42 PQ: 0 ANSI: 5
[   12.084577] Driver 'sd' needs updating - please use bus_type methods
[   12.084658] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
[   12.084671] sd 0:0:0:0: [sda] Write Protect is off
[   12.084673] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   12.084689] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   12.084737] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
[   12.084746] sd 0:0:0:0: [sda] Write Protect is off
[   12.084749] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   12.084764] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   12.084767]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   12.101131]  sda1 sda2 < sda5 >
[   12.102991] sd 0:0:0:0: [sda] Attached SCSI disk
[   12.109118] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   12.109137] sr 4:0:0:0: Attached scsi generic sg1 type 5
[   12.133349] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[   12.133355] Uniform CD-ROM driver Revision: 3.20
[   12.133406] sr 4:0:0:0: Attached scsi CD-ROM sr0
[   12.191304] Attempting manual resume
[   12.191309] swsusp: Resume From Partition 8:5
[   12.191311] PM: Checking swsusp image.
[   12.191399] PM: Resume from disk failed.
[   12.205572] kjournald starting.  Commit interval 5 seconds
[   12.205581] EXT3-fs: mounted filesystem with ordered data mode.
[   12.220139] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[05e40a00531e1052]
[   14.926218] Linux agpgart interface v0.102
[   14.998082] intel_rng: FWH not detected
[   15.016429] agpgart: Detected an Intel 915GM Chipset.
[   15.017068] agpgart: Detected 7932K stolen memory.
[   15.065675] agpgart: AGP aperture is 256M @ 0xc0000000
[   15.125922] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   15.165891] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   15.201867] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   15.381533] iTCO_vendor_support: vendor-support=0
[   15.433461] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   15.433557] iTCO_wdt: Found a ICH6-M TCO device (Version=2, TCOBASE=0x1060)
[   15.433592] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   15.669224] input: Power Button (FF) as /devices/virtual/input/input3
[   15.681069] ACPI: Power Button (FF) [PWRF]
[   15.681167] input: Lid Switch as /devices/virtual/input/input4
[   15.690182] ACPI: Lid Switch [LID0]
[   15.690270] input: Sleep Button (CM) as /devices/virtual/input/input5
[   15.709015] ACPI: Sleep Button (CM) [SLPB]
[   15.952870] ieee80211_crypt: registered algorithm 'NULL'
[   15.971901] ieee80211_crypt: registered algorithm 'CCMP'
[   15.988745] ieee80211_crypt: registered algorithm 'WEP'
[   16.008578] ieee80211_crypt: registered algorithm 'TKIP'
[   16.288367] Yenta: CardBus bridge found at 0000:06:09.0 [17c0:3007]
[   16.288394] Yenta: Using CSCINT to route CSC interrupts to PCI
[   16.288396] Yenta: Routing CardBus interrupts to PCI
[   16.288402] Yenta TI: socket 0000:06:09.0, mfunc 0x00001022, devctl 0x64
[   16.364058] ieee80211_crypt: registered algorithm 'NULL'
[   16.365653] ieee80211: exports duplicate symbol ieee80211_txb_free (owned by ieee80211_rtl)
[   16.520615] Yenta: ISA IRQ mask 0x0cf8, PCI irq 17
[   16.520620] Socket status: 30000006
[   16.520622] Yenta: Raising subordinate bus# of parent bus (#06) from #07 to #0a
[   16.520628] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[   16.520631] cs: IO port probe 0x3000-0x3fff: clean.
[   16.520890] pcmcia: parent PCI bridge Memory window: 0xb8000000 - 0xb80fffff
[   16.572113] ACPI: PCI Interrupt 0000:06:09.3[A] -> GSI 22 (level, low) -> IRQ 17
[   16.584250] sdhci: Secure Digital Host Controller Interface driver
[   16.584253] sdhci: Copyright(c) Pierre Ossman
[   16.584288] sdhci: SDHCI controller found at 0000:06:09.4 [104c:8034] (rev 0)
[   16.584310] ACPI: PCI Interrupt 0000:06:09.4[A] -> GSI 22 (level, low) -> IRQ 17
[   16.584328] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it.
[   16.584369] mmc0: SDHCI at 0xb8009400 irq 17 DMA
[   16.584380] sdhci:slot1: Will use DMA mode even though HW doesn't fully claim to support it.
[   16.584411] mmc1: SDHCI at 0xb8009000 irq 17 DMA
[   16.584421] sdhci:slot2: Will use DMA mode even though HW doesn't fully claim to support it.
[   16.584448] mmc2: SDHCI at 0xb8007400 irq 17 DMA
[   16.598952] tifm_core: MMC/SD card detected in socket 0:3
[   16.621232] ipw2200: Unknown symbol ieee80211_wx_get_encodeext
[   16.621378] ipw2200: Unknown symbol ieee80211_wx_set_encode
[   16.621428] ipw2200: Unknown symbol ieee80211_wx_get_encode
[   16.621587] ipw2200: disagrees about version of symbol ieee80211_txb_free
[   16.621589] ipw2200: Unknown symbol ieee80211_txb_free
[   16.621667] ipw2200: Unknown symbol ieee80211_wx_set_encodeext
[   16.621839] ipw2200: Unknown symbol ieee80211_wx_get_scan
[   16.621885] ipw2200: Unknown symbol escape_essid
[   16.622000] ipw2200: Unknown symbol ieee80211_freq_to_channel
[   16.622271] ipw2200: Unknown symbol ieee80211_set_geo
[   16.622444] ipw2200: Unknown symbol ieee80211_rx
[   16.622578] ipw2200: Unknown symbol ieee80211_channel_to_index
[   16.622865] ipw2200: disagrees about version of symbol ieee80211_rx_mgt
[   16.622868] ipw2200: Unknown symbol ieee80211_rx_mgt
[   16.622917] ipw2200: Unknown symbol ieee80211_get_geo
[   16.623000] ipw2200: Unknown symbol free_ieee80211
[   16.623229] ipw2200: Unknown symbol ieee80211_is_valid_channel
[   16.623347] ipw2200: Unknown symbol alloc_ieee80211
[   17.365259] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x92a0b1, caps: 0xa04713/0x204000
[   17.398465] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input6
[   17.422281] parport_pc 00:06: activated
[   17.422285] parport_pc 00:06: reported by Plug and Play ACPI
[   17.422425] parport_pc 00:06: disabled
[   17.539076] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:00/input/input7
[   17.570302] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   18.535628] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 22
[   18.535662] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   18.685792] ACPI: Battery Slot [BAT0] (battery present)
[   18.691696] ACPI: AC Adapter [ADP1] (on-line)
[   19.689570] mmc3: new SD card at address b368
[   19.837857] cs: IO port probe 0x100-0x3af: clean.
[   19.839593] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   19.840314] cs: IO port probe 0x820-0x8ff: clean.
[   19.840910] cs: IO port probe 0xc00-0xcf7: clean.
[   19.841660] cs: IO port probe 0xa00-0xaff: clean.
[   19.871097] mmcblk0: mmc3:b368 SD    993792KiB 
[   19.871136]  mmcblk0: p1
[   19.967526] lp: driver loaded but no devices found
[   20.004094] Adding 1485972k swap on /dev/sda5.  Priority:-1 extents:1 across:1485972k
[   20.078677] EXT3 FS on sda1, internal journal
[   20.422562] ip_tables: (C) 2000-2006 Netfilter Core Team
[   20.614857] No dock devices found.
[   21.243154] apm: BIOS not found.
[   21.294622] ppdev: user-space parallel port driver
[   21.324229] NET: Registered protocol family 10
[   21.324440] lo: Disabled Privacy Extensions
[   21.343995] audit(1219566454.294:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4937 profile="/usr/sbin/cupsd" namespace="default"
[   62.105389] Marking TSC unstable due to: cpufreq changes.
[   66.289310] r8169: eth0: link up
[   39.901180] Bluetooth: Core ver 2.11
[   39.901907] NET: Registered protocol family 31
[   39.901912] Bluetooth: HCI device and connection manager initialized
[   39.901918] Bluetooth: HCI socket layer initialized
[   39.924390] Bluetooth: L2CAP ver 2.9
[   39.924396] Bluetooth: L2CAP socket layer initialized
[   23.526566] Bluetooth: RFCOMM socket layer initialized
[   23.526582] Bluetooth: RFCOMM TTY layer initialized
[   23.526584] Bluetooth: RFCOMM ver 1.8
[   67.242583] NET: Registered protocol family 17
[   24.660639] [drm] Initialized drm 1.1.0 20060810
[   24.664713] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 22
[   24.664722] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   24.664797] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   75.285909] eth0: no IPv6 routers present

ande then 

lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by bongkin123 on 2008-08-24
It happened to me this morning also. I've been looking around and just realized this is an issue of the IPW2200 driver.

I tried to tweak the ipw2200 drive for a couple of hours but it seems it doesn't work.

Another person also had this issue and you may keep stay up with [this thread]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=889078") and hope someone will find a way.

---

### Post by Despina73 on 2008-08-24
Oh my god, the security update caused the problem?

---

