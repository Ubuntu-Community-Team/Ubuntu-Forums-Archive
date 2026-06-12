---
title: "Wi-fi connection help"
date: 2010-09-01
forum: New to Ubuntu
---

### Post by jackwilson on 2010-09-01
I have:

Acer travelmate 2300 
ipn2220 wireless lan card
windows xp home addition

I installed: 
Ubuntu 10.04 lts. On my hard drive dual boot.

When I put my inf file for my driver in add new driver it said not a valid driver. This was the second time I installed Ubuntu on this machine, the first time when I added inf file in add new driver it showed my driver and yes, but I did not know how to connect to my network using the wireless.

I've been to many sites that say do this, (ndiswrapper) that, (kernel)  the other thing, (configure) and it will work. Mine doesn't.

Please help me understand what I've not done or have done wrong.

Thanks.

---

### Post by theDaveTheRave on 2010-09-02
First, I recoment you change the title of the thread...

My first response was.... I know where I live, do you? ](*,)

so to continue...

first thing to do is to confirm the wireless card, in a terminal run the following...

```
lshw -C network
```

and copy and paste the results into your reply.

here is mine as a sample

```
 *-network
       description: Wireless interface
       [COLOR="SeaGreen"]product: AR2413 802.11bg NIC[/COLOR]
       vendor: Atheros Communications Inc.
       physical id: 3
       bus info: pci@0000:0a:03.0
       logical name: wmaster0
       version: 01
       serial: 00:19:7d:40:b8:c0
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci ip=192.168.1.7 latency=168 maxlatency=28 mingnt=10 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 82:68:ea:24:d1:19
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

specifically you are looking for the product code, as the manufacturers often change the chip even if the actual 'item' is the same.

Then you need to search for this specifically on the forums.

---

### Post by wojox on 2010-09-02
Here's some [Ndiswrapper Help]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

---

### Post by bredman on 2010-09-02
I recommend that you try the instructions on
[https://help.ubuntu.com/community/WifiDocs/Device/ipn2220](https://help.ubuntu.com/community/WifiDocs/Device/ipn2220)

---

### Post by jackwilson on 2010-09-02
I don't know how to or what to change my title to.


This is mine:
*-network:0             
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth0
       version: 01
       serial: 00:c0:9f:66:31:09
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.0.104 latency=64 multicast=yes
       resources: irq:6 memory:e0200000-e0201fff memory:24000000-24003fff(prefetchable)
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
       vendor: Linksys, A Division of Cisco Systems
       physical id: 4
       bus info: pci@0000:02:04.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=64 maxlatency=32 mingnt=32
       resources: ioport:3800(size=32) memory:e0203800-e020381f memory:e0203000-e02037ff

---

### Post by Tracy177 on 2010-09-02
can u open terminal and type dmesg than copy it and paste here [http://paste.ubuntu.com/](http://paste.ubuntu.com/)

than copy the link and paste it over here 


or just open terminal type dmesg copy everything and paste it over here that i can look at it

---

### Post by Elfy on 2010-09-02
> **jackwilson said:**
> I don't know how to or what to change my title to.

How about Wi-fi connection help.

As you can't edit thread title, I did it for you.

---

### Post by jackwilson on 2010-09-02
I though of changing my title to: I want to know what you know, WIFI help.

---

### Post by jackwilson on 2010-09-02
I went to the link you posted and did all of those commands, and my terminal response was: driver already installed.
What do I do next to get my WIFI working?

---

### Post by Tracy177 on 2010-09-02
> **jackwilson said:**
> I went to the link you posted and did all of those commands, and my terminal response was: driver already installed.
What do I do next to get my WIFI working?


can u paste dmesg output to see if your driver is installed or not ?

---

### Post by bredman on 2010-09-02
It looks as if everything is OK and you are almost finished.

If you paste the result of the following commands, it would really help.

dmesg
iwconfig

---

### Post by jackwilson on 2010-09-07
I've done everything that everyone has said to do. When I click system> administration> windows wireless drivers it says neti2220  Hardware present:Yes.
What do I do next?
I've rebooted and this is as far as I get.

---

### Post by jackwilson on 2010-09-07
This is what it shows after those commands:

[    0.188057] ACPI: Interpreter enabled
[    0.188068] ACPI: (supports S0 S3 S4 S5)
[    0.188092] ACPI: Using PIC for interrupt routing
[    0.188347] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[    0.192328] ACPI: EC: GPE = 0x1d, I/O: command/status = 0x66, data = 0x62
[    0.192400] ACPI: Power Resource [PFN0] (off)
[    0.192441] ACPI: Power Resource [PFN1] (off)
[    0.192611] ACPI: No dock devices found.
[    0.193348] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.193502] pci 0000:00:02.0: reg 10 32bit mmio pref: [0xe8000000-0xefffffff]
[    0.193509] pci 0000:00:02.0: reg 14 32bit mmio: [0xe0000000-0xe007ffff]
[    0.193515] pci 0000:00:02.0: reg 18 io port: [0x1800-0x1807]
[    0.193537] pci 0000:00:02.0: supports D1
[    0.193557] pci 0000:00:02.1: reg 10 32bit mmio pref: [0xf0000000-0xf7ffffff]
[    0.193563] pci 0000:00:02.1: reg 14 32bit mmio: [0xe0080000-0xe00fffff]
[    0.193586] pci 0000:00:02.1: supports D1
[    0.193656] pci 0000:00:1d.0: reg 20 io port: [0x1820-0x183f]
[    0.193715] pci 0000:00:1d.1: reg 20 io port: [0x1840-0x185f]
[    0.193765] pci 0000:00:1d.2: reg 20 io port: [0x1860-0x187f]
[    0.193822] pci 0000:00:1d.7: reg 10 32bit mmio: [0xe0100000-0xe01003ff]
[    0.193876] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.193882] pci 0000:00:1d.7: PME# disabled
[    0.193966] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[    0.193971] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH4 GPIO
[    0.193995] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.194002] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.194010] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.194017] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.194025] pci 0000:00:1f.1: reg 20 io port: [0x1810-0x181f]
[    0.194033] pci 0000:00:1f.1: reg 24 32bit mmio: [0x000000-0x0003ff]
[    0.194081] pci 0000:00:1f.3: reg 20 io port: [0x1880-0x189f]
[    0.194123] pci 0000:00:1f.5: reg 10 io port: [0x1c00-0x1cff]
[    0.194130] pci 0000:00:1f.5: reg 14 io port: [0x18c0-0x18ff]
[    0.194138] pci 0000:00:1f.5: reg 18 32bit mmio: [0xe0100c00-0xe0100dff]
[    0.194146] pci 0000:00:1f.5: reg 1c 32bit mmio: [0xe0100800-0xe01008ff]
[    0.194174] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.194179] pci 0000:00:1f.5: PME# disabled
[    0.194209] pci 0000:00:1f.6: reg 10 io port: [0x2400-0x24ff]
[    0.194216] pci 0000:00:1f.6: reg 14 io port: [0x2000-0x207f]
[    0.194251] pci 0000:00:1f.6: PME# supported from D0 D3hot D3cold
[    0.194256] pci 0000:00:1f.6: PME# disabled
[    0.194295] pci 0000:02:02.0: reg 10 32bit mmio: [0xe0200000-0xe0201fff]
[    0.194321] pci 0000:02:02.0: reg 30 32bit mmio pref: [0x000000-0x003fff]
[    0.194338] pci 0000:02:02.0: supports D1 D2
[    0.194341] pci 0000:02:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.194346] pci 0000:02:02.0: PME# disabled
[    0.194376] pci 0000:02:04.0: reg 10 io port: [0x3800-0x381f]
[    0.194384] pci 0000:02:04.0: reg 14 32bit mmio: [0xe0203800-0xe020381f]
[    0.194392] pci 0000:02:04.0: reg 18 32bit mmio: [0xe0203000-0xe02037ff]
[    0.194424] pci 0000:02:04.0: supports D2
[    0.194456] pci 0000:02:06.0: reg 10 32bit mmio: [0xe0202000-0xe0202fff]
[    0.194474] pci 0000:02:06.0: supports D1 D2
[    0.194477] pci 0000:02:06.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.194483] pci 0000:02:06.0: PME# disabled
[    0.194522] pci 0000:00:1e.0: transparent bridge
[    0.194528] pci 0000:00:1e.0: bridge io port: [0x3000-0x3fff]
[    0.194533] pci 0000:00:1e.0: bridge 32bit mmio: [0xe0200000-0xe05fffff]
[    0.194559] pci_bus 0000:00: on NUMA node 0
[    0.194566] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.194754] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.197925] ACPI: PCI Interrupt Link [LNKA] (IRQs *6)
[    0.198047] ACPI: PCI Interrupt Link [LNKB] (IRQs *10)
[    0.198165] ACPI: PCI Interrupt Link [LNKC] (IRQs *6)
[    0.198282] ACPI: PCI Interrupt Link [LNKD] (IRQs *6)
[    0.198400] ACPI: PCI Interrupt Link [LNKE] (IRQs *10)
[    0.198518] ACPI: PCI Interrupt Link [LNKF] (IRQs 10) *0, disabled.
[    0.198644] ACPI: PCI Interrupt Link [LNKG] (IRQs 6) *0, disabled.
[    0.198762] ACPI: PCI Interrupt Link [LNKH] (IRQs *10)
[    0.198899] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.198910] vgaarb: loaded
[    0.199082] SCSI subsystem initialized
[    0.199177] libata version 3.00 loaded.
[    0.199276] usbcore: registered new interface driver usbfs
[    0.199293] usbcore: registered new interface driver hub
[    0.199327] usbcore: registered new device driver usb
[    0.199518] ACPI: WMI: Mapper loaded
[    0.199521] PCI: Using ACPI for IRQ routing
[    0.199741] NetLabel: Initializing
[    0.199744] NetLabel:  domain hash size = 128
[    0.199746] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.199764] NetLabel:  unlabeled traffic allowed by default
[    0.199819] Switching to clocksource tsc
[    0.199999] AppArmor: AppArmor Filesystem Enabled
[    0.199999] pnp: PnP ACPI init
[    0.199999] ACPI: bus type pnp registered
[    0.201024] pnp: PnP ACPI: found 8 devices
[    0.201029] ACPI: ACPI bus type pnp unregistered
[    0.201035] PnPBIOS: Disabled by ACPI PNP
[    0.201055] system 00:04: ioport range 0x164e-0x164f has been reserved
[    0.201061] system 00:04: ioport range 0x600-0x60f has been reserved
[    0.201065] system 00:04: ioport range 0x700-0x70f has been reserved
[    0.201069] system 00:04: ioport range 0x800-0x80f has been reserved
[    0.201073] system 00:04: ioport range 0x1000-0x107f has been reserved
[    0.201077] system 00:04: ioport range 0x1180-0x11bf has been reserved
[    0.201081] system 00:04: ioport range 0x1c0-0x1cf has been reserved
[    0.201087] system 00:04: ioport range 0xfe00-0xfe00 has been reserved
[    0.201091] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[    0.201095] system 00:04: ioport range 0x610-0x61f has been reserved
[    0.201101] system 00:04: iomem range 0xfec10000-0xfec1ffff has been reserved
[    0.201106] system 00:04: iomem range 0xff800000-0xffbfffff has been reserved
[    0.201110] system 00:04: iomem range 0xfff00000-0xffffffff could not be reserved
[    0.201115] system 00:04: iomem range 0x0-0x9ffff could not be reserved
[    0.201119] system 00:04: iomem range 0xe0000-0xfffff could not be reserved
[    0.201123] system 00:04: iomem range 0xdf800-0xdffff could not be reserved
[    0.235908] pci 0000:02:06.0: CardBus bridge, secondary bus 0000:03
[    0.235912] pci 0000:02:06.0:   IO window: 0x003000-0x0030ff
[    0.235918] pci 0000:02:06.0:   IO window: 0x003400-0x0034ff
[    0.235923] pci 0000:02:06.0:   PREFETCH window: 0x20000000-0x23ffffff
[    0.235929] pci 0000:02:06.0:   MEM window: 0x28000000-0x2bffffff
[    0.235935] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.235939] pci 0000:00:1e.0:   IO window: 0x3000-0x3fff
[    0.235945] pci 0000:00:1e.0:   MEM window: 0xe0200000-0xe05fffff
[    0.235951] pci 0000:00:1e.0:   PREFETCH window: 0x20000000-0x25ffffff
[    0.235968] pci 0000:00:1e.0: setting latency timer to 64
[    0.235977] pci 0000:02:06.0: enabling device (0104 -> 0107)
[    0.236211] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 10
[    0.236214] PCI: setting IRQ 10 as level-triggered
[    0.236220] pci 0000:02:06.0: PCI INT A -> Link[LNKE] -> GSI 10 (level, low) -> IRQ 10
[    0.236230] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.236233] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.236237] pci_bus 0000:02: resource 0 io:  [0x3000-0x3fff]
[    0.236241] pci_bus 0000:02: resource 1 mem: [0xe0200000-0xe05fffff]
[    0.236245] pci_bus 0000:02: resource 2 pref mem [0x20000000-0x25ffffff]
[    0.236249] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
[    0.236252] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffff]
[    0.236256] pci_bus 0000:03: resource 0 io:  [0x3000-0x30ff]
[    0.236260] pci_bus 0000:03: resource 1 io:  [0x3400-0x34ff]
[    0.236264] pci_bus 0000:03: resource 2 pref mem [0x20000000-0x23ffffff]
[    0.236267] pci_bus 0000:03: resource 3 mem: [0x28000000-0x2bffffff]
[    0.236326] NET: Registered protocol family 2
[    0.236467] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.236888] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.237013] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.237136] TCP: Hash tables configured (established 16384 bind 16384)
[    0.237140] TCP reno registered
[    0.237256] NET: Registered protocol family 1
[    0.237286] pci 0000:00:02.0: Boot video device
[    0.237481] Simple Boot Flag at 0x37 set to 0x1
[    0.237595] cpufreq-nforce2: No nForce2 chipset.
[    0.237626] Scanning for low memory corruption every 60 seconds
[    0.237810] audit: initializing netlink socket (disabled)
[    0.237832] type=2000 audit(1283868256.236:1): initialized
[    0.252174] Trying to unpack rootfs image as initramfs...
[    0.268456] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.276214] VFS: Disk quotas dquot_6.5.2
[    0.276357] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.277398] fuse init (API version 7.13)
[    0.277542] msgmni has been set to 943
[    0.277863] alg: No test for stdrng (krng)
[    0.277963] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.277967] io scheduler noop registered
[    0.277970] io scheduler anticipatory registered
[    0.277973] io scheduler deadline registered
[    0.278050] io scheduler cfq registered (default)
[    0.278210] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.278241] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.278389] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.296351] ACPI: Lid Switch [LID]
[    0.296462] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.296468] ACPI: Sleep Button [SLPB]
[    0.296535] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.296538] ACPI: Power Button [PWRF]
[    0.296741] fan PNP0C0B:00: registered as cooling_device0
[    0.296749] ACPI: Fan [FAN0] (off)
[    0.296875] fan PNP0C0B:01: registered as cooling_device1
[    0.296888] ACPI: Fan [FAN1] (off)
[    0.297069] Marking TSC unstable due to TSC halts in idle
[    0.297117] processor LNXCPU:00: registered as cooling_device2
[    0.300547] Switching to clocksource acpi_pm
[    0.332766] thermal LNXTHERM:01: registered as thermal_zone0
[    0.332786] ACPI: Thermal Zone [THRM] (42 C)
[    0.332884] ACPI: SBS HC: EC = 0xde85c420, offset = 0x18, query_bit = 0x20
[    0.460269] ACPI: Smart Battery System [SBS0]: AC Adapter [AC0] (on-line)
[    0.571559] Freeing initrd memory: 8088k freed
[    3.812180] ACPI: Smart Battery System [SBS0]: Battery Slot [BAT0] (battery present)
[    3.814241] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    3.814944] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[    3.814951] serial 0000:00:1f.6: PCI INT B -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[    3.814961] serial 0000:00:1f.6: PCI INT B disabled
[    3.816094] isapnp: Scanning for PnP cards...
[    3.821925] brd: module loaded
[    3.822588] loop: module loaded
[    3.822734] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    3.822900] ata_piix 0000:00:1f.1: version 2.13
[    3.822933] ata_piix 0000:00:1f.1: power state changed by ACPI to D0
[    3.822943] ata_piix 0000:00:1f.1: power state changed by ACPI to D0
[    3.822949] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    3.823182] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 6
[    3.823187] PCI: setting IRQ 6 as level-triggered
[    3.823193] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKC] -> GSI 6 (level, low) -> IRQ 6
[    3.823246] ata_piix 0000:00:1f.1: setting latency timer to 64
[    3.823377] scsi0 : ata_piix
[    3.867043] scsi1 : ata_piix
[    3.868367] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[    3.868372] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[    3.868914] Fixed MDIO Bus: probed
[    3.868966] PPP generic driver version 2.4.2
[    3.869055] tun: Universal TUN/TAP device driver, 1.6
[    3.869058] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    3.869186] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.869419] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 10
[    3.869425] ehci_hcd 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 10 (level, low) -> IRQ 10
[    3.869446] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.869451] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.869500] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    3.869537] ehci_hcd 0000:00:1d.7: debug port 1
[    3.873424] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.873711] ehci_hcd 0000:00:1d.7: irq 10, io mem 0xe0100000
[    3.921130] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    3.921278] usb usb1: configuration #1 chosen from 1 choice
[    3.921319] hub 1-0:1.0: USB hub found
[    3.921331] hub 1-0:1.0: 6 ports detected
[    3.921410] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.921433] uhci_hcd: USB Universal Host Controller Interface driver
[    3.921713] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 6
[    3.921719] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 6 (level, low) -> IRQ 6
[    3.921729] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.921734] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.921792] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    3.921819] uhci_hcd 0000:00:1d.0: irq 6, io base 0x00001820
[    3.921953] usb usb2: configuration #1 chosen from 1 choice
[    3.921989] hub 2-0:1.0: USB hub found
[    3.921999] hub 2-0:1.0: 2 ports detected
[    3.922248] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 6
[    3.922253] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 6 (level, low) -> IRQ 6
[    3.922261] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.922265] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.922315] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    3.922338] uhci_hcd 0000:00:1d.1: irq 6, io base 0x00001840
[    3.922463] usb usb3: configuration #1 chosen from 1 choice
[    3.922499] hub 3-0:1.0: USB hub found
[    3.922508] hub 3-0:1.0: 2 ports detected
[    3.922566] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 6 (level, low) -> IRQ 6
[    3.922575] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.922580] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.922625] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    3.922648] uhci_hcd 0000:00:1d.2: irq 6, io base 0x00001860
[    3.922779] usb usb4: configuration #1 chosen from 1 choice
[    3.922815] hub 4-0:1.0: USB hub found
[    3.922829] hub 4-0:1.0: 2 ports detected
[    3.922952] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOU2] at 0x60,0x64 irq 1,12
[    3.925553] i8042.c: Detected active multiplexing controller, rev 1.1.
[    3.926522] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.926533] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    3.926571] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    3.926600] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    3.926634] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    3.926800] mice: PS/2 mouse device common for all mice
[    3.927029] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[    3.927048] rtc0: alarms up to one month, y3k, 242 bytes nvram
[    3.927244] device-mapper: uevent: version 1.0.3
[    3.927410] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    3.927488] device-mapper: multipath: version 1.1.0 loaded
[    3.927492] device-mapper: multipath round-robin: version 1.0.0 loaded
[    3.927680] EISA: Probing bus 0 at eisa.0
[    3.927689] Cannot allocate resource for EISA slot 1
[    3.927692] Cannot allocate resource for EISA slot 2
[    3.927695] Cannot allocate resource for EISA slot 3
[    3.927717] EISA: Detected 0 cards.
[    3.927827] cpuidle: using governor ladder
[    3.927907] cpuidle: using governor menu
[    3.928627] TCP cubic registered
[    3.928886] NET: Registered protocol family 10
[    3.929571] lo: Disabled Privacy Extensions
[    3.930076] NET: Registered protocol family 17
[    3.930155] ACPI Exception: AE_NOT_FOUND, Evaluating _PSS (20090903/processor_perflib-264)
[    3.930170] Using IPI No-Shortcut mode
[    3.930296] PM: Resume from disk failed.
[    3.930313] registered taskstats version 1
[    3.930578]   Magic number: 10:540:80
[    3.930694] rtc_cmos 00:01: setting system clock to 2010-09-07 14:04:20 UTC (1283868260)
[    3.930699] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.930701] EDD information not available.
[    4.105315] hub 2-0:1.0: over-current change on port 1
[    4.105685] ata2.01: NODEV after polling detection
[    4.149235] ata1.00: ATA-6: HTS424040M9AT00, MA2OA71A, max UDMA/100
[    4.149240] ata1.00: 78140160 sectors, multi 16: LBA48 
[    4.149780] ata2.00: ATAPI: UJDA760 DVD/CDRW, 1.00, max UDMA/33
[    4.193800] isapnp: No Plug & Play device found
[    4.193897] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    4.194580] ata2.00: configured for UDMA/33
[    4.194875] ata1.00: configured for UDMA/100
[    4.195059] scsi 0:0:0:0: Direct-Access     ATA      HTS424040M9AT00  MA2O PQ: 0 ANSI: 5
[    4.195243] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.195452] sd 0:0:0:0: [sda] 78140160 512-byte logical blocks: (40.0 GB/37.2 GiB)
[    4.195531] sd 0:0:0:0: [sda] Write Protect is off
[    4.195534] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.195566] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.195749]  sda:
[    4.196863] scsi 1:0:0:0: CD-ROM            MATSHITA UJDA760 DVD/CDRW 1.00 PQ: 0 ANSI: 5
[    4.199916] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    4.199921] Uniform CD-ROM driver Revision: 3.20
[    4.200092] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.200165] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    4.208051] hub 2-0:1.0: over-current change on port 2
[    4.225046]  sda1
[    4.225339] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.225357] Freeing unused kernel memory: 660k freed
[    4.225927] Write protecting the kernel text: 4680k
[    4.225983] Write protecting the kernel read-only data: 1844k
[    4.251680] udev: starting version 151
[    4.424118] usb 1-3: new high speed USB device using ehci_hcd and address 2
[    4.558570] usb 1-3: configuration #1 chosen from 1 choice
[    4.564180] b44 0000:02:02.0: PCI INT A -> Link[LNKD] -> GSI 6 (level, low) -> IRQ 6
[    4.588637] Initializing USB Mass Storage driver...
[    4.588792] scsi2 : SCSI emulation for USB Mass Storage devices
[    4.589059] usbcore: registered new interface driver usb-storage
[    4.589064] USB Mass Storage support registered.
[    4.589218] usb-storage: device found at 2
[    4.589221] usb-storage: waiting for device to settle before scanning
[    4.628119] ssb: Sonics Silicon Backplane found on PCI device 0000:02:02.0
[    4.628152] b44.c:v2.0
[    4.649066] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:c0:9f:66:31:09
[    4.906303] EXT4-fs (loop0): mounted filesystem with ordered data mode
[    4.908054] usb 3-2: new low speed USB device using uhci_hcd and address 2
[    5.066037] usb 3-2: configuration #1 chosen from 1 choice
[    5.308068] usb 4-2: new low speed USB device using uhci_hcd and address 2
[    5.483913] usb 4-2: configuration #1 chosen from 1 choice
[    5.486847] hub 1-0:1.0: over-current change on port 1
[    5.588055] hub 1-0:1.0: over-current change on port 2
[    9.588282] usb-storage: device scan complete
[    9.588752] scsi 2:0:0:0: Direct-Access     SanDisk  Cruzer           8.01 PQ: 0 ANSI: 0 CCS
[    9.589235] scsi 2:0:0:1: CD-ROM            SanDisk  Cruzer           8.01 PQ: 0 ANSI: 0
[    9.589846] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    9.591849] sd 2:0:0:0: [sdb] 3907711 512-byte logical blocks: (2.00 GB/1.86 GiB)
[    9.592970] sd 2:0:0:0: [sdb] Write Protect is off
[    9.592975] sd 2:0:0:0: [sdb] Mode Sense: 45 00 00 08
[    9.592978] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    9.593478] sr1: scsi3-mmc drive: 48x/48x tray
[    9.593634] sr 2:0:0:1: Attached scsi CD-ROM sr1
[    9.593745] sr 2:0:0:1: Attached scsi generic sg3 type 5
[    9.595216] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    9.595221]  sdb: sdb1
[    9.597589] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    9.597594] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   11.112411] udev: starting version 151
[   11.385791] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[   11.386057] acpi device:04: registered as cooling_device3
[   11.386218] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/LNXVIDEO:00/input/input5
[   11.386308] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[   11.565528] Linux agpgart interface v0.103
[   11.632123] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   11.693385] intel_rng: FWH not detected
[   11.734978] agpgart-intel 0000:00:00.0: Intel 855GM Chipset
[   11.735999] agpgart-intel 0000:00:00.0: detected 16252K stolen memory
[   11.749941] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xe8000000
[   11.788866] lp: driver loaded but no devices found
[   12.218019] [drm] Initialized drm 1.1.0 20060810
[   12.372997] Disabling lock debugging due to kernel taint
[   12.401569] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   12.512659] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x126eb1, caps: 0xa04713/0x4000
[   12.551260] type=1505 audit(1283886269.118:2):  operation="profile_load" pid=524 name="/sbin/dhclient3"
[   12.562050] type=1505 audit(1283886269.129:3):  operation="profile_load" pid=524 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   12.562500] type=1505 audit(1283886269.129:4):  operation="profile_load" pid=524 name="/usr/lib/connman/scripts/dhclient-script"
[   12.565904] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input6
[   12.771339] [drm] i915 disabling kernel modesetting for known bad device.
[   12.771372] pci 0000:00:02.0: PCI INT A -> Link[LNKA] -> GSI 6 (level, low) -> IRQ 6
[   12.771379] pci 0000:00:02.0: setting latency timer to 64
[   12.796532] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   12.797785] usbcore: registered new interface driver hiddev
[   12.812545] input: HID 0566:3002 as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input7
[   12.812713] generic-usb 0003:0566:3002.0001: input,hidraw0: USB HID v1.10 Keyboard [HID 0566:3002] on usb-0000:00:1d.1-2/input0
[   12.850831] input: HID 0566:3002 as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.1/input/input8
[   12.851048] generic-usb 0003:0566:3002.0002: input,hiddev96,hidraw1: USB HID v1.10 Device [HID 0566:3002] on usb-0000:00:1d.1-2/input1
[   12.864792] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/input/input9
[   12.864968] generic-usb 0003:046D:C018.0003: input,hidraw2: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1d.2-2/input0
[   12.865015] usbcore: registered new interface driver usbhid
[   12.865019] usbhid: v2.6:USB HID core driver
[   12.929451] yenta_cardbus 0000:02:06.0: CardBus bridge found [1025:0064]
[   12.929471] yenta_cardbus 0000:02:06.0: Enabling burst memory read transactions
[   12.929477] yenta_cardbus 0000:02:06.0: Using CSCINT to route CSC interrupts to PCI
[   12.929481] yenta_cardbus 0000:02:06.0: Routing CardBus interrupts to PCI
[   12.929487] yenta_cardbus 0000:02:06.0: TI: mfunc 0x01a21b22, devctl 0x64
[   12.950041] vga16fb: initializing
[   12.950049] vga16fb: mapped to 0xc00a0000
[   12.950313] fb0: VGA16 VGA frame buffer device
[   13.160610] yenta_cardbus 0000:02:06.0: ISA IRQ mask 0x08b8, PCI irq 10
[   13.160616] yenta_cardbus 0000:02:06.0: Socket status: 30000006
[   13.160621] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   13.160635] yenta_cardbus 0000:02:06.0: pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[   13.160641] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3000-0x3fff: clean.
[   13.160945] yenta_cardbus 0000:02:06.0: pcmcia: parent PCI bridge Memory window: 0xe0200000 - 0xe05fffff
[   13.160950] yenta_cardbus 0000:02:06.0: pcmcia: parent PCI bridge Memory window: 0x20000000 - 0x25ffffff
[   13.339271] ndiswrapper: driver neti2220 (LanExpress,08/11/2004,2.22.08.2004) loaded
[   13.339556] ndiswrapper 0000:02:04.0: PCI INT A -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[   13.381071] ndiswrapper: using IRQ 10
[   13.442249] Console: switching to colour frame buffer device 80x30
[   13.581067] wlan0: ethernet device 00:0e:9b:5f:09:16 using NDIS driver: neti2220, version: 0x20016, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 17FE:2220.5.conf
[   13.581090] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   13.581176] usbcore: registered new interface driver ndiswrapper
[   13.656374] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   13.657961] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[   13.658653] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   13.659233] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   13.660000] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   13.757323] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[   13.757370] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   13.884097] Adding 261112k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:105 across:15763552k 
[   14.076041] intel8x0_measure_ac97_clock: measured 53830 usecs (2594 samples)
[   14.076046] intel8x0: clocking to 48000
[   14.426325] EXT4-fs (loop1): mounted filesystem with ordered data mode
[   32.762323] type=1505 audit(1283886289.329:5):  operation="profile_load" pid=747 name="/usr/share/gdm/guest-session/Xsession"
[   32.770566] type=1505 audit(1283886289.337:6):  operation="profile_replace" pid=750 name="/sbin/dhclient3"
[   32.771389] type=1505 audit(1283886289.337:7):  operation="profile_replace" pid=750 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   32.771837] type=1505 audit(1283886289.337:8):  operation="profile_replace" pid=750 name="/usr/lib/connman/scripts/dhclient-script"
[   33.146987] type=1505 audit(1283886289.713:9):  operation="profile_load" pid=758 name="/usr/bin/evince"
[   33.158104] type=1505 audit(1283886289.725:10):  operation="profile_load" pid=758 name="/usr/bin/evince-previewer"
[   33.164813] type=1505 audit(1283886289.733:11):  operation="profile_load" pid=758 name="/usr/bin/evince-thumbnailer"
[   33.259978] type=1505 audit(1283886289.825:12):  operation="profile_load" pid=770 name="/usr/lib/cups/backend/cups-pdf"
[   33.261017] type=1505 audit(1283886289.829:13):  operation="profile_load" pid=770 name="/usr/sbin/cupsd"
[   33.331759] type=1505 audit(1283886289.899:14):  operation="profile_load" pid=771 name="/usr/sbin/tcpdump"
[   33.580971] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   33.593532] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   34.349735] ppdev: user-space parallel port driver
[   36.816231] b44: eth0: Link is up at 100 Mbps, full duplex.
[   36.816237] b44: eth0: Flow control is off for TX and off for RX.
[   36.816356] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   48.790836] ISO 9660 Extensions: Microsoft Joliet Level 3
[   48.826710] ISOFS: changing to secondary root

user@ubuntu:~$ iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:0 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

user@ubuntu:~$

---

### Post by jackwilson on 2010-09-07
[    0.052784] Time: 15:25:10  Date: 09/07/10
[    0.052848] NET: Registered protocol family 16
[    0.053005] EISA bus registered
[    0.053017] ACPI: bus type pci registered
[    0.054178] PCI: PCI BIOS revision 2.10 entry at 0xfd792, last bus=2
[    0.054181] PCI: Using configuration type 1 for base access
[    0.055474] bio: create slab <bio-0> at 0
[    0.056368] ACPI: EC: Look up EC in DSDT
[    0.060600] ACPI: EC: GPE storm detected, transactions will use polling mode
[    0.188057] ACPI: Interpreter enabled
[    0.188068] ACPI: (supports S0 S3 S4 S5)
[    0.188092] ACPI: Using PIC for interrupt routing
[    0.188347] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[    0.192331] ACPI: EC: GPE = 0x1d, I/O: command/status = 0x66, data = 0x62
[    0.192402] ACPI: Power Resource [PFN0] (off)
[    0.192443] ACPI: Power Resource [PFN1] (off)
[    0.192612] ACPI: No dock devices found.
[    0.193346] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.193502] pci 0000:00:02.0: reg 10 32bit mmio pref: [0xe8000000-0xefffffff]
[    0.193509] pci 0000:00:02.0: reg 14 32bit mmio: [0xe0000000-0xe007ffff]
[    0.193515] pci 0000:00:02.0: reg 18 io port: [0x1800-0x1807]
[    0.193537] pci 0000:00:02.0: supports D1
[    0.193557] pci 0000:00:02.1: reg 10 32bit mmio pref: [0xf0000000-0xf7ffffff]
[    0.193563] pci 0000:00:02.1: reg 14 32bit mmio: [0xe0080000-0xe00fffff]
[    0.193586] pci 0000:00:02.1: supports D1
[    0.193657] pci 0000:00:1d.0: reg 20 io port: [0x1820-0x183f]
[    0.193716] pci 0000:00:1d.1: reg 20 io port: [0x1840-0x185f]
[    0.193767] pci 0000:00:1d.2: reg 20 io port: [0x1860-0x187f]
[    0.193825] pci 0000:00:1d.7: reg 10 32bit mmio: [0xe0100000-0xe01003ff]
[    0.193879] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.193885] pci 0000:00:1d.7: PME# disabled
[    0.193970] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[    0.193975] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH4 GPIO
[    0.193999] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.194006] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.194014] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.194021] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.194029] pci 0000:00:1f.1: reg 20 io port: [0x1810-0x181f]
[    0.194037] pci 0000:00:1f.1: reg 24 32bit mmio: [0x000000-0x0003ff]
[    0.194086] pci 0000:00:1f.3: reg 20 io port: [0x1880-0x189f]
[    0.194127] pci 0000:00:1f.5: reg 10 io port: [0x1c00-0x1cff]
[    0.194135] pci 0000:00:1f.5: reg 14 io port: [0x18c0-0x18ff]
[    0.194142] pci 0000:00:1f.5: reg 18 32bit mmio: [0xe0100c00-0xe0100dff]
[    0.194150] pci 0000:00:1f.5: reg 1c 32bit mmio: [0xe0100800-0xe01008ff]
[    0.194178] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.194183] pci 0000:00:1f.5: PME# disabled
[    0.194213] pci 0000:00:1f.6: reg 10 io port: [0x2400-0x24ff]
[    0.194220] pci 0000:00:1f.6: reg 14 io port: [0x2000-0x207f]
[    0.194255] pci 0000:00:1f.6: PME# supported from D0 D3hot D3cold
[    0.194260] pci 0000:00:1f.6: PME# disabled
[    0.194299] pci 0000:02:02.0: reg 10 32bit mmio: [0xe0200000-0xe0201fff]
[    0.194325] pci 0000:02:02.0: reg 30 32bit mmio pref: [0x000000-0x003fff]
[    0.194341] pci 0000:02:02.0: supports D1 D2
[    0.194345] pci 0000:02:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.194349] pci 0000:02:02.0: PME# disabled
[    0.194380] pci 0000:02:04.0: reg 10 io port: [0x3800-0x381f]
[    0.194387] pci 0000:02:04.0: reg 14 32bit mmio: [0xe0203800-0xe020381f]
[    0.194395] pci 0000:02:04.0: reg 18 32bit mmio: [0xe0203000-0xe02037ff]
[    0.194427] pci 0000:02:04.0: supports D2
[    0.194459] pci 0000:02:06.0: reg 10 32bit mmio: [0xe0202000-0xe0202fff]
[    0.194477] pci 0000:02:06.0: supports D1 D2
[    0.194480] pci 0000:02:06.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.194485] pci 0000:02:06.0: PME# disabled
[    0.194525] pci 0000:00:1e.0: transparent bridge
[    0.194530] pci 0000:00:1e.0: bridge io port: [0x3000-0x3fff]
[    0.194536] pci 0000:00:1e.0: bridge 32bit mmio: [0xe0200000-0xe05fffff]
[    0.194562] pci_bus 0000:00: on NUMA node 0
[    0.194569] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.194757] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.197930] ACPI: PCI Interrupt Link [LNKA] (IRQs *6)
[    0.198050] ACPI: PCI Interrupt Link [LNKB] (IRQs *10)
[    0.198168] ACPI: PCI Interrupt Link [LNKC] (IRQs *6)
[    0.198286] ACPI: PCI Interrupt Link [LNKD] (IRQs *6)
[    0.198404] ACPI: PCI Interrupt Link [LNKE] (IRQs *10)
[    0.198521] ACPI: PCI Interrupt Link [LNKF] (IRQs 10) *0, disabled.
[    0.198645] ACPI: PCI Interrupt Link [LNKG] (IRQs 6) *0, disabled.
[    0.198764] ACPI: PCI Interrupt Link [LNKH] (IRQs *10)
[    0.198900] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.198912] vgaarb: loaded
[    0.199083] SCSI subsystem initialized
[    0.199178] libata version 3.00 loaded.
[    0.199277] usbcore: registered new interface driver usbfs
[    0.199294] usbcore: registered new interface driver hub
[    0.199329] usbcore: registered new device driver usb
[    0.199519] ACPI: WMI: Mapper loaded
[    0.199522] PCI: Using ACPI for IRQ routing
[    0.199741] NetLabel: Initializing
[    0.199744] NetLabel:  domain hash size = 128
[    0.199746] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.199764] NetLabel:  unlabeled traffic allowed by default
[    0.199819] Switching to clocksource tsc
[    0.199999] AppArmor: AppArmor Filesystem Enabled
[    0.199999] pnp: PnP ACPI init
[    0.199999] ACPI: bus type pnp registered
[    0.201014] pnp: PnP ACPI: found 8 devices
[    0.201019] ACPI: ACPI bus type pnp unregistered
[    0.201025] PnPBIOS: Disabled by ACPI PNP
[    0.201044] system 00:04: ioport range 0x164e-0x164f has been reserved
[    0.201050] system 00:04: ioport range 0x600-0x60f has been reserved
[    0.201054] system 00:04: ioport range 0x700-0x70f has been reserved
[    0.201058] system 00:04: ioport range 0x800-0x80f has been reserved
[    0.201062] system 00:04: ioport range 0x1000-0x107f has been reserved
[    0.201066] system 00:04: ioport range 0x1180-0x11bf has been reserved
[    0.201071] system 00:04: ioport range 0x1c0-0x1cf has been reserved
[    0.201076] system 00:04: ioport range 0xfe00-0xfe00 has been reserved
[    0.201080] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[    0.201085] system 00:04: ioport range 0x610-0x61f has been reserved
[    0.201091] system 00:04: iomem range 0xfec10000-0xfec1ffff has been reserved
[    0.201095] system 00:04: iomem range 0xff800000-0xffbfffff has been reserved
[    0.201100] system 00:04: iomem range 0xfff00000-0xffffffff could not be reserved
[    0.201104] system 00:04: iomem range 0x0-0x9ffff could not be reserved
[    0.201108] system 00:04: iomem range 0xe0000-0xfffff could not be reserved
[    0.201113] system 00:04: iomem range 0xdf800-0xdffff could not be reserved
[    0.235890] pci 0000:02:06.0: CardBus bridge, secondary bus 0000:03
[    0.235895] pci 0000:02:06.0:   IO window: 0x003000-0x0030ff
[    0.235900] pci 0000:02:06.0:   IO window: 0x003400-0x0034ff
[    0.235906] pci 0000:02:06.0:   PREFETCH window: 0x20000000-0x23ffffff
[    0.235912] pci 0000:02:06.0:   MEM window: 0x28000000-0x2bffffff
[    0.235917] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.235921] pci 0000:00:1e.0:   IO window: 0x3000-0x3fff
[    0.235928] pci 0000:00:1e.0:   MEM window: 0xe0200000-0xe05fffff
[    0.235934] pci 0000:00:1e.0:   PREFETCH window: 0x20000000-0x25ffffff
[    0.235951] pci 0000:00:1e.0: setting latency timer to 64
[    0.235960] pci 0000:02:06.0: enabling device (0104 -> 0107)
[    0.236193] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 10
[    0.236197] PCI: setting IRQ 10 as level-triggered
[    0.236203] pci 0000:02:06.0: PCI INT A -> Link[LNKE] -> GSI 10 (level, low) -> IRQ 10
[    0.236212] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.236216] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.236220] pci_bus 0000:02: resource 0 io:  [0x3000-0x3fff]
[    0.236224] pci_bus 0000:02: resource 1 mem: [0xe0200000-0xe05fffff]
[    0.236227] pci_bus 0000:02: resource 2 pref mem [0x20000000-0x25ffffff]
[    0.236231] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
[    0.236235] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffff]
[    0.236239] pci_bus 0000:03: resource 0 io:  [0x3000-0x30ff]
[    0.236242] pci_bus 0000:03: resource 1 io:  [0x3400-0x34ff]
[    0.236246] pci_bus 0000:03: resource 2 pref mem [0x20000000-0x23ffffff]
[    0.236250] pci_bus 0000:03: resource 3 mem: [0x28000000-0x2bffffff]
[    0.236306] NET: Registered protocol family 2
[    0.236448] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.236869] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.236994] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.237119] TCP: Hash tables configured (established 16384 bind 16384)
[    0.237123] TCP reno registered
[    0.237239] NET: Registered protocol family 1
[    0.237269] pci 0000:00:02.0: Boot video device
[    0.237465] Simple Boot Flag at 0x37 set to 0x1
[    0.237579] cpufreq-nforce2: No nForce2 chipset.
[    0.237611] Scanning for low memory corruption every 60 seconds
[    0.237791] audit: initializing netlink socket (disabled)
[    0.237812] type=2000 audit(1283873110.236:1): initialized
[    0.252152] Trying to unpack rootfs image as initramfs...
[    0.268430] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.276199] VFS: Disk quotas dquot_6.5.2
[    0.276340] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.277386] fuse init (API version 7.13)
[    0.277530] msgmni has been set to 943
[    0.277851] alg: No test for stdrng (krng)
[    0.277953] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.277957] io scheduler noop registered
[    0.277960] io scheduler anticipatory registered
[    0.277963] io scheduler deadline registered
[    0.278039] io scheduler cfq registered (default)
[    0.278199] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.278230] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.278378] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.296324] ACPI: Lid Switch [LID]
[    0.296435] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.296442] ACPI: Sleep Button [SLPB]
[    0.296509] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.296513] ACPI: Power Button [PWRF]
[    0.296715] fan PNP0C0B:00: registered as cooling_device0
[    0.296723] ACPI: Fan [FAN0] (off)
[    0.296850] fan PNP0C0B:01: registered as cooling_device1
[    0.296862] ACPI: Fan [FAN1] (off)
[    0.297042] Marking TSC unstable due to TSC halts in idle
[    0.297092] processor LNXCPU:00: registered as cooling_device2
[    0.300520] Switching to clocksource acpi_pm
[    0.332740] thermal LNXTHERM:01: registered as thermal_zone0
[    0.332758] ACPI: Thermal Zone [THRM] (42 C)
[    0.332858] ACPI: SBS HC: EC = 0xde85c420, offset = 0x18, query_bit = 0x20
[    0.460250] ACPI: Smart Battery System [SBS0]: AC Adapter [AC0] (on-line)
[    0.571529] Freeing initrd memory: 8088k freed
[    3.812180] ACPI: Smart Battery System [SBS0]: Battery Slot [BAT0] (battery present)
[    3.814242] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    3.814945] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[    3.814953] serial 0000:00:1f.6: PCI INT B -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[    3.814963] serial 0000:00:1f.6: PCI INT B disabled
[    3.816097] isapnp: Scanning for PnP cards...
[    3.821928] brd: module loaded
[    3.822593] loop: module loaded
[    3.822738] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    3.822905] ata_piix 0000:00:1f.1: version 2.13
[    3.822938] ata_piix 0000:00:1f.1: power state changed by ACPI to D0
[    3.822946] ata_piix 0000:00:1f.1: power state changed by ACPI to D0
[    3.822953] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    3.823187] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 6
[    3.823191] PCI: setting IRQ 6 as level-triggered
[    3.823197] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKC] -> GSI 6 (level, low) -> IRQ 6
[    3.823248] ata_piix 0000:00:1f.1: setting latency timer to 64
[    3.823378] scsi0 : ata_piix
[    3.867050] scsi1 : ata_piix
[    3.868371] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[    3.868375] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[    3.868917] Fixed MDIO Bus: probed
[    3.868969] PPP generic driver version 2.4.2
[    3.869057] tun: Universal TUN/TAP device driver, 1.6
[    3.869060] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    3.869188] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.869422] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 10
[    3.869427] ehci_hcd 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 10 (level, low) -> IRQ 10
[    3.869448] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.869453] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.869503] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    3.869540] ehci_hcd 0000:00:1d.7: debug port 1
[    3.873424] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.873712] ehci_hcd 0000:00:1d.7: irq 10, io mem 0xe0100000
[    3.921138] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    3.921288] usb usb1: configuration #1 chosen from 1 choice
[    3.921328] hub 1-0:1.0: USB hub found
[    3.921340] hub 1-0:1.0: 6 ports detected
[    3.921421] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.921444] uhci_hcd: USB Universal Host Controller Interface driver
[    3.921724] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 6
[    3.921729] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 6 (level, low) -> IRQ 6
[    3.921740] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.921744] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.921804] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    3.921831] uhci_hcd 0000:00:1d.0: irq 6, io base 0x00001820
[    3.921964] usb usb2: configuration #1 chosen from 1 choice
[    3.922000] hub 2-0:1.0: USB hub found
[    3.922010] hub 2-0:1.0: 2 ports detected
[    3.922260] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 6
[    3.922265] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 6 (level, low) -> IRQ 6
[    3.922274] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.922278] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.922329] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    3.922351] uhci_hcd 0000:00:1d.1: irq 6, io base 0x00001840
[    3.922477] usb usb3: configuration #1 chosen from 1 choice
[    3.922513] hub 3-0:1.0: USB hub found
[    3.922522] hub 3-0:1.0: 2 ports detected
[    3.922580] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 6 (level, low) -> IRQ 6
[    3.922589] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.922593] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.922639] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    3.922662] uhci_hcd 0000:00:1d.2: irq 6, io base 0x00001860
[    3.922793] usb usb4: configuration #1 chosen from 1 choice
[    3.922829] hub 4-0:1.0: USB hub found
[    3.922842] hub 4-0:1.0: 2 ports detected
[    3.922965] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOU2] at 0x60,0x64 irq 1,12
[    3.925008] i8042.c: Detected active multiplexing controller, rev 1.1.
[    3.925976] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.925988] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    3.926025] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    3.926054] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    3.926089] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    3.926255] mice: PS/2 mouse device common for all mice
[    3.926485] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[    3.926504] rtc0: alarms up to one month, y3k, 242 bytes nvram
[    3.926701] device-mapper: uevent: version 1.0.3
[    3.926868] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    3.926945] device-mapper: multipath: version 1.1.0 loaded
[    3.926949] device-mapper: multipath round-robin: version 1.0.0 loaded
[    3.927135] EISA: Probing bus 0 at eisa.0
[    3.927144] Cannot allocate resource for EISA slot 1
[    3.927147] Cannot allocate resource for EISA slot 2
[    3.927150] Cannot allocate resource for EISA slot 3
[    3.927172] EISA: Detected 0 cards.
[    3.927283] cpuidle: using governor ladder
[    3.927362] cpuidle: using governor menu
[    3.928081] TCP cubic registered
[    3.928340] NET: Registered protocol family 10
[    3.929025] lo: Disabled Privacy Extensions
[    3.929507] NET: Registered protocol family 17
[    3.929586] ACPI Exception: AE_NOT_FOUND, Evaluating _PSS (20090903/processor_perflib-264)
[    3.929599] Using IPI No-Shortcut mode
[    3.929726] PM: Resume from disk failed.
[    3.929742] registered taskstats version 1
[    3.930022]   Magic number: 10:508:436
[    3.930155] rtc_cmos 00:01: setting system clock to 2010-09-07 15:25:14 UTC (1283873114)
[    3.930160] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.930163] EDD information not available.
[    4.104807] hub 2-0:1.0: over-current change on port 1
[    4.105173] ata2.01: NODEV after polling detection
[    4.148773] ata1.00: ATA-6: HTS424040M9AT00, MA2OA71A, max UDMA/100
[    4.148777] ata1.00: 78140160 sectors, multi 16: LBA48 
[    4.149317] ata2.00: ATAPI: UJDA760 DVD/CDRW, 1.00, max UDMA/33
[    4.193284] isapnp: No Plug & Play device found
[    4.193380] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    4.194097] ata2.00: configured for UDMA/33
[    4.194276] ata1.00: configured for UDMA/100
[    4.194476] scsi 0:0:0:0: Direct-Access     ATA      HTS424040M9AT00  MA2O PQ: 0 ANSI: 5
[    4.194661] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.194870] sd 0:0:0:0: [sda] 78140160 512-byte logical blocks: (40.0 GB/37.2 GiB)
[    4.194948] sd 0:0:0:0: [sda] Write Protect is off
[    4.194952] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.194984] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.195167]  sda:
[    4.196303] scsi 1:0:0:0: CD-ROM            MATSHITA UJDA760 DVD/CDRW 1.00 PQ: 0 ANSI: 5
[    4.199359] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    4.199363] Uniform CD-ROM driver Revision: 3.20
[    4.199510] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.199580] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    4.208048] hub 2-0:1.0: over-current change on port 2
[    4.220690]  sda1
[    4.220986] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.221005] Freeing unused kernel memory: 660k freed
[    4.221577] Write protecting the kernel text: 4680k
[    4.221632] Write protecting the kernel read-only data: 1844k
[    4.248890] udev: starting version 151
[    4.424079] usb 1-3: new high speed USB device using ehci_hcd and address 2
[    4.552900] b44 0000:02:02.0: PCI INT A -> Link[LNKD] -> GSI 6 (level, low) -> IRQ 6
[    4.557064] usb 1-3: configuration #1 chosen from 1 choice
[    4.580975] Initializing USB Mass Storage driver...
[    4.583346] scsi2 : SCSI emulation for USB Mass Storage devices
[    4.585031] usbcore: registered new interface driver usb-storage
[    4.585037] USB Mass Storage support registered.
[    4.585561] usb-storage: device found at 2
[    4.585565] usb-storage: waiting for device to settle before scanning
[    4.616169] ssb: Sonics Silicon Backplane found on PCI device 0000:02:02.0
[    4.616204] b44.c:v2.0
[    4.637008] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:c0:9f:66:31:09
[    4.887690] EXT4-fs (loop0): mounted filesystem with ordered data mode
[    4.908048] usb 3-2: new low speed USB device using uhci_hcd and address 2
[    5.065608] usb 3-2: configuration #1 chosen from 1 choice
[    5.308060] usb 4-2: new low speed USB device using uhci_hcd and address 2
[    5.483941] usb 4-2: configuration #1 chosen from 1 choice
[    5.486867] hub 1-0:1.0: over-current change on port 1
[    5.588064] hub 1-0:1.0: over-current change on port 2
[    9.584288] usb-storage: device scan complete
[    9.584876] scsi 2:0:0:0: Direct-Access     SanDisk  Cruzer           8.01 PQ: 0 ANSI: 0 CCS
[    9.585360] scsi 2:0:0:1: CD-ROM            SanDisk  Cruzer           8.01 PQ: 0 ANSI: 0
[    9.585970] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    9.587975] sd 2:0:0:0: [sdb] 3907711 512-byte logical blocks: (2.00 GB/1.86 GiB)
[    9.589095] sd 2:0:0:0: [sdb] Write Protect is off
[    9.589099] sd 2:0:0:0: [sdb] Mode Sense: 45 00 00 08
[    9.589103] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    9.589706] sr1: scsi3-mmc drive: 48x/48x tray
[    9.589883] sr 2:0:0:1: Attached scsi CD-ROM sr1
[    9.590006] sr 2:0:0:1: Attached scsi generic sg3 type 5
[    9.591464] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    9.591469]  sdb: sdb1
[    9.593715] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    9.593720] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   11.264127] udev: starting version 151
[   11.626913] Linux agpgart interface v0.103
[   11.632074] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   11.650895] intel_rng: FWH not detected
[   11.665131] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[   11.665403] acpi device:04: registered as cooling_device3
[   11.665551] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/LNXVIDEO:00/input/input5
[   11.665644] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[   11.926192] agpgart-intel 0000:00:00.0: Intel 855GM Chipset
[   11.926407] agpgart-intel 0000:00:00.0: detected 16252K stolen memory
[   11.928711] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xe8000000
[   11.991211] lp: driver loaded but no devices found
[   12.381736] [drm] Initialized drm 1.1.0 20060810
[   12.495984] Disabling lock debugging due to kernel taint
[   12.522610] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   12.545950] type=1505 audit(1283891123.113:2):  operation="profile_load" pid=534 name="/sbin/dhclient3"
[   12.546764] type=1505 audit(1283891123.113:3):  operation="profile_load" pid=534 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   12.547199] type=1505 audit(1283891123.113:4):  operation="profile_load" pid=534 name="/usr/lib/connman/scripts/dhclient-script"
[   12.603946] usbcore: registered new interface driver hiddev
[   12.629716] input: HID 0566:3002 as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input6
[   12.629860] generic-usb 0003:0566:3002.0001: input,hidraw0: USB HID v1.10 Keyboard [HID 0566:3002] on usb-0000:00:1d.1-2/input0
[   12.667849] input: HID 0566:3002 as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.1/input/input7
[   12.668255] generic-usb 0003:0566:3002.0002: input,hiddev96,hidraw1: USB HID v1.10 Device [HID 0566:3002] on usb-0000:00:1d.1-2/input1
[   12.683582] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/input/input8
[   12.683757] generic-usb 0003:046D:C018.0003: input,hidraw2: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1d.2-2/input0
[   12.683805] usbcore: registered new interface driver usbhid
[   12.683809] usbhid: v2.6:USB HID core driver
[   12.792396] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x126eb1, caps: 0xa04713/0x4000
[   12.834325] yenta_cardbus 0000:02:06.0: CardBus bridge found [1025:0064]
[   12.834345] yenta_cardbus 0000:02:06.0: Enabling burst memory read transactions
[   12.834351] yenta_cardbus 0000:02:06.0: Using CSCINT to route CSC interrupts to PCI
[   12.834355] yenta_cardbus 0000:02:06.0: Routing CardBus interrupts to PCI
[   12.834361] yenta_cardbus 0000:02:06.0: TI: mfunc 0x01a21b22, devctl 0x64
[   12.844788] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input9
[   13.049719] [drm] i915 disabling kernel modesetting for known bad device.
[   13.049753] ndiswrapper 0000:00:02.0: PCI INT A -> Link[LNKA] -> GSI 6 (level, low) -> IRQ 6
[   13.049760] ndiswrapper 0000:00:02.0: setting latency timer to 64
[   13.064931] yenta_cardbus 0000:02:06.0: ISA IRQ mask 0x08b8, PCI irq 10
[   13.064937] yenta_cardbus 0000:02:06.0: Socket status: 30000006
[   13.064942] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   13.064956] yenta_cardbus 0000:02:06.0: pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[   13.064961] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3000-0x3fff: clean.
[   13.065245] yenta_cardbus 0000:02:06.0: pcmcia: parent PCI bridge Memory window: 0xe0200000 - 0xe05fffff
[   13.065250] yenta_cardbus 0000:02:06.0: pcmcia: parent PCI bridge Memory window: 0x20000000 - 0x25ffffff
[   13.078837] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   13.279676] vga16fb: initializing
[   13.279685] vga16fb: mapped to 0xc00a0000
[   13.279960] fb0: VGA16 VGA frame buffer device
[   13.294493] ndiswrapper: driver neti2220 (LanExpress,08/11/2004,2.22.08.2004) loaded
[   13.294783] ndiswrapper 0000:02:04.0: PCI INT A -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[   13.335056] ndiswrapper: using IRQ 10
[   13.548234] wlan0: ethernet device 00:0e:9b:5f:09:16 using NDIS driver: neti2220, version: 0x20016, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 17FE:2220.5.conf
[   13.548257] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   13.548347] usbcore: registered new interface driver ndiswrapper
[   13.635977] Console: switching to colour frame buffer device 80x30
[   13.692002] Adding 261112k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:105 across:15763552k 
[   13.850543] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   13.854210] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[   13.854903] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   13.855480] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   13.856289] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   14.126199] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[   14.126235] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   14.421541] EXT4-fs (loop1): mounted filesystem with ordered data mode
[   14.444054] intel8x0_measure_ac97_clock: measured 53850 usecs (2595 samples)
[   14.444059] intel8x0: clocking to 48000
[   33.354221] type=1505 audit(1283891143.921:5):  operation="profile_load" pid=761 name="/usr/share/gdm/guest-session/Xsession"
[   33.357897] type=1505 audit(1283891143.925:6):  operation="profile_replace" pid=766 name="/sbin/dhclient3"
[   33.358723] type=1505 audit(1283891143.925:7):  operation="profile_replace" pid=766 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   33.366777] type=1505 audit(1283891143.933:8):  operation="profile_replace" pid=766 name="/usr/lib/connman/scripts/dhclient-script"
[   33.511125] type=1505 audit(1283891144.077:9):  operation="profile_load" pid=770 name="/usr/bin/evince"
[   33.522529] type=1505 audit(1283891144.089:10):  operation="profile_load" pid=770 name="/usr/bin/evince-previewer"
[   33.529425] type=1505 audit(1283891144.097:11):  operation="profile_load" pid=770 name="/usr/bin/evince-thumbnailer"
[   33.580603] type=1505 audit(1283891144.149:12):  operation="profile_load" pid=776 name="/usr/lib/cups/backend/cups-pdf"
[   33.581595] type=1505 audit(1283891144.149:13):  operation="profile_load" pid=776 name="/usr/sbin/cupsd"
[   33.585276] type=1505 audit(1283891144.153:14):  operation="profile_load" pid=777 name="/usr/sbin/tcpdump"
[   33.841226] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   33.858746] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   34.746150] ppdev: user-space parallel port driver
[   36.816215] b44: eth0: Link is up at 100 Mbps, full duplex.
[   36.816221] b44: eth0: Flow control is off for TX and off for RX.
[   36.816328] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   67.505147] ISO 9660 Extensions: Microsoft Joliet Level 3
[   67.543869] ISOFS: changing to secondary root
[ 3044.020062] usb 3-2: reset low speed USB device using uhci_hcd and address 2
[ 7054.504110] usb 3-2: reset low speed USB device using uhci_hcd and address 2
[ 7056.960058] usb 3-2: reset low speed USB device using uhci_hcd and address 2
[ 8785.152060] usb 3-2: reset low speed USB device using uhci_hcd and address 2
[ 9486.864069] usb 3-2: reset low speed USB device using uhci_hcd and address 2
user@ubuntu:~$

---

### Post by anewguy on 2010-09-07
Since you are trying ndiswrapper via the gui'd front-end ndisgtk, we first need to verify some things:

- you installed ndiswrapper-common first
- you installed ndiswrapper-utilities second
- you installed ndisgtk third

- you have both the .inf and .sys files for your Windows driver.  Make sure both are in the same folder - I normally tell people just put them on the desktop.

- you have removed all previous attempts at getting this working via ndiswrapper/ndisgtk:

[LIST]
[*]open a terminal window (Applications/Accessories/Terminal)
[*]type:  sudo ndiswrapper -l <press enter> That's a lower case "L" for "list".
[*]For every driver/device returned in the list:[LIST]
[*]sudo ndiswrapper -e xxxxxx <press enter> where xxxxxx is one of the drivers/devices returned in the "list" command
[*]repeat this until sudo ndiswrapper -l returns nothing.
[/LIST][/LIST]

Now add the driver/device via ndisgtk:

- via ndisgtk (System/Administration/Windows Wireless Drivers), do the add (or new) and point it to your .inf file - remember the .sys file(s) must be in the same folder.  Be sure that when you have finished the add that the device shows as ready.

Now be sure wireless is enabled in network manager:

- right-click on the network manager icon and be sure "Enable Wireless" is checked - if not, check it.
- exit from network manager and wait a few seconds

Now check for wireless networks in network manager:

- left-click on the network manager icon and see if any wireless networks show.

Other things to be aware of:

- if your router uses MAC filtering, be sure the MAC of your PC is in the allowed list on the router

- if your router uses some sort of protection/encryption, be sure you match it and the password/passphrase when trying to connect 

- if your router does not broadcast the SSID (the name of your network) you must specifically set up the connection via network manager


Dave ;)

---

### Post by jackwilson on 2010-09-08
Thank you very much 
my wifi is now working fine

---

### Post by anewguy on 2010-09-08
You're welcome!

Dave ;)

---

### Post by jackwilson on 2010-09-26
Hi again,

long story short. my laptop crashed so I dumped everything and reloaded my widows xp home and my ubuntu 10.04 now when I add my driver inf. file it says invalid driver and when I type dmesg in my terminal it says.

 2173.925554] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[ 2173.989800] ndiswrapper (load_wrap_driver:108): couldn't load driver neti2220; check system log for messages from 'loadndisdriver'
[ 2173.989901] usbcore: registered new interface driver ndiswrapper

am I close to getting it right this time, I hope?

please help again 
thanks
jackwilson

---

