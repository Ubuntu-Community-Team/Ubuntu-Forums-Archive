---
title: "Lost Wireless Connection after Upgrading to Ubuntu 10.04"
date: 2010-05-13
forum: New to Ubuntu
---

### Post by RedStarYellowSun on 2010-05-13
I just upgraded my Mom's laptop from Ubuntu 9.10 to 10.04.
The problem is that, now, she can't connect to our wireless connection. It can't even detect our wireless router just beside it.

I looked for some [directions]("http://ubuntuforums.org/showthread.php?p=6183681") to fix it, but I'm stuck at step 5 because I can't I can't identify the Wireless module ("wlan_module_name"). There are so many modules, how do I find it?

Thanks for your time.

Take care,
RedStarYellowSun

---

### Post by sir_nasty on 2010-05-13
can you post for us the information from that directions link that you can get? What kind of latptop, what wireless card, what's loaded etc.... heck just go to terminal type "dmesg" and "ifconfig" then post the results and that's typically a good starting point for someone to help you.

---

### Post by bredman on 2010-05-13
To find the wireless hardware you are using, use command
lshw

To find which modules are loaded, use command
lsmod

To find all modules available in the system, use command
modprobe -l

---

### Post by bredman on 2010-05-13
I may have misread your original post.

If you know the name of your hardware (from the lshw command) just search the web for the words Ubuntu, module, and your hardware name.

---

### Post by RedStarYellowSun on 2010-05-13
> **sir_nasty said:**
> can you post for us the information from that directions link that you can get? What kind of latptop, what wireless card, what's loaded etc.... heck just go to terminal type "dmesg" and "ifconfig" then post the results and that's typically a good starting point for someone to help you.

Problem: I tried "dmesg", but it gave so much information that Terminal cuts the information short. Here is what scrolling up all thew way gives:```
[    0.272944] pci_bus 0000:15: resource 0 io:  [0x7000-0xafff]
[    0.272946] pci_bus 0000:15: resource 1 mem: [0xf8300000-0xfbffffff]
[    0.272948] pci_bus 0000:15: resource 2 pref mem [0xf4000000-0xf7ffffff]
[    0.272950] pci_bus 0000:15: resource 3 io:  [0x00-0xffff]
[    0.272952] pci_bus 0000:15: resource 4 mem: [0x000000-0xffffffff]
[    0.272954] pci_bus 0000:16: resource 0 io:  [0x7000-0x70ff]
[    0.272956] pci_bus 0000:16: resource 1 io:  [0x7400-0x74ff]
[    0.272958] pci_bus 0000:16: resource 2 pref mem [0xf4000000-0xf7ffffff]
[    0.272961] pci_bus 0000:16: resource 3 mem: [0x80000000-0x83ffffff]
[    0.272997] NET: Registered protocol family 2
[    0.273088] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.273387] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.273873] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.274109] TCP: Hash tables configured (established 131072 bind 65536)
[    0.274111] TCP reno registered
[    0.274182] NET: Registered protocol family 1
[    0.274203] pci 0000:00:02.0: Boot video device
[    0.274426] Simple Boot Flag at 0x35 set to 0x1
[    0.274577] cpufreq-nforce2: No nForce2 chipset.
[    0.274602] Scanning for low memory corruption every 60 seconds
[    0.274706] audit: initializing netlink socket (disabled)
[    0.274715] type=2000 audit(1273786572.272:1): initialized
[    0.283152] highmem bounce pool size: 64 pages
[    0.283157] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.284475] VFS: Disk quotas dquot_6.5.2
[    0.284525] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.285009] fuse init (API version 7.13)
[    0.285088] msgmni has been set to 1691
[    0.285278] alg: No test for stdrng (krng)
[    0.285326] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.285329] io scheduler noop registered
[    0.285330] io scheduler anticipatory registered
[    0.285332] io scheduler deadline registered
[    0.285364] io scheduler cfq registered (default)
[    0.285587]   alloc irq_desc for 24 on node -1
[    0.285589]   alloc kstat_irqs on node -1
[    0.285610] pcieport 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.285632] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.285916]   alloc irq_desc for 25 on node -1
[    0.285918]   alloc kstat_irqs on node -1
[    0.285933] pcieport 0000:00:1c.1: irq 25 for MSI/MSI-X
[    0.285952] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.286191]   alloc irq_desc for 26 on node -1
[    0.286192]   alloc kstat_irqs on node -1
[    0.286209] pcieport 0000:00:1c.2: irq 26 for MSI/MSI-X
[    0.286228] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.286452]   alloc irq_desc for 27 on node -1
[    0.286454]   alloc kstat_irqs on node -1
[    0.286463] pcieport 0000:00:1c.3: irq 27 for MSI/MSI-X
[    0.286483] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.286718]   alloc irq_desc for 28 on node -1
[    0.286720]   alloc kstat_irqs on node -1
[    0.286734] pcieport 0000:00:1c.4: irq 28 for MSI/MSI-X
[    0.286756] pcieport 0000:00:1c.4: setting latency timer to 64
[    0.286888] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.287319] pciehp: Using ACPI for slot detection.
[    0.287441] pciehp 0000:00:1c.3:pcie04: HPC vendor_id 8086 device_id 2845 ss_vid 0 ss_did 0
[    0.287509] pciehp 0000:00:1c.3:pcie04: service driver pciehp loaded
[    0.287525] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.287768] ACPI: AC Adapter [AC] (on-line)
[    0.287830] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.288022] ACPI: Lid Switch [LID]
[    0.288060] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.288068] ACPI: Sleep Button [SLPB]
[    0.288115] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.288117] ACPI: Power Button [PWRF]
[    0.288719] ACPI: SSDT 7d6e1b32 00306 (v01  PmRef  Cpu0Ist 00000100 INTL 20050513)
[    0.289376] ACPI: SSDT 7d6e1ebd 0085E (v01  PmRef  Cpu0Cst 00000100 INTL 20050513)
[    0.291843] Monitor-Mwait will be used to enter C-1 state
[    0.291870] Monitor-Mwait will be used to enter C-2 state
[    0.291891] Monitor-Mwait will be used to enter C-3 state
[    0.291932] processor LNXCPU:00: registered as cooling_device0
[    0.292253] ACPI: SSDT 7d6e1a6a 000C8 (v01  PmRef  Cpu1Ist 00000100 INTL 20050513)
[    0.292669] ACPI: SSDT 7d6e1e38 00085 (v01  PmRef  Cpu1Cst 00000100 INTL 20050513)
[    0.305289] processor LNXCPU:01: registered as cooling_device1
[    0.310220] thermal LNXTHERM:01: registered as thermal_zone0
[    0.310227] ACPI: Thermal Zone [THM0] (56 C)
[    0.311572] thermal LNXTHERM:02: registered as thermal_zone1
[    0.311579] ACPI: Thermal Zone [THM1] (49 C)
[    0.312854] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.314045] brd: module loaded
[    0.314438] loop: module loaded
[    0.314510] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.314592] ata_piix 0000:00:1f.1: version 2.13
[    0.314607] ata_piix 0000:00:1f.1: PCI INT C -> GSI 16 (level, low) -> IRQ 16
[    0.314658] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.314750] scsi0 : ata_piix
[    0.314813] scsi1 : ata_piix
[    0.315431] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1c00 irq 14
[    0.315433] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1c08 irq 15
[    0.315717] Fixed MDIO Bus: probed
[    0.315746] PPP generic driver version 2.4.2
[    0.315776] tun: Universal TUN/TAP device driver, 1.6
[    0.315778] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.315846] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.316041] ehci_hcd 0000:00:1a.7: power state changed by ACPI to D0
[    0.316053] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.316069] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.316075] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.316111] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.320034] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.320051] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xfe226c00
[    0.324398] isapnp: Scanning for PnP cards...
[    0.345019] ACPI: Battery Slot [BAT0] (battery present)
[    0.360363] Freeing initrd memory: 7772k freed
[    0.364393] ata2: port disabled. ignoring.
[    0.374417] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.374559] usb usb1: configuration #1 chosen from 1 choice
[    0.374593] hub 1-0:1.0: USB hub found
[    0.374604] hub 1-0:1.0: 4 ports detected
[    0.374953] ehci_hcd 0000:00:1d.7: power state changed by ACPI to D0
[    0.374969]   alloc irq_desc for 19 on node -1
[    0.374971]   alloc kstat_irqs on node -1
[    0.374977] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.375006] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.375011] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.375055] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.375100] ehci_hcd 0000:00:1d.7: debug port 1
[    0.378990] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.379010] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xfe227000
[    0.393017] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.393088] usb usb2: configuration #1 chosen from 1 choice
[    0.393113] hub 2-0:1.0: USB hub found
[    0.393120] hub 2-0:1.0: 6 ports detected
[    0.393190] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.393207] uhci_hcd: USB Universal Host Controller Interface driver
[    0.393252] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.393263] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.393268] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.393294] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.393335] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00001860
[    0.393417] usb usb3: configuration #1 chosen from 1 choice
[    0.393437] hub 3-0:1.0: USB hub found
[    0.393444] hub 3-0:1.0: 2 ports detected
[    0.393653] uhci_hcd 0000:00:1a.1: power state changed by ACPI to D0
[    0.393659] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.393669] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.393675] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.393702] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.393738] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001880
[    0.393820] usb usb4: configuration #1 chosen from 1 choice
[    0.393841] hub 4-0:1.0: USB hub found
[    0.393848] hub 4-0:1.0: 2 ports detected
[    0.394053] uhci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[    0.394059] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.394069] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.394074] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.394104] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    0.394140] uhci_hcd 0000:00:1d.0: irq 16, io base 0x000018a0
[    0.394222] usb usb5: configuration #1 chosen from 1 choice
[    0.394243] hub 5-0:1.0: USB hub found
[    0.394249] hub 5-0:1.0: 2 ports detected
[    0.394290]   alloc irq_desc for 17 on node -1
[    0.394292]   alloc kstat_irqs on node -1
[    0.394295] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.394303] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.394309] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.394334] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    0.394374] uhci_hcd 0000:00:1d.1: irq 17, io base 0x000018c0
[    0.394453] usb usb6: configuration #1 chosen from 1 choice
[    0.394474] hub 6-0:1.0: USB hub found
[    0.394481] hub 6-0:1.0: 2 ports detected
[    0.394681] uhci_hcd 0000:00:1d.2: power state changed by ACPI to D0
[    0.394687]   alloc irq_desc for 18 on node -1
[    0.394689]   alloc kstat_irqs on node -1
[    0.394693] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.394703] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.394708] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.394740] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    0.394778] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018e0
[    0.394865] usb usb7: configuration #1 chosen from 1 choice
[    0.394886] hub 7-0:1.0: USB hub found
[    0.394892] hub 7-0:1.0: 2 ports detected
[    0.394986] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    0.403729] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.403735] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.403839] mice: PS/2 mouse device common for all mice
[    0.403958] rtc_cmos 00:07: RTC can wake from S4
[    0.403992] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    0.404031] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.404115] device-mapper: uevent: version 1.0.3
[    0.404198] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.404259] device-mapper: multipath: version 1.1.0 loaded
[    0.404261] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.404356] EISA: Probing bus 0 at eisa.0
[    0.404364] Cannot allocate resource for EISA slot 1
[    0.404366] Cannot allocate resource for EISA slot 2
[    0.404368] Cannot allocate resource for EISA slot 3
[    0.404370] Cannot allocate resource for EISA slot 4
[    0.404371] Cannot allocate resource for EISA slot 5
[    0.404373] Cannot allocate resource for EISA slot 6
[    0.404375] Cannot allocate resource for EISA slot 7
[    0.404376] Cannot allocate resource for EISA slot 8
[    0.404378] EISA: Detected 0 cards.
[    0.404507] cpuidle: using governor ladder
[    0.404604] cpuidle: using governor menu
[    0.404985] TCP cubic registered
[    0.405134] NET: Registered protocol family 10
[    0.405532] lo: Disabled Privacy Extensions
[    0.405813] NET: Registered protocol family 17
[    0.406481] Using IPI No-Shortcut mode
[    0.406538] PM: Resume from disk failed.
[    0.406549] registered taskstats version 1
[    0.407350]   Magic number: 10:778:651
[    0.407441] rtc_cmos 00:07: setting system clock to 2010-05-13 21:36:13 UTC (1273786573)
[    0.407444] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.407445] EDD information not available.
[    0.410099] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.541706] ata1.00: ATAPI: DVD/CDRW UJDA775, CB03, max UDMA/33
[    0.596346] ata1.00: configured for UDMA/33
[    0.683862] isapnp: No Plug & Play device found
[    0.685353] scsi 0:0:0:0: CD-ROM            MATSHITA DVD/CDRW UJDA775 CB03 PQ: 0 ANSI: 5
[    0.688816] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    0.688819] Uniform CD-ROM driver Revision: 3.20
[    0.688904] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    0.688947] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    0.688992] Freeing unused kernel memory: 656k freed
[    0.689415] Write protecting the kernel text: 4676k
[    0.689466] Write protecting the kernel read-only data: 1840k
[    0.703428] udev: starting version 151
[    0.769733] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k2
[    0.769736] e1000e: Copyright (c) 1999-2008 Intel Corporation.
[    0.769801] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.769817] e1000e 0000:00:19.0: setting latency timer to 64
[    0.769992]   alloc irq_desc for 29 on node -1
[    0.769994]   alloc kstat_irqs on node -1
[    0.770017] e1000e 0000:00:19.0: irq 29 for MSI/MSI-X
[    0.811253] ohci1394 0000:15:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.870080] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[f8301000-f83017ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    1.030637] 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:1c:25:be:c1:68
[    1.030639] 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    1.030682] 0000:00:19.0: eth0: MAC: 6, PHY: 6, PBA No: 1008ff-0ff
[    1.030698] ahci 0000:00:1f.2: version 3.0
[    1.030720] ahci 0000:00:1f.2: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    1.030769]   alloc irq_desc for 30 on node -1
[    1.030770]   alloc kstat_irqs on node -1
[    1.030785] ahci 0000:00:1f.2: irq 30 for MSI/MSI-X
[    1.030845] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 1.5 Gbps 0x5 impl SATA mode
[    1.030848] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ccc 
[    1.030857] ahci 0000:00:1f.2: setting latency timer to 64
[    1.031043] scsi2 : ahci
[    1.031136] scsi3 : ahci
[    1.031195] scsi4 : ahci
[    1.031276] ata3: SATA max UDMA/133 abar m2048@0xfe226000 port 0xfe226100 irq 30
[    1.031278] ata4: DUMMY
[    1.031283] ata5: SATA max UDMA/133 abar m2048@0xfe226000 port 0xfe226200 irq 30
[    1.136089] usb 5-1: new full speed USB device using uhci_hcd and address 2
[    1.341277] usb 5-1: configuration #1 chosen from 1 choice
[    1.348108] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.348138] ata5: SATA link down (SStatus 0 SControl 300)
[    1.349381] ata3.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[    1.349384] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    1.349614] ata3.00: ACPI cmd ef/5f:00:00:00:00:a0 (SET FEATURES) succeeded
[    1.349616] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.350823] ata3.00: ATA-8: HITACHI HTS722016K9SA00, DCDZC75A, max UDMA/133
[    1.350826] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.352326] ata3.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[    1.352329] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    1.352564] ata3.00: ACPI cmd ef/5f:00:00:00:00:a0 (SET FEATURES) succeeded
[    1.352567] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.353793] ata3.00: configured for UDMA/133
[    1.371747] ata3.00: configured for UDMA/133
[    1.371749] ata3: EH complete
[    1.371836] scsi 2:0:0:0: Direct-Access     ATA      HITACHI HTS72201 DCDZ PQ: 0 ANSI: 5
[    1.371962] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.371972] sd 2:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.372056] sd 2:0:0:0: [sda] Write Protect is off
[    1.372059] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.372080] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.372195]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    1.429096] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.580071] usb 5-2: new low speed USB device using uhci_hcd and address 3
[    1.757274] usb 5-2: configuration #1 chosen from 1 choice
[    1.777783] usbcore: registered new interface driver hiddev
[    1.792400] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb5/5-2/5-2:1.0/input/input5
[    1.792480] generic-usb 0003:046D:C51B.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-2/input0
[    1.806287] generic-usb 0003:046D:C51B.0002: hiddev96,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.0-2/input1
[    1.806304] usbcore: registered new interface driver usbhid
[    1.806306] usbhid: v2.6:USB HID core driver
[    2.012069] usb 6-1: new full speed USB device using uhci_hcd and address 2
[    2.015353] kjournald starting.  Commit interval 5 seconds
[    2.015359] EXT3-fs: mounted filesystem with ordered data mode.
[    2.144572] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00016c000065bf1b]
[    2.168512] usb 6-1: configuration #1 chosen from 1 choice
[   20.302891] udev: starting version 151
[   20.609993] Non-volatile memory driver v1.3
[   20.680730] Adding 3016400k swap on /dev/sda6.  Priority:-1 extents:1 across:3016400k 
[   20.741678] lp: driver loaded but no devices found
[   20.863816] EXT3 FS on sda5, internal journal
[   21.023192] type=1505 audit(1273800994.113:2):  operation="profile_load" pid=606 name="/sbin/dhclient3"
[   21.023717] type=1505 audit(1273800994.113:3):  operation="profile_load" pid=606 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   21.024022] type=1505 audit(1273800994.113:4):  operation="profile_load" pid=606 name="/usr/lib/connman/scripts/dhclient-script"
[   21.053385] type=1505 audit(1273800994.144:5):  operation="profile_load" pid=654 name="/usr/sbin/ntpd"
[   21.174398] cfg80211: Calling CRDA to update world regulatory domain
[   21.468143] usbcore: registered new interface driver usbserial
[   21.468851] USB Serial support registered for generic
[   21.473266] ricoh-mmc: Ricoh MMC Controller disabling driver
[   21.473268] ricoh-mmc: Copyright(c) Philip Langdale
[   21.473296] ricoh-mmc: Ricoh MMC controller found at 0000:15:00.3 [1180:0843] (rev 11)
[   21.473316] ricoh-mmc: Controller is now disabled.
[   21.474483] sdhci: Secure Digital Host Controller Interface driver
[   21.474485] sdhci: Copyright(c) Pierre Ossman
[   21.475761] Linux agpgart interface v0.103
[   21.479249] usblp0: USB Bidirectional printer dev 2 if 0 alt 1 proto 2 vid 0x03F0 pid 0x1204
[   21.479268] usbcore: registered new interface driver usblp
[   21.481965] usbcore: registered new interface driver usbserial_generic
[   21.481968] usbserial: USB Serial Driver core
[   21.509291] sdhci-pci 0000:15:00.2: SDHCI controller found [1180:0822] (rev 21)
[   21.509322] sdhci-pci 0000:15:00.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   21.510340] sdhci-pci 0000:15:00.2: Will use DMA mode even though HW doesn't fully claim to support it.
[   21.510350] sdhci-pci 0000:15:00.2: setting latency timer to 64
[   21.511409] Registered led device: mmc0::
[   21.512458] mmc0: SDHCI controller on PCI [0000:15:00.2] using DMA
[   21.529162] USB Serial support registered for Sierra USB modem
[   21.529190] sierra 6-1:1.0: Sierra USB modem converter detected
[   21.530518] usb 6-1: Sierra USB modem converter now attached to ttyUSB0
[   21.530554] usb 6-1: Sierra USB modem converter now attached to ttyUSB1
[   21.530590] usb 6-1: Sierra USB modem converter now attached to ttyUSB2
[   21.530603] usbcore: registered new interface driver sierra
[   21.530604] sierra: v.1.3.8:USB Driver for Sierra Wireless USB modems
[   21.541368] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
[   21.542154] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
[   21.548139] cfg80211: World regulatory domain updated:
[   21.548142] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   21.548145] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   21.548147] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   21.548149] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   21.548151] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   21.548153] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   21.549437] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[   21.746379] mmc0: new high speed SDHC card at address 8fe4
[   21.798877] type=1505 audit(1273800994.889:6):  operation="profile_load" pid=765 name="/usr/share/gdm/guest-session/Xsession"
[   21.800238] type=1505 audit(1273800994.889:7):  operation="profile_replace" pid=766 name="/sbin/dhclient3"
[   21.800778] type=1505 audit(1273800994.889:8):  operation="profile_replace" pid=766 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   21.801096] type=1505 audit(1273800994.893:9):  operation="profile_replace" pid=766 name="/usr/lib/connman/scripts/dhclient-script"
[   21.803693] type=1505 audit(1273800994.893:10):  operation="profile_load" pid=767 name="/usr/bin/evince"
[   21.810997] type=1505 audit(1273800994.901:11):  operation="profile_load" pid=767 name="/usr/bin/evince-previewer"
[   21.833261] yenta_cardbus 0000:15:00.0: CardBus bridge found [17aa:20c6]
[   21.960862] yenta_cardbus 0000:15:00.0: ISA IRQ mask 0x0cb8, PCI irq 16
[   21.960869] yenta_cardbus 0000:15:00.0: Socket status: 30000006
[   21.960875] yenta_cardbus 0000:15:00.0: pcmcia: parent PCI bridge I/O window: 0x7000 - 0xafff
[   21.960878] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x7000-0xafff: clean.
[   21.961614] yenta_cardbus 0000:15:00.0: pcmcia: parent PCI bridge Memory window: 0xf8300000 - 0xfbffffff
[   21.961617] yenta_cardbus 0000:15:00.0: pcmcia: parent PCI bridge Memory window: 0xf4000000 - 0xf7ffffff
[   22.073065] [drm] Initialized drm 1.1.0 20060810
[   22.074734] mmcblk0: mmc0:8fe4 SU04G 3.69 GiB 
[   22.074788]  mmcblk0: p1
[   22.529865] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x81a0b1, caps: 0xa04791/0x300000
[   22.529869] serio: Synaptics pass-through port at isa0060/serio1/input0
[   22.568067] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   22.568070] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   22.568157] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   22.568196] iwlagn 0000:03:00.0: setting latency timer to 64
[   22.568251] iwlagn 0000:03:00.0: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
[   22.577271] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
[   22.619584] iwlagn 0000:03:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   22.619667]   alloc irq_desc for 31 on node -1
[   22.619669]   alloc kstat_irqs on node -1
[   22.619700] iwlagn 0000:03:00.0: irq 31 for MSI/MSI-X
[   22.726021] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   22.727533] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   22.728538] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   22.729107] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   22.729983] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   22.844220] i915 0000:00:02.0: power state changed by ACPI to D0
[   22.844229] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   22.844233] i915 0000:00:02.0: setting latency timer to 64
[   22.850951]   alloc irq_desc for 32 on node -1
[   22.850954]   alloc kstat_irqs on node -1
[   22.850962] i915 0000:00:02.0: irq 32 for MSI/MSI-X
[   22.850968] [drm] set up 7M of stolen space
[   23.169728] apm: BIOS not found.
[   23.236995] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   23.295228] thinkpad_acpi: ThinkPad ACPI Extras v0.24
[   23.295231] thinkpad_acpi: http://ibm-acpi.sf.net/
[   23.295233] thinkpad_acpi: ThinkPad BIOS 7LETC6WW (2.26 ), EC 7KHT24WW-1.08
[   23.295235] thinkpad_acpi: Lenovo ThinkPad T61, model 6465CTO
[   23.301896] thinkpad_acpi: ACPI backlight control delay disabled
[   23.303244] thinkpad_acpi: radio switch found; radios are enabled
[   23.303396] thinkpad_acpi: This ThinkPad has standard ACPI backlight brightness control, supported by the ACPI video driver
[   23.303398] thinkpad_acpi: Disabling thinkpad-acpi brightness events by default...
[   23.309739] [drm] initialized overlay support
[   23.326716] thinkpad_acpi: rfkill switch tpacpi_wwan_sw: radio is unblocked
[   23.327579] Registered led device: tpacpi::thinklight
[   23.327606] Registered led device: tpacpi::power
[   23.327619] Registered led device: tpacpi::standby
[   23.327633] Registered led device: tpacpi::thinkvantage
[   23.331340] thinkpad_acpi: Standard ACPI backlight interface available, not loading native one.
[   23.331514] thinkpad_acpi: Console audio control enabled, mode: monitor (read only)
[   23.334752] input: ThinkPad Extra Buttons as /devices/platform/thinkpad_acpi/input/input7
[   23.798712] fb0: inteldrmfb frame buffer device
[   23.798714] registered panic notifier
[   23.801970] acpi device:01: registered as cooling_device2
[   23.802826] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input8
[   23.802903] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   23.803098] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   23.803143] HDA Intel 0000:00:1b.0: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   23.803146] hda_intel: probe_mask set to 0x1 for device 17aa:20ac
[   23.803181] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   23.829533] ppdev: user-space parallel port driver
[   23.838031] vga16fb: initializing
[   23.838035] vga16fb: mapped to 0xc00a0000
[   23.838038] vga16fb: not registering due to another framebuffer present
[   24.203381] Console: switching to colour frame buffer device 160x50
[   24.311840] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input9
[   25.373760] psmouse serio2: ID: 10 00 64
[   25.536071] CE: hpet increasing min_delta_ns to 15000 nsec
[   25.550483] CE: hpet increasing min_delta_ns to 22500 nsec
[   25.686783] usb 5-1: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[   29.232293] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   29.473981] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input10
[   78.172066] usb 1-3: new high speed USB device using ehci_hcd and address 2
[   78.314672] usb 1-3: configuration #1 chosen from 1 choice
[   78.367234] Initializing USB Mass Storage driver...
[   78.367342] scsi5 : SCSI emulation for USB Mass Storage devices
[   78.367419] usbcore: registered new interface driver usb-storage
[   78.367421] USB Mass Storage support registered.
[   78.367862] usb-storage: device found at 2
[   78.367864] usb-storage: waiting for device to settle before scanning
[   83.364405] usb-storage: device scan complete
[   83.365486] scsi 5:0:0:0: Direct-Access     Kingston DataTraveler 2.0 PMAP PQ: 0 ANSI: 0 CCS
[   83.367149] sd 5:0:0:0: Attached scsi generic sg2 type 0
[   85.077721] sd 5:0:0:0: [sdb] 3903488 512-byte logical blocks: (1.99 GB/1.86 GiB)
[   85.078208] sd 5:0:0:0: [sdb] Write Protect is off
[   85.078210] sd 5:0:0:0: [sdb] Mode Sense: 23 00 00 00
[   85.078213] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[   85.080450] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[   85.080454]  sdb: sdb1
[   85.082563] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[   85.082567] sd 5:0:0:0: [sdb] Attached SCSI removable disk
jutumang@jutumang-laptop:~$ 
```
By the way, do you happen to know how to make Terminal give a full report and not cut information if it is too long?

As for the "ifconfig", here is the output:```
jutumang@jutumang-laptop:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1346 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1346 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:107309 (107.3 KB)  TX bytes:107309 (107.3 KB)
jutumang@jutumang-laptop:~$ 
```

Thanks for the advise so far!

---

### Post by RedStarYellowSun on 2010-05-13
> **bredman said:**
> To find the wireless hardware you are using, use command
lshw

To find which modules are loaded, use command
lsmod

To find all modules available in the system, use command
modprobe -l
The output from "lshw":```
jutumang@jutumang-laptop:~$ lshw
WARNING: you should run this program as super-user.
jutumang-laptop           
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1972MiB
     *-cpu
          product: Intel(R) Core(TM)2 Duo CPU     T8300  @ 2.40GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.7.6
          serial: 0001-0676-0000-0000-0000-0000
          size: 800MHz
          capacity: 800MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm ida tpr_shadow vnmi flexpriority cpufreq
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: Mobile PM965/GM965/GL960 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 0c
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 0c
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:32 memory:f8100000-f81fffff memory:e0000000-efffffff(prefetchable) ioport:1800(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 0c
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: memory:f8200000-f82fffff
        *-network DISABLED
             description: Ethernet interface
             product: 82566MM Gigabit Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth0
             version: 03
             serial: 00:1c:25:be:c1:68
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=e1000e driverversion=1.0.2-k2 firmware=0.3-0 latency=0 multicast=yes
             resources: irq:29 memory:fe000000-fe01ffff memory:fe025000-fe025fff ioport:1840(size=32)
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:1860(size=32)
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:1880(size=32)
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:22 memory:fe226c00-fe226fff
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:17 memory:fe020000-fe023fff
        *-pci:0
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:2000(size=4096) memory:fc000000-fdffffff ioport:f8000000(size=1048576)
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:3000(size=4096) memory:dc000000-df3fffff ioport:dfe00000(size=1048576)
           *-network DISABLED
                description: Wireless interface
                product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 61
                serial: 00:21:5c:54:03:27
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
                resources: irq:31 memory:df3fe000-df3fffff
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:4000(size=4096) memory:d8000000-d9ffffff ioport:dfb00000(size=1048576)
        *-pci:3
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 ioport:5000(size=4096) memory:d4000000-d5ffffff ioport:df800000(size=1048576)
        *-pci:4
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
             resources: irq:28 ioport:6000(size=4096) memory:d0000000-d1ffffff ioport:df500000(size=1048576)
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:18a0(size=32)
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:18c0(size=32)
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:18e0(size=32)
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:19 memory:fe227000-fe2273ff
        *-pci:5
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f3
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             resources: ioport:7000(size=16384) memory:f8300000-fbffffff ioport:f4000000(size=67108864)
           *-pcmcia
                description: CardBus bridge
                product: RL5c476 II
                vendor: Ricoh Co Ltd
                physical id: 0
                bus info: pci@0000:15:00.0
                version: ba
                width: 64 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128
                resources: iomemory:b01716150-b0171614f irq:16 memory:f8300000-f8300fff ioport:7000(size=256) ioport:7400(size=256) memory:f4000000-f7ffffff(prefetchable) memory:80000000-83ffffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 0.1
                bus info: pci@0000:15:00.1
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=2
                resources: irq:17 memory:f8301000-f83017ff
           *-generic:0
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 0.2
                bus info: pci@0000:15:00.2
                version: 21
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci-pci latency=64
                resources: irq:18 memory:f8301800-f83018ff
           *-generic:1
                product: Illegal Vendor ID
                vendor: Illegal Vendor ID
                physical id: 0.3
                bus info: pci@0000:15:00.3
                version: ff
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master vga_palette cap_list
                configuration: driver=ricoh-mmc latency=255 maxlatency=255 mingnt=255
                resources: irq:11 memory:f8301c00-f8301cff
           *-generic:2 UNCLAIMED
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 0.4
                bus info: pci@0000:15:00.4
                version: 11
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: latency=0
                resources: memory:f8302000-f83020ff
           *-generic:3 UNCLAIMED
                description: System peripheral
                product: xD-Picture Card Controller
                vendor: Ricoh Co Ltd
                physical id: 0.5
                bus info: pci@0000:15:00.5
                version: 11
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: latency=0
                resources: memory:f8302400-f83024ff
        *-isa
             description: ISA bridge
             product: 82801HBM (ICH8M-E) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1c00(size=16)
           *-cdrom
                description: DVD reader
                product: DVD/CDRW UJDA775
                vendor: MATSHITA
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: CB03
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=nodisc
        *-storage
             description: SATA controller
             product: 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:30 ioport:1c50(size=8) ioport:1c44(size=4) ioport:1c48(size=8) ioport:1c40(size=4) ioport:1c20(size=32) memory:fe226000-fe2267ff
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fe227400-fe2274ff ioport:1c60(size=32)
  *-scsi
       physical id: 1
       bus info: scsi@5
       logical name: scsi5
       capabilities: scsi-host
       configuration: driver=usb-storage
jutumang@jutumang-laptop:~$
```

To lsmod:```
jutumang@jutumang-laptop:~$ lsmod
Module                  Size  Used by
usb_storage            39425  1 
nls_iso8859_1           3249  2 
nls_cp437               4919  2 
vfat                    8901  2 
fat                    47767  1 vfat
binfmt_misc             6587  1 
snd_hda_codec_analog    58566  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
ppdev                   5259  0 
thinkpad_acpi          68083  0 
arc4                    1153  2 
snd_hda_intel          21877  2 
snd_hda_codec          74201  2 snd_hda_codec_analog,snd_hda_intel
snd_seq_dummy           1338  0 
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
joydev                  8708  0 
i915                  282354  3 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iwlagn                105566  0 
drm_kms_helper         29297  1 i915
iwlcore               105922  1 iwlagn
snd_timer              19098  2 snd_pcm,snd_seq
pcmcia                 33024  0 
mmc_block               8258  2 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
drm                   162471  4 i915,drm_kms_helper
psmouse                63245  0 
yenta_socket           20408  1 
mac80211              204922  2 iwlagn,iwlcore
snd                    54148  17 snd_hda_codec_analog,thinkpad_acpi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              24177  2 i915
sierra                  8992  0 
sdhci_pci               5470  0 
rsrc_nonstatic         10015  1 yenta_socket
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
soundcore               6620  1 snd
sdhci                  15462  1 sdhci_pci
ricoh_mmc               2923  0 
agpgart                31724  2 drm,intel_agp
i2c_algo_bit            5028  1 i915
usblp                  10481  0 
serio_raw               3978  0 
usbserial              33019  1 sierra
cfg80211              126485  3 iwlagn,iwlcore,mac80211
led_class               2864  3 thinkpad_acpi,iwlcore,sdhci
lp                      7028  0 
nvram                   6171  1 thinkpad_acpi
video                  17375  1 i915
output                  1871  1 video
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67032  1 usbhid
ohci1394               26950  0 
ieee1394               81181  1 ohci1394
ahci                   32008  2 
e1000e                119856  0 
jutumang@jutumang-laptop:~$
```

To modprobe -l:```
kernel/sound/isa/snd-dt019x.ko
kernel/sound/isa/snd-es18xx.ko
kernel/sound/isa/snd-opl3sa2.ko
kernel/sound/isa/snd-sc6000.ko
kernel/sound/isa/snd-sgalaxy.ko
kernel/sound/isa/snd-sscape.ko
kernel/sound/isa/ad1816a/snd-ad1816a.ko
kernel/sound/isa/ad1848/snd-ad1848.ko
kernel/sound/isa/cs423x/snd-cs4231.ko
kernel/sound/isa/cs423x/snd-cs4236.ko
kernel/sound/isa/es1688/snd-es1688.ko
kernel/sound/isa/es1688/snd-es1688-lib.ko
kernel/sound/isa/gus/snd-gusclassic.ko
kernel/sound/isa/gus/snd-gus-lib.ko
kernel/sound/isa/gus/snd-gusmax.ko
kernel/sound/isa/gus/snd-gusextreme.ko
kernel/sound/isa/gus/snd-interwave.ko
kernel/sound/isa/gus/snd-interwave-stb.ko
kernel/sound/isa/msnd/snd-msnd-pinnacle.ko
kernel/sound/isa/msnd/snd-msnd-lib.ko
kernel/sound/isa/msnd/snd-msnd-classic.ko
kernel/sound/isa/opti9xx/snd-opti92x-ad1848.ko
kernel/sound/isa/opti9xx/snd-opti92x-cs4231.ko
kernel/sound/isa/opti9xx/snd-opti93x.ko
kernel/sound/isa/opti9xx/snd-miro.ko
kernel/sound/isa/sb/snd-sb-common.ko
kernel/sound/isa/sb/snd-sb16-dsp.ko
kernel/sound/isa/sb/snd-sb8-dsp.ko
kernel/sound/isa/sb/snd-sb8.ko
kernel/sound/isa/sb/snd-sb16.ko
kernel/sound/isa/sb/snd-sbawe.ko
kernel/sound/isa/sb/snd-es968.ko
kernel/sound/isa/sb/snd-sb16-csp.ko
kernel/sound/isa/sb/snd-emu8000-synth.ko
kernel/sound/isa/wavefront/snd-wavefront.ko
kernel/sound/isa/wss/snd-wss-lib.ko
kernel/sound/pci/snd-ad1889.ko
kernel/sound/pci/snd-als300.ko
kernel/sound/pci/snd-als4000.ko
kernel/sound/pci/snd-atiixp.ko
kernel/sound/pci/snd-atiixp-modem.ko
kernel/sound/pci/snd-azt3328.ko
kernel/sound/pci/snd-bt87x.ko
kernel/sound/pci/snd-cmipci.ko
kernel/sound/pci/snd-cs4281.ko
kernel/sound/pci/snd-cs5530.ko
kernel/sound/pci/snd-ens1370.ko
kernel/sound/pci/snd-ens1371.ko
kernel/sound/pci/snd-es1938.ko
kernel/sound/pci/snd-es1968.ko
kernel/sound/pci/snd-fm801.ko
kernel/sound/pci/snd-intel8x0.ko
kernel/sound/pci/snd-intel8x0m.ko
kernel/sound/pci/snd-maestro3.ko
kernel/sound/pci/snd-rme32.ko
kernel/sound/pci/snd-rme96.ko
kernel/sound/pci/snd-sis7019.ko
kernel/sound/pci/snd-sonicvibes.ko
kernel/sound/pci/snd-via82xx.ko
kernel/sound/pci/snd-via82xx-modem.ko
kernel/sound/pci/ac97/snd-ac97-codec.ko
kernel/sound/pci/ali5451/snd-ali5451.ko
kernel/sound/pci/au88x0/snd-au8810.ko
kernel/sound/pci/au88x0/snd-au8820.ko
kernel/sound/pci/au88x0/snd-au8830.ko
kernel/sound/pci/aw2/snd-aw2.ko
kernel/sound/pci/ctxfi/snd-ctxfi.ko
kernel/sound/pci/ca0106/snd-ca0106.ko
kernel/sound/pci/cs46xx/snd-cs46xx.ko
kernel/sound/pci/cs5535audio/snd-cs5535audio.ko
kernel/sound/pci/lx6464es/snd-lx6464es.ko
kernel/sound/pci/echoaudio/snd-darla20.ko
kernel/sound/pci/echoaudio/snd-gina20.ko
kernel/sound/pci/echoaudio/snd-layla20.ko
kernel/sound/pci/echoaudio/snd-darla24.ko
kernel/sound/pci/echoaudio/snd-gina24.ko
kernel/sound/pci/echoaudio/snd-layla24.ko
kernel/sound/pci/echoaudio/snd-mona.ko
kernel/sound/pci/echoaudio/snd-mia.ko
kernel/sound/pci/echoaudio/snd-echo3g.ko
kernel/sound/pci/echoaudio/snd-indigo.ko
kernel/sound/pci/echoaudio/snd-indigoio.ko
kernel/sound/pci/echoaudio/snd-indigodj.ko
kernel/sound/pci/echoaudio/snd-indigoiox.ko
kernel/sound/pci/echoaudio/snd-indigodjx.ko
kernel/sound/pci/emu10k1/snd-emu10k1.ko
kernel/sound/pci/emu10k1/snd-emu10k1-synth.ko
kernel/sound/pci/emu10k1/snd-emu10k1x.ko
kernel/sound/pci/hda/snd-hda-codec.ko
kernel/sound/pci/hda/snd-hda-codec-realtek.ko
kernel/sound/pci/hda/snd-hda-codec-cmedia.ko
kernel/sound/pci/hda/snd-hda-codec-analog.ko
kernel/sound/pci/hda/snd-hda-codec-idt.ko
kernel/sound/pci/hda/snd-hda-codec-si3054.ko
kernel/sound/pci/hda/snd-hda-codec-atihdmi.ko
kernel/sound/pci/hda/snd-hda-codec-cirrus.ko
kernel/sound/pci/hda/snd-hda-codec-ca0110.ko
kernel/sound/pci/hda/snd-hda-codec-conexant.ko
kernel/sound/pci/hda/snd-hda-codec-via.ko
kernel/sound/pci/hda/snd-hda-codec-nvhdmi.ko
kernel/sound/pci/hda/snd-hda-codec-intelhdmi.ko
kernel/sound/pci/hda/snd-hda-intel.ko
kernel/sound/pci/ice1712/snd-ice1712.ko
kernel/sound/pci/ice1712/snd-ice17xx-ak4xxx.ko
kernel/sound/pci/ice1712/snd-ice1724.ko
kernel/sound/pci/korg1212/snd-korg1212.ko
kernel/sound/pci/mixart/snd-mixart.ko
kernel/sound/pci/nm256/snd-nm256.ko
kernel/sound/pci/oxygen/snd-oxygen-lib.ko
kernel/sound/pci/oxygen/snd-hifier.ko
kernel/sound/pci/oxygen/snd-oxygen.ko
kernel/sound/pci/oxygen/snd-virtuoso.ko
kernel/sound/pci/pcxhr/snd-pcxhr.ko
kernel/sound/pci/riptide/snd-riptide.ko
kernel/sound/pci/rme9652/snd-rme9652.ko
kernel/sound/pci/rme9652/snd-hdsp.ko
kernel/sound/pci/rme9652/snd-hdspm.ko
kernel/sound/pci/trident/snd-trident.ko
kernel/sound/pci/ymfpci/snd-ymfpci.ko
kernel/sound/pci/vx222/snd-vx222.ko
kernel/sound/synth/snd-util-mem.ko
kernel/sound/synth/emux/snd-emux-synth.ko
kernel/sound/usb/snd-usb-audio.ko
kernel/sound/usb/snd-usb-lib.ko
kernel/sound/usb/usx2y/snd-usb-usx2y.ko
kernel/sound/usb/usx2y/snd-usb-us122l.ko
kernel/sound/usb/caiaq/snd-usb-caiaq.ko
kernel/sound/pcmcia/vx/snd-vxpocket.ko
kernel/sound/pcmcia/pdaudiocf/snd-pdaudiocf.ko
kernel/sound/soc/snd-soc-core.ko
kernel/sound/soc/codecs/snd-soc-ad1836.ko
kernel/sound/soc/codecs/snd-soc-ad1938.ko
kernel/sound/soc/codecs/snd-soc-ad73311.ko
kernel/sound/soc/codecs/snd-soc-ak4104.ko
kernel/sound/soc/codecs/snd-soc-ak4535.ko
kernel/sound/soc/codecs/snd-soc-ak4642.ko
kernel/sound/soc/codecs/snd-soc-cs4270.ko
kernel/sound/soc/codecs/snd-soc-l3.ko
kernel/sound/soc/codecs/snd-soc-pcm3008.ko
kernel/sound/soc/codecs/snd-soc-spdif.ko
kernel/sound/soc/codecs/snd-soc-ssm2602.ko
kernel/sound/soc/codecs/snd-soc-tlv320aic23.ko
kernel/sound/soc/codecs/snd-soc-tlv320aic26.ko
kernel/sound/soc/codecs/snd-soc-tlv320aic3x.ko
kernel/sound/soc/codecs/snd-soc-twl4030.ko
kernel/sound/soc/codecs/snd-soc-uda134x.ko
kernel/sound/soc/codecs/snd-soc-uda1380.ko
kernel/sound/soc/codecs/snd-soc-wm8350.ko
kernel/sound/soc/codecs/snd-soc-wm8400.ko
kernel/sound/soc/codecs/snd-soc-wm8510.ko
kernel/sound/soc/codecs/snd-soc-wm8523.ko
kernel/sound/soc/codecs/snd-soc-wm8580.ko
kernel/sound/soc/codecs/snd-soc-wm8728.ko
kernel/sound/soc/codecs/snd-soc-wm8731.ko
kernel/sound/soc/codecs/snd-soc-wm8750.ko
kernel/sound/soc/codecs/snd-soc-wm8753.ko
kernel/sound/soc/codecs/snd-soc-wm8776.ko
kernel/sound/soc/codecs/snd-soc-wm8900.ko
kernel/sound/soc/codecs/snd-soc-wm8903.ko
kernel/sound/soc/codecs/snd-soc-wm8971.ko
kernel/sound/soc/codecs/snd-soc-wm8974.ko
kernel/sound/soc/codecs/snd-soc-wm8940.ko
kernel/sound/soc/codecs/snd-soc-wm8960.ko
kernel/sound/soc/codecs/snd-soc-wm8961.ko
kernel/sound/soc/codecs/snd-soc-wm8988.ko
kernel/sound/soc/codecs/snd-soc-wm8990.ko
kernel/sound/soc/codecs/snd-soc-wm8993.ko
kernel/sound/soc/codecs/snd-soc-wm9081.ko
kernel/sound/soc/codecs/snd-soc-wm-hubs.ko
kernel/sound/soc/codecs/snd-soc-max9877.ko
kernel/sound/ac97_bus.ko
kernel/ubuntu/aufs/aufs.ko
kernel/ubuntu/compcache/ramzswap.ko
kernel/ubuntu/compcache/xvmalloc.ko
kernel/ubuntu/dm-raid4-5/dm-raid45.ko
kernel/ubuntu/fsam7400/fsam7400.ko
kernel/ubuntu/iscsitarget/iscsi_trgt.ko
kernel/ubuntu/lirc/lirc_dev/lirc_dev.ko
kernel/ubuntu/lirc/lirc_atiusb/lirc_atiusb.ko
kernel/ubuntu/lirc/lirc_bt829/lirc_bt829.ko
kernel/ubuntu/lirc/lirc_ene0100/lirc_ene0100.ko
kernel/ubuntu/lirc/lirc_i2c/lirc_i2c.ko
kernel/ubuntu/lirc/lirc_igorplugusb/lirc_igorplugusb.ko
kernel/ubuntu/lirc/lirc_imon/lirc_imon.ko
kernel/ubuntu/lirc/lirc_it87/lirc_it87.ko
kernel/ubuntu/lirc/lirc_ite8709/lirc_ite8709.ko
kernel/ubuntu/lirc/lirc_mceusb/lirc_mceusb.ko
kernel/ubuntu/lirc/lirc_sasem/lirc_sasem.ko
kernel/ubuntu/lirc/lirc_serial/lirc_serial.ko
kernel/ubuntu/lirc/lirc_sir/lirc_sir.ko
kernel/ubuntu/lirc/lirc_streamzap/lirc_streamzap.ko
kernel/ubuntu/lirc/lirc_ttusbir/lirc_ttusbir.ko
kernel/ubuntu/ndiswrapper/ndiswrapper.ko
kernel/ubuntu/omnibook/omnibook.ko
kernel/ubuntu/rtl8192se/r8192se_pci.ko
kernel/ubuntu/rfkill/av5100.ko
kernel/ubuntu/rfkill/pbe5.ko
kernel/arch/x86/oprofile/oprofile.ko
kernel/net/core/pktgen.ko
kernel/net/llc/llc2.ko
kernel/net/802/p8023.ko
kernel/net/802/stp.ko
kernel/net/802/garp.ko
kernel/net/sched/act_police.ko
kernel/net/sched/act_gact.ko
kernel/net/sched/act_mirred.ko
kernel/net/sched/act_ipt.ko
kernel/net/sched/act_nat.ko
kernel/net/sched/act_pedit.ko
kernel/net/sched/act_simple.ko
kernel/net/sched/act_skbedit.ko
kernel/net/sched/sch_cbq.ko
kernel/net/sched/sch_htb.ko
kernel/net/sched/sch_hfsc.ko
kernel/net/sched/sch_red.ko
kernel/net/sched/sch_gred.ko
kernel/net/sched/sch_ingress.ko
kernel/net/sched/sch_dsmark.ko
kernel/net/sched/sch_sfq.ko
kernel/net/sched/sch_tbf.ko
kernel/net/sched/sch_teql.ko
kernel/net/sched/sch_prio.ko
kernel/net/sched/sch_multiq.ko
kernel/net/sched/sch_atm.ko
kernel/net/sched/sch_netem.ko
kernel/net/sched/sch_drr.ko
kernel/net/sched/cls_u32.ko
kernel/net/sched/cls_route.ko
kernel/net/sched/cls_fw.ko
kernel/net/sched/cls_rsvp.ko
kernel/net/sched/cls_tcindex.ko
kernel/net/sched/cls_rsvp6.ko
kernel/net/sched/cls_basic.ko
kernel/net/sched/cls_flow.ko
kernel/net/sched/em_cmp.ko
kernel/net/sched/em_nbyte.ko
kernel/net/sched/em_u32.ko
kernel/net/sched/em_meta.ko
kernel/net/sched/em_text.ko
kernel/net/netfilter/nfnetlink.ko
kernel/net/netfilter/nfnetlink_queue.ko
kernel/net/netfilter/nfnetlink_log.ko
kernel/net/netfilter/nf_conntrack.ko
kernel/net/netfilter/nf_conntrack_proto_dccp.ko
kernel/net/netfilter/nf_conntrack_proto_gre.ko
kernel/net/netfilter/nf_conntrack_proto_sctp.ko
kernel/net/netfilter/nf_conntrack_proto_udplite.ko
kernel/net/netfilter/nf_conntrack_netlink.ko
kernel/net/netfilter/nf_conntrack_amanda.ko
kernel/net/netfilter/nf_conntrack_ftp.ko
kernel/net/netfilter/nf_conntrack_h323.ko
kernel/net/netfilter/nf_conntrack_irc.ko
kernel/net/netfilter/nf_conntrack_netbios_ns.ko
kernel/net/netfilter/nf_conntrack_pptp.ko
kernel/net/netfilter/nf_conntrack_sane.ko
kernel/net/netfilter/nf_conntrack_sip.ko
kernel/net/netfilter/nf_conntrack_tftp.ko
kernel/net/netfilter/nf_tproxy_core.ko
kernel/net/netfilter/x_tables.ko
kernel/net/netfilter/xt_tcpudp.ko
kernel/net/netfilter/xt_CLASSIFY.ko
kernel/net/netfilter/xt_CONNMARK.ko
kernel/net/netfilter/xt_CONNSECMARK.ko
kernel/net/netfilter/xt_DSCP.ko
kernel/net/netfilter/xt_HL.ko
kernel/net/netfilter/xt_LED.ko
kernel/net/netfilter/xt_MARK.ko
kernel/net/netfilter/xt_NFLOG.ko
kernel/net/netfilter/xt_NFQUEUE.ko
kernel/net/netfilter/xt_NOTRACK.ko
kernel/net/netfilter/xt_RATEEST.ko
kernel/net/netfilter/xt_SECMARK.ko
kernel/net/netfilter/xt_TPROXY.ko
kernel/net/netfilter/xt_TCPMSS.ko
kernel/net/netfilter/xt_TRACE.ko
kernel/net/netfilter/xt_cluster.ko
kernel/net/netfilter/xt_comment.ko
kernel/net/netfilter/xt_connbytes.ko
kernel/net/netfilter/xt_connlimit.ko
kernel/net/netfilter/xt_connmark.ko
kernel/net/netfilter/xt_conntrack.ko
kernel/net/netfilter/xt_dccp.ko
kernel/net/netfilter/xt_dscp.ko
kernel/net/netfilter/xt_esp.ko
kernel/net/netfilter/xt_hashlimit.ko
kernel/net/netfilter/xt_helper.ko
kernel/net/netfilter/xt_hl.ko
kernel/net/netfilter/xt_iprange.ko
kernel/net/netfilter/xt_length.ko
kernel/net/netfilter/xt_limit.ko
kernel/net/netfilter/xt_mac.ko
kernel/net/netfilter/xt_mark.ko
kernel/net/netfilter/xt_multiport.ko
kernel/net/netfilter/xt_osf.ko
kernel/net/netfilter/xt_owner.ko
kernel/net/netfilter/xt_physdev.ko
kernel/net/netfilter/xt_pkttype.ko
kernel/net/netfilter/xt_policy.ko
kernel/net/netfilter/xt_quota.ko
kernel/net/netfilter/xt_rateest.ko
kernel/net/netfilter/xt_realm.ko
kernel/net/netfilter/xt_recent.ko
kernel/net/netfilter/xt_sctp.ko
kernel/net/netfilter/xt_socket.ko
kernel/net/netfilter/xt_state.ko
kernel/net/netfilter/xt_statistic.ko
kernel/net/netfilter/xt_string.ko
kernel/net/netfilter/xt_tcpmss.ko
kernel/net/netfilter/xt_time.ko
kernel/net/netfilter/xt_u32.ko
kernel/net/netfilter/ipvs/ip_vs.ko
kernel/net/netfilter/ipvs/ip_vs_rr.ko
kernel/net/netfilter/ipvs/ip_vs_wrr.ko
kernel/net/netfilter/ipvs/ip_vs_lc.ko
kernel/net/netfilter/ipvs/ip_vs_wlc.ko
kernel/net/netfilter/ipvs/ip_vs_lblc.ko
kernel/net/netfilter/ipvs/ip_vs_lblcr.ko
kernel/net/netfilter/ipvs/ip_vs_dh.ko
kernel/net/netfilter/ipvs/ip_vs_sh.ko
kernel/net/netfilter/ipvs/ip_vs_sed.ko
kernel/net/netfilter/ipvs/ip_vs_nq.ko
kernel/net/netfilter/ipvs/ip_vs_ftp.ko
kernel/net/ipv4/netfilter/nf_conntrack_ipv4.ko
kernel/net/ipv4/netfilter/nf_nat.ko
kernel/net/ipv4/netfilter/nf_defrag_ipv4.ko
kernel/net/ipv4/netfilter/nf_nat_amanda.ko
kernel/net/ipv4/netfilter/nf_nat_ftp.ko
kernel/net/ipv4/netfilter/nf_nat_h323.ko
kernel/net/ipv4/netfilter/nf_nat_irc.ko
kernel/net/ipv4/netfilter/nf_nat_pptp.ko
kernel/net/ipv4/netfilter/nf_nat_sip.ko
kernel/net/ipv4/netfilter/nf_nat_snmp_basic.ko
kernel/net/ipv4/netfilter/nf_nat_tftp.ko
kernel/net/ipv4/netfilter/nf_nat_proto_dccp.ko
kernel/net/ipv4/netfilter/nf_nat_proto_gre.ko
kernel/net/ipv4/netfilter/nf_nat_proto_udplite.ko
kernel/net/ipv4/netfilter/nf_nat_proto_sctp.ko
kernel/net/ipv4/netfilter/ip_tables.ko
kernel/net/ipv4/netfilter/iptable_filter.ko
kernel/net/ipv4/netfilter/iptable_mangle.ko
kernel/net/ipv4/netfilter/iptable_nat.ko
kernel/net/ipv4/netfilter/iptable_raw.ko
kernel/net/ipv4/netfilter/iptable_security.ko
kernel/net/ipv4/netfilter/ipt_addrtype.ko
kernel/net/ipv4/netfilter/ipt_ah.ko
kernel/net/ipv4/netfilter/ipt_ecn.ko
kernel/net/ipv4/netfilter/ipt_CLUSTERIP.ko
kernel/net/ipv4/netfilter/ipt_ECN.ko
kernel/net/ipv4/netfilter/ipt_LOG.ko
kernel/net/ipv4/netfilter/ipt_MASQUERADE.ko
kernel/net/ipv4/netfilter/ipt_NETMAP.ko
kernel/net/ipv4/netfilter/ipt_REDIRECT.ko
kernel/net/ipv4/netfilter/ipt_REJECT.ko
kernel/net/ipv4/netfilter/ipt_ULOG.ko
kernel/net/ipv4/netfilter/arp_tables.ko
kernel/net/ipv4/netfilter/arpt_mangle.ko
kernel/net/ipv4/netfilter/arptable_filter.ko
kernel/net/ipv4/netfilter/ip_queue.ko
kernel/net/ipv4/ipip.ko
kernel/net/ipv4/ip_gre.ko
kernel/net/ipv4/ah4.ko
kernel/net/ipv4/esp4.ko
kernel/net/ipv4/ipcomp.ko
kernel/net/ipv4/xfrm4_tunnel.ko
kernel/net/ipv4/xfrm4_mode_beet.ko
kernel/net/ipv4/tunnel4.ko
kernel/net/ipv4/xfrm4_mode_transport.ko
kernel/net/ipv4/xfrm4_mode_tunnel.ko
kernel/net/ipv4/tcp_probe.ko
kernel/net/ipv4/tcp_bic.ko
kernel/net/ipv4/tcp_westwood.ko
kernel/net/ipv4/tcp_highspeed.ko
kernel/net/ipv4/tcp_hybla.ko
kernel/net/ipv4/tcp_htcp.ko
kernel/net/ipv4/tcp_vegas.ko
kernel/net/ipv4/tcp_veno.ko
kernel/net/ipv4/tcp_scalable.ko
kernel/net/ipv4/tcp_lp.ko
kernel/net/ipv4/tcp_yeah.ko
kernel/net/ipv4/tcp_illinois.ko
kernel/net/xfrm/xfrm_user.ko
kernel/net/xfrm/xfrm_ipcomp.ko
kernel/net/ipv6/netfilter/ip6_tables.ko
kernel/net/ipv6/netfilter/ip6table_filter.ko
kernel/net/ipv6/netfilter/ip6table_mangle.ko
kernel/net/ipv6/netfilter/ip6_queue.ko
kernel/net/ipv6/netfilter/ip6table_raw.ko
kernel/net/ipv6/netfilter/ip6table_security.ko
kernel/net/ipv6/netfilter/nf_conntrack_ipv6.ko
kernel/net/ipv6/netfilter/ip6t_ah.ko
kernel/net/ipv6/netfilter/ip6t_eui64.ko
kernel/net/ipv6/netfilter/ip6t_frag.ko
kernel/net/ipv6/netfilter/ip6t_ipv6header.ko
kernel/net/ipv6/netfilter/ip6t_mh.ko
kernel/net/ipv6/netfilter/ip6t_hbh.ko
kernel/net/ipv6/netfilter/ip6t_rt.ko
kernel/net/ipv6/netfilter/ip6t_LOG.ko
kernel/net/ipv6/netfilter/ip6t_REJECT.ko
kernel/net/ipv6/ah6.ko
kernel/net/ipv6/esp6.ko
kernel/net/ipv6/ipcomp6.ko
kernel/net/ipv6/xfrm6_tunnel.ko
kernel/net/ipv6/tunnel6.ko
kernel/net/ipv6/xfrm6_mode_transport.ko
kernel/net/ipv6/xfrm6_mode_tunnel.ko
kernel/net/ipv6/xfrm6_mode_ro.ko
kernel/net/ipv6/xfrm6_mode_beet.ko
kernel/net/ipv6/sit.ko
kernel/net/ipv6/ip6_tunnel.ko
kernel/net/8021q/8021q.ko
kernel/net/wireless/cfg80211.ko
kernel/net/wireless/lib80211.ko
kernel/net/wireless/lib80211_crypt_wep.ko
kernel/net/wireless/lib80211_crypt_ccmp.ko
kernel/net/wireless/lib80211_crypt_tkip.ko
kernel/net/ieee802154/nl802154.ko
kernel/net/ieee802154/af_802154.ko
kernel/net/ieee802154/wpan-class.ko
kernel/net/key/af_key.ko
kernel/net/bridge/bridge.ko
kernel/net/bridge/netfilter/ebtables.ko
kernel/net/bridge/netfilter/ebtable_broute.ko
kernel/net/bridge/netfilter/ebtable_filter.ko
kernel/net/bridge/netfilter/ebtable_nat.ko
kernel/net/bridge/netfilter/ebt_802_3.ko
kernel/net/bridge/netfilter/ebt_among.ko
kernel/net/bridge/netfilter/ebt_arp.ko
kernel/net/bridge/netfilter/ebt_ip.ko
kernel/net/bridge/netfilter/ebt_ip6.ko
kernel/net/bridge/netfilter/ebt_limit.ko
kernel/net/bridge/netfilter/ebt_mark_m.ko
kernel/net/bridge/netfilter/ebt_pkttype.ko
kernel/net/bridge/netfilter/ebt_stp.ko
kernel/net/bridge/netfilter/ebt_vlan.ko
kernel/net/bridge/netfilter/ebt_arpreply.ko
kernel/net/bridge/netfilter/ebt_mark.ko
kernel/net/bridge/netfilter/ebt_dnat.ko
kernel/net/bridge/netfilter/ebt_redirect.ko
kernel/net/bridge/netfilter/ebt_snat.ko
kernel/net/bridge/netfilter/ebt_log.ko
kernel/net/bridge/netfilter/ebt_ulog.ko
kernel/net/bridge/netfilter/ebt_nflog.ko
kernel/net/ipx/ipx.ko
kernel/net/appletalk/appletalk.ko
kernel/net/wanrouter/wanrouter.ko
kernel/net/x25/x25.ko
kernel/net/lapb/lapb.ko
kernel/net/netrom/netrom.ko
kernel/net/rose/rose.ko
kernel/net/ax25/ax25.ko
kernel/net/can/can.ko
kernel/net/can/can-raw.ko
kernel/net/can/can-bcm.ko
kernel/net/irda/irda.ko
kernel/net/irda/irlan/irlan.ko
kernel/net/irda/irnet/irnet.ko
kernel/net/irda/ircomm/ircomm.ko
kernel/net/irda/ircomm/ircomm-tty.ko
kernel/net/bluetooth/bluetooth.ko
kernel/net/bluetooth/l2cap.ko
kernel/net/bluetooth/sco.ko
kernel/net/bluetooth/rfcomm/rfcomm.ko
kernel/net/bluetooth/bnep/bnep.ko
kernel/net/bluetooth/cmtp/cmtp.ko
kernel/net/bluetooth/hidp/hidp.ko
kernel/net/sunrpc/sunrpc.ko
kernel/net/sunrpc/auth_gss/auth_rpcgss.ko
kernel/net/sunrpc/auth_gss/rpcsec_gss_krb5.ko
kernel/net/sunrpc/auth_gss/rpcsec_gss_spkm3.ko
kernel/net/sunrpc/xprtrdma/xprtrdma.ko
kernel/net/sunrpc/xprtrdma/svcrdma.ko
kernel/net/rxrpc/af-rxrpc.ko
kernel/net/rxrpc/rxkad.ko
kernel/net/atm/atm.ko
kernel/net/atm/clip.ko
kernel/net/atm/br2684.ko
kernel/net/atm/lec.ko
kernel/net/atm/mpoa.ko
kernel/net/atm/pppoatm.ko
kernel/net/decnet/netfilter/dn_rtmsg.ko
kernel/net/decnet/decnet.ko
kernel/net/econet/econet.ko
kernel/net/phonet/phonet.ko
kernel/net/phonet/pn_pep.ko
kernel/net/dccp/dccp.ko
kernel/net/dccp/dccp_ipv4.ko
kernel/net/dccp/dccp_ipv6.ko
kernel/net/dccp/dccp_diag.ko
kernel/net/dccp/dccp_probe.ko
kernel/net/sctp/sctp.ko
kernel/net/rds/rds.ko
kernel/net/rds/rds_rdma.ko
kernel/net/rds/rds_tcp.ko
kernel/net/mac80211/mac80211.ko
kernel/net/tipc/tipc.ko
kernel/net/9p/9pnet.ko
kernel/net/9p/9pnet_virtio.ko
kernel/net/9p/9pnet_rdma.ko
kernel/net/wimax/wimax.ko
kernel/lib/crc-ccitt.ko
kernel/lib/crc-itu-t.ko
kernel/lib/crc7.ko
kernel/lib/libcrc32c.ko
kernel/lib/zlib_deflate/zlib_deflate.ko
kernel/lib/reed_solomon/reed_solomon.ko
kernel/lib/lzo/lzo_compress.ko
kernel/lib/lzo/lzo_decompress.ko
kernel/lib/ts_kmp.ko
kernel/lib/ts_bm.ko
kernel/lib/ts_fsm.ko
initrd/vesafb.ko
jutumang@jutumang-laptop:~$
```

Thanks for the reply!

---

### Post by RedStarYellowSun on 2010-05-13
> **bredman said:**
> I may have misread your original post.

If you know the name of your hardware (from the lshw command) just search the web for the words Ubuntu, module, and your hardware name.

To lshw:```
jutumang@jutumang-laptop:~$ lshw
WARNING: you should run this program as super-user.
jutumang-laptop           
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1972MiB
     *-cpu
          product: Intel(R) Core(TM)2 Duo CPU     T8300  @ 2.40GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.7.6
          serial: 0001-0676-0000-0000-0000-0000
          size: 800MHz
          capacity: 800MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm ida tpr_shadow vnmi flexpriority cpufreq
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: Mobile PM965/GM965/GL960 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 0c
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 0c
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:32 memory:f8100000-f81fffff memory:e0000000-efffffff(prefetchable) ioport:1800(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 0c
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: memory:f8200000-f82fffff
        *-network DISABLED
             description: Ethernet interface
             product: 82566MM Gigabit Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth0
             version: 03
             serial: 00:1c:25:be:c1:68
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=e1000e driverversion=1.0.2-k2 firmware=0.3-0 latency=0 multicast=yes
             resources: irq:29 memory:fe000000-fe01ffff memory:fe025000-fe025fff ioport:1840(size=32)
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:1860(size=32)
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:1880(size=32)
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:22 memory:fe226c00-fe226fff
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:17 memory:fe020000-fe023fff
        *-pci:0
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:2000(size=4096) memory:fc000000-fdffffff ioport:f8000000(size=1048576)
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:3000(size=4096) memory:dc000000-df3fffff ioport:dfe00000(size=1048576)
           *-network DISABLED
                description: Wireless interface
                product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 61
                serial: 00:21:5c:54:03:27
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
                resources: irq:31 memory:df3fe000-df3fffff
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:4000(size=4096) memory:d8000000-d9ffffff ioport:dfb00000(size=1048576)
        *-pci:3
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 ioport:5000(size=4096) memory:d4000000-d5ffffff ioport:df800000(size=1048576)
        *-pci:4
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
             resources: irq:28 ioport:6000(size=4096) memory:d0000000-d1ffffff ioport:df500000(size=1048576)
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:18a0(size=32)
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:18c0(size=32)
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:18e0(size=32)
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:19 memory:fe227000-fe2273ff
        *-pci:5
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f3
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             resources: ioport:7000(size=16384) memory:f8300000-fbffffff ioport:f4000000(size=67108864)
           *-pcmcia
                description: CardBus bridge
                product: RL5c476 II
                vendor: Ricoh Co Ltd
                physical id: 0
                bus info: pci@0000:15:00.0
                version: ba
                width: 64 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128
                resources: iomemory:b01716150-b0171614f irq:16 memory:f8300000-f8300fff ioport:7000(size=256) ioport:7400(size=256) memory:f4000000-f7ffffff(prefetchable) memory:80000000-83ffffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 0.1
                bus info: pci@0000:15:00.1
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=2
                resources: irq:17 memory:f8301000-f83017ff
           *-generic:0
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 0.2
                bus info: pci@0000:15:00.2
                version: 21
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci-pci latency=64
                resources: irq:18 memory:f8301800-f83018ff
           *-generic:1
                product: Illegal Vendor ID
                vendor: Illegal Vendor ID
                physical id: 0.3
                bus info: pci@0000:15:00.3
                version: ff
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master vga_palette cap_list
                configuration: driver=ricoh-mmc latency=255 maxlatency=255 mingnt=255
                resources: irq:11 memory:f8301c00-f8301cff
           *-generic:2 UNCLAIMED
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 0.4
                bus info: pci@0000:15:00.4
                version: 11
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: latency=0
                resources: memory:f8302000-f83020ff
           *-generic:3 UNCLAIMED
                description: System peripheral
                product: xD-Picture Card Controller
                vendor: Ricoh Co Ltd
                physical id: 0.5
                bus info: pci@0000:15:00.5
                version: 11
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: latency=0
                resources: memory:f8302400-f83024ff
        *-isa
             description: ISA bridge
             product: 82801HBM (ICH8M-E) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1c00(size=16)
           *-cdrom
                description: DVD reader
                product: DVD/CDRW UJDA775
                vendor: MATSHITA
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: CB03
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=nodisc
        *-storage
             description: SATA controller
             product: 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:30 ioport:1c50(size=8) ioport:1c44(size=4) ioport:1c48(size=8) ioport:1c40(size=4) ioport:1c20(size=32) memory:fe226000-fe2267ff
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fe227400-fe2274ff ioport:1c60(size=32)
  *-scsi
       physical id: 1
       bus info: scsi@5
       logical name: scsi5
       capabilities: scsi-host
       configuration: driver=usb-storage
jutumang@jutumang-laptop:~$
```

Thanks!

---

### Post by crowds0 on 2010-05-14
I'm having a very similar issue with my wireless.  I did an upgrade to 10.04 and the wireless was intermittently going out, then I restarted and it stopped working altogether.  I'm using the same wireless NIC (intel 4965 AGN) and the same iwlagn kernel module.  If I find a solution, i'll post back.

---

### Post by crowds0 on 2010-05-14
OK, the problem with the wireless not coming up for me was solved by reading this thread:

[https://bugs.launchpad.net/ubuntu/+bug/555571](https://bugs.launchpad.net/ubuntu/+bug/555571)
  
In
```
/var/lib/NetworkManager/NetworkManager.state
```

I had:
```
NetworkingEnabled=false
```

and it needed to be set to 'true'  I'm not sure why this configuration was changed when I upgraded.  I hope that helps.

---

### Post by speedotorpedo on 2010-05-15
I recently did a fresh install of 10.04 and my wifi stopped working. I fixed it by going to System>Administration>Hardware Drivers. I got dialog box that gave me the choice of two different drivers I could download and install. Maybe this helps or not, just trying to help......


Cheech

---

### Post by RedStarYellowSun on 2010-05-15
> **crowds0 said:**
> OK, the problem with the wireless not coming up for me was solved by reading this thread:

[https://bugs.launchpad.net/ubuntu/+bug/555571](https://bugs.launchpad.net/ubuntu/+bug/555571)
  
In
```
/var/lib/NetworkManager/NetworkManager.state
```

I had:
```
NetworkingEnabled=false
```

and it needed to be set to 'true'  I'm not sure why this configuration was changed when I upgraded.  I hope that helps.

How do you access it? I tried typing directly:```
/var/lib/NetworkManager/NetworkManager.state
```

But, all I got was: ```
bash: /var/lib/NetworkManager/NetworkManager.state: Permission denied
```

It tried nonetheless:```
NetworkingEnabled=false
```
But, I got no response.

How do I get permission?

Thanks for your time.

Take care,
RedStarYellowSun

---

### Post by AsianSpanker on 2010-05-17
> **speedotorpedo said:**
> I recently did a fresh install of 10.04 and my wifi stopped working. I fixed it by going to System>Administration>Hardware Drivers. I got dialog box that gave me the choice of two different drivers I could download and install. Maybe this helps or not, just trying to help......


Cheech
Yep, I went there, it says nothing! I have no drivers? It worked fine with
Ubuntu 9.04...Now what?

Please Please Please don't make me a slave to MacWindows! They take a bigger and bigger chunk of me till I am broke!!

---

### Post by anewguy on 2010-05-17
> **RedStarYellowSun said:**
> How do you access it? I tried typing directly:```
/var/lib/NetworkManager/NetworkManager.state
```

But, all I got was: ```
bash: /var/lib/NetworkManager/NetworkManager.state: Permission denied
```

It tried nonetheless:```
NetworkingEnabled=false
```
But, I got no response.

How do I get permission?

Thanks for your time.

Take care,
RedStarYellowSun


Here's the instructions:

- open a terminal window (Applications/Accessories/Terminal

- type (you can copy and paste this):

sudo cd /var/lib/NetworkManager 

- type (you can copy and paste this):

sudo gedit NetworkManager.state

Look for [main], in that section you should see the following line:

NetworkingEnabled=false

Change it to read:

NetworkingEnabled=true

click "Save" to save the file, then exit the editor and exit the terminal.

Now to just make things the easiest, just reboot.

Dave ;)

---

### Post by RedStarYellowSun on 2010-05-17
> **anewguy said:**
> Here's the instructions:

- open a terminal window (Applications/Accessories/Terminal

- type (you can copy and paste this):

sudo cd /var/lib/NetworkManager 

- type (you can copy and paste this):

sudo gedit NetworkManager.state

Look for [main], in that section you should see the following line:

NetworkingEnabled=false

Change it to read:

NetworkingEnabled=true

click "Save" to save the file, then exit the editor and exit the terminal.

Now to just make things the easiest, just reboot.

Dave ;)

I tried ```
sudo cd /var/lib/NetworkManager
```
But, I got:```
sudo: cd: command not found
```
Then, I tried to get past it with```
sudo gedit NetworkManager.state
```
But got a blank gedit Text Editor window the name "NetworkManager.state".

How can I make the first command be found?

Thanks for continuing to assist me.

Take care,
RedStarYellowSun

---

### Post by anewguy on 2010-05-18
I made a little boo-boo.  Here are the updated instructions - note that the "cd" command does not have "sudo" at the front of it:


- open a terminal window (Applications/Accessories/Terminal

- type (you can copy and paste this):

cd /var/lib/NetworkManager

- type (you can copy and paste this):

sudo gedit NetworkManager.state

Look for [main], in that section you should see the following line:

NetworkingEnabled=false

Change it to read:

NetworkingEnabled=true

click "Save" to save the file, then exit the editor and exit the terminal.

Now to just make things the easiest, just reboot.

Dave ;)

To explain a little:  some folders and files on the system are owned by root, and as such a normal user does not have access to them except for perhaps read access.  "sudo" is a way to temporarily grant you super user access so you can work with such files.

The "cd /var/lib/NetworkManager" changes the default folder you are working in to the /var/lib/NetworkManager folder.

The "sudo gedit NetworkManager.state" calls up the editor to edit the NetworkManager.state file. 

In your first attempt, due to my boo-boo, there was a "sudo" on the front of the command to change your default folder.  As a result, the command failed and you were left in the folder you were in.  Since there was no NetworkManager.state file there, the editor opened with a blank file.

Hope that helps explain things a little.

---

### Post by RedStarYellowSun on 2010-05-18
> **anewguy said:**
> I made a little boo-boo.  Here are the updated instructions - note that the "cd" command does not have "sudo" at the front of it:


- open a terminal window (Applications/Accessories/Terminal

- type (you can copy and paste this):

cd /var/lib/NetworkManager

- type (you can copy and paste this):

sudo gedit NetworkManager.state

Look for [main], in that section you should see the following line:

NetworkingEnabled=false

Change it to read:

NetworkingEnabled=true

click "Save" to save the file, then exit the editor and exit the terminal.

Now to just make things the easiest, just reboot.

Dave ;)

To explain a little:  some folders and files on the system are owned by root, and as such a normal user does not have access to them except for perhaps read access.  "sudo" is a way to temporarily grant you super user access so you can work with such files.

The "cd /var/lib/NetworkManager" changes the default folder you are working in to the /var/lib/NetworkManager folder.

The "sudo gedit NetworkManager.state" calls up the editor to edit the NetworkManager.state file. 

In your first attempt, due to my boo-boo, there was a "sudo" on the front of the command to change your default folder.  As a result, the command failed and you were left in the folder you were in.  Since there was no NetworkManager.state file there, the editor opened with a blank file.

Hope that helps explain things a little.
Thank you so much for your help!
I just connected to the Internet.

Thanks again!

Take care,
RedStarYellowSun

---

### Post by anewguy on 2010-05-18
Congrats!!  Glad I was able to help in a small way.

Dave ;)

---

### Post by Frenchy92 on 2010-08-08
I type:
cd/var/lib/NetworkManager

bash: cd/var/lib/NetworkManager: No such file or directory

I'm very confused because I had this very problem several weeks ago, and all the commands you typed in before worked but this time around they don't work and I don't know why.

---

### Post by linuxnomad4850 on 2010-08-08
was the previous version 32-bit or 64-bit? is the new version 32-bit or 
64-bit? when i had 64-bit on of 9.10 and 10.04 and i had the problem. but when i switched to 32-bit 10.04 it got rid of a lot of issues including fixing the wireless problem. good luck

---

