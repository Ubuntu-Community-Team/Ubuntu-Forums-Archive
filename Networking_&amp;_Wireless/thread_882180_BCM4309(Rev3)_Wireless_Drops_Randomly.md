---
title: "BCM4309(Rev3) Wireless Drops Randomly"
date: 2008-08-06
forum: Networking &amp; Wireless
---

### Post by HieroPosche on 2008-08-06
I've been running this install of Hardy for a few months now and as time has passed the wireless has been dropping more and more frequently.  The network applet will say that it is attempting to reconnect to the wireless network, but just hangs and no packets are transferred.

I've seen a couple of older posts on this searching around but nothing offering a solution that worked.  Only recomendation I didn't try was editing bios as I don't see how that should have any relevance to a degrading wirless connection.

---

### Post by pytheas22 on 2008-08-06
You could try troubleshooting whatever is going on by looking at the output of the command "dmesg" the next time the connection drops.  It's probably a bug with b43, the Broadcom driver.

A possible solution (and probably easier than trying to troubleshoot b43) is to install ndiswrapper.  There's a good guide [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff") for ndiswrapper on Broadcom chipsets.  That guide is pretty easy to follow if you know Linux relatively well, but if you're not comfortable with it and would rather have step-by-step instructions on what to do for your card in particular, let me know and I'll write them out.  If you do follow that guide yourself, pay attention the "Hardy Bug Fix" (it's not really a bug, just the way Hardy is designed to work) section, as your card won't work till you apply the stuff mentioned there.

---

### Post by HieroPosche on 2008-08-08
Well of course as murphy's law predicts, it's not going to happen the day I make this post.  But next time it happens (was every couple of hours as of 2 days ago)  I"ll try out your suggestions.  Thank you for the reply and I will update as the situation progresses.

---

### Post by HieroPosche on 2008-09-05
Well I finally got the output from dmesg when the internet dropped.

Only thing that stands out to me is the PHY transmission error, but see id ya'll can make anything of it.

```
clay@Boris:~$ dmesg 
[    0.000000] Initializing cgroup subsys cpuset 
[    0.000000] Initializing cgroup subsys cpu 
[    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Aug 20 22:56:21 UTC 2008 (Ubuntu 2.6.24-19.41-generic) 
[    0.000000] BIOS-provided physical RAM map: 
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable) 
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved) 
[    0.000000]  BIOS-e820: 0000000000100000 - 000000002ffae000 (usable) 
[    0.000000]  BIOS-e820: 000000002ffae000 - 0000000030000000 (reserved) 
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000fee00000 (reserved) 
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved) 
[    0.000000] 0MB HIGHMEM available. 
[    0.000000] 767MB LOWMEM available. 
[    0.000000] Entering add_active_range(0, 0, 196526) 0 entries of 256 used 
[    0.000000] Zone PFN ranges: 
[    0.000000]   DMA             0 ->     4096 
[    0.000000]   Normal       4096 ->   196526 
[    0.000000]   HighMem    196526 ->   196526 
[    0.000000] Movable zone start PFN for each node 
[    0.000000] early_node_map[1] active PFN ranges 
[    0.000000]     0:        0 ->   196526 
[    0.000000] On node 0 totalpages: 196526 
[    0.000000]   DMA zone: 32 pages used for memmap 
[    0.000000]   DMA zone: 0 pages reserved 
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0 
[    0.000000]   Normal zone: 1503 pages used for memmap 
[    0.000000]   Normal zone: 190927 pages, LIFO batch:31 
[    0.000000]   HighMem zone: 0 pages used for memmap 
[    0.000000]   Movable zone: 0 pages used for memmap 
[    0.000000] DMI 2.3 present. 
[    0.000000] ACPI: RSDP signature @ 0xC00FDF00 checksum 0 
[    0.000000] ACPI: RSDP 000FDF00, 0014 (r0 DELL  ) 
[    0.000000] ACPI: RSDT 2FFF0000, 0030 (r1 DELL    CPi R   27D5061D ASL        61) 
[    0.000000] ACPI: FACP 2FFF0400, 0074 (r1 DELL    CPi R   27D5061D ASL        61) 
[    0.000000] ACPI: DSDT 2FFF0C00, 2E1A (r1 INT430 SYSFexxx     1001 MSFT  100000E) 
[    0.000000] ACPI: FACS 2FFFF800, 0040 
[    0.000000] ACPI: ASF! 2FFF0800, 005B (r16 DELL    CPi R   27D5061D ASL        61) 
[    0.000000] ACPI: BOOT 2FFF07C0, 0028 (r1 DELL    CPi R   27D5061D ASL        61) 
[    0.000000] ACPI: PM-Timer IO Port: 0x808 
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 30000000:ceda0000) 
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000 
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 0000000000100000 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 194991 
[    0.000000] Kernel command line: root=UUID=b092f489-ab4b-4bcb-ab6c-f907ab252398 ro quiet splash 
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic" 
[    0.000000] mapped APIC to ffffb000 (0160e000) 
[    0.000000] Enabling fast FPU save and restore... done. 
[    0.000000] Enabling unmasked SIMD FPU exception support... done. 
[    0.000000] Initializing CPU#0 
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes) 
[    0.000000] Detected 599.503 MHz processor. 
[   13.605181] Console: colour VGA+ 80x25 
[   13.605191] console [tty0] enabled 
[   13.605967] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes) 
[   13.607057] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes) 
[   13.644978] Memory: 767108k/786104k available (2177k kernel code, 18412k reserved, 1006k data, 368k init, 0k highmem) 
[   13.644999] virtual kernel memory layout: 
[   13.645002]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB) 
[   13.645006]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB) 
[   13.645010]     vmalloc : 0xf0800000 - 0xff7fe000   ( 239 MB) 
[   13.645013]     lowmem  : 0xc0000000 - 0xeffae000   ( 767 MB) 
[   13.645017]       .init : 0xc0421000 - 0xc047d000   ( 368 kB) 
[   13.645021]       .data : 0xc03204c4 - 0xc041bdc4   (1006 kB) 
[   13.645024]       .text : 0xc0100000 - 0xc03204c4   (2177 kB) 
[   13.645034] Checking if this processor honours the WP bit even in supervisor mode... Ok. 
[   13.645110] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1 
[   13.725138] Calibrating delay using timer specific routine.. 1200.34 BogoMIPS (lpj=2400696) 
[   13.725190] Security Framework initialized 
[   13.725203] SELinux:  Disabled at boot. 
[   13.725235] AppArmor: AppArmor initialized 
[   13.725245] Failure registering capabilities with primary security module. 
[   13.725265] Mount-cache hash table entries: 512 
[   13.725531] Initializing cgroup subsys ns 
[   13.725541] Initializing cgroup subsys cpuacct 
[   13.725564] CPU: After generic identify, caps: afe9f9bf 00000000 00000000 00000000 00000180 00000000 00000000 00000000 
[   13.725592] CPU: L1 I cache: 32K, L1 D cache: 32K 
[   13.725599] CPU: L2 cache: 2048K 
[   13.725605] CPU: After all inits, caps: afe9f9bf 00000000 00000000 00002040 00000180 00000000 00000000 00000000 
[   13.725629] Compat vDSO mapped to ffffe000. 
[   13.725654] Checking 'hlt' instruction... OK. 
[   13.741979] SMP alternatives: switching to UP code 
[   13.746580] Freeing SMP alternatives: 11k freed 
[   13.746836] Early unpacking initramfs... done 
[   14.747016] ACPI: Core revision 20070126 
[   14.747129] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found. 
[   14.750834] ACPI: setting ELCR to 0200 (from 0800) 
[   14.753524] CPU0: Intel(R) Pentium(R) M processor 1.50GHz stepping 06 
[   14.753536] SMP motherboard not detected. 
[   14.753542] Local APIC not detected. Using dummy APIC emulation. 
[   14.753636] Brought up 1 CPUs 
[   14.753674] CPU0 attaching sched-domain: 
[   14.753681]  domain 0: span 01 
[   14.753686]   groups: 01 
[   14.754061] net_namespace: 64 bytes 
[   14.754092] Booting paravirtualized kernel on bare hardware 
[   14.755263] Time: 23:55:40  Date: 09/05/08 
[   14.755316] NET: Registered protocol family 16 
[   14.755803] EISA bus registered 
[   14.755822] ACPI: bus type pci registered 
[   14.789950] PCI: PCI BIOS revision 2.10 entry at 0xfc96e, last bus=2 
[   14.789956] PCI: Using configuration type 1 
[   14.790019] Setting up standard PCI resources 
[   14.794257] ACPI: EC: Look up EC in DSDT 
[   14.806330] ACPI: Interpreter enabled 
[   14.806339] ACPI: (supports S0 S1 S3 S4 S5) 
[   14.806378] ACPI: Using PIC for interrupt routing 
[   14.831275] ACPI: PCI Root Bridge [PCI0] (0000:00) 
[   14.831859] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO 
[   14.831868] PCI quirk: region 0880-08bf claimed by ICH4 GPIO 
[   14.832596] PCI: Transparent bridge - 0000:00:1e.0 
[   14.832807] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT] 
[   14.833677] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT] 
[   14.833888] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT] 
[   14.861262] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11) 
[   14.861525] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *11 
[   14.861782] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 *11) 
[   14.862038] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 *11) 
[   14.862258] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled. 
[   14.862522] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11 12 14 15) 
[   14.862819] Linux Plug and Play Support v0.97 (c) Adam Belay 
[   14.862900] pnp: PnP ACPI init 
[   14.862918] ACPI: bus type pnp registered 
[   14.918243] pnp: PnP ACPI: found 13 devices 
[   14.918250] ACPI: ACPI bus type pnp unregistered 
[   14.918261] PnPBIOS: Disabled by ACPI PNP 
[   14.918824] PCI: Using ACPI for IRQ routing 
[   14.918831] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report 
[   14.941140] NET: Registered protocol family 8 
[   14.941146] NET: Registered protocol family 20 
[   14.941284] AppArmor: AppArmor Filesystem Enabled 
[   14.945123] Time: tsc clocksource has been installed. 
[   14.953217] system 00:00: iomem range 0x0-0x9fbff could not be reserved 
[   14.953227] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved 
[   14.953236] system 00:00: iomem range 0xc0000-0xcffff could not be reserved 
[   14.953244] system 00:00: iomem range 0xe0000-0xfffff could not be reserved 
[   14.953253] system 00:00: iomem range 0x100000-0x2ffeffff could not be reserved 
[   14.953262] system 00:00: iomem range 0x2fff0000-0x2fffffff could not be reserved 
[   14.953271] system 00:00: iomem range 0xfeda0000-0xfedfffff could not be reserved 
[   14.953280] system 00:00: iomem range 0xffb00000-0xffbfffff could not be reserved 
[   14.953298] system 00:02: ioport range 0x4d0-0x4d1 has been reserved 
[   14.953306] system 00:02: ioport range 0x800-0x805 has been reserved 
[   14.953314] system 00:02: ioport range 0x808-0x80f has been reserved 
[   14.953329] system 00:03: ioport range 0xf400-0xf4fe has been reserved 
[   14.953338] system 00:03: ioport range 0x806-0x807 has been reserved 
[   14.953346] system 00:03: ioport range 0x810-0x85f has been reserved 
[   14.953354] system 00:03: ioport range 0x860-0x87f has been reserved 
[   14.953361] system 00:03: ioport range 0x880-0x8bf has been reserved 
[   14.953369] system 00:03: ioport range 0x8c0-0x8df has been reserved 
[   14.953377] system 00:03: ioport range 0x8e0-0x8ff has been reserved 
[   14.953397] system 00:08: ioport range 0x900-0x97f has been reserved 
[   14.984441] PCI: Bridge: 0000:00:01.0 
[   14.984448]   IO window: c000-cfff 
[   14.984456]   MEM window: fc000000-fdffffff 
[   14.984463]   PREFETCH window: e8000000-efffffff 
[   14.984490] PCI: Bus 3, cardbus bridge: 0000:02:01.0 
[   14.984496]   IO window: 0000d000-0000d0ff 
[   14.984504]   IO window: 0000d400-0000d4ff 
[   14.984511]   PREFETCH window: 44000000-47ffffff 
[   14.984519]   MEM window: 48000000-4bffffff 
[   14.984527] PCI: Bus 7, cardbus bridge: 0000:02:01.1 
[   14.984532]   IO window: 0000d800-0000d8ff 
[   14.984539]   IO window: 0000dc00-0000dcff 
[   14.984547]   PREFETCH window: 4c000000-4fffffff 
[   14.984555]   MEM window: 50000000-53ffffff 
[   14.984562] PCI: Bridge: 0000:00:1e.0 
[   14.984568]   IO window: d000-efff 
[   14.984577]   MEM window: f6000000-fbffffff 
[   14.984584]   PREFETCH window: disabled. 
[   14.984606] PCI: Setting latency timer of device 0000:00:1e.0 to 64 
[   14.984631] PCI: Enabling device 0000:02:01.0 (0000 -> 0003) 
[   14.985008] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11 
[   14.985015] PCI: setting IRQ 11 as level-triggered 
[   14.985023] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11 
[   14.985053] PCI: Enabling device 0000:02:01.1 (0000 -> 0003) 
[   14.985062] ACPI: PCI Interrupt 0000:02:01.1[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11 
[   14.985094] NET: Registered protocol family 2 
[   15.021262] IP route cache hash table entries: 32768 (order: 5, 131072 bytes) 
[   15.021858] TCP established hash table entries: 131072 (order: 8, 1048576 bytes) 
[   15.023853] TCP bind hash table entries: 65536 (order: 7, 524288 bytes) 
[   15.024852] TCP: Hash tables configured (established 131072 bind 65536) 
[   15.024859] TCP reno registered 
[   15.033447] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0 
[   15.994431]  it is 
[   17.010911] Freeing initrd memory: 7325k freed 
[   17.011253] Simple Boot Flag at 0x79 set to 0x1 
[   17.012013] audit: initializing netlink socket (disabled) 
[   17.012042] audit(1220658941.368:1): initialized 
[   17.017465] VFS: Disk quotas dquot_6.5.1 
[   17.017662] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes) 
[   17.017988] io scheduler noop registered 
[   17.017994] io scheduler anticipatory registered 
[   17.018000] io scheduler deadline registered 
[   17.018029] io scheduler cfq registered (default) 
[   17.018133] Boot video device is 0000:01:00.0 
[   17.018777] isapnp: Scanning for PnP cards... 
[   17.374022] isapnp: No Plug & Play device found 
[   17.451181] Real Time Clock Driver v1.12ac 
[   17.451527] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled 
[   17.451848] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A 
[   17.453595] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A 
[   17.454543] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5 
[   17.454553] PCI: setting IRQ 5 as level-triggered 
[   17.454563] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5 
[   17.454589] ACPI: PCI interrupt for device 0000:00:1f.6 disabled 
[   17.456307] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize 
[   17.456509] input: Macintosh mouse button emulation as /devices/virtual/input/input0 
[   17.456775] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12 
[   17.468355] serio: i8042 KBD port at 0x60,0x64 irq 1 
[   17.468368] serio: i8042 AUX port at 0x60,0x64 irq 12 
[   17.485638] Clocksource tsc unstable (delta = 240442882 ns) 
[   17.485825] mice: PS/2 mouse device common for all mice 
[   17.486115] EISA: Probing bus 0 at eisa.0 
[   17.486180] EISA: Detected 0 cards. 
[   17.486190] cpuidle: using governor ladder 
[   17.486196] cpuidle: using governor menu 
[   17.486461] NET: Registered protocol family 1 
[   17.486535] Using IPI No-Shortcut mode 
[   17.486633] registered taskstats version 1 
[   17.486919]   Magic number: 8:724:958 
[   17.487016]   hash matches device ptyzf 
[   17.487114]   hash matches device oldmem 
[   17.487158] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found 
[   17.487165] EDD information not available. 
[   17.487880] Freeing unused kernel memory: 368k freed 
[   17.493619] Time: acpi_pm clocksource has been installed. 
[   17.496861] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1 
[   20.545291] fuse init (API version 7.9) 
[   20.594050] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3]) 
[   20.594068] ACPI: Processor [CPU0] (supports 8 throttling states) 
[   20.604891] ACPI: Thermal Zone [THM] (33 C) 
[   22.231928] usbcore: registered new interface driver usbfs 
[   22.231997] usbcore: registered new interface driver hub 
[   22.271200] usbcore: registered new device driver usb 
[   22.301201] USB Universal Host Controller Interface driver v3.0 
[   22.301907] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11 
[   22.301917] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11 
[   22.301953] PCI: Setting latency timer of device 0000:00:1d.0 to 64 
[   22.301964] uhci_hcd 0000:00:1d.0: UHCI Host Controller 
[   22.302982] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1 
[   22.303042] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000bf80 
[   22.303432] usb usb1: configuration #1 chosen from 1 choice 
[   22.303499] hub 1-0:1.0: USB hub found 
[   22.303513] hub 1-0:1.0: 2 ports detected 
[   22.478539] SCSI subsystem initialized 
[   22.561387] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11 
[   22.561426] PCI: Setting latency timer of device 0000:00:1d.1 to 64 
[   22.561439] uhci_hcd 0000:00:1d.1: UHCI Host Controller 
[   22.561520] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2 
[   22.561574] uhci_hcd 0000:00:1d.1: irq 11, io base 0x0000bf40 
[   22.561887] usb usb2: configuration #1 chosen from 1 choice 
[   22.561953] hub 2-0:1.0: USB hub found 
[   22.561969] hub 2-0:1.0: 2 ports detected 
[   22.685136] libata version 3.00 loaded. 
[   22.821913] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11 
[   22.821926] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11 
[   22.821960] PCI: Setting latency timer of device 0000:00:1d.2 to 64 
[   22.821971] uhci_hcd 0000:00:1d.2: UHCI Host Controller 
[   22.822038] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3 
[   22.822092] uhci_hcd 0000:00:1d.2: irq 11, io base 0x0000bf20 
[   22.822405] usb usb3: configuration #1 chosen from 1 choice 
[   22.822470] hub 3-0:1.0: USB hub found 
[   22.822486] hub 3-0:1.0: 2 ports detected 
[   23.082144] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11 
[   23.082158] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11 
[   23.082197] PCI: Setting latency timer of device 0000:00:1d.7 to 64 
[   23.082208] ehci_hcd 0000:00:1d.7: EHCI Host Controller 
[   23.082277] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4 
[   23.092035] ehci_hcd 0000:00:1d.7: debug port 1 
[   23.092051] PCI: cache line size of 32 is not supported by device 0000:00:1d.7 
[   23.092072] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xf4fffc00 
[   23.131015] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004 
[   23.131286] usb usb4: configuration #1 chosen from 1 choice 
[   23.131352] hub 4-0:1.0: USB hub found 
[   23.131368] hub 4-0:1.0: 6 ports detected 
[   23.391675] tg3.c:v3.86 (November 9, 2007) 
[   23.391752] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11 
[   23.511244] eth0: Tigon3 [partno(BCM95705A50) rev 3001 PHY(5705)] (PCI:33MHz:32-bit) 10/100/1000Base-T Ethernet 00:0f:1f:c0:3c:4f 
[   23.511265] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1] 
[   23.511273] eth0: dma_rwctrl[763f0000] dma_mask[64-bit] 
[   23.511343] ACPI: PCI Interrupt 0000:02:03.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5 
[   23.511415] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x04, vendor 0x4243) 
[   23.511431] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x05, vendor 0x4243) 
[   23.511446] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x02, vendor 0x4243) 
[   23.511461] ssb: Core 3 found: V90 (cc 0x807, rev 0x02, vendor 0x4243) 
[   23.511476] ssb: Core 4 found: PCI (cc 0x804, rev 0x09, vendor 0x4243) 
[   23.519745] ssb: Sonics Silicon Backplane found on PCI device 0000:02:03.0 
[   23.519988] ata_piix 0000:00:1f.1: version 2.12 
[   23.520021] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007) 
[   23.520034] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11 
[   23.520142] PCI: Setting latency timer of device 0000:00:1f.1 to 64 
[   23.521167] scsi0 : ata_piix 
[   23.522672] scsi1 : ata_piix 
[   23.525391] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14 
[   23.525400] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15 
[   23.932010] ata1.00: ATA-6: FUJITSU MHV2040AH, 00000096, max UDMA/100 
[   23.932022] ata1.00: 78140160 sectors, multi 8: LBA 
[   23.971846] ata1.00: configured for UDMA/100 
[   24.771534] ata2.00: ATAPI: HL-DT-STCD-RW/DVD-ROM GCC-4244N, B103, max UDMA/33 
[   25.201330] ata2.00: configured for UDMA/33 
[   25.201703] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHV2040A 0000 PQ: 0 ANSI: 5 
[   25.207030] scsi 1:0:0:0: CD-ROM            HL-DT-ST CDRW/DVD GCC4244 B103 PQ: 0 ANSI: 5 
[   25.252490] Driver 'sd' needs updating - please use bus_type methods 
[   25.252696] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB) 
[   25.252732] sd 0:0:0:0: [sda] Write Protect is off 
[   25.252739] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00 
[   25.252783] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[   25.252912] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB) 
[   25.252939] sd 0:0:0:0: [sda] Write Protect is off 
[   25.252946] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00 
[   25.252988] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[   25.252999]  sda:<4>Driver 'sr' needs updating - please use bus_type methods 
[   25.450262]  sda1 sda2 < sda5 > 
[   25.538615] sd 0:0:0:0: [sda] Attached SCSI disk 
[   25.555222] sd 0:0:0:0: Attached scsi generic sg0 type 0 
[   25.555273] sr 1:0:0:0: Attached scsi generic sg1 type 5 
[   25.556870] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray 
[   25.556880] Uniform CD-ROM driver Revision: 3.20 
[   25.556988] sr 1:0:0:0: Attached scsi CD-ROM sr0 
[   26.107557] Attempting manual resume 
[   26.107569] swsusp: Resume From Partition 8:5 
[   26.107574] PM: Checking swsusp image. 
[   26.107971] PM: Resume from disk failed. 
[   26.260506] kjournald starting.  Commit interval 5 seconds 
[   26.260533] EXT3-fs: mounted filesystem with ordered data mode. 
[   52.440169] Linux agpgart interface v0.102 
[   52.790302] agpgart: Detected an Intel 855PM Chipset. 
[   52.808904] agpgart: AGP aperture is 128M @ 0xe0000000 
[   53.040114] pci_hotplug: PCI Hot Plug PCI Core version: 0.5 
[   53.210320] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4 
[   53.809973] intel_rng: FWH not detected 
[   54.200053] iTCO_vendor_support: vendor-support=0 
[   54.333040] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007) 
[   54.333351] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x0860) 
[   54.333467] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0) 
[   54.670728] ACPI: AC Adapter [AC] (off-line) 
[   56.010459] input: PC Speaker as /devices/platform/pcspkr/input/input2 
[   56.048712] ACPI: Battery Slot [BAT0] (battery present) 
[   56.048842] ACPI: Battery Slot [BAT1] (battery absent) 
[   56.049260] input: Lid Switch as /devices/virtual/input/input3 
[   56.052235] ACPI: Lid Switch [LID] 
[   56.052374] input: Power Button (CM) as /devices/virtual/input/input4 
[   56.089678] ACPI: Power Button (CM) [PBTN] 
[   56.089859] input: Sleep Button (CM) as /devices/virtual/input/input5 
[   56.129638] ACPI: Sleep Button (CM) [SBTN] 
[   57.740417] Yenta: CardBus bridge found at 0000:02:01.0 [1028:011d] 
[   57.740470] Yenta O2: res at 0x94/0xD4: 00/ea 
[   57.740476] Yenta O2: enabling read prefetch/write burst 
[   58.060624] Yenta: ISA IRQ mask 0x0498, PCI irq 11 
[   58.060638] Socket status: 30000006 
[   58.060646] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06 
[   58.060664] pcmcia: parent PCI bridge I/O window: 0xd000 - 0xefff 
[   58.060672] cs: IO port probe 0xd000-0xefff: clean. 
[   58.062034] pcmcia: parent PCI bridge Memory window: 0xf6000000 - 0xfbffffff 
[   58.180267] Yenta: CardBus bridge found at 0000:02:01.1 [1028:011d] 
[   58.500662] Yenta: ISA IRQ mask 0x0498, PCI irq 11 
[   58.500676] Socket status: 30000410 
[   58.500684] Yenta: Raising subordinate bus# of parent bus (#02) from #06 to #0a 
[   58.500701] pcmcia: parent PCI bridge I/O window: 0xd000 - 0xefff 
[   58.500709] cs: IO port probe 0xd000-0xefff: clean. 
[   58.502072] pcmcia: parent PCI bridge Memory window: 0xf6000000 - 0xfbffffff 
[   58.686743] input: DualPoint Stick as /devices/virtual/input/input6 
[   58.758880] input: AlpsPS/2 ALPS DualPoint TouchPad as /devices/platform/i8042/serio1/input/input7 
[   60.309141] pccard: PCMCIA card inserted into slot 1 
[   61.941808] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:1e/LNXVIDEO:00/input/input8 
[   61.978922] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no) 
[   63.930396] parport_pc 00:0c: reported by Plug and Play ACPI 
[   63.930519] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA] 
[   63.981422] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2) 
[   64.082688] b43-phy0: Broadcom 4306 WLAN found 
[   64.133004] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5 
[   64.133069] PCI: Setting latency timer of device 0000:00:1f.5 to 64 
[   64.138727] b43-phy0 debug: Found PHY: Analog 2, Type 2, Revision 2 
[   64.138780] b43-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2 
[   64.204697] phy0: Selected rate control algorithm 'simple' 
[   66.198380] intel8x0_measure_ac97_clock: measured 55440 usecs 
[   66.198393] intel8x0: clocking to 48000 
[   67.698201] cs: memory probe 0xf6000000-0xfbffffff: excluding 0xf6000000-0xf65fffff 0xf6c00000-0xf71fffff 0xf7e00000-0xf83fffff 0xf9c00000-0xfa1fffff 0xfae00000-0xfb3fffff 
[   67.731054] pcmcia: registering new device pcmcia1.0 
[   67.939204] cs: IO port probe 0x100-0x3af: clean. 
[   67.941685] cs: IO port probe 0x3e0-0x4ff: clean. 
[   67.942742] cs: IO port probe 0x820-0x8ff: clean. 
[   67.942870] cs: IO port probe 0xc00-0xcf7: clean. 
[   67.944134] cs: IO port probe 0xa00-0xaff: clean. 
[   67.945611] cs: IO port probe 0x100-0x3af: clean. 
[   67.948224] cs: IO port probe 0x3e0-0x4ff: clean. 
[   67.949283] cs: IO port probe 0x820-0x8ff: clean. 
[   67.949412] cs: IO port probe 0xc00-0xcf7: clean. 
[   67.950688] cs: IO port probe 0xa00-0xaff: clean. 
[   69.103326] lp0: using parport0 (interrupt-driven). 
[   69.209507] Adding 1646620k swap on /dev/sda5.  Priority:-1 extents:1 across:1646620k 
[   69.284494] EXT3 FS on sda1, internal journal 
[   71.128800] ip_tables: (C) 2000-2006 Netfilter Core Team 
[   72.377751] ACPI: ACPI Dock Station Driver 
[   76.365241] apm: BIOS not found. 
[   76.694930] ppdev: user-space parallel port driver 
[   77.207314] audit(1220658967.392:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4783 profile="/usr/sbin/cupsd" namespace="default" 
[  194.183775] Marking TSC unstable due to: cpufreq changes. 
[  213.337984] input: b43-phy0 as /devices/virtual/input/input9 
[   85.433544] Bluetooth: Core ver 2.11 
[   85.455825] NET: Registered protocol family 31 
[   85.455835] Bluetooth: HCI device and connection manager initialized 
[   85.455845] Bluetooth: HCI socket layer initialized 
[   85.594382] Bluetooth: L2CAP ver 2.9 
[   85.594397] Bluetooth: L2CAP socket layer initialized 
[   85.806023] Bluetooth: RFCOMM socket layer initialized 
[   85.806064] Bluetooth: RFCOMM TTY layer initialized 
[   85.806070] Bluetooth: RFCOMM ver 1.8 
[  129.117710] b43-phy0 debug: Loading firmware version 351.126 (2006-07-29 05:54:02) 
[   87.636429] b43-phy0 debug: !WARNING! Idle-TSSI phy->cur_idle_tssi measuring failed. (cur=37, tgt=62). Disabling TX power adjustment. 
[   87.636588] b43-phy0 debug: Chip initialized 
[   87.638056] b43-phy0 debug: 30-bit DMA initialized 
[   87.642042] Registered led device: b43-phy0:tx 
[   87.642443] Registered led device: b43-phy0:rx 
[   87.642780] Registered led device: b43-phy0:radio 
[   87.642887] b43-phy0 ERROR: PHY transmission error 
[   87.643036] b43-phy0 debug: Wireless interface started 
[   87.736228] b43-phy0 ERROR: PHY transmission error 
[   87.736405] b43-phy0 ERROR: PHY transmission error 
[   87.737153] b43-phy0 debug: Adding Interface type 2 
[   89.602934] [drm] Initialized drm 1.1.0 20060810 
[  134.430648] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11 
[  134.432313] [drm] Initialized radeon 1.28.0 20060524 on minor 0 
[   92.671676] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0. 
[   92.672298] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode 
[   92.672731] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode 
[  232.025384] [drm] Setting GART location based on new memory map 
[  232.025438] [drm] Loading R200 Microcode 
[  232.025584] [drm] writeback test succeeded in 3 usecs 
[  272.406171] NET: Registered protocol family 10 
[  272.408741] lo: Disabled Privacy Extensions 
[  272.412133] ADDRCONF(NETDEV_UP): eth0: link is not ready 
[  272.415893] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
[  321.911957] NET: Registered protocol family 17 
[  326.413128] b43-phy0 debug: Using hardware based encryption for keyidx: 0, mac: ff:ff:ff:ff:ff:ff 
[  326.442565] wlan0: Initial auth_alg=1 
[  326.442596] wlan0: authenticate with AP 00:1c:df:01:fd:6e 
[  326.448765] wlan0: RX authentication from 00:1c:df:01:fd:6e (alg=1 transaction=2 status=0) 
[  326.448792] wlan0: replying to auth challenge 
[  326.456342] wlan0: RX authentication from 00:1c:df:01:fd:6e (alg=1 transaction=4 status=0) 
[  326.456366] wlan0: authenticated 
[  326.456385] wlan0: associate with AP 00:1c:df:01:fd:6e 
[  326.461852] wlan0: RX AssocResp from 00:1c:df:01:fd:6e (capab=0x411 status=0 aid=3) 
[  326.461875] wlan0: associated 
[  326.471556] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready 
[  381.508236] b43-phy0 ERROR: PHY transmission error 
[  381.508350] b43-phy0 ERROR: PHY transmission error 
[  381.508413] b43-phy0 ERROR: PHY transmission error 
[  386.595943] wlan0: no IPv6 routers present 
[  219.593566] b43-phy0 ERROR: PHY transmission error 
[  219.593694] b43-phy0 ERROR: PHY transmission error 
[  219.593742] b43-phy0 ERROR: PHY transmission error 
[  219.593790] b43-phy0 ERROR: PHY transmission error 
[  558.745923] wlan0: No ProbeResp from current AP 00:1c:df:01:fd:6e - assume out of range 
[  599.814073] b43-phy0 debug: Disabling hardware based encryption for keyidx: 0, mac: ff:ff:ff:ff:ff:ff 

```

---

### Post by pytheas22 on 2008-09-06
Thanks for the information.  I did some googling and this appears to be simply a bug with the b43 driver.  It may be fixed by Ubuntu updates (so make sure you've applied all updates), or maybe not.  You might also be able to solve it by compiling the latest stable release of the Linux wireless stack from [http://linuxwireless.org/](http://linuxwireless.org/), although that's not always as fun to do as it sounds.

If this is a major problem, probably the easiest thing to do is to use ndiswrapper to drive the card instead of the b43 driver, as I suggested earlier.  There are good instructions [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff") on how to install ndiswrapper for your particular card.

If this only happens once a month (and you use your computer frequently), maybe it's not a big enough deal to merit installing ndiswrapper.  It would probably work when the connection drops simply to run this to get it back up:
```

sudo rmmod b43
sudo modprobe b43
sudo ifconfig wlan0 up
```

If you do try installing ndiswrapper and you run into trouble, post the output of these commands so that we can figure out what's wrong:
```

lshw -C Network
ndiswrapper -l
uname -m
dmesg | grep -e ndis -e wlan
```

Please let me know when you find an acceptable solution, whichever route you decide to take.

---

### Post by HieroPosche on 2008-09-06
Thanks for the reply.  I've had issues with getting ndiswrapper to work with this BC4309 card in the past, from what I gather others have had the same issue. That's actually why I'm using Ubuntu instead of Slackware, I could never get the wireless up and running on Slack.

Since I don't use this computer for much (really just learning linux until I can sever myself from windows completely (games :P)) I'll use the code to reinitialize the wireless for now. 

Thank you again, that code was what I was hoping to find since it doesn't seem to be happening a whole lot anymore.

~Dave

---

### Post by Bucky Ball on 2008-09-06
Eek. The advice to use ndiswrapper with a Broadcom card *must* come from those who don't own one. Nightmare. I would attempt to fix the b43 problem (Broadcom cards are known to be notoriously unfriendly - that is what the Broadcom b43 driver is all about I believe).

One thing to try is simply unticking the driver in System->Hardware Drivers->Broadcom b43 driver. Close, then open Hardware Drivers and switch it on again. I know it sounds kinda numbskull but it has worked before. :)

---

### Post by pytheas22 on 2008-09-06
> Eek. The advice to use ndiswrapper with a Broadcom card must come from those who don't own one. Nightmare. I would attempt to fix the b43 problem (Broadcom cards are known to be notoriously unfriendly - that is what the Broadcom b43 driver is all about I believe).

One thing to try is simply unticking the driver in System->Hardware Drivers->Broadcom b43 driver. Close, then open Hardware Drivers and switch it on again. I know it sounds kinda numbskull but it has worked before. 

I wouldn't call b43 "unfriendly," as it wasn't designed that way on purpose.  b43 is a reverse-engineered driver for Broadcom-based wireless cards, meaning that a group of developers has very tediously written it without any cooperation on the part of the hardware vendor, who refused to support Linux (recently Broadcom has come around and started releasing its own binary-only Linux drivers, although they don't yet support the chipset in question in this thread).  So b43 still has a lot of issues to work out, but for something written from scratch without even any documentation from Broadcom about how its hardware works, b43 is not bad.

I do own a Broadcom card that has been driven by ndiswrapper.  I've never had trouble.  Probably the greatest source of confusion is that there are many different models of Broadcom cards, and each one requires a different Windows driver to work with ndiswrapper.  So you just need to make sure that you you're using the right driver.  ndiswrapper, which has been around much longer, should work more reliably than b43 as long as it's configured properly (the link from my last post has good instructions).

But anyway I guess this doesn't matter much, since HieroPosche will just stick with b43 for the time being anyway, which is probably the best solution as long as the crashes are not a serious problem.  They'll probably eventually get fixed by Ubuntu updates anyway, as b43 is in rapid development and bugs are getting worked out all the time.

---

### Post by Bucky Ball on 2008-09-06
[quote=pytheas22]I wouldn't call b43 "unfriendly[/quote]

Me either. Maybe I wasn't too clear but I was saying just the opposite. I advise to try and fix the b43/b43-fwcutter setup and *ndiswrapper* was the unfriendly bit! I completely agree with and support what you are saying if you re-read my post.

Also, for my card, I wrangled with it for months with the support of some network experienced heads in the forum and to no avail. b43 worked virtually instantly when I installed 8.04. So I agree with you there too, all depends which card exactly.  :)

---

### Post by HieroPosche on 2008-09-07
The strange part of this was that the first time I came to Ubuntu (from Slackware) my wireless worked right off the bat just clicking the restricted drivers in the system setup.  If I remember correctly that was on Fiesty.  Then I came back with a clean install of Hardy and had to do a bunch of updating and such for the B43 to work at all.  Kinda seemed like they backtracked on support for the card.

Also odd, is the fact that the issues with the B43 seem to be a degrading issue, it worked fine for months, then started to get progressively worse.

Thanks for the tip on selecting and unselecting the restricted driver though, if the code line doesn't work for some reason that may come in handy.

---

### Post by Ayuthia on 2008-09-07
> **HieroPosche said:**
> The strange part of this was that the first time I came to Ubuntu (from Slackware) my wireless worked right off the bat just clicking the restricted drivers in the system setup.  If I remember correctly that was on Fiesty.  Then I came back with a clean install of Hardy and had to do a bunch of updating and such for the B43 to work at all.  Kinda seemed like they backtracked on support for the card.

Also odd, is the fact that the issues with the B43 seem to be a degrading issue, it worked fine for months, then started to get progressively worse.

Thanks for the tip on selecting and unselecting the restricted driver though, if the code line doesn't work for some reason that may come in handy.

Can you post your lspci -nn info?  Your dmesg shows that it detected a 4306 card.  Another option is to try the bcm43xx driver also.  That is the driver used in Gutsy and older modules.  You will have to install bcm43xx-fwcutter and blacklist the b43/ssb modules.

---

### Post by HieroPosche on 2008-09-09
```
clay@Boris:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82855PM Processor to I/O Controller [8086:3340] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 82855PM Processor to AGP Controller [8086:3341] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 81)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 01)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 01)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 01)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] [1002:4c66] (rev 02)
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet [14e4:165d] (rev 01)
02:01.0 CardBus bridge [0607]: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller [1217:7113] (rev 20)
02:01.1 CardBus bridge [0607]: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller [1217:7113] (rev 20)
02:03.0 Network controller [0280]: Broadcom Corporation BCM4309 802.11a/b/g [14e4:4324] (rev 03)

```

---

### Post by pytheas22 on 2008-09-09
You've got a 4306 card with a PCI ID of 14e4:4324, which is rare.  According to [this page]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff") (which is generally quite good, although there's only one person on there who reports having used ndiswrapper for your model of wireless card), you could install ndiswrapper for your card by running these commands:

```
sudo apt-get install ndiswrapper* cabextract
wget ftp://ftp.compaq.com/pub/softpaq/sp33001-33500/sp33008.exe
cabextract sp33008.exe
sudo ndiswrapper -i bcmwl5.inf
sudo depmod -a
sudo modprobe ndiswrapper
sudo cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
sudo ndiswrapper -m
echo 'ndiswrapper' | sudo tee -a /etc/modules
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
```

Then reboot, and run these commands:
```

sudo modprobe -r b43 b44 b43legacy ssb ndiswrapper
sudo modprobe ndiswrapper
sudo ifconfig wlan0 up
```

In principle, after that, your wireless would work (you'd need to run those last three commands manually after each reboot to bring up the interface, although we can write a script to do that automatically if we want).  But you may just want to stick with b43 if it works well enough.

You could also possibly use bcm43xx, but I don't know how well it would work; if it were me, I'd go with ndiswrapper before bcm43xx, which is very flaky on my Broadcom 4306/14e4:4320 card.

---

### Post by HieroPosche on 2008-09-10
Well, it started dropping more frequently yesterday, and the other hints didn't reset the card as I'd hoped, so I went ahead and got ndiswrapper going as you suggested.  It seems to be working fine, only odd part is that my wireless signal went from 65% to 26%.  Any suggestions on how to improve that?
It works well enough for day to day operations, just limits download speed a bit.

---

### Post by pytheas22 on 2008-09-10
ndiswrapper doesn't always report signal strength accurately, so 26% may not really be 26%.  Does it get up past 90% when you're really close to the router, or does it always display a low strength?

As for transfer speeds, maybe the bit rate is low.  You can check using the 'iwconfig wlan0' command:
```

 IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.417 GHz  Access Point: Not-Associated   
          **Bit Rate: 11 MB/s**   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

You can try to raise the rate with:
```

sudo iwconfig wlan0 rate 54M
```

---

### Post by HieroPosche on 2008-09-19
Well ndiswrapper has been working fine up until the yesterday.  Now when I try to input this command the entire system locks up.  Only thing I can do is power the system down and reboot.

```
sudo modprobe -r b43 b44 b43legacy ssb ndiswrapper
```

Put that in, enter the psw and everything stops.  So for now I'm stuck with the shoddy driver I was using before.

This is starting to be less than fun, but at least I'm learning lol :P

---

### Post by pytheas22 on 2008-09-19
I guess the best thing to do would be to remove those modules one at a time and figure out which one is causing the lockup.  So run:
```

sudo rmmod b43
sudo rmmod b44
sudo rmmod b43legacy
sudo rmmod ssb
sudo rmmod ndiswrapper
```

and please let us know which one causes the crash.

Also, when your computer locks up, you shouldn't just hard power it off.  Instead, press and hold alt-sysreq (sysreq is probably your printscreen key as well), then (with those two keys still down), press the letters R-E-I-U-S-B, one at a time (you do not need to keep those letters held down, but you should keep alt-sysreq down throughout the whole process).  This should cause your system to reboot more cleanly, minimizing the risk of file system damage that you have with a hard reboot.

---

### Post by HieroPosche on 2008-09-22
Sorry for the long wait in the response, but I finally got it done.

None of those modules caused a crash as far as I can tell.

Neither did:

```
sudo modprobe -r b43 b44 b43legacy ssb ndiswrapper
```

What did cause it was the second line in that setup:

```
sudo modprobe ndiswrapper
```

When I input that it locks the system up completely.

Also, the reiusb performs a shutdown normally, but does not seem to work when it locks up with this issue.  /shrug

---

### Post by pytheas22 on 2008-09-22
> What did cause it was the second line in that setup:

Code:

sudo modprobe ndiswrapper

That's not good.  If it freezes when you try to insert ndiswrapper, there's a major problem.  Does it make a difference if you type this before inserting the ndiswrapper module:
```

sudo depmod -a
```

That should resolve any module-dependency issues and hopefully allow ndiswrapper to be inserted without causing instability.

> Also, the reiusb performs a shutdown normally, but does not seem to work when it locks up with this issue. /shrug 

Sometimes if your system crashes so badly that even sysreq doesn't work, so I guess that's what's happening.  The chances of damaging anything with a cold reboot are very remote anyway, but it's always better to use sysreq if possible.

---

### Post by HieroPosche on 2008-09-23
I'm not certain if this would make any difference, but I never uninstalled the B43 that I was using before. Basically I've been waiting until that connection craps out, then utilizing the ndiswrapper to alleviate the problem.

Could that in any way be effecting the issue?

Unless otherwise instructed I will wait till the connection drops again to follow through with what you asked me to do.

For the record, none of the code lines in my precious posts cause a lock up when the B43 module is running and connected.

---

### Post by pytheas22 on 2008-09-23
The fact that the b43 module is still around should not be causing lockups with ndiswrapper, so I wouldn't worry about deleting it.
> 
For the record, none of the code lines in my precious posts cause a lock up when the B43 module is running and connected. 

So you mean that if the card is running on the b43 driver and you then type 'sudo modprobe ndiswrapper', the system doesn't freeze?  It only freezes if b43 has previously been unloaded (and the wireless card is therefore not doing anything)?  That's strange...

---

### Post by HieroPosche on 2008-09-23
Yes, that's exactly what I meant by it. I'm wondering if it's an issue with the card itself.  As in something happens with the card that renders it incapable of communicating with the system at all, thus the B43 module stops working, and when I try to force it to communicate by starting up ndiswrapper it freaks out the system trying to talk to the card that it can see but can't communicate with.

Does that make any sense? People tell me sometimes that some of my ideas only make sense to me.... :P

---

### Post by pytheas22 on 2008-09-23
No, it makes sense.  From the 'dmesg' output that you posted a few weeks ago, however, I think that when b43 crashes it's because of a bug in the driver or firmware, not hardware failure--although I admit that the error messages getting dumped to dmesg are pretty generic, so it is possible that it's simply a hardware issue.

You may want to try burning a copy of the Interpid alpha CD.  If this is a bug with the firmware and/or driver, it should (hopefully) be fixed in Intrepid.

Also, what happens if you type:
```

sudo modprobe b43
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo rmmod b43
```

This would load ndiswrapper with b43 already present, then unload b43 once ndiswrapper has been loaded.  Perhaps this would prevent the crash, but still give control of your card to ndiswrapper.  Does it work?

---

### Post by HieroPosche on 2008-09-24
Thus far that seems to be working.  I was able to load the ndiswrapper module and it's been stable for a couple of hours now. 

Only thing I had to add was:

```
sudo ifconfig wlan0 up
```

and it was able to connect.

I'll let you know if any other issues arise.

---

### Post by HieroPosche on 2008-09-24
Ok.... 

Well, that worked for a little while, but eventually dropped again.

So, considering the B43 module and the ndiswrapper module both drop randomly, should I consider this a hardware issue?

If you don't think that's the case, I can initialize the ndiswrapper module again, wait for it to drop and get a dmesg output for you.

Again I want to thank you for all the assistance you've offered me thus far, you're like, some sort of amazing ubuntu god sent to cleanse me of my whoes...

---

### Post by pytheas22 on 2008-09-25
Are you sure that it was running under ndiswrapper when it dropped before--did you check the output of 'lshw -C Network'?  I don't mean to doubt you; I just find it a bit surprising that this would turn out to be a case of hardware failure after all, which I'd definitely suspect if you're getting the same strange behavior under both drivers.

> 
If you don't think that's the case, I can initialize the ndiswrapper module again, wait for it to drop and get a dmesg output for you.

Sure, that would be useful for ascertaining whether this is hardware or not.

> 
Again I want to thank you for all the assistance you've offered me thus far, you're like, some sort of amazing ubuntu god sent to cleanse me of my whoes...

Actually I'm just a lazy graduate student who devotes too much time to Ubuntu and not enough to early-modern French history, but thanks :)

---

### Post by anachoret on 2008-12-27
In my case (Ubuntu 8.04,  Broadcom BCM4312 802.11a/b/g (rev 01)) with B43 driver drop PERIODICALLY with following messages in the syslog:

kernel: [ 2406.406643] wlan0: RX deauthentication from xx:xx:xx:xx:xx:xx (reason=2)
NetworkManager: <info>  Supplicant state changed: 0 
kernel: [ 2406.406653] wlan0: deauthenticated
kernel: [ 2407.151124] wlan0: authenticate with AP xx:xx:xx:xx:xx:xx
kernel: [ 2407.152311] wlan0: RX authentication from xx:xx:xx:xx:xx:xx (alg=0 transaction=2 status=0)
kernel: [ 2407.152320] wlan0: authenticated
kernel: [ 2407.152324] wlan0: associate with AP xx:xx:xx:xx:xx:xx
kernel: [ 2407.154361] wlan0: RX ReassocResp from xx:xx:xx:xx:xx:xx (capab=0x431 status=0 aid=194)
kernel: [ 2407.154370] wlan0: associated
NetworkManager: <info>  Supplicant state changed: 1 

xx:xx:xx:xx:xx:xx - MAC address

I just switch to  Broadcom STA wireless driver.

---

