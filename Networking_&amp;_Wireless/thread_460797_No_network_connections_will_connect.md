---
title: "No network connections will connect"
date: 2007-06-01
forum: Networking &amp; Wireless
---

### Post by MusicMastaMike on 2007-06-01
I'm having a very strange problem here.  I just installed Feisty on a friend's laptop (hp Pavillion 3000zt).  Everything seems to work great, except for one thing... No matter what I try, I cannot connect to any sort of network, wired or wireless.  Both NICs are detected, and I can choose which network to connect to, but it is perpetually trying to connect, will never finish.  I have Feisty installed on my own laptop, and am presently typing on it, using his internet without fault.  Also, both wired and wireless connections work fine on his Windows XP.  The Microsoft router uses DHCP and DNS.  I have included as much info as possible.  Please let me know if you have any ideas.

Output of: lspci -v
> 
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
        Subsystem: Compaq Computer Corporation Unknown device 0860
        Flags: bus master, fast devsel, latency 0
        Memory at b0000000 (32-bit, prefetchable) [size=256M]
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 128
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: 90400000-904fffff
        Prefetchable memory behind bridge: 98000000-9fffffff

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Compaq Computer Corporation Unknown device 0860
        Flags: bus master, medium devsel, latency 0, IRQ 10
        I/O ports at 48c0 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Compaq Computer Corporation Unknown device 0860
        Flags: bus master, medium devsel, latency 0, IRQ 5
        I/O ports at 48e0 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Compaq Computer Corporation Unknown device 0860
        Flags: bus master, medium devsel, latency 0, IRQ 5
        I/O ports at 4c00 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
        Subsystem: Compaq Computer Corporation Unknown device 0860
        Flags: bus master, medium devsel, latency 0, IRQ 5
        Memory at a0000000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=06, sec-latency=32
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: 90000000-903fffff
        Prefetchable memory behind bridge: 30000000-33ffffff

00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
        Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
        Subsystem: Compaq Computer Corporation Unknown device 0860
        Flags: bus master, medium devsel, latency 0, IRQ 5
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 4c40 [size=16]
        Memory at 34000000 (32-bit, non-prefetchable) [size=1K]

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
        Subsystem: Compaq Computer Corporation Unknown device 0860
        Flags: medium devsel, IRQ 10
        I/O ports at 4c20 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
        Subsystem: Compaq Computer Corporation Unknown device 0860
        Flags: bus master, medium devsel, latency 0, IRQ 10
        I/O ports at 4000 [size=256]
        I/O ports at 4880 [size=64]
        Memory at a0200000 (32-bit, non-prefetchable) [size=512]
        Memory at a0300000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01) (prog-if 00 [Generic])
        Subsystem: Compaq Computer Corporation Unknown device 0860
        Flags: medium devsel, IRQ 10
        I/O ports at 4400 [size=256]
        I/O ports at 4800 [size=128]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R250 [Mobility FireGL 9000] (rev 01) (prog-if 00 [VGA])
        Subsystem: Compaq Computer Corporation Unknown device 0860
        Flags: bus master, stepping, 66MHz, medium devsel, latency 128, IRQ 10
        Memory at 98000000 (32-bit, prefetchable) [size=128M]
        I/O ports at 3000 [size=256]
        Memory at 90400000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at 90420000 [disabled] [size=128K]
        Capabilities: <access denied>

02:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: VIA Technologies, Inc. IEEE 1394 Host Controller
        Flags: bus master, medium devsel, latency 128, IRQ 10
        Memory at 90200000 (32-bit, non-prefetchable) [size=2K]
        I/O ports at 2400 [size=128]
        Capabilities: <access denied>

02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 20)
        Subsystem: Compaq Computer Corporation Unknown device 0860
        Flags: bus master, medium devsel, latency 128, IRQ 10
        I/O ports at 2000 [size=256]
        Memory at 90300000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

02:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
        Subsystem: Hewlett-Packard Company Unknown device 12f5
        Flags: bus master, medium devsel, latency 128, IRQ 5
        Memory at 90000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

02:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
        Subsystem: Compaq Computer Corporation Unknown device 0860
        Flags: bus master, medium devsel, latency 168, IRQ 5
        Memory at 90100000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
        Memory window 0: 30000000-33fff000 (prefetchable)
        Memory window 1: 38000000-3bfff000
        I/O window 0: 00002800-000028ff
        I/O window 1: 00002c00-00002cff
        16-bit legacy interface ports at 0001


Output of: ifconfig -a
> 
eth0      Link encap:Ethernet  HWaddr 00:0F:B0:01:48:5B  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:797 errors:0 dropped:0 overruns:0 frame:0
          TX packets:224 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:105981 (103.4 KiB)  TX bytes:70770 (69.1 KiB)
          Interrupt:10 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:0E:35:15:C8:17  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:15235 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2066 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:23973 (23.4 KiB)  TX bytes:10944 (10.6 KiB)
          Interrupt:5 Base address:0xe000 Memory:90000000-90000fff 

irda0     Link encap:IrLAP  HWaddr 00:00:00:00  
          NOARP  MTU:2048  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:8 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:7 Base address:0x2f8 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:42 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3739 (3.6 KiB)  TX bytes:3739 (3.6 KiB)


Output of: dmesg
> 
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   131024
[    0.000000]   HighMem    131024 ->   131024
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   131024
[    0.000000] On node 0 totalpages: 131024
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 991 pages used for memmap
[    0.000000]   Normal zone: 125937 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 COMPAQ                                ) @ 0x000f6560
[    0.000000] ACPI: RSDT (v001 HP     CPQ0860  0x07050420 CPQ  0x00000001) @ 0x1fff0c84
[    0.000000] ACPI: FADT (v002 HP     CPQ0860  0x00000002 CPQ  0x00000001) @ 0x1fff0c00
[    0.000000] ACPI: SSDT (v001 COMPAQ  CPQGysr 0x00001001 MSFT 0x0100000e) @ 0x1fff5c3c
[    0.000000] ACPI: DSDT (v001 HP       nx7000 0x00010000 MSFT 0x0100000e) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:e0000000)
[    0.000000] Detected 1694.650 MHz processor.
[   14.152927] Built 1 zonelists.  Total pages: 130001
[   14.152932] Kernel command line: root=UUID=ee6ddc50-2177-4ef4-ac4d-b6a1e61916d1 ro quiet splash
[   14.153095] Local APIC disabled by BIOS -- you can enable it with "lapic"
[   14.153105] mapped APIC to ffffd000 (0140a000)
[   14.153110] Enabling fast FPU save and restore... done.
[   14.153113] Enabling unmasked SIMD FPU exception support... done.
[   14.153125] Initializing CPU#0
[   14.153200] PID hash table entries: 2048 (order: 11, 8192 bytes)
[   14.154408] Console: colour VGA+ 80x25
[   14.154702] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   14.154992] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   14.168833] Memory: 508352k/524096k available (1992k kernel code, 15184k reserved, 893k data, 328k init, 0k highmem)
[   14.168842] virtual kernel memory layout:
[   14.168843]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   14.168845]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   14.168846]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   14.168847]     lowmem  : 0xc0000000 - 0xdffd0000   ( 511 MB)
[   14.168849]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[   14.168850]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[   14.168851]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[   14.168855] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   14.245164] Calibrating delay using timer specific routine.. 3391.35 BogoMIPS (lpj=6782715)
[   14.245205] Security Framework v1.0.0 initialized
[   14.245213] SELinux:  Disabled at boot.
[   14.245230] Mount-cache hash table entries: 512
[   14.245369] CPU: After generic identify, caps: afe9f9bf 00000000 00000000 00000000 00000180 00000000 00000000
[   14.245381] CPU: L1 I cache: 32K, L1 D cache: 32K
[   14.245384] CPU: L2 cache: 2048K
[   14.245387] CPU: After all inits, caps: afe9f9bf 00000000 00000000 00002040 00000180 00000000 00000000
[   14.245397] Compat vDSO mapped to ffffe000.
[   14.245401] Remapping vsyscall page to ffffe000
[   14.245413] Checking 'hlt' instruction... OK.
[   14.261255] SMP alternatives: switching to UP code
[   14.261452] Freeing SMP alternatives: 11k freed
[   14.261626] Early unpacking initramfs... done
[   14.599275] ACPI: Core revision 20060707
[   14.600007] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   14.602255] ACPI: setting ELCR to 0200 (from 0c20)
[   14.664364] CPU0: Intel(R) Pentium(R) M processor 1.70GHz stepping 06
[   14.664369] SMP motherboard not detected.
[   14.664372] Local APIC not detected. Using dummy APIC emulation.
[   14.664406] Brought up 1 CPUs
[   14.664636] Booting paravirtualized kernel on bare hardware
[   14.664702] Time:  0:06:34  Date: 05/01/107
[   14.664727] NET: Registered protocol family 16
[   14.664806] EISA bus registered
[   14.664810] ACPI: bus type pci registered
[   14.666096] PCI: PCI BIOS revision 2.10 entry at 0xf031f, last bus=3
[   14.666098] PCI: Using configuration type 1
[   14.666100] Setting up standard PCI resources
[   14.674940] ACPI: Interpreter enabled
[   14.674943] ACPI: Using PIC for interrupt routing
[   14.675191] ACPI: PCI Root Bridge [C046] (0000:00)
[   14.675198] PCI: Probing PCI hardware (bus 00)
[   14.675215] ACPI: Assume root bridge [\_SB_.C046] bus is 0
[   14.679145] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[   14.679149] PCI quirk: region 1100-113f claimed by ICH4 GPIO
[   14.679389] Boot video device is 0000:01:00.0
[   14.679632] PCI: Transparent bridge - 0000:00:1e.0
[   14.679683] PCI: Bus #03 (-#06) is hidden behind transparent bridge #02 (-#03) (try 'pci=assign-busses')
[   14.679685] Please report the result to linux-kernel to fix this permanently
[   14.679702] ACPI: PCI Interrupt Routing Table [\_SB_.C046._PRT]
[   14.690056] ACPI: PCI Interrupt Routing Table [\_SB_.C046.C047._PRT]
[   14.690261] ACPI: PCI Interrupt Routing Table [\_SB_.C046.C058._PRT]
[   14.712764] ACPI: Power Resource [C18D] (on)
[   14.713535] ACPI: Power Resource [C195] (on)
[   14.714515] ACPI: Power Resource [C19C] (on)
[   14.714822] ACPI: Power Resource [C1A6] (on)
[   14.716053] ACPI: PCI Interrupt Link [C0C2] (IRQs 5 *10)
[   14.716457] ACPI: PCI Interrupt Link [C0C3] (IRQs 5 *10)
[   14.716859] ACPI: PCI Interrupt Link [C0C4] (IRQs *5 10)
[   14.717268] ACPI: PCI Interrupt Link [C0C5] (IRQs *5 10)
[   14.717660] ACPI: PCI Interrupt Link [C0C6] (IRQs 5 10) *0, disabled.
[   14.718060] ACPI: PCI Interrupt Link [C0C7] (IRQs 5 10) *11
[   14.718455] ACPI: PCI Interrupt Link [C0C8] (IRQs 5 10) *0, disabled.
[   14.718854] ACPI: PCI Interrupt Link [C0C9] (IRQs *5 10)
[   14.719903] Linux Plug and Play Support v0.97 (c) Adam Belay
[   14.719912] pnp: PnP ACPI init
[   14.728663] pnp: PnP ACPI: found 15 devices
[   14.728668] PnPBIOS: Disabled by ACPI PNP
[   14.728705] PCI: Using ACPI for IRQ routing
[   14.728708] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   14.784761] NET: Registered protocol family 8
[   14.784763] NET: Registered protocol family 20
[   14.785210] pnp: 00:0d: ioport range 0x4d0-0x4d1 has been reserved
[   14.785214] pnp: 00:0d: ioport range 0x1000-0x107f could not be reserved
[   14.785217] pnp: 00:0d: ioport range 0x1100-0x113f has been reserved
[   14.785220] pnp: 00:0d: ioport range 0x1200-0x121f has been reserved
[   14.785459] PCI: Bridge: 0000:00:01.0
[   14.785462]   IO window: 3000-3fff
[   14.785466]   MEM window: 90400000-904fffff
[   14.785469]   PREFETCH window: 98000000-9fffffff
[   14.785475] PCI: Bus 3, cardbus bridge: 0000:02:04.0
[   14.785477]   IO window: 00002800-000028ff
[   14.785481]   IO window: 00002c00-00002cff
[   14.785485]   PREFETCH window: 30000000-33ffffff
[   14.785489]   MEM window: 38000000-3bffffff
[   14.785493] PCI: Bridge: 0000:00:1e.0
[   14.785496]   IO window: 2000-2fff
[   14.785501]   MEM window: 90000000-903fffff
[   14.785505]   PREFETCH window: 30000000-33ffffff
[   14.785519] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   14.785827] ACPI: PCI Interrupt Link [C0C4] enabled at IRQ 5
[   14.785830] PCI: setting IRQ 5 as level-triggered
[   14.785834] ACPI: PCI Interrupt 0000:02:04.0[A] -> Link [C0C4] -> GSI 5 (level, low) -> IRQ 5
[   14.785856] NET: Registered protocol family 2
[   14.824954] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   14.825023] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   14.825126] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[   14.825179] TCP: Hash tables configured (established 16384 bind 8192)
[   14.825182] TCP reno registered
[   14.836997] checking if image is initramfs... it is
[   15.508989] Freeing initrd memory: 6995k freed
[   15.509429] audit: initializing netlink socket (disabled)
[   15.509447] audit(1180656395.488:1): initialized
[   15.509581] VFS: Disk quotas dquot_6.5.1
[   15.509603] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   15.509658] io scheduler noop registered
[   15.509660] io scheduler anticipatory registered
[   15.509663] io scheduler deadline registered
[   15.509673] io scheduler cfq registered (default)
[   15.509978] isapnp: Scanning for PnP cards...
[   15.863674] isapnp: No Plug & Play device found
[   15.887162] Real Time Clock Driver v1.12ac
[   15.887230] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   15.887348] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   15.887573] serial8250: ttyS2 at I/O 0x3e8 (irq = 4) is a 16550A
[   15.887967] 00:03: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   15.888681] ACPI: PCI Interrupt Link [C0C3] enabled at IRQ 10
[   15.888684] PCI: setting IRQ 10 as level-triggered
[   15.888689] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [C0C3] -> GSI 10 (level, low) -> IRQ 10
[   15.888698] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[   15.888785] mice: PS/2 mouse device common for all mice
[   15.889317] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   15.889543] input: Macintosh mouse button emulation as /class/input/input0
[   15.889576] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   15.889580] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   15.889809] PNP: PS/2 Controller [PNP0303:C1A3,PNP0f13:C1A4] at 0x60,0x64 irq 1,12
[   15.900012] i8042.c: Detected active multiplexing controller, rev 1.1.
[   15.906769] serio: i8042 KBD port at 0x60,0x64 irq 1
[   15.906774] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   15.906776] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   15.906779] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   15.906781] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   15.907260] EISA: Probing bus 0 at eisa.0
[   15.907269] Cannot allocate resource for EISA slot 1
[   15.907271] Cannot allocate resource for EISA slot 2
[   15.907274] Cannot allocate resource for EISA slot 3
[   15.907276] Cannot allocate resource for EISA slot 4
[   15.907294] EISA: Detected 0 cards.
[   15.937383] TCP cubic registered
[   15.937392] NET: Registered protocol family 1
[   15.937413] Using IPI No-Shortcut mode
[   15.937471] ACPI: (supports S0 S3 S4 S5)
[   15.937511]   Magic number: 11:134:101
[   15.937890] Freeing unused kernel memory: 328k freed
[   15.940400] Time: tsc clocksource has been installed.
[   15.953454] input: AT Translated Set 2 keyboard as /class/input/input1
[   17.133015] Capability LSM initialized
[   17.163709] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   17.163715] ACPI: Processor [CPU0] (supports 8 throttling states)
[   17.456242] usbcore: registered new interface driver usbfs
[   17.456264] usbcore: registered new interface driver hub
[   17.456287] usbcore: registered new device driver usb
[   17.457064] USB Universal Host Controller Interface driver v3.0
[   17.457480] ACPI: PCI Interrupt Link [C0C2] enabled at IRQ 10
[   17.457484] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [C0C2] -> GSI 10 (level, low) -> IRQ 10
[   17.457497] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   17.457501] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   17.457677] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   17.457701] uhci_hcd 0000:00:1d.0: irq 10, io base 0x000048c0
[   17.457793] usb usb1: configuration #1 chosen from 1 choice
[   17.457814] hub 1-0:1.0: USB hub found
[   17.457819] hub 1-0:1.0: 2 ports detected
[   17.511469] SCSI subsystem initialized
[   17.528685] libata version 2.20 loaded.
[   17.549559] ieee1394: Initialized config rom entry `ip1394'
[   17.560340] ACPI: PCI Interrupt Link [C0C5] enabled at IRQ 5
[   17.560345] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [C0C5] -> GSI 5 (level, low) -> IRQ 5
[   17.560358] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   17.560362] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   17.560385] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   17.560411] uhci_hcd 0000:00:1d.1: irq 5, io base 0x000048e0
[   17.560506] usb usb2: configuration #1 chosen from 1 choice
[   17.560529] hub 2-0:1.0: USB hub found
[   17.560535] hub 2-0:1.0: 2 ports detected
[   17.560589] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   17.663745] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [C0C4] -> GSI 5 (level, low) -> IRQ 5
[   17.663759] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   17.663763] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   17.663788] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   17.663813] uhci_hcd 0000:00:1d.2: irq 5, io base 0x00004c00
[   17.663901] usb usb3: configuration #1 chosen from 1 choice
[   17.663925] hub 3-0:1.0: USB hub found
[   17.663930] hub 3-0:1.0: 2 ports detected
[   17.770629] ata_piix 0000:00:1f.1: version 2.10ac1
[   17.770645] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[   17.770655] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [C0C4] -> GSI 5 (level, low) -> IRQ 5
[   17.770674] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   17.770722] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00014c40 irq 14
[   17.773113] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00014c48 irq 15
[   17.773142] scsi0 : ata_piix
[   17.799572] usb 1-2: new low speed USB device using uhci_hcd and address 2
[    3.624000] Time: acpi_pm clocksource has been installed.
[    3.776000] usb 1-2: configuration #1 chosen from 1 choice
[    3.788000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[    3.788000] ata1.00: ATA-7: WDC WD1200VE-00KWT0, 01.03K01, max UDMA/100
[    3.788000] ata1.00: 234441648 sectors, multi 16: LBA48 
[    3.796000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[    3.796000] ata1.00: configured for UDMA/100
[    3.796000] scsi1 : ata_piix
[    4.020000] usb 3-2: new full speed USB device using uhci_hcd and address 2
[    4.116000] ata2.00: ATAPI, max MWDMA2
[    4.220000] usb 3-2: configuration #1 chosen from 1 choice
[    4.224000] usbcore: registered new interface driver hiddev
[    4.240000] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /class/input/input2
[    4.240000] input: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:1d.0-2
[    4.240000] usbcore: registered new interface driver usbhid
[    4.240000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[    4.280000] ata2.00: configured for MWDMA2
[    4.280000] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1200VE-00K 01.0 PQ: 0 ANSI: 5
[    4.280000] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD+RW GCA-4040N 1.19 PQ: 0 ANSI: 5
[    4.280000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [C0C2] -> GSI 10 (level, low) -> IRQ 10
[    4.332000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[10]  MMIO=[90200000-902007ff]  Max Packet=[1024]  IR/IT contexts=[4/8]
[    4.340000] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [C0C3] -> GSI 10 (level, low) -> IRQ 10
[    4.340000] eth0: RTL-8139C+ at 0xe084a000, 00:0f:b0:01:48:5b, IRQ 10
[    4.340000] 8139too Fast Ethernet driver 0.9.28
[    4.340000] ACPI: PCI Interrupt Link [C0C9] enabled at IRQ 5
[    4.340000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [C0C9] -> GSI 5 (level, low) -> IRQ 5
[    4.340000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    4.340000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.340000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[    4.340000] ehci_hcd 0000:00:1d.7: debug port 1
[    4.340000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    4.340000] ehci_hcd 0000:00:1d.7: irq 5, io mem 0xa0000000
[    4.344000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.344000] usb usb4: configuration #1 chosen from 1 choice
[    4.344000] hub 4-0:1.0: USB hub found
[    4.344000] hub 4-0:1.0: 6 ports detected
[    4.352000] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
[    4.352000] sda: Write Protect is off
[    4.356000] sda: Mode Sense: 00 3a 00 00
[    4.356000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.356000] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
[    4.356000] sda: Write Protect is off
[    4.356000] sda: Mode Sense: 00 3a 00 00
[    4.356000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.356000]  sda:<6>usb 1-2: USB disconnect, address 2
[    4.404000]  sda1 sda2 sda3 < sda5 >
[    4.436000] sd 0:0:0:0: Attached scsi disk sda
[    4.440000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.440000] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    4.448000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    4.448000] Uniform CD-ROM driver Revision: 3.20
[    4.448000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.700000] Attempting manual resume
[    4.700000] swsusp: Resume From Partition 8:5
[    4.700000] PM: Checking swsusp image.
[    4.700000] PM: Resume from disk failed.
[    4.724000] kjournald starting.  Commit interval 5 seconds
[    4.724000] EXT3-fs: mounted filesystem with ordered data mode.
[    4.860000] usb 3-2: USB disconnect, address 2
[    5.100000] usb 3-2: new full speed USB device using uhci_hcd and address 3
[    5.296000] usb 3-2: configuration #1 chosen from 1 choice
[    5.540000] usb 1-2: new low speed USB device using uhci_hcd and address 3
[    5.612000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023f464a405cfe]
[    5.720000] usb 1-2: configuration #1 chosen from 1 choice
[    5.740000] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /class/input/input3
[    5.740000] input: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:1d.0-2
[   15.196000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   16.268000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   16.280000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.344000] NET: Registered protocol family 17
[   16.728000] intel_rng: FWH not detected
[   16.768000] Linux agpgart interface v0.102 (c) Dave Jones
[   16.772000] agpgart: Detected an Intel 855PM Chipset.
[   16.784000] agpgart: AGP aperture is 256M @ 0xb0000000
[   16.928000] iTCO_vendor_support: vendor-support=0
[   16.928000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   16.928000] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x1060)
[   16.928000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   16.940000] Yenta: CardBus bridge found at 0000:02:04.0 [0e11:0860]
[   16.940000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   16.940000] Yenta: Routing CardBus interrupts to PCI
[   16.940000] Yenta TI: socket 0000:02:04.0, mfunc 0x001c1112, devctl 0x44
[   17.172000] Yenta: ISA IRQ mask 0x08d8, PCI irq 5
[   17.172000] Socket status: 30000006
[   17.172000] Yenta: Raising subordinate bus# of parent bus (#02) from #03 to #06
[   17.172000] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[   17.172000] cs: IO port probe 0x2000-0x2fff: clean.
[   17.172000] pcmcia: parent PCI bridge Memory window: 0x90000000 - 0x903fffff
[   17.172000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
[   17.556000] ieee80211_crypt: registered algorithm 'NULL'
[   17.668000] Bluetooth: Core ver 2.11
[   17.668000] NET: Registered protocol family 31
[   17.668000] Bluetooth: HCI device and connection manager initialized
[   17.668000] Bluetooth: HCI socket layer initialized
[   17.700000] Bluetooth: HCI USB driver ver 2.9
[   17.732000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   17.732000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   17.792000] usbcore: registered new interface driver hci_usb
[   17.792000] parport: PnPBIOS parport detected.
[   17.792000] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   17.832000] input: PC Speaker as /class/input/input4
[   17.884000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
[   17.884000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   17.884000] ACPI: PCI Interrupt 0000:02:02.0[A] -> Link [C0C5] -> GSI 5 (level, low) -> IRQ 5
[   17.884000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   17.884000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x236eb3, caps: 0x904713/0x10008
[   17.936000] irda_init()
[   17.936000] NET: Registered protocol family 23
[   17.944000] input: SynPS/2 Synaptics TouchPad as /class/input/input5
[   17.992000] wbsd: Winbond W83L51xD SD/MMC card interface driver
[   17.992000] wbsd: Copyright(c) Pierre Ossman
[   17.992000] pnp: Device 00:02 activated.
[   17.996000] mmc0: W83L51xD id 7112 at 0x248 irq 6 dma 0 PnP
[   18.180000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   18.220000] Detected unconfigured Compaq x1000 family SMSC IrDA chip, pre-configuring device.
[   18.220000] Setting up Intel 82801 controller and SMSC device
[   18.220000] Detected Chip id: 0x5a, setting up registers...
[   18.220000] found SMC SuperIO Chip (devid=0x5a rev=00 base=0x002e): LPC47N227
[   18.220000] smsc_superio_flat(): fir: 0x2f8, sir: 0x2e8, dma: 03, irq: 7, mode: 0x0e
[   18.220000] SMsC IrDA Controller found
[   18.220000]  IrCC version 2.0, firport 0x2f8, sirport 0x2e8 dma=3, irq=7
[   18.220000] smsc_ircc_set_sir_speed(), Setting speed to: 9600
[   18.220000] No transceiver found. Defaulting to Fast pin select
[   18.220000] IrDA: Registered device irda0
[   18.456000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [C0C3] -> GSI 10 (level, low) -> IRQ 10
[   18.456000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   18.496000] cs: IO port probe 0x100-0x3af: excluding 0x140-0x14f 0x200-0x20f
[   18.496000] cs: IO port probe 0x3e0-0x4ff: clean.
[   18.496000] cs: IO port probe 0x820-0x8ff: clean.
[   18.500000] cs: IO port probe 0xc00-0xcf7: clean.
[   18.500000] cs: IO port probe 0xa00-0xaff: clean.
[   19.276000] intel8x0_measure_ac97_clock: measured 55487 usecs
[   19.276000] intel8x0: clocking to 48000
[   19.532000] fuse init (API version 7.8)
[   19.564000] lp0: using parport0 (interrupt-driven).
[   19.612000] Adding 1510068k swap on /dev/disk/by-uuid/c82f8388-3233-4dc6-a2db-5e3d8ed5d3a1.  Priority:-1 extents:1 across:1510068k
[   19.744000] EXT3 FS on sda2, internal journal
[   23.936000] ACPI: AC Adapter [C134] (on-line)
[   24.008000] input: Power Button (FF) as /class/input/input6
[   24.012000] ACPI: Power Button (FF) [PWRF]
[   24.048000] input: Power Button (CM) as /class/input/input7
[   24.052000] ACPI: Power Button (CM) [C1BE]
[   24.092000] input: Lid Switch as /class/input/input8
[   24.092000] ACPI: Lid Switch [C136]
[   24.104000] Using specific hotkey driver
[   24.132000] ibm_acpi: ec object not found
[   24.156000] No dock devices found.
[   24.212000] ACPI: Battery Slot [C11F] (battery present)
[   24.228000] ACPI: Video Device [C0D0] (multi-head: yes  rom: no  post: no)
[   24.264000] pcc_acpi: loading...
[   26.804000] ttyS0: LSR safety check engaged!
[   26.836000] ttyS2: LSR safety check engaged!
[   28.360000] [drm] Initialized drm 1.1.0 20060810
[   28.372000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [C0C2] -> GSI 10 (level, low) -> IRQ 10
[   28.372000] [drm] Initialized radeon 1.25.0 20060524 on minor 0
[   29.536000] ppdev: user-space parallel port driver
[   30.528000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   30.528000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[   30.528000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
[   30.576000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   30.576000] apm: overridden by ACPI.
[   30.756000] [drm] Setting GART location based on new memory map
[   30.756000] [drm] Loading R200 Microcode
[   30.756000] [drm] writeback test succeeded in 2 usecs
[   30.844000] Bluetooth: L2CAP ver 2.8
[   30.844000] Bluetooth: L2CAP socket layer initialized
[   30.976000] Bluetooth: RFCOMM socket layer initialized
[   30.976000] Bluetooth: RFCOMM TTY layer initialized
[   30.976000] Bluetooth: RFCOMM ver 1.8
[   60.160000] NET: Registered protocol family 10
[   60.160000] lo: Disabled Privacy Extensions
[   60.160000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   70.788000] eth0: no IPv6 routers present
[  174.476000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  184.956000] eth1: no IPv6 routers present
[  200.480000] mtrr: no MTRR for 98000000,4000000 found
[  203.444000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[  203.444000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[  203.444000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
[  203.664000] [drm] Setting GART location based on new memory map
[  203.664000] [drm] Loading R200 Microcode
[  203.664000] [drm] writeback test succeeded in 1 usecs
[  210.460000] eth0: link down
[  281.224000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  281.548000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  292.160000] eth1: no IPv6 routers present
[  326.492000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  326.492000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  337.424000] eth0: no IPv6 routers present
[  341.896000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  344.344000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  747.768000] usb 4-1: new high speed USB device using ehci_hcd and address 4
[  747.900000] usb 4-1: configuration #1 chosen from 1 choice
[  748.092000] usbcore: registered new interface driver libusual
[  748.104000] Initializing USB Mass Storage driver...
[  748.104000] scsi2 : SCSI emulation for USB Mass Storage devices
[  748.104000] usb-storage: device found at 4
[  748.104000] usb-storage: waiting for device to settle before scanning
[  748.104000] usbcore: registered new interface driver usb-storage
[  748.104000] USB Mass Storage support registered.
[  753.104000] usb-storage: device scan complete
[  753.104000] scsi 2:0:0:0: Direct-Access     SanDisk  Cruzer Mini      0.1  PQ: 0 ANSI: 2
[  753.104000] SCSI device sdb: 2001888 512-byte hdwr sectors (1025 MB)
[  753.108000] sdb: Write Protect is off
[  753.108000] sdb: Mode Sense: 03 00 00 00
[  753.108000] sdb: assuming drive cache: write through
[  753.108000] SCSI device sdb: 2001888 512-byte hdwr sectors (1025 MB)
[  753.108000] sdb: Write Protect is off
[  753.108000] sdb: Mode Sense: 03 00 00 00
[  753.108000] sdb: assuming drive cache: write through
[  753.108000]  sdb: sdb1
[  753.112000] sd 2:0:0:0: Attached scsi removable disk sdb
[  753.112000] sd 2:0:0:0: Attached scsi generic sg2 type 0


---

### Post by MusicMastaMike on 2007-06-01
Output of: lsmod
> 
Module                  Size  Used by
nls_iso8859_1           5120  1 
nls_cp437               6784  1 
vfat                   14208  1 
fat                    53916  1 vfat
usb_storage            72256  1 
libusual               17936  1 usb_storage
ipv6                  268704  8 
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25728  5 rfcomm
ppdev                  10116  0 
radeon                124576  2 
drm                    81044  3 radeon
speedstep_centrino      9920  0 
cpufreq_stats           7360  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9228  1 
cpufreq_userspace       5408  0 
freq_table              5792  3 speedstep_centrino,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8200  0 
pcc_acpi               13184  0 
sony_acpi               6284  0 
dev_acpi               12292  0 
tc1100_wmi              8068  0 
sbs                    15652  0 
video                  16388  0 
battery                10756  0 
dock                   10268  0 
button                  8720  0 
container               5248  0 
ac                      6020  0 
i2c_ec                  5888  1 sbs
i2c_core               22784  1 i2c_ec
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
sbp2                   23812  0 
lp                     12452  0 
fuse                   46612  0 
snd_intel8x0           34204  1 
snd_ac97_codec         98336  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
joydev                 10816  0 
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
irtty_sir               9600  0 
sir_dev                17156  1 irtty_sir
smsc_ircc2             23324  0 
pcmcia                 39212  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
wbsd                   18824  0 
mmc_core               26756  1 wbsd
irda                  201276  3 irtty_sir,sir_dev,smsc_ircc2
ipw2200               148040  0 
pcspkr                  4224  0 
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
crc_ccitt               3072  1 irda
ieee80211              34760  1 ipw2200
hci_usb                18204  2 
bluetooth              55908  7 rfcomm,l2cap,hci_usb
snd                    54020  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ieee80211_crypt         7040  1 ieee80211
psmouse                38920  0 
serio_raw               7940  0 
yenta_socket           27532  1 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40852  3 pcmcia,yenta_socket,rsrc_nonstatic
iTCO_wdt               11812  0 
iTCO_vendor_support     4868  1 iTCO_wdt
soundcore               8672  1 snd
intel_agp              25116  1 
agpgart                35400  2 drm,intel_agp
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm
af_packet              23816  4 
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
tsdev                   8768  0 
evdev                  11008  4 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sr_mod                 17060  0 
cdrom                  37664  1 sr_mod
sd_mod                 23428  5 
8139too                27648  0 
generic                 5124  0 [permanent]
usbhid                 26592  0 
hid                    27392  1 usbhid
ata_piix               15492  2 
ehci_hcd               34188  0 
8139cp                 25088  0 
mii                     6528  2 8139too,8139cp
ohci1394               36528  0 
ieee1394              299448  2 sbp2,ohci1394
ata_generic             9092  0 
libata                125720  2 ata_piix,ata_generic
scsi_mod              142348  6 usb_storage,sbp2,sg,sr_mod,sd_mod,libata
uhci_hcd               25360  0 
usbcore               134280  7 usb_storage,libusual,hci_usb,usbhid,ehci_hcd,uhci_hcd
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability


Contents of: /etc/network/interfaces
> 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


---

### Post by MusicMastaMike on 2007-06-01
anyone have any ideas on this?

---

### Post by MusicMastaMike on 2007-06-02
bump... i really need some help on this, if anyone has a clue.

---

### Post by handydan918 on 2007-06-02
What does sudo dhclient give you?

---

### Post by 4ebees on 2007-06-02
> **MusicMastaMike said:**
> bump... i really need some help on this, if anyone has a clue.

Hi,

You might want to keep an eye on this post:

[http://ubuntuforums.org/showthread.php?p=2770493#post2770493](http://ubuntuforums.org/showthread.php?p=2770493#post2770493)

---

### Post by MusicMastaMike on 2007-06-02
Here's the output of: sudo dhclient

> Listening on LPF/eth1/00:0e:35:15:c8:17
Sending on   LPF/eth1/00:0e:35:15:c8:17
Listening on LPF/eth0/00:0f:b0:01:48:5b
Sending on   LPF/eth0/00:0f:b0:01:48:5b
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPOFFER from 192.168.2.1
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPNAK from 192.168.2.1
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPNAK from 192.168.2.1
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 192.168.2.1
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPNAK from 192.168.2.1
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPNAK from 192.168.2.1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by Gatecrasherc6 on 2007-06-18
Any help would be appreciated on this topic as I'm running into the same problem on Feisty.  My wired connection works on eth0. My wireless on eth1 is a completely different story.  I have tried dhclient, ifup, ifdown, shutting down nm-applet.  I have obtained similar results as MusicMastaMike.

---

### Post by RobMBaker on 2007-07-06
Bump ...

I'm having a very similar problem, but I can give a few more details:
I've been using Feisty until a week ago, just with wireless - everything fine - then I got back to the UK and had to use my ethernet connection, and it won't connect to the network.
So, thinking I'd busted something myself, I reinstalled everything; and it worked fine ... until today, when it's gone back to the same problem. The only things I've installed today are (from Synaptic history):-

cabextract (1.2-2)
flashplugin-nonfree (9.0.31.0.2ubuntu1)
gstreamer0.10-ffmpeg (0.10.2-0ubuntu4)
gstreamer0.10-plugins-bad (0.10.4-1ubuntu1)
gstreamer0.10-plugins-ugly (0.10.5-0ubuntu2)
gstreamer0.10-plugins-ugly-multiverse (0.10.5-2)
gxine (0.5.11-1ubuntu2)
java-common (0.25uuntu2)
liba52-0.7.4 (0.7.4-7)
libcdaudio1 (0.99.12p2-2)
libdvdread3 (0.9.7-2ubuntu1)
libfreebob0 (1.0.0-3)
libgsm1 (1.0.10-13)
libid3tag0 (0.15.1b-8)
libjack0.100.0-0 (0.102.20-1)
liblame0 (3.96.1-2ubuntu1)
libltdl3 (1.5.22-4)
libmad0 (0.15.1b-2.1)
libmms0 (0.3-2ubuntu1)
libmodplug0c2 (1:0.7-5.2build1)
libmpcdec3 (1.2.2-1)
libmpeg2-4 (0.4.1-1)
libpulse0 (0.9.5-5ubuntu4.1)
libsidplay1 (1.36.59-4)
libsoundtouch1c2 (1.3.0-2.1)
libswfdec0.3 (0.3.6-2.1)
libwavpack1 (4.40.0-1)
libxine1 (1.1.4-2ubuntu3)
libxvmc1 (2:1.0.2-0ubuntu2)
msttcorefonts (1.8ubuntu1)
odbcinst1debian1 (2.2.11-13)
sun-java6-bin (6-00-2ubuntu2)
sun-java6-jre (6-00-2ubuntu2)
sun-java6-plugin (6-00-2ubuntu2)
ubuntu-restricted-extras (2.2)
unixodbc (2.2.11-13)

All of the above are the results of using Add/Remove Programs; so I went back and removed all the programs that I think I added today ... and did apt-get autoremove, just to be sure ... no joy though ... I even removed Network Manager just in case that was causing issues.
I couldn't remove Sun Java 6 though ...

Would be good to fix this, as it's really annoying me.

---

### Post by kevdog on 2007-07-06
What does 
lshw -C network show??

Can you also edit you /etc/modbrobe.d/blacklist file and add the following:
blacklist ipv6

Reboot.

---

### Post by RobMBaker on 2007-07-06
Don't worry - I think I fixed it ...

I had been using "pci=noapic" as a boot option, to stop my USB crashing sporadically; which was also disabling the ethernet card (though, strangely, not the wireless).
I just added "pci=biosirq" as well (to /boot/grub/menu.lst) and it all seems to work fine now - I also tried using irqpoll instead of pci=biosirq, which fixed the ethernet, but broke the CD drive ...

Hope that's helpful to someone else ...

---

