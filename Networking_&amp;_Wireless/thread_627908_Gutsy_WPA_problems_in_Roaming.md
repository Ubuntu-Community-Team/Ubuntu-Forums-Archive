---
title: "Gutsy WPA problems in Roaming"
date: 2007-11-30
forum: Networking &amp; Wireless
---

### Post by lvleph on 2007-11-30
I am sorry if this question has indeed been asked, but after searching and searching I give up.

I upgraded to Gutsy, and now I am having wireless problems. The first problems were when I tried to use networkmanager applet my computer would crash. I solved that by adding r8185 to blacklist. However, no it doesn't even recognize my wireless. Additionally, my sound no longer works. All of this is in Ubuntu 7.10, kernel 2.6.22-14-generic.

Now if instead I boot to Ubuntu 7.10, kernel 2.6.20-16-generic, my sound works and the wireless is recognized. In fact, it even sees my network. However, when I select my ssid there is no wpa selection for security. I assume this is because there is no WPA_Supplicant anymore. Okay, fine I can't use the roaming feature, but then I try to set it to managed and I select the WPA security, but it will not connect. 

Here is my dmesg
```
[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Sep 23 19:50:39 UTC 2007 (Ubuntu 2.6.20-16.32-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009dc00 end: 000000000009dc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009dc00 size: 0000000000002400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000ce000 size: 0000000000002000 end: 00000000000d0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000dc000 size: 0000000000004000 end: 00000000000e0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e4000 size: 000000000001c000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 0000000037d80000 end: 0000000037e80000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 0000000037e80000 size: 0000000000015000 end: 0000000037e95000 type: 3
[    0.000000] copy_e820_map() start: 0000000037e95000 size: 000000000006b000 end: 0000000037f00000 type: 4
[    0.000000] copy_e820_map() start: 0000000037f00000 size: 0000000000100000 end: 0000000038000000 type: 2
[    0.000000] copy_e820_map() start: 00000000e0000000 size: 0000000010000000 end: 00000000f0000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000010000 end: 00000000fec10000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
[    0.000000] copy_e820_map() start: 00000000fff80000 size: 0000000000080000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000ce000 - 00000000000d0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 00000000000e0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000037e80000 (usable)
[    0.000000]  BIOS-e820: 0000000037e80000 - 0000000037e95000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000037e95000 - 0000000037f00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000037f00000 - 0000000038000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 894MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f7260
[    0.000000] Entering add_active_range(0, 0, 228992) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   228992
[    0.000000]   HighMem    228992 ->   228992
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   228992
[    0.000000] On node 0 totalpages: 228992
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1757 pages used for memmap
[    0.000000]   Normal zone: 223139 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f7230
[    0.000000] ACPI: RSDT (v001 GATEWA SYSTEM   0x06040000  LTP 0x00000000) @ 0x37e8e485
[    0.000000] ACPI: FADT (v001 ATI    Bonefish 0x06040000 ATI  0x000f4240) @ 0x37e94d7c
[    0.000000] ACPI: SLIC (v001 GATEWA SYSTEM   0x06040000 *TK* 0x00000001) @ 0x37e94df0
[    0.000000] ACPI: MADT (v001 PTLTD  	 APIC   0x06040000  LTP 0x00000000) @ 0x37e94f66
[    0.000000] ACPI: MCFG (v001 PTLTD    MCFG   0x06040000  LTP 0x00000000) @ 0x37e94fc4
[    0.000000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20050228) @ 0x37e8e4bd
[    0.000000] ACPI: DSDT (v001 GATEWA SYSTEM   0x06040000 MSFT 0x03000000) @ 0x00000000
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:14 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:14 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 38000000:a8000000)
[    0.000000] Detected 1596.297 MHz processor.
[   17.338010] Built 1 zonelists.  Total pages: 227203
[   17.338018] Kernel command line: root=UUID=badeba58-bc99-45c7-9e2c-3ccf78e784c2 ro quiet splash
[   17.338349] mapped APIC to ffffd000 (fee00000)
[   17.338355] mapped IOAPIC to ffffc000 (fec00000)
[   17.338361] Enabling fast FPU save and restore... done.
[   17.338367] Enabling unmasked SIMD FPU exception support... done.
[   17.338385] Initializing CPU#0
[   17.338495] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   17.339701] Console: colour VGA+ 80x25
[   17.340754] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   17.341790] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   17.383929] Memory: 896944k/915968k available (1993k kernel code, 18472k reserved, 900k data, 328k init, 0k highmem)
[   17.383948] virtual kernel memory layout:
[   17.383950]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   17.383953]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   17.383956]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   17.383959]     lowmem  : 0xc0000000 - 0xf7e80000   ( 894 MB)
[   17.383962]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   17.383964]       .data : 0xc02f2429 - 0xc03d36d4   ( 900 kB)
[   17.383967]       .text : 0xc0100000 - 0xc02f2429   (1993 kB)
[   17.383975] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   17.462411] Calibrating delay using timer specific routine.. 3198.13 BogoMIPS (lpj=6396272)
[   17.462484] Security Framework v1.0.0 initialized
[   17.462496] SELinux:  Disabled at boot.
[   17.462526] Mount-cache hash table entries: 512
[   17.462750] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c189 00000000 00000000
[   17.462767] monitor/mwait feature present.
[   17.462771] using mwait in idle threads.
[   17.462779] CPU: L1 I cache: 32K, L1 D cache: 32K
[   17.462784] CPU: L2 cache: 1024K
[   17.462789] CPU: Physical Processor ID: 0
[   17.462793] CPU: Processor Core ID: 0
[   17.462797] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00002940 0000c189 00000000 00000000
[   17.462815] Compat vDSO mapped to ffffe000.
[   17.462822] Remapping vsyscall page to ffffe000
[   17.462844] Checking 'hlt' instruction... OK.
[   17.478589] SMP alternatives: switching to UP code
[   17.479248] Early unpacking initramfs... done
[   18.169516] ACPI: Core revision 20060707
[   18.211299] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   18.625051] CPU0: Intel Genuine Intel(R) CPU           T2060  @ 1.60GHz stepping 0c
[   18.625087] SMP alternatives: switching to SMP code
[   18.625272] Booting processor 1/1 eip 3000
[   18.635715] Initializing CPU#1
[   18.713442] Calibrating delay using timer specific routine.. 3192.74 BogoMIPS (lpj=6385496)
[   18.713455] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c189 00000000 00000000
[   18.713466] monitor/mwait feature present.
[   18.713472] CPU: L1 I cache: 32K, L1 D cache: 32K
[   18.713477] CPU: L2 cache: 1024K
[   18.713481] CPU: Physical Processor ID: 0
[   18.713484] CPU: Processor Core ID: 1
[   18.713488] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00002940 0000c189 00000000 00000000
[   18.714115] CPU1: Intel Genuine Intel(R) CPU           T2060  @ 1.60GHz stepping 0c
[   18.714158] Total of 2 processors activated (6390.88 BogoMIPS).
[   18.714351] ENABLING IO-APIC IRQs
[   18.714604] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[   18.861344] checking TSC synchronization across 2 CPUs: passed.
[    0.003992] Brought up 2 CPUs
[    0.207104] migration_cost=137
[    0.207621] Booting paravirtualized kernel on bare hardware
[    0.207753] Time: 16:56:48  Date: 10/30/107
[    0.207818] NET: Registered protocol family 16
[    0.207976] EISA bus registered
[    0.207984] ACPI: bus type pci registered
[    0.249633] PCI: PCI BIOS revision 2.10 entry at 0xfd5c4, last bus=10
[    0.249638] PCI: Using configuration type 1
[    0.249642] Setting up standard PCI resources
[    0.265880] ACPI: Interpreter enabled
[    0.265886] ACPI: Using IOAPIC for interrupt routing
[    0.267449] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.267458] PCI: Probing PCI hardware (bus 00)
[    0.269835] Boot video device is 0000:01:05.0
[    0.270547] PCI: Transparent bridge - 0000:00:14.4
[    0.270630] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.275517] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]
[    0.275988] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB5_._PRT]
[    0.280383] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[    0.280894] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[    0.281401] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[    0.281904] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[    0.282413] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[    0.282918] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[    0.283426] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[    0.283940] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[    0.284450] ACPI: PCI Interrupt Link [LNKU] (IRQs 3 4 5 7) *0, disabled.
[    0.285545] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.286087] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.286916] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.286934] pnp: PnP ACPI init
[    0.291846] pnp: PnP ACPI: found 10 devices
[    0.291854] PnPBIOS: Disabled by ACPI PNP
[    0.291954] PCI: Using ACPI for IRQ routing
[    0.291959] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.314914] NET: Registered protocol family 8
[    0.314919] NET: Registered protocol family 20
[    0.315332] pnp: 00:08: ioport range 0x1080-0x1080 has been reserved
[    0.315339] pnp: 00:08: ioport range 0x200-0x20f has been reserved
[    0.315345] pnp: 00:08: ioport range 0x220-0x22f has been reserved
[    0.315351] pnp: 00:08: ioport range 0x40b-0x40b has been reserved
[    0.315933] PCI: Bridge: 0000:00:01.0
[    0.315939]   IO window: 9000-9fff
[    0.315947]   MEM window: c0000000-c00fffff
[    0.315954]   PREFETCH window: d0000000-dfffffff
[    0.315961] PCI: Bridge: 0000:00:04.0
[    0.315966]   IO window: a000-afff
[    0.315973]   MEM window: c0100000-c01fffff
[    0.315979]   PREFETCH window: disabled.
[    0.315985] PCI: Bridge: 0000:00:05.0
[    0.315990]   IO window: 6000-7fff
[    0.315998]   MEM window: b0000000-b1ffffff
[    0.316004]   PREFETCH window: b2000000-b3ffffff
[    0.316011] PCI: Bridge: 0000:00:14.4
[    0.316020]   IO window: b000-bfff
[    0.316031]   MEM window: f0200000-f02fffff
[    0.316040]   PREFETCH window: f0300000-f03fffff
[    0.316076] PCI: Setting latency timer of device 0000:00:04.0 to 64
[    0.316093] PCI: Setting latency timer of device 0000:00:05.0 to 64
[    0.316160] NET: Registered protocol family 2
[    0.351843] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.352132] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.353767] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.354793] TCP: Hash tables configured (established 131072 bind 65536)
[    0.354800] TCP reno registered
[    0.364010] checking if image is initramfs... it is
[    1.745865] Freeing initrd memory: 6772k freed
[    1.747136] audit: initializing netlink socket (disabled)
[    1.747166] audit(1196441809.948:1): initialized
[    1.747469] VFS: Disk quotas dquot_6.5.1
[    1.747509] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.747601] io scheduler noop registered
[    1.747607] io scheduler anticipatory registered
[    1.747612] io scheduler deadline registered
[    1.747636] io scheduler cfq registered (default)
[    1.747961] PCI: Setting latency timer of device 0000:00:04.0 to 64
[    1.748019] assign_interrupt_mode Found MSI capability
[    1.748025] Allocate Port Service[0000:00:04.0:pcie00]
[    1.748099] Allocate Port Service[0000:00:04.0:pcie02]
[    1.748275] PCI: Setting latency timer of device 0000:00:05.0 to 64
[    1.748331] assign_interrupt_mode Found MSI capability
[    1.748337] Allocate Port Service[0000:00:05.0:pcie00]
[    1.748407] Allocate Port Service[0000:00:05.0:pcie02]
[    1.748688] isapnp: Scanning for PnP cards...
[    2.105800] isapnp: No Plug & Play device found
[    2.156912] Real Time Clock Driver v1.12ac
[    2.157031] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    2.158355] mice: PS/2 mouse device common for all mice
[    2.159518] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    2.159809] input: Macintosh mouse button emulation as /class/input/input0
[    2.159882] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    2.159890] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    2.160312] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    2.163767] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.163775] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.163922] EISA: Probing bus 0 at eisa.0
[    2.163938] Cannot allocate resource for EISA slot 1
[    2.163969] Cannot allocate resource for EISA slot 6
[    2.163974] Cannot allocate resource for EISA slot 7
[    2.163978] Cannot allocate resource for EISA slot 8
[    2.163983] EISA: Detected 0 cards.
[    2.191470] input: AT Translated Set 2 keyboard as /class/input/input1
[    2.194144] TCP cubic registered
[    2.194164] NET: Registered protocol family 1
[    2.194209] Starting balanced_irq
[    2.194228] Using IPI No-Shortcut mode
[    2.194281] Time: tsc clocksource has been installed.
[    2.194405] ACPI: (supports S0 S3 S4 S5)
[    2.194502]   Magic number: 15:872:945
[    2.194540]   hash matches device ttya0
[    2.194749]   hash matches device tty2
[    2.195132] Freeing unused kernel memory: 328k freed
[    3.597046] Capability LSM initialized
[    3.669097] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Ist] [20060707]
[    3.670184] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Cst] [20060707]
[    3.670580] ACPI: Processor [CPU0] (supports 8 throttling states)
[    3.671490] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Ist] [20060707]
[    3.671850] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Cst] [20060707]
[    3.672276] ACPI: Processor [CPU1] (supports 8 throttling states)
[    3.677151] ACPI: Thermal Zone [THRM] (69 C)
[    4.325366] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[    4.325404] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
[    4.325425] ATIIXP: chipset revision 128
[    4.325430] ATIIXP: not 100% native mode: will probe irqs later
[    4.325446]     ide0: BM-DMA at 0x8410-0x8417, BIOS settings: hda:DMA, hdb:DMA
[    4.325470]     ide1: BM-DMA at 0x8418-0x841f, BIOS settings: hdc:pio, hdd:pio
[    4.325487] Probing IDE interface ide0...
[    4.426643] usbcore: registered new interface driver usbfs
[    4.427169] usbcore: registered new interface driver hub
[    4.427679] usbcore: registered new device driver usb
[    4.429975] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.693012] hda: HTS421210H9AT00, ATA DISK drive
[    5.476448] hdb: HL-DT-ST DVDRAM GSA-T10N, ATAPI CD/DVD-ROM drive
[    5.533177] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    5.553891] Probing IDE interface ide1...
[    6.119624] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 17
[    6.119652] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    6.120084] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[    6.120117] ohci_hcd 0000:00:13.0: irq 17, io mem 0xc0504000
[    6.181129] usb usb1: configuration #1 chosen from 1 choice
[    6.181402] hub 1-0:1.0: USB hub found
[    6.181424] hub 1-0:1.0: 4 ports detected
[    6.285015] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 17
[    6.285042] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    6.285278] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[    6.285306] ohci_hcd 0000:00:13.1: irq 17, io mem 0xc0505000
[    6.344822] usb usb2: configuration #1 chosen from 1 choice
[    6.345094] hub 2-0:1.0: USB hub found
[    6.345114] hub 2-0:1.0: 4 ports detected
[    6.448942] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 17
[    6.448970] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    6.449215] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[    6.449284] ehci_hcd 0000:00:13.2: irq 17, io mem 0xc0506000
[    6.449301] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    6.453875] usb usb3: configuration #1 chosen from 1 choice
[    6.454170] hub 3-0:1.0: USB hub found
[    6.454190] hub 3-0:1.0: 8 ports detected
[    6.569450] SCSI subsystem initialized
[    6.580921] libata version 2.20 loaded.
[    6.601148] hda: max request size: 512KiB
[    6.602654] hda: 195371568 sectors (100030 MB) w/7528KiB Cache, CHS=16383/255/63, UDMA(100)
[    6.603232] hda: cache flushes supported
[    6.603303]  hda: hda1 hda2 hda3
[    6.661328] hdb: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[    6.661346] Uniform CD-ROM driver Revision: 3.20
[    7.155242] Attempting manual resume
[    7.155250] swsusp: Resume From Partition 3:3
[    7.155253] PM: Checking swsusp image.
[    7.177287] PM: Resume from disk failed.
[    7.243191] kjournald starting.  Commit interval 5 seconds
[    7.243204] EXT3-fs: mounted filesystem with ordered data mode.
[   23.399471] Linux agpgart interface v0.102 (c) Dave Jones
[   23.443313] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   23.473181] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   24.187781] input: PC Speaker as /class/input/input2
[   24.223628] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   24.223653] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   24.223697] sky2 0000:02:00.0: v1.13 addr 0xc0100000 irq 16 Yukon-FE (0xb7) rev 1
[   24.223905] sky2 eth0: addr 00:03:25:3f:b1:e6
[   24.307113] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   24.813106] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x23aeb3, caps: 0xa04713/0x10008
[   24.854401] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   25.275055] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 16
[   25.433429] ALSA /home/erich/Desktop/alsa-driver-1.0.15rc1/pci/hda/../../alsa-kernel/pci/hda/patch_si3054.c:238: si3054: cannot initialize. EXT MID = 0000
[   26.519229] fuse init (API version 7.8)
[   26.597240] lp: driver loaded but no devices found
[   26.680789] ndiswrapper version 1.38 loaded (preempt=no,smp=yes)
[   26.754136] ndiswrapper: driver net8185 (Realtek,02/01/2007,5.1097.0201.2007) loaded
[   26.754522] ACPI: PCI Interrupt 0000:08:09.0[A] -> GSI 22 (level, low) -> IRQ 18
[   27.029905] ndiswrapper: using IRQ 18
[   27.995726] wlan0: ethernet device 00:c0:a8:d0:e4:e0 using NDIS driver: net8185, version: 0x50449, NDIS version: 0x500, vendor: 'Realtek RTL8185 Wireless LAN (Mini-)PCI NIC                                     ', 10EC:8185.5.conf
[   27.996253] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   27.996873] usbcore: registered new interface driver ndiswrapper
[   28.085656] Adding 514072k swap on /dev/hda3.  Priority:-1 extents:1 across:514072k
[   28.646045] EXT3 FS on hda2, internal journal
```

```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:39:B5:C9:8A   
          Bit Rate=1 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:32/100  Signal level:-75 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

I don't have a clue why it says linksys in the ESSID. It certainly is not connected to any wireless as far as I have been able to tell. Unless that wireless cannot connect to the internet.

First I would like to get the wireless working in 2.6.20-16, then I can worry about the rest later.

EDIT:
```
iwlist wlan0 scanning
wlan0     Scan completed :
          Cell 01 - Address: 00:13:10:A9:31:0E
                    ESSID:"Foster"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:100/100  Signal level:-30 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Extra:bcn_int=50
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:18:01:EE:31:9F
                    ESSID:"IQ8K2"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:25/100  Signal level:-80 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:18:39:7B:CC:14
                    ESSID:"linksys"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:75/100  Signal level:-48 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
          Cell 04 - Address: 00:18:39:B5:C9:8A
                    ESSID:"linksys"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:32/100  Signal level:-75 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 05 - Address: 00:18:01:EF:A2:43
                    ESSID:"E4XR2"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:32/100  Signal level:-75 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
```

---

### Post by lvleph on 2007-11-30
Okay, got soe more weirdness.

Decided to switch back to roaming. Told it to connect to the linksys, since it did have a password. I was able to connect to it, but not the internet. To be sure I was connected I went to the router access point. It was there. So I told it to disconnect by selecting my ssid. This time it allowed me to enter my WPA passkey. However, it then said I had a 0% signla (I am literally sitting next to it). Then it went to 100%, but I was not able to access the router through its access point. It then dropped back to 0% and asked for my pass key again. It just keeps doing that. At least, it asks for the key now. lol

EDIT: Here is what was logged:
```
Nov 30 17:56:51 erich-ubuntu NetworkManager: <debug> [1196463411.715138] nm_device_802_11_wireless_get_activation_ap(): Forcing AP 'Foster' 
Nov 30 17:56:51 erich-ubuntu NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/wlan0 / Foster 
Nov 30 17:56:51 erich-ubuntu NetworkManager: <info>  Deactivating device wlan0. 
Nov 30 17:56:51 erich-ubuntu NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan0: Invalid argument 
Nov 30 17:56:51 erich-ubuntu NetworkManager: <info>  Device wlan0 activation scheduled... 
Nov 30 17:56:51 erich-ubuntu NetworkManager: <info>  Deactivating device eth0. 
Nov 30 17:56:51 erich-ubuntu dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 6779
Nov 30 17:56:51 erich-ubuntu dhclient: killed old client process, removed PID file
Nov 30 17:56:51 erich-ubuntu dhclient: DHCPRELEASE on eth0 to 192.168.15.1 port 67
Nov 30 17:56:51 erich-ubuntu avahi-daemon[5101]: Withdrawing address record for 192.168.15.100 on eth0.
Nov 30 17:56:51 erich-ubuntu avahi-daemon[5101]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.15.100.
Nov 30 17:56:51 erich-ubuntu avahi-daemon[5101]: Interface eth0.IPv4 no longer relevant for mDNS.
Nov 30 17:56:52 erich-ubuntu NetworkManager: <info>  Activation (wlan0) started... 
Nov 30 17:56:52 erich-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Nov 30 17:56:52 erich-ubuntu avahi-daemon[5101]: Withdrawing address record for fe80::203:25ff:fe3f:b1e6 on eth0.
Nov 30 17:56:52 erich-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Nov 30 17:56:52 erich-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Nov 30 17:56:52 erich-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Nov 30 17:56:52 erich-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Nov 30 17:56:52 erich-ubuntu NetworkManager: <info>  Activation (wlan0/wireless): access point 'Foster' is encrypted, but NO valid key exists.  New key needed. 
Nov 30 17:56:52 erich-ubuntu NetworkManager: <info>  Activation (wlan0) New wireless user key requested for network 'Foster'. 
Nov 30 17:56:52 erich-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Nov 30 17:56:59 erich-ubuntu NetworkManager: <info>  Activation (wlan0) New wireless user key for network 'Foster' received. 
Nov 30 17:56:59 erich-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Nov 30 17:56:59 erich-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Nov 30 17:56:59 erich-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Nov 30 17:56:59 erich-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Nov 30 17:56:59 erich-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Nov 30 17:56:59 erich-ubuntu NetworkManager: <info>  Activation (wlan0/wireless): access point 'Foster' is encrypted, and a key exists.  No new key needed. 
Nov 30 17:57:00 erich-ubuntu NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Nov 30 17:57:00 erich-ubuntu NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
Nov 30 17:57:00 erich-ubuntu NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD wlan0^I^Iwext^I/var/run/wpa_supplicant8^I' 
Nov 30 17:57:00 erich-ubuntu NetworkManager: <info>  SUP: response was 'OK' 
Nov 30 17:57:00 erich-ubuntu NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Nov 30 17:57:00 erich-ubuntu NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Nov 30 17:57:00 erich-ubuntu NetworkManager: <info>  SUP: response was 'OK' 
Nov 30 17:57:00 erich-ubuntu NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Nov 30 17:57:00 erich-ubuntu NetworkManager: <info>  SUP: response was '0' 
Nov 30 17:57:00 erich-ubuntu NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 466f73746572' 
Nov 30 17:57:00 erich-ubuntu NetworkManager: <info>  SUP: response was 'OK' 
Nov 30 17:57:00 erich-ubuntu NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 proto WPA' 
Nov 30 17:57:00 erich-ubuntu NetworkManager: <info>  SUP: response was 'OK' 
Nov 30 17:57:00 erich-ubuntu NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt WPA-PSK' 
Nov 30 17:57:00 erich-ubuntu NetworkManager: <info>  SUP: response was 'OK' 
Nov 30 17:57:00 erich-ubuntu NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 psk <key>' 
Nov 30 17:57:00 erich-ubuntu NetworkManager: <info>  SUP: response was 'OK' 
Nov 30 17:57:00 erich-ubuntu NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Nov 30 17:57:00 erich-ubuntu NetworkManager: <info>  SUP: response was 'OK' 
Nov 30 17:57:00 erich-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Nov 30 17:57:03 erich-ubuntu kernel: [ 3612.424122] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Nov 30 17:57:05 erich-ubuntu avahi-daemon[5101]: Registering new address record for fe80::2c0:a8ff:fed0:e4e0 on wlan0.*.
Nov 30 17:57:14 erich-ubuntu kernel: [ 3623.327771] wlan0: no IPv6 routers present
Nov 30 17:57:32 erich-ubuntu NetworkManager: <info>  Activation (wlan0/wireless): disconnected during association, asking for new key. 
Nov 30 17:57:32 erich-ubuntu NetworkManager: <info>  Activation (wlan0) New wireless user key requested for network 'Foster'. 
Nov 30 17:57:34 erich-ubuntu NetworkManager: <info>  Activation (wlan0) New wireless user key request for network 'Foster' was canceled. 
Nov 30 17:57:34 erich-ubuntu NetworkManager: <info>  Activation (wlan0) failure scheduled... 
Nov 30 17:57:34 erich-ubuntu NetworkManager: <info>  Activation (wlan0) failed for access point (Foster) 
Nov 30 17:57:34 erich-ubuntu NetworkManager: <info>  Activation (wlan0) failed. 
Nov 30 17:57:34 erich-ubuntu NetworkManager: <info>  Deactivating device wlan0. 
Nov 30 17:57:34 erich-ubuntu NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan0: Invalid argument 
Nov 30 17:57:34 erich-ubuntu NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Nov 30 17:57:34 erich-ubuntu avahi-daemon[5101]: Withdrawing address record for fe80::2c0:a8ff:fed0:e4e0 on wlan0.
```

---

### Post by lvleph on 2007-11-30
Bump?

---

### Post by kevdog on 2007-12-01
Ok so you are using the ndiswrapper driver.  Have you install the wpasupplicant package??

---

### Post by lvleph on 2007-12-01
```
sudo apt-get install wpasupplicant
Reading package lists... Done
Building dependency tree       
Reading state information... Done
wpasupplicant is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

I was pretty sure I already had it.

---

### Post by kevdog on 2007-12-01
Ok first confirm that your wireless connection works via no encryption or WEP.  Dont first jump to wep.

Second see my guide about connecting from the command line -- the guide will tell you how to connect via WPA -- try WPA(1) first since Ive had a lot of people confirm this part of the guide works.  WPA2 seems to be a little bit more variable.

---

### Post by lvleph on 2007-12-01
I connected to someone with out incription once already. The only option I have for my router (that is for wpa) is wpa(1).

**lshw -C network**
```
*-network
       description: Wireless interface
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@0000:08:09.0
       logical name: wlan0
       version: 20
       serial: 00:c0:a8:d0:e4:e0
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.38 firmware=Realtek,02/01/2007,5.1097.0201. latency=64 maxlatency=64 mingnt=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11b
```

**sudo wpa_supplicant -w -Dwext -iwlan0 -c/etc/wpa_supplicant.conf**
```
 sudo wpa_supplicant -w -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
Trying to associate with 00:13:10:a9:31:0e (SSID='Foster' freq=2412 MHz)
Authentication with 00:00:00:00:00:00 timed out.
Trying to associate with 00:13:10:a9:31:0e (SSID='Foster' freq=2412 MHz)
Authentication with 00:00:00:00:00:00 timed out.
l2_packet_receive - recvfrom: Network is down
ioctl[SIOCGIWSCAN]: Resource temporarily unavailable
Trying to associate with 00:13:10:a9:31:0e (SSID='Foster' freq=2412 MHz)
Authentication with 00:00:00:00:00:00 timed out.
Trying to associate with 00:13:10:a9:31:0e (SSID='Foster' freq=2412 MHz)
Associated with 00:13:10:a9:31:0e
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Authentication with 00:00:00:00:00:00 timed out.
ioctl[SIOCGIWSCAN]: Resource temporarily unavailable
ioctl[SIOCGIWSCAN]: Resource temporarily unavailable
ioctl[SIOCGIWSCAN]: Resource temporarily unavailable
ioctl[SIOCGIWSCAN]: Resource temporarily unavailable
ioctl[SIOCGIWSCAN]: Resource temporarily unavailable
ioctl[SIOCGIWSCAN]: Resource temporarily unavailable
ioctl[SIOCGIWSCAN]: Resource temporarily unavailable
ioctl[SIOCGIWSCAN]: Resource temporarily unavailable
ioctl[SIOCGIWSCAN]: Resource temporarily unavailable
ioctl[SIOCGIWSCAN]: Resource temporarily unavailable
ioctl[SIOCGIWSCAN]: Resource temporarily unavailable
```
and it keeps trying.

**syslog**
```
Dec  1 13:41:00 erich-ubuntu dhclient: Listening on LPF/wlan0/00:c0:a8:d0:e4:e0
Dec  1 13:41:00 erich-ubuntu dhclient: Sending on   LPF/wlan0/00:c0:a8:d0:e4:e0
Dec  1 13:41:00 erich-ubuntu dhclient: Sending on   Socket/fallback
Dec  1 13:41:04 erich-ubuntu kernel: [22297.858779] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

Thank you for you help. Hopefully this is something easy to fix.

---

### Post by lvleph on 2007-12-01
Okay, not sure what I have done different, but I am connected with my wireless right now. Weird.

---

### Post by kevdog on 2007-12-01
Weird -- I dont know what you did either!

---

### Post by lvleph on 2007-12-03
Okay, so my problems have not ended.

My wireless connects sometimes, but not always.

---

### Post by lvleph on 2007-12-07
> **lvleph said:**
> Okay, so my problems have not ended.

My wireless connects sometimes, but not always.

It seems to be an issue with 2.6.20-16 under Gutsy for some reason. 2.6.22-14 the wireless works flawlessly.

---

### Post by Leno. on 2007-12-10
I have the exact same problem, and it's annoying the hell out of me.

Any updates on how to make this work?

---

### Post by lvleph on 2007-12-10
Which kernel are you using?

---

### Post by Leno. on 2007-12-11
I am using 2.6.22-14, 64-bit though.

---

### Post by lvleph on 2007-12-11
You will probably have to start you own thread asking the question, because I don't anyone will help you inside this thread, since it was dead.

---

