---
title: "ubuntu hang once in a while..why?"
date: 2009-08-31
forum: New to Ubuntu
---

### Post by sadinsudin on 2009-08-31
hi ubuntu friends! i've been using ubuntu 8.04 since last 3 months and go so well..and even i rarely using xp to do my work! on my desktop i've the eye candy effect like the cairo dock and screenlet..and i love it! but last week my ubuntu performance suddenly turn extremely slow..so i start reading the related thread, then i assumed this might caused by the cairo dock..so i uninstalled the my lovely cairo dock..at first my ubuntu performance was quite well..but sadly last night it start to hang once in a while..on the effect on desktop seem freezing and i can't even move my mouse pointer...some time it hang for few seconds and even it become worst when it hang for several minutes randomly...so can anyone tell me what should i do get my ubuntu work well as it was on the old days..hope to hear from u all soon..

---

### Post by matsuzine on 2009-09-01
Did you make any system changes (installing updates, for example) and then noticed a performance lag?

---

### Post by automaton26 on 2009-09-01
There could be many causes - are you sure you haven't just recently installed some updates?

If you use proprietary graphics drivers, you could try uninstalling them and then reinstalling them again.

Or perhaps your machine can't handle the effects and is overheating. Try disabling all effects, not just a few.

---

### Post by DJINNSeKo on 2009-09-01
Please print the output from:

> sudo dmesg

To see if your computer is actually complaining about something.

---

### Post by sadinsudin on 2009-09-03
sorry guys! actually my problem become worsen, i couldn't enter the desktop properly. each time i've entered the desktop, within 2-4 minutes it will freeze and even worst when in the login window it freeze..and i can't do anything accept plug out the power and wait it dies..i try not to push the power button...is there any other way to enter the terminal and have screen shot for..it?  any other advice.?.while waiting for your reply, i'll tryagain and again untill i manage to get the output required..

---

### Post by sadinsudin on 2009-09-04
ok finally i manage entering the desktop and disable the ndivia gc, screenlets and appearence set to none...but yet there still hang sessions which in much lesser time..so now what should i do?...still hoping that my ubuntu performs as before..

here are the output for $ sudo dmesg

240)
[    0.000000] ACPI: DSDT 3BF1004C, 6A18 (r1 HPQOEM SLIC-MPC  6040000 MSFT  100000E)
[    0.000000] ACPI: FACS 3BF17FC0, 0040
[    0.000000] ACPI: SLIC 3BF16BCC, 0176 (r1 HPQOEM SLIC-MPC  6040000 HPQ         1)
[    0.000000] ACPI: MCFG 3BF16D42, 003C (r1 HPQOEM SLIC-MPC  6040000  LTP        0)
[    0.000000] ACPI: HPET 3BF16D7E, 0038 (r1 HPQOEM SLIC-MPC  6040000  LTP        1)
[    0.000000] ACPI: APIC 3BF16DB6, 005E (r1 HPQOEM SLIC-MPC  6040000  LTP        0)
[    0.000000] ACPI: BOOT 3BF16E14, 0028 (r1 HPQOEM SLIC-MPC  6040000  LTP        1)
[    0.000000] ACPI: SSDT 3BF16E3C, 01C4 (r1 HPQOEM SLIC-MPC  6040000  LTP        1)
[    0.000000] ACPI: DMI detected: Hewlett-Packard
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:8 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:8 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009d000 - 000000000009e000
[    0.000000] swsusp: Registered nosave memory region: 000000000009e000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000d2000
[    0.000000] swsusp: Registered nosave memory region: 00000000000d2000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 243586
[    0.000000] Kernel command line: root=UUID=4e4f43f8-e779-4fd3-8f5d-a2afe2b69e22 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1808.356 MHz processor.
[   19.830259] spurious 8259A interrupt: IRQ7.
[   19.833373] Console: colour VGA+ 80x25
[   19.833376] console [tty0] enabled
[   19.833787] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   19.834351] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   19.854923] Memory: 961464k/982016k available (2181k kernel code, 19968k reserved, 1006k data, 368k init, 64512k highmem)
[   19.854931] virtual kernel memory layout:
[   19.854932]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   19.854933]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   19.854935]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   19.854936]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   19.854937]       .init : 0xc0423000 - 0xc047f000   ( 368 kB)
[   19.854938]       .data : 0xc0321548 - 0xc041cdc4   (1006 kB)
[   19.854940]       .text : 0xc0100000 - 0xc0321548   (2181 kB)
[   19.854942] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   19.854975] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   19.855123] hpet clockevent registered
[   19.935082] Calibrating delay using timer specific routine.. 3619.67 BogoMIPS (lpj=7239352)
[   19.935105] Security Framework initialized
[   19.935112] SELinux:  Disabled at boot.
[   19.935125] AppArmor: AppArmor initialized
[   19.935129] Failure registering capabilities with primary security module.
[   19.935138] Mount-cache hash table entries: 512
[   19.935251] Initializing cgroup subsys ns
[   19.935255] Initializing cgroup subsys cpuacct
[   19.935266] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001f 00000000
[   19.935275] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   19.935278] CPU: L2 Cache: 512K (64 bytes/line)
[   19.935280] CPU 0(2) -> Core 0
[   19.935283] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00020410 00002001 00000000 0000001f 00000000
[   19.935292] Compat vDSO mapped to ffffe000.
[   19.935305] Checking 'hlt' instruction... OK.
[   24.651774] SMP alternatives: switching to UP code
[   24.653057] Early unpacking initramfs... done
[   24.987927] ACPI: Core revision 20070126
[   24.987993] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   24.999063] CPU0: AMD Turion(tm) 64 X2  stepping 02
[   24.999079] SMP alternatives: switching to SMP code
[   24.999561] Booting processor 1/1 eip 3000
[   25.009733] Initializing CPU#1
[   25.088487] Calibrating delay using timer specific routine.. 3616.44 BogoMIPS (lpj=7232891)
[   25.088494] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001f 00000000
[   25.088501] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   25.088503] CPU: L2 Cache: 512K (64 bytes/line)
[   25.088505] CPU 1(2) -> Core 1
[   25.088507] AMD C1E detected late.     Force timer broadcast.
[   25.088509] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00020410 00002001 00000000 0000001f 00000000
[   25.088539] CPU1: AMD Turion(tm) 64 X2  stepping 02
[   25.088554] Total of 2 processors activated (7236.12 BogoMIPS).
[   25.088855] ENABLING IO-APIC IRQs
[   25.089089] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   25.128916] Brought up 2 CPUs
[   25.128971] CPU0 attaching sched-domain:
[   25.128973]  domain 0: span 03
[   25.128975]   groups: 01 02
[   25.128978] CPU1 attaching sched-domain:
[   25.128980]  domain 0: span 03
[   25.128982]   groups: 02 01
[   25.129179] net_namespace: 64 bytes
[   25.129187] Booting paravirtualized kernel on bare hardware
[   25.129648] Time: 10:19:17  Date: 09/04/09
[   25.129675] NET: Registered protocol family 16
[   25.129857] EISA bus registered
[   25.129862] ACPI: bus type pci registered
[   25.141976] PCI: BIOS BUG #81[49435000] found
[   25.142021] PCI: Using configuration type 1
[   25.142029] Setting up standard PCI resources
[   25.143888] ACPI: EC: Look up EC in DSDT
[   25.147746] ACPI: BIOS _OSI(Linux) query ignored via DMI
[   25.148027] ACPI: Interpreter enabled
[   25.148029] ACPI: (supports S0 S3 S4 S5)
[   25.148041] ACPI: Using IOAPIC for interrupt routing
[   25.148658] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   25.175112] ACPI: EC: GPE = 0x1, I/O: command/status = 0x66, data = 0x62
[   25.175114] ACPI: EC: driver started in interrupt mode
[   25.175169] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   25.176375] PCI: Transparent bridge - 0000:00:10.0
[   25.176390] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   25.176485] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[   25.176523] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[   25.176551] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
[   25.307834] ACPI: PCI Interrupt Link [LNK1] (IRQs 16 17 18 22 23) *0, disabled.
[   25.308024] ACPI: PCI Interrupt Link [LNK2] (IRQs 16 17 18 22 23) *10
[   25.308210] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 *10 11 14 15)
[   25.308395] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 10 11 14 15) *0, disabled.
[   25.308581] ACPI: PCI Interrupt Link [LK1E] (IRQs 20) *0, disabled.
[   25.308765] ACPI: PCI Interrupt Link [LK2E] (IRQs 19) *0, disabled.
[   25.308956] ACPI: PCI Interrupt Link [LK3E] (IRQs 21) *10
[   25.309141] ACPI: PCI Interrupt Link [LK4E] (IRQs 16 17 18 22 23) *0, disabled.
[   25.309326] ACPI: PCI Interrupt Link [LSMB] (IRQs 16 17 18 22 23) *10
[   25.309516] ACPI: PCI Interrupt Link [LSMU] (IRQs 16 17 18 22 23) *11
[   25.309701] ACPI: PCI Interrupt Link [LUS0] (IRQs 16 17 18 22 23) *11
[   25.309887] ACPI: PCI Interrupt Link [LUS2] (IRQs 16 17 18 22 23) *7
[   25.310072] ACPI: PCI Interrupt Link [LMAC] (IRQs 16 17 18 22 23) *11
[   25.310262] ACPI: PCI Interrupt Link [LAZA] (IRQs 16 17 18 22 23) *0, disabled.
[   25.310448] ACPI: PCI Interrupt Link [LACI] (IRQs 16 17 18 22 23) *0, disabled.
[   25.310634] ACPI: PCI Interrupt Link [LMCI] (IRQs 16 17 18 22 23) *0, disabled.
[   25.310819] ACPI: PCI Interrupt Link [LPID] (IRQs 16 17 18 22 23) *0, disabled.
[   25.311013] ACPI: PCI Interrupt Link [LTID] (IRQs 16 17 18 22 23) *5
[   25.311209] ACPI: PCI Interrupt Link [LSI1] (IRQs 16 17 18 22 23) *0
[   25.311338] Linux Plug and Play Support v0.97 (c) Adam Belay
[   25.311369] pnp: PnP ACPI init
[   25.311376] ACPI: bus type pnp registered
[   25.315486] pnp: PnP ACPI: found 11 devices
[   25.315488] ACPI: ACPI bus type pnp unregistered
[   25.315491] PnPBIOS: Disabled by ACPI PNP
[   25.315723] PCI: Using ACPI for IRQ routing
[   25.315726] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   25.328899] NET: Registered protocol family 8
[   25.328901] NET: Registered protocol family 20
[   25.328936] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[   25.328941] hpet0: 3 32-bit timers, 25000000 Hz
[   25.329985] AppArmor: AppArmor Filesystem Enabled
[   25.332709] Time: hpet clocksource has been installed.
[   25.332713] Clockevents: could not switch to one-shot mode: lapic is not functional.
[   25.332716] Could not switch to high resolution mode on CPU 0
[   25.336890] Clockevents: could not switch to one-shot mode: lapic is not functional.
[   25.336894] Could not switch to high resolution mode on CPU 1
[   25.344921] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[   25.344927] system 00:02: ioport range 0x1000-0x107f has been reserved
[   25.344929] system 00:02: ioport range 0x1080-0x10ff has been reserved
[   25.344932] system 00:02: ioport range 0x1400-0x147f has been reserved
[   25.344935] system 00:02: ioport range 0x1480-0x14ff has been reserved
[   25.344937] system 00:02: ioport range 0x1800-0x187f has been reserved
[   25.344940] system 00:02: ioport range 0x1880-0x18ff has been reserved
[   25.344943] system 00:02: ioport range 0x2000-0x203f has been reserved
[   25.344949] system 00:03: ioport range 0x360-0x361 has been reserved
[   25.344952] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
[   25.375368] PCI: Bridge: 0000:00:02.0
[   25.375369]   IO window: disabled.
[   25.375372]   MEM window: disabled.
[   25.375374]   PREFETCH window: disabled.
[   25.375376] PCI: Bridge: 0000:00:03.0
[   25.375378]   IO window: 4000-4fff
[   25.375381]   MEM window: b4000000-b7ffffff
[   25.375383]   PREFETCH window: d0000000-d01fffff
[   25.375386] PCI: Bridge: 0000:00:10.0
[   25.375388]   IO window: disabled.
[   25.375391]   MEM window: b8000000-b80fffff
[   25.375393]   PREFETCH window: disabled.
[   25.375405] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   25.375412] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   25.375420] PCI: Setting latency timer of device 0000:00:10.0 to 64
[   25.375431] NET: Registered protocol family 2
[   25.412930] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   25.413238] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   25.414173] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   25.414676] TCP: Hash tables configured (established 131072 bind 65536)
[   25.414679] TCP reno registered
[   25.428984] checking if image is initramfs... it is
[   26.080702] Freeing initrd memory: 7301k freed
[   26.080807] Simple Boot Flag at 0x36 set to 0x1
[   26.081456] audit: initializing netlink socket (disabled)
[   26.081468] audit(1252059552.528:1): initialized
[   26.081625] highmem bounce pool size: 64 pages
[   26.083496] VFS: Disk quotas dquot_6.5.1
[   26.083574] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   26.083697] io scheduler noop registered
[   26.083700] io scheduler anticipatory registered
[   26.083701] io scheduler deadline registered
[   26.083711] io scheduler cfq registered (default)
[   26.083727] pci 0000:00:00.0: Enabling HT MSI Mapping
[   26.083757] pci 0000:00:02.0: Enabling HT MSI Mapping
[   26.083766] pci 0000:00:03.0: Enabling HT MSI Mapping
[   26.083774] Boot video device is 0000:00:05.0
[   26.083795] pci 0000:00:09.0: Enabling HT MSI Mapping
[   26.304534] pci 0000:00:0e.0: Enabling HT MSI Mapping
[   26.304544] pci 0000:00:10.0: Enabling HT MSI Mapping
[   26.304555] pci 0000:00:10.1: Enabling HT MSI Mapping
[   26.304677] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   26.304700] assign_interrupt_mode Found MSI capability
[   26.304720] Allocate Port Service[0000:00:02.0:pcie00]
[   26.304780] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   26.304801] assign_interrupt_mode Found MSI capability
[   26.304816] Allocate Port Service[0000:00:03.0:pcie00]
[   26.305037] isapnp: Scanning for PnP cards...
[   26.657582] isapnp: No Plug & Play device found
[   26.685323] Real Time Clock Driver v1.12ac
[   26.685524] hpet_resources: 0xfed00000 is busy
[   26.685573] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   26.686726] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   26.686789] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   26.686881] PNP: PS/2 Controller [PNP0303:KBD0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   26.687195] i8042.c: Detected active multiplexing controller, rev 1.1.
[   26.687266] serio: i8042 KBD port at 0x60,0x64 irq 1
[   26.687271] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   26.687275] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   26.687277] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   26.687280] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   26.700226] mice: PS/2 mouse device common for all mice
[   26.700356] EISA: Probing bus 0 at eisa.0
[   26.700361] Cannot allocate resource for EISA slot 1
[   26.700363] Cannot allocate resource for EISA slot 2
[   26.700365] Cannot allocate resource for EISA slot 3
[   26.700367] Cannot allocate resource for EISA slot 4
[   26.700381] EISA: Detected 0 cards.
[   26.700383] cpuidle: using governor ladder
[   26.700386] cpuidle: using governor menu
[   26.700473] NET: Registered protocol family 1
[   26.700499] Using IPI No-Shortcut mode
[   26.700529] registered taskstats version 1
[   26.700665]   Magic number: 9:647:324
[   26.700695]   hash matches device ttyyd
[   26.700832]   hash matches device tty49
[   26.700873]   hash matches device PNP0B00:00
[   26.700881] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   26.700883] EDD information not available.
[   26.701106] Freeing unused kernel memory: 368k freed
[   26.701132] Write protecting the kernel read-only data: 802k
[   26.703028] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   27.936718] fuse init (API version 7.9)
[   27.956574] ACPI: Processor [CPU0] (supports 8 throttling states)
[   27.956826] ACPI: Processor [CPU1] (supports 8 throttling states)
[   27.976781] ACPI: Thermal Zone [TZS0] (36 C)
[   27.984422] ACPI: Thermal Zone [TZS1] (39 C)
[   28.457343] usbcore: registered new interface driver usbfs
[   28.457366] usbcore: registered new interface driver hub
[   28.457761] usbcore: registered new device driver usb
[   28.459448] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   28.459827] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 23
[   28.459838] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LUS0] -> GSI 23 (level, high) -> IRQ 16
[   28.459851] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   28.459854] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[   28.460190] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[   28.460212] ohci_hcd 0000:00:0b.0: irq 16, io mem 0xb0004000
[   28.508482] SCSI subsystem initialized
[   28.517191] usb usb1: configuration #1 chosen from 1 choice
[   28.517218] hub 1-0:1.0: USB hub found
[   28.517229] hub 1-0:1.0: 8 ports detected
[   28.518645] libata version 3.00 loaded.
[   28.619635] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 22
[   28.619651] ACPI: PCI Interrupt 0000:05:09.0[A] -> Link [LNK1] -> GSI 22 (level, high) -> IRQ 17
[   28.619791] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 18
[   28.619804] ACPI: PCI Interrupt 0000:00:0b.1[b] -> Link [LUS2] -> GSI 18 (level, high) -> IRQ 18
[   28.619818] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[   28.619821] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[   28.619857] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
[   28.619889] ehci_hcd 0000:00:0b.1: debug port 1
[   28.619894] PCI: cache line size of 64 is not supported by device 0000:00:0b.1
[   28.619905] ehci_hcd 0000:00:0b.1: irq 18, io mem 0xb0005000
[   28.630959] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   28.631072] usb usb2: configuration #1 chosen from 1 choice
[   28.631096] hub 2-0:1.0: USB hub found
[   28.631102] hub 2-0:1.0: 8 ports detected
[   28.671373] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[b8000000-b80007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   28.738901] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   28.739253] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 17
[   28.739263] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [LMAC] -> GSI 17 (level, high) -> IRQ 19
[   28.739270] PCI: Setting latency timer of device 0000:00:14.0 to 64
[   29.259230] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:16:d3:aa:35:a9
[   29.259236] forcedeth 0000:00:14.0: highdma pwrctl timirq lnktim desc-v3
[   29.259375] sata_nv 0000:00:0e.0: version 3.5
[   29.259393] PCI: Enabling device 0000:00:0e.0 (0005 -> 0007)
[   29.259708] ACPI: PCI Interrupt Link [LTID] enabled at IRQ 16
[   29.259718] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LTID] -> GSI 16 (level, high) -> IRQ 20
[   29.259763] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   29.260018] scsi0 : sata_nv
[   29.260066] scsi1 : sata_nv
[   29.260190] ata1: SATA max UDMA/133 cmd 0x30b0 ctl 0x30a4 bmdma 0x3090 irq 20
[   29.260193] ata2: SATA max UDMA/133 cmd 0x30a8 ctl 0x30a0 bmdma 0x3098 irq 20
[   29.738541] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   29.750716] ata1.00: ATA-7: SAMSUNG HM080HI, AB100-16, max UDMA/100
[   29.750719] ata1.00: 156301488 sectors, multi 16: LBA48 
[   29.774700] ata1.00: configured for UDMA/100
[   29.978492] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[07e40a002a2c5031]
[   30.090340] ata2: SATA link down (SStatus 0 SControl 300)
[   30.100981] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HM080HI  AB10 PQ: 0 ANSI: 5
[   30.102206] pata_amd 0000:00:0d.0: version 0.3.10
[   30.102277] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   30.102345] scsi2 : pata_amd
[   30.102498] scsi3 : pata_amd
[   30.103035] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x3080 irq 14
[   30.103038] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x3088 irq 15
[   30.610183] ata4.00: ATAPI: Slimtype DVD A  DS8A1P, CH71, max MWDMA2
[   30.806015] ata4.00: configured for MWDMA2
[   30.808545] scsi 3:0:0:0: CD-ROM            Slimtype DVD A  DS8A1P    CH71 PQ: 0 ANSI: 5
[   30.815945] Driver 'sd' needs updating - please use bus_type methods
[   30.816039] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   30.816051] sd 0:0:0:0: [sda] Write Protect is off
[   30.816054] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   30.816069] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   30.816113] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   30.816121] sd 0:0:0:0: [sda] Write Protect is off
[   30.816123] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   30.816136] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   30.816140]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   30.840799]  sda1 sda2 < sda5 sda6 sda7 >
[   30.891286] sd 0:0:0:0: [sda] Attached SCSI disk
[   30.895934] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   30.895951] sr 3:0:0:0: Attached scsi generic sg1 type 5
[   30.910992] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   30.910998] Uniform CD-ROM driver Revision: 3.20
[   30.911053] sr 3:0:0:0: Attached scsi CD-ROM sr0
[   31.251473] Attempting manual resume
[   31.251477] swsusp: Resume From Partition 8:7
[   31.251479] PM: Checking swsusp image.
[   31.251721] PM: Resume from disk failed.
[   31.264378] EXT3-fs: INFO: recovery required on readonly filesystem.
[   31.264381] EXT3-fs: write access will be enabled during recovery.
[   31.411976] kjournald starting.  Commit interval 5 seconds
[   31.412163] EXT3-fs: sda6: orphan cleanup on readonly fs
[   31.412173] ext3_orphan_cleanup: deleting unreferenced inode 406415
[   31.412198] EXT3-fs: sda6: 1 orphan inode deleted
[   31.412200] EXT3-fs: recovery complete.
[   31.414076] EXT3-fs: mounted filesystem with ordered data mode.
[   44.275187] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   44.615451] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   44.746749] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   44.956177] input: Power Button (FF) as /devices/virtual/input/input3
[   45.014366] ACPI: Power Button (FF) [PWRF]
[   45.014432] input: Sleep Button (CM) as /devices/virtual/input/input4
[   45.077331] ricoh-mmc: Ricoh MMC Controller disabling driver
[   45.077336] ricoh-mmc: Copyright(c) Philip Langdale
[   45.077393] ricoh-mmc: Ricoh MMC controller found at 0000:05:09.2 [1180:0843] (rev 1)
[   45.077402] ricoh-mmc: Controller is now disabled.
[   45.078325] ACPI: Sleep Button (CM) [SLPB]
[   45.078383] input: Power Button (CM) as /devices/virtual/input/input5
[   45.142281] ACPI: Power Button (CM) [PWRB]
[   45.142377] ACPI: WMI-Acer: Mapper loaded
[   45.151945] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x3040
[   45.151961] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x3000
[   45.213563] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:00/input/input6
[   45.274214] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   45.294260] Linux agpgart interface v0.102
[   45.445522] sdhci: Secure Digital Host Controller Interface driver
[   45.445527] sdhci: Copyright(c) Pierre Ossman
[   45.445589] sdhci: SDHCI controller found at 0000:05:09.1 [1180:0822] (rev 19)
[   45.445933] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 23
[   45.445937] ACPI: PCI Interrupt 0000:05:09.1[b] -> Link [LNK2] -> GSI 23 (level, high) -> IRQ 16
[   45.445955] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it.
[   45.445998] mmc0: SDHCI at 0xb8000800 irq 16 DMA
[   45.663657] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x200000
[   45.682262] eth0: no link during initialization.
[   45.692706] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input7
[   45.831544] nvidia: module license 'NVIDIA' taints kernel.
[   46.135235] ACPI: PCI Interrupt Link [LK3E] enabled at IRQ 21
[   46.135248] ACPI: PCI Interrupt 0000:00:05.0[A] -> Link [LK3E] -> GSI 21 (level, high) -> IRQ 21
[   46.135258] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   46.135518] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   46.217378] ACPI: Battery Slot [BAT0] (battery present)
[   46.240733] ACPI: AC Adapter [ADP1] (on-line)
[   46.670665] NET: Registered protocol family 10
[   46.670889] lo: Disabled Privacy Extensions
[   46.671371] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   46.814727] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 22
[   46.814733] ACPI: PCI Interrupt 0000:00:10.1[b] -> Link [LAZA] -> GSI 22 (level, high) -> IRQ 17
[   46.814756] PCI: Setting latency timer of device 0000:00:10.1 to 64
[   47.287264] lp: driver loaded but no devices found
[   47.395372] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   47.483536] usbcore: registered new interface driver ndiswrapper
[   47.609459] Adding 489940k swap on /dev/sda7.  Priority:-1 extents:1 across:489940k
[   48.150219] EXT3 FS on sda6, internal journal
[   49.363424] ip_tables: (C) 2000-2006 Netfilter Core Team
[   49.727378] PPP generic driver version 2.4.2
[   49.771630] NET: Registered protocol family 17
[   50.154991] No dock devices found.
[   50.483659] powernow-k8: Found 1 AMD Turion(tm) 64 X2  processors (2 cpu cores) (version 2.20.00)
[   50.483536] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x13
[   50.483541] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0x15
[   50.483544] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x1e
[   51.339484] apm: BIOS not found.
[   51.465962] ppdev: user-space parallel port driver
[   51.691621] audit(1252030783.648:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5295 profile="/usr/sbin/cupsd" namespace="default"
[   52.595752] Clocksource tsc unstable (delta = -210368531 ns)
[   52.832699] usbcore: deregistering interface driver ndiswrapper
[   52.852495] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   52.872733] usbcore: registered new interface driver ndiswrapper
[   53.664303] Bluetooth: Core ver 2.11
[   53.664385] NET: Registered protocol family 31
[   53.664387] Bluetooth: HCI device and connection manager initialized
[   53.664392] Bluetooth: HCI socket layer initialized
[   53.683755] Bluetooth: L2CAP ver 2.9
[   53.683759] Bluetooth: L2CAP socket layer initialized
[   53.742151] Bluetooth: RFCOMM socket layer initialized
[   53.742294] Bluetooth: RFCOMM TTY layer initialized
[   53.742297] Bluetooth: RFCOMM ver 1.8
[   72.005212] CPU0 attaching NULL sched-domain.
[   72.005221] CPU1 attaching NULL sched-domain.
[   72.021323] CPU0 attaching sched-domain:
[   72.021328]  domain 0: span 03
[   72.021330]   groups: 01 02
[   72.021333] CPU1 attaching sched-domain:
[   72.021335]  domain 0: span 03
[   72.021337]   groups: 02 01

---

### Post by sadinsudin on 2009-09-04
here are the output when i enter $ top in the terminal..(any comments?)

top - 10:40:55 up 11 min,  2 users,  load average: 0.17, 0.74, 0.63
Tasks: 118 total,   1 running, 117 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.2%us,  0.5%sy,  0.0%ni, 98.0%id,  0.0%wa,  0.3%hi,  0.0%si,  0.0%st
Mem:    969324k total,   504820k used,   464504k free,    20228k buffers
Swap:   489940k total,        0k used,   489940k free,   327900k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5682 root      20   0  102m  15m 6556 S      2       1.7   0:19.98 Xorg               
 6355 zahir     20   0 74976  20m  10m S      1       2.1   0:00.70 gnome-terminal     
 6375 zahir     20   0  2308 1120  856 R        1       0.1   0:00.18 top                
    1 root        20   0  2844 1692  544 S        0       0.2   0:01.32 init               
    2 root        15  -5     0      0    0 S    0     0.0    0:00.00 kthreadd           
    3 root        RT  -5     0      0    0 S    0     0.0    0:00.00 migration/0        
    4 root        15  -5     0      0    0 S    0     0.0    0:00.00 ksoftirqd/0        
    5 root        RT  -5     0      0    0 S    0     0.0    0:00.00 watchdog/0         
    6 root        RT  -5     0      0    0 S    0     0.0    0:00.00 migration/1

---

### Post by DJINNSeKo on 2009-09-04
> sorry guys! actually my problem become worsen, i couldn't enter the desktop properly. each time i've entered the desktop, within 2-4 minutes it will freeze and even worst when in the login window it freeze..and i can't do anything accept plug out the power and wait it dies..i try not to push the power button...is there any other way to enter the terminal and have screen shot for..it? any other advice.?.while waiting for your reply, i'll tryagain and again untill i manage to get the output required..

You can enter terminal with "Ctrl Alt F2" then you can post the output of a comand to a file,

i.e. sudo dmesg > mydmesg.txt

and finally scp that to another computer.


But anyway from your posts I don't see anything wrong going on.

If you insert a live CD does it work fine?

---

### Post by stinger30au on 2009-09-04
check the basics first

dia-assm the pc and clean it with an air compressor, *NOT* a vacume cleaner

hold a pen or something on fan blades to not spin them and give them a good clean

remove cpu heat sink and clean all the heat sink off and apply fresh stuff, not too much. too much is worse then none at all

check all hdd for defects with dos boot cd  
[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

---

### Post by sadinsudin on 2009-09-06
thanks guys! thanks 4 the great info..so now i'm still running ubuntu in the simplest way..no any eye candy effect and it seem no more hang sessions..and now i'm googling all softwares contain in the ubcd disc(thanks stinger30au !! you rock dude!!), which i find it really usefull in this kind situations..if everything go well i might reinstall all the eye candy effects, but is it wise?! or any other suggestions? final question..is there any routine or any measures that should i take in order to maintain my ubuntu health..thanks

---

### Post by sadinsudin on 2009-09-09
still can't determine the main reason why my ubuntu hang....but luckily now i manage to run my ubuntu again..after uninstalling the nvidia gc driver and make a fresh install (follow the instruction according to the ubuntu documentations..) and then once again by referring the ubuntu documentation instructions as my guide i installed almost all needed stuffs on my ubuntu..an then i started updating all updates available..and now my ubuntu run better than my "dark age" of ubuntu ...still facing the "freezing"/hang sessions but acceptableupdate...now cpu run on about 5% regularly..my ubuntu apprence i set on normal..with 2 desktop size only no cube effect..no screenlets but i have my cairo-dock..
by the way i learn that by using the 

$sudo apt-get <instructions>
i can complete remove all the uninstall files by 
$sudo apt-get autoclean and 
update all the files by 
$sudo apt-get update

and so much more to learn...

---

