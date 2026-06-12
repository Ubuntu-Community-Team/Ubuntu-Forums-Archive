---
title: "How to set up Glink CDMA usb modem or data card for internet"
date: 2011-01-11
forum: New to Ubuntu
---

### Post by chitragurung on 2011-01-11
I have been using ubuntu 8.04 in my dell inspiron mini machine. Now I want to use CDMA usb modem for internet access. But I could not set up it. As I noticed from forum I have some result from the code advised from forum. Can you help me to set up ?

chitra@chitra:~$ lsusb
Bus 005 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. 
Bus 005 Device 003: ID 064e:a129 Suyin Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 006: ID 1c4f:0003  
Bus 001 Device 001: ID 0000:0000

Than dmseg

[    8.895585] SMP alternatives: switching to UP code
[    8.897767] Early unpacking initramfs... done
[    9.099205] ACPI: Core revision 20070126
[    9.099314] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    9.107758] CPU0: Intel(R) Atom(TM) CPU N270   @ 1.60GHz stepping 02
[    9.107787] SMP alternatives: switching to SMP code
[    9.108494] Booting processor 1/1 eip 3000
[    9.118512] Initializing CPU#1
[    9.198840] Calibrating delay using timer specific routine.. 3192.23 BogoMIPS (lpj=638447
[    9.198853] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0040c39d 00000000 00000001 00000000
[    9.198865] monitor/mwait feature present.
[    9.198871] CPU: L1 I cache: 32K, L1 D cache: 24K
[    9.198876] CPU: L2 cache: 512K
[    9.198880] CPU: Physical Processor ID: 0
[    9.198886] CPU: After all inits, caps: bfe9fbf7 00100000 00000000 00043940 0040c39d 00000000 00000001 00000000
[    9.198897] Intel machine check architecture supported.
[    9.198903] Intel machine check reporting enabled on CPU#1.
[    9.199146] CPU1: Intel(R) Atom(TM) CPU N270   @ 1.60GHz stepping 02
[    9.199187] Total of 2 processors activated (6384.29 BogoMIPS).
[    9.199391] ENABLING IO-APIC IRQs
[    9.199613] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    9.346932] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    9.366934] Brought up 2 CPUs
[    9.366976] CPU0 attaching sched-domain:
[    9.366981]  domain 0: span 03
[    9.366984]   groups: 01 02
[    9.366990]   domain 1: span 03
[    9.366993]    groups: 03
[    9.366997] CPU1 attaching sched-domain:
[    9.367000]  domain 0: span 03
[    9.367003]   groups: 02 01
[    9.367008]   domain 1: span 03
[    9.367011]    groups: 03
[    9.367405] net_namespace: 64 bytes
[    9.367419] Booting paravirtualized kernel on bare hardware
[    9.368384] Time: 15:41:58  Date: 01/11/11
[    9.368479] NET: Registered protocol family 16
[    9.368855] No dock devices found.
[    9.369032] ACPI: bus type pci registered
[    9.369842] PCI: PCI BIOS revision 3.00 entry at 0xfde5f, last bus=5
[    9.369847] PCI: Using configuration type 1
[    9.369861] Setting up standard PCI resources
[    9.374769] ACPI: EC: Look up EC in DSDT
[    9.377720] ACPI: BIOS _OSI(Linux) query honored via cmdline
[    9.377726] ACPI: DMI System Vendor: Dell Inc.
[    9.377730] ACPI: DMI Product Name: Inspiron 1011
[    9.377733] ACPI: DMI Product Version: A06
[    9.377735] ACPI: DMI Board Name: CN0Y53
[    9.377738] ACPI: DMI BIOS Vendor: Dell Inc.
[    9.377741] ACPI: DMI BIOS Date: 07/29/2009
[    9.377744] ACPI: Please send DMI info above to [EMAIL="linux-acpi@vger.kernel.org"]linux-acpi@vger.kernel.org[/EMAIL]
[    9.378665] ACPI: Interpreter enabled
[    9.378672] ACPI: (supports S0 S3 S4 S5)
[    9.378698] ACPI: Using IOAPIC for interrupt routing
[    9.379301] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    9.479905] ACPI: EC: GPE = 0x19, I/O: command/status = 0x66, data = 0x62
[    9.479913] ACPI: EC: driver started in interrupt mode
[    9.480000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    9.480914] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    9.480922] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[    9.482347] PCI: Transparent bridge - 0000:00:1e.0
[    9.482401] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    9.483017] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    9.483283] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    9.483538] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    9.483820] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    9.499048] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[    9.499260] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    9.499467] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    9.499672] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    9.499877] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    9.500082] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    9.500288] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    9.500492] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[    9.500855] ACPI: WMI: Mapper loaded
[    9.500861] Linux Plug and Play Support v0.97 (c) Adam Belay
[    9.500925] pnp: PnP ACPI init
[    9.500942] ACPI: bus type pnp registered
[    9.526934] pnp: PnP ACPI: found 11 devices
[    9.526939] ACPI: ACPI bus type pnp unregistered
[    9.527281] SCSI subsystem initialized
[    9.527358] libata version 3.00 loaded.
[    9.527680] usbcore: registered new interface driver usbfs
[    9.527753] usbcore: registered new interface driver hub
[    9.527836] usbcore: registered new device driver usb
[    9.528469] PCI: Using ACPI for IRQ routing
[    9.528476] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    9.610718] NET: Registered protocol family 8
[    9.610723] NET: Registered protocol family 20
[    9.610834] AppArmor: AppArmor Filesystem Enabled
[    9.614488] Time: tsc clocksource has been installed.
[    9.630763] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[    9.630771] system 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
[    9.630776] system 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
[    9.630782] system 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
[    9.630788] system 00:01: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[    9.630793] system 00:01: iomem range 0xfed20000-0xfed3ffff could not be reserved
[    9.630799] system 00:01: iomem range 0xfed40000-0xfed44fff could not be reserved
[    9.630805] system 00:01: iomem range 0xfed45000-0xfed8ffff could not be reserved
[    9.630819] system 00:04: iomem range 0xfed00000-0xfed003ff could not be reserved
[    9.630831] system 00:06: ioport range 0x680-0x69f has been reserved
[    9.630836] system 00:06: ioport range 0x800-0x80f has been reserved
[    9.630841] system 00:06: ioport range 0x1000-0x107f has been reserved
[    9.630847] system 00:06: ioport range 0x1180-0x11bf has been reserved
[    9.630852] system 00:06: ioport range 0x1640-0x164f has been reserved
[    9.630857] system 00:06: ioport range 0xfe00-0xfe7f has been reserved
[    9.630862] system 00:06: ioport range 0xff00-0xff7f has been reserved
[    9.630874] system 00:07: ioport range 0x6a0-0x6af has been reserved
[    9.630879] system 00:07: ioport range 0x6b0-0x6ff has been reserved
[    9.666259] PCI: Bridge: 0000:00:1c.0
[    9.666264]   IO window: disabled.
[    9.666271]   MEM window: disabled.
[    9.666277]   PREFETCH window: disabled.
[    9.666285] PCI: Bridge: 0000:00:1c.1
[    9.666287]   IO window: disabled.
[    9.666295]   MEM window: f0100000-f01fffff
[    9.666300]   PREFETCH window: disabled.
[    9.666309] PCI: Bridge: 0000:00:1c.2
[    9.666314]   IO window: 2000-2fff
[    9.666321]   MEM window: 50000000-500fffff
[    9.666328]   PREFETCH window: f0500000-f05fffff
[    9.666336] PCI: Bridge: 0000:00:1e.0
[    9.666338]   IO window: disabled.
[    9.666345]   MEM window: disabled.
[    9.666351]   PREFETCH window: disabled.
[    9.666398] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 16
[    9.666410] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    9.666445] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 17
[    9.666455] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    9.666484] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[    9.666493] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    9.666510] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    9.666532] NET: Registered protocol family 2
[    9.706529] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    9.707003] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    9.708048] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    9.708603] TCP: Hash tables configured (established 131072 bind 65536)
[    9.708610] TCP reno registered
[    9.718673] checking if image is initramfs... it is
[   10.109605] Freeing initrd memory: 2751k freed
[   10.109885] Simple Boot Flag at 0x36 set to 0x80
[   10.111126] audit: initializing netlink socket (disabled)
[   10.111147] audit(1294760518.112:1): initialized
[   10.111420] highmem bounce pool size: 64 pages
[   10.115195] VFS: Disk quotas dquot_6.5.1
[   10.115348] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   10.116230] io scheduler noop registered
[   10.116235] io scheduler anticipatory registered
[   10.116238] io scheduler deadline registered
[   10.116355] io scheduler cfq registered (default)
[   10.116375] Boot video device is 0000:00:02.0
[   10.116670] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   10.116736] assign_interrupt_mode Found MSI capability
[   10.116795] Allocate Port Service[0000:00:1c.0:pcie00]
[   10.116862] Allocate Port Service[0000:00:1c.0cie02]
[   10.117004] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   10.117069] assign_interrupt_mode Found MSI capability
[   10.117123] Allocate Port Service[0000:00:1c.1cie00]
[   10.117189] Allocate Port Service[0000:00:1c.1cie02]
[   10.117335] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   10.117400] assign_interrupt_mode Found MSI capability
[   10.117453] Allocate Port Service[0000:00:1c.2cie00]
[   10.117517] Allocate Port Service[0000:00:1c.2:pcie02]
[   10.121610] ACPI: AC Adapter [ACAD] (on-line)
[   10.162337] Switched to high resolution mode on CPU 1
[   10.165989] Switched to high resolution mode on CPU 0
[   10.501705] ACPI: Battery Slot [BAT1] (battery present)
[   10.502067] input: Power Button (FF) as /devices/virtual/input/input0
[   10.502074] ACPI: Power Button (FF) [PWRF]
[   10.502193] input: Lid Switch as /devices/virtual/input/input1
[   10.502287] ACPI: Lid Switch [LID0]
[   10.502405] input: Power Button (CM) as /devices/virtual/input/input2
[   10.502412] ACPI: Power Button (CM) [PWRB]
[   10.511341] ACPI: device:01 is registered as cooling_device0
[   10.511720] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input3
[   10.511729] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   10.512456] ACPI: SSDT 3F6DBC78, 0245 (r2  PmRef  Cpu0Ist     3000 INTL 20050624)
[   10.512803] ACPI: SSDT 3F6DB60E, 05E5 (r2  PmRef  Cpu0Cst     3001 INTL 20050624)
[   10.513566] Monitor-Mwait will be used to enter C-1 state
[   10.513572] Monitor-Mwait will be used to enter C-2 state
[   10.513576] Monitor-Mwait will be used to enter C-3 state
[   10.513669] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   10.513755] ACPI: ACPI0007:00 is registered as cooling_device1
[   10.513765] ACPI: Processor [CPU0] (supports 8 throttling states)
[   10.514272] ACPI: SSDT 3F6DBEBD, 00D4 (r2  PmRef  Cpu1Ist     3000 INTL 20050624)
[   10.514605] ACPI: SSDT 3F6DBBF3, 0085 (r2  PmRef  Cpu1Cst     3000 INTL 20050624)
[   10.515580] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   10.515667] ACPI: ACPI0007:01 is registered as cooling_device2
[   10.515676] ACPI: Processor [CPU1] (supports 8 throttling states)
[   10.546497] ACPI: LNXTHERM:01 is registered as thermal_zone0
[   10.559094] ACPI: Thermal Zone [TZ01] (49 C)
[   10.664459] Real Time Clock Driver v1.12ac
[   10.664819] hpet_acpi_add: no address or irqs in _CRS
[   10.664850] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   10.667287] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   10.667882] loop: module loaded
[   10.667968] Driver 'sd' needs updating - please use bus_type methods
[   10.668032] Driver 'sr' needs updating - please use bus_type methods
[   10.668236] ata_piix 0000:00:1f.2: version 2.12
[   10.668248] ata_piix 0000:00:1f.2: MAP [ P0 P2 -- -- ]
[   10.821351] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[   10.821404] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   10.821531] scsi0 : ata_piix
[   10.821677] scsi1 : ata_piix
[   10.823357] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[   10.823363] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[   11.033699] ata1.00: ATA-8: WDC WD1600BEVT-75ZCT2, 11.01A11, max UDMA/133
[   11.033705] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   11.050154] ata1.00: configured for UDMA/133
[   11.216353] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600BEVT-7 11.0 PQ: 0 ANSI: 5
[   11.216601] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   11.216630] sd 0:0:0:0: [sda] Write Protect is off
[   11.216637] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   11.216681] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   11.216774] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   11.216802] sd 0:0:0:0: [sda] Write Protect is off
[   11.216808] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   11.216854] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   11.216861]  sda: sda1 sda2 sda3
[   11.223721] sd 0:0:0:0: [sda] Attached SCSI disk
[   11.223861] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   11.224253] USB Universal Host Controller Interface driver v3.0
[   11.224361] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
[   11.224377] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   11.224384] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   11.224550] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   11.224593] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00001820
[   11.224950] usb usb1: configuration #1 chosen from 1 choice
[   11.225038] hub 1-0:1.0: USB hub found
[   11.225051] hub 1-0:1.0: 2 ports detected
[   11.328965] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[   11.328980] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   11.328986] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   11.329148] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   11.329188] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[   11.329458] usb usb2: configuration #1 chosen from 1 choice
[   11.329545] hub 2-0:1.0: USB hub found
[   11.329557] hub 2-0:1.0: 2 ports detected
[   11.432850] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   11.432865] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   11.432872] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   11.433035] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   11.433077] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[   11.433351] usb usb3: configuration #1 chosen from 1 choice
[   11.433437] hub 3-0:1.0: USB hub found
[   11.433449] hub 3-0:1.0: 2 ports detected
[   11.536757] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 17
[   11.536772] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   11.536778] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   11.536936] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   11.536976] uhci_hcd 0000:00:1d.3: irq 17, io base 0x00001880
[   11.537243] usb usb4: configuration #1 chosen from 1 choice
[   11.537331] hub 4-0:1.0: USB hub found
[   11.537342] hub 4-0:1.0: 2 ports detected
[   11.640663] Initializing USB Mass Storage driver...
[   11.640741] usbcore: registered new interface driver usb-storage
[   11.640747] USB Mass Storage support registered.
[   11.640819] usbcore: registered new interface driver libusual
[   11.641049] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   11.642693] i8042_command I8042_CMD_KBD_DISABLE OK
[   11.673081] i8042_command I8042_CMD_KBD_ENABLE OK
[   11.676117] serio: i8042 KBD port at 0x60,0x64 irq 1
[   11.676126] serio: i8042 AUX port at 0x60,0x64 irq 12
[   11.676362] mice: PS/2 mouse device common for all mice
[   11.732722] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   11.755080] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[   11.805412] cpuidle: using governor ladder
[   12.807997] cpuidle: using governor menu
[   12.808064] sdhci: Secure Digital Host Controller Interface driver
[   12.808069] sdhci: Copyright(c) Pierre Ossman
[   12.808894] NET: Registered protocol family 1
[   12.809341] NET: Registered protocol family 10
[   12.809693] lo: Disabled Privacy Extensions
[   12.810305] NET: Registered protocol family 17
[   12.810345] Using IPI No-Shortcut mode
[   12.810537]   Magic number: 11:517:689
[   12.810881] Freeing unused kernel memory: 296k freed
[   13.163214] usbcore: registered new interface driver hiddev
[   13.163297] usbcore: registered new interface driver usbhid
[   13.163304] /build/buildd/linux-2.6.24/debian/build/custom-source-lpia/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   13.180228] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
[   13.180256] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   13.180266] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   13.180470] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   13.184444] ehci_hcd 0000:00:1d.7: debug port 1
[   13.184464] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   13.184476] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xf0444000
[   13.200002] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   13.200297] usb usb5: configuration #1 chosen from 1 choice
[   13.200402] hub 5-0:1.0: USB hub found
[   13.200417] hub 5-0:1.0: 8 ports detected
[   13.381867] Registering unionfs 1.4
[   13.381874] unionfs: debugging is not enabled
[   13.395204] squashfs: version 3.3 (2007/10/31) Phillip Lougher
[   13.482779] fuse init (API version 7.9)
[   14.147111] usb 5-2: new high speed USB device using ehci_hcd and address 3
[   14.324301] usb 5-2: configuration #1 chosen from 1 choice
[   14.565655] usb 5-3: new high speed USB device using ehci_hcd and address 4
[   14.904587] kjournald starting.  Commit interval 5 seconds
[   14.904613] EXT3-fs: mounted filesystem with ordered data mode.
[   15.651725] usb 5-3: configuration #1 chosen from 1 choice
[   15.653807] scsi2 : SCSI emulation for USB Mass Storage devices
[   15.653929] usb-storage: device found at 4
[   15.653934] usb-storage: waiting for device to settle before scanning
[   16.136170] usb 1-1: new low speed USB device using uhci_hcd and address 2
[   16.309993] usb 1-1: configuration #1 chosen from 1 choice
[   16.326121] input: SIGMACH1P U+P Mouse as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/input/input6
[   16.352058] input,hidraw0: USB HID v1.10 Mouse [SIGMACH1P U+P Mouse] on usb-0000:00:1d.0-1
[   16.591723] usb 4-2: new full speed USB device using uhci_hcd and address 2
[   16.655621] Clocksource tsc unstable (delta = -805470108 ns)
[   16.659610] Time: acpi_pm clocksource has been installed.
[   16.732014] usb 4-2: configuration #1 chosen from 1 choice
[   18.338502] 2.6.2X-Elan-touchpad-2009-03-09
[   18.338510] +elantech_detect
[   18.699573] elantech.c: PSMOUSE_CMD_RESET_BAT  param[0]=aa param[1]=0 param[2]=0
[   18.737686] elantech.c: unexpected magic knock result 0x00, 0x02, 0x64.
[   18.737694] 2.6.2X-Elan-touchpad-2009-03-09
[   18.737698] +elantech_detect
[   18.798234] usb 1-1: USB disconnect, address 2
[   19.097209] elantech.c: PSMOUSE_CMD_RESET_BAT  param[0]=aa param[1]=0 param[2]=0
[   19.134953] elantech.c: unexpected magic knock result 0x00, 0x02, 0x64.
[   19.134961] 2.6.2X-Elan-touchpad-2009-03-09
[   19.134964] +elantech_detect
[   19.493921] elantech.c: PSMOUSE_CMD_RESET_BAT  param[0]=aa param[1]=0 param[2]=0
[   19.532066] elantech.c: unexpected magic knock result 0x00, 0x02, 0x64.
[   19.664621] usb 1-1: new low speed USB device using uhci_hcd and address 3
[   19.702292] usb 1-1: configuration #1 chosen from 1 choice
[   19.716050] input: SIGMACH1P U+P Mouse as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/input/input7
[   19.743990] input,hidraw0: USB HID v1.10 Mouse [SIGMACH1P U+P Mouse] on usb-0000:00:1d.0-1
[   20.033539] usb-storage: device scan complete
[   20.037220] scsi 2:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[   20.040521] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   20.040600] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   20.228277] Synaptics Touchpad, model: 1, fw: 7.4, id: 0x1e0b1, caps: 0xd04711/0xa40000
[   20.260183] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[   20.401577] intel_rng: FWH not detected
[   20.471340] iTCO_vendor_support: vendor-support=0
[   20.502326] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   20.502467] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   20.502523] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   20.560910] ieee80211_crypt: registered algorithm 'NULL'
[   20.564103] usb 1-1: USB disconnect, address 3
[   20.597412] r8169 Gigabit Ethernet driver 2.2LK loaded
[   20.597496] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[   20.597552] PCI: Setting latency timer of device 0000:04:00.0 to 64
[   20.598934] eth0: RTL8102e at 0xf886c000, 00:24:e8:db:1a:9e, XID 24c00000 IRQ 220
[   20.692671] ieee80211_crypt: registered algorithm 'TKIP'
[   20.821147] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   20.821564] EXT3 FS on sda2, internal journal
[   21.155001] usb 1-1: new low speed USB device using uhci_hcd and address 4
[   21.237986] usb 1-1: configuration #1 chosen from 1 choice
[   21.254276] input: SIGMACH1P U+P Mouse as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/input/input9
[   21.292087] input,hidraw0: USB HID v1.10 Mouse [SIGMACH1P U+P Mouse] on usb-0000:00:1d.0-1
[   23.270461] ip_tables: (C) 2000-2006 Netfilter Core Team
[   23.815524] PPP generic driver version 2.4.2
[   27.704126] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 21
[   27.704175] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   28.063927] Linux agpgart interface v0.102
[   28.068707] agpgart: Detected an Intel 945GME Chipset.
[   28.068915] agpgart: Detected 7932K stolen memory.
[   28.086960] agpgart: AGP aperture is 256M @ 0xd0000000
[   28.128926] [drm] Initialized drm 1.1.0 20060810
[   33.495387] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
[   33.495420] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   33.500159] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   33.893624] usb 1-1: USB disconnect, address 4
[   34.632928] usb 1-1: new low speed USB device using uhci_hcd and address 5
[   34.806790] usb 1-1: configuration #1 chosen from 1 choice
[   34.823398] input: SIGMACH1P U+P Mouse as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/input/input10
[   34.865890] input,hidraw0: USB HID v1.10 Mouse [SIGMACH1P U+P Mouse] on usb-0000:00:1d.0-1
[   35.132505] usb 1-1: USB disconnect, address 5
[   36.120460] usb 1-1: new low speed USB device using uhci_hcd and address 6
[   36.300225] usb 1-1: configuration #1 chosen from 1 choice
[   36.316713] input: SIGMACH1P U+P Mouse as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/input/input11
[   36.386336] input,hidraw0: USB HID v1.10 Mouse [SIGMACH1P U+P Mouse] on usb-0000:00:1d.0-1
[   38.748446] parport 0x378 (WARNING): CTR: wrote 0x0c, read 0xff
[   38.748465] parport 0x378 (WARNING): DATA: wrote 0xaa, read 0xff
[   38.748471] parport 0x378: You gave this address, but there is probably no parallel port there!
[   38.748506] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   38.844647] ppdev: user-space parallel port driver
[   40.938662] audit(1294760551.813:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5205 profile="/usr/sbin/cupsd" namespace="default"
[   42.126943] r8169: eth0: link down
[   42.130130] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   77.923570] Bluetooth: Core ver 2.11
[   77.924402] NET: Registered protocol family 31
[   77.924413] Bluetooth: HCI device and connection manager initialized
[   77.924424] Bluetooth: HCI socket layer initialized
[   77.961512] Bluetooth: HCI USB driver ver 2.9
[   77.961603] usbcore: registered new interface driver hci_usb
[   78.159571] Bluetooth: L2CAP ver 2.9
[   78.159584] Bluetooth: L2CAP socket layer initialized
[   78.730360] Bluetooth: RFCOMM socket layer initialized
[   78.730388] Bluetooth: RFCOMM TTY layer initialized
[   78.730393] Bluetooth: RFCOMM ver 1.8
[   79.180205] Linux video capture interface: v2.00
[   79.224141] uvcvideo: Found UVC 1.00 device Integrated Webcam (064e:a129)
[   79.240049] usbcore: registered new interface driver uvcvideo
[   79.240064] USB Video Class driver (v0.1.0)
[   79.315536] usbcore: registered new interface driver cdc_acm
[   79.316968] /build/buildd/linux-2.6.24/debian/build/custom-source-lpia/drivers/usb/class/cdc-acm.c: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
[   79.471902] usbcore: registered new interface driver cdc_ether
[   79.476106] usbcore: registered new interface driver mbm
[   79.990260] usb 4-2: USB disconnect, address 2
[   80.468220] wl: module license 'MIXED/Proprietary' taints kernel.
[   80.475476] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 16
[   80.475504] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   80.499011] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.91.9
[   90.895810] eth1: no IPv6 routers present
[  110.832171] usb 4-2: new full speed USB device using uhci_hcd and address 3
[  110.993098] usb 4-2: configuration #1 chosen from 1 choice
[  111.181083] usbcore: registered new interface driver usbserial
[  111.181679] /build/buildd/linux-2.6.24/debian/build/custom-source-lpia/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[  111.182675] usbcore: registered new interface driver usbserial_generic
[  111.182691] /build/buildd/linux-2.6.24/debian/build/custom-source-lpia/drivers/usb/serial/usb-serial.c: USB Serial Driver core
[  111.198792] /build/buildd/linux-2.6.24/debian/build/custom-source-lpia/drivers/usb/serial/usb-serial.c: USB Serial support registered for pl2303
[  111.199834] pl2303 4-2:1.0: pl2303 converter detected
[  111.200609] usb 4-2: pl2303 converter now attached to ttyUSB0
[  111.201179] usbcore: registered new interface driver pl2303
[  111.201192] /build/buildd/linux-2.6.24/debian/build/custom-source-lpia/drivers/usb/serial/pl2303.c: Prolific PL2303 USB to serial adaptor driver

---

