---
title: "Messed my wifi up (please Help)"
date: 2007-08-17
forum: Networking &amp; Wireless
---

### Post by Ambby on 2007-08-17
Alright so i had my wifi card working fine,the thing was i had it on auto config,but it would lose connection every so often,prob because i have a password protected router,it never asked for me to put the password in,& it still worked,but it would cut of at random times,i got tired of it,so i tried to do a manual wireless config & it did not work,ever since then,my wifi card wont work,like when i first had it,before i got the wrapper program,so i try to use the wrapper program to set up the driver for my card again & the program opens up for a second & closes right away each time,so i cant get my wifi card to work anymore,no lights its totaly dead,& i dont know whats wrong,can someone help?


Thanks.

---

### Post by Jose Catre-Vandis on 2007-08-17
What is your wireless adapter?
What security are you using on your router?

---

### Post by Ambby on 2007-08-17
Its a generic card.


Realtek Semiconductor Co., Ltd.

RTL8180L 802.11b MAC

PCI


& i cant get the exact security settings,but i know its 64 bit wih numbers & letters



Mabye  messed some setting up,& now that program wont open,or something wont let it open?


If i could just get to that program & enable my drivers again it should work.

---

### Post by Jose Catre-Vandis on 2007-08-18
Can you drop the security on the router to see if you can connect without it first? Is your adapter working and detecting the network?

First off:
```
iwconfig
```
```
ifconfig
```
```
iwlist scan
```

These commands at the terminal should help you to see what is going on.

I would have thought that an RTL 8180L chipset would be in the kernel and should work out of the box, without having to use ndiswrapper or similar.

What does dmesg report?
```
dmesg
```

---

### Post by Ambby on 2007-08-26
From the terminal command you gave me i got this.


(Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e0000 size: 0000000000020000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001fed0000 end: 000000001ffd0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000001ffd0000 size: 0000000000020c00 end: 000000001fff0c00 type: 2
[    0.000000] copy_e820_map() start: 000000001fff0c00 size: 000000000000b400 end: 000000001fffc000 type: 4
[    0.000000] copy_e820_map() start: 000000001fffc000 size: 0000000000004000 end: 0000000020000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001ffd0000 (usable)
[    0.000000]  BIOS-e820: 000000001ffd0000 - 000000001fff0c00 (reserved)
[    0.000000]  BIOS-e820: 000000001fff0c00 - 000000001fffc000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001fffc000 - 0000000020000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 131024) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   131024
[    0.000000]   HighMem    131024 ->   131024
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   131024
[    0.000000] On node 0 totalpages: 131024
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 991 pages used for memmap
[    0.000000]   Normal zone: 125937 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 COMPAQ                                ) @ 0x000f69f0
[    0.000000] ACPI: RSDT (v001 COMPAQ CPQ00B7  0x18040320 CPQ  0x00000001) @ 0x1fff0c84
[    0.000000] ACPI: FADT (v002 COMPAQ CPQ00B7  0x00000002 CPQ  0x00000001) @ 0x1fff0c00
[    0.000000] ACPI: SSDT (v001 COMPAQ  CPQGysr 0x00001001 MSFT 0x0100000e) @ 0x1fff6c59
[    0.000000] ACPI: DSDT (v001 COMPAQ EVON610C 0x00010000 MSFT 0x0100000e) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:e0000000)
[    0.000000] Detected 1196.190 MHz processor.
[   22.738829] Built 1 zonelists.  Total pages: 130001
[   22.738837] Kernel command line: root=UUID=811addc0-b452-4dc9-befe-9f7354de81a8 ro quiet splash
[   22.739199] Local APIC disabled by BIOS -- you can enable it with "lapic"
[   22.739213] mapped APIC to ffffd000 (0140a000)
[   22.739220] Enabling fast FPU save and restore... done.
[   22.739227] Enabling unmasked SIMD FPU exception support... done.
[   22.739249] Initializing CPU#0
[   22.739370] PID hash table entries: 2048 (order: 11, 8192 bytes)
[   22.741047] Console: colour VGA+ 80x25
[   22.741552] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   22.742036] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   22.763397] Memory: 508352k/524096k available (1992k kernel code, 15180k reserved, 893k data, 328k init, 0k highmem)
[   22.763418] virtual kernel memory layout:
[   22.763420]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   22.763422]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   22.763425]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   22.763427]     lowmem  : 0xc0000000 - 0xdffd0000   ( 511 MB)
[   22.763429]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[   22.763432]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[   22.763434]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[   22.763441] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   22.843371] Calibrating delay using timer specific routine.. 2395.39 BogoMIPS (lpj=4790796)
[   22.843459] Security Framework v1.0.0 initialized
[   22.843473] SELinux:  Disabled at boot.
[   22.843509] Mount-cache hash table entries: 512
[   22.843805] CPU: After generic identify, caps: bfebf9ff 00000000 00000000 00000000 00004400 00000000 00000000
[   22.843832] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   22.843838] CPU: L2 cache: 512K
[   22.843842] CPU: Hyper-Threading is disabled
[   22.843847] CPU: After all inits, caps: bfebf9ff 00000000 00000000 00003080 00004400 00000000 00000000
[   22.843870] Compat vDSO mapped to ffffe000.
[   22.843877] Remapping vsyscall page to ffffe000
[   22.843902] Checking 'hlt' instruction... OK.
[   22.859567] SMP alternatives: switching to UP code
[   22.859899] Freeing SMP alternatives: 11k freed
[   22.860311] Early unpacking initramfs... done
[   23.526771] ACPI: Core revision 20060707
[   23.528158] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   23.533791] ACPI: setting ELCR to 0200 (from 0c00)
[   23.567555] CPU0: Intel Mobile Intel(R) Pentium(R) 4 - M CPU 2.00GHz stepping 07
[   23.567571] SMP motherboard not detected.
[   23.567575] Local APIC not detected. Using dummy APIC emulation.
[   23.567649] Brought up 1 CPUs
[   23.568165] Booting paravirtualized kernel on bare hardware
[   23.568276] Time: 16:46:54  Date: 07/26/107
[   23.568329] NET: Registered protocol family 16
[   23.568501] EISA bus registered
[   23.568511] ACPI: bus type pci registered
[   23.570925] PCI: PCI BIOS revision 2.10 entry at 0xf03a2, last bus=4
[   23.570929] PCI: Using configuration type 1
[   23.570933] Setting up standard PCI resources
[   23.594339] ACPI: Interpreter enabled
[   23.594348] ACPI: Using PIC for interrupt routing
[   23.595027] ACPI: PCI Root Bridge [C045] (0000:00)
[   23.595038] PCI: Probing PCI hardware (bus 00)
[   23.595080] ACPI: Assume root bridge [\_SB_.C045] bus is 0
[   23.602190] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[   23.602199] PCI quirk: region 1100-113f claimed by ICH4 GPIO
[   23.602525] Boot video device is 0000:01:00.0
[   23.602877] PCI: Firmware left 0000:02:08.0 e100 interrupts enabled, disabling
[   23.603252] PCI: Transparent bridge - 0000:00:1e.0
[   23.603500] PCI: Bus #04 (-#07) is hidden behind transparent bridge #02 (-#04) (try 'pci=assign-busses')
[   23.603506] Please report the result to linux-kernel to fix this permanently
[   23.603545] ACPI: PCI Interrupt Routing Table [\_SB_.C045._PRT]
[   23.615833] ACPI: PCI Interrupt Routing Table [\_SB_.C045.C046._PRT]
[   23.616393] ACPI: PCI Interrupt Routing Table [\_SB_.C045.C058._PRT]
[   23.621532] ACPI: Power Resource [C15D] (on)
[   23.625268] ACPI: Power Resource [C171] (on)
[   23.628362] ACPI: Power Resource [C175] (on)
[   23.631418] ACPI: Power Resource [C178] (on)
[   23.632162] ACPI: Power Resource [C181] (on)
[   23.635067] ACPI: PCI Interrupt Link [C0C0] (IRQs 5 10 *11)
[   23.636038] ACPI: PCI Interrupt Link [C0C1] (IRQs 5 10 *11)
[   23.636961] ACPI: PCI Interrupt Link [C0C2] (IRQs 5 10 11) *0, disabled.
[   23.637893] ACPI: PCI Interrupt Link [C0C3] (IRQs 5 10 *11)
[   23.638826] ACPI: PCI Interrupt Link [C0C4] (IRQs 5 *10 11)
[   23.639505] ACPI: Blank IRQ resource
[   23.639510] ACPI: Resource is not an IRQ entry
[   23.639805] ACPI: PCI Interrupt Link [C0C5] (IRQs) *0, disabled.
[   23.640487] ACPI: Blank IRQ resource
[   23.640492] ACPI: Resource is not an IRQ entry
[   23.640780] ACPI: PCI Interrupt Link [C0C6] (IRQs) *0, disabled.
[   23.641454] ACPI: Blank IRQ resource
[   23.641459] ACPI: Resource is not an IRQ entry
[   23.641745] ACPI: PCI Interrupt Link [C0C7] (IRQs) *0, disabled.
[   23.644199] ACPI: Power Resource [C1EB] (off)
[   23.644473] ACPI: Power Resource [C1EC] (off)
[   23.644749] ACPI: Power Resource [C1ED] (off)
[   23.645197] Linux Plug and Play Support v0.97 (c) Adam Belay
[   23.645220] pnp: PnP ACPI init
[   23.676583] pnp: PnP ACPI: found 14 devices
[   23.676592] PnPBIOS: Disabled by ACPI PNP
[   23.676699] PCI: Using ACPI for IRQ routing
[   23.676706] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   23.738709] NET: Registered protocol family 8
[   23.738714] NET: Registered protocol family 20
[   23.739791] pnp: 00:0c: ioport range 0x140-0x14f has been reserved
[   23.739804] pnp: 00:0d: ioport range 0x4d0-0x4d1 has been reserved
[   23.739811] pnp: 00:0d: ioport range 0x1000-0x107f could not be reserved
[   23.739817] pnp: 00:0d: ioport range 0x1100-0x113f has been reserved
[   23.739822] pnp: 00:0d: ioport range 0x1200-0x121f has been reserved
[   23.740487] PCI: Bridge: 0000:00:01.0
[   23.740495]   IO window: 3000-3fff
[   23.740503]   MEM window: 40400000-404fffff
[   23.740510]   PREFETCH window: 48000000-4fffffff
[   23.740531] PCI: Bus 3, cardbus bridge: 0000:02:06.0
[   23.740536]   IO window: 00002800-000028ff
[   23.740543]   IO window: 00002c00-00002cff
[   23.740552]   PREFETCH window: 30000000-33ffffff
[   23.740560]   MEM window: 3c000000-3fffffff
[   23.740568] PCI: Bus 4, cardbus bridge: 0000:02:06.1
[   23.740572]   IO window: 00001400-000014ff
[   23.740580]   IO window: 00001800-000018ff
[   23.740588]   PREFETCH window: 34000000-37ffffff
[   23.740596]   MEM window: 44000000-47ffffff
[   23.740604] PCI: Bridge: 0000:00:1e.0
[   23.740610]   IO window: 2000-2fff
[   23.740619]   MEM window: 40000000-403fffff
[   23.740628]   PREFETCH window: 30000000-37ffffff
[   23.740657] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   23.741393] ACPI: PCI Interrupt Link [C0C3] enabled at IRQ 11
[   23.741400] PCI: setting IRQ 11 as level-triggered
[   23.741406] ACPI: PCI Interrupt 0000:02:06.0[A] -> Link [C0C3] -> GSI 11 (level, low) -> IRQ 11
[   23.741438] ACPI: PCI Interrupt 0000:02:06.1[A] -> Link [C0C3] -> GSI 11 (level, low) -> IRQ 11
[   23.741493] NET: Registered protocol family 2
[   23.779450] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   23.779625] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   23.779762] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[   23.779832] TCP: Hash tables configured (established 16384 bind 8192)
[   23.779837] TCP reno registered
[   23.791568] checking if image is initramfs... it is
[   25.089296] Freeing initrd memory: 6990k freed
[   25.089992] audit: initializing netlink socket (disabled)
[   25.090018] audit(1188146815.504:1): initialized
[   25.090301] VFS: Disk quotas dquot_6.5.1
[   25.090336] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   25.090431] io scheduler noop registered
[   25.090438] io scheduler anticipatory registered
[   25.090443] io scheduler deadline registered
[   25.090462] io scheduler cfq registered (default)
[   25.090935] isapnp: Scanning for PnP cards...
[   25.444961] isapnp: No Plug & Play device found
[   25.502140] Real Time Clock Driver v1.12ac
[   25.502268] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   25.502451] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   25.502928] serial8250: ttyS2 at I/O 0x3e8 (irq = 4) is a 16550A
[   25.503781] 00:02: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   25.504571] mice: PS/2 mouse device common for all mice
[   25.505820] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   25.506142] input: Macintosh mouse button emulation as /class/input/input0
[   25.506223] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   25.506232] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   25.506582] PNP: PS/2 Controller [PNP0303:C17E,PNP0f13:C17F] at 0x60,0x64 irq 1,12
[   25.508298] i8042.c: Detected active multiplexing controller, rev 1.1.
[   25.509032] serio: i8042 KBD port at 0x60,0x64 irq 1
[   25.509040] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   25.509046] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   25.509052] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   25.509058] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   25.509309] EISA: Probing bus 0 at eisa.0
[   25.509323] Cannot allocate resource for EISA slot 1
[   25.509329] Cannot allocate resource for EISA slot 2
[   25.509333] Cannot allocate resource for EISA slot 3
[   25.509338] Cannot allocate resource for EISA slot 4
[   25.509357] EISA: Detected 0 cards.
[   25.539555] TCP cubic registered
[   25.539568] NET: Registered protocol family 1
[   25.539613] Using IPI No-Shortcut mode
[   25.539747] ACPI: (supports S0 S3 S4 S5)
[   25.539836]   Magic number: 3:898:793
[   25.540063]   hash matches device ptyr1
[   25.540619] Freeing unused kernel memory: 328k freed
[   25.543204] Time: tsc clocksource has been installed.
[   25.552132] input: AT Translated Set 2 keyboard as /class/input/input1
[   27.174923] Capability LSM initialized
[   27.608983] ACPI: Transitioning device [C1EE] to D3
[   27.608991] ACPI: Transitioning device [C1EE] to D3
[   27.608999] ACPI: Fan [C1EE] (off)
[   27.609393] ACPI: Transitioning device [C1EF] to D3
[   27.609398] ACPI: Transitioning device [C1EF] to D3
[   27.609405] ACPI: Fan [C1EF] (off)
[   27.609799] ACPI: Transitioning device [C1F0] to D3
[   27.609804] ACPI: Transitioning device [C1F0] to D3
[   27.609811] ACPI: Fan [C1F0] (off)
[   27.619412] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   27.619427] ACPI: Processor [C000] (supports 8 throttling states)
[   27.631721] ACPI: Thermal Zone [TZ1] (45 C)
[   27.633583] ACPI: Thermal Zone [C1EA] (45 C)
[   28.796345] SCSI subsystem initialized
[   28.807691] libata version 2.20 loaded.
[   28.815873] ata_piix 0000:00:1f.1: version 2.10ac1
[   28.815900] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[   28.816691] ACPI: PCI Interrupt Link [C0C2] enabled at IRQ 10
[   28.816697] PCI: setting IRQ 10 as level-triggered
[   28.816704] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [C0C2] -> GSI 10 (level, low) -> IRQ 10
[   28.816739] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   28.816838] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00014440 irq 14
[   28.816894] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00014448 irq 15
[   28.816938] scsi0 : ata_piix
[   28.944063] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k2-NAPI
[   28.944070] e100: Copyright(c) 1999-2006 Intel Corporation
[   28.974617] usbcore: registered new interface driver usbfs
[   28.974662] usbcore: registered new interface driver hub
[   28.974712] usbcore: registered new device driver usb
[   28.979434] ata1.00: ata_hpa_resize 1: sectors = 78140160, hpa_sectors = 78140160
[   28.979443] ata1.00: ATA-5: HITACHI_DK23EA-40, 00K3A0A2, max UDMA/100
[   28.979449] ata1.00: 78140160 sectors, multi 16: LBA 
[   28.987389] ata1.00: ata_hpa_resize 1: sectors = 78140160, hpa_sectors = 78140160
[   28.987397] ata1.00: configured for UDMA/100
[   28.987417] scsi1 : ata_piix
[   29.124933] Floppy drive(s): fd0 is 1.44M
[   29.153510] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   29.223577] FDC 0 is a post-1991 82077
[   29.307304] ata2.00: ATAPI, max MWDMA2
[    6.648000] Time: acpi_pm clocksource has been installed.
[    6.704000] ata2.00: configured for MWDMA2
[    6.704000] scsi 0:0:0:0: Direct-Access     ATA      HITACHI_DK23EA-4 00K3 PQ: 0 ANSI: 5
[    6.704000] scsi 1:0:0:0: CD-ROM            TOSHIBA  DVD-ROM SD-R2102 1A16 PQ: 0 ANSI: 5
[    6.708000] ACPI: PCI Interrupt Link [C0C4] enabled at IRQ 10
[    6.708000] ACPI: PCI Interrupt 0000:02:08.0[A] -> Link [C0C4] -> GSI 10 (level, low) -> IRQ 10
[    6.804000] e100: eth0: e100_probe: addr 0x40100000, irq 10, MAC addr 00:08:02:94:C6:2C
[    6.804000] ACPI: PCI Interrupt 0000:02:0e.2[C] -> Link [C0C4] -> GSI 10 (level, low) -> IRQ 10
[    6.804000] ehci_hcd 0000:02:0e.2: EHCI Host Controller
[    6.804000] ehci_hcd 0000:02:0e.2: new USB bus registered, assigned bus number 1
[    6.828000] ehci_hcd 0000:02:0e.2: irq 10, io mem 0x40300000
[    6.828000] ehci_hcd 0000:02:0e.2: USB 2.0 started, EHCI 0.95, driver 10 Dec 2004
[    6.828000] usb usb1: configuration #1 chosen from 1 choice
[    6.828000] hub 1-0:1.0: USB hub found
[    6.828000] hub 1-0:1.0: 5 ports detected
[    6.840000] SCSI device sda: 78140160 512-byte hdwr sectors (40008 MB)
[    6.840000] sda: Write Protect is off
[    6.840000] sda: Mode Sense: 00 3a 00 00
[    6.840000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.840000] SCSI device sda: 78140160 512-byte hdwr sectors (40008 MB)
[    6.840000] sda: Write Protect is off
[    6.840000] sda: Mode Sense: 00 3a 00 00
[    6.840000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.840000]  sda: sda1 sda2
[    6.880000] sd 0:0:0:0: Attached scsi disk sda
[    6.888000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    6.888000] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    6.900000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    6.900000] Uniform CD-ROM driver Revision: 3.20
[    6.900000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    6.932000] ACPI: PCI Interrupt 0000:02:0e.0[A] -> Link [C0C4] -> GSI 10 (level, low) -> IRQ 10
[    6.932000] ohci_hcd 0000:02:0e.0: OHCI Host Controller
[    6.932000] ohci_hcd 0000:02:0e.0: new USB bus registered, assigned bus number 2
[    6.932000] ohci_hcd 0000:02:0e.0: irq 10, io mem 0x40180000
[    7.492000] usb usb2: configuration #1 chosen from 1 choice
[    7.496000] hub 2-0:1.0: USB hub found
[    7.496000] hub 2-0:1.0: 3 ports detected
[    7.744000] Attempting manual resume
[    7.744000] swsusp: Resume From Partition 8:2
[    7.744000] PM: Checking swsusp image.
[    7.744000] PM: Resume from disk failed.
[    7.772000] EXT3-fs: INFO: recovery required on readonly filesystem.
[    7.772000] EXT3-fs: write access will be enabled during recovery.
[    8.012000] ACPI: PCI Interrupt 0000:02:0e.1[B] -> Link [C0C4] -> GSI 10 (level, low) -> IRQ 10
[    8.012000] ohci_hcd 0000:02:0e.1: OHCI Host Controller
[    8.012000] ohci_hcd 0000:02:0e.1: new USB bus registered, assigned bus number 3
[    8.012000] ohci_hcd 0000:02:0e.1: irq 10, io mem 0x40200000
[    8.572000] usb usb3: configuration #1 chosen from 1 choice
[    8.576000] hub 3-0:1.0: USB hub found
[    8.576000] hub 3-0:1.0: 2 ports detected
[    9.324000] kjournald starting.  Commit interval 5 seconds
[    9.324000] EXT3-fs: recovery complete.
[    9.324000] EXT3-fs: mounted filesystem with ordered data mode.
[   21.668000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[   23.108000] NET: Registered protocol family 17
[   24.240000] iTCO_vendor_support: vendor-support=0
[   24.244000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   24.244000] iTCO_wdt: Found a ICH3-M TCO device (Version=1, TCOBASE=0x1060)
[   24.244000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   24.264000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   24.268000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   24.300000] Linux agpgart interface v0.102 (c) Dave Jones
[   24.304000] agpgart: Detected an Intel i845 Chipset.
[   24.320000] agpgart: AGP aperture is 256M @ 0x60000000
[   24.332000] intel_rng: FWH not detected
[   26.004000] Yenta: CardBus bridge found at 0000:02:06.0 [0e11:00b7]
[   26.004000] Yenta: Enabling burst memory read transactions
[   26.004000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   26.004000] Yenta: Routing CardBus interrupts to PCI
[   26.004000] Yenta TI: socket 0000:02:06.0, mfunc 0x01001002, devctl 0x64
[   26.024000] input: PC Speaker as /class/input/input2
[   26.236000] Yenta: ISA IRQ mask 0x00b8, PCI irq 11
[   26.236000] Socket status: 30000020
[   26.236000] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[   26.236000] cs: IO port probe 0x2000-0x2fff: clean.
[   26.236000] pcmcia: parent PCI bridge Memory window: 0x40000000 - 0x403fffff
[   26.236000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x37ffffff
[   26.236000] Yenta: CardBus bridge found at 0000:02:06.1 [0e11:00b7]
[   26.236000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   26.236000] Yenta: Routing CardBus interrupts to PCI
[   26.236000] Yenta TI: socket 0000:02:06.1, mfunc 0x01001002, devctl 0x64
[   26.268000] irda_init()
[   26.268000] NET: Registered protocol family 23
[   26.328000] parport: PnPBIOS parport detected.
[   26.328000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   26.368000] Synaptics Touchpad, model: 1, fw: 5.8, id: 0x9b48b1, caps: 0x884793/0x0
[   26.368000] serio: Synaptics pass-through port at isa0060/serio4/input0
[   26.416000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   26.468000] Yenta: ISA IRQ mask 0x0038, PCI irq 11
[   26.468000] Socket status: 30000006
[   26.468000] Yenta: Raising subordinate bus# of parent bus (#02) from #04 to #07
[   26.468000] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[   26.468000] cs: IO port probe 0x2000-0x2fff: clean.
[   26.468000] pcmcia: parent PCI bridge Memory window: 0x40000000 - 0x403fffff
[   26.468000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x37ffffff
[   26.588000] found SMC SuperIO Chip (devid=0x0e rev=01 base=0x002e): LPC47N252
[   26.588000] smsc_ircc_present: can't get sir_base of 0x3e8
[   26.872000] pccard: CardBus card inserted into slot 0
[   26.944000] ACPI: PCI Interrupt Link [C0C1] enabled at IRQ 11
[   26.944000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [C0C1] -> GSI 11 (level, low) -> IRQ 11
[   26.944000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   27.260000] intel8x0_measure_ac97_clock: measured 54448 usecs
[   27.260000] intel8x0: clocking to 48000
[   27.864000] cs: IO port probe 0x100-0x3af: excluding 0x100-0x107
[   27.864000] cs: IO port probe 0x3e0-0x4ff: clean.
[   27.864000] cs: IO port probe 0x820-0x8ff: clean.
[   27.864000] cs: IO port probe 0xc00-0xcf7: clean.
[   27.864000] cs: IO port probe 0xa00-0xaff: clean.
[   27.904000] cs: IO port probe 0x100-0x3af: excluding 0x100-0x107
[   27.904000] cs: IO port probe 0x3e0-0x4ff: clean.
[   27.908000] cs: IO port probe 0x820-0x8ff: clean.
[   27.908000] cs: IO port probe 0xc00-0xcf7: clean.
[   27.908000] cs: IO port probe 0xa00-0xaff: clean.
[   28.108000] fuse init (API version 7.8)
[   28.164000] lp0: using parport0 (interrupt-driven).
[   28.228000] Adding 3486096k swap on /dev/disk/by-uuid/b0b588ba-e095-4731-829c-2269be8b59c4.  Priority:-1 extents:1 across:3486096k
[   28.420000] EXT3 FS on sda1, internal journal
[   28.672000] NET: Registered protocol family 10
[   28.672000] lo: Disabled Privacy Extensions
[   33.352000] IBM TrackPoint firmware: 0x0b, buttons: 2/3
[   33.696000] input: TPPS/2 IBM TrackPoint as /class/input/input4
[   34.200000] ibm_acpi: ec object not found
[   34.304000] ACPI: AC Adapter [C19A] (off-line)
[   34.344000] No dock devices found.
[   34.412000] input: Power Button (FF) as /class/input/input5
[   34.412000] ACPI: Power Button (FF) [PWRF]
[   34.432000] input: Sleep Button (CM) as /class/input/input6
[   34.432000] ACPI: Sleep Button (CM) [C19B]
[   34.444000] input: Lid Switch as /class/input/input7
[   34.444000] ACPI: Lid Switch [C19C]
[   34.604000] Using specific hotkey driver
[   34.660000] ACPI: Video Device [C0CE] (multi-head: yes  rom: no  post: no)
[   34.768000] ACPI: Battery Slot [C198] (battery present)
[   34.768000] ACPI: Battery Slot [C199] (battery absent)
[   34.952000] pcc_acpi: loading...
[   39.332000] eth0: no IPv6 routers present
[   43.724000] [drm] Initialized drm 1.1.0 20060810
[   43.740000] ACPI: PCI Interrupt Link [C0C0] enabled at IRQ 11
[   43.740000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [C0C0] -> GSI 11 (level, low) -> IRQ 11
[   43.744000] [drm] Initialized radeon 1.25.0 20060524 on minor 0
[   44.916000] ppdev: user-space parallel port driver
[   44.976000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   44.976000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[   44.976000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
[   45.388000] [drm] Setting GART location based on new memory map
[   45.388000] [drm] writeback test succeeded in 2 usecs
[   46.156000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   46.156000] apm: overridden by ACPI.
[   46.572000] Bluetooth: Core ver 2.11
[   46.576000] NET: Registered protocol family 31
[   46.576000] Bluetooth: HCI device and connection manager initialized
[   46.576000] Bluetooth: HCI socket layer initialized
[   46.664000] Bluetooth: L2CAP ver 2.8
[   46.664000] Bluetooth: L2CAP socket layer initialized
[   46.820000] Bluetooth: RFCOMM socket layer initialized
[   46.820000] Bluetooth: RFCOMM TTY layer initialized
[   46.820000] Bluetooth: RFCOMM ver 1.8
[   59.432000] eth0: no IPv6 routers present
[  321.668000] e100: eth0: e100_watchdog: link down
[  323.668000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[  323.668000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  344.592000] eth0: no IPv6 routers present
[  397.108000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  397.112000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[  398.052000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  421.160000] eth0: no IPv6 routers present
[  471.112000] e100: eth0: e100_watchdog: link down
[  477.112000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[  477.112000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  479.112000] e100: eth0: e100_watchdog: link down
[  481.112000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[  481.112000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  495.448000] eth0: no IPv6 routers present
[  753.112000] e100: eth0: e100_watchdog: link down
[  775.112000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[  775.112000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  785.892000] eth0: no IPv6 routers present
[ 1000.484000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1000.488000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[ 1000.488000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1074.488000] e100: eth0: e100_watchdog: link down
[ 1088.488000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[ 1088.488000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1105.984000] eth0: no IPv6 routers present



Im connected directly to my modem now,but i need my wifi card to work,i dont think its a matter of security,my modem card wont even go on,the lights dont flash on,im pretty sure my laptop is not detecting it right now,or mabye some conflict between settings is canceling it out? it was fine at first,& i started having alot of net slow down & total loss of conection,i thought it was my card,so i went to try & change the settings  myself & as i did so one setting took affect & then my card did not even show up at all,so when i go to look at the connection i can choose from i only see wired network as an option,in the end i found out my modem was fried,so the card was fine & i screwed it up for no reason & now im trying to get it back somehow,& when i use the rapper program for the card it says the program is already installed & that i dont need to do it again,but when i launch the app,it closes itself down everytime right away,makes no sense to me o.0

---

