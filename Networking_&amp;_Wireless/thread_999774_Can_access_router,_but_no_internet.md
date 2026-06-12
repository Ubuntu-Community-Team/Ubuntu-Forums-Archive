---
title: "Can access router, but no internet"
date: 2008-12-02
forum: Networking &amp; Wireless
---

### Post by retrodans on 2008-12-02
I have installed Ubuntu using Wubi, my XP OS has fully working internet and network access.  When I first logged into Ubuntu, it all appeared to be working fine.  Then, when I logged in later, I couldn't connect to the internet.  I cannot ping address either by URL or IP (tried 64.233.167.99 which is apparently google).

Previously, on a different computer I hda to login to windows and enable Wake-on-lan after shutdown, but I am unable to find this setting for this network card.

The network card is: Marvell Yukon 88E8053 PCI-E

As internet is down, I have to reboot to get to it and login to windows.  I also cant run apt-get update, or any such apps, my unix knowledge is limited, so installing a driver or something would need to know how to install it.

I have also disabled ipv6 (using aliases file and in firefox) as mentioned in a different post.

Thankyou for any advise you can give
Dan

---

### Post by retrodans on 2008-12-02
UPDATE: Still not working, in fact, I can no longer connect to my router through my browser.  I don't know if I have done something that has done this, or did something that temporarily gave me access which has since been reset.

I really don't know where to look now.

The network manager appears to be giving me and ip as is cmomonly the issue.

---

### Post by superprash2003 on 2008-12-02
is this a wired or wifi card?? go to the terminal and type ifconfig and post output

---

### Post by retrodans on 2008-12-02
The card is a wired card.  As for the other stats, I remember being asked this before when sorting out my laptops wireless.  So in case they are of use, I have also done dmesg and lspci.



ifconfig
---------------------------------------------------------------
```
eth0      Link encap:Ethernet  HWaddr 00:15:f2:af:35:57  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:604 (604.0 B)  TX bytes:3037 (3.0 KB)
          Interrupt:19 

eth1      Link encap:Ethernet  HWaddr 00:15:f2:af:3c:5f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15416 (15.4 KB)  TX bytes:15416 (15.4 KB)

```



dmesg
---------------------------------------------------------------
```
[    0.424071] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.424083] NetLabel:  unlabeled traffic allowed by default
[    0.425246] tracer: 1286 pages allocated for 65536 entries of 80 bytes
[    0.425248]    actual entries 65586
[    0.425374] AppArmor: AppArmor Filesystem Enabled
[    0.425400] ACPI: RTC can wake from S4
[    0.436044] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.436047] system 00:08: ioport range 0x800-0x80f has been reserved
[    0.436049] system 00:08: ioport range 0x500-0x57f has been reserved
[    0.436051] system 00:08: ioport range 0x580-0x5ff has been reserved
[    0.436053] system 00:08: ioport range 0x800-0x87f could not be reserved
[    0.436055] system 00:08: ioport range 0x880-0x8ff has been reserved
[    0.436057] system 00:08: ioport range 0x900-0x97f has been reserved
[    0.436059] system 00:08: ioport range 0x980-0x9ff has been reserved
[    0.436062] system 00:08: iomem range 0xfee01000-0xfeefffff could not be reserved
[    0.436064] system 00:08: iomem range 0xfefff000-0xfeffffff has been reserved
[    0.436067] system 00:08: iomem range 0xffb00000-0xffbfffff could not be reserved
[    0.436069] system 00:08: iomem range 0xfff00000-0xffffffff could not be reserved
[    0.436073] system 00:09: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.436076] system 00:09: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.436085] system 00:0d: ioport range 0xc00-0xc0f has been reserved
[    0.436087] system 00:0d: ioport range 0xd00-0xd0f has been reserved
[    0.436089] system 00:0d: ioport range 0xa20-0xa2f has been reserved
[    0.436091] system 00:0d: ioport range 0xa30-0xa3f has been reserved
[    0.436096] system 00:0e: iomem range 0xe0000000-0xefffffff has been reserved
[    0.436100] system 00:0f: iomem range 0x0-0x9ffff could not be reserved
[    0.436102] system 00:0f: iomem range 0xc0000-0xcffff has been reserved
[    0.436104] system 00:0f: iomem range 0xe0000-0xfffff could not be reserved
[    0.436107] system 00:0f: iomem range 0x100000-0x7fffffff could not be reserved
[    0.441020] pci 0000:00:02.0: PCI bridge, secondary bus 0000:01
[    0.441022] pci 0000:00:02.0:   IO window: 0x7000-0x7fff
[    0.441025] pci 0000:00:02.0:   MEM window: 0xff100000-0xff2fffff
[    0.441028] pci 0000:00:02.0:   PREFETCH window: disabled
[    0.441030] pci 0000:00:03.0: PCI bridge, secondary bus 0000:02
[    0.441032] pci 0000:00:03.0:   IO window: 0x8000-0x8fff
[    0.441034] pci 0000:00:03.0:   MEM window: 0xff300000-0xff3fffff
[    0.441036] pci 0000:00:03.0:   PREFETCH window: disabled
[    0.441039] pci 0000:00:04.0: PCI bridge, secondary bus 0000:03
[    0.441041] pci 0000:00:04.0:   IO window: 0x9000-0xbfff
[    0.441043] pci 0000:00:04.0:   MEM window: 0xff400000-0xff4fffff
[    0.441046] pci 0000:00:04.0:   PREFETCH window: 0x000000bff00000-0x000000dfefffff
[    0.441049] pci 0000:00:12.0: PCI bridge, secondary bus 0000:04
[    0.441051] pci 0000:00:12.0:   IO window: 0xc000-0xcfff
[    0.441054] pci 0000:00:12.0:   MEM window: 0xff500000-0xff5fffff
[    0.441056] pci 0000:00:12.0:   PREFETCH window: disabled
[    0.441059] pci 0000:00:16.0: PCI bridge, secondary bus 0000:05
[    0.441061] pci 0000:00:16.0:   IO window: disabled
[    0.441064] pci 0000:00:16.0:   MEM window: disabled
[    0.441066] pci 0000:00:16.0:   PREFETCH window: disabled
[    0.441069] pci 0000:00:17.0: PCI bridge, secondary bus 0000:06
[    0.441071] pci 0000:00:17.0:   IO window: disabled
[    0.441073] pci 0000:00:17.0:   MEM window: disabled
[    0.441076] pci 0000:00:17.0:   PREFETCH window: disabled
[    0.441085] pci 0000:00:02.0: setting latency timer to 64
[    0.441088] pci 0000:00:03.0: setting latency timer to 64
[    0.441092] pci 0000:00:04.0: setting latency timer to 64
[    0.441096] pci 0000:00:12.0: setting latency timer to 64
[    0.441101] pci 0000:00:16.0: setting latency timer to 64
[    0.441106] pci 0000:00:17.0: setting latency timer to 64
[    0.441108] bus: 00 index 0 io port: [0, ffff]
[    0.441110] bus: 00 index 1 mmio: [0, ffffffffffffffff]
[    0.441112] bus: 01 index 0 io port: [7000, 7fff]
[    0.441113] bus: 01 index 1 mmio: [ff100000, ff2fffff]
[    0.441114] bus: 01 index 2 mmio: [0, 0]
[    0.441116] bus: 01 index 3 mmio: [0, 0]
[    0.441117] bus: 02 index 0 io port: [8000, 8fff]
[    0.441119] bus: 02 index 1 mmio: [ff300000, ff3fffff]
[    0.441120] bus: 02 index 2 mmio: [0, 0]
[    0.441121] bus: 02 index 3 mmio: [0, 0]
[    0.441123] bus: 03 index 0 io port: [9000, bfff]
[    0.441124] bus: 03 index 1 mmio: [ff400000, ff4fffff]
[    0.441126] bus: 03 index 2 mmio: [bff00000, dfefffff]
[    0.441127] bus: 03 index 3 mmio: [0, 0]
[    0.441129] bus: 04 index 0 io port: [c000, cfff]
[    0.441130] bus: 04 index 1 mmio: [ff500000, ff5fffff]
[    0.441131] bus: 04 index 2 mmio: [0, 0]
[    0.441133] bus: 04 index 3 io port: [0, ffff]
[    0.441134] bus: 04 index 4 mmio: [0, ffffffffffffffff]
[    0.441136] bus: 05 index 0 mmio: [0, 0]
[    0.441137] bus: 05 index 1 mmio: [0, 0]
[    0.441138] bus: 05 index 2 mmio: [0, 0]
[    0.441139] bus: 05 index 3 mmio: [0, 0]
[    0.441141] bus: 06 index 0 mmio: [0, 0]
[    0.441142] bus: 06 index 1 mmio: [0, 0]
[    0.441143] bus: 06 index 2 mmio: [0, 0]
[    0.441144] bus: 06 index 3 mmio: [0, 0]
[    0.441154] NET: Registered protocol family 2
[    0.444044] Switched to high resolution mode on CPU 0
[    0.480095] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.480836] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.483052] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.483643] TCP: Hash tables configured (established 262144 bind 65536)
[    0.483645] TCP reno registered
[    0.492101] NET: Registered protocol family 1
[    0.492202] checking if image is initramfs... it is
[    1.074919] Freeing initrd memory: 8714k freed
[    1.080579] audit: initializing netlink socket (disabled)
[    1.080592] type=2000 audit(1228233767.080:1): initialized
[    1.085230] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.088836] VFS: Disk quotas dquot_6.5.1
[    1.088953] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.089081] msgmni has been set to 4016
[    1.089230] io scheduler noop registered
[    1.089232] io scheduler anticipatory registered
[    1.089233] io scheduler deadline registered
[    1.089422] io scheduler cfq registered (default)
[    1.089436] pci 0000:00:00.0: Enabling HT MSI Mapping
[    1.089470] pci 0000:00:02.0: Enabling HT MSI Mapping
[    1.089479] pci 0000:00:03.0: Enabling HT MSI Mapping
[    1.089487] pci 0000:00:04.0: Enabling HT MSI Mapping
[    1.089500] pci 0000:00:09.0: Enabling HT MSI Mapping
[    1.089572] pci 0000:00:16.0: Enabling HT MSI Mapping
[    1.089582] pci 0000:00:16.0: Found enabled HT MSI Mapping
[    1.089585] pci 0000:00:16.0: Linking AER extended capability
[    1.089594] pci 0000:00:17.0: Enabling HT MSI Mapping
[    1.089603] pci 0000:00:17.0: Found enabled HT MSI Mapping
[    1.089605] pci 0000:00:17.0: Linking AER extended capability
[    1.089614] pci 0000:03:00.0: Boot video device
[    1.089766] pcieport-driver 0000:00:02.0: setting latency timer to 64
[    1.089786] pcieport-driver 0000:00:02.0: found MSI capability
[    1.089805] pci_express 0000:00:02.0:pcie00: allocate port service
[    1.089887] pci_express 0000:00:02.0:pcie03: allocate port service
[    1.089993] pcieport-driver 0000:00:03.0: setting latency timer to 64
[    1.090013] pcieport-driver 0000:00:03.0: found MSI capability
[    1.090029] pci_express 0000:00:03.0:pcie00: allocate port service
[    1.090113] pci_express 0000:00:03.0:pcie03: allocate port service
[    1.090216] pcieport-driver 0000:00:04.0: setting latency timer to 64
[    1.090236] pcieport-driver 0000:00:04.0: found MSI capability
[    1.090251] pci_express 0000:00:04.0:pcie00: allocate port service
[    1.090329] pci_express 0000:00:04.0:pcie03: allocate port service
[    1.090438] pcieport-driver 0000:00:16.0: setting latency timer to 64
[    1.090466] pcieport-driver 0000:00:16.0: found MSI capability
[    1.090486] pci_express 0000:00:16.0:pcie00: allocate port service
[    1.090557] pci_express 0000:00:16.0:pcie03: allocate port service
[    1.090659] pcieport-driver 0000:00:17.0: setting latency timer to 64
[    1.090686] pcieport-driver 0000:00:17.0: found MSI capability
[    1.090706] pci_express 0000:00:17.0:pcie00: allocate port service
[    1.090768] pci_express 0000:00:17.0:pcie03: allocate port service
[    1.132518] Linux agpgart interface v0.103
[    1.132553] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.132724] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.133442] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.135649] brd: module loaded
[    1.135733] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.135877] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.138166] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.138172] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.148113] mice: PS/2 mouse device common for all mice
[    1.148255] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.148277] rtc0: alarms up to one year, y3k
[    1.148348] cpuidle: using governor ladder
[    1.148350] cpuidle: using governor menu
[    1.148663] TCP cubic registered
[    1.148922] registered taskstats version 1
[    1.149077]   Magic number: 4:843:33
[    1.149202] rtc_cmos 00:02: setting system clock to 2008-12-02 16:02:48 UTC (1228233768)
[    1.149204] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.149205] EDD information not available.
[    1.149240] Freeing unused kernel memory: 536k freed
[    1.149527] Write protecting the kernel read-only data: 4348k
[    1.176310] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.297109] fuse init (API version 7.9)
[    1.514386] processor ACPI0007:00: registered as cooling_device0
[    1.514396] ACPI: Processor [CPU1] (supports 8 throttling states)
[    2.126129] No dock devices found.
[    2.140833] SCSI subsystem initialized
[    2.164770] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 19
[    2.164781] sky2 0000:02:00.0: PCI INT A -> Link[LNKA] -> GSI 19 (level, low) -> IRQ 19
[    2.164790] sky2 0000:02:00.0: setting latency timer to 64
[    2.164809] sky2 0000:02:00.0: v1.22 addr 0xff3fc000 irq 19 Yukon-2 EC rev 2
[    2.165136] sky2 eth0: addr 00:15:f2:af:35:57
[    2.171165] libata version 3.00 loaded.
[    2.173489] sata_sil24 0000:01:00.0: version 1.1
[    2.173838] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 18
[    2.173848] sata_sil24 0000:01:00.0: PCI INT A -> Link[LNKB] -> GSI 18 (level, low) -> IRQ 18
[    2.173918] sata_sil24 0000:01:00.0: setting latency timer to 64
[    2.176747] scsi0 : sata_sil24
[    2.176862] scsi1 : sata_sil24
[    2.176892] ata1: SATA max UDMA/100 host m128@0xff2ffc00 port 0xff2f8000 irq 18
[    2.176895] ata2: SATA max UDMA/100 host m128@0xff2ffc00 port 0xff2fa000 irq 18
[    2.233975] usbcore: registered new interface driver usbfs
[    2.233995] usbcore: registered new interface driver hub
[    2.249410] usbcore: registered new device driver usb
[    2.255297] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.256041] ata1: SATA link down (SStatus 0 SControl 0)
[    6.336038] ata2: SATA link down (SStatus 0 SControl 0)
[    6.337455] pata_acpi 0000:00:0f.0: setting latency timer to 64
[    6.337884] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 23
[    6.337894] pata_acpi 0000:00:10.0: PCI INT A -> Link[LSA0] -> GSI 23 (level, low) -> IRQ 23
[    6.337909] pata_acpi 0000:00:10.0: setting latency timer to 64
[    6.337916] pata_acpi 0000:00:10.0: PCI INT A disabled
[    6.338275] ACPI: PCI Interrupt Link [LSA1] enabled at IRQ 22
[    6.338281] pata_acpi 0000:00:11.0: PCI INT A -> Link[LSA1] -> GSI 22 (level, low) -> IRQ 22
[    6.338295] pata_acpi 0000:00:11.0: setting latency timer to 64
[    6.338303] pata_acpi 0000:00:11.0: PCI INT A disabled
[    6.338791] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 21
[    6.338797] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[LUB0] -> GSI 21 (level, low) -> IRQ 21
[    6.338808] ohci_hcd 0000:00:0b.0: setting latency timer to 64
[    6.338810] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    6.338862] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[    6.338886] ohci_hcd 0000:00:0b.0: irq 21, io mem 0xff6fe000
[    6.394145] usb usb1: configuration #1 chosen from 1 choice
[    6.394170] hub 1-0:1.0: USB hub found
[    6.394178] hub 1-0:1.0: 10 ports detected
[    6.496591] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 20
[    6.496601] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[LUB2] -> GSI 20 (level, low) -> IRQ 20
[    6.496613] ehci_hcd 0000:00:0b.1: setting latency timer to 64
[    6.496615] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[    6.496636] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
[    6.496661] ehci_hcd 0000:00:0b.1: debug port 1
[    6.496665] ehci_hcd 0000:00:0b.1: cache line size of 64 is not supported
[    6.496682] ehci_hcd 0000:00:0b.1: irq 20, io mem 0xff6ffc00
[    6.508022] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    6.508123] usb usb2: configuration #1 chosen from 1 choice
[    6.508144] hub 2-0:1.0: USB hub found
[    6.508150] hub 2-0:1.0: 10 ports detected
[    6.612259] sata_nv 0000:00:10.0: version 3.5
[    6.612271] sata_nv 0000:00:10.0: PCI INT A -> Link[LSA0] -> GSI 23 (level, low) -> IRQ 23
[    6.612308] sata_nv 0000:00:10.0: setting latency timer to 64
[    6.613099] scsi2 : sata_nv
[    6.613833] scsi3 : sata_nv
[    6.613998] ata3: SATA max UDMA/133 cmd 0xe480 ctl 0xe400 bmdma 0xdc00 irq 23
[    6.614001] ata4: SATA max UDMA/133 cmd 0xe080 ctl 0xe000 bmdma 0xdc08 irq 23
[    7.088040] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    7.111958] ata3.00: ATA-7: WDC WD3200KS-00PFB0, 21.00M21, max UDMA/133
[    7.111960] ata3.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/1)
[    7.120321] ata3.00: configured for UDMA/133
[    7.440029] ata4: SATA link down (SStatus 0 SControl 300)
[    7.440068] isa bounce pool size: 16 pages
[    7.440139] scsi 2:0:0:0: Direct-Access     ATA      WDC WD3200KS-00P 21.0 PQ: 0 ANSI: 5
[    7.441720] scsi 2:0:0:0: Attached scsi generic sg0 type 0
[    7.444670] sata_nv 0000:00:11.0: PCI INT A -> Link[LSA1] -> GSI 22 (level, low) -> IRQ 22
[    7.444708] sata_nv 0000:00:11.0: setting latency timer to 64
[    7.445521] scsi4 : sata_nv
[    7.445609] scsi5 : sata_nv
[    7.445781] ata5: SATA max UDMA/133 cmd 0xd880 ctl 0xd800 bmdma 0xd080 irq 22
[    7.445783] ata6: SATA max UDMA/133 cmd 0xd480 ctl 0xd400 bmdma 0xd088 irq 22
[    7.764029] ata5: SATA link down (SStatus 0 SControl 300)
[    8.084027] ata6: SATA link down (SStatus 0 SControl 300)
[    8.084110] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    8.084455] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 23
[    8.084459] forcedeth 0000:00:13.0: PCI INT A -> Link[LMAC] -> GSI 23 (level, low) -> IRQ 23
[    8.084463] forcedeth 0000:00:13.0: setting latency timer to 64
[    8.084489] nv_probe: set workaround bit for reversed mac addr
[    8.604869] forcedeth 0000:00:13.0: ifname eth1, PHY OUI 0x5043 @ 1, addr 00:15:f2:af:3c:5f
[    8.604872] forcedeth 0000:00:13.0: highdma csum timirq gbit lnktim desc-v3
[    8.609795] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 17
[    8.609806] ohci1394 0000:04:08.2: PCI INT B -> Link[LNKD] -> GSI 17 (level, low) -> IRQ 17
[    8.659542] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[ff5ff800-ff5fffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    8.661298] ohci1394 0000:04:0b.0: PCI INT A -> Link[LNKA] -> GSI 19 (level, low) -> IRQ 19
[    8.711034] ohci1394: fw-host1: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[ff5ff000-ff5ff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    8.716091] pata_amd 0000:00:0f.0: version 0.3.10
[    8.716137] pata_amd 0000:00:0f.0: setting latency timer to 64
[    8.716769] scsi6 : pata_amd
[    8.717863] scsi7 : pata_amd
[    8.719378] ata7: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    8.719381] ata8: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    8.753809] Driver 'sd' needs updating - please use bus_type methods
[    8.753929] sd 2:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[    8.753951] sd 2:0:0:0: [sda] Write Protect is off
[    8.753953] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    8.753991] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.754058] sd 2:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[    8.754077] sd 2:0:0:0: [sda] Write Protect is off
[    8.754078] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    8.754113] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.754117]  sda: sda1 sda2 < sda5 >
[    8.772042] sd 2:0:0:0: [sda] Attached SCSI disk
[    9.044321] ata8.00: ATAPI: HL-DT-ST DVDRAM GSA-H10N, JL10, max UDMA/33
[    9.044332] ata8: nv_mode_filter: 0x739f&0x701f->0x701f, BIOS=0x7000 (0xc000) ACPI=0x701f (60:900:0x11)
[    9.060253] ata8.00: configured for UDMA/33
[    9.064184] scsi 7:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-H10N  JL10 PQ: 0 ANSI: 5
[    9.064321] scsi 7:0:0:0: Attached scsi generic sg1 type 5
[    9.094070] Driver 'sr' needs updating - please use bus_type methods
[    9.101411] sr0: scsi3-mmc drive: 125x/125x writer dvd-ram cd/rw xa/form2 cdda tray
[    9.101416] Uniform CD-ROM driver Revision: 3.20
[    9.101506] sr 7:0:0:0: Attached scsi CD-ROM sr0
[    9.727002] loop: module loaded
[    9.759315] kjournald starting.  Commit interval 5 seconds
[    9.759333] EXT3-fs: mounted filesystem with ordered data mode.
[    9.932225] ieee1394: Host added: ID:BUS[0-01:1023]  GUID[00023c014100af7b]
[    9.984140] ieee1394: Host added: ID:BUS[1-00:1023]  GUID[0011d800008fc4c0]
[   14.876720] udevd version 124 started
[   15.402827] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   15.416051] ACPI: Power Button (FF) [PWRF]
[   15.416222] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[   15.432032] ACPI: Power Button (CM) [PWRB]
[   16.180743] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   16.211660] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.380328] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x600
[   16.380343] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x700
[   16.957748] gameport: EMU10K1 is pci0000:04:08.1/gameport0, io 0xcc00, speed 1094kHz
[   17.372498] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   17.598908] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 16
[   17.598919] EMU10K1_Audigy 0000:04:08.0: PCI INT A -> Link[LNKC] -> GSI 16 (level, low) -> IRQ 16
[   17.602416] Installing spdif_bug patch: Audigy 2 ZS [2001]
[   18.196466] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input5
[   25.694507] sr 7:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   25.694512] sr 7:0:0:0: [sr0] Sense Key : Medium Error [current] 
[   25.694516] Info fld=0x1ed3c0
[   25.694517] sr 7:0:0:0: [sr0] Add. Sense: Unrecovered read error
[   25.694521] end_request: I/O error, dev sr0, sector 8081152
[   25.694525] Buffer I/O error on device sr0, logical block 1010144
[   32.066649] sr 7:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   32.066652] sr 7:0:0:0: [sr0] Sense Key : Medium Error [current] 
[   32.066654] Info fld=0x1ed3c0
[   32.066655] sr 7:0:0:0: [sr0] Add. Sense: Unrecovered read error
[   32.066658] end_request: I/O error, dev sr0, sector 8081152
[   32.066660] Buffer I/O error on device sr0, logical block 1010144
[   37.792028] sr 7:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   37.792030] sr 7:0:0:0: [sr0] Sense Key : Medium Error [current] 
[   37.792033] Info fld=0x1ed3ec
[   37.792034] sr 7:0:0:0: [sr0] Add. Sense: Unrecovered read error
[   37.792036] end_request: I/O error, dev sr0, sector 8081328
[   37.792038] Buffer I/O error on device sr0, logical block 1010166
[   43.414340] sr 7:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   43.414342] sr 7:0:0:0: [sr0] Sense Key : Medium Error [current] 
[   43.414345] Info fld=0x1ed3ec
[   43.414346] sr 7:0:0:0: [sr0] Add. Sense: Unrecovered read error
[   43.414348] end_request: I/O error, dev sr0, sector 8081328
[   43.414350] Buffer I/O error on device sr0, logical block 1010166
[   49.661041] sr 7:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   49.661044] sr 7:0:0:0: [sr0] Sense Key : Medium Error [current] 
[   49.661046] Info fld=0x1ed3ee
[   49.661047] sr 7:0:0:0: [sr0] Add. Sense: Unrecovered read error
[   49.661050] end_request: I/O error, dev sr0, sector 8081336
[   49.661052] Buffer I/O error on device sr0, logical block 1010167
[   55.491469] sr 7:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   55.491471] sr 7:0:0:0: [sr0] Sense Key : Medium Error [current] 
[   55.491474] Info fld=0x1ed3ee
[   55.491475] sr 7:0:0:0: [sr0] Add. Sense: Unrecovered read error
[   55.491477] end_request: I/O error, dev sr0, sector 8081336
[   55.491479] Buffer I/O error on device sr0, logical block 1010167
[   60.738787] sr 7:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   60.738790] sr 7:0:0:0: [sr0] Sense Key : Medium Error [current] 
[   60.738792] Info fld=0x1ed3ee
[   60.738793] sr 7:0:0:0: [sr0] Add. Sense: Unrecovered read error
[   60.738795] end_request: I/O error, dev sr0, sector 8081336
[   60.738797] Buffer I/O error on device sr0, logical block 1010167
[   66.235949] sr 7:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   66.235952] sr 7:0:0:0: [sr0] Sense Key : Medium Error [current] 
[   66.235954] Info fld=0x1ed3ee
[   66.235955] sr 7:0:0:0: [sr0] Add. Sense: Unrecovered read error
[   66.235958] end_request: I/O error, dev sr0, sector 8081336
[   66.235960] Buffer I/O error on device sr0, logical block 1010167
[   71.858120] sr 7:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   71.858122] sr 7:0:0:0: [sr0] Sense Key : Medium Error [current] 
[   71.858125] Info fld=0x1ed3ee
[   71.858126] sr 7:0:0:0: [sr0] Add. Sense: Unrecovered read error
[   71.858128] end_request: I/O error, dev sr0, sector 8081336
[   71.858130] Buffer I/O error on device sr0, logical block 1010167
[   77.230489] sr 7:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   77.230491] sr 7:0:0:0: [sr0] Sense Key : Medium Error [current] 
[   77.230494] Info fld=0x1ed3ee
[   77.230495] sr 7:0:0:0: [sr0] Add. Sense: Unrecovered read error
[   77.230497] end_request: I/O error, dev sr0, sector 8081336
[   77.230499] Buffer I/O error on device sr0, logical block 1010167
[   83.727122] sr 7:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   83.727124] sr 7:0:0:0: [sr0] Sense Key : Medium Error [current] 
[   83.727127] Info fld=0x1ed3ee
[   83.727128] sr 7:0:0:0: [sr0] Add. Sense: Unrecovered read error
[   83.727130] end_request: I/O error, dev sr0, sector 8081336
[   83.727132] Buffer I/O error on device sr0, logical block 1010167
[   89.724019] sr 7:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   89.724021] sr 7:0:0:0: [sr0] Sense Key : Medium Error [current] 
[   89.724024] Info fld=0x1ed3e0
[   89.724025] sr 7:0:0:0: [sr0] Add. Sense: Unrecovered read error
[   89.724027] end_request: I/O error, dev sr0, sector 8081280
[   89.724029] Buffer I/O error on device sr0, logical block 1010160
[   95.637504] sr 7:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   95.637507] sr 7:0:0:0: [sr0] Sense Key : Medium Error [current] 
[   95.637509] Info fld=0x1ed3ec
[   95.637510] sr 7:0:0:0: [sr0] Add. Sense: Unrecovered read error
[   95.637513] end_request: I/O error, dev sr0, sector 8081328
[   95.637515] Buffer I/O error on device sr0, logical block 1010166
[  101.592632] sr 7:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  101.592634] sr 7:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  101.592637] Info fld=0x1ed3ee
[  101.592638] sr 7:0:0:0: [sr0] Add. Sense: Unrecovered read error
[  101.592640] end_request: I/O error, dev sr0, sector 8081336
[  101.592642] Buffer I/O error on device sr0, logical block 1010167
[  106.839833] sr 7:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  106.839836] sr 7:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  106.839838] Info fld=0x1ed3ee
[  106.839839] sr 7:0:0:0: [sr0] Add. Sense: Unrecovered read error
[  106.839841] end_request: I/O error, dev sr0, sector 8081336
[  106.839843] Buffer I/O error on device sr0, logical block 1010167
[  107.899736] lp: driver loaded but no devices found
[  108.649096] EXT3 FS on loop0, internal journal
[  117.128957] Adding 976552k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:976552k
[  117.259736] type=1505 audit(1228233884.486:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4237
[  117.391777] type=1505 audit(1228233884.618:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4242
[  117.391952] type=1505 audit(1228233884.618:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4242
[  117.500099] ip_tables: (C) 2000-2006 Netfilter Core Team
[  117.986480] ACPI: WMI: Mapper loaded
[  118.164022] powernow-k8: Found 1 AMD Athlon(tm) 64 FX-55 Processor processors (1 cpu cores) (version 2.20.00)
[  118.164056] powernow-k8:    0 : fid 0x12 (2600 MHz), vid 0x2
[  118.164057] powernow-k8:    1 : fid 0x4 (1200 MHz), vid 0x12
[  118.852790] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[  118.989729] ppdev: user-space parallel port driver
[  120.797064] Bluetooth: Core ver 2.13
[  120.799348] NET: Registered protocol family 31
[  120.799354] Bluetooth: HCI device and connection manager initialized
[  120.799357] Bluetooth: HCI socket layer initialized
[  120.814500] Bluetooth: L2CAP ver 2.11
[  120.814506] Bluetooth: L2CAP socket layer initialized
[  120.823485] Bluetooth: SCO (Voice Link) ver 0.6
[  120.823491] Bluetooth: SCO socket layer initialized
[  120.832663] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  120.832670] Bluetooth: BNEP filters: protocol multicast
[  120.873748] Bridge firewalling registered
[  120.874640] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[  120.896325] Bluetooth: RFCOMM socket layer initialized
[  120.897885] Bluetooth: RFCOMM TTY layer initialized
[  120.897890] Bluetooth: RFCOMM ver 1.10
[  122.594488] pci 0000:03:00.0: PCI INT A -> Link[LNKA] -> GSI 19 (level, low) -> IRQ 19
[  122.821828] [drm] Initialized drm 1.1.0 20060810
[  122.853234] pci 0000:03:00.0: setting latency timer to 64
[  122.854902] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[  122.940017] Clocksource tsc unstable (delta = -269221394 ns)
[  124.198234] [drm] Setting GART location based on new memory map
[  124.198528] [drm] Loading R500 Microcode
[  124.198761] [drm] Num pipes: 4
[  124.198770] [drm] writeback test succeeded in 1 usecs
[  124.976615] eth1: no link during initialization.
[  124.978745] sky2 eth0: enabling interface
[  126.729566] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
[  126.821158] NET: Registered protocol family 17
[  132.034122]  CIFS VFS: No username specified
[  132.034136]  CIFS VFS: cifs_mount failed w/return code = -22
[  132.034913]  CIFS VFS: No username specified
[  132.034923]  CIFS VFS: cifs_mount failed w/return code = -22
[  132.038518]  CIFS VFS: No username specified
[  132.038527]  CIFS VFS: cifs_mount failed w/return code = -22
[  132.042052]  CIFS VFS: No username specified
[  132.042064]  CIFS VFS: cifs_mount failed w/return code = -22
[  132.045239]  CIFS VFS: No username specified
[  132.045253]  CIFS VFS: cifs_mount failed w/return code = -22
[  132.048370]  CIFS VFS: No username specified
[  132.048383]  CIFS VFS: cifs_mount failed w/return code = -22
[  132.051811]  CIFS VFS: No username specified
[  132.051821]  CIFS VFS: cifs_mount failed w/return code = -22
[  159.713478] UDF-fs: No VRS found
[  159.728751] ISO 9660 Extensions: Microsoft Joliet Level 3
[  159.730957] ISOFS: changing to secondary root
```



LSPCI
---------------------------------------------------------------
```
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:09.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a4)
00:0a.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a4)
00:0a.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:0b.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:0b.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a4)
00:0f.0 IDE interface: nVidia Corporation CK804 IDE (rev f3)
00:10.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:11.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:12.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:13.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:16.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:17.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 Mass storage controller: Silicon Image, Inc. SiI 3132 Serial ATA Raid II Controller (rev 01)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 15)
03:00.0 VGA compatible controller: ATI Technologies Inc R580 [Radeon X1900 XT] (Primary)
03:00.1 Display controller: ATI Technologies Inc R580 [Radeon X1900 XT] (Secondary)
04:08.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
04:08.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
04:08.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
04:0b.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
```

Thankyou

---

### Post by superprash2003 on 2008-12-03
you seem to be getting an ip 192.168.0.2 .. is your gateway (Router ) ip 192.168.0.1 ?? if so in the terminal type ping 192.168.0.1 and post output..

---

### Post by retrodans on 2008-12-03
My router is at 192.168.0.1 which is strange, as it always used to be at 192.168.0.4 preset as its a SKY-UK linksys router.

I ping'd both IPs, and the results are:

```

retrobadger@ubuntu:~$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=1.62 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=64 time=0.771 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=64 time=0.746 ms
64 bytes from 192.168.0.1: icmp_seq=4 ttl=64 time=0.739 ms
64 bytes from 192.168.0.1: icmp_seq=5 ttl=64 time=0.732 ms

```

```

retrobadger@ubuntu:~$ ping 192.168.0.4
PING 192.168.0.4 (192.168.0.4) 56(84) bytes of data.
From 192.168.0.2 icmp_seq=1 Destination Host Unreachable
From 192.168.0.2 icmp_seq=2 Destination Host Unreachable
From 192.168.0.2 icmp_seq=3 Destination Host Unreachable
From 192.168.0.2 icmp_seq=5 Destination Host Unreachable

```

---

### Post by superprash2003 on 2008-12-04
in windows did you require a dialer to connect to the internet?? if no type ping google.com and post output.. also post output of cat /etc/resolv.conf

---

### Post by retrodans on 2008-12-04
No I didn't need a dialler.  Wasn't sure where you wanted those commands run, so did them in both


WINDOWS XP - CMD

ping google.com
```
Pinging google.com [72.14.205.100] with 32 bytes of data:

Reply from 72.14.205.100: bytes=32 time=132ms TTL=245
Reply from 72.14.205.100: bytes=32 time=125ms TTL=245
Reply from 72.14.205.100: bytes=32 time=125ms TTL=245
Reply from 72.14.205.100: bytes=32 time=133ms TTL=245

Ping statistics for 72.14.205.100:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 125ms, Maximum = 133ms, Average = 128ms
```
    
    
UBUNTU - Terminal

ping google.com
```
retrobadger@ubuntu:~$ ping google.com
ping: unknown host google.com
```


cat /etc/resolv.conf
```
retrobadger@ubuntu:~$ cat /etc/resolv.conf
retrobadger@ubuntu:~$ ping google.com
ping: unknown host google.com
```

---

### Post by superprash2003 on 2008-12-05
you may have a DNS issue as your resolv.conf seems to be blank , post outpt of ping 72.14.205.100 from ubuntu

---

### Post by retrodans on 2008-12-08
Ah okay, I see the resolv.conf carries links to the DNS servers if that is correct.  Okay, well I have ping'd the IP you recommended, the results are below:

```
PING 72.14.205.100 (72.14.205.100) 56(84) bytes of data.
64 bytes from 72.14.205.100: icmp_seq=1 ttl=245 time=127 ms
64 bytes from 72.14.205.100: icmp_seq=2 ttl=245 time=128 ms
64 bytes from 72.14.205.100: icmp_seq=3 ttl=245 time=127 ms
64 bytes from 72.14.205.100: icmp_seq=4 ttl=245 time=131 ms
64 bytes from 72.14.205.100: icmp_seq=5 ttl=245 time=129 ms
64 bytes from 72.14.205.100: icmp_seq=6 ttl=245 time=128 ms
64 bytes from 72.14.205.100: icmp_seq=7 ttl=245 time=130 ms
64 bytes from 72.14.205.100: icmp_seq=8 ttl=245 time=129 ms
64 bytes from 72.14.205.100: icmp_seq=9 ttl=245 time=127 ms
64 bytes from 72.14.205.100: icmp_seq=10 ttl=245 time=127 ms
64 bytes from 72.14.205.100: icmp_seq=11 ttl=245 time=126 ms
64 bytes from 72.14.205.100: icmp_seq=12 ttl=245 time=129 ms
```

---

### Post by retrodans on 2008-12-10
I don't know whether something has changed, or if I made a mistake the first time (if it's the latter, I am ever so sorry).  But I redid /cat/resolv.conf as I was trying to understand the problem better, and this time I got the below:

```

# Generated by NetworkManager
nameserver 192.168.0.1
```

So I do have something in resolv.conf, which is strange, I was sure it returned empty before.

Any help would be most appreciated.

---

### Post by retrodans on 2008-12-10
I have also attempted to install XAMPP on my system if this will make any difference.

---

### Post by kking on 2008-12-10
As you were able to ping an ip address your connection seems fine, but you don't have the nameservers listed properly.

Boot into windows and run ipconfig /all to get your DNS server addresses.

Boot back into ubuntu and edit your /etc/resolv.conf file to remove the entry that is there now and add "nameserver xxx.xxx.xxx.xxx" for your DNS server addresses.

I'm not sure if this change is picked up right away, if not restart networking with:
sudo /etc/init.d/networking restart

---

### Post by retrodans on 2008-12-11
I ran ipconfig /all in windows, but got back the ip that was the same as what was already in ubuntu.  



Part of the results are:

```
Ethernet adapter Local Area Connection 2:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : Marvell Yukon 88E8053 PCI-E Gigabit
        DNS Servers . . . . . . . . . . . : 192.168.0.1
```

---

### Post by cariboo on 2008-12-11
I see you have both eth0 and eth1 listed in a previous post, with eth0 having an ip address and eth0 not having anything, In your last post your are showing local area connection 2 with a dns of 192.168.0.1. What does it say for a dns address for Local area connection 1 when you run ipconfig /all?

Jim

---

### Post by retrodans on 2008-12-11
In windows, when I run ipconfig /all I don't have a connection 2.  The 3 I do have are:

Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\Retrobadger>ipconfig /all

```
Windows IP Configuration:

Ethernet adapter Hamachi:

Ethernet adapter Local Area Connection 2:
```

---

### Post by retrodans on 2008-12-13
Sorry if this is something I should have mentioned earlier when I specced out the problem, but I am on Sky Broadband [uk], and my access goes through a wireless modem.  So I believe this means the router allocates the DNS nameserver, and the DNS server link goes to the router.

So for some reason the DNS is getting calculated by XP and not Ubuntu.  Whilst I love Ubuntu, the setup process is proving to be a bit of a pain, although it will eventually be worth it :-D

---

### Post by retrodans on 2008-12-18
Any ideas on this, I am not having much luck from searching the posts.  It's strange as it was working before, and it has on other installations.  I may just have to uninstall and reinstall in the new year I think!

---

