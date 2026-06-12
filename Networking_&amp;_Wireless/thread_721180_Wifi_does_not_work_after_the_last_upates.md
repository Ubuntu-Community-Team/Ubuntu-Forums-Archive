---
title: "Wifi does not work after the last upates"
date: 2008-03-11
forum: Networking &amp; Wireless
---

### Post by jatorrero on 2008-03-11
Hi:

Three weeks ago I installed Ubuntu 7.10 in a laptop with a Centrino CPU. The Wifi configuration was extremely easy using Network Manager. I just chose the name of the wifi nework and wrote the key. My laptop has a hardware switch to turn on/off the wifi, and it worked perfectly

But the last week, when I updated some modules, the wifi stopped working. I have tried to configure manually, but it does not work too. The hardware switch does not work too.

I have noticed that the eth1 interface (that it is assigned to my wifi card) is always off. The dmesg shows that RF Kill switch is on, so I have tried to modify it, and change the rf_kill to '0'. I have tried to use ndiswrapper too. I also tried to reinstall the ipw2200 module. Nothing works.

I have read also that the problems is solved if you boot on windows, change the state of the wifi and then reeboot on Ubuntu. But I do not have windows.

Could you give some help? Is there a way to restore the previous state without install Ubuntu again?

---

### Post by ajmorris on 2008-03-11
hi there,
could you please post the output of:
```
sudo iwconfig
sudo ifconfig
sudo ndiswrapper -l
sudo dmesg
sudo lspci
```

AJ

---

### Post by jatorrero on 2008-03-11
Sorry but I do not know how to include code in the forums:

eth1      radio off  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


eth0      Link encap:Ethernet  direcciónHW 00:02:3F:0B:B9:8D  
          inet addr:192.168.1.27  Difusión:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::202:3fff:fe0b:b98d/64 Scope:Link
          UP DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Metric:1
          RX packets:13529 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12952 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:7683024 (7.3 MB)  TX bytes:2343444 (2.2 MB)
          Interrupt:10 Base address:0x6000 

eth1      Link encap:Ethernet  direcciónHW 00:0E:35:C9:86:43  
          UP DIFUSIÓN MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0xe000 Memory:d0000000-d0000fff 

lo        Link encap:Bucle local  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK CORRIENDO  MTU:16436  Metric:1
          RX packets:8349 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8349 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:1872323 (1.7 MB)  TX bytes:1872323 (1.7 MB)

[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 07:42:25 UTC 2008 (Ubuntu 2.6.22-14.52-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)
[    0.000000]  BIOS-e820: 000000003fff0000 - 000000003fffffc0 (ACPI data)
[    0.000000]  BIOS-e820: 000000003fffffc0 - 0000000040000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000ffb80000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 262128) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   262128
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   262128
[    0.000000] On node 0 totalpages: 262128
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 255 pages used for memmap
[    0.000000]   HighMem zone: 32497 pages, LIFO batch:7
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00E6010 checksum 0
[    0.000000] ACPI: RSDP 000E6010, 0014 (r0 OID_00)
[    0.000000] ACPI: RSDT 3FFFA7F0, 0034 (r1 INSYDE RSDT_000        1 _CSI    10101)
[    0.000000] ACPI: FACP 3FFFFB00, 0074 (r1 COMPAL DCL56         200 _CSI    10101)
[    0.000000] ACPI: DSDT 3FFFAC70, 4E8A (r1 COMPAL   DCL561        6 MSFT  100000E)
[    0.000000] ACPI: FACS 3FFFFFC0, 0040
[    0.000000] ACPI: BOOT 3FFFFB90, 0028 (r1 INSYDE SYS_BOOT      100 _CSI    10101)
[    0.000000] ACPI: DBGP 3FFFFBC0, 0034 (r1 INSYDE DBGP_000      100 _CSI    10101)
[    0.000000] ACPI: SSDT 3FFFA830, 02DC (r1 INSYDE   GV3Ref     2000 INTL 20021002)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bfb80000)
[    0.000000] Built 1 zonelists.  Total pages: 260081
[    0.000000] Kernel command line: root=UUID=13616ae8-1678-475a-8d5c-a0731054e870 ro quiet splash
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffd000 (0180e000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1794.244 MHz processor.
[   10.040197] Console: colour VGA+ 80x25
[   10.040810] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   10.041394] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   10.078398] Memory: 1027880k/1048512k available (2015k kernel code, 19940k reserved, 915k data, 364k init, 131008k highmem)
[   10.078408] virtual kernel memory layout:
[   10.078409]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   10.078410]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   10.078411]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   10.078413]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   10.078414]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   10.078415]       .data : 0xc02f7e86 - 0xc03dce84   ( 915 kB)
[   10.078416]       .text : 0xc0100000 - 0xc02f7e86   (2015 kB)
[   10.078420] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   10.078456] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   10.158377] Calibrating delay using timer specific routine.. 3590.84 BogoMIPS (lpj=7181683)
[   10.158401] Security Framework v1.0.0 initialized
[   10.158408] SELinux:  Disabled at boot.
[   10.158422] Mount-cache hash table entries: 512
[   10.158544] CPU: After generic identify, caps: afe9f9bf 00000000 00000000 00000000 00000180 00000000 00000000
[   10.158556] CPU: L1 I cache: 32K, L1 D cache: 32K
[   10.158558] CPU: L2 cache: 2048K
[   10.158561] CPU: After all inits, caps: afe9f9bf 00000000 00000000 00002040 00000180 00000000 00000000
[   10.158570] Compat vDSO mapped to ffffe000.
[   10.158581] Checking 'hlt' instruction... OK.
[   10.174457] SMP alternatives: switching to UP code
[   10.174655] Freeing SMP alternatives: 11k freed
[   10.174911] Early unpacking initramfs... done
[   10.500326] ACPI: Core revision 20070126
[   10.500392] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   10.502141] ACPI: setting ELCR to 0200 (from 0c00)
[   10.508585] CPU0: Intel(R) Pentium(R) M processor 1.80GHz stepping 06
[   10.508591] SMP motherboard not detected.
[   10.508593] Local APIC not detected. Using dummy APIC emulation.
[   10.508625] Brought up 1 CPUs
[   10.508730] Booting paravirtualized kernel on bare hardware
[   10.508795] Time:  7:42:40  Date: 02/11/108
[   10.508817] NET: Registered protocol family 16
[   10.508893] EISA bus registered
[   10.508906] ACPI: bus type pci registered
[   10.508964] PCI: PCI BIOS revision 2.10 entry at 0xe97a4, last bus=2
[   10.508966] PCI: Using configuration type 1
[   10.508968] Setting up standard PCI resources
[   10.510855] ACPI: EC: Look up EC in DSDT
[   10.513435] ACPI: EC: GPE=0x1c, ports=0x66, 0x62
[   10.514424] ACPI: Interpreter enabled
[   10.514426] ACPI: (supports S0 S1 S3 S4 S5)
[   10.514439] ACPI: Using PIC for interrupt routing
[   10.559188] ACPI: EC: GPE=0x1c, ports=0x66, 0x62
[   10.559225] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   10.559229] PCI: Probing PCI hardware (bus 00)
[   10.559578] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[   10.559582] PCI quirk: region 1300-133f claimed by ICH4 GPIO
[   10.560050] PCI: Transparent bridge - 0000:00:1e.0
[   10.560111] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   10.560287] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
[   10.560357] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB_._PRT]
[   10.565703] ACPI: PCI Interrupt Link [LNKA] (IRQs 5 *10)
[   10.565777] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 10) *11
[   10.565850] ACPI: PCI Interrupt Link [LNKC] (IRQs 5 10) *11
[   10.565929] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 10) *11
[   10.566004] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[   10.566082] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[   10.566160] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[   10.566238] ACPI: PCI Interrupt Link [LNKH] (IRQs 5 10) *11
[   10.566317] Linux Plug and Play Support v0.97 (c) Adam Belay
[   10.566325] pnp: PnP ACPI init
[   10.566334] ACPI: bus type pnp registered
[   10.568593]  00:08: SMCf010 not responding at SIR 0x2f8, FIR 0x6f8; auto-configuring
[   10.568661] pnp: Device 00:08 disabled.
[   10.570982] pnp: Device 00:08 activated.
[   10.570991]  00:08: responds at SIR 0x2f8, FIR 0x6f8
[   10.590086] pnp: PnP ACPI: found 11 devices
[   10.590089] ACPI: ACPI bus type pnp unregistered
[   10.590092] PnPBIOS: Disabled by ACPI PNP
[   10.590127] PCI: Using ACPI for IRQ routing
[   10.590130] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   10.590157] PCI: Cannot allocate resource region 0 of device 0000:02:03.0
[   10.592850] NET: Registered protocol family 8
[   10.592852] NET: Registered protocol family 20
[   10.592897] pnp: 00:01: iomem range 0xfff80000-0xffffffff could not be reserved
[   10.593840] Time: tsc clocksource has been installed.
[   10.623108] PCI: Bridge: 0000:00:01.0
[   10.623111]   IO window: c000-dfff
[   10.623114]   MEM window: e0000000-efffffff
[   10.623117]   PREFETCH window: a0000000-afffffff
[   10.623125] PCI: Bus 3, cardbus bridge: 0000:02:03.0
[   10.623127]   IO window: 0000a400-0000a4ff
[   10.623131]   IO window: 0000a800-0000a8ff
[   10.623135]   PREFETCH window: 90000000-93ffffff
[   10.623139]   MEM window: d4000000-d7ffffff
[   10.623143] PCI: Bridge: 0000:00:1e.0
[   10.623145]   IO window: a000-bfff
[   10.623150]   MEM window: d0000000-dfffffff
[   10.623154]   PREFETCH window: 90000000-9fffffff
[   10.623168] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   10.623302] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[   10.623305] PCI: setting IRQ 10 as level-triggered
[   10.623309] ACPI: PCI Interrupt 0000:02:03.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[   10.623323] NET: Registered protocol family 2
[   10.661784] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   10.661847] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   10.663274] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   10.664073] TCP: Hash tables configured (established 131072 bind 65536)
[   10.664077] TCP reno registered
[   10.673923] checking if image is initramfs... it is
[   11.125214] Switched to high resolution mode on CPU 0
[   11.314108] Freeing initrd memory: 7070k freed
[   11.314280] Simple Boot Flag at 0x37 set to 0x1
[   11.314496] audit: initializing netlink socket (disabled)
[   11.314512] audit(1205221360.020:1): initialized
[   11.314593] highmem bounce pool size: 64 pages
[   11.316276] VFS: Disk quotas dquot_6.5.1
[   11.316324] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   11.316413] io scheduler noop registered
[   11.316415] io scheduler anticipatory registered
[   11.316417] io scheduler deadline registered
[   11.316431] io scheduler cfq registered (default)
[   11.316503] Boot video device is 0000:01:00.0
[   11.316657] isapnp: Scanning for PnP cards...
[   11.670057] isapnp: No Plug & Play device found
[   11.692985] Real Time Clock Driver v1.12ac
[   11.693101] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   11.693308] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   11.694019] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[   11.694023] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   11.694032] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[   11.694531] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   11.694730] input: Macintosh mouse button emulation as /class/input/input0
[   11.694802] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   11.695061] i8042.c: Detected active multiplexing controller, rev 1.1.
[   11.695103] serio: i8042 KBD port at 0x60,0x64 irq 1
[   11.695108] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   11.695110] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   11.695113] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   11.695115] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   11.695275] mice: PS/2 mouse device common for all mice
[   11.695523] EISA: Probing bus 0 at eisa.0
[   11.695531] Cannot allocate resource for EISA slot 1
[   11.695559] EISA: Detected 0 cards.
[   11.695732] TCP cubic registered
[   11.695750] NET: Registered protocol family 1
[   11.695776] Using IPI No-Shortcut mode
[   11.695932]   Magic number: 0:232:723
[   11.696329] Freeing unused kernel memory: 364k freed
[   11.768372] input: AT Translated Set 2 keyboard as /class/input/input1
[   12.872653] AppArmor: AppArmor initialized<5>audit(1205221361.520:2):  type=1505 info="AppArmor initialized" pid=1183
[   12.877881] fuse init (API version 7.8)
[   12.881669] Failure registering capabilities with primary security module.
[   12.899294] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
[   12.899300] ACPI: Processor [CPU0] (supports 8 throttling states)
[   13.256353] usbcore: registered new interface driver usbfs
[   13.256377] usbcore: registered new interface driver hub
[   13.256394] usbcore: registered new device driver usb
[   13.257116] USB Universal Host Controller Interface driver v3.0
[   13.257369] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
[   13.257372] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[   13.257383] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   13.257386] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   13.257586] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   13.257609] uhci_hcd 0000:00:1d.0: irq 10, io base 0x00001200
[   13.257713] usb usb1: configuration #1 chosen from 1 choice
[   13.257739] hub 1-0:1.0: USB hub found
[   13.257745] hub 1-0:1.0: 2 ports detected
[   13.341894] SCSI subsystem initialized
[   13.346758] libata version 2.21 loaded.
[   13.359475] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10
[   13.359480] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[   13.359492] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   13.359495] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   13.359519] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   13.359543] uhci_hcd 0000:00:1d.1: irq 10, io base 0x00001600
[   13.359636] usb usb2: configuration #1 chosen from 1 choice
[   13.359666] hub 2-0:1.0: USB hub found
[   13.359672] hub 2-0:1.0: 2 ports detected
[   13.388995] 8139too Fast Ethernet driver 0.9.28
[   13.462237] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[   13.462251] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   13.462255] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   13.462278] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   13.462301] uhci_hcd 0000:00:1d.2: irq 10, io base 0x00001700
[   13.462396] usb usb3: configuration #1 chosen from 1 choice
[   13.462419] hub 3-0:1.0: USB hub found
[   13.462425] hub 3-0:1.0: 2 ports detected
[   13.568023] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 10
[   13.568028] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 10 (level, low) -> IRQ 10
[   13.568040] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   13.568044] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   13.568072] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[   13.568104] ehci_hcd 0000:00:1d.7: debug port 1
[   13.568110] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   13.568118] ehci_hcd 0000:00:1d.7: irq 10, io mem 0xf4000000
[   13.572023] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   13.572102] usb usb4: configuration #1 chosen from 1 choice
[   13.572130] hub 4-0:1.0: USB hub found
[   13.572136] hub 4-0:1.0: 6 ports detected
[   13.676636] ata_piix 0000:00:1f.1: version 2.11
[   13.676651] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[   13.676661] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[   13.676695] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   13.676772] scsi0 : ata_piix
[   13.690986] scsi1 : ata_piix
[   13.691197] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011100 irq 14
[   13.691200] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011108 irq 15
[    3.692000] Marking TSC unstable due to: possible TSC halt in C2.
[    3.696000] Time: acpi_pm clocksource has been installed.
[    3.784000] ata1.00: ATA-6: FUJITSU MHT2080AT, 0022, max UDMA/100
[    3.784000] ata1.00: 156301488 sectors, multi 16: LBA 
[    3.800000] ata1.00: configured for UDMA/100
[    4.160000] ata2.00: ATAPI: TOSHIBA ODD-DVD SD-R6372, 1030, max UDMA/33
[    4.356000] ata2.00: configured for UDMA/33
[    4.356000] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHT2080A 0022 PQ: 0 ANSI: 5
[    4.360000] scsi 1:0:0:0: CD-ROM            TOSHIBA  ODD-DVD SD-R6372 1030 PQ: 0 ANSI: 5
[    4.360000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[    4.412000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[10]  MMIO=[d0001800-d0001fff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    4.428000] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[    4.428000] eth0: RealTek RTL8139 at 0xf8856000, 00:02:3f:0b:b9:8d, IRQ 10
[    4.428000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    4.432000] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    4.436000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    4.436000] sd 0:0:0:0: [sda] Write Protect is off
[    4.436000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.436000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.436000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    4.436000] sd 0:0:0:0: [sda] Write Protect is off
[    4.436000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.436000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.436000]  sda: sda1 sda2 < sda5 >
[    4.536000] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.540000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.540000] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    4.584000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    4.584000] Uniform CD-ROM driver Revision: 3.20
[    4.584000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.768000] Attempting manual resume
[    4.768000] swsusp: Resume From Partition 8:5
[    4.768000] PM: Checking swsusp image.
[    4.772000] PM: Resume from disk failed.
[    4.824000] kjournald starting.  Commit interval 5 seconds
[    4.824000] EXT3-fs: mounted filesystem with ordered data mode.
[    5.692000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023f4a524016a2]
[   13.048000] Clocksource tsc unstable (delta = -357291032 ns)
[   14.580000] Linux agpgart interface v0.102 (c) Dave Jones
[   14.588000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   14.592000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   14.720000] agpgart: Detected an Intel 855PM Chipset.
[   14.724000] agpgart: AGP aperture is 64M @ 0xb0000000
[   14.732000] iTCO_vendor_support: vendor-support=0
[   14.732000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   14.732000] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x1060)
[   14.732000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   14.756000] intel_rng: Firmware space is locked read-only. <4>intel_rng: If you can't or
[   14.756000]  don't want to <4>intel_rng: disable this in firmware setup, and <4>intel_rng: if
[   14.756000]  you are certain that your <4>intel_rng: system has a functional
[   14.756000]  RNG, try<4>intel_rng: using the 'no_fwh_detect' option.
[   15.420000] Yenta: CardBus bridge found at 0000:02:03.0 [14c0:0012]
[   15.420000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   15.420000] Yenta: Routing CardBus interrupts to PCI
[   15.420000] Yenta TI: socket 0000:02:03.0, mfunc 0x001c1112, devctl 0x44
[   15.556000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x254ab1, caps: 0x804713/0x0
[   15.588000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[   15.652000] Yenta: ISA IRQ mask 0x08c8, PCI irq 10
[   15.652000] Socket status: 30000006
[   15.652000] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   15.652000] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xbfff
[   15.652000] cs: IO port probe 0xa000-0xbfff: clean.
[   15.652000] pcmcia: parent PCI bridge Memory window: 0xd0000000 - 0xdfffffff
[   15.652000] pcmcia: parent PCI bridge Memory window: 0x90000000 - 0x9fffffff
[   15.772000] input: PC Speaker as /class/input/input3
[   15.796000] parport_pc 00:09: reported by Plug and Play ACPI
[   15.796000] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   15.820000] ieee80211_crypt: registered algorithm 'NULL'
[   15.900000] ieee80211: 802.11 data/management/control stack, 1.2.18
[   15.900000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   15.972000] wbsd: Winbond W83L51xD SD/MMC card interface driver
[   15.972000] wbsd: Copyright(c) Pierre Ossman
[   15.972000] pnp: Device 00:0a activated.
[   15.980000] mmc0: W83L51xD id 7112 at 0x248 irq 6 FIFO PnP
[   16.040000] irda_init()
[   16.040000] NET: Registered protocol family 23
[   16.056000] found SMC SuperIO Chip (devid=0x7a rev=00 base=0x002e): LPC47N227
[   16.056000] smsc_superio_flat(): fir: 0x6f8, sir: 0x2f8, dma: 01, irq: 3, mode: 0x0e
[   16.056000] smsc_ircc_present: can't get sir_base of 0x2f8
[   16.108000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2
[   16.108000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   16.108000] ACPI: PCI Interrupt 0000:02:02.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[   16.112000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   16.304000] ipw2200: Radio Frequency Kill Switch is On:
[   16.304000] Kill switch must be turned off for wireless networking to work.
[   16.304000] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)
[   16.548000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   16.548000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   16.660000] cs: IO port probe 0x100-0x3af: clean.
[   16.660000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   16.660000] cs: IO port probe 0x820-0x8ff: clean.
[   16.664000] cs: IO port probe 0xc00-0xcf7: clean.
[   16.664000] cs: IO port probe 0xa00-0xaff: clean.
[   17.376000] intel8x0_measure_ac97_clock: measured 55288 usecs
[   17.376000] intel8x0: clocking to 48000
[   18.380000] lp0: using parport0 (interrupt-driven).
[   18.476000] ndiswrapper version 1.45 loaded (smp=yes)
[   18.528000] usbcore: registered new interface driver ndiswrapper
[   18.624000] ieee80211_crypt: registered algorithm 'CCMP'
[   18.664000] ieee80211_crypt: registered algorithm 'TKIP'
[   18.716000] ieee80211_crypt: registered algorithm 'WEP'
[   18.768000] Adding 3028212k swap on /dev/sda5.  Priority:-1 extents:1 across:3028212k
[   19.416000] EXT3 FS on sda1, internal journal
[   20.508000] ACPI: Battery Slot [BAT1] (battery present)
[   20.684000] ACPI: AC Adapter [ACAD] (off-line)
[   20.724000] No dock devices found.
[   20.728000] ACPI: \_SB_.PCI0.IDEC.SECD.S_D0: found ejectable bay
[   20.728000] ACPI: \_SB_.PCI0.IDEC.SECD.S_D0: Adding notify handler
[   20.728000] ACPI: Error installing bay notify handler
[   20.728000] ACPI: Bay [\_SB_.PCI0.IDEC.SECD.S_D0] Added
[   20.812000] input: Power Button (FF) as /class/input/input4
[   20.812000] ACPI: Power Button (FF) [PWRF]
[   20.812000] ACPI Error (evxfevnt-0186): Could not enable SleepButton event [20070126]
[   20.812000] ACPI Warning (evxface-0145): Could not enable fixed event 3 [20070126]
[   20.848000] input: Lid Switch as /class/input/input5
[   20.852000] ACPI: Lid Switch [LID]
[   20.888000] input: Power Button (CM) as /class/input/input6
[   20.892000] ACPI: Power Button (CM) [PWRB]
[   22.376000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   22.472000] ppdev: user-space parallel port driver
[   22.760000] audit(1205221382.423:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4642 profile="/usr/sbin/cupsd"
[   22.836000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   22.836000] apm: overridden by ACPI.
[   23.176000] Failure registering capabilities with primary security module.
[   23.400000] Bluetooth: Core ver 2.11
[   23.400000] NET: Registered protocol family 31
[   23.400000] Bluetooth: HCI device and connection manager initialized
[   23.400000] Bluetooth: HCI socket layer initialized
[   23.428000] Bluetooth: L2CAP ver 2.8
[   23.428000] Bluetooth: L2CAP socket layer initialized
[   23.580000] Bluetooth: RFCOMM socket layer initialized
[   23.580000] Bluetooth: RFCOMM TTY layer initialized
[   23.580000] Bluetooth: RFCOMM ver 1.8
[   25.052000] [drm] Initialized drm 1.1.0 20060810
[   25.068000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[   25.072000] [drm] Initialized radeon 1.27.0 20060524 on minor 0
[   26.476000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   26.476000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   26.476000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[   27.664000] NET: Registered protocol family 17
[   27.740000] [drm] Setting GART location based on new memory map
[   27.740000] [drm] Loading R300 Microcode
[   27.740000] [drm] writeback test succeeded in 2 usecs
[   34.432000] NET: Registered protocol family 10
[   34.432000] lo: Disabled Privacy Extensions
[   34.432000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   44.572000] eth0: no IPv6 routers present
[ 1351.060000] ipw2200: Failed to send POWER_MODE: Command timed out.
[ 1379.012000] ipw2200: Failed to send TX_POWER: Command timed out.


00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 21)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 21)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
02:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
02:03.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)

---

### Post by ajmorris on 2008-03-15
could you please try: ```
sudo ifup eth1
```

also, are you using ndiswrapper or the native linux drivers?

---

### Post by jatorrero on 2008-03-17
the output of sudo ifup eth1:

```

Ignoring unknown interface eth1=eth1.

```

And still the radio is off.

I am using the ipw2200 drivers right now.

---

### Post by ajmorris on 2008-03-18
sorry for asking for so many command outputs, but could you please post the output of ```
sudo lsmod
```

---

### Post by jatorrero on 2008-03-18
No problem.

Here is the output of sudo lsmod

```

~$ sudo lsmod
[sudo] password for jatorrero:
Module                  Size  Used by
ipv6                  273892  8 
af_packet              24840  2 
binfmt_misc            12936  1 
radeon                125472  2 
drm                    83348  3 radeon
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
acpi_cpufreq           10568  0 
cpufreq_powersave       2688  0 
cpufreq_userspace       5280  0 
cpufreq_stats           7232  0 
cpufreq_ondemand        9612  1 
cpufreq_conservative     8072  0 
freq_table              5792  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
sbs                    19592  0 
video                  18060  0 
button                  8976  0 
container               5504  0 
bay                     6912  0 
dock                   10656  1 bay
ac                      6148  0 
battery                11012  0 
ieee80211_crypt_wep     6400  0 
ieee80211_crypt_tkip    12800  0 
ieee80211_crypt_ccmp     9088  0 
rfkill_input            5376  0 
rfkill                  8208  1 rfkill_input
ndiswrapper           185240  0 
sbp2                   24072  0 
lp                     12580  0 
snd_intel8x0           34972  1 
snd_ac97_codec        100644  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
pcmcia                 41388  0 
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
joydev                 11328  0 
ipw2200               136496  0 
irda                  202300  0 
parport_pc             37412  1 
wbsd                   18056  0 
mmc_core               28420  1 wbsd
ieee80211              51308  3 ieee80211_crypt_tkip,ieee80211_crypt_ccmp,ipw2200
ieee80211_crypt         7296  4 ieee80211_crypt_wep,ieee80211_crypt_tkip,ieee80211_crypt_ccmp,ieee80211
crc_ccitt               3072  1 irda
snd                    54660  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
parport                37448  3 ppdev,lp,parport_pc
pcspkr                  4224  0 
yenta_socket           27532  1 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40980  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
psmouse                39952  0 
serio_raw               8068  0 
iTCO_wdt               11940  0 
iTCO_vendor_support     4868  1 iTCO_wdt
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
intel_agp              25620  1 
agpgart                35016  2 drm,intel_agp
evdev                  11136  5 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
8139cp                 25088  0 
sr_mod                 17828  0 
cdrom                  37536  1 sr_mod
sd_mod                 30336  3 
ata_piix               17540  2 
8139too                27776  0 
mii                     6528  2 8139cp,8139too
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
ata_generic             8452  0 
libata                125168  2 ata_piix,ata_generic
scsi_mod              147084  5 sbp2,sg,sr_mod,sd_mod,libata
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138632  4 ndiswrapper,ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  2 acpi_cpufreq,thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor



```

---

### Post by Big Bear on 2008-04-04
Any updates on this?  I seem to have the exact same problem as the poster here and this thread just dead ends.  If I had windows I'd use it, I did it in the past and it worked fine but I no longer have that option.

---

### Post by Big Bear on 2008-04-05
I fixed this in a strange way, I dunno why I thought of this but the problem for me started when my battery ran out, upon boot up my wireless was off.  As mentioned before the only way I fixed this in the past was to boot into windows and tell it to turn on from there but I don't have windows anymore so that was not an option.

The idea came to me somehow to turn off the wireless(as it showed as on in that screen but radio off in the command line) from the network icon at the top of the screen, I then pressed Fn+F1 which is my sleep combo on this laptop.  So the computer immediately went to sleep which I then immediately turned back on and then re-enabled the wireless and viola it all of a sudden began working again. 

I don't understand it one bit, maybe it was a fluke but I don't wanna test that theory out.  Hopefully it did work and maybe work for some of you having this problem if you see this post.

---

### Post by PeteZA on 2008-04-05
Big Bear, I don't fully understand what it is that you did. However i am suffering the same annoying problem. At this stage i am thinking that i might just wait for the hardy upgrade and that might fix my wireless. Anybody got any ideas? I dont have windows loaded so thats not an option?

---

### Post by jatorrero on 2008-04-14
> **Big Bear said:**
> I fixed this in a strange way, I dunno why I thought of this but the problem for me started when my battery ran out, upon boot up my wireless was off.  As mentioned before the only way I fixed this in the past was to boot into windows and tell it to turn on from there but I don't have windows anymore so that was not an option.

The idea came to me somehow to turn off the wireless(as it showed as on in that screen but radio off in the command line) from the network icon at the top of the screen, I then pressed Fn+F1 which is my sleep combo on this laptop.  So the computer immediately went to sleep which I then immediately turned back on and then re-enabled the wireless and viola it all of a sudden began working again. 

I don't understand it one bit, maybe it was a fluke but I don't wanna test that theory out.  Hopefully it did work and maybe work for some of you having this problem if you see this post.

Big Bear, I did what you mentioned but my Wifi doesn't work yet. I turn off the radio with the icon on the top right, I pressed Fn + Esc (my key to activate sleep mode), the laptop went to sleep. I turned on the laptop, re-enabled the wireless, but there was no radio yet.

---

