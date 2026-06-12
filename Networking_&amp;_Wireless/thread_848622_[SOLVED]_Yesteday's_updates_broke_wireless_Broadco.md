---
title: "[SOLVED] Yesteday's updates broke wireless Broadcom BCM4310 chipset HP Compaq 6720s"
date: 2008-07-03
forum: Networking &amp; Wireless
---

### Post by itsjustarumour on 2008-07-03
Yesterday's automatic updates of the following components broke the wireless on my HP Compaq 6720s laptop with Broadcom BCM 4310 chipset (wl driver):

linux-restricted-modules-2.6.24-19-generic (2.6.24.13-19.42) to 2.6.24.13-19.44
linux-restricted-modules-common (2.6.24.13-19.42) to 2.6.24.13-19.44

I have confirmed this behaviour on 2 different laptops, and 3 Hardy 8.04 installs.

I originally had this problem 6 days ago when these updates first appeared in the "Hardy-Proposed" repository.  However, I disabled that repo and was able to roll back both of these components (Synaptic>Package>Force Version) and easily get things working again.

However, now that the same has happened today when these updates were sent out in the "Hardy-Updates" repo, I can't roll back "linux-restricted-modules-2.6.24-19-generic (2.6.24.13-19.42) to 2.6.24.13-19.44" because "Force Version" is greyed out.

Unfortunately at the moment, my only home Internet access is via a community wireless cloud (I'm sending this from my local coffee shop!) so I'm a bit stuck with getting this working again...

Has anyone got any ideas as to where I should go from here?  And out of curiosity, are there any other "victims" out there with Broadcom 4310 cards? Is this something I should report as a "bug"?

Best regards to all,

itsjustarumour

---

### Post by pytheas22 on 2008-07-03
First you should figure out why the wireless broke.  My guess is a firmware/driver conflict.  Could you please post the output of the command:
```

dmesg
```

here?

---

### Post by gator42 on 2008-07-03
oh thanks for posting...I have not started up my laptop in a few days and I have this model. So I hope to not allow update till i see what is going on.

---

### Post by itsjustarumour on 2008-07-03
> **pytheas22 said:**
> First you should figure out why the wireless broke.  My guess is a firmware/driver conflict.  Could you please post the output of the command:
```

dmesg
```

here?

Hi Pytheas22,

Thanks for the message.  Heres the output from dmesg (sorry in advance if theres rather a lot of this...)  :-)

[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000 [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000 [    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000 [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 518081 [    0.000000] Kernel command line: root=UUID=0ce63566-908d-4a69-8b06-8a166d39269c ro quiet splash  [    0.000000] mapped APIC to ffffb000 (fee00000) [    0.000000] mapped IOAPIC to ffffa000 (fec00000) [    0.000000] Enabling fast FPU save and restore... done. [    0.000000] Enabling unmasked SIMD FPU exception support... done. [    0.000000] Initializing CPU#0 [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes) [    0.000000] Detected 1995.038 MHz processor. [   13.715584] Console: colour VGA+ 80x25 [   13.715587] console [tty0] enabled [   13.715926] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes) [   13.716209] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes) [   13.797051] Memory: 2058760k/2088640k available (2177k kernel code, 28604k reserved, 1006k data, 368k init, 1171136k highmem) [   13.797058] virtual kernel memory layout: [   13.797059]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB) [   13.797060]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB) [   13.797061]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB) [   13.797061]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB) [   13.797062]       .init : 0xc0421000 - 0xc047d000   ( 368 kB) [   13.797063]       .data : 0xc0320434 - 0xc041bdc4   (1006 kB) [   13.797064]       .text : 0xc0100000 - 0xc0320434   (2177 kB) [   13.797066] Checking if this processor honours the WP bit even in supervisor mode... Ok. [   13.797111] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1 [   13.797251] hpet clockevent registered [   13.877213] Calibrating delay using timer specific routine.. 3994.72 BogoMIPS (lpj=7989449) [   13.877235] Security Framework initialized [   13.877242] SELinux:  Disabled at boot. [   13.877256] AppArmor: AppArmor initialized [   13.877260] Failure registering capabilities with primary security module. [   13.877268] Mount-cache hash table entries: 512 [   13.877395] Initializing cgroup subsys ns [   13.877400] Initializing cgroup subsys cpuacct [   13.877411] CPU: After generic identify, caps: afebfbff 20100000 00000000 00000000 0000e31d 00000000 00000001 00000000
[   13.877417] monitor/mwait feature present.
[   13.877419] using mwait in idle threads.
[   13.877423] CPU: L1 I cache: 32K, L1 D cache: 32K
[   13.877425] CPU: L2 cache: 1024K
[   13.877427] CPU: After all inits, caps: afebfbff 20100000 00000000 00003940 0000e31d 00000000 00000001 00000000
[   13.877437] Compat vDSO mapped to ffffe000.
[   13.877449] Checking 'hlt' instruction... OK.
[   13.893570] SMP alternatives: switching to UP code
[   13.894984] Freeing SMP alternatives: 11k freed
[   13.895075] Early unpacking initramfs... done
[   14.183777] ACPI: Core revision 20070126
[   14.183852] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   14.291194] CPU0: Intel(R) Celeron(R) CPU          550  @ 2.00GHz stepping 01
[   14.291218] Total of 1 processors activated (3994.72 BogoMIPS).
[   14.291408] ENABLING IO-APIC IRQs
[   14.291598] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   14.436938] Brought up 1 CPUs
[   14.436958] CPU0 attaching sched-domain:
[   14.436960]  domain 0: span 01
[   14.436961]   groups: 01
[   14.437098] net_namespace: 64 bytes
[   14.437106] HP Compaq Laptop series board detected. Selecting BIOS-method for reboots.
[   14.437109] Booting paravirtualized kernel on bare hardware
[   14.437505] Time:  0:33:36  Date: 07/04/08
[   14.437527] NET: Registered protocol family 16 [   14.437684] EISA bus registered
[   14.437689] ACPI: bus type pci registered
[   14.438962] PCI: PCI BIOS revision 2.10 entry at 0xf0322, last bus=40
[   14.438963] PCI: Using configuration type 1
[   14.438976] Setting up standard PCI resources [   14.440682] ACPI: EC: Look up EC in DSDT
[   14.442579] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   14.489460] ACPI: Interpreter enabled
[   14.489464] ACPI: (supports S0 S3 S4 S5)
[   14.489473] ACPI: Using IOAPIC for interrupt routing
[   14.498226] ACPI: EC: GPE = 0x16, I/O: command/status = 0x66, data = 0x62
[   14.498228] ACPI: EC: driver started in interrupt mode
[   14.498282] ACPI: PCI Root Bridge [C003] (0000:00)
[   14.499333] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   14.499337] PCI quirk: region 1100-113f claimed by ICH6 GPIO
[   14.500098] PCI: Transparent bridge - 0000:00:1e.0
[   14.500143] ACPI: PCI Interrupt Routing Table [\_SB_.C003._PRT]
[   14.500471] ACPI: PCI Interrupt Routing Table [\_SB_.C003.C0B1._PRT]
[   14.500598] ACPI: PCI Interrupt Routing Table [\_SB_.C003.C11E._PRT]
[   14.500719] ACPI: PCI Interrupt Routing Table [\_SB_.C003.C132._PRT]
[   14.500841] ACPI: PCI Interrupt Routing Table [\_SB_.C003.C135._PRT]
[   14.537919] ACPI: PCI Interrupt Link [C12E] (IRQs *10 11)
[   14.538120] ACPI: PCI Interrupt Link [C12F] (IRQs *10 11)
[   14.538318] ACPI: PCI Interrupt Link [C130] (IRQs 10 *11)
[   14.538509] ACPI: PCI Interrupt Link [C131] (IRQs 10 11) *0, disabled.
[   14.538708] ACPI: PCI Interrupt Link [C141] (IRQs *10 11)
[   14.538906] ACPI: PCI Interrupt Link [C142] (IRQs *10 11)
[   14.539105] ACPI: PCI Interrupt Link [C143] (IRQs 10 11) *5
[   14.539201] ACPI Exception (pci_link-0184): AE_NOT_FOUND, Evaluating _PRS [20070126] [   14.539376] ACPI: Power Resource [C29B] (on)
[   14.539423] ACPI: Power Resource [C1C6] (off)
[   14.539522] ACPI: Power Resource [C3B2] (off)
[   14.539616] ACPI: Power Resource [C3B3] (off)
[   14.539709] ACPI: Power Resource [C3B4] (off)
[   14.539802] ACPI: Power Resource [C3B5] (off)
[   14.539895] ACPI: Power Resource [C3B6] (off)
[   14.539943] Linux Plug and Play Support v0.97 (c) Adam Belay
[   14.539970] pnp: PnP ACPI init
[   14.539977] ACPI: bus type pnp registered
[   14.547147] pnp: PnP ACPI: found 12 devices
[   14.547150] ACPI: ACPI bus type pnp unregistered
[   14.547153] PnPBIOS: Disabled by ACPI PNP
[   14.547330] PCI: Using ACPI for IRQ routing
[   14.547332] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   14.680766] NET: Registered protocol family 8
[   14.680768] NET: Registered protocol family 20
[   14.680797] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   14.680800] hpet0: 3 64-bit timers, 14318180 Hz
[   14.681839] AppArmor: AppArmor Filesystem Enabled
[   14.684758] Time: tsc clocksource has been installed.
[   14.684772] Switched to high resolution mode on CPU 0
[   14.692745] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[   14.692748] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
[   14.692750] system 00:00: iomem range 0x100000-0x7f7fffff could not be reserved
[   14.692758] system 00:09: ioport range 0x500-0x57f has been reserved
[   14.692760] system 00:09: ioport range 0x800-0x80f has been reserved
[   14.692763] system 00:09: iomem range 0xffb00000-0xffbfffff could not be reserved
[   14.692765] system 00:09: iomem range 0xfff00000-0xffffffff could not be reserved
[   14.692770] system 00:0a: ioport range 0x4d0-0x4d1 has been reserved
[   14.692772] system 00:0a: ioport range 0x1000-0x107f has been reserved
[   14.692774] system 00:0a: ioport range 0x1100-0x113f has been reserved
[   14.692776] system 00:0a: ioport range 0x1200-0x121f has been reserved
[   14.692778] system 00:0a: iomem range 0xf8000000-0xfbffffff has been reserved
[   14.692781] system 00:0a: iomem range 0xfec00000-0xfec000ff could not be reserved
[   14.692783] system 00:0a: iomem range 0xfed20000-0xfed3ffff could not be reserved
[   14.692785] system 00:0a: iomem range 0xfed45000-0xfed8ffff could not be reserved
[   14.692787] system 00:0a: iomem range 0xfed90000-0xfed99fff could not be reserved
[   14.692792] system 00:0b: iomem range 0xcee00-0xcffff has been reserved
[   14.692794] system 00:0b: iomem range 0xd2000-0xd3fff has been reserved
[   14.692796] system 00:0b: iomem range 0xfeda0000-0xfedbffff could not be reserved
[   14.692798] system 00:0b: iomem range 0xfee00000-0xfee00fff could not be reserved
[   14.723136] PCI: Bridge: 0000:00:1c.0
[   14.723138]   IO window: disabled.
[   14.723144]   MEM window: disabled.
[   14.723148]   PREFETCH window: disabled.
[   14.723154] PCI: Bridge: 0000:00:1c.1
[   14.723155]   IO window: disabled.
[   14.723161]   MEM window: e4000000-e40fffff
[   14.723165]   PREFETCH window: disabled.
[   14.723171] PCI: Bridge: 0000:00:1c.4
[   14.723174]   IO window: 2000-3fff
[   14.723179]   MEM window: e0000000-e3ffffff
[   14.723184]   PREFETCH window: disabled.
[   14.723189] PCI: Bridge: 0000:00:1e.0
[   14.723190]   IO window: disabled.
[   14.723196]   MEM window: disabled. [   14.723200]   PREFETCH window: disabled.
[   14.723238] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   14.723245] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   14.723270] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
[   14.723276] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   14.723300] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 16 (level, low) -> IRQ 16
[   14.723305] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   14.723320] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   14.723330] NET: Registered protocol family 2
[   14.760737] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   14.760944] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   14.761505] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   14.761869] TCP: Hash tables configured (established 131072 bind 65536)
[   14.761871] TCP reno registered
[   14.772823] checking if image is initramfs... it is [   15.336279] Freeing initrd memory: 7322k freed
[   15.336877] audit: initializing netlink socket (disabled)
[   15.336891] audit(1215131616.332:1): initialized
[   15.337063] highmem bounce pool size: 64 pages
[   15.338650] VFS: Disk quotas dquot_6.5.1
[   15.338708] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   15.338829] io scheduler noop registered
[   15.338831] io scheduler anticipatory registered [   15.338832] io scheduler deadline registered
[   15.338841] io scheduler cfq registered (default)
[   15.338853] Boot video device is 0000:00:02.0
[   15.339038] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   15.339098] assign_interrupt_mode Found MSI capability
[   15.339150] Allocate Port Service[0000:00:1c.0:pcie00]
[   15.339252] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   15.339313] assign_interrupt_mode Found MSI capability
[   15.339361] Allocate Port Service[0000:00:1c.1:pcie00]
[   15.339388] Allocate Port Service[0000:00:1c.1:pcie02]
[   15.339487] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   15.339547] assign_interrupt_mode Found MSI capability
[   15.339596] Allocate Port Service[0000:00:1c.4:pcie00]
[   15.339623] Allocate Port Service[0000:00:1c.4:pcie02]
[   15.339841] isapnp: Scanning for PnP cards...
[   15.694452] isapnp: No Plug & Play device found
[   15.716252] Real Time Clock Driver v1.12ac
[   15.716482] hpet_resources: 0xfed00000 is busy
[   15.716525] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   15.717551] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   15.717609] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   15.717693] PNP: PS/2 Controller [PNP0303:C298,PNP0f13:C299] at 0x60,0x64 irq 1,12
[   15.719548] i8042.c: Detected active multiplexing controller, rev 1.1.
[   15.720313] serio: i8042 KBD port at 0x60,0x64 irq 1
[   15.720316] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   15.720318] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   15.720320] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   15.720322] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   15.724296] mice: PS/2 mouse device common for all mice
[   15.724388] EISA: Probing bus 0 at eisa.0
[   15.724395] Cannot allocate resource for EISA slot 1
[   15.724397] Cannot allocate resource for EISA slot 2
[   15.724398] Cannot allocate resource for EISA slot 3
[   15.724400] Cannot allocate resource for EISA slot 4
[   15.724417] EISA: Detected 0 cards.
[   15.724420] cpuidle: using governor ladder
[   15.724421] cpuidle: using governor menu
[   15.724493] NET: Registered protocol family 1
[   15.724518] Using IPI No-Shortcut mode
[   15.724543] registered taskstats version 1
[   15.724620]   Magic number: 0:331:556
[   15.724657]   hash matches device ptya2
[   15.724693]   hash matches device PNP0C0F:07
[   15.724707] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   15.724709] EDD information not available.
[   15.724890] Freeing unused kernel memory: 368k freed
[   15.752132] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   16.911515] fuse init (API version 7.9)
[   16.923950] ACPI: Transitioning device [C3B7] to D3
[   16.923953] ACPI: Transitioning device [C3B7] to D3
[   16.923956] ACPI: Fan [C3B7] (off)
[   16.924137] ACPI: Transitioning device [C3B8] to D3
[   16.924138] ACPI: Transitioning device [C3B8] to D3
[   16.924141] ACPI: Fan [C3B8] (off)
[   16.924320] ACPI: Transitioning device [C3B9] to D3
[   16.924321] ACPI: Transitioning device [C3B9] to D3
[   16.924323] ACPI: Fan [C3B9] (off)
[   16.924501] ACPI: Transitioning device [C3BA] to D3
[   16.924503] ACPI: Transitioning device [C3BA] to D3
[   16.924506] ACPI: Fan [C3BA] (off)
[   16.924683] ACPI: Transitioning device [C3BB] to D3
[   16.924685] ACPI: Transitioning device [C3BB] to D3
[   16.924688] ACPI: Fan [C3BB] (off)
[   16.933794] Monitor-Mwait will be used to enter C-1 state
[   16.933797] Monitor-Mwait will be used to enter C-2 state
[   16.933877] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   16.933880] ACPI: Processor [CPU0] (supports 8 throttling states)
[   16.933894] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   16.938041] ACPI: Thermal Zone [TZ3] (45 C)
[   16.939794] ACPI: Thermal Zone [TZ4] (29 C)
[   16.940185] ACPI: Thermal Zone [TZ5] (67 C)
[   16.946652] ACPI: Thermal Zone [TZ0] (56 C)
[   16.950149] ACPI: Thermal Zone [TZ1] (51 C)
[   17.619050] Intel(R) PRO/1000 Network Driver - version 7.3.20-k2-NAPI
[   17.619054] Copyright (c) 1999-2006 Intel Corporation.
[   17.619114] ACPI: PCI Interrupt 0000:00:19.0[A] -> GSI 22 (level, low) -> IRQ 18
[   17.619127] PCI: Setting latency timer of device 0000:00:19.0 to 64
[   17.647995] e1000: 0000:00:19.0: e1000_probe: (PCI Express:2.5Gb/s:Width x1) 00:1f:29:89:14:68
[   17.648470] usbcore: registered new interface driver usbfs
[   17.648489] usbcore: registered new interface driver hub
[   17.659026] usbcore: registered new device driver usb
[   17.660578] USB Universal Host Controller Interface driver v3.0
[   17.696848] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[   17.696958] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
[   17.696969] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   17.696973] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   17.697209] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[   17.697243] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00004040
[   17.697356] usb usb1: configuration #1 chosen from 1 choice
[   17.697376] hub 1-0:1.0: USB hub found
[   17.697380] hub 1-0:1.0: 2 ports detected
[   17.783325] SCSI subsystem initialized
[   17.799024] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 19
[   17.799036] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   17.799040] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   17.799059] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[   17.799091] uhci_hcd 0000:00:1d.0: irq 19, io base 0x00004060
[   17.799183] usb usb2: configuration #1 chosen from 1 choice [   17.799203] hub 2-0:1.0: USB hub found
[   17.799207] hub 2-0:1.0: 2 ports detected
[   17.818575] libata version 3.00 loaded.
[   17.902959] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 21 (level, low) -> IRQ 20
[   17.902972] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   17.902976] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   17.902996] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[   17.903027] uhci_hcd 0000:00:1d.1: irq 20, io base 0x00004080
[   17.903128] usb usb3: configuration #1 chosen from 1 choice
[   17.903147] hub 3-0:1.0: USB hub found
[   17.903151] hub 3-0:1.0: 2 ports detected
[   18.006895] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 21
[   18.006908] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   18.006913] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   18.006933] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4 [   18.006965] uhci_hcd 0000:00:1d.2: irq 21, io base 0x000040a0
[   18.007062] usb usb4: configuration #1 chosen from 1 choice
[   18.007082] hub 4-0:1.0: USB hub found
[   18.007086] hub 4-0:1.0: 2 ports detected
[   18.110946] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 21
[   18.110961] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   18.110965] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   18.110990] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 5 [   18.114899] ehci_hcd 0000:00:1a.7: debug port 1
[   18.114906] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   18.114913] ehci_hcd 0000:00:1a.7: irq 21, io mem 0xe4621000
[   18.130728] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   18.130830] usb usb5: configuration #1 chosen from 1 choice
[   18.130851] hub 5-0:1.0: USB hub found
[   18.130856] hub 5-0:1.0: 4 ports detected
[   18.234785] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 19
[   18.234801] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   18.234805] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   18.234827] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 6
[   18.238732] ehci_hcd 0000:00:1d.7: debug port 1
[   18.238738] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   18.238744] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xe4628000
[   18.254673] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   18.254772] usb usb6: configuration #1 chosen from 1 choice
[   18.254792] hub 6-0:1.0: USB hub found
[   18.254798] hub 6-0:1.0: 6 ports detected
[   18.361933] ata_piix 0000:00:1f.2: version 2.12
[   18.361941] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[   18.502501] Clocksource tsc unstable (delta = -7460552944 ns)
[   18.506505] Time: hpet clocksource has been installed.
[   18.507290] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 17
[   18.507327] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   18.507406] scsi0 : ata_piix
[   18.507585] scsi1 : ata_piix
[   18.508148] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x40c0 irq 14
[   18.508151] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x40c8 irq 15
[   18.513827] ata1.00: ATA-8: TOSHIBA MK1646GSX, LB114C, max UDMA/100
[   18.513831] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   18.514524] ata1.00: configured for UDMA/100
[   18.524391] ata2.00: ATAPI: MATSHITADVD-RAM UJ-861H, 1.50, max MWDMA2
[   18.529558] ata2.00: configured for MWDMA2
[   18.529661] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK1646GS LB11 PQ: 0 ANSI: 5
[   18.531182] scsi 1:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-861H  1.50 PQ: 0 ANSI: 5
[   18.542875] Driver 'sd' needs updating - please use bus_type methods
[   18.542949] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   18.542959] sd 0:0:0:0: [sda] Write Protect is off
[   18.542961] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   18.542974] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   18.543012] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   18.543020] sd 0:0:0:0: [sda] Write Protect is off
[   18.543021] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   18.543033] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   18.543037]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   18.550027]  sda1 sda2 < sda5 sda6 sda7 sda8 >
[   18.551867] sd 0:0:0:0: [sda] Attached SCSI disk
[   18.557729] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   18.557747] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   18.563691] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   18.563695] Uniform CD-ROM driver Revision: 3.20
[   18.563743] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   18.668764] Attempting manual resume
[   18.668767] swsusp: Resume From Partition 8:6
[   18.668768] PM: Checking swsusp image.
[   18.668959] PM: Resume from disk failed.
[   18.683516] kjournald starting.  Commit interval 5 seconds
[   18.683527] EXT3-fs: mounted filesystem with ordered data mode.
[   20.974181] ip_tables: (C) 2000-2006 Netfilter Core Team
[   21.019722] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   21.666058] Linux agpgart interface v0.102
[   21.833661] agpgart: Detected an Intel 965GME/GLE Chipset.
[   21.833920] agpgart: Detected 7676K stolen memory.
[   21.848021] agpgart: AGP aperture is 256M @ 0xd0000000
[   21.901591] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   21.961588] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   22.070629] input: Power Button (FF) as /devices/virtual/input/input2
[   22.081429] ACPI: Power Button (FF) [PWRF]
[   22.081557] input: Sleep Button (CM) as /devices/virtual/input/input3
[   22.097408] ACPI: Sleep Button (CM) [C2B4]
[   22.097512] input: Lid Switch as /devices/virtual/input/input4
[   22.097605] ACPI: Lid Switch [C154]
[   22.273690] ACPI: AC Adapter [C23A] (on-line)
[   22.377466] ACPI: Battery Slot [C23B] (battery present)
[   22.415453] ACPI: WMI-Acer: Mapper loaded
[   23.417342] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input5
[   23.428603] ACPI: Video Device [C099] (multi-head: yes  rom: no  post: no)
[   24.364979] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   24.365010] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   24.454945] ieee80211_crypt: registered algorithm 'NULL'
[   24.455862] wl: module license 'unspecified' taints kernel.
[   24.455918] wl: Unknown symbol wlc_get
[   24.456127] wl: Unknown symbol wf_channel2mhz
[   24.456156] wl: Unknown symbol wlc_isr
[   24.456203] wl: Unknown symbol wlc_set
[   24.456246] wl: Unknown symbol wlc_statsupd
[   24.456290] wl: Unknown symbol bcm_bprintf
[   24.456430] wl: Unknown symbol wlc_dpc [   24.456498] wl: Unknown symbol wlc_chipmatch
[   24.456548] wl: Unknown symbol wlc_reset
[   24.456634] wl: Unknown symbol wlc_sendpkt
[   24.456703] wl: Unknown symbol wlc_intrsrestore
[   24.456731] wl: Unknown symbol wlc_init
[   24.456763] wl: Unknown symbol bcm_parse_tlvs
[   24.456882] wl: Unknown symbol wlc_down
[   24.456928] wl: Unknown symbol wlc_iovar_getint
[   24.456973] wl: Unknown symbol wlc_iovar_setint [   24.457016] wl: Unknown symbol wlc_up
[   24.457094] wl: Unknown symbol bcm_qdbm_to_mw
[   24.457124] wl: Unknown symbol bcm_mkiovar
[   24.457161] wl: Unknown symbol wlc_intrsoff
[   24.457191] wl: Unknown symbol bcm_mw_to_qdbm
[   24.457238] wl: Unknown symbol wlc_intrsupd
[   24.457267] wl: Unknown symbol wlc_ioctl
[   24.457309] wl: Unknown symbol wf_mhz2channel
[   24.457338] wl: Unknown symbol wlc_intrson
[   24.457367] wl: Unknown symbol wlc_attach
[   24.457426] wl: Unknown symbol wlc_iovar_op
[   24.457454] wl: Unknown symbol wlc_detach
[   24.457494] wl: Unknown symbol pktsetprio
[   24.668672] iTCO_vendor_support: vendor-support=0
[   24.684906] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   24.685015] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x1060)
[   24.685065] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   25.219624] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   25.963347] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x200000
[   26.003358] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input7
[   26.944769] lp: driver loaded but no devices found
[   27.091768] Adding 5140760k swap on /dev/sda6.  Priority:-1 extents:1 across:5140760k
[   27.174787] EXT3 FS on sda5, internal journal
[   27.785215] No dock devices found.
[   28.408652] apm: BIOS not found.
[   28.450261] ppdev: user-space parallel port driver
[   28.467060] audit(1215128048.404:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5085 profile="/usr/sbin/cupsd" namespace="default"
[   29.247275] Bluetooth: Core ver 2.11
[   29.247803] NET: Registered protocol family 31 [   29.247806] Bluetooth: HCI device and connection manager initialized
[   29.247809] Bluetooth: HCI socket layer initialized
[   29.279455] Bluetooth: L2CAP ver 2.9
[   29.279460] Bluetooth: L2CAP socket layer initialized
[   29.335213] Bluetooth: RFCOMM socket layer initialized
[   29.335227] Bluetooth: RFCOMM TTY layer initialized
[   29.335229] Bluetooth: RFCOMM ver 1.8
[   30.530468] [drm] Initialized drm 1.1.0 20060810
[   30.533170] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   30.533178] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   30.533257] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   33.846327] NET: Registered protocol family 10
[   33.846733] lo: Disabled Privacy Extensions
[   33.847279] ADDRCONF(NETDEV_UP): eth0: link is not ready
ian@COOLERMASTER3:~$

---

### Post by kinkdxm on 2008-07-03
I had the same problems on a dell.
Someone else did on a hp as well.
[http://ubuntuforums.org/showthread.php?p=5310468](http://ubuntuforums.org/showthread.php?p=5310468)

I have no idea how to file a bug report or I would.

---

### Post by pytheas22 on 2008-07-03
It looks like this problem is really new, but it is definitely a bug that's affecting other people, and a report is filed (from 29 June): [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/243930](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/243930) .  Unfortunately no one has suggested a solution yet.  Hopefully they will soon.  In the meantime, I don't own this card but if I can think of anything to work around the problem, I'll let you know.

It should also work to boot into the older kernel--at the boot menu you should have two different kernels to boot into.  Choose the second one and see if the wireless works under that.

---

### Post by kinkdxm on 2008-07-03
Just booted into a older one. Still no wireless. Thanks for the idea though.

---

### Post by itsjustarumour on 2008-07-03
> **pytheas22 said:**
> It looks like this problem is really new, but it is definitely a bug that's affecting other people, and a report is filed (from 29 June): [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/243930](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/243930) .  Unfortunately no one has suggested a solution yet.  Hopefully they will soon.  In the meantime, I don't own this card but if I can think of anything to work around the problem, I'll let you know.

It should also work to boot into the older kernel--at the boot menu you should have two different kernels to boot into.  Choose the second one and see if the wireless works under that.

Thanks for the post, and the link to the bug report on Launchpad (which I've updated). :-) Looks like we'll just have to wait and see what happens now.  I couldn't get this to work by booting into an older kernel by the way - I only had 2.6.24-16, although the bug report suggests that 2.6.24-18 should work.

Thanks again,

itsjustarumour

---

### Post by corwinspyre on 2008-07-03
> **itsjustarumour said:**
> Thanks for the post, and the link to the bug report on Launchpad (which I've updated). :-) Looks like we'll just have to wait and see what happens now.  I couldn't get this to work by booting into an older kernel by the way - I only had 2.6.24-16, although the bug report suggests that 2.6.24-18 should work.

Thanks again,

itsjustarumour

Same for me.  Also, the restricted drivers window looks like this:
[img]http://i25.tinypic.com/33yjd5v.png[/img]

---

### Post by kinkdxm on 2008-07-03
Only had the 16 kernel version as well.

---

### Post by dhruvraj on 2008-07-04
I have the exact same issue on a Dell using BCM4310. 

The driver was working seamlessly till the last time I updated packages (yesterday) - it shows not in use now, and if I enable it asks for a restart - after which it still says not in use. bah.

frustrating 

Getting b43 to work seems like a never ending effort

---

### Post by mringer on 2008-07-04
I have a problem that looks superficially similar on different h-ware. 
I cannot recall exactly
when I updated or what updates got installed, please is there a log somewhere? As a temp work-around I got wireless to work using this
post:

[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

but the interface name has changed, it used to be eth1 & is now wlan0.

---

### Post by pytheas22 on 2008-07-04
> when I updated or what updates got installed, please is there a log somewhere?

Yes, type "gedit /var/log/dpkg.log" to view the log.

> As a temp work-around I got wireless to work using this
post:

[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

but the interface name has changed, it used to be eth1 & is now wlan0.

What exactly did you do from that post to get your card working?  Did you install ndiswrapper, which would explain why eth1 changed to wlan0?  If not, then let us know what you did because maybe a solution/workaround to the wl driver problem lies there.

Otherwise, switching to ndiswrapper would be a solution for everyone with this problem.  You just need to add wl to /etc/modprobe.d/blacklist, install ndiswrapper (sudo apt-get install ndiswrapper* ndisgtk) and then install the Windows drivers for your card.  But hopefully the problem with the native driver will just be fixed soon.

---

### Post by mexpolk on 2008-07-04
The same with me...

```


$ dmesg | grep wl

[   24.390807] wl: module license 'unspecified' taints kernel.
[   24.390847] wl: Unknown symbol wlc_get
[   24.391028] wl: Unknown symbol wf_channel2mhz
[   24.391055] wl: Unknown symbol wlc_isr
[   24.391100] wl: Unknown symbol wlc_set
[   24.391141] wl: Unknown symbol wlc_statsupd
[   24.391183] wl: Unknown symbol bcm_bprintf
[   24.391320] wl: Unknown symbol wlc_dpc
[   24.391387] wl: Unknown symbol wlc_chipmatch
[   24.391434] wl: Unknown symbol wlc_reset
[   24.391518] wl: Unknown symbol wlc_sendpkt
[   24.391584] wl: Unknown symbol wlc_intrsrestore
[   24.391611] wl: Unknown symbol wlc_init
[   24.391641] wl: Unknown symbol bcm_parse_tlvs
[   24.391758] wl: Unknown symbol wlc_down
[   24.391801] wl: Unknown symbol wlc_iovar_getint
[   24.391844] wl: Unknown symbol wlc_iovar_setint
[   24.391884] wl: Unknown symbol wlc_up
[   24.391961] wl: Unknown symbol bcm_qdbm_to_mw
[   24.391988] wl: Unknown symbol bcm_mkiovar
[   24.392024] wl: Unknown symbol wlc_intrsoff
[   24.392052] wl: Unknown symbol bcm_mw_to_qdbm
[   24.392097] wl: Unknown symbol wlc_intrsupd
[   24.392123] wl: Unknown symbol wlc_ioctl
[   24.392164] wl: Unknown symbol wf_mhz2channel
[   24.392190] wl: Unknown symbol wlc_intrson
[   24.392217] wl: Unknown symbol wlc_attach
[   24.392273] wl: Unknown symbol wlc_iovar_op
[   24.392300] wl: Unknown symbol wlc_detach
[   24.392337] wl: Unknown symbol pktsetprio


```

Immediately after notice the problem, I tried to boot with older kernel but I only have revision 16 and 19. So no luck with booting with older kernel.

Hardy has been a mayor nightmare to me!!! I miss Gutsy | Feisty (performed better out of the box) :(

---

### Post by mexpolk on 2008-07-04
Update:

I tried installing linux-image-2.6.24-18-generic and nothing. Te driver isn't listed at all (wl).

---

### Post by bdamon on 2008-07-04
Same problem here. BCM4310

---

### Post by mringer on 2008-07-04
> **pytheas22 said:**
> 
[snip]
What exactly did you do from that post to get your card working?  

This is a long story, I will give outline only.

Dell Inspiron 1525, B-com 4310 (we all LOVE these, dont we?). 
Installed X-Ub 8.04, network manager, and then ndiswrapper after 
other attempts failed. Ref:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

This worked partially. About 2 weeks ago I installed WICD which was working until yesterday. (July 4)

Late last night: updated lots of things including the Linux restricted modules mentioned in the first post. 

This morning: wireless dead.

I am sure that I correctly remember that before the crash the wired net device was eth0  and the wireless was eth1.  Now eth1 seems to have vanished, e.g.

sudo ifconfig eth1
error: no such device

To answer the actual question:

sudo ifconfig eth0 down
sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid "X"
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0

where "X" stands for the actual essid.

This worked for me. I am sorry but if it doesnt work for you, I cannot help any further.

---

### Post by mexpolk on 2008-07-04
I've found a post that fixed the problem, thanks to **[Nathan.Flow]("http://backports.ubuntuforums.com/member.php?u=233875")** who posted it **[here]("http://backports.ubuntuforums.com/showthread.php?t=650729&page=2")**.

1. Download latest stable **[ndiswrapper]("http://ndiswrapper.sourceforge.net/joomla/")**. And compile and install it (make, make install).
2. Download your latest AND CORRECT drivers. I've an XPS M-1330 with Broadcom BCM4310 USB, and I downloaded drivers from **[here]("http://support.dell.com/support/downloads/download.aspx?c=us&cs=12&l=en&s=bsdv&releaseid=R174291&SystemID=VOS_N_1500&servicetag=&os=WW1&osl=en&deviceid=9805&devlib=0&typecnt=0&vercnt=4&catid=5&impid=-1&formatcnt=1&libid=5&fileid=236819")**.
2. Follow **[this]("http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper")** instructions.

Hope that works for you also.

---

### Post by qwallis on 2008-07-04
> **pytheas22 said:**
> 
It should also work to boot into the older kernel--at the boot menu you should have two different kernels to boot into.  Choose the second one and see if the wireless works under that.
I got things working by stepping back to *14 which was still listed in GRUB: but I read other posts saying a clean install would work so tried that and am still suffering the problem with no other boot options.

Looks like you can add [D-Link's DWL-G510]("http://ubuntuforums.org/showthread.php?t=849635") to the list of cards affected.
:(

---

### Post by otto3108 on 2008-07-04
I can also confirm problems after an upgrade to the latest kernel. I'm using Gutsy on a Compaq Presario C310 (Broadcom 4311) and upgraded to kernel 15 last night. No wireless found this morning, but reverting to previous kernel in the Boot loader has restored wireless functionality.

---

### Post by pytheas22 on 2008-07-05
> I've found a post that fixed the problem, thanks to Nathan.Flow who posted it here.

1. Download latest stable ndiswrapper. And compile and install it (make, make install).
2. Download your latest AND CORRECT drivers. I've an XPS M-1330 with Broadcom BCM4310 USB, and I downloaded drivers from here.
2. Follow this instructions.

Hope that works for you also.

Just to be clear: ndiswrapper is not really a solution, just a work-around.  ndiswrapper is a utility to drive wireless devices using Windows drivers.  The problem that everyone's having with BCM4310 is that there's a bug with the native Linux driver in the most recent release (which has been pushed out via Ubuntu updates), which hopefully will be solved very soon.  It's better to use the native Linux driver whenever possible...ndiswrapper is from the days when few vendors offered any Linux support and using Windows drivers was the only option.  Fortunately those days are gone in most cases and ndiswrapper is not necessary for most people, although it will still work.  But Broadcom's drivers, which were painstakingly reverse-engineered because Broadcom has always been really nasty about open-source support (despite the fact that it makes millions putting its chips in wireless routers that ironically run Linux), offer more features and are easier to fix than ndiswrapper, so you should use wl where possible.

If you want to use ndiswrapper as a temporary solution to this problem, however, you need to add the line:
```

blacklist wl
```

to the file /etc/modprobe.d/blacklist, then install ndiswrapper (plenty of guides online).  To go back to the native driver when it gets repaired, remove that line from /etc/modprobe.d/blacklist and replace it with the line:
```

blacklist ndiswrapper
```

(I don't have any qualms with ndiswrapper, but I've been troubled lately by mass confusion--particularly among the Broadcom crowd--about what it is and what it is not, which I think results from badly written documentation, so I wanted to point this out.)

---

### Post by itsjustarumour on 2008-07-05
> **pytheas22 said:**
> Just to be clear: ndiswrapper is not really a solution, just a work-around.  ndiswrapper is a utility to drive wireless devices using Windows drivers.  The problem that everyone's having with BCM4310 is that there's a bug with the native Linux driver in the most recent release (which has been pushed out via Ubuntu updates), which hopefully will be solved very soon.  It's better to use the native Linux driver whenever possible...

I totally agree with pytheas22's comments above. Nsiswrapper is just a workaround, and as this wireless problem is caused by a bug then really this is something that Ubuntu should fix - and hopefully fix very promptly - without having to resort to Ndiswrapper.  

On a more personal note, I've been using Ubuntu for 2 years and during that time have spent literally many tens of hours trying to get Ndiswrapper to work (or work properly) on various Ubuntu installs, and with very mixed results.  To be honest I've reached a point where I just consider life too short to spend any more time battling with it. I for one will just be sitting tight and awaiting a fix from Ubuntu for the wl driver - its a pain in the a*se, and if I get REALLY desperate I'll just have to re-install the OS without these updates (yet more pain in the a*se!) but frankly, for me at least, anything is preferable to Ndiswrapper!

---

### Post by mexpolk on 2008-07-05
Yes that's a work around... 
that's why I didn't put a smiley face icon.

Aldo, interesting workaround from pytheas22. 
Simpler than mine! But I have to argue that wl driver never worked for me, before this update couldn't make **_[SSH]("http://ubuntuforums.org/showthread.php?t=823127")_**, couldn't make F-Spot signup to Facebook, etc. Only with wired network.

For me, Hardy has been the hardest release ever!

---

### Post by pytheas22 on 2008-07-05
> Aldo, interesting workaround from pytheas22.
Simpler than mine! But I have to argue that wl driver never worked for me, before this update couldn't make SSH, couldn't make F-Spot signup to Facebook, etc. Only with wired network.

Well really your solution is just as simple as mine...I just didn't list all the steps to installing ndiswrapper since there are plenty of guides online.  I did point out that you have to blacklist the "wl" driver first, because not all ndiswrapper tutorials mention that and it can be a confusing source of problems for new users.  ndiswrapper won't work on a BCM4310 card unless wl is blacklisted.

---

### Post by itsjustarumour on 2008-07-07
Looks like a fix for this is on its way very soon.

To quote dev Ben Collins on the bug thread at [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/243930](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/243930)

"I've uploaded the fix for this to hardy-proposed. Needs to be processed."

Don't touch that dial, folks!  :-D

---

### Post by Hoaxe on 2008-07-08
so i can stop freaking out now?

---

### Post by itsjustarumour on 2008-07-08
Lol, I guess so!  :-D

---

### Post by loolee on 2008-07-08
Hi
I've the same problem on Hp6720s.
I don't want to use ndisWrapper, could you help me please?

Tnx ;)

---

### Post by itsjustarumour on 2008-07-08
> **loolee said:**
> Hi
I've the same problem on Hp6720s.
I don't want to use ndisWrapper, could you help me please?

Tnx ;)

Hi Loolee, 

I should just hang fire until the official update comes out to fix this :-)

---

### Post by carltonh on 2008-07-08
Still no luck on the Dell Inspiron 1525 that I bought yesterday, but I can also report that the liveCDs for Sidux 2008.02 and Sabayon 3.5 don't work either.  A little surprised on Sabayon not working because it supports the bcm4318 out of the box.

---

### Post by Charles Sloan on 2008-07-08
I'm glad that I read up on this, since when I first installed Ubuntu after the updates it worked without a hitch. Then I experimented with Mandriva which only confirmed my initial choice of distros with Ubuntu. Then I reinstall x64 only to find the wireless is out...

But its a relief that at least this is being looked into. Although isn't there a way to somehow roll back the update to the previous release for the time being?

---

### Post by Charles Sloan on 2008-07-08
I noticed that from the link that was provided there was a fix (at least for one person):

> Through the Synaptic Package Manager, I enabled the "hardy-backports" repository and was able to remove the 2.6.24-19 modules to install the 2.6.24-18.41 modules and it worked for me (granted, I'm on a 64-bit rather than a 32-bit).

Either way, if you aren't seeing more than one version of the restricted modules, make sure you have the backports repository enabled.


But I couldn't find an 2.6.24-18.41 mod, the highest I found was 2.6.24-18.16. Is that because I have a new install without the previous update?

---

### Post by loolee on 2008-07-09
Hi! if I enter with 2.6.24-18- kernel I've got the wireless... but I've lost the audio :D

it's incredible.

Anyway, I wait, I think it's better.

---

### Post by pytheas22 on 2008-07-09
I don't know if this will help, but I remembered that apt-get caches all packages for a long time.  So if you open up /var/cache/apt/archives, you will find all the packages for all of the updates that you've ever installed.  Various versions of linux-restricted-modules should be in there.  Try installing an earlier version of that package (you can just double-click to start the installer) and see if it helps.

As a disclaimer, I don't know if the installation will even work (there may be dependency issues that are unresolvable offline, although I don't think so), let alone fix the problem.  And if something weird happens (in principle it shouldn't, but I can't make any guarantees), it could mess up your system, so don't say I didn't warn you.

I don't have a BCM4310 card so I can't test it myself.  But if you're desperate for a fix, it's worth a shot.  The fix mentioned in the bug report still isn't in hardy-proposed, so I don't know what the timetable is going to be on pushing a patch out.

---

### Post by Hoaxe on 2008-07-09
i am confirming that the updated linux packages in the proposed sources have fixed my wireless.

more info here: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/243930](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/243930)

---

### Post by dhruvraj on 2008-07-09
Yes the update works, select system->administration->software sources

under the update tab select hardy-proposed, and install the restricted drivers module and restart your computer

---

### Post by itsjustarumour on 2008-07-09
Also confirming that now working fine on Ubuntu 8.04.1 32-bit, HP Compaq 6720s with a Broadcom BCM4310 chipset.

Took me an hour and three quarters to download the fix on a GPRS connection, but it sure feels good to be "back on the air"... :-)

---

### Post by Mike V on 2008-07-09
Confirming Dell Inspiron I1525-119B with Dell 1395 Wireless minicard working with the fix posted on launchpad, using Hardy Heron 32bit, enabling the proposed repos, same previous issues as everyone else, the update kill my wireless and the proposed get it back, now booting again Ubuntu everywhere XD

---

### Post by carltonh on 2008-07-09
This is not resolved for me by following the hardy-proposed directions.  However, I'm using a 2 day old laptop and so maybe the fix only relates to those who already had the 4310 working?  According to [http://www.linuxwireless.org/en/users/Drivers/b43](http://www.linuxwireless.org/en/users/Drivers/b43) the b43 driver is "not supported" for the bcm4310 card.

So what are y'all additionally doing to get this to work?

---

### Post by itsjustarumour on 2008-07-09
> **carltonh said:**
> This is not resolved for me by following the hardy-proposed directions.  However, I'm using a 2 day old laptop and so maybe the fix only relates to those who already had the 4310 working?  According to [http://www.linuxwireless.org/en/users/Drivers/b43](http://www.linuxwireless.org/en/users/Drivers/b43) the b43 driver is "not supported" for the bcm4310 card.

So what are y'all additionally doing to get this to work?

@carltonh,

This thread relates to the "wl" driver rather than the "b43" one you're trying to use.  I checked the thread you quote, and see you're trying to use it with b43-fwcutter - I'd ditch that method if you have a BCM4310 chipset and just try installing the new Hardy packages 

linux-restricted-modules-2.6.24-19-generic (2.6.24.13-19.45)
linux-restricted-modules-common (2.6.24.13-19.45) 

Then System>Administration>Hardware Drivers and make sure "wl" is enabled.

---

### Post by kinkdxm on 2008-07-10
Works on dell inspiron 1525.

---

### Post by loolee on 2008-07-10
now it's OK on my HP6720s ;)

---

### Post by Charles Sloan on 2008-07-10
Confirmed to work on my HP Pavilion DV2740SE laptop running x64.

---

