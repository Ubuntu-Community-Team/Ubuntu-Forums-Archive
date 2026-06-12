---
title: "Slow boot up, networking problem?"
date: 2008-05-20
forum: Networking &amp; Wireless
---

### Post by muadnu on 2008-05-20
I have a Dell Vostro 1400 with Hardy 64 bit running. My boot up time is starting to get annoyingly long, and I think it has to do with some networking issue, though I don't know what's going on (see the output of dmesg below, I marked in bold the parts that seem to be taking long). There are a couple of parts where the boot up process is getting stuck, some have to do with networking, another with bluetooth, and a last one that I don't know how to interpret.

In general it's taking, from grub to having gnome ready, anything from 90 seconds to, say, 3 minutes (it varies). It goes from grub to starting gnome pretty fast (I'm using auto login), but then it gets stuck in, first, colored background, and then showing only my wallpaper. I think this doesn't have to do with gnome though, if I'm not mistaken part of the boot up process is still being done while gnome loads. 

Here's the output of dmesg after having logged in (I'm skipping the first part but including all the rest, just in case):

```

[   11.063673] Marking TSC unstable due to TSCs unsynchronized
[   11.063675] time.c: Detected 1994.999 MHz processor.
[   11.065822] Console: colour VGA+ 80x25
[   11.065825] console [tty0] enabled
[   11.065841] Checking aperture...
[   11.065853] Calgary: detecting Calgary via BIOS EBDA area
[   11.065855] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[   11.085865] Memory: 2053520k/2095540k available (2466k kernel code, 41632k reserved, 1309k data, 316k init)
[   11.085899] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   11.165602] Calibrating delay using timer specific routine.. 3994.53 BogoMIPS (lpj=7989073)
[   11.165635] Security Framework initialized
[   11.165642] SELinux:  Disabled at boot.
[   11.165654] AppArmor: AppArmor initialized
[   11.165658] Failure registering capabilities with primary security module.
[   11.165872] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   11.167197] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   11.167780] Mount-cache hash table entries: 256
[   11.167917] CPU: L1 I cache: 32K, L1 D cache: 32K
[   11.167920] CPU: L2 cache: 4096K
[   11.167922] CPU 0/0 -> Node 0
[   11.167924] using mwait in idle threads.
[   11.167925] CPU: Physical Processor ID: 0
[   11.167926] CPU: Processor Core ID: 0
[   11.167932] CPU0: Thermal monitoring enabled (TM2)
[   11.167945] SMP alternatives: switching to UP code
[   11.168694] Early unpacking initramfs... done
[   11.529341] ACPI: Core revision 20070126
[   11.529382] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   11.573459] Using local APIC timer interrupts.
[   11.623560] APIC timer calibration result 12468740
[   11.623562] Detected 12.468 MHz APIC timer.
[   11.623639] SMP alternatives: switching to SMP code
[   11.624279] Booting processor 1/2 APIC 0x1
[   11.634771] Initializing CPU#1
[   11.711516] Calibrating delay using timer specific routine.. 3989.96 BogoMIPS (lpj=7979920)
[   11.711523] CPU: L1 I cache: 32K, L1 D cache: 32K
[   11.711524] CPU: L2 cache: 4096K
[   11.711526] CPU 1/1 -> Node 0
[   11.711527] CPU: Physical Processor ID: 0
[   11.711528] CPU: Processor Core ID: 1
[   11.711534] CPU1: Thermal monitoring enabled (TM2)
[   11.712029] Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz stepping 0a
[   11.712105] Brought up 2 CPUs
[   11.712186] CPU0 attaching sched-domain:
[   11.712188]  domain 0: span 03
[   11.712189]   groups: 01 02
[   11.712192]   domain 1: span 03
[   11.712193]    groups: 03
[   11.712195] CPU1 attaching sched-domain:
[   11.712197]  domain 0: span 03
[   11.712198]   groups: 02 01
[   11.712200]   domain 1: span 03
[   11.712201]    groups: 03
[   11.712406] net_namespace: 120 bytes
[   11.712775] Time:  1:02:47  Date: 05/21/08
[   11.712798] NET: Registered protocol family 16
[   11.712965] ACPI: bus type pci registered
[   11.713031] PCI: Using configuration type 1
[   11.719952] ACPI: EC: Look up EC in DSDT
[   11.763352] ACPI: Interpreter enabled
[   11.763355] ACPI: (supports S0 S3 S4 S5)
[   11.763367] ACPI: Using IOAPIC for interrupt routing
[   11.782919] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   11.783880] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   11.783884] PCI quirk: region 1080-10bf claimed by ICH6 GPIO
[   11.785591] PCI: Transparent bridge - 0000:00:1e.0
[   11.785642] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   11.786120] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[   11.786267] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[   11.786363] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[   11.786479] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[   11.786591] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[   11.786702] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[   11.797436] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 11) *7
[   11.797544] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
[   11.797649] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 11) *4
[   11.797754] ACPI: PCI Interrupt Link [LNKD] (IRQs *5 7 9 10 11)
[   11.797859] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   11.797965] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   11.798071] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   11.798170] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   11.798299] Linux Plug and Play Support v0.97 (c) Adam Belay
[   11.798326] pnp: PnP ACPI init
[   11.798332] ACPI: bus type pnp registered
[   11.835263] pnpacpi: exceeded the max number of mem resources: 12
[   11.835454] pnp: PnP ACPI: found 12 devices
[   11.835456] ACPI: ACPI bus type pnp unregistered
[   11.835656] PCI: Using ACPI for IRQ routing
[   11.835658] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   11.847458] NET: Registered protocol family 8
[   11.847459] NET: Registered protocol family 20
[   11.847488] PCI-GART: No AMD northbridge found.
[   11.847494] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   11.847497] hpet0: 3 64-bit timers, 14318180 Hz
[   11.848528] AppArmor: AppArmor Filesystem Enabled
[   11.851438] Time: hpet clocksource has been installed.
[   11.851447] Switched to high resolution mode on CPU 0
[   11.851966] Switched to high resolution mode on CPU 1
[   11.859426] system 00:05: ioport range 0xc80-0xcff could not be reserved
[   11.859433] system 00:08: iomem range 0xfed00000-0xfed003ff has been reserved
[   11.859437] system 00:09: ioport range 0x900-0x97f has been reserved
[   11.859440] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
[   11.859442] system 00:09: ioport range 0x1000-0x1005 has been reserved
[   11.859444] system 00:09: ioport range 0x1008-0x100f has been reserved
[   11.859449] system 00:0a: ioport range 0xf400-0xf4fe has been reserved
[   11.859451] system 00:0a: ioport range 0x1006-0x1007 has been reserved
[   11.859453] system 00:0a: ioport range 0x100a-0x1059 could not be reserved
[   11.859455] system 00:0a: ioport range 0x1060-0x107f has been reserved
[   11.859458] system 00:0a: ioport range 0x1080-0x10bf has been reserved
[   11.859460] system 00:0a: ioport range 0x10c0-0x10df has been reserved
[   11.859462] system 00:0a: ioport range 0x1010-0x102f has been reserved
[   11.859464] system 00:0a: ioport range 0x809-0x809 has been reserved
[   11.859469] system 00:0b: iomem range 0x0-0x9efff could not be reserved
[   11.859471] system 00:0b: iomem range 0x9f000-0x9ffff could not be reserved
[   11.859473] system 00:0b: iomem range 0xc0000-0xcffff has been reserved
[   11.859475] system 00:0b: iomem range 0xe0000-0xfffff has been reserved
[   11.859478] system 00:0b: iomem range 0x100000-0x7fe6d7ff could not be reserved
[   11.859480] system 00:0b: iomem range 0x7fe6d800-0x7fefffff could not be reserved
[   11.859482] system 00:0b: iomem range 0x7ff00000-0x7fffffff could not be reserved
[   11.859484] system 00:0b: iomem range 0x7ff00000-0x806fffff could not be reserved
[   11.859487] system 00:0b: iomem range 0xfff00000-0xffffffff could not be reserved
[   11.859489] system 00:0b: iomem range 0xffa00000-0xffafffff has been reserved
[   11.859492] system 00:0b: iomem range 0xfec00000-0xfec0ffff could not be reserved
[   11.859494] system 00:0b: iomem range 0xfee00000-0xfee0ffff could not be reserved
[   11.859856] PCI: Bridge: 0000:00:01.0
[   11.859859]   IO window: e000-efff
[   11.859862]   MEM window: fa000000-feafffff
[   11.859864]   PREFETCH window: e0000000-efffffff
[   11.859867] PCI: Bridge: 0000:00:1c.0
[   11.859868]   IO window: disabled.
[   11.859874]   MEM window: disabled.
[   11.859877]   PREFETCH window: disabled.
[   11.859883] PCI: Bridge: 0000:00:1c.1
[   11.859884]   IO window: disabled.
[   11.859890]   MEM window: f9f00000-f9ffffff
[   11.859893]   PREFETCH window: disabled.
[   11.859899] PCI: Bridge: 0000:00:1c.3
[   11.859902]   IO window: d000-dfff
[   11.859907]   MEM window: f9c00000-f9efffff
[   11.859911]   PREFETCH window: f0000000-f01fffff
[   11.859917] PCI: Bridge: 0000:00:1c.5
[   11.859918]   IO window: disabled.
[   11.859923]   MEM window: f9b00000-f9bfffff
[   11.859927]   PREFETCH window: disabled.
[   11.859933] PCI: Bridge: 0000:00:1e.0
[   11.859934]   IO window: disabled.
[   11.859939]   MEM window: f9a00000-f9afffff
[   11.859943]   PREFETCH window: disabled.
[   11.859959] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   11.859963] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   11.859985] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   11.859990] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   11.860014] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
[   11.860020] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   11.860043] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 19
[   11.860048] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   11.860071] ACPI: PCI Interrupt 0000:00:1c.5[B] -> GSI 17 (level, low) -> IRQ 17
[   11.860077] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[   11.860090] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   11.860099] NET: Registered protocol family 2
[   11.895468] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[   11.896107] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[   11.897577] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   11.898071] TCP: Hash tables configured (established 262144 bind 65536)
[   11.898073] TCP reno registered
[   11.907518] checking if image is initramfs... it is
[   12.617941] Freeing initrd memory: 7947k freed
[   12.621597] Simple Boot Flag at 0x79 set to 0x1
[   12.622361] audit: initializing netlink socket (disabled)
[   12.622381] audit(1211331768.516:1): initialized
[   12.624273] VFS: Disk quotas dquot_6.5.1
[   12.624334] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   12.624447] io scheduler noop registered
[   12.624449] io scheduler anticipatory registered
[   12.624450] io scheduler deadline registered
[   12.624538] io scheduler cfq registered (default)
[   12.628380] Boot video device is 0000:01:00.0
[   12.628526] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   12.628559] assign_interrupt_mode Found MSI capability
[   12.628585] Allocate Port Service[0000:00:01.0:pcie00]
[   12.628618] Allocate Port Service[0000:00:01.0:pcie02]
[   12.628687] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   12.628744] assign_interrupt_mode Found MSI capability
[   12.628790] Allocate Port Service[0000:00:1c.0:pcie00]
[   12.628817] Allocate Port Service[0000:00:1c.0:pcie02]
[   12.628913] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   12.628971] assign_interrupt_mode Found MSI capability
[   12.629017] Allocate Port Service[0000:00:1c.1:pcie00]
[   12.629043] Allocate Port Service[0000:00:1c.1:pcie02]
[   12.629140] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   12.629198] assign_interrupt_mode Found MSI capability
[   12.629243] Allocate Port Service[0000:00:1c.3:pcie00]
[   12.629270] Allocate Port Service[0000:00:1c.3:pcie02]
[   12.629366] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[   12.629424] assign_interrupt_mode Found MSI capability
[   12.629469] Allocate Port Service[0000:00:1c.5:pcie00]
[   12.629499] Allocate Port Service[0000:00:1c.5:pcie02]
[   12.650569] Real Time Clock Driver v1.12ac
[   12.650699] hpet_resources: 0xfed00000 is busy
[   12.650750] Linux agpgart interface v0.102
[   12.650752] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   12.651969] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   12.652026] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   12.652107] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   12.655335] serio: i8042 KBD port at 0x60,0x64 irq 1
[   12.655339] serio: i8042 AUX port at 0x60,0x64 irq 12
[   12.667986] mice: PS/2 mouse device common for all mice
[   12.668017] cpuidle: using governor ladder
[   12.668019] cpuidle: using governor menu
[   12.668128] NET: Registered protocol family 1
[   12.668173] registered taskstats version 1
[   12.668295]   Magic number: 8:634:3
[   12.668300]   hash matches device ttybe
[   12.668367] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   12.668370] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   12.668371] EDD information not available.
[   12.668377] Freeing unused kernel memory: 316k freed
[   12.671563] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   13.849710] fuse init (API version 7.9)
[   13.898469] ACPI: SSDT 7FE6E4F2, 0286 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[   13.898655] ACPI: SSDT 7FE6DE88, 05E5 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[   13.899157] Monitor-Mwait will be used to enter C-1 state
[   13.899159] Monitor-Mwait will be used to enter C-2 state
[   13.899161] Monitor-Mwait will be used to enter C-3 state
[   13.899268] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   13.899272] ACPI: Processor [CPU0] (supports 8 throttling states)
[   13.899471] ACPI: SSDT 7FE6E778, 00C4 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
[   13.899640] ACPI: SSDT 7FE6E46D, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
[   13.900333] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   13.900337] ACPI: Processor [CPU1] (supports 8 throttling states)
[   13.906095] ACPI: Thermal Zone [THM] (40 C)
[   14.174119] usbcore: registered new interface driver usbfs
[   14.174138] usbcore: registered new interface driver hub
[   14.175870] usbcore: registered new device driver usb
[   14.176983] USB Universal Host Controller Interface driver v3.0
[   14.177041] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 20 (level, low) -> IRQ 20
[   14.177053] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   14.177057] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   14.177345] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[   14.177379] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00006f20
[   14.177491] usb usb1: configuration #1 chosen from 1 choice
[   14.177510] hub 1-0:1.0: USB hub found
[   14.177514] hub 1-0:1.0: 2 ports detected
[   14.243262] SCSI subsystem initialized
[   14.255355] libata version 3.00 loaded.
[   14.279076] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 21
[   14.279091] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   14.279095] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   14.279119] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[   14.279154] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00006f00
[   14.279255] usb usb2: configuration #1 chosen from 1 choice
[   14.279273] hub 2-0:1.0: USB hub found
[   14.279277] hub 2-0:1.0: 2 ports detected
[   14.383035] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 20
[   14.383050] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   14.383054] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   14.383076] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
[   14.383108] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00006f80
[   14.383202] usb usb3: configuration #1 chosen from 1 choice
[   14.383221] hub 3-0:1.0: USB hub found
[   14.383225] hub 3-0:1.0: 2 ports detected
[   14.486926] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 21 (level, low) -> IRQ 21
[   14.486938] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   14.486941] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   14.486961] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
[   14.486990] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00006f60
[   14.487078] usb usb4: configuration #1 chosen from 1 choice
[   14.487096] hub 4-0:1.0: USB hub found
[   14.487101] hub 4-0:1.0: 2 ports detected
[   14.521832] usb 1-2: new full speed USB device using uhci_hcd and address 2
[   14.590865] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 22 (level, low) -> IRQ 22
[   14.590876] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   14.590880] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   14.590897] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
[   14.590928] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00006f40
[   14.591016] usb usb5: configuration #1 chosen from 1 choice
[   14.591035] hub 5-0:1.0: USB hub found
[   14.591039] hub 5-0:1.0: 2 ports detected
[   14.676211] usb 1-2: configuration #1 chosen from 1 choice
[   14.677122] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 22 (level, low) -> IRQ 22
[   14.678137] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   14.678144] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   14.678190] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
[   14.682092] ehci_hcd 0000:00:1a.7: debug port 1
[   14.682098] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   14.682104] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xfed1c400
[   14.684694] hub 1-2:1.0: USB hub found
[   14.686082] hub 1-2:1.0: 3 ports detected
[   14.688101] hub 1-2:1.0: hub_hub_status failed (err = -71)
[   14.688104] hub 1-2:1.0: config failed, can't get hub status (err -71)
[   14.696648] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   14.696745] usb usb6: configuration #1 chosen from 1 choice
[   14.696766] hub 6-0:1.0: USB hub found
[   14.696771] hub 6-0:1.0: 4 ports detected
[   14.738170] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 20
[   14.739088] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   14.739095] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   14.739141] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[   14.743067] ehci_hcd 0000:00:1d.7: debug port 1
[   14.743073] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   14.743079] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfed1c000
[   14.749890] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   14.750044] usb usb7: configuration #1 chosen from 1 choice
[   14.750079] hub 7-0:1.0: USB hub found
[   14.750086] hub 7-0:1.0: 6 ports detected
[   14.775532] tg3.c:v3.86 (November 9, 2007)
[   14.775578] ACPI: PCI Interrupt 0000:09:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   14.775595] PCI: Setting latency timer of device 0000:09:00.0 to 64
[   14.795121] usb 1-2: USB disconnect, address 2
[   14.837980] Clocksource tsc unstable (delta = -263656592 ns)
[   14.878436] eth0: Tigon3 [partno(BCM95906) rev c002 PHY(5906)] (PCI Express) 10/100Base-TX Ethernet 00:1a:a0:fd:64:0b
[   14.878441] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[0] TSOcap[0]
[   14.878443] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   14.880208] ahci 0000:00:1f.2: version 3.0
[   14.880236] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 17
[   14.881145] ahci 0000:00:1f.2: nr_ports (3) and implemented port map (0x5) don't match, using nr_ports
[   14.881149] ahci 0000:00:1f.2: forcing PORTS_IMPL to 0x7
[   14.949671] usb 7-6: new high speed USB device using ehci_hcd and address 2
[   15.086631] usb 7-6: configuration #1 chosen from 1 choice
[   15.255846] usb 1-2: new full speed USB device using uhci_hcd and address 3
[   15.296399] usb 1-2: configuration #1 chosen from 1 choice
[   15.297561] hub 1-2:1.0: USB hub found
[   15.299524] hub 1-2:1.0: 3 ports detected
[   15.373802] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[   15.373807] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part 
[   15.373815] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   15.374051] scsi0 : ahci
[   15.374093] scsi1 : ahci
[   15.374125] scsi2 : ahci
[   15.374363] ata1: SATA max UDMA/133 abar m2048@0xfebfb800 port 0xfebfb900 irq 506
[   15.374367] ata2: SATA max UDMA/133 abar m2048@0xfebfb800 port 0xfebfb980 irq 506
[   15.374370] ata3: SATA max UDMA/133 abar m2048@0xfebfb800 port 0xfebfba00 irq 506
[   15.444229] usb 1-2.1: new full speed USB device using uhci_hcd and address 4
[   15.508691] usb 1-2.1: configuration #1 chosen from 1 choice
[   15.626941] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   15.645275] usb 1-2.2: new full speed USB device using uhci_hcd and address 5
[   15.783314] usb 1-2.2: configuration #1 chosen from 1 choice
[   15.988092] usb 1-2.3: new full speed USB device using uhci_hcd and address 6
[   16.006098] ata1.00: ATA-7: TOSHIBA MK1237GSX, DL140D, max UDMA/100
[   16.006103] ata1.00: 234441648 sectors, multi 8: LBA48 NCQ (depth 31/32)
[   16.007076] ata1.00: configured for UDMA/100
[   16.051322] usb 1-2.3: configuration #1 chosen from 1 choice
[   16.054538] usbcore: registered new interface driver hiddev
[   16.057743] input: Broadcom Corp as /devices/pci0000:00/0000:00:1a.0/usb1/1-2/1-2.2/1-2.2:1.0/input/input2
[   16.069711] input,hidraw0: USB HID v1.11 Keyboard [Broadcom Corp] on usb-0000:00:1a.0-2.2
[   16.074432] input: Broadcom Corp as /devices/pci0000:00/0000:00:1a.0/usb1/1-2/1-2.3/1-2.3:1.0/input/input3
[   16.085525] input,hidraw1: USB HID v1.11 Mouse [Broadcom Corp] on usb-0000:00:1a.0-2.3
[   16.085540] usbcore: registered new interface driver usbhid
[   16.085544] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   16.130025] ata2: SATA link down (SStatus 0 SControl 0)
[   16.196874] ata3: SATA link down (SStatus 0 SControl 300)
[   16.197005] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK1237GS DL14 PQ: 0 ANSI: 5
[   16.197313] ata_piix 0000:00:1f.1: version 2.12
[   16.197330] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 16
[   16.197365] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   16.197438] scsi3 : ata_piix
[   16.197572] scsi4 : ata_piix
[   16.198174] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x6fa0 irq 14
[   16.198176] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x6fa8 irq 15
[   16.203622] Driver 'sd' needs updating - please use bus_type methods
[   16.209430] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   16.209440] sd 0:0:0:0: [sda] Write Protect is off
[   16.209442] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   16.209456] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   16.209496] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   16.209504] sd 0:0:0:0: [sda] Write Protect is off
[   16.209506] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   16.209519] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   16.209522]  sda: sda1 sda2 < sda5 sda6 >
[   16.324898] sd 0:0:0:0: [sda] Attached SCSI disk
[   16.328599] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   16.532313] ata4.00: ATAPI: PIONEER DVD+/-RW DR-K17Y, 0.95, max UDMA/33
[   16.546389] Attempting manual resume
[   16.546391] swsusp: Resume From Partition 8:6
[   16.546393] PM: Checking swsusp image.
[   16.546658] PM: Resume from disk failed.
[   16.583452] kjournald starting.  Commit interval 5 seconds
[   16.583489] EXT3-fs: mounted filesystem with ordered data mode.
[   16.720513] ata4.00: configured for UDMA/33
[   16.720560] ata5: port disabled. ignoring.
[   16.731047] scsi 3:0:0:0: CD-ROM            PIONEER  DVD+-RW DR-K17Y  0.95 PQ: 0 ANSI: 5
[   16.731107] scsi 3:0:0:0: Attached scsi generic sg1 type 5
[   16.731299] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 19 (level, low) -> IRQ 19
[B][   16.784456] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[f9aff800-f9afffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   18.059705] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[474fc0000bd1b581][/B]
[   25.772001] ip_tables: (C) 2000-2006 Netfilter Core Team
[   25.817487] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   26.339245] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   26.363248] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   26.443285] input: Lid Switch as /devices/virtual/input/input4
[   26.443784] ACPI: Lid Switch [LID]
[   26.443823] input: Power Button (CM) as /devices/virtual/input/input5
[   26.475133] ACPI: Power Button (CM) [PBTN]
[   26.475199] input: Sleep Button (CM) as /devices/virtual/input/input6
[   26.507131] ACPI: Sleep Button (CM) [SBTN]
[   26.507317] ACPI: AC Adapter [AC] (on-line)
[   26.534551] ACPI: Battery Slot [BAT0] (battery present)
[   26.693656] ACPI: WMI-Acer: Mapper loaded
[   26.809458] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:2e/LNXVIDEO:00/input/input7
[   26.830906] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   26.840636] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input8
[   26.862894] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[   26.863035] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:02/input/input9
[   26.894875] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[   27.634768] nvidia: module license 'NVIDIA' taints kernel.
[   27.909345] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   27.909357] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   27.909446] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  169.12  Thu Feb 14 17:51:09 PST 2008
[   27.985541] input: PC Speaker as /devices/platform/pcspkr/input/input10
[   28.046284] Bluetooth: Core ver 2.11
[   28.056446] NET: Registered protocol family 31
[   28.056448] Bluetooth: HCI device and connection manager initialized
[   28.056451] Bluetooth: HCI socket layer initialized
[   28.134139] iTCO_vendor_support: vendor-support=0
[   28.143071] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   28.158130] sdhci: Secure Digital Host Controller Interface driver
[   28.158132] sdhci: Copyright(c) Pierre Ossman
[   28.158175] sdhci: SDHCI controller found at 0000:03:01.1 [1180:0822] (rev 22)
[   28.158197] ACPI: PCI Interrupt 0000:03:01.1[B] -> GSI 18 (level, low) -> IRQ 18
[   28.162149] mmc0: SDHCI at 0xf9aff500 irq 18 DMA
[   28.183121] Bluetooth: HCI USB driver ver 2.9
[   28.184557] usbcore: registered new interface driver hci_usb
[   28.252997] Driver 'sr' needs updating - please use bus_type methods
[   28.301830] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[   28.301834] Uniform CD-ROM driver Revision: 3.20
[   28.301876] sr 3:0:0:0: Attached scsi CD-ROM sr0
[   28.330626] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   28.330629] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   28.330765] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   28.330782] PCI: Setting latency timer of device 0000:0c:00.0 to 64
[   28.331690] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   28.332539] input: PS/2 Mouse as /devices/virtual/input/input11
[   28.346427] Linux video capture interface: v2.00
[   28.399789] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input12
[   28.412051] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:2640)
[   28.412912] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
[   28.413937] usbcore: registered new interface driver uvcvideo
[   28.413940] USB Video Class driver (v0.1.0)
[   28.456124] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   28.456184] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x1060)
[   28.456223] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   28.465118] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 21
[   28.466031] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   29.216377] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   29.216816] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[   29.375030] udev: renamed network interface wlan0 to eth1
[   29.455719] lp: driver loaded but no devices found
[   29.598524] Adding 4096532k swap on /dev/sda6.  Priority:-1 extents:1 across:4096532k
[   29.627783] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   29.628045] EXT3 FS on sda5, internal journal
[   29.893049] kjournald starting.  Commit interval 5 seconds
[   29.893354] EXT3 FS on sda1, internal journal
[B][   29.893359] EXT3-fs: mounted filesystem with ordered data mode.
[   32.707127] No dock devices found.
[   34.121949] ppdev: user-space parallel port driver
[   34.630025] audit(1211331792.275:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5513 profile="/usr/sbin/cupsd" namespace="default"
[/B][   37.475521] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   37.475533] vboxdrv: Successfully done.
[   37.475536] vboxdrv: Found 2 processor cores.
[   37.475565] vboxdrv: fAsync=0 u64DiffCores=3740.
[   37.477680] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   37.477686] vboxdrv: Successfully loaded version 1.6.0 (interface 0x00070001).
[   37.559076] tun: Universal TUN/TAP device driver, 1.6
[   37.559086] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[   39.036478] Bluetooth: L2CAP ver 2.9
[   39.036487] Bluetooth: L2CAP socket layer initialized
[   39.188952] Bluetooth: RFCOMM socket layer initialized
[   39.188985] Bluetooth: RFCOMM TTY layer initialized
**[   39.188989] Bluetooth: RFCOMM ver 1.8**
[   46.221388] NET: Registered protocol family 10
[   46.221966] lo: Disabled Privacy Extensions
[B][   46.222950] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   46.224018] ADDRCONF(NETDEV_UP): eth1: link is not ready
[/B][   55.599965] CPU0 attaching NULL sched-domain.
[   55.599977] CPU1 attaching NULL sched-domain.
[   55.605763] CPU0 attaching sched-domain:
[   55.605775]  domain 0: span 03
[   55.605779]   groups: 01 02
[   55.605785]   domain 1: span 03
[   55.605789]    groups: 03
[   55.605793] CPU1 attaching sched-domain:
[   55.605796]  domain 0: span 03
[   55.605799]   groups: 02 01
[   55.605804]   domain 1: span 03
[   55.605808]    groups: 03
**[   59.369760] NET: Registered protocol family 17**
[   60.986445] eth1: Initial auth_alg=0
[   60.986453] eth1: authenticate with AP 00:19:7e:64:35:e5
[   60.989200] eth1: Initial auth_alg=0
[   60.989207] eth1: authenticate with AP 00:19:7e:64:35:e5
[   60.989233] eth1: RX authentication from 00:19:7e:64:35:e5 (alg=0 transaction=2 status=0)
[   60.989237] eth1: authenticated
[   60.989239] eth1: associate with AP 00:19:7e:64:35:e5
[   60.990711] eth1: authentication frame received from 00:19:7e:64:35:e5, but not in authenticate state - ignored
[   60.991726] eth1: RX AssocResp from 00:19:7e:64:35:e5 (capab=0x401 status=0 aid=1)
[   60.991747] eth1: associated
[B][   60.996234] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   79.483067] eth1: no IPv6 routers present[/B]
```

Any suggestions? Thanks in advance...

---

