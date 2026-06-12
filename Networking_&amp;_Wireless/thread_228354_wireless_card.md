---
title: "wireless card"
date: 2006-08-03
forum: Networking &amp; Wireless
---

### Post by clericclark on 2006-08-03
i just installed ubuntu on my other computer and i dont have any internet at all. it doesnt show my pci bus at all or the wireless card in it. i can only see modem as an option in network.i cant select wireless. can anyone help me with this?

---

### Post by rattlerviper on 2006-08-03
> **clericclark said:**
> i just installed ubuntu on my other computer and i dont have any internet at all. it doesnt show my pci bus at all or the wireless card in it. i can only see modem as an option in network.i cant select wireless. can anyone help me with this?

More than willing to help, but we need some information to help you.  What kind(brand and model#) of wireless card are you using?  We need to know if it is compatible with Ubuntu or not.  If it is you may need to use ndiswrapper to "wrap" your windows driver and make it work for Linux since it would'nt appear that there is a Linux driver for it in Ubuntu.  If it is not a compatible device then all we can do is reccomend the purchase of one that is.

---

### Post by clericclark on 2006-08-03
is there a list anywhere of the supported wireless cards?

---

### Post by rattlerviper on 2006-08-03
> **clericclark said:**
> is there a list anywhere of the supported wireless cards?

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")

---

### Post by clericclark on 2006-08-03
my wireless card is supported but i still cant access the internet. i have a  Cisco Aironet CB21AG. i put the card into the card bus and it shows up under device manager, but i cant access the internet or see wireless under network.

i tried following these directions [https://help.ubuntu.com/community/WifiDocs/Device/CiscoCB21AG?highlight=%28CB21AG%29](https://help.ubuntu.com/community/WifiDocs/Device/CiscoCB21AG?highlight=%28CB21AG%29)
but i dont really know what to do with some of the stuff on there and what it says to do.

any help is appreciated. like any simpler directions to get it to work or something im doing wrong. im kinda like a little above a complete newbie at this.

---

### Post by rattlerviper on 2006-08-03
> **clericclark said:**
> my wireless card is supported but i still cant access the internet. i have a  Cisco Aironet CB21AG. i put the card into the card bus and it shows up under device manager, but i cant access the internet or see wireless under network.

i tried following these directions [https://help.ubuntu.com/community/WifiDocs/Device/CiscoCB21AG?highlight=%28CB21AG%29](https://help.ubuntu.com/community/WifiDocs/Device/CiscoCB21AG?highlight=%28CB21AG%29)
but i dont really know what to do with some of the stuff on there and what it says to do.

any help is appreciated. like any simpler directions to get it to work or something im doing wrong. im kinda like a little above a complete newbie at this.

Copy and paste the commands in the terminal...you'll find the terminal under applications then accesories in the top left corner of you desktop(if you haven't moved it). then just follow the directions closely.

Another question for you, are you using Dapper or Breezy?  The card is confirmed to work with breezy, and according to the instruction page you linked to the instructions are for 5.10 Breezy. That means it may or may not work on dapper. Wifi is funny that way.  

Worst case scenario buy one that has a Atheros chipset/driver and states that it is supported by dapper.  That should save you trying to install if you are unable to find the directions.  Dapper will just make those cards work for you.

Really wish I could be of more help, but those directions are fairly clear(clearer than I could give you).  So unless you happen to live on N.Scottsdale all I can do is point you to the right rescources.  Unfortuanantly a search for your wifi card is turning up only your post here in the forum.  Hopefully someone else will pop up who can better explain how to do what you need.

---

### Post by clericclark on 2006-08-04
wow i didnt see that it was for breezy. i have dapper 6.06 thanks for catching that. thats probably why it isnt working. im probably going to end up getting a different wireless card. but just wondering. where can i download breezy so i can try it on there anyway?

---

### Post by stormblue on 2006-08-04
If it works in Breezy, it probably is going to work in Drapper.  With that said, I'd recommend the WG511T from Negear it works out of the box and I picked it up on ebay for $23.

---

### Post by Cryonic on 2006-08-04
In my experience, this: [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)
is the better guide for wireless problems in Dapper. I have a card with Marvel chipset, the Marvel driver that comes with Dapper is faulty so I used ndiswrapper with the Win98 driver.

If you're not clear with the Guide and need step by step instructions, please say so. 
Also, I'd refrain from getting another card unless you're 100% sure it won't work, you're better off learning a solution to a problem than trying to evade it (imho).

---

### Post by rattlerviper on 2006-08-04
Cryonic, thanks for showing up to help!  I no longer had any ideas on how to make it easier.

---

### Post by rattlerviper on 2006-08-04
Also might try copying the directions off to a floppy so you can look at them on the computer you are working on.  Ok I know I am tired now, Good night ya'll.

---

### Post by clericclark on 2006-08-04
thanks for the help. im gonna take a look at the trouble shooting guide and see if that helps.

---

### Post by clericclark on 2006-08-07
question. does anyone know where i can find the driver for the cisco aironet CB21AG wireless card? i cant seem the find it and i need it.

---

### Post by bensexson on 2006-08-07
I*t is built into the kernel.  You should not have to install it.  Please post the output of dmesg.

---

### Post by clericclark on 2006-08-07
the output is kinda long but here it is.

[4294667.296000] Linux version 2.6.15-23-386 (buildd@rothera) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Tue May 23 13:49:40 UTC 2006
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[4294667.296000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000e6c00 - 0000000000100000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 00000000040fd800 (usable)
[4294667.296000]  BIOS-e820: 00000000040fd800 - 00000000040ff800 (ACPI data)
[4294667.296000]  BIOS-e820: 00000000040ff800 - 00000000040ffc00 (ACPI NVS)
[4294667.296000]  BIOS-e820: 00000000040ffc00 - 0000000010000000 (usable)
[4294667.296000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[4294667.296000] 0MB HIGHMEM available.
[4294667.296000] 256MB LOWMEM available.
[4294667.296000] On node 0 totalpages: 65536
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:0
[4294667.296000]   DMA32 zone: 0 pages, LIFO batch:0
[4294667.296000]   Normal zone: 61440 pages, LIFO batch:15
[4294667.296000]   HighMem zone: 0 pages, LIFO batch:0
[4294667.296000] DMI 2.1 present.
[4294667.296000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f6bc0
[4294667.296000] ACPI: RSDT (v001 PTLTD    RSDT   0x00000001 PTL  0x01000000) @ 0x040fdbcb
[4294667.296000] ACPI: FADT (v001 DELL   KUBLAI   0x20000208 PTL  0x000f4240) @ 0x040ff78c
[4294667.296000] ACPI: DSDT (v001  Intel  S2440BX 0x00000001 MSFT 0x01000004) @ 0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0x8008
[4294667.296000] Allocating PCI resources starting at 20000000 (gap: 10000000:eff80000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hda1 ro quiet splash
[4294667.296000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[4294667.296000] mapped APIC to ffffd000 (01201000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[4294667.296000] Detected 798.443 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294671.354000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)[4294671.355000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[4294671.384000] Memory: 249012k/262144k available (1976k kernel code, 12592k reserved, 606k data, 288k init, 0k highmem)
[4294671.384000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294671.444000] Calibrating delay using timer specific routine.. 1597.07 BogoMIPS (lpj=798537)
[4294671.444000] Security Framework v1.0.0 initialized
[4294671.444000] SELinux:  Disabled at boot.
[4294671.444000] Mount-cache hash table entries: 512
[4294671.444000] CPU: After generic identify, caps: 0387f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[4294671.444000] CPU: After vendor identify, caps: 0387f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[4294671.444000] CPU: L1 I cache: 16K, L1 D cache: 16K
[4294671.444000] CPU: L2 cache: 256K
[4294671.444000] CPU serial number disabled.
[4294671.444000] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[4294671.444000] mtrr: v2.0 (20020519)
[4294671.444000] CPU: Intel Pentium III (Coppermine) stepping 03
[4294671.444000] Enabling fast FPU save and restore... done.
[4294671.444000] Enabling unmasked SIMD FPU exception support... done.
[4294671.444000] Checking 'hlt' instruction... OK.
[4294671.448000] checking if image is initramfs... it is
[4294673.435000] Freeing initrd memory: 6837k freed
[4294673.474000] ACPI: Looking for DSDT ... not found!
[4294673.476000] ACPI: setting ELCR to 0200 (from 0a00)
[4294673.478000] NET: Registered protocol family 16
[4294673.478000] EISA bus registered
[4294673.478000] ACPI: bus type pci registered
[4294673.478000] PCI: PCI BIOS revision 2.10 entry at 0xfd993, last bus=1
[4294673.478000] PCI: Using configuration type 1
[4294673.479000] ACPI: Subsystem revision 20051216
[4294673.482000] ACPI: Interpreter enabled
[4294673.482000] ACPI: Using PIC for interrupt routing
[4294673.482000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294673.482000] PCI: Probing PCI hardware (bus 00)
[4294673.482000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[4294673.488000] PCI quirk: region 8000-803f claimed by PIIX4 ACPI
[4294673.488000] PCI quirk: region 7000-700f claimed by PIIX4 SMB
[4294673.488000] Boot video device is 0000:01:00.0
[4294673.488000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294673.490000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[4294673.491000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[4294673.491000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[4294673.492000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 *9 10 11 12)
[4294673.492000] ACPI: Power Resource [PFAN] (on)
[4294673.496000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294673.496000] pnp: PnP ACPI init
[4294673.502000] pnp: PnP ACPI: found 11 devices
[4294673.503000] PnPBIOS: Disabled by ACPI PNP
[4294673.503000] PCI: Using ACPI for IRQ routing
[4294673.503000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294673.504000] pnp: 00:00: ioport range 0x7000-0x700f has been reserved
[4294673.504000] pnp: 00:00: ioport range 0x8000-0x803f could not be reserved
[4294673.505000] PCI: Failed to allocate mem resource #6:10000@fe000000 for 0000:01:00.0
[4294673.505000] PCI: Bridge: 0000:00:01.0
[4294673.505000]   IO window: disabled.
[4294673.505000]   MEM window: f5000000-f5ffffff
[4294673.505000]   PREFETCH window: fc000000-fdffffff
[4294673.505000] PCI: Bus 2, cardbus bridge: 0000:00:0e.0
[4294673.505000]   IO window: 00001400-000014ff
[4294673.505000]   IO window: 00001800-000018ff
[4294673.505000]   PREFETCH window: 20000000-21ffffff
[4294673.505000]   MEM window: 22000000-23ffffff
[4294673.505000] PCI: Bus 6, cardbus bridge: 0000:00:0e.1
[4294673.505000]   IO window: 00001c00-00001cff
[4294673.505000]   IO window: 00002000-000020ff
[4294673.505000]   PREFETCH window: 24000000-25ffffff
[4294673.505000]   MEM window: 26000000-27ffffff
[4294673.505000] PCI: Enabling device 0000:00:0e.0 (0000 -> 0003)
[4294673.505000] **** SET: Misaligned resource pointer: cf6887e2 Type 07 Len 0
[4294673.505000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[4294673.505000] PCI: setting IRQ 11 as level-triggered
[4294673.506000] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[4294673.506000] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[4294673.506000] PCI: Enabling device 0000:00:0e.1 (0000 -> 0003)
[4294673.506000] ACPI: PCI Interrupt 0000:00:0e.1[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[4294673.506000] PCI: Setting latency timer of device 0000:00:0e.1 to 64
[4294673.507000] audit: initializing netlink socket (disabled)
[4294673.507000] audit(1154985509.506:1): initialized
[4294673.507000] VFS: Disk quotas dquot_6.5.1
[4294673.507000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294673.507000] Initializing Cryptographic API
[4294673.507000] io scheduler noop registered
[4294673.507000] io scheduler anticipatory registered
[4294673.507000] io scheduler deadline registered
[4294673.507000] io scheduler cfq registered
[4294673.507000] Limiting direct PCI/PCI transfers.
[4294673.507000] isapnp: Scanning for PnP cards...
[4294673.866000] isapnp: No Plug & Play device found
[4294673.902000] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MICE] at 0x60,0x64 irq 1,12
[4294673.914000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294673.915000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294673.915000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[4294673.915000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294673.921000] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294673.922000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294673.923000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294673.923000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294673.923000] mice: PS/2 mouse device common for all mice
[4294673.925000] EISA: Probing bus 0 at eisa.0
[4294673.925000] Cannot allocate resource for EISA slot 1
[4294673.925000] Cannot allocate resource for EISA slot 2
[4294673.925000] Cannot allocate resource for EISA slot 7
[4294673.925000] Cannot allocate resource for EISA slot 8
[4294673.925000] EISA: Detected 0 cards.
[4294673.925000] NET: Registered protocol family 2
[4294673.935000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)[4294673.935000] TCP established hash table entries: 16384 (order: 4, 65536 bytes)
[4294673.936000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[4294673.936000] TCP: Hash tables configured (established 16384 bind 16384)
[4294673.936000] TCP reno registered
[4294673.936000] TCP bic registered
[4294673.936000] NET: Registered protocol family 1
[4294673.936000] NET: Registered protocol family 8
[4294673.936000] NET: Registered protocol family 20
[4294673.937000] Using IPI Shortcut mode
[4294673.937000] ACPI wakeup devices:
[4294673.937000] PCI0 USB0 UAR1  KBC MICE
[4294673.937000] ACPI: (supports S0 S1 S5)
[4294673.937000] Freeing unused kernel memory: 288k freed
[4294673.956000] input: AT Translated Set 2 keyboard as /class/input/input0
[4294674.073000] vga16fb: initializing
[4294674.073000] vga16fb: mapped to 0xc00a0000
[4294674.207000] Console: switching to colour frame buffer device 80x25
[4294674.207000] fb0: VGA16 VGA frame buffer device
[4294675.335000] Capability LSM initialized
[4294675.408000] ACPI: Fan [FAN1] (on)
[4294675.418000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[4294676.584000] PIIX4: IDE controller at PCI slot 0000:00:07.1
[4294676.584000] PIIX4: chipset revision 1
[4294676.584000] PIIX4: not 100% native mode: will probe irqs later
[4294676.584000]     ide0: BM-DMA at 0x1020-0x1027, BIOS settings: hda:pio, hdb:DMA
[4294676.584000]     ide1: BM-DMA at 0x1028-0x102f, BIOS settings: hdc:DMA, hdd:pio
[4294676.584000] Probing IDE interface ide0...
[4294676.848000] hda: Maxtor 52049U4, ATA DISK drive
[4294677.103000] hdb: WDC WD204BB, ATA DISK drive
[4294677.155000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294677.155000] Probing IDE interface ide1...
[4294677.827000] hdc: PHILIPS DVD+/-RW DVD8701, ATAPI CD/DVD-ROM drive
[4294678.439000] ide1 at 0x170-0x177,0x376 on irq 15
[4294678.455000] hda: max request size: 128KiB
[4294678.477000] hda: 40020624 sectors (20490 MB) w/2048KiB Cache, CHS=39703/16/63, UDMA(33)
[4294678.477000] hda: cache flushes not supported
[4294678.477000]  hda: hda1 hda2 < hda5 >
[4294678.510000] hdb: max request size: 128KiB
[4294678.534000] hdb: 39876480 sectors (20416 MB) w/2048KiB Cache, CHS=39560/16/63, UDMA(33)
[4294678.534000] hdb: cache flushes not supported
[4294678.534000]  hdb: hdb1
[4294678.542000] hdc: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[4294678.542000] Uniform CD-ROM driver Revision: 3.20
[4294679.051000] usbcore: registered new driver usbfs
[4294679.052000] usbcore: registered new driver hub
[4294679.057000] USB Universal Host Controller Interface driver v2.3
[4294679.059000] **** SET: Misaligned resource pointer: c3d333e2 Type 07 Len 0
[4294679.059000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 9
[4294679.059000] PCI: setting IRQ 9 as level-triggered
[4294679.059000] ACPI: PCI Interrupt 0000:00:07.2[D] -> Link [LNKD] -> GSI 9 (level, low) -> IRQ 9
[4294679.059000] uhci_hcd 0000:00:07.2: UHCI Host Controller
[4294679.060000] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[4294679.060000] uhci_hcd 0000:00:07.2: irq 9, io base 0x00001000
[4294679.060000] hub 1-0:1.0: USB hub found
[4294679.060000] hub 1-0:1.0: 2 ports detected
[4294679.265000] Attempting manual resume
[4294679.326000] EXT3-fs: mounted filesystem with ordered data mode.
[4294679.329000] kjournald starting.  Commit interval 5 seconds
[4294679.367000] usb 1-1: new full speed USB device using uhci_hcd and address 2[4294679.723000] usb 1-2: new full speed USB device using uhci_hcd and address 3[4294695.415000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294695.421000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294695.446000] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[4294695.446000] Yenta: CardBus bridge found at 0000:00:0e.0 [414e:454c]
[4294695.446000] Yenta: Enabling burst memory read transactions
[4294695.446000] Yenta: Using CSCINT to route CSC interrupts to PCI
[4294695.446000] Yenta: Routing CardBus interrupts to PCI
[4294695.446000] Yenta TI: socket 0000:00:0e.0, mfunc 0x00c00d02, devctl 0x62
[4294695.466000] Linux agpgart interface v0.101 (c) Dave Jones
[4294695.472000] agpgart: Detected an Intel 440BX Chipset.
[4294695.476000] agpgart: AGP aperture is 64M @ 0xf8000000
[4294695.506000] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[4294695.669000] Yenta: ISA IRQ mask 0x0000, PCI irq 11
[4294695.669000] Socket status: 30000020
[4294695.669000] ACPI: PCI Interrupt 0000:00:0e.1[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[4294695.670000] Yenta: CardBus bridge found at 0000:00:0e.1 [414e:454c]
[4294695.670000] Yenta: Using CSCINT to route CSC interrupts to PCI
[4294695.670000] Yenta: Routing CardBus interrupts to PCI
[4294695.670000] Yenta TI: socket 0000:00:0e.1, mfunc 0x00c00d02, devctl 0x62
[4294695.893000] Yenta: ISA IRQ mask 0x0000, PCI irq 11
[4294695.893000] Socket status: 30000006
[4294696.176000] input: ImExPS/2 Generic Explorer Mouse as /class/input/input1
[4294696.294000] pccard: CardBus card inserted into slot 0
[4294696.678000] Real Time Clock Driver v1.12
[4294696.807000] nvidia: module license 'NVIDIA' taints kernel.
[4294696.822000] NVRM: The NVIDIA RIVA TNT2 Model 64/Model 64 Pro GPU installed in this system is
[4294696.822000] NVRM:  supported through the NVIDIA Legacy drivers. Please
[4294696.822000] NVRM:  visit [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) for more
[4294696.822000] NVRM:  information.  The 1.0-8762 NVIDIA driver will ignore
[4294696.822000] NVRM:  this GPU.  Continuing probe...
[4294696.822000] NVRM: No NVIDIA graphics adapter found!
[4294696.922000] **** SET: Misaligned resource pointer: cbc44da2 Type 07 Len 0
[4294696.923000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[4294696.923000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[4294696.923000] NVRM: loading NVIDIA Linux x86 NVIDIA Kernel Module  1.0-7174 Tue Mar 22 06:44:39 PST 2005
[4294696.932000] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [LNKD] -> GSI 9 (level, low) -> IRQ 9
[4294696.932000] Vortex: init.... <6>parport: PnPBIOS parport detected.
[4294697.073000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[4294697.254000] done.
[4294697.297000] gameport: AU88x0 Gameport is pci0000:00:10.0/gameport0, speed 1807kHz
[4294697.342000] input: PC Speaker as /class/input/input2
[4294697.916000] ts: Compaq touchscreen protocol output
[4294698.074000] ath_hal: 0.9.14.9 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413)
[4294698.110000] SCSI subsystem initialized
[4294698.148000] Initializing USB Mass Storage driver...
[4294698.149000] scsi0 : SCSI emulation for USB Mass Storage devices
[4294698.149000] usb-storage: device found at 2
[4294698.149000] usb-storage: waiting for device to settle before scanning
[4294698.149000] scsi1 : SCSI emulation for USB Mass Storage devices
[4294698.150000] usb-storage: device found at 3
[4294698.150000] usb-storage: waiting for device to settle before scanning
[4294698.150000] usbcore: registered new driver usb-storage
[4294698.150000] USB Mass Storage support registered.
[4294698.341000] cs: IO port probe 0x100-0x3af: clean.
[4294698.343000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[4294698.344000] cs: IO port probe 0x820-0x8ff: clean.
[4294698.345000] cs: IO port probe 0xc00-0xcf7: clean.
[4294698.346000] cs: IO port probe 0xa00-0xaff: clean.
[4294698.348000] cs: IO port probe 0x100-0x3af: clean.
[4294698.350000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[4294698.351000] cs: IO port probe 0x820-0x8ff: clean.
[4294698.352000] cs: IO port probe 0xc00-0xcf7: clean.
[4294698.353000] cs: IO port probe 0xa00-0xaff: clean.
[4294698.373000] wlan: 0.8.6.0 (EXPERIMENTAL)
[4294698.431000] ath_rate_sample: 1.2
[4294698.517000] ath_pci: 0.9.6.0 (EXPERIMENTAL)
[4294698.517000] PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
[4294698.517000] ACPI: PCI Interrupt 0000:02:00.0[?] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[4294698.518000] ath_attach: unable to attach hardware: 'Hardware self-test failed' (HAL status 14)
[4294698.519000] ACPI: PCI interrupt for device 0000:02:00.0 disabled
[4294699.413000] floppy0: no floppy controllers found
[4294699.842000] lp0: using parport0 (interrupt-driven).
[4294699.974000] Adding 746980k swap on /dev/hda5.  Priority:-1 extents:1 across:746980k
[4294700.144000] EXT3 FS on hda1, internal journal
[4294700.472000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294700.472000] md: bitmap version 4.39
[4294701.173000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294701.998000] cdrom: open failed.
[4294703.155000]   Vendor: Generic   Model: STORAGE DEVICE    Rev: 1.02
[4294703.155000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4294703.156000]   Vendor: IC35L090  Model: AVV207-0          Rev: 0000
[4294703.156000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4294703.163000] usb-storage: device scan complete
[4294703.164000] usb-storage: device scan complete
[4294703.330000] Driver 'sd' needs updating - please use bus_type methods
[4294703.601000] SCSI device sda: 512000 512-byte hdwr sectors (262 MB)
[4294703.606000] sda: Write Protect is off
[4294703.606000] sda: Mode Sense: 02 00 00 00
[4294703.606000] sda: assuming drive cache: write through
[4294703.623000] SCSI device sda: 512000 512-byte hdwr sectors (262 MB)
[4294703.629000] sda: Write Protect is off
[4294703.629000] sda: Mode Sense: 02 00 00 00
[4294703.629000] sda: assuming drive cache: write through
[4294703.629000]  sda: sda1
[4294703.636000] sd 0:0:0:0: Attached scsi removable disk sda
[4294703.643000] SCSI device sdb: 156250000 512-byte hdwr sectors (80000 MB)
[4294703.643000] sdb: assuming drive cache: write through
[4294703.651000] SCSI device sdb: 156250000 512-byte hdwr sectors (80000 MB)
[4294703.651000] sdb: assuming drive cache: write through
[4294703.651000]  sdb: sdb1 sdb2 < sdb5 >
[4294703.739000] sd 1:0:0:0: Attached scsi disk sdb
[4294703.781000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[4294703.782000] sd 1:0:0:0: Attached scsi generic sg1 type 0
[4294704.641000] NET: Registered protocol family 17
[4294711.495000] ACPI: Power Button (FF) [PWRF]
[4294711.736000] ibm_acpi: ec object not found
[4294711.787000] pcc_acpi: loading...
[4294719.848000] ppdev: user-space parallel port driver
[4294720.270000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294720.270000] apm: overridden by ACPI.
[4294728.243000] Bluetooth: Core ver 2.8
[4294728.243000] NET: Registered protocol family 31
[4294728.243000] Bluetooth: HCI device and connection manager initialized
[4294728.243000] Bluetooth: HCI socket layer initialized
[4294728.328000] Bluetooth: L2CAP ver 2.8
[4294728.328000] Bluetooth: L2CAP socket layer initialized
[4294728.351000] Bluetooth: RFCOMM socket layer initialized
[4294728.351000] Bluetooth: RFCOMM TTY layer initialized
[4294728.351000] Bluetooth: RFCOMM ver 1.7
[4294879.298000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[4294879.298000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[4294879.369000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[4294879.369000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[4294885.354000] NET: Registered protocol family 10
[4294885.354000] lo: Disabled Privacy Extensions
[4294885.354000] IPv6 over IPv4 tunneling driver
[4294888.856000] vortex: IRQ fifo error
[4294889.943000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[4294891.418000] NTFS driver 2.1.25 [Flags: R/O MODULE].
[4294891.421000] NTFS-fs warning (device sdb1): parse_options(): Option iocharset is deprecated. Please use option nls=<charsetname> in the future.
[4294891.866000] NTFS volume version 3.1.
[4294892.133000] NTFS-fs warning (device sdb5): parse_options(): Option iocharset is deprecated. Please use option nls=<charsetname> in the future.
[4294892.977000] NTFS volume version 3.1.
[4294909.823000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[4294909.823000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.

---

