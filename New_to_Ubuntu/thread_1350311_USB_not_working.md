---
title: "USB not working?"
date: 2009-12-09
forum: New to Ubuntu
---

### Post by paulcupboard on 2009-12-09
Hi, 
 
I recently installed ubuntu and am struggling with it to be honest. I thought the days of having to use DOS like commands were way behind us... Anyway I want to keep at it.
 
The main problem I am having at the minute is that I have an external hard drive that I had used to back up stuff off windows and to use with my PS3. Its is partitioned. 
 
When I plug the USB from the external hard drive into the laptop runnning Ubuntu nothing happens. It doesnt show up. How do I see this external drive?
 
I have tried to install different programs to see if they can see it but nothing is seeing the drive. I know the drive is fully functioning. 
 
Thanks
 
*complete noob*
Paul

---

### Post by jagnikam on 2009-12-09
can u post dmesg log before and after plugin usb drive?

command to check log : dmesg

---

### Post by ukripper on 2009-12-09
disconnect and re-connect your usb drive and post output of these commands:
```
lsusb
```

```
dmesg | tail
```

---

### Post by paulcupboard on 2009-12-09
> **ukripper said:**
> disconnect and re-connect your usb drive and post output of these commands:
```
lsusb
``````
dmesg | tail
```

Ok, disconected and reconnected external drive

lsusb give the following results

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 005: ID 0a5c:4503 Broadcom Corp. 
Bus 003 Device 004: ID 0a5c:4502 Broadcom Corp. 
Bus 003 Device 003: ID 413c:8126 Dell Computer Corp. Wireless 355 Bluetooth
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


dmesg | tail gave 

[   52.607810] [drm] TV-14: set mode NTSC 480i 0
[   54.383838] [drm] TV-14: set mode NTSC 480i 0
[   54.524219] [drm] TV-14: set mode NTSC 480i 0
[   60.538428] wlan0: authenticate with AP 00:1b:2f:40:38:48
[   60.540048] wlan0: authenticated
[   60.540053] wlan0: associate with AP 00:1b:2f:40:38:48
[   60.543110] wlan0: RX AssocResp from 00:1b:2f:40:38:48 (capab=0x471 status=0 aid=1)
[   60.543116] wlan0: associated
[   60.546451] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   71.520212] wlan0: no IPv6 routers present

Thanks for looking at this with me. Fingers crossed I get it sorted.

---

### Post by paulcupboard on 2009-12-09
> **jagnikam said:**
> can u post dmesg log before and after plugin usb drive?

command to check log : dmesg

dmesg before I plug in the usb is 

[    0.529164] pci 0000:00:1c.0:   IO window: disabled
[    0.529177] pci 0000:00:1c.0:   MEM window: disabled
[    0.529188] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.529197] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:0c
[    0.529202] pci 0000:00:1c.1:   IO window: disabled
[    0.529216] pci 0000:00:1c.1:   MEM window: 0xfe800000-0xfe8fffff
[    0.529225] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.529236] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:0d
[    0.529244] pci 0000:00:1c.3:   IO window: 0xd000-0xdfff
[    0.529257] pci 0000:00:1c.3:   MEM window: 0xfe600000-0xfe7fffff
[    0.529267] pci 0000:00:1c.3:   PREFETCH window: 0x000000f0000000-0x000000f01fffff
[    0.529285] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[    0.529288] pci 0000:00:1e.0:   IO window: disabled
[    0.529301] pci 0000:00:1e.0:   MEM window: 0xfe500000-0xfe5fffff
[    0.529312] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.529337]   alloc irq_desc for 16 on node -1
[    0.529342]   alloc kstat_irqs on node -1
[    0.529354] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.529367] pci 0000:00:1c.0: setting latency timer to 64
[    0.529383]   alloc irq_desc for 17 on node -1
[    0.529388]   alloc kstat_irqs on node -1
[    0.529396] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.529408] pci 0000:00:1c.1: setting latency timer to 64
[    0.529424]   alloc irq_desc for 19 on node -1
[    0.529429]   alloc kstat_irqs on node -1
[    0.529437] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.529449] pci 0000:00:1c.3: setting latency timer to 64
[    0.529464] pci 0000:00:1e.0: setting latency timer to 64
[    0.529476] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.529482] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.529489] pci_bus 0000:0c: resource 1 mem: [0xfe800000-0xfe8fffff]
[    0.529496] pci_bus 0000:0d: resource 0 io:  [0xd000-0xdfff]
[    0.529502] pci_bus 0000:0d: resource 1 mem: [0xfe600000-0xfe7fffff]
[    0.529506] pci_bus 0000:0d: resource 2 pref mem [0xf0000000-0xf01fffff]
[    0.529513] pci_bus 0000:03: resource 1 mem: [0xfe500000-0xfe5fffff]
[    0.529519] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
[    0.529526] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffff]
[    0.529604] NET: Registered protocol family 2
[    0.529822] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.530551] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.531382] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.531812] TCP: Hash tables configured (established 131072 bind 65536)
[    0.531816] TCP reno registered
[    0.531971] NET: Registered protocol family 1
[    0.532131] Trying to unpack rootfs image as initramfs...
[    0.989652] Freeing initrd memory: 7789k freed
[    0.996630] Simple Boot Flag at 0x79 set to 0x1
[    0.997025] cpufreq-nforce2: No nForce2 chipset.
[    0.997085] Scanning for low memory corruption every 60 seconds
[    0.997307] audit: initializing netlink socket (disabled)
[    0.997342] type=2000 audit(1260375837.996:1): initialized
[    1.017665] highmem bounce pool size: 64 pages
[    1.017678] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.021214] VFS: Disk quotas dquot_6.5.2
[    1.021368] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.022634] fuse init (API version 7.12)
[    1.022830] msgmni has been set to 1706
[    1.023294] alg: No test for stdrng (krng)
[    1.023328] io scheduler noop registered
[    1.023331] io scheduler anticipatory registered
[    1.023337] io scheduler deadline registered
[    1.023432] io scheduler cfq registered (default)
[    1.023458] pci 0000:00:02.0: Boot video device
[    1.024001]   alloc irq_desc for 24 on node -1
[    1.024006]   alloc kstat_irqs on node -1
[    1.024058] pcieport-driver 0000:00:1c.0: irq 24 for MSI/MSI-X
[    1.024083] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.024396]   alloc irq_desc for 25 on node -1
[    1.024401]   alloc kstat_irqs on node -1
[    1.024418] pcieport-driver 0000:00:1c.1: irq 25 for MSI/MSI-X
[    1.024439] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    1.024731]   alloc irq_desc for 26 on node -1
[    1.024734]   alloc kstat_irqs on node -1
[    1.024752] pcieport-driver 0000:00:1c.3: irq 26 for MSI/MSI-X
[    1.024773] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    1.024994] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.025219] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.025563] ACPI: AC Adapter [AC] (off-line)
[    1.025737] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    1.026554] ACPI: Lid Switch [LID]
[    1.026662] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.026675] ACPI: Power Button [PBTN]
[    1.026779] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.026785] ACPI: Sleep Button [SBTN]
[    1.028238] ACPI: SSDT 7f66e4f2 00286 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    1.029358] ACPI: SSDT 7f66de88 005E5 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    1.030243] Monitor-Mwait will be used to enter C-1 state
[    1.030300] Monitor-Mwait will be used to enter C-2 state
[    1.030353] Monitor-Mwait will be used to enter C-3 state
[    1.030372] Marking TSC unstable due to TSC halts in idle
[    1.030409] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.030468] processor LNXCPU:00: registered as cooling_device0
[    1.030476] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.031204] ACPI: SSDT 7f66e778 000C4 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    1.031960] ACPI: SSDT 7f66e46d 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    1.033136] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    1.033192] processor LNXCPU:01: registered as cooling_device1
[    1.033201] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.046961] thermal LNXTHERM:01: registered as thermal_zone0
[    1.046981] ACPI: Thermal Zone [THM] (25 C)
[    1.047131] isapnp: Scanning for PnP cards...
[    1.161420] ACPI: Battery Slot [BAT0] (battery present)
[    1.429813] isapnp: No Plug & Play device found
[    1.432423] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.435503] brd: module loaded
[    1.436559] loop: module loaded
[    1.436711] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    1.436884] ahci 0000:00:1f.2: version 3.0
[    1.436911] ahci 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.436976]   alloc irq_desc for 27 on node -1
[    1.436981]   alloc kstat_irqs on node -1
[    1.437026] ahci 0000:00:1f.2: irq 27 for MSI/MSI-X
[    1.437147] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x5 impl SATA mode
[    1.437157] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ems 
[    1.437167] ahci 0000:00:1f.2: setting latency timer to 64
[    1.445119] scsi0 : ahci
[    1.445296] scsi1 : ahci
[    1.445423] scsi2 : ahci
[    1.445941] ata1: SATA max UDMA/133 abar m2048@0xfe9fb800 port 0xfe9fb900 irq 27
[    1.445945] ata2: DUMMY
[    1.445952] ata3: SATA max UDMA/133 abar m2048@0xfe9fb800 port 0xfe9fba00 irq 27
[    1.446066] ata_piix 0000:00:1f.1: version 2.13
[    1.446084] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.446158] ata_piix 0000:00:1f.1: setting latency timer to 64
[    1.446283] scsi3 : ata_piix
[    1.446407] scsi4 : ata_piix
[    1.447742] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x6fa0 irq 14
[    1.447749] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x6fa8 irq 15
[    1.449949] Fixed MDIO Bus: probed
[    1.450026] PPP generic driver version 2.4.2
[    1.450218] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.450254]   alloc irq_desc for 22 on node -1
[    1.450259]   alloc kstat_irqs on node -1
[    1.450271] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    1.450293] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    1.450300] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    1.450397] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    1.454330] ehci_hcd 0000:00:1a.7: debug port 1
[    1.454344] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    1.454392] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xfed1c400
[    1.454744] ata5: port disabled. ignoring.
[    1.469026] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    1.469183] usb usb1: configuration #1 chosen from 1 choice
[    1.469250] hub 1-0:1.0: USB hub found
[    1.469268] hub 1-0:1.0: 4 ports detected
[    1.469387]   alloc irq_desc for 20 on node -1
[    1.469392]   alloc kstat_irqs on node -1
[    1.469402] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.469422] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.469430] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.469501] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    1.473436] ehci_hcd 0000:00:1d.7: debug port 1
[    1.473449] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    1.473477] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfed1c000
[    1.488033] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.488192] usb usb2: configuration #1 chosen from 1 choice
[    1.488256] hub 2-0:1.0: USB hub found
[    1.488270] hub 2-0:1.0: 6 ports detected
[    1.488410] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.488450] uhci_hcd: USB Universal Host Controller Interface driver
[    1.488503] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.488517] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.488524] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    1.488606] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    1.488651] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00006f20
[    1.488819] usb usb3: configuration #1 chosen from 1 choice
[    1.488881] hub 3-0:1.0: USB hub found
[    1.488897] hub 3-0:1.0: 2 ports detected
[    1.489017]   alloc irq_desc for 21 on node -1
[    1.489023]   alloc kstat_irqs on node -1
[    1.489032] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.489046] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    1.489053] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    1.489121] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    1.489183] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00006f00
[    1.489354] usb usb4: configuration #1 chosen from 1 choice
[    1.489416] hub 4-0:1.0: USB hub found
[    1.489430] hub 4-0:1.0: 2 ports detected
[    1.489542] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.489556] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.489563] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.489631] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    1.489678] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00006f80
[    1.489848] usb usb5: configuration #1 chosen from 1 choice
[    1.489910] hub 5-0:1.0: USB hub found
[    1.489923] hub 5-0:1.0: 2 ports detected
[    1.490031] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.490045] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.490052] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.490119] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    1.490162] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00006f60
[    1.490338] usb usb6: configuration #1 chosen from 1 choice
[    1.490399] hub 6-0:1.0: USB hub found
[    1.490416] hub 6-0:1.0: 2 ports detected
[    1.490523] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    1.490537] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.490544] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.490625] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    1.490670] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00006f40
[    1.490842] usb usb7: configuration #1 chosen from 1 choice
[    1.490905] hub 7-0:1.0: USB hub found
[    1.490919] hub 7-0:1.0: 2 ports detected
[    1.491151] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.494615] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.494628] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.494749] mice: PS/2 mouse device common for all mice
[    1.494975] rtc_cmos 00:03: RTC can wake from S4
[    1.495047] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.495098] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.495327] device-mapper: uevent: version 1.0.3
[    1.495533] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    1.495720] device-mapper: multipath: version 1.1.0 loaded
[    1.495726] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.496002] EISA: Probing bus 0 at eisa.0
[    1.496083] EISA: Mainboard TG_FFFF detected.
[    1.496117] Cannot allocate resource for EISA slot 1
[    1.496169] EISA: Detected 0 cards.
[    1.496519] cpuidle: using governor ladder
[    1.496802] cpuidle: using governor menu
[    1.498011] TCP cubic registered
[    1.498373] NET: Registered protocol family 10
[    1.498614] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.499485] lo: Disabled Privacy Extensions
[    1.500323] NET: Registered protocol family 17
[    1.500359] Bluetooth: L2CAP ver 2.13
[    1.500364] Bluetooth: L2CAP socket layer initialized
[    1.500370] Bluetooth: SCO (Voice Link) ver 0.6
[    1.500375] Bluetooth: SCO socket layer initialized
[    1.500459] Bluetooth: RFCOMM TTY layer initialized
[    1.500466] Bluetooth: RFCOMM socket layer initialized
[    1.500472] Bluetooth: RFCOMM ver 1.11
[    1.501589] Using IPI No-Shortcut mode
[    1.501667] PM: Resume from disk failed.
[    1.501683] registered taskstats version 1
[    1.501837]   Magic number: 5:233:388
[    1.501844] usb usb6: hash matches
[    1.501971] rtc_cmos 00:03: setting system clock to 2009-12-09 16:23:58 UTC (1260375838)
[    1.501974] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.501978] EDD information not available.
[    1.632781] ata4.00: ATAPI: TSSTcorp DVD+/-RW TS-L632H, D300, max UDMA/33
[    1.664635] ata4.00: configured for UDMA/33
[    1.764279] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.776103] ata3: SATA link down (SStatus 0 SControl 300)
[    1.807742] ata1.00: ATA-8: WDC WD1600BEVT-00ZCT0, 11.01A11, max UDMA/133
[    1.807749] ata1.00: 312581808 sectors, multi 8: LBA48 NCQ (depth 31/32)
[    1.809192] ata1.00: configured for UDMA/133
[    1.824466] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600BEVT-0 11.0 PQ: 0 ANSI: 5
[    1.824610] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.824667] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.824729] sd 0:0:0:0: [sda] Write Protect is off
[    1.824733] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.824764] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.824926]  sda:
[    1.830181] scsi 3:0:0:0: CD-ROM            TSSTcorp DVD+-RW TS-L632H D300 PQ: 0 ANSI: 5
[    1.832839]  sda1 sda2 <sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    1.842833] Uniform CD-ROM driver Revision: 3.20
[    1.843010] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    1.843057] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    1.862542]  sda5 >
[    1.862952] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.862998] Freeing unused kernel memory: 540k freed
[    1.863461] Write protecting the kernel text: 4568k
[    1.863542] Write protecting the kernel read-only data: 1836k
[    1.893060] usb 2-6: new high speed USB device using ehci_hcd and address 2
[    2.001028] Clocksource tsc unstable (delta = -265055643 ns)
[    2.031800] Linux agpgart interface v0.103
[    2.046423] usb 2-6: configuration #1 chosen from 1 choice
[    2.055740] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
[    2.056344] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
[    2.059764] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[    2.113113] [drm] Initialized drm 1.1.0 20060810
[    2.169983] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.169995] i915 0000:00:02.0: setting latency timer to 64
[    2.174571]   alloc irq_desc for 28 on node -1
[    2.174578]   alloc kstat_irqs on node -1
[    2.174598] i915 0000:00:02.0: irq 28 for MSI/MSI-X
[    2.323646] b44 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.392140] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[    2.392191] b44.c:v2.0
[    2.392245] ohci1394 0000:03:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.413818] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:1d:09:bd:b4:de
[    2.454096] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[fe5fd800-fe5fdfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    2.500507] usb 3-2: new full speed USB device using uhci_hcd and address 2
[    2.659452] [drm] TV-14: set mode NTSC 480i 0
[    2.779499] usb 3-2: configuration #1 chosen from 1 choice
[    2.791976] [drm] fb0: inteldrmfb frame buffer device
[    2.792130] hub 3-2:1.0: USB hub found
[    2.794241] hub 3-2:1.0: 3 ports detected
[    2.815800] acpi device:37: registered as cooling_device2
[    2.816812] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:34/input/input5
[    2.816880] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[    2.817001] ACPI Warning: \_SB_.PCI0.VID2._DOD: Return Package has no elements (empty) 20090521 nspredef-434
[    2.817178] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:39/input/input6
[    2.817237] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[    2.817282] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    2.893969] [drm] LVDS-8: set mode 1280x800 17
[    3.074790] usb 3-2.1: new full speed USB device using uhci_hcd and address 3
[    3.202946] usb 3-2.1: configuration #1 chosen from 1 choice
[    3.232188] Console: switching to colour frame buffer device 160x50
[    3.282909] usb 3-2.2: new full speed USB device using uhci_hcd and address 4
[    3.413588] usb 3-2.2: configuration #1 chosen from 1 choice
[    3.429873] usbcore: registered new interface driver hiddev
[    3.433412] input: Broadcom Corp as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2.2/3-2.2:1.0/input/input7
[    3.433561] generic-usb 0003:0A5C:4502.0001: input,hidraw0: USB HID v1.11 Keyboard [Broadcom Corp] on usb-0000:00:1a.0-2.2/input0
[    3.433596] usbcore: registered new interface driver usbhid
[    3.433602] usbhid: v2.6:USB HID core driver
[    3.505810] usb 3-2.3: new full speed USB device using uhci_hcd and address 5
[    3.658040] usb 3-2.3: configuration #1 chosen from 1 choice
[    3.692762] input: Broadcom Corp as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2.3/3-2.3:1.0/input/input8
[    3.692940] generic-usb 0003:0A5C:4503.0002: input,hidraw1: USB HID v1.11 Mouse [Broadcom Corp] on usb-0000:00:1a.0-2.3/input0
[    3.740242] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[474fc000030e3070]
[    3.970451] PM: Starting manual resume from disk
[    3.970460] PM: Resume from partition 8:5
[    3.970465] PM: Checking hibernation image.
[    3.970662] PM: Resume from disk failed.
[    4.021063] EXT4-fs (sda1): barriers enabled
[    4.042289] kjournald2 starting: pid 431, dev sda1:8, commit interval 5 seconds
[    4.042345] EXT4-fs (sda1): delayed allocation enabled
[    4.042355] EXT4-fs: file extents enabled
[    4.073364] EXT4-fs: mballoc enabled
[    4.073396] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    4.841298] type=1505 audit(1260375841.838:2): operation="profile_load" pid=458 name=/usr/share/gdm/guest-session/Xsession
[    4.846967] type=1505 audit(1260375841.843:3): operation="profile_load" pid=459 name=/sbin/dhclient3
[    4.848824] type=1505 audit(1260375841.843:4): operation="profile_load" pid=459 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    4.849823] type=1505 audit(1260375841.847:5): operation="profile_load" pid=459 name=/usr/lib/connman/scripts/dhclient-script
[    4.904261] type=1505 audit(1260375841.898:6): operation="profile_load" pid=460 name=/usr/bin/evince
[    4.933821] type=1505 audit(1260375841.931:7): operation="profile_load" pid=460 name=/usr/bin/evince-previewer
[    4.951166] type=1505 audit(1260375841.947:8): operation="profile_load" pid=460 name=/usr/bin/evince-thumbnailer
[    4.998603] type=1505 audit(1260375841.995:9): operation="profile_load" pid=462 name=/usr/lib/cups/backend/cups-pdf
[    5.000793] type=1505 audit(1260375841.995:10): operation="profile_load" pid=462 name=/usr/sbin/cupsd
[    6.272093] Adding 6008268k swap on /dev/sda5.  Priority:-1 extents:1 across:6008268k 
[    6.464089] EXT4-fs (sda1): internal journal on sda1:8
[    7.065674] udev: starting version 147
[    7.989046] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[    8.041081] Bluetooth: Generic Bluetooth USB driver ver 0.5
[    8.041379] usbcore: registered new interface driver btusb
[    8.100281] cfg80211: Calling CRDA to update world regulatory domain
[    8.120721] ricoh-mmc: Ricoh MMC Controller disabling driver
[    8.120729] ricoh-mmc: Copyright(c) Philip Langdale
[    8.120788] ricoh-mmc: Ricoh MMC controller found at 0000:03:01.2 [1180:0843] (rev 12)
[    8.120825] ricoh-mmc: Controller is now disabled.
[    8.149580] sdhci: Secure Digital Host Controller Interface driver
[    8.149587] sdhci: Copyright(c) Pierre Ossman
[    8.166675] input: Dell WMI hotkeys as /devices/virtual/input/input9
[    8.189821] sdhci-pci 0000:03:01.1: SDHCI controller found [1180:0822] (rev 22)
[    8.189853]   alloc irq_desc for 18 on node -1
[    8.189859]   alloc kstat_irqs on node -1
[    8.189873] sdhci-pci 0000:03:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    8.192023] Registered led device: mmc0::
[    8.193090] mmc0: SDHCI controller on PCI [0000:03:01.1] using DMA
[    8.252352] lp: driver loaded but no devices found
[    8.299663] Linux video capture interface: v2.00
[    8.578479] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:2640)
[    8.579549] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[    8.580303] input: Laptop Integrated Webcam as /devices/pci0000:00/0000:00:1d.7/usb2/2-6/2-6:1.0/input/input10
[    8.580439] usbcore: registered new interface driver uvcvideo
[    8.580447] USB Video Class driver (v0.1.0)
[    8.586201] mmc0: new SD card at address 19bb
[    8.703066] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[    8.703074] iwl3945: Copyright(c) 2003-2009 Intel Corporation
[    8.703252] iwl3945 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    8.703273] iwl3945 0000:0c:00.0: setting latency timer to 64
[    8.759939] cfg80211: World regulatory domain updated:
[    8.759947]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    8.759954]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.759961]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    8.759968]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    8.759974]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.759980]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.771097] mmcblk0: mmc0:19bb SD512 488 MiB 
[    8.771194]  mmcblk0: p1
[    8.782417] iwl3945 0000:0c:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[    8.782426] iwl3945 0000:0c:00.0: Detected Intel Wireless WiFi Link 3945ABG
[    8.782571]   alloc irq_desc for 29 on node -1
[    8.782576]   alloc kstat_irqs on node -1
[    8.782621] iwl3945 0000:0c:00.0: irq 29 for MSI/MSI-X
[    8.814543] ip_tables: (C) 2000-2006 Netfilter Core Team
[    8.962017] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04793/0x300000
[    8.962030] serio: Synaptics pass-through port at isa0060/serio1/input0
[    9.012152] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input11
[    9.207109] phy0: Selected rate control algorithm 'iwl-3945-rs'
[    9.461910] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    9.461964] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    9.566061] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input12
[    9.624574] input: HDA Intel Mic at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[    9.624749] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[   10.233089] __ratelimit: 3 callbacks suppressed
[   10.233097] type=1505 audit(1260375847.231:12): operation="profile_replace" pid=944 name=/usr/share/gdm/guest-session/Xsession
[   10.237441] type=1505 audit(1260375847.235:13): operation="profile_replace" pid=945 name=/sbin/dhclient3
[   10.239285] type=1505 audit(1260375847.235:14): operation="profile_replace" pid=945 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   10.240308] type=1505 audit(1260375847.235:15): operation="profile_replace" pid=945 name=/usr/lib/connman/scripts/dhclient-script
[   10.249453] type=1505 audit(1260375847.247:16): operation="profile_replace" pid=947 name=/usr/bin/evince
[   10.280004] type=1505 audit(1260375847.275:17): operation="profile_replace" pid=947 name=/usr/bin/evince-previewer
[   10.298379] type=1505 audit(1260375847.295:18): operation="profile_replace" pid=947 name=/usr/bin/evince-thumbnailer
[   10.322815] type=1505 audit(1260375847.319:19): operation="profile_replace" pid=949 name=/usr/lib/cups/backend/cups-pdf
[   10.324952] type=1505 audit(1260375847.319:20): operation="profile_replace" pid=949 name=/usr/sbin/cupsd
[   10.331060] type=1505 audit(1260375847.327:21): operation="profile_replace" pid=950 name=/usr/sbin/tcpdump
[   10.341336] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   10.341344] Bluetooth: BNEP filters: protocol multicast
[   10.529111] Bridge firewalling registered
[   12.598951] iwl3945 0000:0c:00.0: firmware: requesting iwlwifi-3945-2.ucode
[   13.004678] iwl3945 0000:0c:00.0: loaded firmware version 15.32.2.9
[   13.081665] Registered led device: iwl-phy0::radio
[   13.081699] Registered led device: iwl-phy0::assoc
[   13.081728] Registered led device: iwl-phy0::RX
[   13.081756] Registered led device: iwl-phy0::TX
[   13.101017] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   13.105935] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.872643] [drm] TV-14: set mode NTSC 480i 0
[   17.017785] [drm] TV-14: set mode NTSC 480i 0
[   17.334936] [drm] TV-14: set mode NTSC 480i 0
[   17.505311] [drm] TV-14: set mode NTSC 480i 0
[   21.673040] ppdev: user-space parallel port driver
[   25.167486] [drm] TV-14: set mode NTSC 480i 0
[   25.308514] [drm] TV-14: set mode NTSC 480i 0
[   25.575715] [drm] TV-14: set mode NTSC 480i 0
[   25.716812] [drm] TV-14: set mode NTSC 480i 0
[   26.019417] [drm] TV-14: set mode NTSC 480i 0
[   26.160141] [drm] TV-14: set mode NTSC 480i 0
[   49.396673] padlock: VIA PadLock not detected.
[   51.657022] [drm] TV-14: set mode NTSC 480i 0
[   51.797247] [drm] TV-14: set mode NTSC 480i 0
[   52.063890] [drm] TV-14: set mode NTSC 480i 0
[   52.204549] [drm] TV-14: set mode NTSC 480i 0
[   52.467861] [drm] TV-14: set mode NTSC 480i 0
[   52.607810] [drm] TV-14: set mode NTSC 480i 0
[   54.383838] [drm] TV-14: set mode NTSC 480i 0
[   54.524219] [drm] TV-14: set mode NTSC 480i 0
[   60.538428] wlan0: authenticate with AP 00:1b:2f:40:38:48
[   60.540048] wlan0: authenticated
[   60.540053] wlan0: associate with AP 00:1b:2f:40:38:48
[   60.543110] wlan0: RX AssocResp from 00:1b:2f:40:38:48 (capab=0x471 status=0 aid=1)
[   60.543116] wlan0: associated
[   60.546451] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   71.520212] wlan0: no IPv6 routers present



 and after i plug it in it is

 
[    0.529177] pci 0000:00:1c.0:   MEM window: disabled
[    0.529188] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.529197] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:0c
[    0.529202] pci 0000:00:1c.1:   IO window: disabled
[    0.529216] pci 0000:00:1c.1:   MEM window: 0xfe800000-0xfe8fffff
[    0.529225] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.529236] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:0d
[    0.529244] pci 0000:00:1c.3:   IO window: 0xd000-0xdfff
[    0.529257] pci 0000:00:1c.3:   MEM window: 0xfe600000-0xfe7fffff
[    0.529267] pci 0000:00:1c.3:   PREFETCH window: 0x000000f0000000-0x000000f01fffff
[    0.529285] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[    0.529288] pci 0000:00:1e.0:   IO window: disabled
[    0.529301] pci 0000:00:1e.0:   MEM window: 0xfe500000-0xfe5fffff
[    0.529312] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.529337]   alloc irq_desc for 16 on node -1
[    0.529342]   alloc kstat_irqs on node -1
[    0.529354] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.529367] pci 0000:00:1c.0: setting latency timer to 64
[    0.529383]   alloc irq_desc for 17 on node -1
[    0.529388]   alloc kstat_irqs on node -1
[    0.529396] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.529408] pci 0000:00:1c.1: setting latency timer to 64
[    0.529424]   alloc irq_desc for 19 on node -1
[    0.529429]   alloc kstat_irqs on node -1
[    0.529437] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.529449] pci 0000:00:1c.3: setting latency timer to 64
[    0.529464] pci 0000:00:1e.0: setting latency timer to 64
[    0.529476] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.529482] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.529489] pci_bus 0000:0c: resource 1 mem: [0xfe800000-0xfe8fffff]
[    0.529496] pci_bus 0000:0d: resource 0 io:  [0xd000-0xdfff]
[    0.529502] pci_bus 0000:0d: resource 1 mem: [0xfe600000-0xfe7fffff]
[    0.529506] pci_bus 0000:0d: resource 2 pref mem [0xf0000000-0xf01fffff]
[    0.529513] pci_bus 0000:03: resource 1 mem: [0xfe500000-0xfe5fffff]
[    0.529519] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
[    0.529526] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffff]
[    0.529604] NET: Registered protocol family 2
[    0.529822] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.530551] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.531382] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.531812] TCP: Hash tables configured (established 131072 bind 65536)
[    0.531816] TCP reno registered
[    0.531971] NET: Registered protocol family 1
[    0.532131] Trying to unpack rootfs image as initramfs...
[    0.989652] Freeing initrd memory: 7789k freed
[    0.996630] Simple Boot Flag at 0x79 set to 0x1
[    0.997025] cpufreq-nforce2: No nForce2 chipset.
[    0.997085] Scanning for low memory corruption every 60 seconds
[    0.997307] audit: initializing netlink socket (disabled)
[    0.997342] type=2000 audit(1260375837.996:1): initialized
[    1.017665] highmem bounce pool size: 64 pages
[    1.017678] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.021214] VFS: Disk quotas dquot_6.5.2
[    1.021368] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.022634] fuse init (API version 7.12)
[    1.022830] msgmni has been set to 1706
[    1.023294] alg: No test for stdrng (krng)
[    1.023328] io scheduler noop registered
[    1.023331] io scheduler anticipatory registered
[    1.023337] io scheduler deadline registered
[    1.023432] io scheduler cfq registered (default)
[    1.023458] pci 0000:00:02.0: Boot video device
[    1.024001]   alloc irq_desc for 24 on node -1
[    1.024006]   alloc kstat_irqs on node -1
[    1.024058] pcieport-driver 0000:00:1c.0: irq 24 for MSI/MSI-X
[    1.024083] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.024396]   alloc irq_desc for 25 on node -1
[    1.024401]   alloc kstat_irqs on node -1
[    1.024418] pcieport-driver 0000:00:1c.1: irq 25 for MSI/MSI-X
[    1.024439] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    1.024731]   alloc irq_desc for 26 on node -1
[    1.024734]   alloc kstat_irqs on node -1
[    1.024752] pcieport-driver 0000:00:1c.3: irq 26 for MSI/MSI-X
[    1.024773] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    1.024994] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.025219] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.025563] ACPI: AC Adapter [AC] (off-line)
[    1.025737] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    1.026554] ACPI: Lid Switch [LID]
[    1.026662] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.026675] ACPI: Power Button [PBTN]
[    1.026779] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.026785] ACPI: Sleep Button [SBTN]
[    1.028238] ACPI: SSDT 7f66e4f2 00286 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    1.029358] ACPI: SSDT 7f66de88 005E5 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    1.030243] Monitor-Mwait will be used to enter C-1 state
[    1.030300] Monitor-Mwait will be used to enter C-2 state
[    1.030353] Monitor-Mwait will be used to enter C-3 state
[    1.030372] Marking TSC unstable due to TSC halts in idle
[    1.030409] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.030468] processor LNXCPU:00: registered as cooling_device0
[    1.030476] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.031204] ACPI: SSDT 7f66e778 000C4 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    1.031960] ACPI: SSDT 7f66e46d 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    1.033136] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    1.033192] processor LNXCPU:01: registered as cooling_device1
[    1.033201] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.046961] thermal LNXTHERM:01: registered as thermal_zone0
[    1.046981] ACPI: Thermal Zone [THM] (25 C)
[    1.047131] isapnp: Scanning for PnP cards...
[    1.161420] ACPI: Battery Slot [BAT0] (battery present)
[    1.429813] isapnp: No Plug & Play device found
[    1.432423] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.435503] brd: module loaded
[    1.436559] loop: module loaded
[    1.436711] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    1.436884] ahci 0000:00:1f.2: version 3.0
[    1.436911] ahci 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.436976]   alloc irq_desc for 27 on node -1
[    1.436981]   alloc kstat_irqs on node -1
[    1.437026] ahci 0000:00:1f.2: irq 27 for MSI/MSI-X
[    1.437147] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x5 impl SATA mode
[    1.437157] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ems 
[    1.437167] ahci 0000:00:1f.2: setting latency timer to 64
[    1.445119] scsi0 : ahci
[    1.445296] scsi1 : ahci
[    1.445423] scsi2 : ahci
[    1.445941] ata1: SATA max UDMA/133 abar m2048@0xfe9fb800 port 0xfe9fb900 irq 27
[    1.445945] ata2: DUMMY
[    1.445952] ata3: SATA max UDMA/133 abar m2048@0xfe9fb800 port 0xfe9fba00 irq 27
[    1.446066] ata_piix 0000:00:1f.1: version 2.13
[    1.446084] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.446158] ata_piix 0000:00:1f.1: setting latency timer to 64
[    1.446283] scsi3 : ata_piix
[    1.446407] scsi4 : ata_piix
[    1.447742] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x6fa0 irq 14
[    1.447749] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x6fa8 irq 15
[    1.449949] Fixed MDIO Bus: probed
[    1.450026] PPP generic driver version 2.4.2
[    1.450218] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.450254]   alloc irq_desc for 22 on node -1
[    1.450259]   alloc kstat_irqs on node -1
[    1.450271] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    1.450293] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    1.450300] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    1.450397] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    1.454330] ehci_hcd 0000:00:1a.7: debug port 1
[    1.454344] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    1.454392] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xfed1c400
[    1.454744] ata5: port disabled. ignoring.
[    1.469026] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    1.469183] usb usb1: configuration #1 chosen from 1 choice
[    1.469250] hub 1-0:1.0: USB hub found
[    1.469268] hub 1-0:1.0: 4 ports detected
[    1.469387]   alloc irq_desc for 20 on node -1
[    1.469392]   alloc kstat_irqs on node -1
[    1.469402] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.469422] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.469430] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.469501] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    1.473436] ehci_hcd 0000:00:1d.7: debug port 1
[    1.473449] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    1.473477] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfed1c000
[    1.488033] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.488192] usb usb2: configuration #1 chosen from 1 choice
[    1.488256] hub 2-0:1.0: USB hub found
[    1.488270] hub 2-0:1.0: 6 ports detected
[    1.488410] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.488450] uhci_hcd: USB Universal Host Controller Interface driver
[    1.488503] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.488517] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.488524] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    1.488606] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    1.488651] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00006f20
[    1.488819] usb usb3: configuration #1 chosen from 1 choice
[    1.488881] hub 3-0:1.0: USB hub found
[    1.488897] hub 3-0:1.0: 2 ports detected
[    1.489017]   alloc irq_desc for 21 on node -1
[    1.489023]   alloc kstat_irqs on node -1
[    1.489032] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.489046] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    1.489053] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    1.489121] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    1.489183] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00006f00
[    1.489354] usb usb4: configuration #1 chosen from 1 choice
[    1.489416] hub 4-0:1.0: USB hub found
[    1.489430] hub 4-0:1.0: 2 ports detected
[    1.489542] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.489556] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.489563] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.489631] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    1.489678] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00006f80
[    1.489848] usb usb5: configuration #1 chosen from 1 choice
[    1.489910] hub 5-0:1.0: USB hub found
[    1.489923] hub 5-0:1.0: 2 ports detected
[    1.490031] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.490045] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.490052] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.490119] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    1.490162] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00006f60
[    1.490338] usb usb6: configuration #1 chosen from 1 choice
[    1.490399] hub 6-0:1.0: USB hub found
[    1.490416] hub 6-0:1.0: 2 ports detected
[    1.490523] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    1.490537] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.490544] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.490625] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    1.490670] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00006f40
[    1.490842] usb usb7: configuration #1 chosen from 1 choice
[    1.490905] hub 7-0:1.0: USB hub found
[    1.490919] hub 7-0:1.0: 2 ports detected
[    1.491151] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.494615] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.494628] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.494749] mice: PS/2 mouse device common for all mice
[    1.494975] rtc_cmos 00:03: RTC can wake from S4
[    1.495047] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.495098] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.495327] device-mapper: uevent: version 1.0.3
[    1.495533] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    1.495720] device-mapper: multipath: version 1.1.0 loaded
[    1.495726] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.496002] EISA: Probing bus 0 at eisa.0
[    1.496083] EISA: Mainboard TG_FFFF detected.
[    1.496117] Cannot allocate resource for EISA slot 1
[    1.496169] EISA: Detected 0 cards.
[    1.496519] cpuidle: using governor ladder
[    1.496802] cpuidle: using governor menu
[    1.498011] TCP cubic registered
[    1.498373] NET: Registered protocol family 10
[    1.498614] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.499485] lo: Disabled Privacy Extensions
[    1.500323] NET: Registered protocol family 17
[    1.500359] Bluetooth: L2CAP ver 2.13
[    1.500364] Bluetooth: L2CAP socket layer initialized
[    1.500370] Bluetooth: SCO (Voice Link) ver 0.6
[    1.500375] Bluetooth: SCO socket layer initialized
[    1.500459] Bluetooth: RFCOMM TTY layer initialized
[    1.500466] Bluetooth: RFCOMM socket layer initialized
[    1.500472] Bluetooth: RFCOMM ver 1.11
[    1.501589] Using IPI No-Shortcut mode
[    1.501667] PM: Resume from disk failed.
[    1.501683] registered taskstats version 1
[    1.501837]   Magic number: 5:233:388
[    1.501844] usb usb6: hash matches
[    1.501971] rtc_cmos 00:03: setting system clock to 2009-12-09 16:23:58 UTC (1260375838)
[    1.501974] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.501978] EDD information not available.
[    1.632781] ata4.00: ATAPI: TSSTcorp DVD+/-RW TS-L632H, D300, max UDMA/33
[    1.664635] ata4.00: configured for UDMA/33
[    1.764279] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.776103] ata3: SATA link down (SStatus 0 SControl 300)
[    1.807742] ata1.00: ATA-8: WDC WD1600BEVT-00ZCT0, 11.01A11, max UDMA/133
[    1.807749] ata1.00: 312581808 sectors, multi 8: LBA48 NCQ (depth 31/32)
[    1.809192] ata1.00: configured for UDMA/133
[    1.824466] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600BEVT-0 11.0 PQ: 0 ANSI: 5
[    1.824610] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.824667] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.824729] sd 0:0:0:0: [sda] Write Protect is off
[    1.824733] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.824764] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.824926]  sda:
[    1.830181] scsi 3:0:0:0: CD-ROM            TSSTcorp DVD+-RW TS-L632H D300 PQ: 0 ANSI: 5
[    1.832839]  sda1 sda2 <sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    1.842833] Uniform CD-ROM driver Revision: 3.20
[    1.843010] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    1.843057] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    1.862542]  sda5 >
[    1.862952] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.862998] Freeing unused kernel memory: 540k freed
[    1.863461] Write protecting the kernel text: 4568k
[    1.863542] Write protecting the kernel read-only data: 1836k
[    1.893060] usb 2-6: new high speed USB device using ehci_hcd and address 2
[    2.001028] Clocksource tsc unstable (delta = -265055643 ns)
[    2.031800] Linux agpgart interface v0.103
[    2.046423] usb 2-6: configuration #1 chosen from 1 choice
[    2.055740] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
[    2.056344] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
[    2.059764] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[    2.113113] [drm] Initialized drm 1.1.0 20060810
[    2.169983] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.169995] i915 0000:00:02.0: setting latency timer to 64
[    2.174571]   alloc irq_desc for 28 on node -1
[    2.174578]   alloc kstat_irqs on node -1
[    2.174598] i915 0000:00:02.0: irq 28 for MSI/MSI-X
[    2.323646] b44 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.392140] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[    2.392191] b44.c:v2.0
[    2.392245] ohci1394 0000:03:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.413818] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:1d:09:bd:b4:de
[    2.454096] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[fe5fd800-fe5fdfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    2.500507] usb 3-2: new full speed USB device using uhci_hcd and address 2
[    2.659452] [drm] TV-14: set mode NTSC 480i 0
[    2.779499] usb 3-2: configuration #1 chosen from 1 choice
[    2.791976] [drm] fb0: inteldrmfb frame buffer device
[    2.792130] hub 3-2:1.0: USB hub found
[    2.794241] hub 3-2:1.0: 3 ports detected
[    2.815800] acpi device:37: registered as cooling_device2
[    2.816812] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:34/input/input5
[    2.816880] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[    2.817001] ACPI Warning: \_SB_.PCI0.VID2._DOD: Return Package has no elements (empty) 20090521 nspredef-434
[    2.817178] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:39/input/input6
[    2.817237] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[    2.817282] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    2.893969] [drm] LVDS-8: set mode 1280x800 17
[    3.074790] usb 3-2.1: new full speed USB device using uhci_hcd and address 3
[    3.202946] usb 3-2.1: configuration #1 chosen from 1 choice
[    3.232188] Console: switching to colour frame buffer device 160x50
[    3.282909] usb 3-2.2: new full speed USB device using uhci_hcd and address 4
[    3.413588] usb 3-2.2: configuration #1 chosen from 1 choice
[    3.429873] usbcore: registered new interface driver hiddev
[    3.433412] input: Broadcom Corp as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2.2/3-2.2:1.0/input/input7
[    3.433561] generic-usb 0003:0A5C:4502.0001: input,hidraw0: USB HID v1.11 Keyboard [Broadcom Corp] on usb-0000:00:1a.0-2.2/input0
[    3.433596] usbcore: registered new interface driver usbhid
[    3.433602] usbhid: v2.6:USB HID core driver
[    3.505810] usb 3-2.3: new full speed USB device using uhci_hcd and address 5
[    3.658040] usb 3-2.3: configuration #1 chosen from 1 choice
[    3.692762] input: Broadcom Corp as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2.3/3-2.3:1.0/input/input8
[    3.692940] generic-usb 0003:0A5C:4503.0002: input,hidraw1: USB HID v1.11 Mouse [Broadcom Corp] on usb-0000:00:1a.0-2.3/input0
[    3.740242] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[474fc000030e3070]
[    3.970451] PM: Starting manual resume from disk
[    3.970460] PM: Resume from partition 8:5
[    3.970465] PM: Checking hibernation image.
[    3.970662] PM: Resume from disk failed.
[    4.021063] EXT4-fs (sda1): barriers enabled
[    4.042289] kjournald2 starting: pid 431, dev sda1:8, commit interval 5 seconds
[    4.042345] EXT4-fs (sda1): delayed allocation enabled
[    4.042355] EXT4-fs: file extents enabled
[    4.073364] EXT4-fs: mballoc enabled
[    4.073396] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    4.841298] type=1505 audit(1260375841.838:2): operation="profile_load" pid=458 name=/usr/share/gdm/guest-session/Xsession
[    4.846967] type=1505 audit(1260375841.843:3): operation="profile_load" pid=459 name=/sbin/dhclient3
[    4.848824] type=1505 audit(1260375841.843:4): operation="profile_load" pid=459 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    4.849823] type=1505 audit(1260375841.847:5): operation="profile_load" pid=459 name=/usr/lib/connman/scripts/dhclient-script
[    4.904261] type=1505 audit(1260375841.898:6): operation="profile_load" pid=460 name=/usr/bin/evince
[    4.933821] type=1505 audit(1260375841.931:7): operation="profile_load" pid=460 name=/usr/bin/evince-previewer
[    4.951166] type=1505 audit(1260375841.947:8): operation="profile_load" pid=460 name=/usr/bin/evince-thumbnailer
[    4.998603] type=1505 audit(1260375841.995:9): operation="profile_load" pid=462 name=/usr/lib/cups/backend/cups-pdf
[    5.000793] type=1505 audit(1260375841.995:10): operation="profile_load" pid=462 name=/usr/sbin/cupsd
[    6.272093] Adding 6008268k swap on /dev/sda5.  Priority:-1 extents:1 across:6008268k 
[    6.464089] EXT4-fs (sda1): internal journal on sda1:8
[    7.065674] udev: starting version 147
[    7.989046] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[    8.041081] Bluetooth: Generic Bluetooth USB driver ver 0.5
[    8.041379] usbcore: registered new interface driver btusb
[    8.100281] cfg80211: Calling CRDA to update world regulatory domain
[    8.120721] ricoh-mmc: Ricoh MMC Controller disabling driver
[    8.120729] ricoh-mmc: Copyright(c) Philip Langdale
[    8.120788] ricoh-mmc: Ricoh MMC controller found at 0000:03:01.2 [1180:0843] (rev 12)
[    8.120825] ricoh-mmc: Controller is now disabled.
[    8.149580] sdhci: Secure Digital Host Controller Interface driver
[    8.149587] sdhci: Copyright(c) Pierre Ossman
[    8.166675] input: Dell WMI hotkeys as /devices/virtual/input/input9
[    8.189821] sdhci-pci 0000:03:01.1: SDHCI controller found [1180:0822] (rev 22)
[    8.189853]   alloc irq_desc for 18 on node -1
[    8.189859]   alloc kstat_irqs on node -1
[    8.189873] sdhci-pci 0000:03:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    8.192023] Registered led device: mmc0::
[    8.193090] mmc0: SDHCI controller on PCI [0000:03:01.1] using DMA
[    8.252352] lp: driver loaded but no devices found
[    8.299663] Linux video capture interface: v2.00
[    8.578479] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:2640)
[    8.579549] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[    8.580303] input: Laptop Integrated Webcam as /devices/pci0000:00/0000:00:1d.7/usb2/2-6/2-6:1.0/input/input10
[    8.580439] usbcore: registered new interface driver uvcvideo
[    8.580447] USB Video Class driver (v0.1.0)
[    8.586201] mmc0: new SD card at address 19bb
[    8.703066] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[    8.703074] iwl3945: Copyright(c) 2003-2009 Intel Corporation
[    8.703252] iwl3945 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    8.703273] iwl3945 0000:0c:00.0: setting latency timer to 64
[    8.759939] cfg80211: World regulatory domain updated:
[    8.759947]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    8.759954]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.759961]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    8.759968]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    8.759974]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.759980]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.771097] mmcblk0: mmc0:19bb SD512 488 MiB 
[    8.771194]  mmcblk0: p1
[    8.782417] iwl3945 0000:0c:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[    8.782426] iwl3945 0000:0c:00.0: Detected Intel Wireless WiFi Link 3945ABG
[    8.782571]   alloc irq_desc for 29 on node -1
[    8.782576]   alloc kstat_irqs on node -1
[    8.782621] iwl3945 0000:0c:00.0: irq 29 for MSI/MSI-X
[    8.814543] ip_tables: (C) 2000-2006 Netfilter Core Team
[    8.962017] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04793/0x300000
[    8.962030] serio: Synaptics pass-through port at isa0060/serio1/input0
[    9.012152] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input11
[    9.207109] phy0: Selected rate control algorithm 'iwl-3945-rs'
[    9.461910] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    9.461964] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    9.566061] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input12
[    9.624574] input: HDA Intel Mic at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[    9.624749] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[   10.233089] __ratelimit: 3 callbacks suppressed
[   10.233097] type=1505 audit(1260375847.231:12): operation="profile_replace" pid=944 name=/usr/share/gdm/guest-session/Xsession
[   10.237441] type=1505 audit(1260375847.235:13): operation="profile_replace" pid=945 name=/sbin/dhclient3
[   10.239285] type=1505 audit(1260375847.235:14): operation="profile_replace" pid=945 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   10.240308] type=1505 audit(1260375847.235:15): operation="profile_replace" pid=945 name=/usr/lib/connman/scripts/dhclient-script
[   10.249453] type=1505 audit(1260375847.247:16): operation="profile_replace" pid=947 name=/usr/bin/evince
[   10.280004] type=1505 audit(1260375847.275:17): operation="profile_replace" pid=947 name=/usr/bin/evince-previewer
[   10.298379] type=1505 audit(1260375847.295:18): operation="profile_replace" pid=947 name=/usr/bin/evince-thumbnailer
[   10.322815] type=1505 audit(1260375847.319:19): operation="profile_replace" pid=949 name=/usr/lib/cups/backend/cups-pdf
[   10.324952] type=1505 audit(1260375847.319:20): operation="profile_replace" pid=949 name=/usr/sbin/cupsd
[   10.331060] type=1505 audit(1260375847.327:21): operation="profile_replace" pid=950 name=/usr/sbin/tcpdump
[   10.341336] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   10.341344] Bluetooth: BNEP filters: protocol multicast
[   10.529111] Bridge firewalling registered
[   12.598951] iwl3945 0000:0c:00.0: firmware: requesting iwlwifi-3945-2.ucode
[   13.004678] iwl3945 0000:0c:00.0: loaded firmware version 15.32.2.9
[   13.081665] Registered led device: iwl-phy0::radio
[   13.081699] Registered led device: iwl-phy0::assoc
[   13.081728] Registered led device: iwl-phy0::RX
[   13.081756] Registered led device: iwl-phy0::TX
[   13.101017] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   13.105935] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.872643] [drm] TV-14: set mode NTSC 480i 0
[   17.017785] [drm] TV-14: set mode NTSC 480i 0
[   17.334936] [drm] TV-14: set mode NTSC 480i 0
[   17.505311] [drm] TV-14: set mode NTSC 480i 0
[   21.673040] ppdev: user-space parallel port driver
[   25.167486] [drm] TV-14: set mode NTSC 480i 0
[   25.308514] [drm] TV-14: set mode NTSC 480i 0
[   25.575715] [drm] TV-14: set mode NTSC 480i 0
[   25.716812] [drm] TV-14: set mode NTSC 480i 0
[   26.019417] [drm] TV-14: set mode NTSC 480i 0
[   26.160141] [drm] TV-14: set mode NTSC 480i 0
[   49.396673] padlock: VIA PadLock not detected.
[   51.657022] [drm] TV-14: set mode NTSC 480i 0
[   51.797247] [drm] TV-14: set mode NTSC 480i 0
[   52.063890] [drm] TV-14: set mode NTSC 480i 0
[   52.204549] [drm] TV-14: set mode NTSC 480i 0
[   52.467861] [drm] TV-14: set mode NTSC 480i 0
[   52.607810] [drm] TV-14: set mode NTSC 480i 0
[   54.383838] [drm] TV-14: set mode NTSC 480i 0
[   54.524219] [drm] TV-14: set mode NTSC 480i 0
[   60.538428] wlan0: authenticate with AP 00:1b:2f:40:38:48
[   60.540048] wlan0: authenticated
[   60.540053] wlan0: associate with AP 00:1b:2f:40:38:48
[   60.543110] wlan0: RX AssocResp from 00:1b:2f:40:38:48 (capab=0x471 status=0 aid=1)
[   60.543116] wlan0: associated
[   60.546451] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   71.520212] wlan0: no IPv6 routers present

---

### Post by ukripper on 2009-12-09
what make is your usb drive?

---

### Post by paulcupboard on 2009-12-09
I have tried a camera as well. It doesnt show either. The external hard drive is a Maxtor.

---

### Post by ukripper on 2009-12-09
your webcam is showing up in lspci output but unfortunately your external usb is not showing up anywhere. Looks like it is not supported by linux kernel. Can you tell us what model your drive is?

---

### Post by paulcupboard on 2009-12-09
No, not my web cam. I mean that I connected a digital camera via usb to the laptop and it didnt register either. The external hard drive is by Maxtor model number pn:9nz2a4-500. But as I say you say it looks like its a problems with the actual USB's. Its a Dell inspiron 1520 laptop if that helps at all. Might there be a problem with the drivers?

---

### Post by nothingspecial on 2009-12-09
Try it in all of your usb ports, then run dmesg each time (don`t post that lot again).

You are looking for something like this

 ```
usb 1-6: USB disconnect, address 3
[14363.468089] usb 1-6: new high speed USB device using ehci_hcd and address 5
[14363.609608] usb 1-6: configuration #1 chosen from 1 choice
[14363.635777] scsi3 : SCSI emulation for USB Mass Storage devices
[14363.645747] usb-storage: device found at 5
[14363.645763] usb-storage: waiting for device to settle before scanning
```

If you see anything about usb device in the output, please post it here, but just the relevant bit at the end, not the entire output of dmesg.

---

### Post by paulcupboard on 2009-12-09
OK, I have found this:

[    2.500507] usb 3-2: new full speed USB device using uhci_hcd and address 2
[    2.659452] [drm] TV-14: set mode NTSC 480i 0
[    2.779499] usb 3-2: configuration #1 chosen from 1 choice
[    2.791976] [drm] fb0: inteldrmfb frame buffer device

and this 

 3.074790] usb 3-2.1: new full speed USB device using uhci_hcd and address 3
[    3.202946] usb 3-2.1: configuration #1 chosen from 1 choice
[    3.232188] Console: switching to colour frame buffer device 160x50
[    3.282909] usb 3-2.2: new full speed USB device using uhci_hcd and address 4
[    3.413588] usb 3-2.2: configuration #1 chosen from 1 choice
[    3.429873] usbcore: registered new interface driver hiddev
[    3.433412] input: Broadcom Corp as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2.2/3-2.2:1.0/input/input7
[    3.433561] generic-usb 0003:0A5C:4502.0001: input,hidraw0: USB HID v1.11 Keyboard [Broadcom Corp] on usb-0000:00:1a.0-2.2/input0
[    3.433596] usbcore: registered new interface driver usbhid
[    3.433602] usbhid: v2.6:USB HID core driver
[    3.505810] usb 3-2.3: new full speed USB device using uhci_hcd and address 5
[    3.658040] usb 3-2.3: configuration #1 chosen from 1 choice
[    3.692762] input: Broadcom Corp as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2.3/3-2.3:1.0/input/input8
[    3.692940] generic-usb 0003:0A5C:4503.0002: input,hidraw1: USB HID v1.11 Mouse [Broadcom Corp] on usb-0000:00:1a.0-2.3/input0
[    3.740242] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[474fc000030e3070]
[    3.970451] PM: Starting manual resume from disk
[    3.970460] PM: Resume from partition 8:5
[    3.970465] PM: Checking hibernation image.
[    3.970662] PM: Resume from disk failed.
[    4.021063] EXT4-fs (sda1): barriers enabled


But nothing that looks like what you posted.

---

### Post by nothingspecial on 2009-12-09
Well, it looks like linux has found it, and I`m not sure exactly what all those messages mean but I don`t think it likes it.

With it plugged in, will you now post the output of ```
sudo fdisk -l
```

Oh and how big is it?

---

### Post by paulcupboard on 2009-12-09
Fixed. It was turned off in the BIOS. Dont know why or how it happened but thats what it was. Thanks for everyones help :)

---

### Post by ukripper on 2009-12-10
No wonder lspci wasn't showing your drive plugged in. I am glad you figured it out.

---

### Post by buteomont on 2009-12-13
Rats, I was anxiously reading this thread, hoping to find out how to get my USB working under Karmic.  The thing that fixed yours is not my problem, since there's no USB settings in my BIOS.

When I plug stuff into a USB port, Ubuntu sees it, but won't use it.  Doesn't matter what it is.  If I plug in a bluetooth dongle, the little bluetooth icon appears, but I can't enable it.  (I plugged the same dongle into a friend's laptop running Ubuntu, and it worked fine.)  If I plug in a webcam, I get a bunch of stuff in dmesg showing that it sees it, but can't use the camera.  If I plug in a memory stick,  it will sometimes actually work.  But usually not.

If I open a terminal window and type "lsusb", more often than not it will hang, requiring that I kill the terminal session to unhang it.  But sometimes it will return a good list of things that are plugged in, even though none of them will actually work.

I tried doing a general update, and it found a bunch of updates for various things (I had just installed Karmic a few days ago).  I installed them all, and one of the updates was a new kernel, to 2.6.31-16-generic.  It won't boot when I select it from Grub.  Says "Error, you need to load the kernel first."  Sheesh.

I'm not a Linux newbie, but have never used Linux for my "main" computer until now.  I got fed up with Vista, and Win7 wasn't any better.  Thing is, I've had more trouble out of Ubuntu in the few short days that I've had it loaded than I had out of Windows!

If I can at least get the USB to work, I think a lot of my problems will go away.  Anyone have any ideas?  I'll post whatever logs, etc. that is necessary.

Thanks, David

---

### Post by ukripper on 2009-12-14
> **buteomont said:**
> Rats, I was anxiously reading this thread, hoping to find out how to get my USB working under Karmic.  The thing that fixed yours is not my problem, since there's no USB settings in my BIOS.

When I plug stuff into a USB port, Ubuntu sees it, but won't use it.  Doesn't matter what it is.  If I plug in a bluetooth dongle, the little bluetooth icon appears, but I can't enable it.  (I plugged the same dongle into a friend's laptop running Ubuntu, and it worked fine.)  If I plug in a webcam, I get a bunch of stuff in dmesg showing that it sees it, but can't use the camera.  If I plug in a memory stick,  it will sometimes actually work.  But usually not.

If I open a terminal window and type "lsusb", more often than not it will hang, requiring that I kill the terminal session to unhang it.  But sometimes it will return a good list of things that are plugged in, even though none of them will actually work.

I tried doing a general update, and it found a bunch of updates for various things (I had just installed Karmic a few days ago).  I installed them all, and one of the updates was a new kernel, to 2.6.31-16-generic.  It won't boot when I select it from Grub.  Says "Error, you need to load the kernel first."  Sheesh.

I'm not a Linux newbie, but have never used Linux for my "main" computer until now.  I got fed up with Vista, and Win7 wasn't any better.  Thing is, I've had more trouble out of Ubuntu in the few short days that I've had it loaded than I had out of Windows!

If I can at least get the USB to work, I think a lot of my problems will go away.  Anyone have any ideas?  I'll post whatever logs, etc. that is necessary.

Thanks, David

connect any of your usb device and post output of this command:
```
dmesg | tail
``` if it hangs then after reboot attach whole list as a text file of your dmesg as an attachement by running this:
```
dmesg > ~/dmesg-output.txt
```
dmesg-output.txt will be saved in your home directory.

---

### Post by buteomont on 2010-01-06
Sorry for the delay, I thought I would get an email when a reply came on this forum, but I never got one.  I've attached the output of dmesg to this post (I hope!).  I plugged in a USB device (Arduino) at 242794.950374.

---

### Post by styleruk on 2010-01-07
Hi

I'm having a similar problem, just updated to Ubuntu 9.10 and can't see the external USB drive anymore...it's just a hard disk in a box. If I fire up 'Gparted', it shows the drive as /dev/sde1 and fat32 but will not mount it.

To complicate things, my little EEEpc fires it up no problem so it must be something to do with updating to 9.10.

Is there anything I can do to fix Ubuntu, seems a bit backwards that it forgot how to access this drive seeing as it was there when I updated Ubuntu!

Si

---

