---
title: "Lost internet connection after update"
date: 2008-06-29
forum: Networking &amp; Wireless
---

### Post by drinkymilk on 2008-06-29
I'm running Ubuntu 8.04 Hardy, updated from 7.10. I have virtual box installed, and after I upgraded to hardy it hasn't been working properly. So I think I made a mistake when I installed vbox-modules-rt. Vbox still wasn't working until it released updates which I installed through Ubuntu's update manager. After I restarted the computer (which is a Toshiba Satellite A55-S1066 in case thats useful info) it won't wirelessly, or through hardwire, connect to the internet. Also Compize, AWN, and the Screenlets programs all don't work. So I hurriedly uninstalled Vbox and all it's components, in hopes that it would remedy the problem.

After I restarted again nothing has changed.

Thanks for any help you can give me

~tim

---

### Post by pytheas22 on 2008-06-29
I don't know how Virtual Box could be affecting all of those things.  But to clarify: after you upgraded to Hardy, Internet and compiz worked alright, and it was only *after* installing vbox-modules-rt that you started having problems?

The best place I can think to look to figure out what's wrong is dmesg.  Open a terminal and type:
```

dmesg
```

and please post the output here.  If it's hard to do that since you don't have Internet on the Ubuntu machine at the moment, remember that you could copy and paste the output into a text file and then transfer that file (via a USB driver for instance) to a computer where you can copy and paste into this forum.

---

### Post by drinkymilk on 2008-06-29
well it wasn't after the install of vbox-rt it was after I updated, and it was a very large update. so it might not have been vbox at all. I guess I just freaked out and blamed the newest thing i installed.

well here is what I got after dmesg. I don't think I got all of it because It doesn't show the tim@desktop$: at the top


```
[20952.522957]  [<c0105403>] common_interrupt+0x23/0x30
[20952.522966]  [<c017f186>] find_vma+0x36/0x70
[20952.522971]  [<c031364f>] do_page_fault+0x13f/0x730
[20952.522978]  [<c019206f>] vfs_read+0x15f/0x170
[20952.522984]  [<c0145cd4>] do_gettimeofday+0x34/0xe0
[20952.522996]  [<c0313510>] do_page_fault+0x0/0x730
[20952.523000]  [<c0311e42>] error_code+0x72/0x80
[20952.523007]  [<c0310000>] schedule+0x110/0x5e0
[20952.523017]  =======================
[20952.523019] Mem-info:
[20952.523020] DMA per-cpu:
[20952.523023] CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
[20952.523026] Normal per-cpu:
[20952.523029] CPU    0: Hot: hi:  186, btch:  31 usd: 156   Cold: hi:   62, btch:  15 usd:  57
[20952.523034] Active:57631 inactive:56952 dirty:0 writeback:0 unstable:0
[20952.523035]  free:1496 slab:2443 mapped:3 pagetables:986 bounce:0
[20952.523040] DMA free:1988kB min:88kB low:108kB high:132kB active:5992kB inactive:4308kB present:16256kB pages_scanned:17555 all_unreclaimable? yes
[20952.523044] lowmem_reserve[]: 0 475 475 475
[20952.523049] Normal free:3996kB min:2744kB low:3428kB high:4116kB active:224532kB inactive:223500kB present:486920kB pages_scanned:869449 all_unreclaimable? yes
[20952.523053] lowmem_reserve[]: 0 0 0 0
[20952.523057] DMA: 3*4kB 1*8kB 1*16kB 1*32kB 0*64kB 1*128kB 1*256kB 1*512kB 1*1024kB 0*2048kB 0*4096kB = 1988kB
[20952.523067] Normal: 297*4kB 17*8kB 3*16kB 0*32kB 1*64kB 0*128kB 0*256kB 1*512kB 0*1024kB 1*2048kB 0*4096kB = 3996kB
[20952.523077] Swap cache: add 405609, delete 405601, find 843347/847407, race 0+0
[20952.523080] Free swap  = 0kB
[20952.523082] Total swap = 1461872kB
[20952.523084] Free swap:            0kB
[20952.526373] 126784 pages of RAM
[20952.526375] 0 pages of HIGHMEM
[20952.526377] 2109 reserved pages
[20952.526378] 3400 pages shared
[20952.526380] 8 pages swap cached
[20952.526382] 0 pages dirty
[20952.526383] 0 pages writeback
[20952.526385] 3 pages mapped
[20952.526386] 2443 pages slab
[20952.526388] 986 pages pagetables
[20952.526391] Out of memory: kill process 5498 (python) score 54038 or a child
[20952.526427] Killed process 5498 (python)
tim@tim-laptop:~$ 
tim@tim-laptop:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-virtual (buildd@vernadsky) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 4 17:57:54 UTC 2008 (Ubuntu 2.6.24-19.33-virtual)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 00000000000eee00 (reserved)
[    0.000000]  BIOS-e820: 00000000000eee00 - 00000000000ef000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000000ef000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001ef40000 (usable)
[    0.000000]  BIOS-e820: 000000001ef40000 - 000000001ef50000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001ef50000 - 000000001f000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec10000 - 00000000fec20000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000fedc0000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb80000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 495MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 126784) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   126784
[    0.000000]   HighMem    126784 ->   126784
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   126784
[    0.000000] On node 0 totalpages: 126784
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 958 pages used for memmap
[    0.000000]   Normal zone: 121730 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F0180 checksum 0
[    0.000000] ACPI: RSDP 000F0180, 0014 (r0 TOSHIB)
[    0.000000] ACPI: RSDT 1EF40000, 0038 (r1 TOSHIB 750        970814 TASM  4010000)
[    0.000000] ACPI: FACP 1EF40060, 0084 (r2 TOSHIB 750      20030101 TASM  4010000)
[    0.000000] ACPI: DSDT 1EF40118, 44B9 (r1 TOSHIB A0015    20040426 MSFT  100000E)
[    0.000000] ACPI: FACS 000EEE00, 0040
[    0.000000] ACPI: SSDT 1EF445D1, 0231 (r1 TOSHIB LNK10SS  20040226 MSFT  100000E)
[    0.000000] ACPI: DBGP 1EF400E4, 0034 (r1 TOSHIB 750        970814 TASM  4010000)
[    0.000000] ACPI: BOOT 1EF40038, 0028 (r1 TOSHIB 750        970814 TASM  4010000)
[    0.000000] ACPI: SSDT 1EF44802, 06C4 (r1 TOSHIB A0015    20040226 MSFT  100000E)
[    0.000000] ACPI: DMI detected: Toshiba
[    0.000000] ACPI: PM-Timer IO Port: 0xd808
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 1f000000:dfc10000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 00000000000ee000
[    0.000000] swsusp: Registered nosave memory region: 00000000000ee000 - 00000000000ef000
[    0.000000] swsusp: Registered nosave memory region: 00000000000ef000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 125794
[    0.000000] Kernel command line: root=UUID=04a51a89-1ab0-4d22-8ae7-b3a69e1655fe ro quiet splash
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffb000 (013ed000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 1496.285 MHz processor.
[  183.931567] Console: colour VGA+ 80x25
[  183.931572] console [tty0] enabled
[  183.931759] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[  183.932006] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[  183.947899] Memory: 493884k/507136k available (2134k kernel code, 12656k reserved, 953k data, 272k init, 0k highmem)
[  183.947909] virtual kernel memory layout:
[  183.947910]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[  183.947912]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[  183.947913]     vmalloc : 0xdf800000 - 0xff7fe000   ( 511 MB)
[  183.947915]     lowmem  : 0xc0000000 - 0xdef40000   ( 495 MB)
[  183.947916]       .init : 0xc0409000 - 0xc044d000   ( 272 kB)
[  183.947918]       .data : 0xc03159ba - 0xc0403e04   ( 953 kB)
[  183.947919]       .text : 0xc0100000 - 0xc03159ba   (2134 kB)
[  183.947923] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[  183.947968] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[  184.027950] Calibrating delay using timer specific routine.. 2994.64 BogoMIPS (lpj=5989288)
[  184.027980] Security Framework initialized
[  184.027991] SELinux:  Disabled at boot.
[  184.028007] AppArmor: AppArmor initialized
[  184.028012] Failure registering capabilities with primary security module.
[  184.028022] Mount-cache hash table entries: 512
[  184.028170] Initializing cgroup subsys ns
[  184.028176] Initializing cgroup subsys cpuacct
[  184.028188] CPU: After generic identify, caps: afe9f9ff 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[  184.028200] CPU: L1 I cache: 32K, L1 D cache: 32K
[  184.028203] CPU: L2 cache: 1024K
[  184.028206] CPU: After all inits, caps: afe9f9ff 00000000 00000000 00002040 00000000 00000000 00000000 00000000
[  184.028216] Compat vDSO mapped to ffffe000.
[  184.028231] Checking 'hlt' instruction... OK.
[  184.044370] SMP alternatives: switching to UP code
[  184.046530] Freeing SMP alternatives: 11k freed
[  184.046657] Early unpacking initramfs... done
[  184.289777] ACPI: Core revision 20070126
[  184.289853] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[  184.291879] ACPI: setting ELCR to 0200 (from 0e00)
[  184.292359] CPU0: Intel(R) Celeron(R) M processor         1.50GHz stepping 08
[  184.292366] SMP motherboard not detected.
[  184.292369] Local APIC not detected. Using dummy APIC emulation.
[  184.292420] Brought up 1 CPUs
[  184.292439] CPU0 attaching sched-domain:
[  184.292442]  domain 0: span 01
[  184.292444]   groups: 01
[  184.292643] net_namespace: 64 bytes
[  184.292653] Booting paravirtualized kernel on bare hardware
[  184.293161] Time: 22:58:06  Date: 06/21/08
[  184.293194] NET: Registered protocol family 16
[  184.293427] ACPI: bus type pci registered
[  184.293654] PCI: PCI BIOS revision 2.10 entry at 0xfd480, last bus=3
[  184.293657] PCI: Using configuration type 1
[  184.293667] Setting up standard PCI resources
[  184.296425] ACPI: EC: Look up EC in DSDT
[  184.299520] ACPI: Interpreter enabled
[  184.299523] ACPI: (supports S0 S3 S4 S5)
[  184.299537] ACPI: Using PIC for interrupt routing
[  184.303911] ACPI: PCI Root Bridge [PCI0] (0000:00)
[  184.304416] PCI quirk: region d800-d87f claimed by ICH4 ACPI/GPIO/TCO
[  184.304420] PCI quirk: region eec0-eeff claimed by ICH4 GPIO
[  184.304729] PCI: Transparent bridge - 0000:00:1e.0
[  184.304793] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[  184.304849] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[  184.306687] ACPI: PCI Interrupt Link [LNKA] (IRQs *10)
[  184.306828] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *11)
[  184.306966] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *11)
[  184.307104] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *11)
[  184.307241] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *11)
[  184.307382] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *11)
[  184.307519] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *11)
[  184.307656] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *11)
[  184.307875] ACPI: Power Resource [PFAN] (off)
[  184.307929] Linux Plug and Play Support v0.97 (c) Adam Belay
[  184.307963] pnp: PnP ACPI init
[  184.307972] ACPI: bus type pnp registered
[  184.309645] pnpacpi: exceeded the max number of IO resources: 40 
[  184.310036] pnp: PnP ACPI: found 9 devices
[  184.310038] ACPI: ACPI bus type pnp unregistered
[  184.310201] PCI: Using ACPI for IRQ routing
[  184.310203] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[  184.310216] PCI: Cannot allocate resource region 4 of device 0000:00:1d.0
[  184.310220] PCI: Cannot allocate resource region 4 of device 0000:00:1d.1
[  184.310224] PCI: Cannot allocate resource region 4 of device 0000:00:1d.2
[  184.319895] AppArmor: AppArmor Filesystem Enabled
[  184.323803] Time: tsc clocksource has been installed.
[  184.331842] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[  184.331846] system 00:00: iomem range 0xe0000-0xeffff could not be reserved
[  184.331850] system 00:00: iomem range 0xf0000-0xfffff could not be reserved
[  184.331853] system 00:00: iomem range 0x100000-0x1ef3ffff could not be reserved
[  184.331857] system 00:00: iomem range 0x1ef40000-0x1ef4ffff could not be reserved
[  184.331860] system 00:00: iomem range 0x1ef50000-0x1effffff could not be reserved
[  184.331864] system 00:00: iomem range 0xfec10000-0xfec1ffff could not be reserved
[  184.331868] system 00:00: iomem range 0xfeda0000-0xfedbffff could not be reserved
[  184.331871] system 00:00: iomem range 0xffb80000-0xffbfffff could not be reserved
[  184.331875] system 00:00: iomem range 0xfff00000-0xffffffff could not be reserved
[  184.331885] system 00:08: ioport range 0x1e0-0x1e7 has been reserved
[  184.331888] system 00:08: ioport range 0x480-0x48f has been reserved
[  184.331891] system 00:08: ioport range 0x680-0x6ff has been reserved
[  184.331894] system 00:08: ioport range 0xd800-0xd87f has been reserved
[  184.331897] system 00:08: ioport range 0xd880-0xd89f has been reserved
[  184.331901] system 00:08: ioport range 0xd8a0-0xd8bf has been reserved
[  184.331904] system 00:08: ioport range 0xe000-0xe07f has been reserved
[  184.331907] system 00:08: ioport range 0xe080-0xe0ff has been reserved
[  184.331911] system 00:08: ioport range 0xe400-0xe47f has been reserved
[  184.331914] system 00:08: ioport range 0xe480-0xe4ff has been reserved
[  184.331917] system 00:08: ioport range 0xe800-0xe87f has been reserved
[  184.331920] system 00:08: ioport range 0xe880-0xe8ff has been reserved
[  184.331923] system 00:08: ioport range 0xec00-0xec7f has been reserved
[  184.331927] system 00:08: ioport range 0xec80-0xecff has been reserved
[  184.331930] system 00:08: ioport range 0xeeac-0xeeac has been reserved
[  184.331933] system 00:08: ioport range 0xeeb0-0xeebf has been reserved
[  184.331936] system 00:08: ioport range 0xeec0-0xeeff has been reserved
[  184.362397] PCI: Bus 2, cardbus bridge: 0000:01:0b.0
[  184.362400]   IO window: 0000c000-0000c0ff
[  184.362404]   IO window: 0000c400-0000c4ff
[  184.362408]   PREFETCH window: 2c000000-2fffffff
[  184.362413]   MEM window: 30000000-33ffffff
[  184.362417] PCI: Bridge: 0000:00:1e.0
[  184.362420]   IO window: c000-cfff
[  184.362424]   MEM window: cff00000-cfffffff
[  184.362428]   PREFETCH window: disabled.
[  184.362441] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[  184.362455] PCI: Enabling device 0000:01:0b.0 (0000 -> 0003)
[  184.362660] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[  184.362663] PCI: setting IRQ 11 as level-triggered
[  184.362667] ACPI: PCI Interrupt 0000:01:0b.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[  184.362684] NET: Registered protocol family 2
[  184.399838] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[  184.400057] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[  184.400183] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[  184.400318] TCP: Hash tables configured (established 16384 bind 16384)
[  184.400321] TCP reno registered
[  184.411913] checking if image is initramfs... it is
[  184.863560] Switched to high resolution mode on CPU 0
[  184.889998] Freeing initrd memory: 4327k freed
[  184.890291] Simple Boot Flag at 0x7c set to 0x1
[  184.890692] audit: initializing netlink socket (disabled)
[  184.890712] audit(1214089086.944:1): initialized
[  184.893116] VFS: Disk quotas dquot_6.5.1
[  184.893215] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[  184.893421] io scheduler noop registered
[  184.893424] io scheduler anticipatory registered
[  184.893426] io scheduler deadline registered
[  184.893440] io scheduler cfq registered (default)
[  184.893461] Boot video device is 0000:00:02.0
[  184.893513] PCI: Firmware left 0000:01:08.0 e100 interrupts enabled, disabling
[  184.928255] Real Time Clock Driver v1.12ac
[  184.928390] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[  184.929115] PCI: Enabling device 0000:00:1f.6 (0000 -> 0001)
[  184.929337] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[  184.929341] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[  184.929352] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[  184.930022] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[  184.930031] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[  184.930036] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[  184.930166] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[  184.935400] serio: i8042 KBD port at 0x60,0x64 irq 1
[  184.935406] serio: i8042 AUX port at 0x60,0x64 irq 12
[  184.935574] mice: PS/2 mouse device common for all mice
[  184.935635] cpuidle: using governor ladder
[  184.935637] cpuidle: using governor menu
[  184.935794] NET: Registered protocol family 1
[  184.935813] Using IPI No-Shortcut mode
[  184.935856] registered taskstats version 1
[  184.935976]   Magic number: 12:355:1008
[  184.935982]   hash matches device ttye7
[  184.935992]   hash matches device ttyba
[  184.936291] Freeing unused kernel memory: 272k freed
[  184.961508] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input0
[  186.127890] fuse init (API version 7.9)
[  186.143413] ACPI: Transitioning device [FAN] to D3
[  186.143418] ACPI: Transitioning device [FAN] to D3
[  186.143423] ACPI: Fan [FAN] (off)
[  186.149306] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[  186.150634] ACPI: Thermal Zone [THRM] (61 C)
[  186.514655] usbcore: registered new interface driver usbfs
[  186.514687] usbcore: registered new interface driver hub
[  186.521799] usbcore: registered new device driver usb
[  186.526816] USB Universal Host Controller Interface driver v3.0
[  186.527161] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
[  186.527165] PCI: setting IRQ 10 as level-triggered
[  186.527169] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[  186.527182] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[  186.527187] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[  186.527646] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[  186.527675] uhci_hcd 0000:00:1d.0: irq 10, io base 0x000018c0
[  186.527833] usb usb1: configuration #1 chosen from 1 choice
[  186.527864] hub 1-0:1.0: USB hub found
[  186.527871] hub 1-0:1.0: 2 ports detected
[  186.574404] SCSI subsystem initialized
[  186.606852] libata version 3.00 loaded.
[  186.630889] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[  186.630897] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[  186.630911] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[  186.630916] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[  186.630945] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[  186.630972] uhci_hcd 0000:00:1d.1: irq 11, io base 0x000018e0
[  186.631103] usb usb2: configuration #1 chosen from 1 choice
[  186.631132] hub 2-0:1.0: USB hub found
[  186.631138] hub 2-0:1.0: 2 ports detected
[  186.734551] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[  186.734567] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[  186.734572] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[  186.734600] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[  186.734624] uhci_hcd 0000:00:1d.2: irq 11, io base 0x00001c00
[  186.734753] usb usb3: configuration #1 chosen from 1 choice
[  186.734780] hub 3-0:1.0: USB hub found
[  186.734787] hub 3-0:1.0: 2 ports detected
[  186.838622] PCI: Enabling device 0000:00:1d.7 (0000 -> 0002)
[  186.838888] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[  186.838892] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
[  186.838909] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[  186.838913] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[  186.838948] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[  186.842846] ehci_hcd 0000:00:1d.7: debug port 1
[  186.842852] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[  186.842861] ehci_hcd 0000:00:1d.7: irq 11, io mem 0x28080000
[  186.858368] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[  186.858526] usb usb4: configuration #1 chosen from 1 choice
[  186.858556] hub 4-0:1.0: USB hub found
[  186.858565] hub 4-0:1.0: 6 ports detected
[  186.962610] ata_piix 0000:00:1f.1: version 2.12
[  186.962638] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[  186.962680] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[  186.963886] scsi0 : ata_piix
[  186.964472] scsi1 : ata_piix
[  186.964977] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[  186.964981] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[  187.126716] ata1.00: ATA-6: HTS541040G9AT00, MB2OA60A, max UDMA/100
[  187.126722] ata1.00: 78140160 sectors, multi 0: LBA48 
[  187.142638] ata1.00: configured for UDMA/100
[  187.618288] ata2.00: ATAPI: UJDA760 DVD/CDRW, 1.00, max UDMA/33
[  187.790171] ata2.00: configured for UDMA/33
[  187.790333] scsi 0:0:0:0: Direct-Access     ATA      HTS541040G9AT00  MB2O PQ: 0 ANSI: 5
[  187.792100] scsi 1:0:0:0: CD-ROM            MATSHITA UJDA760 DVD/CDRW 1.00 PQ: 0 ANSI: 5
[  187.806468] Driver 'sd' needs updating - please use bus_type methods
[  187.806584] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[  187.806599] sd 0:0:0:0: [sda] Write Protect is off
[  187.806602] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  187.806620] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  187.806674] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[  187.806684] sd 0:0:0:0: [sda] Write Protect is off
[  187.806687] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  187.806704] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  187.806709]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[  187.824361]  sda1 sda2 < sda5 >
[  187.843307] sd 0:0:0:0: [sda] Attached SCSI disk
[  187.849450] sd 0:0:0:0: Attached scsi generic sg0 type 0
[  187.849472] sr 1:0:0:0: Attached scsi generic sg1 type 5
[  187.852927] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[  187.852933] Uniform CD-ROM driver Revision: 3.20
[  187.852993] sr 1:0:0:0: Attached scsi CD-ROM sr0
[  188.057835] Attempting manual resume
[  188.057840] swsusp: Resume From Partition 8:5
[  188.057842] PM: Checking swsusp image.
[  188.058042] PM: Resume from disk failed.
[  188.101788] kjournald starting.  Commit interval 5 seconds
[  188.101807] EXT3-fs: mounted filesystem with ordered data mode.
[  196.352796] Clocksource tsc unstable (delta = -403321609 ns)
[  196.356775] Time: acpi_pm clocksource has been installed.
[  196.880557] Linux agpgart interface v0.102
[  196.898275] agpgart: Detected an Intel 855GM Chipset.
[  196.898663] agpgart: Detected 16252K stolen memory.
[  196.907954] agpgart: AGP aperture is 128M @ 0xd8000000
[  196.992582] intel_rng: FWH not detected
[  197.004555] input: PC Speaker as /devices/platform/pcspkr/input/input1
[  197.019009] input: Power Button (FF) as /devices/virtual/input/input2
[  197.032430] ACPI: Power Button (FF) [PWRF]
[  197.032563] input: Lid Switch as /devices/virtual/input/input3
[  197.032645] ACPI: Lid Switch [LID]
[  197.032700] input: Power Button (CM) as /devices/virtual/input/input4
[  197.048421] ACPI: Power Button (CM) [PWRB]
[  197.048588] ACPI: AC Adapter [ADP1] (on-line)
[  197.176120] iTCO_vendor_support: vendor-support=0
[  197.188533] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[  197.188631] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0xd860)
[  197.188666] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[  197.632248] PCI: Enabling device 0000:00:1f.5 (0000 -> 0003)
[  197.632260] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[  197.632287] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[  198.100594] input: PS/2 Generic Mouse as /devices/platform/i8042/serio1/input/input5
[  198.459547] intel8x0_measure_ac97_clock: measured 55453 usecs
[  198.459553] intel8x0: clocking to 48000
[  199.067354] lp: driver loaded but no devices found
[  199.171634] Adding 1461872k swap on /dev/sda5.  Priority:-1 extents:1 across:1461872k
[  199.502144] EXT3 FS on sda1, internal journal
[  200.374845] ip_tables: (C) 2000-2006 Netfilter Core Team
[  202.074639] ppdev: user-space parallel port driver
[  202.260077] audit(1214089106.013:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4503 profile="/usr/sbin/cupsd" namespace="default"
[  202.529511] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[  202.529519] vboxdrv: Successfully done.
[  202.529950] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[  202.529954] vboxdrv: Successfully loaded version 1.5.6_OSE (interface 0x00050002).
[  216.659535] NET: Registered protocol family 10
[  216.660042] lo: Disabled Privacy Extensions
[20952.514845] firefox invoked oom-killer: gfp_mask=0x1201d2, order=0, oomkilladj=0
[20952.514858] Pid: 2284, comm: firefox Not tainted 2.6.24-19-virtual #1
[20952.514881]  [<c01707ba>] oom_kill_process+0x10a/0x120
[20952.514899]  [<c0170c07>] out_of_memory+0x167/0x1a0
[20952.514908]  [<c017307c>] __alloc_pages+0x36c/0x3a0
[20952.514919]  [<c01751fd>] __do_page_cache_readahead+0x11d/0x250
[20952.514924]  [<c016d530>] sync_page+0x0/0x40
[20952.514936]  [<c017571c>] do_page_cache_readahead+0x4c/0x70
[20952.514943]  [<c016fcf4>] filemap_fault+0x2f4/0x420
[20952.514953]  [<c017b101>] __do_fault+0x61/0x420
[20952.514959]  [<c019a6fa>] getname+0xaa/0xe0
[20952.514969]  [<c0120e0d>] kunmap_atomic+0x3d/0xc0
[20952.514975]  [<c017d638>] handle_mm_fault+0x118/0x730
[20952.514987]  [<c031364f>] do_page_fault+0x13f/0x730
[20952.514999]  [<c0313510>] do_page_fault+0x0/0x730
[20952.515003]  [<c0311e42>] error_code+0x72/0x80
[20952.515010]  [<c0310000>] schedule+0x110/0x5e0
[20952.515020]  =======================
[20952.515022] Mem-info:
[20952.515024] DMA per-cpu:
[20952.515027] CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
[20952.515031] Normal per-cpu:
[20952.515034] CPU    0: Hot: hi:  186, btch:  31 usd: 165   Cold: hi:   62, btch:  15 usd:  61
[20952.515038] Active:57623 inactive:56950 dirty:0 writeback:0 unstable:0
[20952.515040]  free:1496 slab:2443 mapped:3 pagetables:986 bounce:0
[20952.515045] DMA free:1988kB min:88kB low:108kB high:132kB active:5992kB inactive:4308kB present:16256kB pages_scanned:17555 all_unreclaimable? yes
[20952.515048] lowmem_reserve[]: 0 475 475 475
[20952.515054] Normal free:3996kB min:2744kB low:3428kB high:4116kB active:224500kB inactive:223492kB present:486920kB pages_scanned:861353 all_unreclaimable? yes
[20952.515058] lowmem_reserve[]: 0 0 0 0
[20952.515062] DMA: 3*4kB 1*8kB 1*16kB 1*32kB 0*64kB 1*128kB 1*256kB 1*512kB 1*1024kB 0*2048kB 0*4096kB = 1988kB
[20952.515071] Normal: 297*4kB 17*8kB 3*16kB 0*32kB 1*64kB 0*128kB 0*256kB 1*512kB 0*1024kB 1*2048kB 0*4096kB = 3996kB
[20952.515083] Swap cache: add 405601, delete 405601, find 843347/847406, race 0+0
[20952.515085] Free swap  = 0kB
[20952.515087] Total swap = 1461872kB
[20952.515089] Free swap:            0kB
[20952.518516] 126784 pages of RAM
[20952.518518] 0 pages of HIGHMEM
[20952.518520] 2109 reserved pages
[20952.518522] 3398 pages shared
[20952.518523] 0 pages swap cached
[20952.518525] 0 pages dirty
[20952.518526] 0 pages writeback
[20952.518528] 3 pages mapped
[20952.518530] 2443 pages slab
[20952.518531] 986 pages pagetables
[20952.518534] Out of memory: kill process 5516 (python) score 216154 or a child
[20952.518571] Killed process 5516 (python)
[20952.522839] python invoked oom-killer: gfp_mask=0x1201d2, order=0, oomkilladj=0
[20952.522847] Pid: 5495, comm: python Not tainted 2.6.24-19-virtual #1
[20952.522867]  [<c01707ba>] oom_kill_process+0x10a/0x120
[20952.522881]  [<c0170c07>] out_of_memory+0x167/0x1a0
[20952.522890]  [<c017307c>] __alloc_pages+0x36c/0x3a0
[20952.522901]  [<c01751fd>] __do_page_cache_readahead+0x11d/0x250
[20952.522906]  [<c016d530>] sync_page+0x0/0x40
[20952.522918]  [<c017571c>] do_page_cache_readahead+0x4c/0x70
[20952.522925]  [<c016fcf4>] filemap_fault+0x2f4/0x420
[20952.522935]  [<c017b101>] __do_fault+0x61/0x420
[20952.522945]  [<c0120e0d>] kunmap_atomic+0x3d/0xc0
[20952.522952]  [<c017d638>] handle_mm_fault+0x118/0x730
[20952.522957]  [<c0105403>] common_interrupt+0x23/0x30
[20952.522966]  [<c017f186>] find_vma+0x36/0x70
[20952.522971]  [<c031364f>] do_page_fault+0x13f/0x730
[20952.522978]  [<c019206f>] vfs_read+0x15f/0x170
[20952.522984]  [<c0145cd4>] do_gettimeofday+0x34/0xe0
[20952.522996]  [<c0313510>] do_page_fault+0x0/0x730
[20952.523000]  [<c0311e42>] error_code+0x72/0x80
[20952.523007]  [<c0310000>] schedule+0x110/0x5e0
[20952.523017]  =======================
[20952.523019] Mem-info:
[20952.523020] DMA per-cpu:
[20952.523023] CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
[20952.523026] Normal per-cpu:
[20952.523029] CPU    0: Hot: hi:  186, btch:  31 usd: 156   Cold: hi:   62, btch:  15 usd:  57
[20952.523034] Active:57631 inactive:56952 dirty:0 writeback:0 unstable:0
[20952.523035]  free:1496 slab:2443 mapped:3 pagetables:986 bounce:0
[20952.523040] DMA free:1988kB min:88kB low:108kB high:132kB active:5992kB inactive:4308kB present:16256kB pages_scanned:17555 all_unreclaimable? yes
[20952.523044] lowmem_reserve[]: 0 475 475 475
[20952.523049] Normal free:3996kB min:2744kB low:3428kB high:4116kB active:224532kB inactive:223500kB present:486920kB pages_scanned:869449 all_unreclaimable? yes
[20952.523053] lowmem_reserve[]: 0 0 0 0
[20952.523057] DMA: 3*4kB 1*8kB 1*16kB 1*32kB 0*64kB 1*128kB 1*256kB 1*512kB 1*1024kB 0*2048kB 0*4096kB = 1988kB
[20952.523067] Normal: 297*4kB 17*8kB 3*16kB 0*32kB 1*64kB 0*128kB 0*256kB 1*512kB 0*1024kB 1*2048kB 0*4096kB = 3996kB
[20952.523077] Swap cache: add 405609, delete 405601, find 843347/847407, race 0+0
[20952.523080] Free swap  = 0kB
[20952.523082] Total swap = 1461872kB
[20952.523084] Free swap:            0kB
[20952.526373] 126784 pages of RAM
[20952.526375] 0 pages of HIGHMEM
[20952.526377] 2109 reserved pages
[20952.526378] 3400 pages shared
[20952.526380] 8 pages swap cached
[20952.526382] 0 pages dirty
[20952.526383] 0 pages writeback
[20952.526385] 3 pages mapped
[20952.526386] 2443 pages slab
[20952.526388] 986 pages pagetables
[20952.526391] Out of memory: kill process 5498 (python) score 54038 or a child
[20952.526427] Killed process 5498 (python)
tim@tim-laptop:~$ 


```

---

### Post by pytheas22 on 2008-06-30
From dmesg it looks like you're running completely out of memory and the system is killing processes as a result.  This would explain why compiz and other things aren't working.

Is there a reason this should be happening?  How much RAM and swap space do you have?  On any decent computer, you should never be getting to the point that every last kilobyte of swap space is tied up.  If you type:
```

top
```

you'll see a list of processes and how memory they're using, among other things.  Is there a process going out of control?

---

### Post by seeker1458 on 2008-06-30
I am having the same problem after updateing a virtual Hardy install.  I cannot get online after rebooting from installing the updates.  Here is my dmesg output.

```
user@ubuntu:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:43:41 UTC 2008 (Ubuntu 2.6.24-19.34-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000ca000 - 00000000000cc000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fef0000 (usable)
[    0.000000]  BIOS-e820: 000000003fef0000 - 000000003fefc000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003fefc000 - 000000003ff00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003ff00000 - 0000000040000000 (usable)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fffe0000 - 0000000100000000 (reserved)
[    0.000000] 128MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f6ce0
[    0.000000] Entering add_active_range(0, 0, 262144) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   262144
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   262144
[    0.000000] On node 0 totalpages: 262144
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 256 pages used for memmap
[    0.000000]   HighMem zone: 32512 pages, LIFO batch:7
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F6C70 checksum 0
[    0.000000] ACPI: RSDP 000F6C70, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 3FEF7B74, 0030 (r1 PTLTD    RSDT    6040000  LTP        0)
[    0.000000] ACPI: FACP 3FEFBF14, 0074 (r1 INTEL  440BX     6040000 PTL     F4240)
[    0.000000] ACPI: DSDT 3FEF7BA4, 4370 (r1 PTLTD  Custom    6040000 MSFT  100000D)
[    0.000000] ACPI: FACS 3FEFCFC0, 0040
[    0.000000] ACPI: APIC 3FEFBF88, 0050 (r1 PTLTD  	 APIC    6040000  LTP        0)
[    0.000000] ACPI: BOOT 3FEFBFD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:2 APIC version 17
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000ca000
[    0.000000] swsusp: Registered nosave memory region: 00000000000ca000 - 00000000000cc000
[    0.000000] swsusp: Registered nosave memory region: 00000000000cc000 - 00000000000dc000
[    0.000000] swsusp: Registered nosave memory region: 00000000000dc000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 260096
[    0.000000] Kernel command line: root=UUID=89879598-257f-4c09-b039-476d8636dd45 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2792.133 MHz processor.
[272966.900435] Console: colour VGA+ 80x25
[272966.901109] console [tty0] enabled
[272966.901966] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[272966.902823] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[272966.922947] Memory: 1027360k/1048576k available (2177k kernel code, 20456k reserved, 1006k data, 368k init, 131008k highmem)
[272966.923204] virtual kernel memory layout:
[272966.923216]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[272966.923227]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[272966.923239]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[272966.923250]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[272966.923294]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[272966.923313]       .data : 0xc0320434 - 0xc041bdc4   (1006 kB)
[272966.923332]       .text : 0xc0100000 - 0xc0320434   (2177 kB)
[272966.923425] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[272966.924282] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[272967.005631] Calibrating delay using timer specific routine.. 5689.77 BogoMIPS (lpj=11379548)
[272967.005694] Security Framework initialized
[272967.005756] SELinux:  Disabled at boot.
[272967.005819] AppArmor: AppArmor initialized
[272967.005881] Failure registering capabilities with primary security module.
[272967.005943] Mount-cache hash table entries: 512
[272967.006006] Initializing cgroup subsys ns
[272967.006068] Initializing cgroup subsys cpuacct
[272967.006131] CPU: After generic identify, caps: 0febfbff 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[272967.006193] CPU: Trace cache: 12K uops, L1 D cache: 8K
[272967.006251] CPU: L2 cache: 512K
[272967.006313] CPU: After all inits, caps: 0febfbff 00000000 00000000 0000b080 00000000 00000000 00000000 00000000
[272967.006375] Compat vDSO mapped to ffffe000.
[272967.006438] Checking 'hlt' instruction... OK.
[272967.021083] SMP alternatives: switching to UP code
[272967.021145] Freeing SMP alternatives: 11k freed
[272967.021208] Early unpacking initramfs... done
[272967.021270] ACPI: Core revision 20070126
[272967.025175] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[272967.025487] CPU0: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 08
[272967.025611] Total of 1 processors activated (5689.77 BogoMIPS).
[272967.025674] ENABLING IO-APIC IRQs
[272967.025900] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[272967.216044] Brought up 1 CPUs
[272967.223673] CPU0 attaching sched-domain:
[272967.223844]  domain 0: span 01
[272967.223920]   groups: 01
[272967.267168] net_namespace: 64 bytes
[272967.267649] Booting paravirtualized kernel on bare hardware
[272967.275690] Time: 13:17:42  Date: 06/30/08
[272967.287021] NET: Registered protocol family 16
[272967.299747] EISA bus registered
[272967.303144] ACPI: bus type pci registered
[272967.311057] PCI: PCI BIOS revision 2.10 entry at 0xfd9a0, last bus=1
[272967.311134] PCI: Using configuration type 1
[272967.311209] Setting up standard PCI resources
[272967.395770] ACPI: EC: Look up EC in DSDT
[272967.575202] ACPI: Interpreter enabled
[272967.575388] ACPI: (supports S0 S1 S5)
[272967.579291] ACPI: Using IOAPIC for interrupt routing
[272967.803335] ACPI: PCI Root Bridge [PCI0] (0000:00)
[272967.827587] PCI quirk: region 1000-103f claimed by PIIX4 ACPI
[272967.830019] PCI quirk: region 1040-104f claimed by PIIX4 SMB
[272967.851342] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[272967.887452] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
[272967.891033] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11 14 15)
[272967.891566] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 14 15)
[272967.894598] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *9 10 11 14 15)
[272967.899514] Linux Plug and Play Support v0.97 (c) Adam Belay
[272967.902075] pnp: PnP ACPI init
[272967.903162] ACPI: bus type pnp registered
[272968.421391] pnp: PnP ACPI: found 12 devices
[272968.422336] ACPI: ACPI bus type pnp unregistered
[272968.422593] PnPBIOS: Disabled by ACPI PNP
[272968.447148] PCI: Using ACPI for IRQ routing
[272968.449280] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[272968.664906] NET: Registered protocol family 8
[272968.665017] NET: Registered protocol family 20
[272968.670405] Time: tsc clocksource has been installed.
[272968.682250] Clocksource tsc unstable (delta = 276040297 ns)
[272968.686107] Time: pit clocksource has been installed.
[272968.690710] AppArmor: AppArmor Filesystem Enabled
[272968.714142] system 00:01: ioport range 0x1000-0x103f has been reserved
[272968.714206] system 00:01: ioport range 0x1040-0x104f has been reserved
[272968.772238] PCI: Bridge: 0000:00:01.0
[272968.772295]   IO window: disabled.
[272968.772357]   MEM window: disabled.
[272968.772420]   PREFETCH window: disabled.
[272968.772470] PCI: Setting latency timer of device 0000:00:01.0 to 64
[272968.772470] NET: Registered protocol family 2
[272968.774153] Time: acpi_pm clocksource has been installed.
[272968.774411] Switched to high resolution mode on CPU 0
[272968.813847] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[272968.817841] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[272968.821836] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[272968.821858] TCP: Hash tables configured (established 131072 bind 65536)
[272968.821881] TCP reno registered
[272968.837807] checking if image is initramfs... it is
[272969.740324] Freeing initrd memory: 7320k freed
[272969.740680] Simple Boot Flag at 0x36 set to 0x1
[272969.742306] audit: initializing netlink socket (disabled)
[272969.742353] audit(1214831848.328:1): initialized
[272969.744901] highmem bounce pool size: 64 pages
[272969.750541] VFS: Disk quotas dquot_6.5.1
[272969.750793] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[272969.752466] io scheduler noop registered
[272969.752512] io scheduler anticipatory registered
[272969.752545] io scheduler deadline registered
[272969.752591] io scheduler cfq registered (default)
[272969.752638] Limiting direct PCI/PCI transfers.
[272969.752740] Boot video device is 0000:00:0f.0
[272969.753850] isapnp: Scanning for PnP cards...
[272970.116640] isapnp: No Plug & Play device found
[272970.189171] Real Time Clock Driver v1.12ac
[272970.189468] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[272970.191600] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[272970.191906] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[272970.192737] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[272970.193082] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[272970.195172] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[272970.195697] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[272970.195998] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUS] at 0x60,0x64 irq 1,12
[272970.714745] serio: i8042 KBD port at 0x60,0x64 irq 1
[272970.714867] serio: i8042 AUX port at 0x60,0x64 irq 12
[272970.730982] mice: PS/2 mouse device common for all mice
[272970.731843] EISA: Probing bus 0 at eisa.0
[272970.731999] Cannot allocate resource for EISA slot 1
[272970.732077] EISA: Detected 0 cards.
[272970.732156] cpuidle: using governor ladder
[272970.732234] cpuidle: using governor menu
[272970.732312] NET: Registered protocol family 1
[272970.732390] Using IPI No-Shortcut mode
[272970.732468] registered taskstats version 1
[272970.732547]   Magic number: 12:352:282
[272970.732625]   hash matches device ttyvd
[272970.732703]   hash matches device tty19
[272970.732778] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[272970.732825] EDD information not available.
[272970.750639] Freeing unused kernel memory: 368k freed
[272970.751808] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[272972.453056] fuse init (API version 7.9)
[272972.635534] ACPI: Processor [CPU0] (supports 8 throttling states)
[272972.635562] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[272972.635590] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[272972.635618] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[272973.286575] SCSI subsystem initialized
[272973.490163] libata version 3.00 loaded.
[272973.518124] usbcore: registered new interface driver usbfs
[272973.518189] usbcore: registered new interface driver hub
[272973.601899] usbcore: registered new device driver usb
[272973.678433] Fusion MPT base driver 3.04.06
[272973.678467] Copyright (c) 1999-2007 LSI Corporation
[272973.729706] Fusion MPT SPI Host driver 3.04.06
[272973.729771] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 17 (level, low) -> IRQ 16
[272973.729835] mptbase: ioc0: Initiating bringup
[272973.805475] ioc0: LSI53C1030 B0: Capabilities={Initiator}
[272973.809570] USB Universal Host Controller Interface driver v3.0
[272973.849623] pcnet32.c:v1.34 14.Aug.2007 tsbogend@alpha.franken.de
[272973.961330] scsi0 : ioc0: LSI53C1030 B0, FwRev=00000000h, Ports=1, MaxQ=128, IRQ=16
[272974.093607] ata_piix 0000:00:07.1: version 2.12
[272974.104968] scsi 0:0:0:0: Direct-Access     VMware,  VMware Virtual S 1.0  PQ: 0 ANSI: 2
[272974.105022]  target0:0:0: Beginning Domain Validation
[272974.105075]  target0:0:0: Domain Validation skipping write tests
[272974.105128]  target0:0:0: Ending Domain Validation
[272974.105182]  target0:0:0: FAST-40 WIDE SCSI 80.0 MB/s ST (25 ns, offset 127)
[272974.145028] scsi1 : ata_piix
[272974.188812] scsi2 : ata_piix
[272974.188865] ata1: PATA max UDMA/33 cmd 0x1f0 ctl 0x3f6 bmdma 0x1050 irq 14
[272974.188907] ata2: PATA max UDMA/33 cmd 0x170 ctl 0x376 bmdma 0x1058 irq 15
[272974.189068] ata1: port disabled. ignoring.
[272974.500975] ata2.00: ATAPI: VMware Virtual IDE CDROM Drive, 00000001, max UDMA/33
[272974.656239] ata2.00: configured for UDMA/33
[272974.656754] scsi 2:0:0:0: CD-ROM            NECVMWar VMware IDE CDR10 1.00 PQ: 0 ANSI: 5
[272974.664018] ACPI: PCI Interrupt 0000:00:07.2[D] -> GSI 19 (level, low) -> IRQ 17
[272974.664070] uhci_hcd 0000:00:07.2: UHCI Host Controller
[272974.664121] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[272974.664231] uhci_hcd 0000:00:07.2: irq 17, io base 0x00001060
[272974.668108] usb usb1: configuration #1 chosen from 1 choice
[272974.668160] hub 1-0:1.0: USB hub found
[272974.668212] hub 1-0:1.0: 2 ports detected
[272974.772109] ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 18 (level, low) -> IRQ 18
[272974.772161] pcnet32: PCnet/PCI II 79C970A at 0x1400, 00 0c 29 07 ed c5 assigned IRQ 18.
[272974.772213] eth0: registered as PCnet/PCI II 79C970A
[272974.772265] pcnet32: 1 cards_found.
[272975.019905] Floppy drive(s): fd0 is 1.44M
[272975.035704] FDC 0 is a post-1991 82077
[272976.591303] Driver 'sd' needs updating - please use bus_type methods
[272976.592789] sd 0:0:0:0: [sda] 16777216 512-byte hardware sectors (8590 MB)
[272976.592940] sd 0:0:0:0: [sda] Write Protect is off
[272976.593040] sd 0:0:0:0: [sda] Mode Sense: 5d 00 00 00
[272976.593191] sd 0:0:0:0: [sda] Cache data unavailable
[272976.593288] sd 0:0:0:0: [sda] Assuming drive cache: write through
[272976.612760] sd 0:0:0:0: [sda] 16777216 512-byte hardware sectors (8590 MB)
[272976.612880] sd 0:0:0:0: [sda] Write Protect is off
[272976.612931] sd 0:0:0:0: [sda] Mode Sense: 5d 00 00 00
[272976.613051] sd 0:0:0:0: [sda] Cache data unavailable
[272976.613081] sd 0:0:0:0: [sda] Assuming drive cache: write through
[272976.613200]  sda: sda1 sda2 < sda5 >
[272976.632808] sd 0:0:0:0: [sda] Attached SCSI disk
[272976.660907] sd 0:0:0:0: Attached scsi generic sg0 type 0
[272976.661019] scsi 2:0:0:0: Attached scsi generic sg1 type 5
[272976.700680] Driver 'sr' needs updating - please use bus_type methods
[272976.701888] sr0: scsi3-mmc drive: 1x/1x xa/form2 cdda tray
[272976.702007] Uniform CD-ROM driver Revision: 3.20
[272976.702127] sr 2:0:0:0: Attached scsi CD-ROM sr0
[272977.143981] Attempting manual resume
[272977.144027] swsusp: Resume From Partition 8:5
[272977.144056] PM: Checking swsusp image.
[272977.144194] PM: Resume from disk failed.
[272977.177434] kjournald starting.  Commit interval 5 seconds
[272977.177573] EXT3-fs: mounted filesystem with ordered data mode.
[273012.286935] Linux agpgart interface v0.102
[273012.380506] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[273012.456749] agpgart: Detected an Intel 440BX Chipset.
[273012.463988] agpgart: AGP aperture is 64M @ 0xec000000
[273012.537605] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[273012.695162] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[273012.695351] piix4_smbus 0000:00:07.3: Host SMBus controller not enabled!
[273013.164955] input: PC Speaker as /devices/platform/pcspkr/input/input2
[273013.956200] ACPI: AC Adapter [ACAD] (on-line)
[273014.077384] input: Power Button (FF) as /devices/virtual/input/input3
[273014.093527] ACPI: Power Button (FF) [PWRF]
[273014.110415] eth0: link up
[273016.462128] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input4
[273017.212874] parport_pc 00:08: reported by Plug and Play ACPI
[273017.214946] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[273018.173103] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 19 (level, low) -> IRQ 17
[273025.776699] NET: Registered protocol family 10
[273025.779828] lo: Disabled Privacy Extensions
[273030.017893] loop: module loaded
[273030.079475] lp0: using parport0 (interrupt-driven).
[273031.452421] EXT3 FS on sda1, internal journal
[273035.646624] ip_tables: (C) 2000-2006 Netfilter Core Team
[273036.475137] eth0: no IPv6 routers present
[273039.012986] No dock devices found.
[273043.157380] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[273043.157510] apm: overridden by ACPI.
[273043.361585] ppdev: user-space parallel port driver
[273043.592541] audit(1214849923.232:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4729 profile="/usr/sbin/cupsd" namespace="default"
[273043.593859] audit(1214849923.232:3): type=1503 operation="inode_permission" requested_mask="w::" denied_mask="w::" name="/etc/krb5.conf" pid=4729 profile="/usr/sbin/cupsd" namespace="default"
[273068.077853] Bluetooth: Core ver 2.11
[273068.085080] NET: Registered protocol family 31
[273068.085124] Bluetooth: HCI device and connection manager initialized
[273068.085547] Bluetooth: HCI socket layer initialized
[273068.224378] Bluetooth: L2CAP ver 2.9
[273068.224421] Bluetooth: L2CAP socket layer initialized
[273068.350874] Bluetooth: RFCOMM socket layer initialized
[273068.355773] Bluetooth: RFCOMM TTY layer initialized
[273068.355823] Bluetooth: RFCOMM ver 1.8
[273070.564913] mtrr: your processor doesn't support write-combining
[273100.145997] UDF-fs: No VRS found
[273100.200032] ISO 9660 Extensions: RRIP_1991A
[273131.527815] usb 1-1: new full speed USB device using uhci_hcd and address 2
[273131.694115] usb 1-1: configuration #1 chosen from 1 choice
[273131.946779] usbcore: registered new interface driver libusual
[273132.056065] Initializing USB Mass Storage driver...
[273132.064019] scsi3 : SCSI emulation for USB Mass Storage devices
[273132.073532] usbcore: registered new interface driver usb-storage
[273132.073985] USB Mass Storage support registered.
[273132.075249] usb-storage: device found at 2
[273132.075328] usb-storage: waiting for device to settle before scanning
[273137.070518] usb-storage: device scan complete
[273137.095793] scsi 3:0:0:0: Direct-Access     SanDisk  U3 Cruzer Micro  4.05 PQ: 0 ANSI: 2
[273137.132166] sd 3:0:0:0: [sdb] 8027789 512-byte hardware sectors (4110 MB)
[273137.145612] sd 3:0:0:0: [sdb] Write Protect is off
[273137.145671] sd 3:0:0:0: [sdb] Mode Sense: 03 00 00 00
[273137.145738] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[273137.214697] sd 3:0:0:0: [sdb] 8027789 512-byte hardware sectors (4110 MB)
[273137.229414] sd 3:0:0:0: [sdb] Write Protect is off
[273137.229437] sd 3:0:0:0: [sdb] Mode Sense: 03 00 00 00
[273137.229453] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[273137.229554]  sdb: sdb1
[273137.255375] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[273137.256235] sd 3:0:0:0: Attached scsi generic sg2 type 0


```

---

### Post by pytheas22 on 2008-06-30
> I am having the same problem after updateing a virtual Hardy install. I cannot get online after rebooting from installing the updates.

seeker, just to confirm: you're running Ubuntu inside a virtual machine?  What is the host operating system and which virtualization software are you using (VirtualBox, vmware...)?

From your dmesg, things look alright as far as the Internet goes.  eth0 is coming up but reports not seeing anything to connect to.  You may want to make sure that your settings for the virtual interface are alright, and if you have something like "guest additions" installed inside the virtual machine, make sure they're still intact--the upgrade could have killed them.

Actually in VirtualBox at least an upgrade almost definitely would have killed them, since they need to be recompiled whenever you change kernels.  I don't know about other virtualization platforms but it's probably the same situation.

---

### Post by seeker1458 on 2008-06-30
Host OS is XP Pro SP2.  Virtualization software is VMWare Server.  The virtual interface is still set to bridged (connect directly to the physical network).  I never installed any thrid party software.  All I did was download the virtual machine from VMWare's webpage. The configured a static IP and set up the syslog-ng server.  After all that was set up, then I downloaded and installed the updates using ubuntu's update manager.  What would I need to check to make sure nothing got broken, (like guest additions...don't even know what that is)

just an fyi...the static connection was working and I was receiving logs from about 20 devices...so I know it was set up right to begin with. And yes I have tried DHCP.

---

### Post by pytheas22 on 2008-06-30
By "guest additions" I mean software from VMware (VirtualBox calls them guest additions; I forgot what their name in VMware is but it's the same kind of thing) that you install in the virtual machine to enable stuff like mouse integration, copy-and-paste from the virtual machine to the host, make the virtual video card work better, et cetera.  Are you sure you didn't install anything like this?

Maybe something got broken with the static IP configuration.  What is the output of:
```

cat /etc/network/interfaces
```

Also did you try NAT networking (using the same IP address as the host machine--I think it's called NAT)?

---

### Post by drinkymilk on 2008-07-01
i typed in the command top and what I see as processes going out of control are:

Xorg
python
init
gnome-settings
pulseaudio
at-spi-regristry


but its mostly Xorg and python hitting the top the most.

~note: I am running Ubuntu 8.04 only on this machine. I am kind of bummed I deleted vbox so hastily.

~tim

---

### Post by pytheas22 on 2008-07-01
> i typed in the command top and what I see as processes going out of control are:

Xorg
python
init
gnome-settings
pulseaudio
at-spi-regristry


but its mostly Xorg and python hitting the top the most.


It's normal for those processes (with the exception of python) to be at the top.  Are they using an unreasonable amount of CPU and memory?  There are two columns that tell you how much they're using as a percent of the system's total; what are those numbers?  Or you could just copy and paste the top output here, or take a screenshot of the terminal window.

I do wonder why python would be up so high.  Were you running any python-heavy applications (like Deluge, the torrent client)?  Otherwise I think it is suspicious to see python hogging a substantial number of resources.

---

