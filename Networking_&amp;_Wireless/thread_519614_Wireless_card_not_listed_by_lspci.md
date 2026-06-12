---
title: "Wireless card not listed by lspci"
date: 2007-08-07
forum: Networking &amp; Wireless
---

### Post by hammerhai on 2007-08-07
Hello,

my wireless card (a Broadcom 4311AG) is not listed by lspci. Only the wired ethernet device (BCM5906M) shows up, the wireless one however is missing. I already added noapic and nolapic to the boot options but still the device doesn't show up.
```
00:00.0 Host bridge: ATI Technologies Inc Unknown device 7910
00:01.0 PCI bridge: ATI Technologies Inc Unknown device 7912
00:04.0 PCI bridge: ATI Technologies Inc Unknown device 7914
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 7915
00:06.0 PCI bridge: ATI Technologies Inc Unknown device 7916
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SB600 SMBus (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SB600 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SB600 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon X1200 Series
02:04.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b6)
10:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
```

My dmesg output, in case it is useful:
```
[    0.000000] Linux version 2.6.22-9-generic (buildd@palmer) (gcc version 4.1.3 20070718 (prerelease) (Ubuntu 4.1.2-14ubuntu1)) #1 SMP Fri Aug 3 00:50:37 GMT 2007 (Ubuntu 2.6.22-9.25-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000037fb0000 (usable)
[    0.000000]  BIOS-e820: 0000000037fb0000 - 0000000037fc8000 (reserved)
[    0.000000]  BIOS-e820: 0000000037fc8000 - 0000000037fe7fb8 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000037fe7fb8 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec02000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffbc0000 - 00000000ffcc0000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 895MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 229296) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229296
[    0.000000]   HighMem    229296 ->   229296
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   229296
[    0.000000] On node 0 totalpages: 229296
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1759 pages used for memmap
[    0.000000]   Normal zone: 223441 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP 000FE0B0, 0024 (r2 HP    )
[    0.000000] ACPI: XSDT 37FC81BC, 0064 (r1 HPQOEM SLIC-MPC        1 HP          1)
[    0.000000] ACPI: FACP 37FC8084, 00F4 (r4 HP     0944            3 HP          1)
[    0.000000] ACPI Error (tbfadt-0445): 32/64X address mismatch in "Pm2ControlBlock": [00008800] [0000000000008100], using 64X [20070126]
[    0.000000] ACPI: DSDT 37FC84A4, 11437 (r1 HP        SB400    10000 MSFT  3000001)
[    0.000000] ACPI: FACS 37FE7D80, 0040
[    0.000000] ACPI: SLIC 37FC8220, 0176 (r1 HPQOEM SLIC-MPC        1 HP          1)
[    0.000000] ACPI: EPTH 37FC8398, 0038 (r1 HP     0944            1 HP          1)
[    0.000000] ACPI: APIC 37FC83D0, 0062 (r1 HP     0944            1 HP          1)
[    0.000000] ACPI: MCFG 37FC8434, 003C (r1 HP     0944            1 HP          1)
[    0.000000] ACPI: TCPA 37FC8470, 0032 (r2 HP     0944            1 HP          1)
[    0.000000] ACPI: SSDT 37FD98DB, 0059 (r1 HP       HPQNLP        1 MSFT  3000001)
[    0.000000] ACPI: SSDT 37FD9934, 0115 (r1 HP     PSSTBLID        1 HP          1)
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] Built 1 zonelists.  Total pages: 227505
[    0.000000] Kernel command line: root=UUID=7ff11e37-10b9-49b8-a05d-11faf55747d8 ro quiet splash noapic nolapic
[    0.000000] mapped APIC to ffffd000 (0170e000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1995.996 MHz processor.
[   89.791054] Console: colour VGA+ 80x25
[   89.791523] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   89.792261] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   89.818743] Memory: 897812k/917184k available (2010k kernel code, 18700k reserved, 917k data, 364k init, 0k highmem)
[   89.818753] virtual kernel memory layout:
[   89.818754]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   89.818755]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   89.818756]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   89.818757]     lowmem  : 0xc0000000 - 0xf7fb0000   ( 895 MB)
[   89.818776]       .init : 0xc03e1000 - 0xc043c000   ( 364 kB)
[   89.818777]       .data : 0xc02f6806 - 0xc03dbe64   ( 917 kB)
[   89.818779]       .text : 0xc0100000 - 0xc02f6806   (2010 kB)
[   89.818781] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   89.818846] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   89.898841] Calibrating delay using timer specific routine.. 4000.83 BogoMIPS (lpj=8001670)
[   89.898878] Security Framework v1.0.0 initialized
[   89.898900] SELinux:  Disabled at boot.
[   89.898910] Mount-cache hash table entries: 512
[   89.899105] CPU: After generic identify, caps: 078bfbff ebd3fbff 00000000 00000000 00002001 00000000 00000019
[   89.899131] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   89.899133] CPU: L2 Cache: 256K (64 bytes/line)
[   89.899136] CPU: After all inits, caps: 078bfbff ebd3fbff 00000000 00000410 00002001 00000000 00000019
[   89.899161] Compat vDSO mapped to ffffe000.
[   89.899170] Checking 'hlt' instruction... OK.
[   89.915025] SMP alternatives: switching to UP code
[   89.915315] Freeing SMP alternatives: 11k freed
[   89.915810] Early unpacking initramfs... done
[   90.511316] ACPI: Core revision 20070126
[   90.511552] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   90.517960] ACPI: setting ELCR to 0200 (from 0c20)
[   90.599775] CPU0: AMD Mobile AMD Sempron(tm) Processor 3600+ stepping 02
[   90.599781] SMP motherboard not detected.
[   90.599783] Local APIC not detected. Using dummy APIC emulation.
[   90.599810] Brought up 1 CPUs
[   90.599891] HP Compaq Laptop series board detected. Selecting BIOS-method for reboots.
[   90.599894] Booting paravirtualized kernel on bare hardware
[   90.599961] Time: 10:45:07  Date: 07/07/107
[   90.599978] NET: Registered protocol family 16
[   90.600040] EISA bus registered
[   90.600056] ACPI: bus type pci registered
[   90.600711] PCI: PCI BIOS revision 2.10 entry at 0xf0322, last bus=48
[   90.600713] PCI: Using configuration type 1
[   90.600714] Setting up standard PCI resources
[   90.602769] ACPI: EC: Look up EC in DSDT
[   90.602839] ACPI: EC: GPE=0x11, ports=0x66, 0x62
[   90.833014] ACPI: Interpreter enabled
[   90.833019] ACPI: (supports S0 S3 S4 S5)
[   90.833030] ACPI: Using PIC for interrupt routing
[   90.840803] ACPI: EC: GPE=0x11, ports=0x66, 0x62
[   90.840868] ACPI: PCI Root Bridge [C08B] (0000:00)
[   90.840875] PCI: Probing PCI hardware (bus 00)
[   90.842044] PCI: Transparent bridge - 0000:00:14.4
[   90.842102] PCI: Bus #03 (-#06) is hidden behind transparent bridge #02 (-#03) (try 'pci=assign-busses')
[   90.842104] Please report the result to linux-kernel to fix this permanently
[   90.842137] ACPI: PCI Interrupt Routing Table [\_SB_.C08B._PRT]
[   90.842518] ACPI: PCI Interrupt Routing Table [\_SB_.C08B.C08C._PRT]
[   90.842626] ACPI: PCI Interrupt Routing Table [\_SB_.C08B.C0FC._PRT]
[   90.860378] ACPI: PCI Interrupt Link [C145] (IRQs *10 11)
[   90.860523] ACPI: PCI Interrupt Link [C146] (IRQs 10 11) *5
[   90.860658] ACPI: PCI Interrupt Link [C147] (IRQs 10 11) *0, disabled.
[   90.860804] ACPI: PCI Interrupt Link [C148] (IRQs 10 *11)
[   90.860939] ACPI: PCI Interrupt Link [C149] (IRQs 10 11) *0, disabled.
[   90.861075] ACPI: PCI Interrupt Link [C14A] (IRQs 9) *0, disabled.
[   90.861210] ACPI: PCI Interrupt Link [C14B] (IRQs 10 11) *0, disabled.
[   90.861351] ACPI: PCI Interrupt Link [C14C] (IRQs 10 *11)
[   90.861475] ACPI: Power Resource [C171] (off)
[   90.861518] ACPI: Power Resource [C24C] (on)
[   90.861611] ACPI: Power Resource [C395] (off)
[   90.861689] ACPI: Power Resource [C396] (off)
[   90.861767] ACPI: Power Resource [C397] (off)
[   90.861844] ACPI: Power Resource [C398] (off)
[   90.861852] Linux Plug and Play Support v0.97 (c) Adam Belay
[   90.861861] pnp: PnP ACPI init
[   90.861869] ACPI: bus type pnp registered
[   90.868192] pnp: PnP ACPI: found 11 devices
[   90.868194] ACPI: ACPI bus type pnp unregistered
[   90.868198] PnPBIOS: Disabled by ACPI PNP
[   90.868237] PCI: Using ACPI for IRQ routing
[   90.868240] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   90.868271] PCI: Cannot allocate resource region 0 of device 0000:00:14.2
[   90.987228] NET: Registered protocol family 8
[   90.987230] NET: Registered protocol family 20
[   90.987279] pnp: 00:00: iomem range 0x0-0x9ffff could not be reserved
[   90.987282] pnp: 00:00: iomem range 0xe0000-0xfffff could not be reserved
[   90.987285] pnp: 00:00: iomem range 0x100000-0xffffffff could not be reserved
[   90.987292] pnp: 00:08: ioport range 0x40b-0x40b has been reserved
[   90.987295] pnp: 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   90.987298] pnp: 00:08: iomem range 0xffb00000-0xffbfffff could not be reserved
[   90.987301] pnp: 00:08: iomem range 0xfff00000-0xffffffff could not be reserved
[   90.987305] pnp: 00:09: ioport range 0x8000-0x802f has been reserved
[   90.987308] pnp: 00:09: ioport range 0x8100-0x811f has been reserved
[   90.987311] pnp: 00:09: iomem range 0xe0000000-0xefffffff could not be reserved
[   90.987314] pnp: 00:09: iomem range 0xfec00000-0xfec000ff could not be reserved
[   90.987317] pnp: 00:09: iomem range 0xfed45000-0xfed8ffff has been reserved
[   90.987321] pnp: 00:0a: iomem range 0xcd400-0xcffff has been reserved
[   90.987323] pnp: 00:0a: iomem range 0xd2a00-0xd2fff has been reserved
[   90.987326] pnp: 00:0a: iomem range 0x0-0x7ffffff could not be reserved
[   90.987329] pnp: 00:0a: iomem range 0xfee00000-0xfee00fff has been reserved
[   90.990269] Time: tsc clocksource has been installed.
[   91.017540] PCI: Bridge: 0000:00:01.0
[   91.017542]   IO window: 4000-4fff
[   91.017545]   MEM window: d0200000-d03fffff
[   91.017548]   PREFETCH window: c0000000-c7ffffff
[   91.017551] PCI: Bridge: 0000:00:04.0
[   91.017552]   IO window: disabled.
[   91.017555]   MEM window: d0000000-d00fffff
[   91.017557]   PREFETCH window: disabled.
[   91.017560] PCI: Bridge: 0000:00:05.0
[   91.017562]   IO window: 2000-3fff
[   91.017564]   MEM window: cc000000-cfffffff
[   91.017566]   PREFETCH window: disabled.
[   91.017569] PCI: Bridge: 0000:00:06.0
[   91.017570]   IO window: disabled.
[   91.017573]   MEM window: c8000000-c80fffff
[   91.017575]   PREFETCH window: disabled.
[   91.017579] PCI: Bus 3, cardbus bridge: 0000:02:04.0
[   91.017581]   IO window: 00001000-000010ff
[   91.017589]   IO window: 00001400-000014ff
[   91.017594]   PREFETCH window: 50000000-53ffffff
[   91.017599]   MEM window: 58000000-5bffffff
[   91.017603] PCI: Bridge: 0000:00:14.4
[   91.017606]   IO window: 1000-1fff
[   91.017611]   MEM window: d0100000-d01fffff
[   91.017615]   PREFETCH window: 50000000-53ffffff
[   91.017632] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   91.017638] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   91.017644] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   91.017970] ACPI: PCI Interrupt Link [C149] enabled at IRQ 11
[   91.017973] PCI: setting IRQ 11 as level-triggered
[   91.017980] ACPI: PCI Interrupt 0000:02:04.0[A] -> Link [C149] -> GSI 11 (level, low) -> IRQ 11
[   91.017995] NET: Registered protocol family 2
[   91.054272] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   91.054352] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   91.055156] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   91.055425] TCP: Hash tables configured (established 131072 bind 65536)
[   91.055428] TCP reno registered
[   91.066340] checking if image is initramfs... it is
[   91.518037] Switched to high resolution mode on CPU 0
[   91.609040] Freeing initrd memory: 6860k freed
[   91.609293] audit: initializing netlink socket (disabled)
[   91.609303] audit(1186483507.596:1): initialized
[   91.610894] VFS: Disk quotas dquot_6.5.1
[   91.610936] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   91.611010] io scheduler noop registered
[   91.611012] io scheduler anticipatory registered
[   91.611014] io scheduler deadline registered
[   91.611026] io scheduler cfq registered (default)
[   91.611079] Boot video device is 0000:01:05.0
[   91.611156] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   91.611175] assign_interrupt_mode Found MSI capability
[   91.611196] Allocate Port Service[0000:00:04.0:pcie00]
[   91.611249] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   91.611266] assign_interrupt_mode Found MSI capability
[   91.611283] Allocate Port Service[0000:00:05.0:pcie00]
[   91.611332] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   91.611350] assign_interrupt_mode Found MSI capability
[   91.611367] Allocate Port Service[0000:00:06.0:pcie00]
[   91.611493] isapnp: Scanning for PnP cards...
[   91.968661] isapnp: No Plug & Play device found
[   91.992044] Real Time Clock Driver v1.12ac
[   91.992125] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   91.992996] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   91.993190] input: Macintosh mouse button emulation as /class/input/input0
[   91.993245] PNP: PS/2 Controller [PNP0303:C249,PNP0f13:C24A] at 0x60,0x64 irq 1,12
[   91.995344] i8042.c: Detected active multiplexing controller, rev 1.1.
[   91.996114] serio: i8042 KBD port at 0x60,0x64 irq 1
[   91.996118] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   91.996121] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   91.996123] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   91.996125] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   91.996280] mice: PS/2 mouse device common for all mice
[   91.996453] EISA: Probing bus 0 at eisa.0
[   91.996463] Cannot allocate resource for EISA slot 1
[   91.996466] Cannot allocate resource for EISA slot 2
[   91.996467] Cannot allocate resource for EISA slot 3
[   91.996469] Cannot allocate resource for EISA slot 4
[   91.996471] Cannot allocate resource for EISA slot 5
[   91.996481] Cannot allocate resource for EISA slot 8
[   91.996482] EISA: Detected 0 cards.
[   91.996553] TCP cubic registered
[   91.996563] NET: Registered protocol family 1
[   91.996581] Using IPI No-Shortcut mode
[   91.996723]   Magic number: 3:831:779
[   91.996804]   hash matches device ptyq1
[   91.997041] Freeing unused kernel memory: 364k freed
[   92.093657] input: AT Translated Set 2 keyboard as /class/input/input1
[   92.098151] spurious 8259A interrupt: IRQ7.
[   93.197702] AppArmor: AppArmor initialized
[   93.197710] audit(1186483509.096:2): AppArmor initialized
[   93.197711]
[   93.200724] AppArmor: Registered secondary security module: capability.
[   93.200728] Capability LSM initialized as secondary
[   93.203876] ACPI: Transitioning device [C399] to D3
[   93.203879] ACPI: Transitioning device [C399] to D3
[   93.203882] ACPI: Fan [C399] (off)
[   93.204032] ACPI: Transitioning device [C39A] to D3
[   93.204034] ACPI: Transitioning device [C39A] to D3
[   93.204036] ACPI: Fan [C39A] (off)
[   93.204183] ACPI: Transitioning device [C39B] to D3
[   93.204185] ACPI: Transitioning device [C39B] to D3
[   93.204187] ACPI: Fan [C39B] (off)
[   93.204334] ACPI: Transitioning device [C39C] to D3
[   93.204336] ACPI: Transitioning device [C39C] to D3
[   93.204339] ACPI: Fan [C39C] (off)
[   93.208014] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   93.208019] ACPI: Processor [C000] (supports 8 throttling states)
[   93.208029] ACPI Exception (processor_core-0781): AE_NOT_FOUND, Processor Device is not present [20070126]
[   93.216053] ACPI: Thermal Zone [TZ1] (42 C)
[   93.733020] tg3.c:v3.77 (May 31, 2007)
[   93.733423] ACPI: PCI Interrupt Link [C145] enabled at IRQ 10
[   93.733426] PCI: setting IRQ 10 as level-triggered
[   93.733433] ACPI: PCI Interrupt 0000:10:00.0[A] -> Link [C145] -> GSI 10 (level, low) -> IRQ 10
[   93.733479] PCI: Setting latency timer of device 0000:10:00.0 to 64
[   93.772135] SCSI subsystem initialized
[   93.776045] libata version 2.21 loaded.
[   93.791916] usbcore: registered new interface driver usbfs
[   93.791935] usbcore: registered new interface driver hub
[   93.791955] usbcore: registered new device driver usb
[   93.792549] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   93.931917] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   93.931922] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    4.188000] Marking TSC unstable due to: possible TSC halt in C2.
[    4.192000] Time: acpi_pm clocksource has been installed.
[    4.584000] eth0: Tigon3 [partno(BCM95906) rev c002 PHY(5906)] (PCI Express) 10/100Base-TX Ethernet 00:17:a4:e8:82:09
[    4.584000] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[0] TSOcap[0]
[    4.584000] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    4.584000] ahci 0000:00:12.0: version 2.2
[    4.584000] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [C145] -> GSI 10 (level, low) -> IRQ 10
[    4.584000] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
[    5.588000] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    5.588000] ahci 0000:00:12.0: flags: ncq ilck pm led clo pio slum part
[    5.588000] scsi0 : ahci
[    5.588000] scsi1 : ahci
[    5.588000] scsi2 : ahci
[    5.588000] scsi3 : ahci
[    5.588000] ata1: SATA max UDMA/133 cmd 0xf882e100 ctl 0x00000000 bmdma 0x00000000 irq 10
[    5.588000] ata2: SATA max UDMA/133 cmd 0xf882e180 ctl 0x00000000 bmdma 0x00000000 irq 10
[    5.588000] ata3: SATA max UDMA/133 cmd 0xf882e200 ctl 0x00000000 bmdma 0x00000000 irq 10
[    5.588000] ata4: SATA max UDMA/133 cmd 0xf882e280 ctl 0x00000000 bmdma 0x00000000 irq 10
[    6.072000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    6.088000] ata1.00: ATA-7: FUJITSU MHW2080BH PL, 891F, max UDMA/100
[    6.088000] ata1.00: 156301488 sectors, multi 16: LBA48
[    6.092000] ata1.00: configured for UDMA/100
[    6.404000] ata2: SATA link down (SStatus 0 SControl 0)
[    6.716000] ata3: SATA link down (SStatus 0 SControl 0)
[    7.028000] ata4: SATA link down (SStatus 0 SControl 0)
[    7.028000] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHW2080B 891F PQ: 0 ANSI: 5
[    7.028000] ACPI: PCI Interrupt Link [C14C] enabled at IRQ 11
[    7.028000] ACPI: PCI Interrupt 0000:00:13.0[A] -> Link [C14C] -> GSI 11 (level, low) -> IRQ 11
[    7.028000] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    7.028000] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[    7.028000] ohci_hcd 0000:00:13.0: irq 11, io mem 0xd0401000
[    7.036000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    7.036000] sd 0:0:0:0: [sda] Write Protect is off
[    7.036000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    7.036000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.036000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    7.036000] sd 0:0:0:0: [sda] Write Protect is off
[    7.036000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    7.036000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.036000]  sda:<6>usb usb1: configuration #1 chosen from 1 choice
[    7.088000] hub 1-0:1.0: USB hub found
[    7.088000] hub 1-0:1.0: 2 ports detected
[    7.120000]  sda1 sda2 < sda5 >
[    7.172000] sd 0:0:0:0: [sda] Attached SCSI disk
[    7.176000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    7.192000] ACPI: PCI Interrupt Link [C146] enabled at IRQ 10
[    7.192000] ACPI: PCI Interrupt 0000:00:13.1[B] -> Link [C146] -> GSI 10 (level, low) -> IRQ 10
[    7.192000] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    7.192000] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[    7.192000] ohci_hcd 0000:00:13.1: irq 10, io mem 0xd0402000
[    7.252000] usb usb2: configuration #1 chosen from 1 choice
[    7.252000] hub 2-0:1.0: USB hub found
[    7.252000] hub 2-0:1.0: 2 ports detected
[    7.356000] ACPI: PCI Interrupt 0000:00:13.2[C] -> Link [C146] -> GSI 10 (level, low) -> IRQ 10
[    7.356000] ohci_hcd 0000:00:13.2: OHCI Host Controller
[    7.356000] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[    7.356000] ohci_hcd 0000:00:13.2: irq 10, io mem 0xd0403000
[    7.416000] usb usb3: configuration #1 chosen from 1 choice
[    7.416000] hub 3-0:1.0: USB hub found
[    7.416000] hub 3-0:1.0: 2 ports detected
[    7.468000] Attempting manual resume
[    7.468000] swsusp: Resume From Partition 8:5
[    7.468000] PM: Checking swsusp image.
[    7.472000] PM: Resume from disk failed.
[    7.520000] ACPI: PCI Interrupt 0000:00:13.3[B] -> Link [C146] -> GSI 10 (level, low) -> IRQ 10
[    7.520000] ohci_hcd 0000:00:13.3: OHCI Host Controller
[    7.520000] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 4
[    7.520000] ohci_hcd 0000:00:13.3: irq 10, io mem 0xd0404000
[    7.580000] usb usb4: configuration #1 chosen from 1 choice
[    7.580000] hub 4-0:1.0: USB hub found
[    7.580000] hub 4-0:1.0: 2 ports detected
[    7.608000] kjournald starting.  Commit interval 5 seconds
[    7.608000] EXT3-fs: mounted filesystem with ordered data mode.
[    7.672000] usb 2-1: new low speed USB device using ohci_hcd and address 2
[    7.684000] ACPI: PCI Interrupt 0000:00:13.4[C] -> Link [C146] -> GSI 10 (level, low) -> IRQ 10
[    7.684000] ohci_hcd 0000:00:13.4: OHCI Host Controller
[    7.684000] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 5
[    7.684000] ohci_hcd 0000:00:13.4: irq 10, io mem 0xd0405000
[    7.748000] usb usb5: configuration #1 chosen from 1 choice
[    7.748000] hub 5-0:1.0: USB hub found
[    7.748000] hub 5-0:1.0: 2 ports detected
[    7.852000] ACPI: PCI Interrupt 0000:00:13.5[D] -> Link [C14C] -> GSI 11 (level, low) -> IRQ 11
[    7.852000] ehci_hcd 0000:00:13.5: EHCI Host Controller
[    7.852000] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 6
[    7.852000] ehci_hcd 0000:00:13.5: debug port 1
[    7.852000] ehci_hcd 0000:00:13.5: irq 11, io mem 0xd0406000
[    7.852000] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    7.852000] usb usb6: configuration #1 chosen from 1 choice
[    7.852000] hub 6-0:1.0: USB hub found
[    7.852000] hub 6-0:1.0: 10 ports detected
[    7.956000] SB600_PATA: IDE controller at PCI slot 0000:00:14.1
[    7.956000] ACPI: PCI Interrupt 0000:00:14.1[A] -> Link [C145] -> GSI 10 (level, low) -> IRQ 10
[    7.956000] SB600_PATA: chipset revision 0
[    7.956000] SB600_PATA: not 100% native mode: will probe irqs later
[    7.956000]     ide0: BM-DMA at 0x5040-0x5047, BIOS settings: hda:DMA, hdb:pio
[    7.956000] Probing IDE interface ide0...
[    8.360000] usb 2-1: device not accepting address 2, error -62
[    8.692000] hda: HL-DT-ST DVDRAM GSA-T20L, ATAPI CD/DVD-ROM drive
[    9.028000] hda: selected mode 0x22
[    9.028000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    9.044000] usb 2-1: new low speed USB device using ohci_hcd and address 4
[    9.372000] usb 2-1: configuration #1 chosen from 1 choice
[   49.136000] PM: Writing back config space on device 0000:10:00.0 at offset c (was ffff0000, writing 0)
[   49.136000] PM: Writing back config space on device 0000:10:00.0 at offset 1 (was 100406, writing 100006)
[   49.292000] tg3: eth0: No interrupt was generated using MSI, switching to INTx mode. Please report this failure to the PCI maintainer and include system chipset information.
[   50.632000] Linux agpgart interface v0.102 (c) Dave Jones
[   50.648000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   50.652000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   50.656000] NET: Registered protocol family 17
[   50.944000] tg3: eth0: Link is up at 100 Mbps, full duplex.
[   50.944000] tg3: eth0: Flow control is on for TX and on for RX.
[   51.444000] Yenta: CardBus bridge found at 0000:02:04.0 [103c:30c2]
[   51.564000] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   51.572000] Yenta: ISA IRQ mask 0x00b8, PCI irq 11
[   51.572000] Socket status: 30000006
[   51.572000] Yenta: Raising subordinate bus# of parent bus (#02) from #03 to #06
[   51.572000] pcmcia: parent PCI bridge I/O window: 0x1000 - 0x1fff
[   51.572000] cs: IO port probe 0x1000-0x1fff: clean.
[   51.572000] pcmcia: parent PCI bridge Memory window: 0xd0100000 - 0xd01fffff
[   51.572000] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x53ffffff
[   52.040000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x2580b1, caps: 0xa04793/0x300000
[   52.040000] serio: Synaptics pass-through port at isa0060/serio4/input0
[   52.084000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[   52.160000] usbcore: registered new interface driver hiddev
[   52.212000] input: PC Speaker as /class/input/input3
[   52.240000] hda: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, DMA
[   52.240000] Uniform CD-ROM driver Revision: 3.20
[   52.408000] ACPI: PCI Interrupt 0000:00:14.2[A] -> Link [C145] -> GSI 10 (level, low) -> IRQ 10
[   52.428000] input: Logitech USB-PS/2 Optical Mouse as /class/input/input4
[   52.428000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:13.1-1
[   52.428000] usbcore: registered new interface driver usbhid
[   52.428000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   52.620000] cs: IO port probe 0x100-0x3af: clean.
[   52.620000] cs: IO port probe 0x3e0-0x4ff: clean.
[   52.620000] cs: IO port probe 0x820-0x8ff: clean.
[   52.624000] cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xc10-0xc17 0xc50-0xc57 0xc68-0xc6f 0xcd0-0xcdf
[   52.624000] cs: IO port probe 0xa00-0xaff: clean.
[   53.320000] si3054: cannot initialize. EXT MID = 0000
[   54.272000] fuse init (API version 7.8)
[   54.296000] lp: driver loaded but no devices found
[   54.536000] Adding 2650684k swap on /dev/disk/by-uuid/acdc13ae-12a2-4507-97c1-319849db31d0.  Priority:-1 extents:1 across:2650684k
[   55.948000] EXT3 FS on sda1, internal journal
[   56.572000] AppArmor: Unregistered secondary security module: capability
[   57.588000] NET: Registered protocol family 10
[   57.588000] lo: Disabled Privacy Extensions
[   61.232000] ndiswrapper version 1.47 loaded (smp=yes)
[   61.644000] usbcore: registered new interface driver ndiswrapper
[   64.492000] No dock devices found.
[   64.572000] input: Power Button (FF) as /class/input/input5
[   64.576000] ACPI: Power Button (FF) [PWRF]
[   64.612000] input: Sleep Button (CM) as /class/input/input6
[   64.616000] ACPI: Sleep Button (CM) [C28D]
[   64.648000] input: Lid Switch as /class/input/input7
[   64.652000] ACPI: Lid Switch [C265]
[   64.764000] set_level status: 0
[   64.764000] ACPI: Video Device [C08D] (multi-head: yes  rom: no  post: no)
[   64.804000] ACPI: Battery Slot [C1ED] (battery present)
[   64.804000] ACPI: Battery Slot [C1EC] (battery absent)
[   65.304000] ACPI: AC Adapter [C1EB] (off-line)
[   65.780000] powernow-k8: Found 1 Mobile AMD Sempron(tm) Processor 3600+ processors (version 2.00.00)
[   65.780000] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0xe
[   65.780000] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x10
[   65.780000] powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x12
[   65.780000] powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x18
[   65.780000] powernow-k8: ph2 null fid transition 0xc
[   68.088000] eth0: no IPv6 routers present
[   69.208000] apm: BIOS not found.
[   70.620000] Clocksource tsc unstable (delta = -136891217 ns)
[   73.036000] AppArmor: Registered secondary security module: capability.
[   73.036000] Capability LSM initialized as secondary
[   73.764000] Bluetooth: Core ver 2.11
[   73.764000] NET: Registered protocol family 31
[   73.764000] Bluetooth: HCI device and connection manager initialized
[   73.764000] Bluetooth: HCI socket layer initialized
[   73.844000] Bluetooth: L2CAP ver 2.8
[   73.844000] Bluetooth: L2CAP socket layer initialized
[   74.196000] Bluetooth: RFCOMM socket layer initialized
[   74.200000] Bluetooth: RFCOMM TTY layer initialized
[   74.200000] Bluetooth: RFCOMM ver 1.8
[  305.948000] [fglrx] Maximum main memory to use for locked dma buffers: 804 MBytes.
[  305.948000] [fglrx] module loaded - fglrx 8.37.6 [May 25 2007] on minor 0
[  305.996000] ACPI: PCI Interrupt Link [C148] enabled at IRQ 11
[  305.996000] ACPI: PCI Interrupt 0000:01:05.0[B] -> Link [C148] -> GSI 11 (level, low) -> IRQ 11
[  310.164000] [fglrx] total      GART = 130023424
[  310.164000] [fglrx] free       GART = 114032640
[  310.164000] [fglrx] max single GART = 114032640
[  310.164000] [fglrx] total      LFB  = 134217728
[  310.164000] [fglrx] free       LFB  = 119828480
[  310.164000] [fglrx] max single LFB  = 119828480
[  310.164000] [fglrx] total      Inv  = 0
[  310.164000] [fglrx] free       Inv  = 0
[  310.164000] [fglrx] max single Inv  = 0
[  310.164000] [fglrx] total      TIM  = 0
[  351.848000] hda-intel: Invalid position buffer, using LPIB read method instead.
[  376.508000] set_level status: 0
[  771.580000] set_level status: 0
```

Any advice how I can get my system to recognise the wireless device?

Thanks.

PS: I found similar threads by using the search function but none of them provided a solution, so I'm opening a new one.

---

### Post by hammerhai on 2007-08-09
No one? Or did I miss to specify some essential details necessary to solve this problem?

---

### Post by alsan on 2008-07-07
Hi,

I get the exactly problem with my HP Compaq 6515b notebook. Do you or anyone got the solution?

---

### Post by Ptero-4 on 2008-07-07
It might seem weird. But can you post your lsusb. I ask because my laptop have a realtek 8187b internal USB card (a weird thing which sits inside the computer but hooks straight to the USB chipset) and I though that maybe your broadcom is also like that.

---

### Post by hammerhai on 2008-07-08
Unfortunately I've never been able to solve this issue. The card also doesn't appear with lsusb. I finally bought myself a PCMCIA wireless card instead...

---

