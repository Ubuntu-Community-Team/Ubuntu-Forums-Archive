---
title: "Feisty, Netgear WG311v2 and wicd working great!"
date: 2007-05-31
forum: Networking &amp; Wireless
---

### Post by dlbolton on 2007-05-31
I just wanted to let anyone know that this combo has been working great for the last 4-6 weeks. I am really excited about how wicd has transformed the wireless support in 7.04 from a PITA to something I no longer have to even think about!

Previously I had been able to get my wireless card to work only once - until a restart broke things. I could load the firmware, even get an ip address but I could not connect to the internet.  I have naever been able to get network manager to work with this wireless card.

Then I installed wicd.  In less than a minute it connected to my router and has been rock-solid ever since.  Interestingly, it has been WAY more stable than my 2 windows computers.  On those 2, the wireless connection frequently drops out then (usually but not always) reconnects.

I am not using WPA ( I am just relying on not broadcasting my SSID) so I am not sure this is a really stringent test, it is just the network in my house.

Dave

---

### Post by paleck on 2007-05-31
I cant seem to get mine to connect to any networks out of the box. Any idea what I am doing wrong?

---

### Post by dlbolton on 2007-05-31
I have to admit I am starting to get a little rusty but here goes ...

I am assuming you have a WG311v2 wireless card. Let me know if that is not correct. That is what  I have and it (along with several other brands/models of cards) are based on the Texas Instruments acx111 chipset.  

First run the following command and post the results:    **sudo dmesg**
This will produce some fairly lengthy output, not all of which will be related to your wireless card.  What this will do is to show if the firmware is getting loaded and will also show the error that is causing your card to not work.  

Next, do the same for the following commands:         **sudo iwconfig**
This will show whether your system is even aware of your wireless card.

and:                                 **sudo ifconfig**
This wil show whether your card is talking to your router. In my case I could not get the router to assign an ip address to my wireless card.

Not long ago I was pretty frustrated, so I can appreciate what you are going through.  I will try to check this thread tonight.

Dave

---

### Post by paleck on 2007-05-31
[PHP]
chris@chris-desktop:~$ sudo dmesg
[    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000002fef0000 end: 000000002fff0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000002fff0000 size: 0000000000003000 end: 000000002fff3000 type: 4
[    0.000000] copy_e820_map() start: 000000002fff3000 size: 000000000000d000 end: 0000000030000000 type: 3
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000001000 end: 00000000fec01000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
[    0.000000] copy_e820_map() start: 00000000ffff0000 size: 0000000000010000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000002fff0000 (usable)
[    0.000000]  BIOS-e820: 000000002fff0000 - 000000002fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000002fff3000 - 0000000030000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 767MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f5380
[    0.000000] Entering add_active_range(0, 0, 196592) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   196592
[    0.000000]   HighMem    196592 ->   196592
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   196592
[    0.000000] On node 0 totalpages: 196592
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1503 pages used for memmap
[    0.000000]   Normal zone: 190993 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 VIAK8T                                ) @ 0x000f6da0
[    0.000000] ACPI: RSDT (v001 VIAK8T AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x2fff3000
[    0.000000] ACPI: FADT (v001 VIAK8T AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x2fff3040
[    0.000000] ACPI: MADT (v001 VIAK8T AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x2fff8140
[    0.000000] ACPI: DSDT (v001 VIAK8T AWRDACPI 0x00001000 MSFT 0x0100000e) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:12 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 30000000:cec00000)
[    0.000000] Detected 1599.928 MHz processor.
[   18.187506] Built 1 zonelists.  Total pages: 195057
[   18.187510] Kernel command line: root=UUID=4fcbed27-85a1-4fbf-b5c7-250bb8dfcc8f ro quiet splash
[   18.187668] mapped APIC to ffffd000 (fee00000)
[   18.187671] mapped IOAPIC to ffffc000 (fec00000)
[   18.187674] Enabling fast FPU save and restore... done.
[   18.187677] Enabling unmasked SIMD FPU exception support... done.
[   18.187687] Initializing CPU#0
[   18.187766] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   18.189312] Console: colour VGA+ 80x25
[   18.189922] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   18.190922] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   18.207259] Memory: 768064k/786368k available (1992k kernel code, 17620k reserved, 893k data, 328k init, 0k highmem)
[   18.207271] virtual kernel memory layout:
[   18.207272]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   18.207274]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   18.207275]     vmalloc : 0xf0800000 - 0xff7fe000   ( 239 MB)
[   18.207277]     lowmem  : 0xc0000000 - 0xefff0000   ( 767 MB)
[   18.207278]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[   18.207280]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[   18.207281]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[   18.207285] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   18.283770] Calibrating delay using timer specific routine.. 3203.46 BogoMIPS (lpj=6406936)
[   18.283813] Security Framework v1.0.0 initialized
[   18.283818] SELinux:  Disabled at boot.
[   18.283835] Mount-cache hash table entries: 512
[   18.283965] CPU: After generic identify, caps: 078bfbff c3d3fbff 00000000 00000000 00000000 00000000 00000000
[   18.283975] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   18.283978] CPU: L2 Cache: 128K (64 bytes/line)
[   18.283981] CPU: After all inits, caps: 078bfbff c3d3fbff 00000000 00000410 00000000 00000000 00000000
[   18.283991] Compat vDSO mapped to ffffe000.
[   18.283995] Remapping vsyscall page to ffffe000
[   18.284005] Checking 'hlt' instruction... OK.
[   18.299895] SMP alternatives: switching to UP code
[   18.300125] Freeing SMP alternatives: 11k freed
[   18.300374] Early unpacking initramfs... done
[   18.657455] ACPI: Core revision 20060707
[   18.660169] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   18.663316] CPU0: AMD Sempron(tm) Processor 2600+ stepping 00
[   18.663340] Total of 1 processors activated (3203.46 BogoMIPS).
[   18.663841] ENABLING IO-APIC IRQs
[   18.664159] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=0 pin2=0
[   18.811788] Brought up 1 CPUs
[   18.812052] Booting paravirtualized kernel on bare hardware
[   18.812154] Time: 19:48:08  Date: 04/31/107
[   18.812191] NET: Registered protocol family 16
[   18.812296] EISA bus registered
[   18.812300] ACPI: bus type pci registered
[   18.817751] PCI: PCI BIOS revision 2.10 entry at 0xfb830, last bus=1
[   18.817753] PCI: Using configuration type 1
[   18.817755] Setting up standard PCI resources
[   18.828567] ACPI: Interpreter enabled
[   18.828572] ACPI: Using IOAPIC for interrupt routing
[   18.829125] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   18.829130] PCI: Probing PCI hardware (bus 00)
[   18.830185] Boot video device is 0000:01:00.0
[   18.830229] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   18.912758] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12)
[   18.913154] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 *11 12)
[   18.913551] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 11 12) *5
[   18.913922] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   18.914272] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   18.914611] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   18.914946] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   18.915280] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   18.915900] ACPI: PCI Interrupt Link [ALKA] (IRQs *20)
[   18.916497] ACPI: PCI Interrupt Link [ALKB] (IRQs *21)
[   18.916916] ACPI: PCI Interrupt Link [ALKC] (IRQs *22)
[   18.917424] ACPI: PCI Interrupt Link [ALKD] (IRQs *23)
[   18.920818] Linux Plug and Play Support v0.97 (c) Adam Belay
[   18.920836] pnp: PnP ACPI init
[   18.926834] pnp: PnP ACPI: found 14 devices
[   18.926840] PnPBIOS: Disabled by ACPI PNP
[   18.926903] PCI: Using ACPI for IRQ routing
[   18.926907] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   18.956233] NET: Registered protocol family 8
[   18.956235] NET: Registered protocol family 20
[   18.956745] pnp: 00:02: ioport range 0x4000-0x407f could not be reserved
[   18.956749] pnp: 00:02: ioport range 0x5000-0x500f has been reserved
[   18.957029] PCI: Bridge: 0000:00:01.0
[   18.957031]   IO window: disabled.
[   18.957036]   MEM window: e8000000-e9ffffff
[   18.957040]   PREFETCH window: e0000000-e7ffffff
[   18.957056] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   18.957094] NET: Registered protocol family 2
[   18.995812] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   18.996027] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   18.997420] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   18.998134] TCP: Hash tables configured (established 131072 bind 65536)
[   18.998139] TCP reno registered
[   19.007875] checking if image is initramfs... it is
[   19.717990] Freeing initrd memory: 6987k freed
[   19.718437] audit: initializing netlink socket (disabled)
[   19.718451] audit(1180640888.608:1): initialized
[   19.718585] VFS: Disk quotas dquot_6.5.1
[   19.718609] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   19.718664] io scheduler noop registered
[   19.718666] io scheduler anticipatory registered
[   19.718669] io scheduler deadline registered
[   19.718683] io scheduler cfq registered (default)
[   19.719027] isapnp: Scanning for PnP cards...
[   20.072924] isapnp: No Plug & Play device found
[   20.107947] Real Time Clock Driver v1.12ac
[   20.107992] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   20.108098] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   20.108341] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   20.109015] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   20.109318] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   20.109603] mice: PS/2 mouse device common for all mice
[   20.110136] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   20.110399] input: Macintosh mouse button emulation as /class/input/input0
[   20.110432] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   20.110436] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   20.110706] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   20.111003] serio: i8042 KBD port at 0x60,0x64 irq 1
[   20.111008] serio: i8042 AUX port at 0x60,0x64 irq 12
[   20.111129] EISA: Probing bus 0 at eisa.0
[   20.111149] Cannot allocate resource for EISA slot 4
[   20.111151] Cannot allocate resource for EISA slot 5
[   20.111164] EISA: Detected 0 cards.
[   20.141302] TCP cubic registered
[   20.141315] NET: Registered protocol family 1
[   20.141341] Using IPI No-Shortcut mode
[   20.141433] ACPI: (supports S0 S1 S4 S5)
[   20.141478]   Magic number: 7:128:851
[   20.141557]   hash matches device ptyv3
[   20.141917] Freeing unused kernel memory: 328k freed
[   20.143666] Time: tsc clocksource has been installed.
[   20.158429] input: AT Translated Set 2 keyboard as /class/input/input1
[   21.414824] Capability LSM initialized
[   21.460994] ACPI: Thermal Zone [THRM] (40 C)
[   22.095738] SCSI subsystem initialized
[   22.100795] libata version 2.20 loaded.
[   22.103884] sata_via 0000:00:0f.0: version 2.1
[   22.104224] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[   22.104233] ACPI: PCI Interrupt 0000:00:0f.0[B] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 16
[   22.104251] sata_via 0000:00:0f.0: routed to hard irq line 11
[   22.104312] ata1: SATA max UDMA/133 cmd 0x0001b400 ctl 0x0001b802 bmdma 0x0001c400 irq 16
[   22.104339] ata2: SATA max UDMA/133 cmd 0x0001bc00 ctl 0x0001c002 bmdma 0x0001c408 irq 16
[   22.104355] scsi0 : sata_via
[   22.134170] usbcore: registered new interface driver usbfs
[   22.134194] usbcore: registered new interface driver hub
[   22.134216] usbcore: registered new device driver usb
[   22.206490] USB Universal Host Controller Interface driver v3.0
[   22.233358] via-rhine.c:v1.10-LK1.4.2 Sept-11-2006 Written by Donald Becker
[   22.311358] ata1: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   22.322011] ATA: abnormal status 0x7F on port 0x0001b407
[   22.322038] scsi1 : sata_via
[   22.356985] Floppy drive(s): fd0 is 1.44M
[   22.393219] FDC 0 is a post-1991 82077
[   22.527317] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   22.537970] ATA: abnormal status 0x7F on port 0x0001bc07
[   22.539147] VP_IDE: IDE controller at PCI slot 0000:00:0f.1
[   22.539169] ACPI: PCI Interrupt 0000:00:0f.1[A] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 16
[   22.539181] VP_IDE: chipset revision 6
[   22.539184] VP_IDE: not 100% native mode: will probe irqs later
[   22.539195] VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
[   22.539204]     ide0: BM-DMA at 0xcc00-0xcc07, BIOS settings: hda:pio, hdb:pio
[   22.539216]     ide1: BM-DMA at 0xcc08-0xcc0f, BIOS settings: hdc:pio, hdd:pio
[   22.539224] Probing IDE interface ide0...
[   22.959356] hda: WDC WD800JB-00FMA0, ATA DISK drive
[   23.631389] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   23.635844] Probing IDE interface ide1...
[   46.012618] hdc: TSSTcorpCD/DVDW TS-H552U, ATAPI CD/DVD-ROM drive
[   46.796529] hdd: HL-DT-ST GCE-8400B, ATAPI CD/DVD-ROM drive
[   46.852904] ide1 at 0x170-0x177,0x376 on irq 15
[   46.855146] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
[   46.855157] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 17
[   46.855170] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   46.855499] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   46.855536] uhci_hcd 0000:00:10.0: irq 17, io base 0x0000d000
[   46.856173] usb usb1: configuration #1 chosen from 1 choice
[   46.856502] hub 1-0:1.0: USB hub found
[   46.856518] hub 1-0:1.0: 2 ports detected
[   46.961222] ACPI: PCI Interrupt 0000:00:10.1[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 17
[   46.961236] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   46.961397] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   46.961423] uhci_hcd 0000:00:10.1: irq 17, io base 0x0000d400
[   46.962008] usb usb2: configuration #1 chosen from 1 choice
[   46.962298] hub 2-0:1.0: USB hub found
[   46.962312] hub 2-0:1.0: 2 ports detected
[   47.069181] ACPI: PCI Interrupt 0000:00:10.2[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 17
[   47.069195] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   47.069375] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   47.069401] uhci_hcd 0000:00:10.2: irq 17, io base 0x0000d800
[   47.070001] usb usb3: configuration #1 chosen from 1 choice
[   47.070298] hub 3-0:1.0: USB hub found
[   47.070313] hub 3-0:1.0: 2 ports detected
[   47.177190] ACPI: PCI Interrupt 0000:00:10.3[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 17
[   47.177204] uhci_hcd 0000:00:10.3: UHCI Host Controller
[   47.177377] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   47.177404] uhci_hcd 0000:00:10.3: irq 17, io base 0x0000dc00
[   47.177996] usb usb4: configuration #1 chosen from 1 choice
[   47.178295] hub 4-0:1.0: USB hub found
[   47.178309] hub 4-0:1.0: 2 ports detected
[   47.285687] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 23
[   47.285698] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [ALKD] -> GSI 23 (level, low) -> IRQ 18
[   47.289919] eth0: VIA Rhine II at 0x1e800, 00:11:5b:b2:67:7f, IRQ 18.
[   47.290635] eth0: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
[   47.290774] ACPI: PCI Interrupt 0000:00:10.4[C] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 17
[   47.290787] ehci_hcd 0000:00:10.4: EHCI Host Controller
[   47.291010] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[   47.291057] ehci_hcd 0000:00:10.4: irq 17, io mem 0xea422000
[   47.291064] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   47.291652] usb usb5: configuration #1 chosen from 1 choice
[   47.291951] hub 5-0:1.0: USB hub found
[   47.291966] hub 5-0:1.0: 8 ports detected
[   47.404018] hda: max request size: 128KiB
[   47.414926] hda: 156301488 sectors (80026 MB) w/8192KiB Cache, CHS=65535/16/63, UDMA(100)
[   47.417910] hda: cache flushes supported
[   47.417961]  hda: hda1 hda2 < hda5 >
[   47.466335] hdc: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[   47.466345] Uniform CD-ROM driver Revision: 3.20
[   47.480627] hdd: ATAPI 40X CD-ROM CD-R/RW drive, 8192kB Cache, UDMA(33)
[   47.691951] Attempting manual resume
[   47.691956] swsusp: Resume From Partition 3:5
[   47.691958] PM: Checking swsusp image.
[   47.692140] PM: Resume from disk failed.
[   47.740924] kjournald starting.  Commit interval 5 seconds
[   47.740938] EXT3-fs: mounted filesystem with ordered data mode.
[   56.906829] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   56.956970] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   57.008725] Linux agpgart interface v0.102 (c) Dave Jones
[   57.024550] agpgart: Detected AGP bridge 0
[   57.029235] agpgart: AGP aperture is 128M @ 0xd8000000
[   57.250060] acx: Loaded combined PCI/USB driver, firmware_ver=default
[   57.250065] acx: compiled to use 32bit I/O access. I/O timing issues might occur, such as non-working firmware upload. Report them
[   57.250127] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 17 (level, low) -> IRQ 19
[   57.250148] acx: found ACX111-based wireless network card at 0000:00:09.0, irq:19, phymem1:0xEA420000, phymem2:0xEA400000, mem1:0xf097c000, mem1_size:8192, mem2:0xf0a00000, mem2_size:131072
[   57.251142] acx: loading firmware for acx1111 chipset with radio ID 16
[   57.541731] input: PC Speaker as /class/input/input2
[   57.882862] parport: PnPBIOS parport detected.
[   57.882938] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   58.285778] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
[   58.759549] NVS_vendor_offs:01CD probe_delay:200 eof_memory:1114112
[   58.759555] CCAModes:04 Diversity:01 ShortPreOpt:01 PBCC:01 ChanAgil:00 PHY:05 Temp:01
[   58.759559] AntennaID:00 Len:02 Data:01 02 
[   58.759562] PowerLevelID:01 Len:02 Data:001E 000A 
[   58.759565] DataRatesID:02 Len:05 Data:02 04 11 22 44 
[   58.759569] DomainID:03 Len:06 Data:41 20 30 31 32 40 
[   58.759574] ProductID:04 Len:09 Data:TI ACX100
[   58.759576] ManufacturerID:05 Len:07 Data:TI Test
[   58.819076] acx: === chipset TNETW1130, radio type 0x16 (Radia), form factor 0x01 ((mini-)PCI / CardBus), EEPROM version 0x05: uploaded firmware 'Rev 1.2.1.34' ===
[   58.819218] acx v0.3.36: net device wlan0, driver compiled against wireless extensions 21 and Linux 2.6.20-15-generic
[   58.819278] usbcore: registered new interface driver acx_usb
[   58.822409] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[   58.822421] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 20
[   58.822562] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   59.529086] fuse init (API version 7.8)
[   59.551840] lp0: using parport0 (interrupt-driven).
[   59.587526] Adding 2265124k swap on /dev/disk/by-uuid/9e3d4abf-fe11-487f-a6a9-8af134198f6d.  Priority:-1 extents:1 across:2265124k
[   59.707025] EXT3 FS on hda1, internal journal
[   61.248109] NET: Registered protocol family 17
[   64.085012] Using specific hotkey driver
[   64.167710] No dock devices found.
[   64.231012] input: Power Button (FF) as /class/input/input4
[   64.235684] ACPI: Power Button (FF) [PWRF]
[   64.268140] input: Power Button (CM) as /class/input/input5
[   64.272779] ACPI: Power Button (CM) [PWRB]
[   64.294096] ibm_acpi: ec object not found
[   64.419377] pcc_acpi: loading...
[   64.623023] powernow-k8: Power state transitions not supported
[   64.654683] ACPI Exception (acpi_processor-0235): AE_NOT_FOUND, Evaluating _PSS [20060707]
[   69.515424] eth0: link down
[   70.792498] ppdev: user-space parallel port driver
[   71.387413] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   71.387419] apm: overridden by ACPI.
[   71.582683] Bluetooth: Core ver 2.11
[   71.582749] NET: Registered protocol family 31
[   71.582752] Bluetooth: HCI device and connection manager initialized
[   71.582756] Bluetooth: HCI socket layer initialized
[   71.627676] Bluetooth: L2CAP ver 2.8
[   71.627681] Bluetooth: L2CAP socket layer initialized
[   71.806353] Bluetooth: RFCOMM socket layer initialized
[   71.806368] Bluetooth: RFCOMM TTY layer initialized
[   71.806370] Bluetooth: RFCOMM ver 1.8
[  153.224959] NET: Registered protocol family 10
[  153.225073] lo: Disabled Privacy Extensions
[  153.225135] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  153.225137] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  471.922335] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  475.147688] eth0: link down
[  475.147775] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  496.129004] eth0: link down
[  496.129028] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  511.975532] eth0: link down
[  511.975556] ADDRCONF(NETDEV_UP): eth0: link is not ready
chris@chris-desktop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b+/g+  ESSID:""  Nickname:"acx v0.3.36"
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3  
          Retry min limit:7   RTS thr:off   
          Encryption key:off
          Power Management:off
          Link Quality=38/100  Signal level=13/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

chris@chris-desktop:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:5B:B2:67:7F  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0xe800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:300 (300.0 b)  TX bytes:300 (300.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:0F:B5:80:2B:E5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 


[/PHP]

---

### Post by steeleyuk on 2007-05-31
Unfortunately the WG311v2 does not work out of the box with WPA, theres no support for it in the ACX driver. Alternatively you can use NDIS but from my experience its not as stable as the ACX driver.

>  I cant seem to get mine to connect to any networks out of the box. Any idea what I am doing wrong?

You don't happen to have Network-Manager installed do you? I can't get the Netgear card to work with NM so I just removed it.

---

### Post by paleck on 2007-05-31
> **steeleyuk said:**
> Unfortunately the WG311v2 does not work out of the box with WPA, theres no support for it in the ACX driver. Alternatively you can use NDIS but from my experience its not as stable as the ACX driver.



You don't happen to have Network-Manager installed do you? I can't get the Netgear card to work with NM so I just removed it.

WPA support isn't a big deal to me as I will be using it on an open network. 

However, I am using Network-Manager to try and connect to the network. Maybe that is my issue and I need to just use the terminal. Can anyone point me in the direction of connecting using the terminal.

---

### Post by dlbolton on 2007-06-01
Hello,
I have removed some of the lines that don have anything to do with your wireless card ...

[   57.250060] acx: Loaded combined PCI/USB driver, firmware_ver=default
[   57.250065] acx: compiled to use 32bit I/O access. I/O timing issues might occur, such as non-working firmware upload. Report them
[   57.250148] acx: found ACX111-based wireless network card at 0000:00:09.0, irq:19, phymem1:0xEA420000, phymem2:0xEA400000, mem1:0xf097c000, mem1_size:8192, mem2:0xf0a00000, mem2_size:131072
[   57.251142] acx: loading firmware for acx1111 chipset with radio ID 16
[   58.759559] AntennaID:00 Len:02 Data:01 02 
[   58.759562] PowerLevelID:01 Len:02 Data:001E 000A 
[   58.759565] DataRatesID:02 Len:05 Data:02 04 11 22 44 
[   58.759569] DomainID:03 Len:06 Data:41 20 30 31 32 40 
[   58.759574] ProductID:04 Len:09 Data:TI ACX100
[   58.759576] ManufacturerID:05 Len:07 Data:TI Test
[   58.819076] acx: === chipset TNETW1130, radio type 0x16 (Radia), form factor 0x01 ((mini-)PCI / CardBus), EEPROM version 0x05: uploaded firmware 'Rev 1.2.1.34' ===
[   58.819218] acx v0.3.36: net device wlan0, driver compiled against wireless extensions 21 and Linux 2.6.20-15-generic
[   58.819278] usbcore: registered new interface driver acx_usb
[   69.515424] eth0: link down
[  153.225135] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  153.225137] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  471.922335] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  475.147688] eth0: link down
[  475.147775] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  496.129004] eth0: link down
[  496.129028] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  511.975532] eth0: link down
[  511.975556] ADDRCONF(NETDEV_UP): eth0: link is not ready

The link is not ready message is also what I see when I use this same command.  However, these lines do show that the firmware is getting loaded.

chris@chris-desktop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b+/g+  ESSID:""  Nickname:"acx v0.3.36"
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3  
          Retry min limit:7   RTS thr:off   
          Encryption key:off
          Power Management:off
          Link Quality=38/100  Signal level=13/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Note the line that says Access Point: Not Associated - this means it has not been given an ip address from your router.  Also, the ESSID is blank. You can use the iwconfig command to set this.  Type Man iwconfig"in a terminal window to find out how to do this (sudo iwconfig essid <key>). 

Then you will need to restart the networking.  The easiest way to do this is to use the command ¨sudo rmmod acx
Then 
¨sudo ifup wlan0¨ 

Before you do this, make sure that networkmanager is not trying to control your wireless card.  Go into the Network control applet and uncheck the box that says indicates whether network manager is to manage your card.

I only got these commands to work once, then I resorted to wicd, but you might be luckier than I was.  I´ve got a few more tricks as well, I will check back tomorrow.

Dave

---

### Post by dlbolton on 2007-06-01
Hello,

I mentioned in my last message about getting an ip address from your router. Here is the command that should do this (it comes from the wireless troubleshooting guide mentioned below)
sudo iwconfig wlan0 essid <your essid> ap <xx:xx:xx:xx:xx> key <xxx> mode <> commit

some parts of this are optional, I think. replace the xx:xx:xx:xx:xx with the mac address of your router (see the output in your prior message).

Here are a couple of other links that might help
1. list of links to ubuntu documentation and help:
[https://help.ubuntu.com/community/CategoryDocumentation](https://help.ubuntu.com/community/CategoryDocumentation)

2. Wireless Troubleshooting Guide (very helpful - discusses the commands in more detail)
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide?highlight=%28CategoryDocumentation%29](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide?highlight=%28CategoryDocumentation%29)

3. wicd website:
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

wicd appears to handle wpa, although I do not use it.  I have had great success using it.  Basically, enter your ssid then click on ¨Connect¨.  It will give you some info about the signal level and confirm you are connected to your router.

I&#314;l check back later.  Good Luck.

Dave

---

### Post by paleck on 2007-06-01
I disabled Network-Manager and things seem to be working fine. Thanks for the help.

---

