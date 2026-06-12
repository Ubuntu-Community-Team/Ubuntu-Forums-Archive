---
title: "getting wext driver???"
date: 2008-04-05
forum: Networking &amp; Wireless
---

### Post by equity on 2008-04-05
Hi,

I had got a lot of trouble connecting to wireless networks using nm-applet and now even connecting via the command line using kevdog's tutorial that is sticky in this forum does not work (gonna getting desperate) ...

So I asked for help:

[http://ubuntuforums.org/showthread.php?t=746098](http://ubuntuforums.org/showthread.php?t=746098)
[http://ubuntuforums.org/showthread.php?t=745047](http://ubuntuforums.org/showthread.php?t=745047)

Kevdog adviced me to change my WLAN driver (I got an Intel Pro/Wireless 3945) from ipw3945 to wext. But in some other topic I read that wext is the abbreviation for wireless extension and neither in the English nor in the German speaking part of Wikipedia is wext mentioned (apart from the radio station).


I got an Asus G1-AP021C notebook and now I am tired of connecting to the internet via cable...


I would be thankful for any advice on how to change the WLAN driver to wext or supporting me on my other threads.

---

### Post by kevdog on 2008-04-05
Please be more specific in your explanation.

I believe you stated originally you can connect via an unencrypted connection but not with WPA.  Specifically I believe you were passing ipw as the driver identifier with the wpa_supplicant command rather than specifying the wext driver as the driver identifier. 

Please represents the facts more clearly.  There is no wext driver per se.

---

### Post by equity on 2008-04-05
No no, you missapprehanded me. Since I am not using nm-applet anymore I cannot connect to any WLAN AP (using the command line, following your instructions), I can only connect via cable.

---

### Post by kevdog on 2008-04-05
So post something we can work with like:

lshw -C network
dmesg
iwlist scan
lspci -nn

Thanks.

---

### Post by equity on 2008-04-05
Okay, I typed all these commands:

[B]user@G1-AP021C:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:1a:92:ef:d8:f3
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.1.34 latency=0 module=r8169 multicast=yes
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 02
       serial: 00:19:d2:d2:69:00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp.ubuntu1 firmware=14.2 1:0 () latency=0 module=ipw3945 wireless=unassociated
user@G1-AP021C:~$ 
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1995.113 MHz processor.
[   12.046610] Console: colour VGA+ 80x25
[   12.046860] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   12.047120] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   12.125546] Memory: 2067460k/2096960k available (2015k kernel code, 28200k reserved, 915k data, 364k init, 1179456k highmem)
[   12.125553] virtual kernel memory layout:
[   12.125554]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   12.125555]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   12.125556]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   12.125557]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   12.125558]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   12.125559]       .data : 0xc02f7e86 - 0xc03dce84   ( 915 kB)
[   12.125560]       .text : 0xc0100000 - 0xc02f7e86   (2015 kB)
[   12.125563] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   12.125596] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   12.125724] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   12.125729] hpet0: 3 64-bit timers, 14318180 Hz
[   12.206704] Calibrating delay using timer specific routine.. 3994.35 BogoMIPS (lpj=7988700)
[   12.206726] Security Framework v1.0.0 initialized
[   12.206731] SELinux:  Disabled at boot.
[   12.206742] Mount-cache hash table entries: 512
[   12.206859] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
[   12.206866] monitor/mwait feature present.
[   12.206867] using mwait in idle threads.
[   12.206871] CPU: L1 I cache: 32K, L1 D cache: 32K
[   12.206873] CPU: L2 cache: 4096K
[   12.206875] CPU: Physical Processor ID: 0
[   12.206877] CPU: Processor Core ID: 0
[   12.206878] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001
[   12.206887] Compat vDSO mapped to ffffe000.
[   12.206899] Checking 'hlt' instruction... OK.
[   12.222797] SMP alternatives: switching to UP code
[   12.223187] Early unpacking initramfs... done
[   12.500342] ACPI: Core revision 20070126
[   12.500387] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   12.515593] CPU0: Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz stepping 06
[   12.515607] SMP alternatives: switching to SMP code
[   12.515679] Booting processor 1/1 eip 3000
[   12.526108] Initializing CPU#1
[   12.606476] Calibrating delay using timer specific routine.. 3990.05 BogoMIPS (lpj=7980105)
[   12.606481] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
[   12.606486] monitor/mwait feature present.
[   12.606488] CPU: L1 I cache: 32K, L1 D cache: 32K
[   12.606490] CPU: L2 cache: 4096K
[   12.606492] CPU: Physical Processor ID: 0
[   12.606493] CPU: Processor Core ID: 1
[   12.606494] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001
[   12.607185] CPU1: Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz stepping 06
[   12.607204] Total of 2 processors activated (7984.40 BogoMIPS).
[   12.607398] ENABLING IO-APIC IRQs
[   12.607587] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   12.754475] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   12.774478] Brought up 2 CPUs
[   12.995865] migration_cost=51
[   12.995982] Booting paravirtualized kernel on bare hardware
[   12.996054] Time:  9:57:03  Date: 03/05/108
[   12.996071] NET: Registered protocol family 16
[   12.996144] EISA bus registered
[   12.996148] ACPI: bus type pci registered
[   12.996312] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=5
[   12.996313] PCI: Using configuration type 1
[   12.996315] Setting up standard PCI resources
[   12.999555] ACPI: EC: Look up EC in DSDT
[   13.000048] ACPI: EC: GPE=0x1c, ports=0x66, 0x62
[   13.057815] ACPI: Interpreter enabled
[   13.057817] ACPI: (supports S0 S1 S3 S4 S5)
[   13.057837] ACPI: Using IOAPIC for interrupt routing
[   13.064986] ACPI: EC: GPE=0x1c, ports=0x66, 0x62
[   13.065101] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   13.065116] PCI: Probing PCI hardware (bus 00)
[   13.065761] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[   13.065766] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
[   13.066815] PCI: Transparent bridge - 0000:00:1e.0
[   13.066935] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   13.067070] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[   13.067159] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   13.067276] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[   13.067376] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
[   13.076785] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *11 12)
[   13.076917] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 12)
[   13.077047] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 12)
[   13.077176] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 7 12)
[   13.077306] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 12)
[   13.077436] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 *7 12)
[   13.077565] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 *6 7 12)
[   13.077694] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 *4 5 6 7 12)
[   13.077844] ACPI: Power Resource [GFAN] (off)
[   13.077849] Linux Plug and Play Support v0.97 (c) Adam Belay
[   13.077857] pnp: PnP ACPI init
[   13.077866] ACPI: bus type pnp registered
[   13.079957] pnp: PnP ACPI: found 15 devices
[   13.079959] ACPI: ACPI bus type pnp unregistered
[   13.079962] PnPBIOS: Disabled by ACPI PNP
[   13.079998] PCI: Using ACPI for IRQ routing
[   13.080000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   13.095421] NET: Registered protocol family 8
[   13.095423] NET: Registered protocol family 20
[   13.095464] pnp: 00:01: iomem range 0xfed13000-0xfed19fff has been reserved
[   13.095472] pnp: 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[   13.095474] pnp: 00:08: iomem range 0xfed20000-0xfed8ffff has been reserved
[   13.095479] pnp: 00:0a: iomem range 0xffb80000-0xffbfffff could not be reserved
[   13.095482] pnp: 00:0a: iomem range 0xfff80000-0xffffffff could not be reserved
[   13.095486] pnp: 00:0b: iomem range 0xffc00000-0xfff7ffff could not be reserved
[   13.095490] pnp: 00:0c: ioport range 0x400-0x41f has been reserved
[   13.095492] pnp: 00:0c: iomem range 0xfec00000-0xfec00fff has been reserved
[   13.095495] pnp: 00:0c: iomem range 0xfee00000-0xfee00fff could not be reserved
[   13.095497] pnp: 00:0c: iomem range 0xfec10000-0xfec17fff has been reserved
[   13.095500] pnp: 00:0c: iomem range 0xfec28000-0xfec2ffff has been reserved
[   13.095504] pnp: 00:0d: iomem range 0xe0000000-0xe3ffffff has been reserved
[   13.095508] pnp: 00:0e: iomem range 0x0-0x9ffff could not be reserved
[   13.095511] pnp: 00:0e: iomem range 0xc0000-0xcffff could not be reserved
[   13.095513] pnp: 00:0e: iomem range 0xe0000-0xfffff could not be reserved
[   13.095516] pnp: 00:0e: iomem range 0x100000-0x7fffffff could not be reserved
[   13.098208] Time: tsc clocksource has been installed.
[   13.098221] Switched to high resolution mode on CPU 0
[   13.098295] Switched to high resolution mode on CPU 1
[   13.125755] PCI: Bridge: 0000:00:01.0
[   13.125758]   IO window: b000-bfff
[   13.125761]   MEM window: f9f00000-fdffffff
[   13.125764]   PREFETCH window: bdf00000-ddefffff
[   13.125768] PCI: Bridge: 0000:00:1c.0
[   13.125770]   IO window: c000-cfff
[   13.125776]   MEM window: fe000000-fe0fffff
[   13.125780]   PREFETCH window: disabled.
[   13.125786] PCI: Bridge: 0000:00:1c.3
[   13.125787]   IO window: disabled.
[   13.125793]   MEM window: fe100000-fe1fffff
[   13.125797]   PREFETCH window: disabled.
[   13.125808] PCI: Bus 5, cardbus bridge: 0000:04:01.0
[   13.125810]   IO window: 0000d000-0000d0ff
[   13.125814]   IO window: 0000d400-0000d4ff
[   13.125819]   PREFETCH window: 88000000-8bffffff
[   13.125823]   MEM window: 8c000000-8fffffff
[   13.125827] PCI: Bridge: 0000:00:1e.0
[   13.125830]   IO window: d000-dfff
[   13.125836]   MEM window: fe200000-feafffff
[   13.125840]   PREFETCH window: ddf00000-dfefffff
[   13.125855] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   13.125859] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   13.125882] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 20 (level, low) -> IRQ 17
[   13.125887] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   13.125911] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 18
[   13.125916] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   13.125929] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   13.125945] ACPI: PCI Interrupt 0000:04:01.0[A] -> GSI 17 (level, low) -> IRQ 19
[   13.125957] NET: Registered protocol family 2
[   13.174146] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   13.174194] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   13.174767] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   13.174959] TCP: Hash tables configured (established 131072 bind 65536)
[   13.174961] TCP reno registered
[   13.190222] checking if image is initramfs... it is
[   13.733531] Freeing initrd memory: 7077k freed
[   13.733646] Simple Boot Flag at 0x52 set to 0x1
[   13.734127] audit: initializing netlink socket (disabled)
[   13.734142] audit(1207389423.292:1): initialized
[   13.734232] highmem bounce pool size: 64 pages
[   13.735951] VFS: Disk quotas dquot_6.5.1
[   13.735990] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   13.736068] io scheduler noop registered
[   13.736070] io scheduler anticipatory registered
[   13.736072] io scheduler deadline registered
[   13.736083] io scheduler cfq registered (default)
[   13.736182] Boot video device is 0000:01:00.0
[   13.736255] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   13.736289] assign_interrupt_mode Found MSI capability
[   13.736292] Allocate Port Service[0000:00:01.0:pcie00]
[   13.736366] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   13.736421] assign_interrupt_mode Found MSI capability
[   13.736423] Allocate Port Service[0000:00:1c.0:pcie00]
[   13.736451] Allocate Port Service[0000:00:1c.0:pcie02]
[   13.736545] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   13.736600] assign_interrupt_mode Found MSI capability
[   13.736602] Allocate Port Service[0000:00:1c.3:pcie00]
[   13.736631] Allocate Port Service[0000:00:1c.3:pcie02]
[   13.736780] isapnp: Scanning for PnP cards...
[   14.091007] isapnp: No Plug & Play device found
[   14.109454] Real Time Clock Driver v1.12ac
[   14.109613] hpet_resources: 0xfed00000 is busy
[   14.109658] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   14.110848] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   14.110960] input: Macintosh mouse button emulation as /class/input/input0
[   14.111032] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   14.113772] i8042.c: Detected active multiplexing controller, rev 1.1.
[   14.114931] serio: i8042 KBD port at 0x60,0x64 irq 1
[   14.114936] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   14.114938] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   14.114941] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   14.114943] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   14.115045] mice: PS/2 mouse device common for all mice
[   14.115157] EISA: Probing bus 0 at eisa.0
[   14.115195] EISA: Detected 0 cards.
[   14.115260] TCP cubic registered
[   14.115270] NET: Registered protocol family 1
[   14.115288] Using IPI No-Shortcut mode
[   14.115420]   Magic number: 4:756:979
[   14.115426]   hash matches device ttyc6
[   14.115663] Freeing unused kernel memory: 364k freed
[   14.189474] input: AT Translated Set 2 keyboard as /class/input/input1
[   15.282555] AppArmor: AppArmor initialized<5>audit(1207389424.792:2):  type=1505 info="AppArmor initialized" pid=1239
[   15.287328] fuse init (API version 7.8)
[   15.290908] Failure registering capabilities with primary security module.
[   15.320124] ACPI: Transitioning device [FN00] to D3
[   15.320127] ACPI: Transitioning device [FN00] to D3
[   15.320129] ACPI: Fan [FN00] (off)
[   15.323856] ACPI Warning (tbutils-0217): Incorrect checksum in table [SSDT] -  7B, should be 9F [20070126]
[   15.323864] ACPI: SSDT 7FFD7FF0, 0A95 (r1    AMI   CPU1PM        1 INTL 20051117)
[   15.324149] Monitor-Mwait will be used to enter C-1 state
[   15.324152] Monitor-Mwait will be used to enter C-2 state
[   15.324156] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   15.324159] ACPI: Processor [CPU1] (supports 8 throttling states)
[   15.324200] ACPI Warning (tbutils-0217): Incorrect checksum in table [SSDT] -  03, should be 9B [20070126]
[   15.324204] ACPI: SSDT 7FFD8A90, 042F (r1    AMI   CPU2PM        1 INTL 20051117)
[   15.324511] ACPI: CPU1 (power states: C1[C1] C2[C2])
[   15.324516] ACPI: Processor [CPU2] (supports 8 throttling states)
[   15.333436] ACPI: Thermal Zone [THRM] (33 C)
[    3.028000] Marking TSC unstable due to: possible TSC halt in C2.
[    3.032000] Time: hpet clocksource has been installed.
[    3.392000] usbcore: registered new interface driver usbfs
[    3.392000] usbcore: registered new interface driver hub
[    3.392000] usbcore: registered new device driver usb
[    3.392000] USB Universal Host Controller Interface driver v3.0
[    3.392000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
[    3.392000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    3.392000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.392000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    3.392000] uhci_hcd 0000:00:1d.0: irq 20, io base 0x0000ec00
[    3.392000] usb usb1: configuration #1 chosen from 1 choice
[    3.392000] hub 1-0:1.0: USB hub found
[    3.392000] hub 1-0:1.0: 2 ports detected
[    3.480000] SCSI subsystem initialized
[    3.496000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 20 (level, low) -> IRQ 17
[    3.496000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    3.496000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.496000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    3.496000] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000e880
[    3.496000] usb usb2: configuration #1 chosen from 1 choice
[    3.496000] hub 2-0:1.0: USB hub found
[    3.496000] hub 2-0:1.0: 2 ports detected
[    3.508000] libata version 2.21 loaded.
[    3.600000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 22 (level, low) -> IRQ 21
[    3.600000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    3.600000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.600000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    3.600000] uhci_hcd 0000:00:1d.2: irq 21, io base 0x0000e800
[    3.600000] usb usb3: configuration #1 chosen from 1 choice
[    3.600000] hub 3-0:1.0: USB hub found
[    3.600000] hub 3-0:1.0: 2 ports detected
[    3.704000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 18 (level, low) -> IRQ 22
[    3.704000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    3.704000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.704000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    3.704000] uhci_hcd 0000:00:1d.3: irq 22, io base 0x0000e480
[    3.704000] usb usb4: configuration #1 chosen from 1 choice
[    3.704000] hub 4-0:1.0: USB hub found
[    3.704000] hub 4-0:1.0: 2 ports detected
[    3.736000] usb 1-1: new low speed USB device using uhci_hcd and address 2
[    3.808000] ACPI: PCI Interrupt 0000:04:01.1[B] -> GSI 18 (level, low) -> IRQ 22
[    3.860000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[22]  MMIO=[feaff800-feafffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    3.868000] ata_piix 0000:00:1f.2: version 2.11
[    3.868000] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    3.868000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 18
[    3.868000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    3.868000] scsi0 : ata_piix
[    3.868000] scsi1 : ata_piix
[    3.868000] ata1: SATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14
[    3.868000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15
[    3.912000] usb 1-1: configuration #1 chosen from 1 choice
[    4.032000] ata1.00: ATA-7: ST9160821AS, 3.ALC, max UDMA/133
[    4.032000] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    4.048000] ata1.00: configured for UDMA/133
[    4.156000] usb 3-1: new full speed USB device using uhci_hcd and address 2
[    4.380000] ata2.00: ATAPI: HL-DT-ST DVDRAM GSA-T20L, NR02, max UDMA/33
[    4.392000] usb 3-1: configuration #1 chosen from 1 choice
[    4.552000] ata2.00: configured for UDMA/33
[    4.552000] scsi 0:0:0:0: Direct-Access     ATA      ST9160821AS      3.AL PQ: 0 ANSI: 5
[    4.556000] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T20L  NR02 PQ: 0 ANSI: 5
[    4.556000] r8169 Gigabit Ethernet driver 2.2LK loaded
[    4.556000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[    4.556000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[    4.556000] eth0: RTL8168b/8111b at 0xf887a000, 00:1a:92:ef:d8:f3, XID 38000000 IRQ 16
[    4.556000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
[    4.556000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    4.556000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.556000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    4.556000] ehci_hcd 0000:00:1d.7: debug port 1
[    4.556000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    4.556000] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfebfbc00
[    4.636000] usb 3-2: new full speed USB device using uhci_hcd and address 3
[    4.636000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.636000] usb usb5: configuration #1 chosen from 1 choice
[    4.636000] hub 5-0:1.0: USB hub found
[    4.636000] hub 5-0:1.0: 8 ports detected
[    4.748000] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    4.748000] sd 0:0:0:0: [sda] Write Protect is off
[    4.748000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.748000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.748000] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    4.748000] sd 0:0:0:0: [sda] Write Protect is off
[    4.748000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.748000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.748000]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    4.812000] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.816000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.816000] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    4.828000] usb 3-1: USB disconnect, address 2
[    4.828000] usbcore: registered new interface driver hiddev
[    4.832000] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.832000] Uniform CD-ROM driver Revision: 3.20
[    4.832000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    5.144000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e01800038aa7ac]
[    5.160000] Attempting manual resume
[    5.160000] swsusp: Resume From Partition 8:5
[    5.160000] PM: Checking swsusp image.
[    5.164000] PM: Resume from disk failed.
[    5.184000] kjournald starting.  Commit interval 5 seconds
[    5.184000] EXT3-fs: mounted filesystem with ordered data mode.
[    5.620000] usb 5-6: new high speed USB device using ehci_hcd and address 4
[    5.752000] usb 5-6: configuration #1 chosen from 1 choice
[    5.992000] usb 5-7: new high speed USB device using ehci_hcd and address 5
[    6.124000] usb 5-7: config 1 interface 0 altsetting 0 endpoint 0x81 has an invalid bInterval 0, changing to 9
[    6.124000] usb 5-7: config 1 interface 0 altsetting 0 endpoint 0x2 has an invalid bInterval 0, changing to 9
[    6.124000] usb 5-7: configuration #1 chosen from 1 choice
[    6.124000] usb 1-1: USB disconnect, address 2
[    6.124000] usbcore: registered new interface driver usbhid
[    6.124000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[    6.364000] usb 1-1: new low speed USB device using uhci_hcd and address 3
[    6.540000] usb 1-1: configuration #1 chosen from 1 choice
[    6.556000] input: Logitech USB-PS/2 Optical Mouse as /class/input/input2
[    6.556000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.0-1
[    6.796000] usb 3-1: new full speed USB device using uhci_hcd and address 4
[    7.040000] usb 3-1: configuration #1 chosen from 1 choice
[   12.708000] ip_tables: (C) 2000-2006 Netfilter Core Team
[   12.772000] Netfilter messages via NETLINK v0.30.
[   12.800000] nf_conntrack version 0.5.0 (8192 buckets, 65536 max)
[   13.928000] Linux agpgart interface v0.102 (c) Dave Jones
[   14.036000] iTCO_vendor_support: vendor-support=0
[   14.080000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   14.084000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x0860)
[   14.084000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   14.128000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   14.136000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   14.308000] intel_rng: FWH not detected
[   14.512000] Bluetooth: Core ver 2.11
[   14.512000] NET: Registered protocol family 31
[   14.512000] Bluetooth: HCI device and connection manager initialized
[   14.512000] Bluetooth: HCI socket layer initialized
[   14.548000] input: PC Speaker as /class/input/input3
[   14.556000] Bluetooth: HCI USB driver ver 2.9
[   14.560000] usbcore: registered new interface driver hci_usb
[   14.692000] ieee80211_crypt: registered algorithm 'NULL'
[   14.692000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   14.692000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   14.796000] Yenta: CardBus bridge found at 0000:04:01.0 [1043:1437]
[   14.876000] sdhci: Secure Digital Host Controller Interface driver
[   14.876000] sdhci: Copyright(c) Pierre Ossman
[   14.920000] nvidia: module license 'NVIDIA' taints kernel.
[   14.924000] Yenta: ISA IRQ mask 0x0cb8, PCI irq 19
[   14.924000] Socket status: 30000006
[   14.924000] Yenta: Raising subordinate bus# of parent bus (#04) from #05 to #08
[   14.924000] pcmcia: parent PCI bridge I/O window: 0xd000 - 0xdfff
[   14.924000] cs: IO port probe 0xd000-0xdfff: clean.
[   14.924000] pcmcia: parent PCI bridge Memory window: 0xfe200000 - 0xfeafffff
[   14.924000] pcmcia: parent PCI bridge Memory window: 0xddf00000 - 0xdfefffff
[   14.924000] sdhci: SDHCI controller found at 0000:04:01.2 [1180:0822] (rev 17)
[   14.924000] ACPI: PCI Interrupt 0000:04:01.2[B] -> GSI 18 (level, low) -> IRQ 22
[   14.924000] mmc0: SDHCI at 0xfeaff400 irq 22 DMA
[   15.188000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   15.188000] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   15.188000] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.19  Wed Sep 12 14:12:24 PDT 2007
[   15.196000] usbcore: registered new interface driver xpad
[   15.196000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
[   15.212000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.2mp.ubuntu1
[   15.212000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   15.212000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 19 (level, low) -> IRQ 18
[   15.212000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   15.212000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   15.312000] Synaptics Touchpad, model: 1, fw: 6.1, id: 0xa3a0b3, caps: 0xa04713/0x10008
[   15.348000] input: SynPS/2 Synaptics TouchPad as /class/input/input4
[   15.536000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 23
[   15.536000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   15.564000] cs: IO port probe 0x100-0x3af: clean.
[   15.564000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   15.564000] cs: IO port probe 0x820-0x8ff: clean.
[   15.564000] cs: IO port probe 0xc00-0xcf7: clean.
[   15.568000] cs: IO port probe 0xa00-0xaff: clean.
[   16.272000] lp: driver loaded but no devices found
[   16.352000] Adding 2000052k swap on /dev/sda5.  Priority:-1 extents:1 across:2000052k
[   17.132000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
[  190.744000] EXT3 FS on sda6, internal journal
[  192.024000] No dock devices found.
[  192.056000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[  192.140000] ACPI: AC Adapter [AC0] (on-line)
[  192.160000] Asus Laptop ACPI Extras version 0.30
[  192.160000]   unsupported model G1, trying default values
[  192.160000]   send /proc/acpi/dsdt to the developers
[  192.216000] ACPI: Battery Slot [BAT0] (battery present)
[  192.228000] input: Power Button (FF) as /class/input/input5
[  192.228000] ACPI: Power Button (FF) [PWRF]
[  192.228000] input: Lid Switch as /class/input/input6
[  192.228000] ACPI: Lid Switch [LID]
[  192.228000] input: Power Button (CM) as /class/input/input7
[  192.228000] ACPI: Power Button (CM) [PWRB]
[  192.228000] input: Sleep Button (CM) as /class/input/input8
[  192.228000] ACPI: Sleep Button (CM) [SLPB]
[  193.216000] NET: Registered protocol family 10
[  193.216000] lo: Disabled Privacy Extensions
[  193.960000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  193.960000] apm: disabled - APM is not SMP safe.
[  196.248000] NET: Registered protocol family 17
[  197.552000] Failure registering capabilities with primary security module.
[  432.672000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  432.700000] device eth1 entered promiscuous mode
[  432.700000] audit(1207382655.451:3): dev=eth1 prom=256 old_prom=0 auid=4294967295
[  437.444000] device eth1 left promiscuous mode
[  437.444000] audit(1207382659.950:4): dev=eth1 prom=0 old_prom=256 auid=4294967295
[  443.404000] device eth1 entered promiscuous mode
[  443.404000] audit(1207382665.950:5): dev=eth1 prom=256 old_prom=0 auid=4294967295
[  446.452000] device eth1 left promiscuous mode
[  446.452000] audit(1207382668.950:6): dev=eth1 prom=0 old_prom=256 auid=4294967295
[  724.868000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 1003.812000] ipw3945: Radio Frequency Kill Switch is On:
[ 1003.812000] Kill switch must be turned off for wireless networking to work.
[ 1007.516000] usb 3-1: USB disconnect, address 4
[ 1034.836000] r8169: eth0: link up
[ 1034.836000] r8169: eth0: link up
[ 1044.864000] eth0: no IPv6 routers present
[ 1114.668000] r8169: eth0: link up
[ 1124.868000] eth0: no IPv6 routers present
[ 1200.836000] r8169: eth0: link up
[ 1211.044000] eth0: no IPv6 routers present
[ 1260.320000] r8169: eth0: link up
[ 1271.232000] eth0: no IPv6 routers present
[ 1319.976000] r8169: eth0: link up
[ 1330.256000] eth0: no IPv6 routers present
[ 4984.720000] Monitor-Mwait will be used to enter C-3 state
[ 5237.000000] Clocksource tsc unstable (delta = -145537055 ns)
[12407.468000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
[12416.148000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[12419.896000] device eth1 entered promiscuous mode
[12419.896000] audit(1207394642.430:7): dev=eth1 prom=256 old_prom=0 auid=4294967295
[12430.020000] device eth1 left promiscuous mode
[12430.020000] audit(1207394652.430:8): dev=eth1 prom=0 old_prom=256 auid=4294967295
[12449.516000] r8169: eth0: link down
[12451.204000] device eth1 entered promiscuous mode
[12451.204000] audit(1207394673.930:9): dev=eth1 prom=256 old_prom=0 auid=4294967295
[12455.572000] device eth1 left promiscuous mode
[12455.572000] audit(1207394678.430:10): dev=eth1 prom=0 old_prom=256 auid=4294967295
[12498.660000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[12768.324000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[12887.400000] device eth1 entered promiscuous mode
[12887.400000] audit(1207395109.930:11): dev=eth1 prom=256 old_prom=0 auid=4294967295
[12896.164000] device eth1 left promiscuous mode
[12896.164000] audit(1207395118.930:12): dev=eth1 prom=0 old_prom=256 auid=4294967295
[12950.292000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[13281.744000] r8169: eth0: link up
[13292.700000] eth0: no IPv6 routers present
[13531.300000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[13551.828000] device eth1 entered promiscuous mode
[13551.828000] audit(1207395774.428:13): dev=eth1 prom=256 old_prom=0 auid=4294967295
[13556.920000] ipw3945: Daemon command aborted.
[13556.932000] device eth1 left promiscuous mode
[13556.932000] audit(1207395779.428:14): dev=eth1 prom=0 old_prom=256 auid=4294967295
[13609.988000] device eth1 entered promiscuous mode
[13609.988000] audit(1207395832.428:15): dev=eth1 prom=256 old_prom=0 auid=4294967295
[13613.388000] device eth1 left promiscuous mode
[13613.388000] audit(1207395835.928:16): dev=eth1 prom=0 old_prom=256 auid=4294967295
[13636.352000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[13752.428000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[13806.944000] r8169: eth0: link down
[13806.944000] r8169: eth0: link down
[13806.948000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[13842.304000] r8169: eth0: link down
[13842.304000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[13908.832000] r8169: eth0: link up
[13908.836000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[13919.720000] eth0: no IPv6 routers present
[14484.936000] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.
[14484.936000] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
[14484.936000] pcmcia: see [http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html](http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html) for details.
[14540.368000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[21953.044000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[22082.260000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[22168.132000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[22527.200000] r8169: eth0: link up
[22527.200000] r8169: eth0: link up
[22537.636000] eth0: no IPv6 routers present
[40675.388000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[40675.420000] device eth1 entered promiscuous mode
[40675.420000] audit(1207422897.883:17): dev=eth1 prom=256 old_prom=0 auid=4294967295
[40680.748000] device eth1 left promiscuous mode
[40680.748000] audit(1207422903.383:18): dev=eth1 prom=0 old_prom=256 auid=4294967295
[40683.588000] device eth1 entered promiscuous mode
[40683.588000] audit(1207422906.383:19): dev=eth1 prom=256 old_prom=0 auid=4294967295
[40689.328000] device eth1 left promiscuous mode
[40689.328000] audit(1207422911.883:20): dev=eth1 prom=0 old_prom=256 auid=4294967295
user@G1-AP021C:~$ 
user@G1-AP021C:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:19:5B:BF:91:B7
                    ESSID:"berkan"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=57/100  Signal level=-74 dBm  Noise level=-74 dBm
                    Extra: Last beacon: 676ms ago
          Cell 02 - Address: 00:13:49:EE:DA:FA
                    ESSID:"my_essid_in_quotes"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=77/100  Signal level=-57 dBm  Noise level=-57 dBm
                    Extra: Last beacon: 412ms ago

user@G1-AP021C:~$ 
user@G1-AP021C:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port [8086:27a1] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 [8086:27d6] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 02)
01:00.0 VGA compatible controller [0300]: nVidia Corporation GeForce Go 7700 [10de:0397] (rev a1)
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 01)
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:4222] (rev 02)
04:01.0 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev b3)
04:01.1 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C552 IEEE 1394 Controller [1180:0552] (rev 08)
04:01.2 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 17)
04:01.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 08)
user@G1-AP021C:~$[/B]

---

### Post by equity on 2008-04-05
I did it!!! It works now!! Now I will purge and reinstall wpa_supplicant and try to connect to my AP with WPA enabled using your guide.

Thanks a lot.

---

### Post by equity on 2008-04-05
How can I mark this topic as "[Solved]" ?

---

### Post by kevdog on 2008-04-05
Im not sure what you did, but Im glad everything works.

---

### Post by equity on 2008-04-06
I did exactly what you have written in your tutorial about how to connect to an unencrypted network.
I think the last time I had just forgotten to shut down my wired ethernet device.

---

