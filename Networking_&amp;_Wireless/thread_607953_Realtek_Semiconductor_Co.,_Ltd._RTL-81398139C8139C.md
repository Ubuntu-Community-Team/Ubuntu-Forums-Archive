---
title: "Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+"
date: 2007-11-09
forum: Networking &amp; Wireless
---

### Post by carlinuxlearner on 2007-11-09
I installed Ubuntu 7.10 on this laptop, but it would NOT detect the wired network card during the installation, so now that it's installed the little network icon on the top bar says it didn't detect any network interfaces, I don't know how to get it working, the network device is 
"00:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)" 
any help would be greatly appreciated.

C@RL

I've been looking around but can't find any way to get it working. When I execute "sudo modprobe 8139too" nothing happens, and the same with "sudo modprobe 8139cp"

---

### Post by noob12 on 2007-11-09
Does the interface show up in these commands?

```

lspci -nn

sudo lshw -C network

ifconfig -a

```

Check whether you have a link detected from the output of this command

```

sudo ethtool eth0

```

---

### Post by carlinuxlearner on 2007-11-09
lspci -nn

00:04.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)

sudo lshw -C network
"[sudo] password for carl:
  *-network UNCLAIMED     
       description: Ethernet controller
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 4
       bus info: pci@0000:00:04.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 maxlatency=64 mingnt=32"

ifconfig -a

"lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)"

sudo ethtool eth0

"Settings for eth0:
Cannot get device settings: No such device
Cannot get wake-on-lan settings: No such device
Cannot get message level: No such device
Cannot get link status: No such device
No data available"

That's what it gave me.

C@RL

---

### Post by noob12 on 2007-11-09
OK.  The card is detected but the driver had some trouble claiming it.  Check the output of the command **dmesg** right after an initial boot.  If you can post the output it may help diagnosis.

Have you tried booting with the option **pci=noacpi** ?

---

### Post by carlinuxlearner on 2007-11-09
Heres what I got. (I have no idea what it means)

> 
carl@carlubuntulappy:~$ dmesg
[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000ec800 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000177f0000 (usable)
[    0.000000]  BIOS-e820: 00000000177f0000 - 00000000177ffc00 (ACPI data)
[    0.000000]  BIOS-e820: 00000000177ffc00 - 0000000017800000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fffc0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 375MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 96240) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    96240
[    0.000000]   HighMem     96240 ->    96240
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    96240
[    0.000000] On node 0 totalpages: 96240
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 719 pages used for memmap
[    0.000000]   Normal zone: 91425 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7600 checksum 0
[    0.000000] ACPI: RSDP 000F7600, 0014 (r0 KDST  )
[    0.000000] ACPI: RSDT 177FCCC7, 0028 (r1 KDST   SUMO            1 PTL         0)
[    0.000000] ACPI: FACP 177FFB8C, 0074 (r1 KDST   SUMO            1 PTL     F4240)
[    0.000000] ACPI: DSDT 177FCCEF, 2E9D (r1   KDST     SUMO        1 MSFT  100000B)
[    0.000000] ACPI: FACS 177FFFC0, 0040
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 17800000:e87c0000)
[    0.000000] Built 1 zonelists.  Total pages: 95489
[    0.000000] Kernel command line: root=UUID=1266254f-a576-4351-9958-1616b8bf4bfb ro quiet splash force_addr=0xaddr
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffd000 (012fd000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 797.015 MHz processor.
[   60.808860] Console: colour VGA+ 80x25
[   60.810732] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   60.813581] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   60.879829] Memory: 369676k/384960k available (2015k kernel code, 14636k reserved, 916k data, 364k init, 0k highmem)
[   60.879859] virtual kernel memory layout:
[   60.879862]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   60.879866]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   60.879870]     vmalloc : 0xd8000000 - 0xff7fe000   ( 631 MB)
[   60.879874]     lowmem  : 0xc0000000 - 0xd77f0000   ( 375 MB)
[   60.879878]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   60.879881]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   60.879885]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   60.879894] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   60.880018] SLUB: Genslabs=22, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   60.960025] Calibrating delay using timer specific routine.. 1595.60 BogoMIPS (lpj=3191218)
[   60.960132] Security Framework v1.0.0 initialized
[   60.960171] SELinux:  Disabled at boot.
[   60.960221] Mount-cache hash table entries: 512
[   60.960708] CPU: After generic identify, caps: 0387f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   60.960742] CPU: L1 I cache: 16K, L1 D cache: 16K
[   60.960749] CPU: L2 cache: 256K
[   60.960760] CPU serial number disabled.
[   60.960769] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[   60.960804] Compat vDSO mapped to ffffe000.
[   60.960858] Checking 'hlt' instruction... OK.
[   60.976371] SMP alternatives: switching to UP code
[   60.977092] Freeing SMP alternatives: 11k freed
[   60.978130] Early unpacking initramfs... done
[   61.996755] ACPI: Core revision 20070126
[   61.997242] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   62.001046] ACPI: setting ELCR to 0200 (from 0e20)
[   62.007194] CPU0: Intel Pentium III (Coppermine) stepping 03
[   62.007216] SMP motherboard not detected.
[   62.007224] Local APIC not detected. Using dummy APIC emulation.
[   62.007419] Brought up 1 CPUs
[   62.008031] Booting paravirtualized kernel on bare hardware
[   62.008253] Time:  2:54:08  Date: 10/07/107
[   62.008394] NET: Registered protocol family 16
[   62.008887] EISA bus registered
[   62.008930] ACPI: bus type pci registered
[   62.050069] PCI: PCI BIOS revision 2.10 entry at 0xfd8ce, last bus=1
[   62.050077] PCI: Using configuration type 1
[   62.050083] Setting up standard PCI resources
[   62.069239] ACPI: EC: Look up EC in DSDT
[   62.123946] ACPI: EC: GPE=0x06, ports=0x66, 0x62
[   62.125638] ACPI: Interpreter enabled
[   62.125649] ACPI: (supports S0 S1 S4 S5)
[   62.125688] ACPI: Using PIC for interrupt routing
[   62.215084] ACPI: EC: GPE=0x06, ports=0x66, 0x62
[   62.215282] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   62.215307] PCI: Probing PCI hardware (bus 00)
[   62.215901] PCI quirk: region 8000-803f claimed by ali7101 ACPI
[   62.215911] PCI quirk: region 8040-805f claimed by ali7101 SMB
[   62.216453] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   62.220111] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 7 *9 10 11 12)
[   62.220418] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 7 9 10 11 12) *0, disabled.
[   62.220705] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 7 9 10 11 12) *5
[   62.220994] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 7 9 10 11 12) *0, disabled.
[   62.221282] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 7 9 10 11 12) *0, disabled.
[   62.221569] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 7 9 10 11 12) *0, disabled.
[   62.221858] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 7 9 10 11 12) *0, disabled.
[   62.222148] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 7 9 *10 11 12)
[   62.222437] ACPI: PCI Interrupt Link [LNKU] (IRQs 3 4 7 9 10 *11 12)
[   62.222865] ACPI: Power Resource [PFAN] (off)
[   62.222887] Linux Plug and Play Support v0.97 (c) Adam Belay
[   62.222931] pnp: PnP ACPI init
[   62.222973] ACPI: bus type pnp registered
[   62.328739] pnp: PnP ACPI: found 11 devices
[   62.328757] ACPI: ACPI bus type pnp unregistered
[   62.328774] PnPBIOS: Disabled by ACPI PNP
[   62.329048] PCI: Using ACPI for IRQ routing
[   62.329061] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   62.330654] NET: Registered protocol family 8
[   62.330661] NET: Registered protocol family 20
[   62.331002] pnp: 00:07: ioport range 0x3810-0x381f has been reserved
[   62.331012] pnp: 00:07: ioport range 0x4d0-0x4d1 has been reserved
[   62.331020] pnp: 00:07: ioport range 0x8000-0x805f could not be reserved
[   62.331029] pnp: 00:07: ioport range 0x1000-0x10ef has been reserved
[   62.331039] pnp: 00:07: iomem range 0xfffc0000-0xffffffff could not be reserved
[   62.331324] Time: tsc clocksource has been installed.
[   62.362218] PCI: Bridge: 0000:00:01.0
[   62.362227]   IO window: disabled.
[   62.362236]   MEM window: ee900000-efffffff
[   62.362245]   PREFETCH window: 28000000-280fffff
[   62.362257] PCI: Bus 2, cardbus bridge: 0000:00:03.0
[   62.362264]   IO window: 00001c00-00001cff
[   62.362272]   IO window: 00002000-000020ff
[   62.362280]   PREFETCH window: 20000000-23ffffff
[   62.362287]   MEM window: 24000000-27ffffff
[   62.362315] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   62.363032] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[   62.363044] PCI: setting IRQ 11 as level-triggered
[   62.363052] ACPI: PCI Interrupt 0000:00:03.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[   62.363065] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   62.363125] NET: Registered protocol family 2
[   62.399538] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   62.399802] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[   62.401433] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   62.402915] TCP: Hash tables configured (established 16384 bind 16384)
[   62.402926] TCP reno registered
[   62.412079] checking if image is initramfs...<6>Switched to high resolution mode on CPU 0
[   63.166278]  it is
[   64.246392] Freeing initrd memory: 7347k freed
[   64.248049] audit: initializing netlink socket (disabled)
[   64.248117] audit(1194404049.908:1): initialized
[   64.255856] VFS: Disk quotas dquot_6.5.1
[   64.256170] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   64.256682] io scheduler noop registered
[   64.256694] io scheduler anticipatory registered
[   64.256700] io scheduler deadline registered
[   64.256780] io scheduler cfq registered (default)
[   64.256888] Activating ISA DMA hang workarounds.
[   64.256907] Boot video device is 0000:01:00.0
[   64.257608] isapnp: Scanning for PnP cards...
[   64.612524] isapnp: No Plug & Play device found
[   64.719770] Real Time Clock Driver v1.12ac
[   64.720114] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   64.720357] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   64.723378] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   64.726105] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   64.726908] input: Macintosh mouse button emulation as /class/input/input0
[   64.727180] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   64.729327] serio: i8042 KBD port at 0x60,0x64 irq 1
[   64.729345] serio: i8042 AUX port at 0x60,0x64 irq 12
[   64.729951] mice: PS/2 mouse device common for all mice
[   64.730367] EISA: Probing bus 0 at eisa.0
[   64.730395] Cannot allocate resource for EISA slot 1
[   64.730403] Cannot allocate resource for EISA slot 2
[   64.730410] Cannot allocate resource for EISA slot 3
[   64.730441] Cannot allocate resource for EISA slot 8
[   64.730446] EISA: Detected 0 cards.
[   64.730810] TCP cubic registered
[   64.730875] NET: Registered protocol family 1
[   64.730973] Using IPI No-Shortcut mode
[   64.731550]   Magic number: 15:654:914
[   64.731828]   hash matches device ptywd
[   64.734503] Freeing unused kernel memory: 364k freed
[   64.809865] input: AT Translated Set 2 keyboard as /class/input/input1
[   66.818536] AppArmor: AppArmor initialized<5>audit(1194404052.408:2):  type=1505 info="AppArmor initialized" pid=1176
[   66.850516] fuse init (API version 7.8)
[   66.870107] Failure registering capabilities with primary security module.
[   66.899806] ACPI: Transitioning device [FAN] to D3
[   66.899820] ACPI: Transitioning device [FAN] to D3
[   66.899834] ACPI: Fan [FAN] (off)
[   66.920298] ACPI: Processor [CPU0] (supports 8 throttling states)
[   66.932527] ACPI: Thermal Zone [THRM] (59 C)
[   69.455771] usbcore: registered new interface driver usbfs
[   69.455865] usbcore: registered new interface driver hub
[   69.455949] usbcore: registered new device driver usb
[   69.460405] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   69.461230] ACPI: PCI Interrupt Link [LNKU] enabled at IRQ 11
[   69.461242] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKU] -> GSI 11 (level, low) -> IRQ 11
[   69.461292] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   69.461830] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[   69.461889] ohci_hcd 0000:00:02.0: irq 11, io mem 0xee800000
[   69.550266] usb usb1: configuration #1 chosen from 1 choice
[   69.550373] hub 1-0:1.0: USB hub found
[   69.550479] hub 1-0:1.0: 2 ports detected
[   69.670488] SCSI subsystem initialized
[   69.697360] libata version 2.21 loaded.
[   69.870868] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   69.870893] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   69.874939] ALI15X3: IDE controller at PCI slot 0000:00:0f.0
[   69.875002] ACPI: Unable to derive IRQ for device 0000:00:0f.0
[   69.875009] ACPI: PCI Interrupt 0000:00:0f.0[A]: no GSI
[   69.875037] ALI15X3: chipset revision 195
[   69.875044] ALI15X3: not 100% native mode: will probe irqs later
[   69.875089]     ide0: BM-DMA at 0x1800-0x1807, BIOS settings: hda:DMA, hdb:pio
[   69.875131]     ide1: BM-DMA at 0x1808-0x180f, BIOS settings: hdc:DMA, hdd:pio
[   69.875158] Probing IDE interface ide0...
[   70.011824] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   70.174187] Floppy drive(s): fd0 is 1.44M
[   70.252498] FDC 0 is a post-1991 82077
[   70.254312] hda: TOSHIBA MK3018GAS, ATA DISK drive
[   70.925553] hda: host side 80-wire cable detection failed, limiting max speed to UDMA33
[   70.925576] hda: selected mode 0x42
[   70.925730] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   71.317656] Probing IDE interface ide1...
[   72.053055] hdc: TOSHIBA DVD-ROM SD-C2502, ATAPI CD/DVD-ROM drive
[   72.724327] hdc: selected mode 0x42
[   72.765909] ide1 at 0x170-0x177,0x376 on irq 15
[   72.768331] 8139cp 0000:00:04.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   72.768350] 8139cp 0000:00:04.0: Try the "8139too" driver instead.
[   72.778629] 8139too Fast Ethernet driver 0.9.28
[   72.781438] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[   72.781463] PCI: setting IRQ 10 as level-triggered
[   72.781471] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[   72.781499] PCI: Unable to reserve I/O region #1:100@1000 for device 0000:00:04.0
[   72.781510] Trying to free nonexistent resource <0000000000001000-00000000000010ff>
[   72.781524] Trying to free nonexistent resource <00000000ee802000-00000000ee8020ff>
[   72.781546] 8139too: probe of 0000:00:04.0 failed with error -16
[   72.818033] hda: max request size: 128KiB
[   72.855250] hda: 58605120 sectors (30005 MB), CHS=58140/16/63, UDMA(33)
[   72.855417] hda: cache flushes supported
[   72.855666]  hda: hda1 hda2
[   73.016830] hdc: ATAPI 24X DVD-ROM drive, 128kB Cache, UDMA(33)
[   73.016866] Uniform CD-ROM driver Revision: 3.20
[   73.538860] Attempting manual resume
[   73.538877] swsusp: Resume From Partition 3:2
[   73.538882] PM: Checking swsusp image.
[   73.565018] PM: Resume from disk failed.
[   73.685531] kjournald starting.  Commit interval 5 seconds
[   73.685588] EXT3-fs: mounted filesystem with ordered data mode.
[   79.174139] floppy0: unexpected interrupt 
[   79.174237] floppy0: sensei repl[0]=c0 repl[1]=0 
[   79.174294] floppy0: sensei repl[0]=80 
[   91.225833] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   91.233745] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   91.262860] Yenta: CardBus bridge found at 0000:00:03.0 [168f:0001]
[   91.262902] Yenta: Enabling burst memory read transactions
[   91.262910] Yenta: Using CSCINT to route CSC interrupts to PCI
[   91.262916] Yenta: Routing CardBus interrupts to PCI
[   91.262924] Yenta TI: socket 0000:00:03.0, mfunc 0x01221c72, devctl 0x66
[   91.284711] Linux agpgart interface v0.102 (c) Dave Jones
[   91.492303] Yenta: ISA IRQ mask 0x04b8, PCI irq 11
[   91.492318] Socket status: 30000006
[   91.511047] agpgart: Detected ALi M1632 chipset
[   91.518745] agpgart: AGP aperture is 64M @ 0xf0000000
[   93.634813] input: PC Speaker as /class/input/input2
[   93.825411] Synaptics Touchpad, model: 1, fw: 4.1, id: 0x848a1, caps: 0x0/0x0
[   93.859293] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   93.955547] parport_pc 00:08: reported by Plug and Play ACPI
[   93.955661] parport0: PC-style at 0x378 (0x778), irq 7, dma 0 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   94.417555] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 10
[   94.417576] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LNKH] -> GSI 10 (level, low) -> IRQ 10
[   94.598618] cs: IO port probe 0x100-0x3af: excluding 0x200-0x207 0x220-0x22f 0x330-0x337 0x388-0x38f
[   94.601227] cs: IO port probe 0x3e0-0x4ff: excluding 0x408-0x40f 0x480-0x48f
[   94.602417] cs: IO port probe 0x820-0x8ff: clean.
[   94.603397] cs: IO port probe 0xc00-0xcf7: clean.
[   94.604646] cs: IO port probe 0xa00-0xaff: clean.
[   96.560184] MC'97 1 converters and GPIO not ready (0xf000)
[   97.702134] lp0: using parport0 (interrupt-driven).
[   97.862345] Adding 1108476k swap on /dev/hda2.  Priority:-1 extents:1 across:1108476k
[  192.075939] EXT3 FS on hda1, internal journal
[  196.883123] ACPI: Battery Slot [BAT1] (battery absent)
[  196.932632] ACPI: AC Adapter [ACAD] (on-line)
[  196.978243] No dock devices found.
[  197.584045] input: Power Button (FF) as /class/input/input4
[  197.585111] ACPI: Power Button (FF) [PWRF]
[  197.612052] input: Lid Switch as /class/input/input5
[  197.613234] ACPI: Lid Switch [LID]
[  197.628040] input: Sleep Button (CM) as /class/input/input6
[  197.629235] ACPI: Sleep Button (CM) [SLPB]
[  202.493225] ppdev: user-space parallel port driver
[  204.118168] audit(1194404190.456:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4517 profile="/usr/sbin/cupsd"
[  204.377805] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  204.377831] apm: overridden by ACPI.
[  205.083044] Failure registering capabilities with primary security module.
[  205.720128] Bluetooth: Core ver 2.11
[  205.721160] NET: Registered protocol family 31
[  205.721173] Bluetooth: HCI device and connection manager initialized
[  205.721185] Bluetooth: HCI socket layer initialized
[  205.815309] Bluetooth: L2CAP ver 2.8
[  205.815330] Bluetooth: L2CAP socket layer initialized
[  205.947094] Bluetooth: RFCOMM socket layer initialized
[  205.947394] Bluetooth: RFCOMM TTY layer initialized
[  205.947403] Bluetooth: RFCOMM ver 1.8
carl@carlubuntulappy:~$ 


C@RL

Tried "pci=noacpi" didn't do any thing.

::EDIT

Can some one PLEASE help me out, I've been trying to get this working for weeks!

---

### Post by noob12 on 2007-11-10
```

Kernel command line: root=UUID=1266254f-a576-4351-9958-1616b8bf4bfb ro quiet splash force_addr=0xaddr

```

If you had seen some message about using the **force_addr** flag the 0xaddr part wan't meant to be taken literally, it was meant to indicate that you should replace the **0xaddr** with a hexadecimal base address.  If you didn't get a suggestion from the kernel to use that, I'd suggest removing it.

I'm not sure that this is causing your problem, but this is where the 8139too driver is failing to claim the device...
```

[ 72.778629] 8139too Fast Ethernet driver 0.9.28
[ 72.781438] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[ 72.781463] PCI: setting IRQ 10 as level-triggered
[ 72.781471] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[ 72.781499] PCI: Unable to reserve I/O region #1:100@1000 for device 0000:00:04.0
[ 72.781510] Trying to free nonexistent resource <0000000000001000-00000000000010ff>
[ 72.781524] Trying to free nonexistent resource <00000000ee802000-00000000ee8020ff>
[ 72.781546] 8139too: probe of 0000:00:04.0 failed with error -16

```

After you boot check the output of
```

dmesg | grep 'Kernel command line'

```
to verify that your boot flags are as you expect.

---

### Post by carlinuxlearner on 2007-11-10
Ah, yes I did see that "force_addr=0xaddr" and NO I didn't put that in, and I did NOT know that to use it, you are supposed to put in a hexadecimal number, so I'm not sure why it's there. I did use that when I booted off the Live CD to install, because it suggested it, so maybe it put it in there because of that? I will remove it.

C@RL

---

### Post by carlinuxlearner on 2007-11-10
Ok it's good
"carl@carlubuntulappy:~$ dmesg | grep 'Kernel command line'
[    0.000000] Kernel command line: root=UUID=1266254f-a576-4351-9958-1616b8bf4bfb ro quiet splash
carl@carlubuntulappy:~$ "

So what do I do now?

C@RL

---

### Post by noob12 on 2007-11-11
What is the situation now when the 8139too driver loads?  Do you see the same errors after 8139too loads in the dmesg output on boot?  Is the device getting claimed now (see **sudo lshw -C network**) ?

---

### Post by carlinuxlearner on 2007-11-11
The 8139too has the same errors. The device is still not getting claimed.

C@RL

---

### Post by noob12 on 2007-11-13
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/22575](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/22575) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				OK.    There is probably a combination of kernel boot flags that will work to get most of the devices running properly.   I'm not sure what it would be though.  Perhaps another forum reader can suggest it, here or on the Intstallation and Upgrades forum or on [http://launchpad.net/ubuntu](http://launchpad.net/ubuntu).

This might be related to this bug report: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/22575](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/22575)

It looks like the range that gets reported in the error during the loading of 8139too in your dmesg output is one of the ranges that was allocated to pnp earlier in your dmesg output, and the error is similar.  The responder there suggests trying the boot flags:  **noisapnp**  **pnpacpi=off**  **pnpbios=off**  but note that the reporter claims that this didn't work for him.  Still, you might want to try those.

You might also try to post a new bug on launchpad and get help from a kernel guru there.

---

