---
title: "yet another wirless thread"
date: 2007-08-02
forum: Networking &amp; Wireless
---

### Post by BoneSaw on 2007-08-02
okay. i know there are probably a couple hundred threads on this forum about wireless internet, but i cant seem to find the help i need.

i recently got my ubuntu pre-installed dell in the mail (had to compile alsa drivers myself to get the sound working.). so today i decide to try and install compiz fusion. well im not sure if it was compiz fusion or what, but now my wireless doesnt want to work. the lspci output says that it sees my card but the iwconfig says there are no wireless extensions. where do i go from here?

i am about to go crazy.  ](*,)

---

### Post by ev5unleash1 on 2007-08-02
Where did you get the Compiz software from. It could of been a fake file that just currpted your files. And if not make sure that this install was not related to any other installations.

You could also try reinstalling Ubuntu on the machine and not try it again. But if you have files on there look at other threads.

About your wireless, be spesify what kind it is and that the driver just decided not to work anymore.

---

### Post by noob12 on 2007-08-02
Somewhere in the process did you install a new video driver?

Can you post the output from running **dmesg**?  Look for errors; go ahead and post the whole thing if you don't really know.

---

### Post by BoneSaw on 2007-08-02
i got the compiz from trevinos repos so i know its legit.

re-installing would be a last resort cause movie my 70 gigs of music is a hassle.

the wireless card is an intel 3945ABG so im almost certain there are drivers. and it has worked in the past.

---

### Post by ev5unleash1 on 2007-08-02
Yea mine the same. But those drivers are a hassle too you may just need to manually put in your network information to connect if that is the problem. If you have enough space on your HDD download a partition mangaer and make another one big enough for your files like another EXT3 that can be usable and then put your files on there and then reinstall Ubuntu and then put them all back.

---

### Post by BoneSaw on 2007-08-02
> **noob12 said:**
> Somewhere in the process did you install a new video driver?

Can you post the output from running **dmesg**?  Look for errors; go ahead and post the whole thing if you don't really know.

no new video drivers. im on my other comp so ill get back to you on dmesg


```
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f6d3400 (usable)
[    0.000000]  BIOS-e820: 000000003f6d3400 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4007000 (reserved)
[    0.000000]  BIOS-e820: 00000000f4008000 - 00000000f400c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] 118MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 259795) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   259795
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   259795
[    0.000000] On node 0 totalpages: 259795
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 237 pages used for memmap
[    0.000000]   HighMem zone: 30182 pages, LIFO batch:7
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP (v000 DELL                                  ) @ 0x000fc1d0
[    0.000000] ACPI: RSDT (v001 DELL    M07     0x27d7060d ASL  0x00000061) @ 0x3f6d39cd
[    0.000000] ACPI: FADT (v001 DELL    M07     0x27d7060d ASL  0x00000061) @ 0x3f6d4800
[    0.000000] ACPI: HPET (v001 DELL    M07     0x00000001 ASL  0x00000061) @ 0x3f6d4f00
[    0.000000] ACPI: MADT (v001 DELL    M07     0x27d7060d ASL  0x00000047) @ 0x3f6d5000
[    0.000000] ACPI: MCFG (v016 DELL    M07     0x27d7060d ASL  0x00000061) @ 0x3f6d4fc0
[    0.000000] ACPI: SLIC (v001 DELL    M07     0x27d7060d ASL  0x00000061) @ 0x3f6d509c
[    0.000000] ACPI: BOOT (v001 DELL    M07     0x27d7060d ASL  0x00000061) @ 0x3f6d4bc0
[    0.000000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20050624) @ 0x3f6d3a0d
[    0.000000] ACPI: DSDT (v001 INT430 SYSFexxx 0x00001001 INTL 0x20050624) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:14 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:14 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:b0000000)
[    0.000000] Detected 1729.115 MHz processor.
[    8.015712] Built 1 zonelists.  Total pages: 257766
[    8.015716] Kernel command line: root=UUID=78d5c908-2192-4591-8258-0b4a755a8b9f ro quiet splash reboot=b
[    8.015876] mapped APIC to ffffd000 (fee00000)
[    8.015878] mapped IOAPIC to ffffc000 (fec00000)
[    8.015881] Enabling fast FPU save and restore... done.
[    8.015884] Enabling unmasked SIMD FPU exception support... done.
[    8.015892] Initializing CPU#0
[    8.015957] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    8.017617] Console: colour VGA+ 80x25
[    8.017927] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    8.018325] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    8.044090] Memory: 1018984k/1039180k available (1992k kernel code, 19408k reserved, 900k data, 328k init, 121676k highmem)
[    8.044100] virtual kernel memory layout:
[    8.044101]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[    8.044102]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    8.044103]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[    8.044104]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    8.044106]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[    8.044107]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[    8.044108]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[    8.044112] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    8.044268] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    8.044274] hpet0: 3 64-bit timers, 14318180 Hz
[    8.045280] Using HPET for base-timer
[    8.124238] Calibrating delay using timer specific routine.. 3461.86 BogoMIPS (lpj=6923738)
[    8.124279] Security Framework v1.0.0 initialized
[    8.124287] SELinux:  Disabled at boot.
[    8.124302] Mount-cache hash table entries: 512
[    8.124447] CPU: After generic identify, caps: bfe9fbff 00000000 00000000 00000000 0000c189 00000000 00000000
[    8.124456] monitor/mwait feature present.
[    8.124458] using mwait in idle threads.
[    8.124464] CPU: L1 I cache: 32K, L1 D cache: 32K
[    8.124467] CPU: L2 cache: 1024K
[    8.124469] CPU: Physical Processor ID: 0
[    8.124471] CPU: Processor Core ID: 0
[    8.124473] CPU: After all inits, caps: bfe9fbff 00000000 00000000 00002940 0000c189 00000000 00000000
[    8.124483] Compat vDSO mapped to ffffe000.
[    8.124487] Remapping vsyscall page to ffffe000
[    8.124500] Checking 'hlt' instruction... OK.
[    8.140347] SMP alternatives: switching to UP code
[    8.140741] Early unpacking initramfs... done
[    8.469459] ACPI: Core revision 20060707
[    8.485970] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[    8.488635] CPU0: Intel Genuine Intel(R) CPU           T2080  @ 1.73GHz stepping 0c
[    8.488656] SMP alternatives: switching to SMP code
[    8.488791] Booting processor 1/1 eip 3000
[   10.548144] Initializing CPU#1
[   10.626629] Calibrating delay using timer specific routine.. 3458.11 BogoMIPS (lpj=6916226)
[   10.626636] CPU: After generic identify, caps: bfe9fbff 00000000 00000000 00000000 0000c189 00000000 00000000
[   10.626641] monitor/mwait feature present.
[   10.626644] CPU: L1 I cache: 32K, L1 D cache: 32K
[   10.626646] CPU: L2 cache: 1024K
[   10.626649] CPU: Physical Processor ID: 0
[   10.626650] CPU: Processor Core ID: 1
[   10.626652] CPU: After all inits, caps: bfe9fbff 00000000 00000000 00002940 0000c189 00000000 00000000
[    8.580402] CPU1: Intel Genuine Intel(R) CPU           T2080  @ 1.73GHz stepping 0c
[    8.580426] Total of 2 processors activated (6919.98 BogoMIPS).
[    8.580629] ENABLING IO-APIC IRQs
[    8.580834] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    8.727983] checking TSC synchronization across 2 CPUs: 
[    0.000002] CPU#0 had -1023723 usecs TSC skew, fixed it up.
[    0.000004] CPU#1 had 1023723 usecs TSC skew, fixed it up.
[    0.004003] Brought up 2 CPUs
[    0.076428] migration_cost=57
[    0.076715] Booting paravirtualized kernel on bare hardware
[    0.076806] Time: 18:23:20  Date: 07/02/107
[    0.076835] NET: Registered protocol family 16
[    0.076925] EISA bus registered
[    0.076929] ACPI: bus type pci registered
[    0.105903] PCI: PCI BIOS revision 2.10 entry at 0xfb336, last bus=13
[    0.105906] PCI: Using configuration type 1
[    0.105908] Setting up standard PCI resources
[    0.133505] ACPI: Interpreter enabled
[    0.133510] ACPI: Using IOAPIC for interrupt routing
[    0.134452] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.134460] PCI: Probing PCI hardware (bus 00)
[    0.134659] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[    0.148284] Boot video device is 0000:00:02.0
[    0.148925] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.148930] PCI quirk: region 1080-10bf claimed by ICH6 GPIO
[    0.150053] PCI: Transparent bridge - 0000:00:1e.0
[    0.150116] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.171814] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[    0.172088] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *4
[    0.172352] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 *11)
[    0.172615] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 11) *3
[    0.172879] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.173146] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.173412] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
[    0.173682] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.175215] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    0.175493] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.175908] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.176357] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.176370] pnp: PnP ACPI init
[    0.210292] pnp: PnP ACPI: found 12 devices
[    0.210296] PnPBIOS: Disabled by ACPI PNP
[    0.210348] PCI: Using ACPI for IRQ routing
[    0.210352] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.258484] NET: Registered protocol family 8
[    0.258486] NET: Registered protocol family 20
[    0.277472] pnp: 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.277476] pnp: 00:02: ioport range 0x1000-0x1005 could not be reserved
[    0.277479] pnp: 00:02: ioport range 0x1008-0x100f could not be reserved
[    0.277484] pnp: 00:03: ioport range 0xf400-0xf4fe has been reserved
[    0.277487] pnp: 00:03: ioport range 0x1006-0x1007 has been reserved
[    0.277490] pnp: 00:03: ioport range 0x100a-0x1059 could not be reserved
[    0.277493] pnp: 00:03: ioport range 0x1060-0x107f has been reserved
[    0.277496] pnp: 00:03: ioport range 0x1080-0x10bf has been reserved
[    0.277498] pnp: 00:03: ioport range 0x10c0-0x10df has been reserved
[    0.277507] pnp: 00:08: ioport range 0xc80-0xcff could not be reserved
[    0.277510] pnp: 00:08: ioport range 0x910-0x91f has been reserved
[    0.277513] pnp: 00:08: ioport range 0x920-0x92f has been reserved
[    0.277515] pnp: 00:08: ioport range 0xcb0-0xcbf has been reserved
[    0.277518] pnp: 00:08: ioport range 0x930-0x97f has been reserved
[    0.277823] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[    0.277828] PCI: Bridge: 0000:00:1c.0
[    0.277829]   IO window: disabled.
[    0.277836]   MEM window: efd00000-efdfffff
[    0.277841]   PREFETCH window: disabled.
[    0.277847] PCI: Bridge: 0000:00:1c.3
[    0.277850]   IO window: d000-dfff
[    0.277856]   MEM window: efa00000-efcfffff
[    0.277861]   PREFETCH window: e0000000-e01fffff
[    0.277868] PCI: Bridge: 0000:00:1e.0
[    0.277869]   IO window: disabled.
[    0.277876]   MEM window: ef900000-ef9fffff
[    0.277880]   PREFETCH window: disabled.
[    0.277913] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[    0.277921] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.277946] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 17
[    0.277952] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[    0.277966] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    0.277997] NET: Registered protocol family 2
[    0.319918] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.320042] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.320767] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.321156] TCP: Hash tables configured (established 131072 bind 65536)
[    0.321160] TCP reno registered
[    0.336007] checking if image is initramfs... it is
[    0.978545] Freeing initrd memory: 6747k freed
[    0.978726] Simple Boot Flag at 0x79 set to 0x1
[    0.979207] audit: initializing netlink socket (disabled)
[    0.979223] audit(1186079000.740:1): initialized
[    0.979325] highmem bounce pool size: 64 pages
[    0.979420] VFS: Disk quotas dquot_6.5.1
[    0.979442] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.979491] io scheduler noop registered
[    0.979494] io scheduler anticipatory registered
[    0.979496] io scheduler deadline registered
[    0.979510] io scheduler cfq registered (default)
[    0.979783] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.979842] assign_interrupt_mode Found MSI capability
[    0.979845] Allocate Port Service[0000:00:1c.0:pcie00]
[    0.979880] Allocate Port Service[0000:00:1c.0:pcie02]
[    0.980010] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[    0.980069] assign_interrupt_mode Found MSI capability
[    0.980071] Allocate Port Service[0000:00:1c.3:pcie00]
[    0.980104] Allocate Port Service[0000:00:1c.3:pcie02]
[    0.980285] isapnp: Scanning for PnP cards...
[    1.334164] isapnp: No Plug & Play device found
[    1.359923] Real Time Clock Driver v1.12ac
[    1.359993] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.360686] mice: PS/2 mouse device common for all mice
[    1.361247] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.361486] input: Macintosh mouse button emulation as /class/input/input0
[    1.361522] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    1.361525] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    1.361776] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.364587] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.364593] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.364729] EISA: Probing bus 0 at eisa.0
[    1.364739] Cannot allocate resource for EISA slot 1
[    1.364771] EISA: Detected 0 cards.
[    1.369149] input: AT Translated Set 2 keyboard as /class/input/input1
[    1.394863] TCP cubic registered
[    1.394874] NET: Registered protocol family 1
[    1.394900] Starting balanced_irq
[    1.394909] Using IPI No-Shortcut mode
[    1.395013] ACPI: (supports S0 S3 S4 S5)
[    1.395060]   Magic number: 3:892:391
[    1.395357] Freeing unused kernel memory: 328k freed
[    1.395418] Time: tsc clocksource has been installed.
[    2.609495] Capability LSM initialized
[    2.649814] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Ist] [20060707]
[    2.649999] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Cst] [20060707]
[    2.650213] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    2.650218] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.650655] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Ist] [20060707]
[    2.650824] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Cst] [20060707]
[    2.651086] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    2.651091] ACPI: Processor [CPU1] (supports 8 throttling states)
[    3.236000] ACPI: Thermal Zone [THM] (46 C)
[    3.240000] Time: hpet clocksource has been installed.
[    3.600000] SCSI subsystem initialized
[    3.604000] libata version 2.20 loaded.
[    3.608000] ata_piix 0000:00:1f.2: version 2.10ac1
[    3.608000] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    3.608000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 18
[    3.608000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    3.608000] ata1: SATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001bfa0 irq 14
[    3.616000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001bfa8 irq 15
[    3.616000] scsi0 : ata_piix
[    3.636000] usbcore: registered new interface driver usbfs
[    3.636000] usbcore: registered new interface driver hub
[    3.636000] usbcore: registered new device driver usb
[    3.636000] USB Universal Host Controller Interface driver v3.0
[    3.680000] ieee1394: Initialized config rom entry `ip1394'
[    3.780000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[    3.780000] ata1.00: ATA-7: TOSHIBA MK1237GSX, DL140D, max UDMA/100
[    3.780000] ata1.00: 234441648 sectors, multi 8: LBA48 NCQ (depth 0/32)
[    3.788000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[    3.788000] ata1.00: configured for UDMA/100
[    3.788000] scsi1 : ata_piix
[    4.124000] ata2.00: ATAPI, max UDMA/33
[    4.304000] ata2.00: configured for UDMA/33
[    4.304000] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK1237GS DL14 PQ: 0 ANSI: 5
[    4.304000] scsi 1:0:0:0: CD-ROM            TSSTcorp CDRW/DVD TSL462D DE04 PQ: 0 ANSI: 5
[    4.304000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 19
[    4.304000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    4.304000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    4.304000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    4.304000] uhci_hcd 0000:00:1d.0: irq 19, io base 0x0000bf80
[    4.304000] usb usb1: configuration #1 chosen from 1 choice
[    4.304000] hub 1-0:1.0: USB hub found
[    4.304000] hub 1-0:1.0: 2 ports detected
[    4.316000] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
[    4.316000] sda: Write Protect is off
[    4.316000] sda: Mode Sense: 00 3a 00 00
[    4.316000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.316000] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
[    4.316000] sda: Write Protect is off
[    4.316000] sda: Mode Sense: 00 3a 00 00
[    4.316000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.316000]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    4.364000] sd 0:0:0:0: Attached scsi disk sda
[    4.368000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.368000] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    4.372000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    4.372000] Uniform CD-ROM driver Revision: 3.20
[    4.372000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.408000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 21 (level, low) -> IRQ 20
[    4.408000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    4.408000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    4.408000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    4.408000] uhci_hcd 0000:00:1d.1: irq 20, io base 0x0000bf60
[    4.408000] usb usb2: configuration #1 chosen from 1 choice
[    4.408000] hub 2-0:1.0: USB hub found
[    4.408000] hub 2-0:1.0: 2 ports detected
[    4.512000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 22 (level, low) -> IRQ 21
[    4.512000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    4.512000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    4.512000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    4.512000] uhci_hcd 0000:00:1d.2: irq 21, io base 0x0000bf40
[    4.512000] usb usb3: configuration #1 chosen from 1 choice
[    4.512000] hub 3-0:1.0: USB hub found
[    4.512000] hub 3-0:1.0: 2 ports detected
[    4.616000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 23 (level, low) -> IRQ 22
[    4.616000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    4.616000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    4.616000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    4.616000] uhci_hcd 0000:00:1d.3: irq 22, io base 0x0000bf20
[    4.616000] usb usb4: configuration #1 chosen from 1 choice
[    4.616000] hub 4-0:1.0: USB hub found
[    4.616000] hub 4-0:1.0: 2 ports detected
[    4.692000] Attempting manual resume
[    4.692000] swsusp: Resume From Partition 8:5
[    4.692000] PM: Checking swsusp image.
[    4.692000] PM: Resume from disk failed.
[    4.720000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 19
[    4.720000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    4.720000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.720000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    4.720000] ehci_hcd 0000:00:1d.7: debug port 1
[    4.720000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    4.720000] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xffa80000
[    4.724000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.724000] usb usb5: configuration #1 chosen from 1 choice
[    4.724000] hub 5-0:1.0: USB hub found
[    4.724000] hub 5-0:1.0: 8 ports detected
[    4.800000] kjournald starting.  Commit interval 5 seconds
[    4.800000] EXT3-fs: mounted filesystem with ordered data mode.
[    4.828000] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 19 (level, low) -> IRQ 17
[    4.880000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[ef9fd800-ef9fdfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    4.884000] b44.c:v1.01 (Jun 16, 2006)
[    4.884000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 18
[    4.888000] eth0: Broadcom 4400 10/100BaseT Ethernet 00:19:b9:72:d0:06
[    6.156000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[374fc0000257ad81]
[   15.364000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   15.368000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   15.552000] iTCO_vendor_support: vendor-support=0
[   15.568000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   15.568000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   15.568000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   15.804000] intel_rng: FWH not detected
[   15.832000] NET: Registered protocol family 17
[   15.872000] input: PC Speaker as /class/input/input2
[   15.896000] Linux agpgart interface v0.102 (c) Dave Jones
[   15.900000] agpgart: Detected an Intel 945GM Chipset.
[   15.900000] agpgart: Detected 7932K stolen memory.
[   15.916000] agpgart: AGP aperture is 256M @ 0xd0000000
[   15.984000] ieee80211_crypt: registered algorithm 'NULL'
[   15.992000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   15.992000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   16.032000] sdhci: Secure Digital Host Controller Interface driver
[   16.032000] sdhci: Copyright(c) Pierre Ossman
[   16.032000] sdhci: SDHCI controller found at 0000:03:01.1 [1180:0822] (rev 19)
[   16.032000] ACPI: PCI Interrupt 0000:03:01.1[B] -> GSI 18 (level, low) -> IRQ 23
[   16.032000] mmc0: SDHCI at 0xef9fd400 irq 23 DMA
[   16.112000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.0mp
[   16.112000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   16.124000] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   16.124000] PCI: Setting latency timer of device 0000:0b:00.0 to 64
[   16.124000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   16.408000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x180b1, caps: 0xa04713/0x200000
[   16.448000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   16.716000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 20
[   16.716000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   17.340000] lp: driver loaded but no devices found
[   17.368000] Adding 1293192k swap on /dev/disk/by-uuid/53c8c315-ad15-4101-91c3-2db46a50ffce.  Priority:-1 extents:1 across:1293192k
[   17.456000] EXT3 FS on sda6, internal journal
[   17.612000] kjournald starting.  Commit interval 5 seconds
[   17.612000] EXT3 FS on sda3, internal journal
[   17.612000] EXT3-fs: mounted filesystem with ordered data mode.
[   18.032000] ipw3945: Radio Frequency Kill Switch is On:
[   18.032000] Kill switch must be turned off for wireless networking to work.
[   30.752000] hsfengine: module license 'see LICENSE file distributed with driver' taints kernel.
[   30.812000] usbcore: registered new interface driver hsfusbcd2
[   30.920000] ACPI: AC Adapter [AC] (on-line)
[   30.976000] ACPI: Battery Slot [BAT0] (battery present)
[   30.996000] input: Lid Switch as /class/input/input4
[   30.996000] ACPI: Lid Switch [LID]
[   30.996000] input: Power Button (CM) as /class/input/input5
[   30.996000] ACPI: Power Button (CM) [PBTN]
[   30.996000] input: Sleep Button (CM) as /class/input/input6
[   30.996000] ACPI: Sleep Button (CM) [SBTN]
[   31.068000] Using specific hotkey driver
[   31.112000] No dock devices found.
[   31.160000] ibm_acpi: ec object not found
[   31.268000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   31.276000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   31.276000] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[   31.296000] pcc_acpi: loading...
[   35.652000] ppdev: user-space parallel port driver
[   36.608000] apm: BIOS not found.
[   36.896000] [drm] Initialized drm 1.1.0 20060810
[   36.896000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   36.896000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   36.964000] Bluetooth: Core ver 2.11
[   36.964000] NET: Registered protocol family 31
[   36.964000] Bluetooth: HCI device and connection manager initialized
[   36.964000] Bluetooth: HCI socket layer initialized
[   36.980000] Bluetooth: L2CAP ver 2.8
[   36.980000] Bluetooth: L2CAP socket layer initialized
[   37.180000] Bluetooth: RFCOMM socket layer initialized
[   37.180000] Bluetooth: RFCOMM TTY layer initialized
[   37.180000] Bluetooth: RFCOMM ver 1.8
[   56.812000] NET: Registered protocol family 10
[   56.812000] lo: Disabled Privacy Extensions
[   56.812000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  757.420000] b44: eth0: Link is up at 100 Mbps, full duplex.
[  757.420000] b44: eth0: Flow control is off for TX and off for RX.
[  757.424000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  761.420000] b44: eth0: Link is down.
[  763.420000] b44: eth0: Link is up at 100 Mbps, full duplex.
[  763.420000] b44: eth0: Flow control is off for TX and off for RX.
[  763.424000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  774.068000] eth0: no IPv6 routers present

```

---

### Post by noob12 on 2007-08-02
> 
[   18.032000] ipw3945: Radio Frequency Kill Switch is On:
[   18.032000] Kill switch must be turned off for wireless networking to work.


Can you check your hardware kill switch (typically a slider on the side of the laptop, sometimes a FN key) and also check any BIOS settings to make sure Wireless is enabled by default on startup?

---

### Post by BoneSaw on 2007-08-02
okay...now i feel retarded.

---

### Post by noob12 on 2007-08-02
But happy I take it?

---

### Post by BoneSaw on 2007-08-03
yes. thank you very much for the help.

---

