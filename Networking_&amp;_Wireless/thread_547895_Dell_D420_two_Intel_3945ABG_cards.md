---
title: "Dell D420 two Intel 3945ABG cards"
date: 2007-09-10
forum: Networking &amp; Wireless
---

### Post by poncenby on 2007-09-10
Hello

I have a Dell D420 with 2 Intel 3945ABG wireless cards.
I have used Windows and it can see both wireless cards, however Feisty only shows one wireless card, even though Im pretty sure Feisty does actually see the second card.

Is there something I need to do for Feisty to see the second card?
I've looked at interfaces(5) and ifup(8) but cannot get anything to work.

Another wireless-y type question: is the Intel 4965 AGN mini-PCIe card supported in Feisty?

Below is hopefully all the info you might need:

Linux ubuntu 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux

Here is my edited /etc/network/interfaces file (eth0 is the fixed ethernet interface)

```

auto lo, eth0, eth1, eth2
iface lo inet loopback
iface eth0 inet dhcp
iface eth1 inet dhcp
iface eth2 inet dhcp

```

Here is the dmesg:

```

[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000010000 end: 00000000fee10000 type: 2
[    0.000000] copy_e820_map() start: 00000000ffb00000 size: 0000000000500000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007f681400 (usable)
[    0.000000]  BIOS-e820: 000000007f681400 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4007000 (reserved)
[    0.000000]  BIOS-e820: 00000000f4008000 - 00000000f400c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] 1142MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 521857) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   521857
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   521857
[    0.000000] On node 0 totalpages: 521857
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2285 pages used for memmap
[    0.000000]   HighMem zone: 290196 pages, LIFO batch:31
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP (v000 DELL                                  ) @ 0x000fc0e0
[    0.000000] ACPI: RSDT (v001 DELL    M07     0x27d70403 ASL  0x00000061) @ 0x7f681a0e
[    0.000000] ACPI: FADT (v001 DELL    M07     0x27d70403 ASL  0x00000061) @ 0x7f682800
[    0.000000] ACPI: HPET (v001 DELL    M07     0x00000001 ASL  0x00000061) @ 0x7f682f00
[    0.000000] ACPI: MADT (v001 DELL    M07     0x27d70403 ASL  0x00000047) @ 0x7f683000
[    0.000000] ACPI: ASF! (v016 DELL    M07     0x27d70403 ASL  0x00000061) @ 0x7f682c00
[    0.000000] ACPI: MCFG (v016 DELL    M07     0x27d70403 ASL  0x00000061) @ 0x7f682fc0
[    0.000000] ACPI: SLIC (v001 DELL    M07     0x27d70403 ASL  0x00000061) @ 0x7f68309c
[    0.000000] ACPI: TCPA (v001 DELL    M07     0x27d70403 ASL  0x00000061) @ 0x7f683300
[    0.000000]   >>> ERROR: Invalid checksum
[    0.000000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20050624) @ 0x7f681a95
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
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:70000000)
[    0.000000] Detected 1197.332 MHz processor.
[    8.648109] Built 1 zonelists.  Total pages: 517780
[    8.648118] Kernel command line: root=UUID=2f41f53e-941e-44c1-bf84-d99995cd3b4d ro quiet splash
[    8.648441] mapped APIC to ffffd000 (fee00000)
[    8.648446] mapped IOAPIC to ffffc000 (fec00000)
[    8.648452] Enabling fast FPU save and restore... done.
[    8.648457] Enabling unmasked SIMD FPU exception support... done.
[    8.648470] Initializing CPU#0
[    8.648556] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    8.650629] Console: colour VGA+ 80x25
[    8.651028] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    8.651726] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    8.830746] Memory: 2058468k/2087428k available (1992k kernel code, 27644k reserved, 900k data, 328k init, 1169924k highmem)
[    8.830766] virtual kernel memory layout:
[    8.830768]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[    8.830771]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    8.830774]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[    8.830777]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    8.830780]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[    8.830782]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[    8.830785]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[    8.830793] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    8.831044] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    8.831055] hpet0: 3 64-bit timers, 14318180 Hz
[    8.832064] Using HPET for base-timer
[    8.911025] Calibrating delay using timer specific routine.. 2397.89 BogoMIPS (lpj=4795797)
[    8.911102] Security Framework v1.0.0 initialized
[    8.911115] SELinux:  Disabled at boot.
[    8.911144] Mount-cache hash table entries: 512
[    8.911376] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c1a9 00000000 00000000
[    8.911393] monitor/mwait feature present.
[    8.911397] using mwait in idle threads.
[    8.911405] CPU: L1 I cache: 32K, L1 D cache: 32K
[    8.911410] CPU: L2 cache: 2048K
[    8.911415] CPU: Physical Processor ID: 0
[    8.911419] CPU: Processor Core ID: 0
[    8.911423] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00002940 0000c1a9 00000000 00000000
[    8.911441] Compat vDSO mapped to ffffe000.
[    8.911449] Remapping vsyscall page to ffffe000
[    8.911471] Checking 'hlt' instruction... OK.
[    8.927223] SMP alternatives: switching to UP code
[    8.927907] Early unpacking initramfs... done
[    9.634159] ACPI: Core revision 20060707
[    9.651136] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[    9.656328] CPU0: Intel Genuine Intel(R) CPU           U2500  @ 1.20GHz stepping 08
[    9.656363] SMP alternatives: switching to SMP code
[    9.656549] Booting processor 1/1 eip 3000
[   11.625323] Initializing CPU#1
[   11.705854] Calibrating delay using timer specific routine.. 2394.77 BogoMIPS (lpj=4789545)
[   11.705866] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c1a9 00000000 00000000
[   11.705877] monitor/mwait feature present.
[   11.705883] CPU: L1 I cache: 32K, L1 D cache: 32K
[   11.705888] CPU: L2 cache: 2048K
[   11.705893] CPU: Physical Processor ID: 0
[   11.705896] CPU: Processor Core ID: 1
[   11.705900] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00002940 0000c1a9 00000000 00000000
[    9.751738] CPU1: Intel Genuine Intel(R) CPU           U2500  @ 1.20GHz stepping 08
[    9.751782] Total of 2 processors activated (4792.67 BogoMIPS).
[    9.751998] ENABLING IO-APIC IRQs
[    9.752249] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    9.898742] checking TSC synchronization across 2 CPUs: 
[    0.000003] CPU#0 had -978075 usecs TSC skew, fixed it up.
[    0.000008] CPU#1 had 978075 usecs TSC skew, fixed it up.
[    0.003999] Brought up 2 CPUs
[    0.177247] migration_cost=149
[    0.177747] Booting paravirtualized kernel on bare hardware
[    0.177870] Time: 19:55:08  Date: 08/10/107
[    0.177923] NET: Registered protocol family 16
[    0.178071] EISA bus registered
[    0.178079] ACPI: bus type pci registered
[    0.207452] PCI: PCI BIOS revision 2.10 entry at 0xface6, last bus=12
[    0.207458] PCI: Using configuration type 1
[    0.207461] Setting up standard PCI resources
[    0.254042] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ LMPWR] OemTableId [ DELLLOM] [20060707]
[    0.254213] ACPI: Interpreter enabled
[    0.254218] ACPI: Using IOAPIC for interrupt routing
[    0.255676] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.255693] PCI: Probing PCI hardware (bus 00)
[    0.255919] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[    0.283423] Boot video device is 0000:00:02.0
[    0.284315] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.284324] PCI quirk: region 1080-10bf claimed by ICH6 GPIO
[    0.285996] PCI: Transparent bridge - 0000:00:1e.0
[    0.286102] PCI: Bus #03 (-#06) is hidden behind transparent bridge #02 (-#03) (try 'pci=assign-busses')
[    0.286108] Please report the result to linux-kernel to fix this permanently
[    0.286202] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.372364] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[    0.372924] ACPI: PCI Interrupt Link [LNKB] (IRQs *5 7)
[    0.373480] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 11) *3
[    0.374039] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 *10 11)
[    0.374601] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.375172] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.375734] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.376312] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[    0.377926] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    0.379580] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.380115] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.380621] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PXP0._PRT]
[    0.381558] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.381579] pnp: PnP ACPI init
[    0.472100] pnp: PnP ACPI: found 13 devices
[    0.472108] PnPBIOS: Disabled by ACPI PNP
[    0.472187] PCI: Using ACPI for IRQ routing
[    0.472193] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.531989] NET: Registered protocol family 8
[    0.531994] NET: Registered protocol family 20
[    0.573690] pnp: 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.573698] pnp: 00:02: ioport range 0x1000-0x1005 could not be reserved
[    0.573705] pnp: 00:02: ioport range 0x1008-0x100f could not be reserved
[    0.573715] pnp: 00:03: ioport range 0xf400-0xf4fe has been reserved
[    0.573722] pnp: 00:03: ioport range 0x1006-0x1007 has been reserved
[    0.573728] pnp: 00:03: ioport range 0x100a-0x1059 could not be reserved
[    0.573734] pnp: 00:03: ioport range 0x1060-0x107f has been reserved
[    0.573740] pnp: 00:03: ioport range 0x1080-0x10bf has been reserved
[    0.573747] pnp: 00:03: ioport range 0x10c0-0x10df has been reserved
[    0.573766] pnp: 00:08: ioport range 0xc80-0xcaf has been reserved
[    0.573776] pnp: 00:08: ioport range 0xcc0-0xcff could not be reserved
[    0.573782] pnp: 00:08: ioport range 0x910-0x91f has been reserved
[    0.573788] pnp: 00:08: ioport range 0x920-0x92f has been reserved
[    0.573794] pnp: 00:08: ioport range 0xcbc-0xcbf has been reserved
[    0.573800] pnp: 00:08: ioport range 0x930-0x97f has been reserved
[    0.573818] pnp: 00:0c: ioport range 0xcb0-0xcbb has been reserved
[    0.574384] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[    0.574396] PCI: Bridge: 0000:00:1c.0
[    0.574400]   IO window: disabled.
[    0.574410]   MEM window: efd00000-efdfffff
[    0.574417]   PREFETCH window: disabled.
[    0.574426] PCI: Bridge: 0000:00:1c.1
[    0.574430]   IO window: disabled.
[    0.574439]   MEM window: efc00000-efcfffff
[    0.574446]   PREFETCH window: disabled.
[    0.574455] PCI: Bridge: 0000:00:1c.2
[    0.574458]   IO window: disabled.
[    0.574468]   MEM window: efb00000-efbfffff
[    0.574475]   PREFETCH window: disabled.
[    0.574495] PCI: Bus 3, cardbus bridge: 0000:02:01.0
[    0.574499]   IO window: 00002000-000020ff
[    0.574508]   IO window: 00002400-000024ff
[    0.574516]   PREFETCH window: 88000000-8bffffff
[    0.574524]   MEM window: 8c000000-8fffffff
[    0.574531] PCI: Bridge: 0000:00:1e.0
[    0.574537]   IO window: 2000-2fff
[    0.574547]   MEM window: efa00000-efafffff
[    0.574555]   PREFETCH window: 88000000-8bffffff
[    0.574600] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[    0.574612] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.574647] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
[    0.574658] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    0.574693] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[    0.574703] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    0.574724] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    0.574747] PCI: Enabling device 0000:02:01.0 (0000 -> 0003)
[    0.574755] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 19 (level, low) -> IRQ 19
[    0.574812] NET: Registered protocol family 2
[    0.615887] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.616064] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.617635] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.618445] TCP: Hash tables configured (established 131072 bind 65536)
[    0.618450] TCP reno registered
[    0.632034] checking if image is initramfs... it is
[    2.016848] Freeing initrd memory: 6769k freed
[    2.017958] audit: initializing netlink socket (disabled)
[    2.017985] audit(1189454110.168:1): initialized
[    2.018160] highmem bounce pool size: 64 pages
[    2.018322] VFS: Disk quotas dquot_6.5.1
[    2.018356] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.018440] io scheduler noop registered
[    2.018445] io scheduler anticipatory registered
[    2.018450] io scheduler deadline registered
[    2.018473] io scheduler cfq registered (default)
[    2.018862] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    2.018942] assign_interrupt_mode Found MSI capability
[    2.018949] Allocate Port Service[0000:00:1c.0:pcie00]
[    2.019016] Allocate Port Service[0000:00:1c.0:pcie02]
[    2.019211] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    2.019291] assign_interrupt_mode Found MSI capability
[    2.019296] Allocate Port Service[0000:00:1c.1:pcie00]
[    2.019374] Allocate Port Service[0000:00:1c.1:pcie02]
[    2.019567] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    2.019646] assign_interrupt_mode Found MSI capability
[    2.019651] Allocate Port Service[0000:00:1c.2:pcie00]
[    2.019713] Allocate Port Service[0000:00:1c.2:pcie02]
[    2.020017] isapnp: Scanning for PnP cards...
[    2.374410] isapnp: No Plug & Play device found
[    2.420992] Real Time Clock Driver v1.12ac
[    2.421100] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    2.422270] mice: PS/2 mouse device common for all mice
[    2.423429] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    2.423853] input: Macintosh mouse button emulation as /class/input/input0
[    2.423927] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    2.423934] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    2.424295] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.428342] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.428351] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.428578] EISA: Probing bus 0 at eisa.0
[    2.428587] EISA: Cannot allocate resource for mainboard
[    2.428593] Cannot allocate resource for EISA slot 1
[    2.428599] Cannot allocate resource for EISA slot 2
[    2.428640] EISA: Detected 0 cards.
[    2.458804] TCP cubic registered
[    2.458822] NET: Registered protocol family 1
[    2.458865] Starting balanced_irq
[    2.458877] Using IPI No-Shortcut mode
[    2.458999] input: AT Translated Set 2 keyboard as /class/input/input1
[    2.459129] ACPI: (supports S0 S3 S4 S5)
[    2.459221]   Magic number: 7:675:950
[    2.459244]   hash matches device ttya5
[    2.459384]   hash matches device tty7
[    2.459645] Freeing unused kernel memory: 328k freed
[    2.461286] Time: tsc clocksource has been installed.
[    3.909288] Capability LSM initialized
[    3.984864] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Ist] [20060707]
[    3.985266] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Cst] [20060707]
[    3.985718] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    3.985729] ACPI: Processor [CPU0] (supports 8 throttling states)
[    3.986678] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Ist] [20060707]
[    3.987053] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Cst] [20060707]
[    3.987600] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    3.987610] ACPI: Processor [CPU1] (supports 8 throttling states)
[    4.964000] Time: hpet clocksource has been installed.
[    4.964000] ACPI: Thermal Zone [THM] (25 C)
[    5.660000] usbcore: registered new interface driver usbfs
[    5.660000] usbcore: registered new interface driver hub
[    5.660000] usbcore: registered new device driver usb
[    5.660000] USB Universal Host Controller Interface driver v3.0
[    5.660000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 20
[    5.660000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    5.660000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    5.660000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    5.660000] uhci_hcd 0000:00:1d.0: irq 20, io base 0x0000bf80
[    5.660000] usb usb1: configuration #1 chosen from 1 choice
[    5.660000] hub 1-0:1.0: USB hub found
[    5.660000] hub 1-0:1.0: 2 ports detected
[    5.704000] SCSI subsystem initialized
[    5.716000] libata version 2.20 loaded.
[    5.764000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 21 (level, low) -> IRQ 21
[    5.764000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    5.764000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    5.764000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    5.764000] uhci_hcd 0000:00:1d.1: irq 21, io base 0x0000bf60
[    5.764000] usb usb2: configuration #1 chosen from 1 choice
[    5.764000] hub 2-0:1.0: USB hub found
[    5.764000] hub 2-0:1.0: 2 ports detected
[    5.852000] ieee1394: Initialized config rom entry `ip1394'
[    5.868000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 22 (level, low) -> IRQ 22
[    5.868000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    5.868000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    5.868000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    5.868000] uhci_hcd 0000:00:1d.2: irq 22, io base 0x0000bf40
[    5.868000] usb usb3: configuration #1 chosen from 1 choice
[    5.868000] hub 3-0:1.0: USB hub found
[    5.868000] hub 3-0:1.0: 2 ports detected
[    5.972000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 23 (level, low) -> IRQ 23
[    5.972000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    5.972000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    5.972000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    5.972000] uhci_hcd 0000:00:1d.3: irq 23, io base 0x0000bf20
[    5.972000] usb usb4: configuration #1 chosen from 1 choice
[    5.972000] hub 4-0:1.0: USB hub found
[    5.972000] hub 4-0:1.0: 2 ports detected
[    6.004000] usb 1-2: new full speed USB device using uhci_hcd and address 2
[    6.076000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 20
[    6.076000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    6.076000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    6.076000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    6.076000] ehci_hcd 0000:00:1d.7: debug port 1
[    6.076000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    6.076000] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xffa80000
[    6.080000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    6.080000] usb usb5: configuration #1 chosen from 1 choice
[    6.080000] hub 5-0:1.0: USB hub found
[    6.080000] hub 5-0:1.0: 8 ports detected
[    6.184000] tg3.c:v3.72 (January 8, 2007)
[    6.184000] ACPI: PCI Interrupt 0000:09:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[    6.184000] PCI: Setting latency timer of device 0000:09:00.0 to 64
[    6.204000] eth0: Tigon3 [partno(BCM5752KFBG) rev 6002 PHY(5752)] (PCI Express) 10/100/1000Base-T Ethernet 00:18:8b:be:9e:f6
[    6.204000] eth0: RXcsums[1] LinkChgREG[1] MIirq[1] ASF[0] Split[0] WireSpeed[1] TSOcap[1] 
[    6.204000] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    6.204000] ata_piix 0000:00:1f.1: version 2.10ac1
[    6.204000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 16
[    6.204000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    6.204000] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001bfa0 irq 14
[    6.204000] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001bfa8 irq 15
[    6.204000] scsi0 : ata_piix
[    6.368000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[    6.368000] ata1.00: ATA-6: TOSHIBA MK8009GAH, BQ001A, max UDMA/100
[    6.368000] ata1.00: 156301488 sectors, multi 8: LBA48 
[    6.376000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[    6.376000] ata1.00: configured for UDMA/100
[    6.376000] scsi1 : ata_piix
[    6.376000] ata2: port disabled. ignoring.
[    6.376000] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK8009GA BQ00 PQ: 0 ANSI: 5
[    6.380000] ACPI: PCI Interrupt 0000:02:01.1[B] -> GSI 17 (level, low) -> IRQ 17
[    6.432000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[    6.432000] sda: Write Protect is off
[    6.432000] sda: Mode Sense: 00 3a 00 00
[    6.432000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.432000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[    6.432000] sda: Write Protect is off
[    6.432000] sda: Mode Sense: 00 3a 00 00
[    6.432000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.432000]  sda:<6>ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[efaff800-efafffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    6.472000]  sda1 sda2 < sda5 >
[    6.500000] sd 0:0:0:0: Attached scsi disk sda
[    6.508000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    6.528000] usb 1-2: device not accepting address 2, error -71
[    6.720000] Attempting manual resume
[    6.720000] swsusp: Resume From Partition 8:5
[    6.720000] PM: Checking swsusp image.
[    6.720000] PM: Resume from disk failed.
[    6.780000] kjournald starting.  Commit interval 5 seconds
[    6.780000] EXT3-fs: mounted filesystem with ordered data mode.
[    7.012000] usb 1-2: new full speed USB device using uhci_hcd and address 4
[    7.164000] usb 1-2: configuration #1 chosen from 1 choice
[    7.164000] hub 1-2:1.0: USB hub found
[    7.168000] hub 1-2:1.0: 4 ports detected
[    7.500000] usb 1-2.3: new full speed USB device using uhci_hcd and address 5
[    7.612000] usb 1-2.3: configuration #1 chosen from 1 choice
[    7.612000] hub 1-2.3:1.0: USB hub found
[    7.616000] hub 1-2.3:1.0: 3 ports detected
[    7.712000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[324fc00000a26450]
[    7.940000] usb 1-2.4: new full speed USB device using uhci_hcd and address 6
[    8.092000] usb 1-2.4: configuration #1 chosen from 1 choice
[    8.300000] usb 1-2.3.1: new full speed USB device using uhci_hcd and address 7
[    8.436000] usb 1-2.3.1: configuration #1 chosen from 1 choice
[    8.640000] usb 1-2.3.2: new full speed USB device using uhci_hcd and address 8
[    8.756000] usb 1-2.3.2: configuration #1 chosen from 1 choice
[   25.192000] intel_rng: FWH not detected
[   25.208000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   25.212000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   25.232000] Yenta: CardBus bridge found at 0000:02:01.0 [1028:01d6]
[   25.348000] iTCO_vendor_support: vendor-support=0
[   25.360000] Yenta: ISA IRQ mask 0x0cb8, PCI irq 19
[   25.360000] Socket status: 30000006
[   25.360000] Yenta: Raising subordinate bus# of parent bus (#02) from #03 to #06
[   25.360000] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[   25.360000] cs: IO port probe 0x2000-0x2fff: clean.
[   25.360000] pcmcia: parent PCI bridge Memory window: 0xefa00000 - 0xefafffff
[   25.360000] pcmcia: parent PCI bridge Memory window: 0x88000000 - 0x8bffffff
[   25.436000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   25.672000] Linux agpgart interface v0.102 (c) Dave Jones
[   25.680000] agpgart: Detected an Intel 945GM Chipset.
[   25.680000] agpgart: Detected 7932K stolen memory.
[   25.700000] agpgart: AGP aperture is 256M @ 0xd0000000
[   25.880000] input: PS/2 Mouse as /class/input/input2
[   25.904000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input3
[   25.908000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   25.908000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   26.076000] input: PC Speaker as /class/input/input4
[   26.176000] sdhci: Secure Digital Host Controller Interface driver
[   26.176000] sdhci: Copyright(c) Pierre Ossman
[   26.176000] sdhci: SDHCI controller found at 0000:02:01.2 [1180:0822] (rev 18)
[   26.176000] ACPI: PCI Interrupt 0000:02:01.2[C] -> GSI 18 (level, low) -> IRQ 18
[   26.176000] mmc0: SDHCI at 0xefaff700 irq 18 DMA
[   26.248000] ieee80211_crypt: registered algorithm 'NULL'
[   26.252000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   26.252000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   26.284000] Bluetooth: Core ver 2.11
[   26.284000] NET: Registered protocol family 31
[   26.284000] Bluetooth: HCI device and connection manager initialized
[   26.284000] Bluetooth: HCI socket layer initialized
[   26.308000] Bluetooth: HCI USB driver ver 2.9
[   26.360000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.0mp
[   26.360000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   26.360000] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   26.360000] PCI: Setting latency timer of device 0000:0b:00.0 to 64
[   26.404000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   26.452000] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   26.452000] PCI: Setting latency timer of device 0000:0c:00.0 to 64
[   26.452000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   26.456000] usbcore: registered new interface driver hci_usb
[   26.808000] cs: IO port probe 0x100-0x3af: clean.
[   26.812000] cs: IO port probe 0x3e0-0x4ff: clean.
[   26.812000] cs: IO port probe 0x820-0x8ff: clean.
[   26.812000] cs: IO port probe 0xc00-0xcf7: clean.
[   26.816000] cs: IO port probe 0xa00-0xaff: clean.
[   26.912000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 21
[   26.912000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   28.212000] hda_intel: azx_get_response timeout, switching to polling mode...
[   28.376000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
[   28.496000] lp: driver loaded but no devices found
[   28.716000] Adding 3229024k swap on /dev/disk/by-uuid/384be804-6273-4341-8212-9705bff8ab8b.  Priority:-1 extents:1 across:3229024k
[   28.920000] EXT3 FS on sda1, internal journal
[   30.732000] NET: Registered protocol family 17
[   31.976000] input: Lid Switch as /class/input/input5
[   31.976000] ACPI: Lid Switch [LID]
[   31.976000] input: Power Button (CM) as /class/input/input6
[   31.976000] ACPI: Power Button (CM) [PBTN]
[   31.976000] input: Sleep Button (CM) as /class/input/input7
[   31.976000] ACPI: Sleep Button (CM) [SBTN]
[   32.104000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   32.104000] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[   32.220000] Using specific hotkey driver
[   32.276000] ibm_acpi: ec object not found
[   32.316000] ACPI: AC Adapter [AC] (off-line)
[   32.392000] ACPI: Battery Slot [BAT0] (battery present)
[   32.520000] ACPI: ACPI Dock Station Driver 
[   32.552000] pcc_acpi: loading...
[   39.724000] [drm] Initialized drm 1.1.0 20060810
[   39.728000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   39.732000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   40.068000] apm: BIOS not found.
[   41.180000] Bluetooth: L2CAP ver 2.8
[   41.180000] Bluetooth: L2CAP socket layer initialized
[   41.376000] hub 1-2.3:1.0: hub_port_status failed (err = -71)
[   41.376000] hub 1-2.3:1.0: cannot disable port 1 (err = -71)
[   41.376000] hub 1-2.3:1.0: hub_port_status failed (err = -71)
[   41.428000] Bluetooth: RFCOMM socket layer initialized
[   41.428000] Bluetooth: RFCOMM TTY layer initialized
[   41.428000] Bluetooth: RFCOMM ver 1.8
[   41.460000] hub 1-2:1.0: port 3 disabled by hub (EMI?), re-enabling...
[   41.460000] usb 1-2.3: USB disconnect, address 5
[   41.460000] usb 1-2.3.1: USB disconnect, address 7
[   41.460000] usb 1-2.3.2: USB disconnect, address 8
[   41.536000] usb 1-2.3: new full speed USB device using uhci_hcd and address 9
[   41.648000] usb 1-2.3: configuration #1 chosen from 1 choice
[   41.648000] hub 1-2.3:1.0: USB hub found
[   41.652000] hub 1-2.3:1.0: 3 ports detected
[   41.960000] usb 1-2.3.1: new full speed USB device using uhci_hcd and address 10
[   42.092000] usb 1-2.3.1: configuration #1 chosen from 1 choice
[   42.300000] usb 1-2.3.2: new full speed USB device using uhci_hcd and address 11
[   42.420000] usb 1-2.3.2: configuration #1 chosen from 1 choice
[   42.440000] ip_tables: (C) 2000-2006 Netfilter Core Team
[   42.936000] Netfilter messages via NETLINK v0.30.
[   43.008000] nf_conntrack version 0.5.0 (8192 buckets, 65536 max)
[   47.196000] NET: Registered protocol family 10
[   47.196000] lo: Disabled Privacy Extensions
[  271.704000] ipw3945: Radio Frequency Kill Switch is On:
[  271.704000] Kill switch must be turned off for wireless networking to work.
[  271.704000] atkbd.c: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[  271.704000] atkbd.c: Use 'setkeycodes e008 <keycode>' to make it known.
[  271.736000] usb 1-2.4: USB disconnect, address 6
[  481.244000] PM: Writing back config space on device 0000:09:00.0 at offset c (was 379b0000, writing 0)
[  481.328000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  485.324000] tg3: eth0: Link is up at 1000 Mbps, full duplex.
[  485.324000] tg3: eth0: Flow control is on for TX and on for RX.
[  485.328000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  496.120000] eth0: no IPv6 routers present

```

and here is the output from `ifup -a`

```

Ignoring unknown interface lo,=lo,.
Ignoring unknown interface eth0,=eth0,.
Ignoring unknown interface eth1,=eth1,.
eth2: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device

```

---

### Post by noob12 on 2007-09-10
This line is not proper syntax, and that's why your **ifup -a** complains
```

auto lo, eth0, eth1, eth2

```
Put each one on a separate line, no commas here.  Like this
```

auto lo
auto eth0
...

```

Can you post the output of of these commands:
```

lspci -nn

sudo lshw -C network

ifconfig -a

```

---

### Post by spd106 on 2007-09-10
First you need to edit the interfaces file to remove the commas in that auto line. Then you should not get the unknown interface errors.

Have you tried the restricted drivers manager? It should say whether the Intel ipw3945 driver is in use. Also try looking at the output of this command.
```
sudo lshw -class network
```

AFAIK support for the 4965agn card was brought in with kernel 2.6.22, so you'll have to build your own or wait for Ubuntu 7.10. From some reports I've read the Gutsy Gibbon testing is getting to be stable, so you could try a daily live cd.

---

### Post by poncenby on 2007-09-10
Many thanks for such prompt replies, here is the output from the suggested commands:

lspci -nn

```

00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 01)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 01)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 01)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 [8086:27d4] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 [8086:27c8] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 [8086:27c9] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 [8086:27ca] (rev 01)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 [8086:27cb] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 01)
02:01.0 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev b4)
02:01.1 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C552 IEEE 1394 Controller [1180:0552] (rev 09)
02:01.2 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 18)
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express [14e4:1600] (rev 02)
0b:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:4222] (rev 02)
0c:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:4222] (rev 02)

```

sudo lshw -C network

```

  *-network
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0b:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=ipw3945 latency=0
       resources: iomemory:efdff000-efdfffff irq:16
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0c:00.0
       logical name: eth1
       version: 02
       serial: 00:19:d2:7c:b5:3d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.0mp firmware=14.2 1:0 () latency=0 link=no multicast=yes wireless=radio off
       resources: iomemory:efcff000-efcfffff irq:17
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5752 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@09:00.0
       logical name: eth0
       version: 02
       serial: 00:18:8b:be:9e:f6
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.72 duplex=full firmware=5752-v3.19 ip=10.0.0.2 latency=0 link=yes multicast=yes port=twisted pair speed=1GB/s
       resources: iomemory:efbf0000-efbfffff irq:18

```

ifconfig -a

```

eth0      Link encap:Ethernet  HWaddr 00:18:8B:BE:9E:F6  
          inet addr:10.0.0.2  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::218:8bff:febe:9ef6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:55 errors:0 dropped:0 overruns:0 frame:0
          TX packets:70 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3922 (3.8 KiB)  TX bytes:51285 (50.0 KiB)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:19:D2:7C:B5:3D  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:2709 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0x4000 Memory:efcff000-efcfffff 

lo        Link encap:Local Loopback  
          LOOPBACK  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

so obviously one of the cards is disabled, how do I go about enabling it?

thanks again

---

### Post by noob12 on 2007-09-10
The one that says DISABLED has an interface (eth1) associated to it.  It's actually in better shape.  It is only disabled because your wireless switch is off on  your laptop.  You need to turn the wireless switch on.

The one that has no interface associated to it (the one at **pci@0b:00.0**) is actually the one that is not showing up in **ifconfig -a** output, and I don't yet know why.  The driver did claim it.

---

