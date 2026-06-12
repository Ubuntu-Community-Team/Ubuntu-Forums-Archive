---
title: "Why can't I mount USB automatically?"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by Yanno on 2009-11-04
In newly installed 9.10,I have to run 
     sudo stop udev
     sudo start udev
to activate mounting each time I login.How to solve the problem???

---

### Post by ndefontenay on 2009-11-04
This is quite weird.
You could work around this however.

Just need to put those lines in a script and launch it on startup.

I don't know why your service needs a restart before it accepts to mount your usb devices properly.

My next advice would be reinstall your computer. I would go for the script personally.

You could also check launchpad.net to see if there's any bugs related to your problem.

Nico

---

### Post by philinux on 2009-11-04
> **Yanno said:**
> In newly installed 9.10,I have to run 
     sudo stop udev
     sudo start udev
to activate mounting each time I login.How to solve the problem???

When you plug something in does lsusb show the device?

Anything show up in dmesg?

---

### Post by Yanno on 2009-11-05
yanno@yanno-laptop:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 1bcf:0535 Sunplus Innovation Technology Inc. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 0951:1613 Kingston Technology 
Bus 002 Device 003: ID 04f2:b105 Chicony Electronics Co., Ltd 
Bus 002 Device 004: ID 1164:1f08 YUAN High-Tech Development Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
yanno@yanno-laptop:~$ 


[    0.590162] msgmni has been set to 1705
[    0.590354] alg: No test for stdrng (krng)
[    0.590368] io scheduler noop registered
[    0.590370] io scheduler anticipatory registered
[    0.590372] io scheduler deadline registered
[    0.590413] io scheduler cfq registered (default)
[    0.590823] pci 0000:01:00.0: Boot video device
[    0.590949]   alloc irq_desc for 24 on node -1
[    0.590951]   alloc kstat_irqs on node -1
[    0.590959] pcieport-driver 0000:00:01.0: irq 24 for MSI/MSI-X
[    0.590966] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    0.591102]   alloc irq_desc for 25 on node -1
[    0.591104]   alloc kstat_irqs on node -1
[    0.591113] pcieport-driver 0000:00:1c.0: irq 25 for MSI/MSI-X
[    0.591124] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    0.591281]   alloc irq_desc for 26 on node -1
[    0.591283]   alloc kstat_irqs on node -1
[    0.591291] pcieport-driver 0000:00:1c.1: irq 26 for MSI/MSI-X
[    0.591303] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    0.591460]   alloc irq_desc for 27 on node -1
[    0.591462]   alloc kstat_irqs on node -1
[    0.591471] pcieport-driver 0000:00:1c.2: irq 27 for MSI/MSI-X
[    0.591482] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    0.591589] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.591957] pciehp: Using ACPI for slot detection.
[    0.592092] pciehp 0000:00:1c.2:pcie04: HPC vendor_id 8086 device_id 2944 ss_vid 0 ss_did 0
[    0.592138] pciehp 0000:00:1c.2:pcie04: service driver pciehp loaded
[    0.592146] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.592340] ACPI: AC Adapter [AC0] (on-line)
[    0.592398] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.592401] ACPI: Power Button [PWRF]
[    0.592469] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    0.592712] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.603393] ACPI: Lid Switch [LID]
[    0.603450] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.603457] ACPI: Sleep Button [SLPB]
[    0.604551] ACPI: SSDT 7fa62c98 00223 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.605313] ACPI: SSDT 7fa60798 006F1 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.606923] Monitor-Mwait will be used to enter C-1 state
[    0.606948] Monitor-Mwait will be used to enter C-2 state
[    0.606966] Monitor-Mwait will be used to enter C-3 state
[    0.606973] Marking TSC unstable due to TSC halts in idle
[    0.606994] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    0.607021] processor LNXCPU:00: registered as cooling_device0
[    0.607025] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.607517] ACPI: SSDT 7fa61e18 001CF (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.608121] ACPI: SSDT 7fa60f18 0008D (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.609898] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    0.609920] processor LNXCPU:01: registered as cooling_device1
[    0.609924] ACPI: Processor [CPU1] (supports 8 throttling states)
[    0.624328] thermal LNXTHERM:01: registered as thermal_zone0
[    0.624336] ACPI: Thermal Zone [THRM] (31 C)
[    0.624396] isapnp: Scanning for PnP cards...
[    0.692320] ACPI: Battery Slot [BAT0] (battery present)
[    0.981438] isapnp: No Plug & Play device found
[    0.982622] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.983990] brd: module loaded
[    0.984427] loop: module loaded
[    0.984498] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.984574] ahci 0000:00:1f.2: version 3.0
[    0.984590]   alloc irq_desc for 19 on node -1
[    0.984592]   alloc kstat_irqs on node -1
[    0.984599] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.984634]   alloc irq_desc for 28 on node -1
[    0.984635]   alloc kstat_irqs on node -1
[    0.984645] ahci 0000:00:1f.2: irq 28 for MSI/MSI-X
[    0.984684] ahci: SSS flag set, parallel bus scan disabled
[    0.984715] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x3 impl SATA mode
[    0.984718] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag led clo pio slum part ems 
[    0.984724] ahci 0000:00:1f.2: setting latency timer to 64
[    0.993075] scsi0 : ahci
[    0.993170] scsi1 : ahci
[    0.993222] scsi2 : ahci
[    0.993275] scsi3 : ahci
[    0.993462] ata1: SATA max UDMA/133 abar m2048@0xd3d04000 port 0xd3d04100 irq 28
[    0.993466] ata2: SATA max UDMA/133 irq_stat 0x00400040, connection status changed irq 28
[    0.993468] ata3: DUMMY
[    0.993469] ata4: DUMMY
[    0.994381] Fixed MDIO Bus: probed
[    0.994415] PPP generic driver version 2.4.2
[    0.994509] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.994530] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    0.994545] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.994549] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.994599] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.998513] ehci_hcd 0000:00:1a.7: debug port 1
[    0.998520] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.998536] ehci_hcd 0000:00:1a.7: irq 19, io mem 0xd3d04c00
[    1.013012] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    1.013081] usb usb1: configuration #1 chosen from 1 choice
[    1.013110] hub 1-0:1.0: USB hub found
[    1.013117] hub 1-0:1.0: 6 ports detected
[    1.013183]   alloc irq_desc for 23 on node -1
[    1.013185]   alloc kstat_irqs on node -1
[    1.013191] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.013202] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.013205] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.013237] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    1.017132] ehci_hcd 0000:00:1d.7: debug port 1
[    1.017138] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    1.017152] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xd3d04800
[    1.032017] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.032085] usb usb2: configuration #1 chosen from 1 choice
[    1.032111] hub 2-0:1.0: USB hub found
[    1.032117] hub 2-0:1.0: 6 ports detected
[    1.032179] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.032197] uhci_hcd: USB Universal Host Controller Interface driver
[    1.032223] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.032230] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.032233] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    1.032270] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    1.032307] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000d0c0
[    1.032382] usb usb3: configuration #1 chosen from 1 choice
[    1.032409] hub 3-0:1.0: USB hub found
[    1.032415] hub 3-0:1.0: 2 ports detected
[    1.032463]   alloc irq_desc for 21 on node -1
[    1.032465]   alloc kstat_irqs on node -1
[    1.032469] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.032476] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    1.032479] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    1.032508] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    1.032543] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000d0a0
[    1.032622] usb usb4: configuration #1 chosen from 1 choice
[    1.032647] hub 4-0:1.0: USB hub found
[    1.032653] hub 4-0:1.0: 2 ports detected
[    1.032700] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    1.032707] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    1.032711] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    1.032738] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    1.032768] uhci_hcd 0000:00:1a.2: irq 19, io base 0x0000d080
[    1.032847] usb usb5: configuration #1 chosen from 1 choice
[    1.032872] hub 5-0:1.0: USB hub found
[    1.032878] hub 5-0:1.0: 2 ports detected
[    1.032928] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.032935] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.032938] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.032967] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    1.032995] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000d060
[    1.033087] usb usb6: configuration #1 chosen from 1 choice
[    1.033112] hub 6-0:1.0: USB hub found
[    1.033118] hub 6-0:1.0: 2 ports detected
[    1.033169] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.033175] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.033179] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.033209] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    1.033237] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d040
[    1.033310] usb usb7: configuration #1 chosen from 1 choice
[    1.033334] hub 7-0:1.0: USB hub found
[    1.033340] hub 7-0:1.0: 2 ports detected
[    1.033390] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.033397] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.033400] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.033428] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    1.033464] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d020
[    1.033538] usb usb8: configuration #1 chosen from 1 choice
[    1.033563] hub 8-0:1.0: USB hub found
[    1.033569] hub 8-0:1.0: 2 ports detected
[    1.033673] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.037668] i8042.c: Detected active multiplexing controller, rev 1.1.
[    1.039272] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.039277] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.039280] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.039283] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.039286] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.039339] mice: PS/2 mouse device common for all mice
[    1.039445] rtc_cmos 00:07: RTC can wake from S4
[    1.039476] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    1.039508] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    1.039610] device-mapper: uevent: version 1.0.3
[    1.039705] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    1.039792] device-mapper: multipath: version 1.1.0 loaded
[    1.039794] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.039916] EISA: Probing bus 0 at eisa.0
[    1.039953] EISA: Detected 0 cards.
[    1.040128] cpuidle: using governor ladder
[    1.040246] cpuidle: using governor menu
[    1.040735] TCP cubic registered
[    1.040884] NET: Registered protocol family 10
[    1.041329] lo: Disabled Privacy Extensions
[    1.041652] NET: Registered protocol family 17
[    1.041670] Bluetooth: L2CAP ver 2.13
[    1.041672] Bluetooth: L2CAP socket layer initialized
[    1.041675] Bluetooth: SCO (Voice Link) ver 0.6
[    1.041677] Bluetooth: SCO socket layer initialized
[    1.041703] Bluetooth: RFCOMM TTY layer initialized
[    1.041706] Bluetooth: RFCOMM socket layer initialized
[    1.041708] Bluetooth: RFCOMM ver 1.11
[    1.043106] Using IPI No-Shortcut mode
[    1.043174] PM: Resume from disk failed.
[    1.043186] registered taskstats version 1
[    1.043304]   Magic number: 1:41:826
[    1.043406] rtc_cmos 00:07: setting system clock to 2009-11-05 08:50:33 UTC (1257411033)
[    1.043409] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.043411] EDD information not available.
[    1.077718] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.320061] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.321127] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[    1.321188] ata1.00: ACPI cmd ef/10:06:00:00:00:a0 succeeded
[    1.321191] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    1.321545] ata1.00: ATA-8: ST9250827AS, 3.AAB, max UDMA/133
[    1.321548] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.322642] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[    1.322707] ata1.00: ACPI cmd ef/10:06:00:00:00:a0 succeeded
[    1.322710] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    1.323094] ata1.00: configured for UDMA/133
[    1.323230] scsi 0:0:0:0: Direct-Access     ATA      ST9250827AS      3.AA PQ: 0 ANSI: 5
[    1.323349] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.323387] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.323430] sd 0:0:0:0: [sda] Write Protect is off
[    1.323433] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.323456] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.323573]  sda: sda1 sda2
[    1.373666] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.400049] usb 2-5: new high speed USB device using ehci_hcd and address 3
[    1.500040] Clocksource tsc unstable (delta = -416766546 ns)
[    1.637633] usb 2-5: configuration #1 chosen from 1 choice
[    1.748040] usb 2-6: new high speed USB device using ehci_hcd and address 4
[    1.881033] usb 2-6: configuration #1 chosen from 1 choice
[    2.044052] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.058868] ata2.00: ACPI cmd ef/10:06:00:00:00:a0 succeeded
[    2.058872] ata2.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    2.059489] ata2.00: ACPI cmd ef/90:05:00:00:00:a0 succeeded
[    2.073473] ata2.00: ATAPI: Optiarc DVD RW AD-7560S, S805, max UDMA/100, ATAPI AN
[    2.088033] ata2.00: ACPI cmd ef/10:06:00:00:00:a0 succeeded
[    2.088037] ata2.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    2.088678] ata2.00: ACPI cmd ef/90:05:00:00:00:a0 succeeded
[    2.102765] ata2.00: configured for UDMA/100
[    2.104259] scsi 1:0:0:0: CD-ROM            Optiarc  DVD RW AD-7560S  S805 PQ: 0 ANSI: 5
[    2.107132] sr0: scsi3-mmc drive: 62x/62x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.107135] Uniform CD-ROM driver Revision: 3.20
[    2.107216] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.107260] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.107355] Freeing unused kernel memory: 540k freed
[    2.107655] Write protecting the kernel text: 4568k
[    2.107708] Write protecting the kernel read-only data: 1836k
[    2.125086] usb 6-1: new low speed USB device using uhci_hcd and address 2
[    2.232037] ACPI Warning: _BQC returned an invalid level 20090521 video-629
[    2.246574] Linux agpgart interface v0.103
[    2.280428] tg3.c:v3.99 (April 20, 2009)
[    2.280493] tg3 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.280509] tg3 0000:02:00.0: setting latency timer to 64
[    2.303533] tg3 0000:02:00.0: PME# disabled
[    2.323022] acpi device:09: registered as cooling_device2
[    2.323178] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:05/device:06/input/input5
[    2.323217] ACPI: Video Device [VGA1] (multi-head: yes  rom: no  post: no)
[    2.328164] usb 6-1: configuration #1 chosen from 1 choice
[    2.343617]   alloc irq_desc for 20 on node -1
[    2.343620]   alloc kstat_irqs on node -1
[    2.343628] ohci1394 0000:07:03.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.347551] usbcore: registered new interface driver hiddev
[    2.369461] input: 2.4GHz 2way RF Mouse Receiver as /devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1:1.0/input/input6
[    2.369575] generic-usb 0003:1BCF:0535.0001: input,hiddev96,hidraw0: USB HID v1.11 Mouse [2.4GHz 2way RF Mouse Receiver] on usb-0000:00:1d.0-1/input0
[    2.369592] usbcore: registered new interface driver usbhid
[    2.369598] usbhid: v2.6:USB HID core driver
[    2.399061] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[20]  MMIO=[d3c00000-d3c007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    2.677905] eth0: Tigon3 [partno(BCM95906) rev c002] (PCI Express) MAC address 00:23:54:67:17:8d
[    2.677909] eth0: attached PHY is 5906 (10/100Base-TX Ethernet) (WireSpeed[0])
[    2.677912] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    2.677914] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    3.712450] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001e8c0001a0f68e]
[    4.053130] PM: Starting manual resume from disk
[    4.053134] PM: Resume from partition 8:1
[    4.053136] PM: Checking hibernation image.
[    4.053287] PM: Resume from disk failed.
[    4.071452] EXT4-fs (sda2): barriers enabled
[    4.088687] kjournald2 starting: pid 414, dev sda2:8, commit interval 5 seconds
[    4.088712] EXT4-fs (sda2): delayed allocation enabled
[    4.088716] EXT4-fs: file extents enabled
[    4.106588] EXT4-fs: mballoc enabled
[    4.106604] EXT4-fs (sda2): mounted filesystem with ordered data mode
[    4.817374] type=1505 audit(1257411037.272:2): operation="profile_load" pid=437 name=/usr/share/gdm/guest-session/Xsession
[    4.819838] type=1505 audit(1257411037.272:3): operation="profile_load" pid=438 name=/sbin/dhclient3
[    4.820561] type=1505 audit(1257411037.272:4): operation="profile_load" pid=438 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    4.820955] type=1505 audit(1257411037.272:5): operation="profile_load" pid=438 name=/usr/lib/connman/scripts/dhclient-script
[    4.861740] type=1505 audit(1257411037.317:6): operation="profile_load" pid=439 name=/usr/bin/evince
[    4.872987] type=1505 audit(1257411037.328:7): operation="profile_load" pid=439 name=/usr/bin/evince-previewer
[    4.879637] type=1505 audit(1257411037.332:8): operation="profile_load" pid=439 name=/usr/bin/evince-thumbnailer
[    4.902675] type=1505 audit(1257411037.356:9): operation="profile_load" pid=441 name=/usr/lib/cups/backend/cups-pdf
[    6.276483] Adding 4996172k swap on /dev/sda1.  Priority:-1 extents:1 across:4996172k 
[    6.452249] udev: starting version 147
[    7.213423] EXT4-fs (sda2): internal journal on sda2:8
[    8.514809] ip_tables: (C) 2000-2006 Netfilter Core Team
[    8.802639] asus_laptop: Asus Laptop Support version 0.42
[    8.808210] asus_laptop: BSTS called, 0xff7f returned
[    8.808744] input: Asus Laptop extra buttons as /devices/virtual/input/input7
[    8.808990] asus_laptop: Brightness ignored, must be controlled by ACPI video driver
[    8.835598] lp: driver loaded but no devices found
[    9.031155] ricoh-mmc: Ricoh MMC Controller disabling driver
[    9.031158] ricoh-mmc: Copyright(c) Philip Langdale
[    9.031187] ricoh-mmc: Ricoh MMC controller found at 0000:07:03.2 [1180:0843] (rev 12)
[    9.031204] ricoh-mmc: Controller is now disabled.
[    9.066224] sdhci: Secure Digital Host Controller Interface driver
[    9.066227] sdhci: Copyright(c) Pierre Ossman
[   10.310435] nvidia: module license 'NVIDIA' taints kernel.
[   10.310440] Disabling lock debugging due to kernel taint
[   10.358516] __ratelimit: 6 callbacks suppressed
[   10.358519] type=1505 audit(1257411042.812:12): operation="profile_replace" pid=812 name=/usr/share/gdm/guest-session/Xsession
[   10.360356] type=1505 audit(1257411042.816:13): operation="profile_replace" pid=813 name=/sbin/dhclient3
[   10.361095] type=1505 audit(1257411042.816:14): operation="profile_replace" pid=813 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   10.361493] type=1505 audit(1257411042.816:15): operation="profile_replace" pid=813 name=/usr/lib/connman/scripts/dhclient-script
[   10.365725] type=1505 audit(1257411042.820:16): operation="profile_replace" pid=814 name=/usr/bin/evince
[   10.376981] type=1505 audit(1257411042.832:17): operation="profile_replace" pid=814 name=/usr/bin/evince-previewer
[   10.383767] type=1505 audit(1257411042.836:18): operation="profile_replace" pid=814 name=/usr/bin/evince-thumbnailer
[   10.393236] type=1505 audit(1257411042.848:19): operation="profile_replace" pid=816 name=/usr/lib/cups/backend/cups-pdf
[   10.394081] type=1505 audit(1257411042.848:20): operation="profile_replace" pid=816 name=/usr/sbin/cupsd
[   10.396692] type=1505 audit(1257411042.852:21): operation="profile_replace" pid=817 name=/usr/sbin/tcpdump
[   10.563825] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.563847] nvidia 0000:01:00.0: setting latency timer to 64
[   10.564029] NVRM: loading NVIDIA UNIX x86 Kernel Module  185.18.36  Fri Aug 14 17:18:04 PDT 2009
[   10.599981] sdhci-pci 0000:07:03.1: SDHCI controller found [1180:0822] (rev 22)
[   10.600001] sdhci-pci 0000:07:03.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[   10.601044] sdhci-pci 0000:07:03.1: Will use DMA mode even though HW doesn't fully claim to support it.
[   10.602093] Registered led device: mmc0::
[   10.603123] mmc0: SDHCI controller on PCI [0000:07:03.1] using DMA
[   10.611149] Linux video capture interface: v2.00
[   10.612253] lib80211: common routines for IEEE802.11 drivers
[   10.612256] lib80211_crypt: registered algorithm 'NULL'
[   10.617556] wl 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   10.617571] wl 0000:03:00.0: setting latency timer to 64
[   10.701232] uvcvideo: Found UVC 1.00 device Lenovo EasyCamera (04f2:b105)
[   10.705395] input: Lenovo EasyCamera as /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/input/input8
[   10.705446] usbcore: registered new interface driver uvcvideo
[   10.705450] USB Video Class driver (v0.1.0)
[   10.777523] lib80211_crypt: registered algorithm 'TKIP'
[   10.778914] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.91.9
[   11.197512] dib0700: loaded with support for 9 different device-types
[   11.197717] dvb-usb: found a 'YUAN High-Tech STK7700PH' in cold state, will try to load a firmware
[   11.197723] usb 2-6: firmware: requesting dvb-usb-dib0700-1.20.fw
[   11.357474] Synaptics Touchpad, model: 1, fw: 6.2, id: 0xa580b1, caps: 0xa04711/0x200000
[   11.398137] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input9
[   11.666768] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw'
[   11.877323] dib0700: firmware started successfully.
[   12.384066] dvb-usb: found a 'YUAN High-Tech STK7700PH' in warm state.
[   12.384122] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   12.384320] DVB: registering new adapter (YUAN High-Tech STK7700PH)
[   12.627956] DVB: registering adapter 0 frontend 0 (DiBcom 7000PC)...
[   13.496969]   alloc irq_desc for 22 on node -1
[   13.496972]   alloc kstat_irqs on node -1
[   13.496979] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   13.497041] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   13.846839] hda_codec: Unknown model for ALC1200, trying auto-probe from BIOS...
[   13.847130] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input10
[   13.849784] xc2028 1-0061: creating new instance
[   13.849787] xc2028 1-0061: type set to XCeive xc2028/xc3028 tuner
[   13.849861] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1d.7/usb2/2-6/input/input11
[   13.849897] dvb-usb: schedule remote query interval to 50 msecs.
[   13.849900] dvb-usb: YUAN High-Tech STK7700PH successfully initialized and connected.
[   13.853717] usbcore: registered new interface driver dvb_usb_dib0700
[   17.656115] ppdev: user-space parallel port driver
[   18.401685] tg3 0000:02:00.0: PME# disabled
[   18.401871]   alloc irq_desc for 29 on node -1
[   18.401873]   alloc kstat_irqs on node -1
[   18.401903] tg3 0000:02:00.0: irq 29 for MSI/MSI-X
[   18.457204] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.449547] sr 1:0:0:0: [sr0] Unhandled sense code
[   26.449551] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   26.449555] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
[   26.449559] sr 1:0:0:0: [sr0] Add. Sense: No seek complete
[   26.449564] end_request: I/O error, dev sr0, sector 9064064
[   26.449568] Buffer I/O error on device sr0, logical block 1133008
[   29.564025] eth1: no IPv6 routers present
[   31.460110] sr 1:0:0:0: [sr0] Unhandled sense code
[   31.460114] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   31.460118] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
[   31.460122] sr 1:0:0:0: [sr0] Add. Sense: No seek complete
[   31.460127] end_request: I/O error, dev sr0, sector 9064064
[   31.460132] Buffer I/O error on device sr0, logical block 1133008
[   36.322851] sr 1:0:0:0: [sr0] Unhandled sense code
[   36.322855] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   36.322859] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
[   36.322863] sr 1:0:0:0: [sr0] Add. Sense: No seek complete
[   36.322868] end_request: I/O error, dev sr0, sector 9064240
[   36.322873] Buffer I/O error on device sr0, logical block 1133030
[   41.280686] sr 1:0:0:0: [sr0] Unhandled sense code
[   41.280690] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   41.280694] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
[   41.280698] sr 1:0:0:0: [sr0] Add. Sense: No seek complete
[   41.280703] end_request: I/O error, dev sr0, sector 9064240
[   41.280709] Buffer I/O error on device sr0, logical block 1133030
[   47.200398] sr 1:0:0:0: [sr0] Unhandled sense code
[   47.200402] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   47.200406] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
[   47.200410] sr 1:0:0:0: [sr0] Add. Sense: No seek complete
[   47.200415] end_request: I/O error, dev sr0, sector 9064064
[   47.200420] Buffer I/O error on device sr0, logical block 1133008
[   52.270407] sr 1:0:0:0: [sr0] Unhandled sense code
[   52.270411] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   52.270415] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
[   52.270419] sr 1:0:0:0: [sr0] Add. Sense: No seek complete
[   52.270424] end_request: I/O error, dev sr0, sector 9064064
[   52.270428] Buffer I/O error on device sr0, logical block 1133008
[   65.912016] sr 1:0:0:0: [sr0] Unhandled sense code
[   65.912020] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   65.912024] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
[   65.912028] sr 1:0:0:0: [sr0] Add. Sense: No seek complete
[   65.912033] end_request: I/O error, dev sr0, sector 9064008
[   65.912039] Buffer I/O error on device sr0, logical block 1133001
[   65.912043] Buffer I/O error on device sr0, logical block 1133002
[   65.912046] Buffer I/O error on device sr0, logical block 1133003
[   65.912049] Buffer I/O error on device sr0, logical block 1133004
[   70.808300] sr 1:0:0:0: [sr0] Unhandled sense code
[   70.808304] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   70.808308] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
[   70.808312] sr 1:0:0:0: [sr0] Add. Sense: No seek complete
[   70.808317] end_request: I/O error, dev sr0, sector 9063856
[   70.808322] Buffer I/O error on device sr0, logical block 1132982
[   70.808327] Buffer I/O error on device sr0, logical block 1132983
[   75.746124] sr 1:0:0:0: [sr0] Unhandled sense code
[   75.746127] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   75.746131] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
[   75.746136] sr 1:0:0:0: [sr0] Add. Sense: No seek complete
[   75.746141] end_request: I/O error, dev sr0, sector 9063856
[   75.746145] Buffer I/O error on device sr0, logical block 1132982
[   76.565618] UDF-fs: Partition marked readonly; forcing readonly mount
[   76.606957] UDF-fs INFO UDF: Mounting volume 'xyy02', timestamp 2005/11/15 23:30 (11e0)
[  567.052065] usb 2-3: new high speed USB device using ehci_hcd and address 5
[  567.186547] usb 2-3: configuration #1 chosen from 1 choice
[  567.262744] Initializing USB Mass Storage driver...
[  567.263203] scsi4 : SCSI emulation for USB Mass Storage devices
[  567.263422] usbcore: registered new interface driver usb-storage
[  567.263427] USB Mass Storage support registered.
[  567.266905] usb-storage: device found at 5
[  567.266910] usb-storage: waiting for device to settle before scanning
[  572.264400] usb-storage: device scan complete
[  572.265105] scsi 4:0:0:0: Direct-Access     Kingston DT 101 II        PMAP PQ: 0 ANSI: 0 CCS
[  572.265820] sd 4:0:0:0: Attached scsi generic sg2 type 0
[  573.267677] sd 4:0:0:0: [sdb] 7936000 512-byte logical blocks: (4.06 GB/3.78 GiB)
[  573.268291] sd 4:0:0:0: [sdb] Write Protect is off
[  573.268296] sd 4:0:0:0: [sdb] Mode Sense: 23 00 00 00
[  573.268300] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  573.270416] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  573.270423]  sdb: sdb1
[  573.329559] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  573.329568] sd 4:0:0:0: [sdb] Attached SCSI removable disk
yanno@yanno-laptop:~$ 



I just run the command,there're too many lines about that,I couldn't understand.
When I open "Disk Utility" in Administration,It shows Kingston DT 101II,no media detected.

---

### Post by Yanno on 2009-11-05
> **ndefontenay said:**
> This is quite weird.
You could work around this however.

Just need to put those lines in a script and launch it on startup.

I don't know why your service needs a restart before it accepts to mount your usb devices properly.

My next advice would be reinstall your computer. I would go for the script personally.

You could also check launchpad.net to see if there's any bugs related to your problem.

Nico


Actually I reinstalled it before,it isn't solved.And there are many many people have problems about mountings in Ubuntu9.10 which didn't occured in 9.04.Now I still have to run the command when I need to USE a USB...

I just wonder how to make the script that could be launched on startup.

---

### Post by zwygart on 2009-11-05
How to make/launch script on startup

1. Write the script   The commands you wrote earlier.
2. Place it in a accessible place
3. Make it executable chmod a+x yourscript
4. Add a entry in /etc/rc.local
This is the file wich is executed at end of startup.
Append a line wich is the absolute path to your script.

---

