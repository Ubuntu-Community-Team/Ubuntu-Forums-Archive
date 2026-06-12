---
title: "Problem with ethernet connexion"
date: 2008-02-20
forum: Networking &amp; Wireless
---

### Post by pietshah on 2008-02-20
Hi to all and thanx in advance for your help.

I can hardly use other threads, since I dont know well where my problem comes from, except that I "think" that it comes from my Ethernet controler or something like that.

I'm using Ubuntu 7.10, connected on a local Ethernet network which worked perfectly from the first happy day when I switched to Ubuntu.
I tested the network with other computer, it works perfect, but, from a day to the other it stopped to work on my laptop (acer travelmate 2300)

As mentionned in the Ubuntu Help I made in the terminal "**ifconfig eth1**"  (if I've to replace eth1 I dont know by what)
As answer I have: **error in the info search in the interface: material not found**  (sorry for the bad translation, I'm using Ubuntu in french)

What's wrong?

A tip: I kept a Windows session on the same computer, and there also Internet stopped to work.

Thanks a lot for your help !!!

---

### Post by SpaceTeddy on 2008-02-20
please post the output of the following commands to help figure out what your problem ist
> sudo ifconfig
sudo route -n
sudo dmesg
sudo lsmod
cat /etc/network/interfaces

hopefully we will be able to find out what is wrong then :)

---

### Post by pietshah on 2008-02-21
Thanks Teddy.
Well, below the result of these commands. I hope I did it right

sudo ifconfig

> sudo ifconfig

eth0      Lien encap:Ethernet  HWaddr 00:C0:9F:58:60:D1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 b) Octets transmis:0 (0.0 b)
          Interruption:6 

lo        Lien encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:2080 erreurs:0 :0 overruns:0 frame:0
          TX packets:2080 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:60320 (58.9 KB) Octets transmis:60320 (58.9 KB)


sudo route -n

> sudo route -n

Table de routage IP du noyau
Destination     Passerelle      Genmask         Indic Metric Ref    Use Iface



sudo dmesg

> sudo dmesg

[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Dec 18 08:02:57 UTC 2007 (Ubuntu 2.6.22-14.47-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000ce000 - 00000000000d0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001eee0000 (usable)
[    0.000000]  BIOS-e820: 000000001eee0000 - 000000001eeec000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001eeec000 - 000000001ef00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001ef00000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec10000 - 00000000fec20000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff800000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fffffc00 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 494MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 126688) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   126688
[    0.000000]   HighMem    126688 ->   126688
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   126688
[    0.000000] On node 0 totalpages: 126688
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 957 pages used for memmap
[    0.000000]   Normal zone: 121635 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F62E0 checksum 0
[    0.000000] ACPI: RSDP 000F62E0, 0014 (r0 ACER  )
[    0.000000] ACPI: RSDT 1EEE7C68, 0030 (r1 ACER   Kestrel  20020803  LTP        0)
[    0.000000] ACPI: FACP 1EEEBF2C, 0074 (r1 ACER   Kestrel  20020803 PTL        50)
[    0.000000] ACPI: DSDT 1EEE7C98, 4294 (r1 ACER   Kestrel  20020803 MSFT  100000E)
[    0.000000] ACPI: FACS 1EEFCFC0, 0040
[    0.000000] ACPI: HPET 1EEEBFA0, 0038 (r1 ACER   Kestrel  20020803 PTL         0)
[    0.000000] ACPI: BOOT 1EEEBFD8, 0028 (r1 ACER   Kestrel  20020803  LTP        1)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0x0
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec10000)
[    0.000000] Built 1 zonelists.  Total pages: 125699
[    0.000000] Kernel command line: root=UUID=d621713a-5bc8-47cf-80f6-6baf189e6445 ro quiet splash
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffd000 (013ed000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 1498.784 MHz processor.
[  113.312494] Console: colour VGA+ 80x25
[  113.312675] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[  113.312966] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[  113.331857] Memory: 490764k/506752k available (2015k kernel code, 15360k reserved, 916k data, 364k init, 0k highmem)
[  113.331870] virtual kernel memory layout:
[  113.331871]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[  113.331873]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[  113.331874]     vmalloc : 0xdf800000 - 0xff7fe000   ( 511 MB)
[  113.331876]     lowmem  : 0xc0000000 - 0xdeee0000   ( 494 MB)
[  113.331878]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[  113.331879]       .data : 0xc02f7de6 - 0xc03dce84   ( 916 kB)
[  113.331881]       .text : 0xc0100000 - 0xc02f7de6   (2015 kB)
[  113.331885] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[  113.331932] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[  113.411928] Calibrating delay using timer specific routine.. 2999.51 BogoMIPS (lpj=5999025)
[  113.411960] Security Framework v1.0.0 initialized
[  113.411969] SELinux:  Disabled at boot.
[  113.411987] Mount-cache hash table entries: 512
[  113.412137] CPU: After generic identify, caps: a7e9f9bf 00000000 00000000 00000000 00000000 00000000 00000000
[  113.412150] CPU: L1 I cache: 32K, L1 D cache: 32K
[  113.412153] CPU: L2 cache: 512K
[  113.412157] CPU: After all inits, caps: a7e9f9bf 00000000 00000000 00002040 00000000 00000000 00000000
[  113.412167] Compat vDSO mapped to ffffe000.
[  113.412181] Checking 'hlt' instruction... OK.
[  113.428026] SMP alternatives: switching to UP code
[  113.428207] Freeing SMP alternatives: 11k freed
[  113.428514] Early unpacking initramfs... done
[  113.829569] ACPI: Core revision 20070126
[  113.829655] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[  113.831764] ACPI: setting ELCR to 0200 (from 0440)
[  113.856943] CPU0: Intel(R) Celeron(R) M processor         1500MHz stepping 05
[  113.856950] SMP motherboard not detected.
[  113.856954] Local APIC not detected. Using dummy APIC emulation.
[  113.856997] Brought up 1 CPUs
[  113.857136] Booting paravirtualized kernel on bare hardware
[  113.857214] Time: 22:00:20  Date: 01/20/108
[  113.857243] NET: Registered protocol family 16
[  113.857353] EISA bus registered
[  113.857369] ACPI: bus type pci registered
[  113.858611] PCI: PCI BIOS revision 2.10 entry at 0xfd792, last bus=2
[  113.858614] PCI: Using configuration type 1
[  113.858616] Setting up standard PCI resources
[  113.876051] ACPI: EC: Look up EC in DSDT
[  113.876838] ACPI: EC: GPE=0x1d, ports=0x66, 0x62
[  113.878026] ACPI: Interpreter enabled
[  113.878031] ACPI: (supports S0 S3 S4 S5)
[  113.878046] ACPI: Using PIC for interrupt routing
[  113.882259] ACPI: EC: GPE=0x1d, ports=0x66, 0x62
[  113.882310] ACPI: PCI Root Bridge [PCI0] (0000:00)
[  113.882319] PCI: Probing PCI hardware (bus 00)
[  113.882759] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[  113.882764] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
[  113.883093] PCI: Transparent bridge - 0000:00:1e.0
[  113.883165] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[  113.883410] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[  113.885974] ACPI: PCI Interrupt Link [LNKA] (IRQs *6)
[  113.886073] ACPI: PCI Interrupt Link [LNKB] (IRQs *10)
[  113.886168] ACPI: PCI Interrupt Link [LNKC] (IRQs *6)
[  113.886261] ACPI: PCI Interrupt Link [LNKD] (IRQs *6)
[  113.886355] ACPI: PCI Interrupt Link [LNKE] (IRQs *10)
[  113.886455] ACPI: PCI Interrupt Link [LNKF] (IRQs 10) *0, disabled.
[  113.886551] ACPI: PCI Interrupt Link [LNKG] (IRQs 6) *0, disabled.
[  113.886647] ACPI: PCI Interrupt Link [LNKH] (IRQs *10)
[  113.886798] ACPI: Power Resource [PFN0] (off)
[  113.886835] ACPI: Power Resource [PFN1] (off)
[  113.886842] Linux Plug and Play Support v0.97 (c) Adam Belay
[  113.886859] pnp: PnP ACPI init
[  113.886878] ACPI: bus type pnp registered
[  113.888550] pnp: PnP ACPI: found 8 devices
[  113.888553] ACPI: ACPI bus type pnp unregistered
[  113.888558] PnPBIOS: Disabled by ACPI PNP
[  113.888627] PCI: Using ACPI for IRQ routing
[  113.888631] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[  113.893517] NET: Registered protocol family 8
[  113.893520] NET: Registered protocol family 20
[  113.893606] pnp: 00:04: ioport range 0x164e-0x164f has been reserved
[  113.893611] pnp: 00:04: iomem range 0xfec10000-0xfec1ffff could not be reserved
[  113.893616] pnp: 00:04: iomem range 0xff800000-0xffbfffff could not be reserved
[  113.893620] pnp: 00:04: iomem range 0xfff00000-0xffffffff could not be reserved
[  113.893624] pnp: 00:04: iomem range 0x0-0x9ffff could not be reserved
[  113.895783] Time: tsc clocksource has been installed.
[  113.923977] PCI: Error while updating region 0000:02:04.0/2 (e0203000 != c0203000)
[  113.924035] PCI: Error while updating region 0000:02:04.0/1 (e0203800 != c0203800)
[  113.924086] PCI: Bus 3, cardbus bridge: 0000:02:06.0
[  113.924089]   IO window: 00003000-000030ff
[  113.924093]   IO window: 00003400-000034ff
[  113.924098]   PREFETCH window: 30000000-33ffffff
[  113.924102]   MEM window: 38000000-3bffffff
[  113.924106] PCI: Bridge: 0000:00:1e.0
[  113.924110]   IO window: 3000-3fff
[  113.924115]   MEM window: e0200000-e05fffff
[  113.924120]   PREFETCH window: 30000000-35ffffff
[  113.924133] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[  113.924146] PCI: Enabling device 0000:02:06.0 (0104 -> 0107)
[  113.924343] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 10
[  113.924348] PCI: setting IRQ 10 as level-triggered
[  113.924352] ACPI: PCI Interrupt 0000:02:06.0[A] -> Link [LNKE] -> GSI 10 (level, low) -> IRQ 10
[  113.924372] NET: Registered protocol family 2
[  113.963807] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[  113.963857] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[  113.964057] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[  113.964219] TCP: Hash tables configured (established 16384 bind 16384)
[  113.964223] TCP reno registered
[  113.975936] checking if image is initramfs... it is
[  114.427650] Switched to high resolution mode on CPU 0
[  114.755099] Freeing initrd memory: 7109k freed
[  114.755271] Simple Boot Flag at 0x37 set to 0x1
[  114.755554] audit: initializing netlink socket (disabled)
[  114.755572] audit(1203544820.044:1): initialized
[  114.758095] VFS: Disk quotas dquot_6.5.1
[  114.758171] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[  114.758300] io scheduler noop registered
[  114.758304] io scheduler anticipatory registered
[  114.758306] io scheduler deadline registered
[  114.758335] io scheduler cfq registered (default)
[  114.758355] Boot video device is 0000:00:02.0
[  114.758599] isapnp: Scanning for PnP cards...
[  115.112346] isapnp: No Plug & Play device found
[  115.159752] Real Time Clock Driver v1.12ac
[  115.159867] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[  115.161160] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[  115.161166] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[  115.161177] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[  115.161816] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[  115.162094] input: Macintosh mouse button emulation as /class/input/input0
[  115.162181] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOU2] at 0x60,0x64 irq 1,12
[  115.165887] i8042.c: Detected active multiplexing controller, rev 1.1.
[  115.166897] serio: i8042 KBD port at 0x60,0x64 irq 1
[  115.166904] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[  115.166907] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[  115.166910] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[  115.166913] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[  115.167164] mice: PS/2 mouse device common for all mice
[  115.167401] EISA: Probing bus 0 at eisa.0
[  115.167410] Cannot allocate resource for EISA slot 1
[  115.167414] Cannot allocate resource for EISA slot 2
[  115.167417] Cannot allocate resource for EISA slot 3
[  115.167438] EISA: Detected 0 cards.
[  115.167564] TCP cubic registered
[  115.167586] NET: Registered protocol family 1
[  115.167620] Using IPI No-Shortcut mode
[  115.167831]   Magic number: 12:772:47
[  115.168219] Freeing unused kernel memory: 364k freed
[  115.261669] input: AT Translated Set 2 keyboard as /class/input/input1
[  116.414007] AppArmor: AppArmor initialized<5>audit(1203544822.044:2):  type=1505 info="AppArmor initialized" pid=1178
[  116.424733] fuse init (API version 7.8)
[  116.430445] Failure registering capabilities with primary security module.
[  116.447708] ACPI: Transitioning device [FAN0] to D3
[  116.447713] ACPI: Transitioning device [FAN0] to D3
[  116.447717] ACPI: Fan [FAN0] (off)
[  116.447824] ACPI: Transitioning device [FAN1] to D3
[  116.447826] ACPI: Transitioning device [FAN1] to D3
[  116.447830] ACPI: Fan [FAN1] (off)
[  116.454606] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[  116.454613] ACPI: Processor [CPU0] (supports 8 throttling states)
[    3.112000] Marking TSC unstable due to: possible TSC halt in C2.
[    3.116000] Time: acpi_pm clocksource has been installed.
[    3.116000] ACPI: Thermal Zone [THRM] (55 C)
[    3.708000] usbcore: registered new interface driver usbfs
[    3.708000] usbcore: registered new interface driver hub
[    3.708000] usbcore: registered new device driver usb
[    3.708000] USB Universal Host Controller Interface driver v3.0
[    3.708000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 6
[    3.708000] PCI: setting IRQ 6 as level-triggered
[    3.708000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 6 (level, low) -> IRQ 6
[    3.708000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    3.708000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.708000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    3.708000] uhci_hcd 0000:00:1d.0: irq 6, io base 0x00001820
[    3.708000] usb usb1: configuration #1 chosen from 1 choice
[    3.708000] hub 1-0:1.0: USB hub found
[    3.708000] hub 1-0:1.0: 2 ports detected
[    3.784000] SCSI subsystem initialized
[    3.796000] libata version 2.21 loaded.
[    3.812000] hub 1-0:1.0: over-current change on port 1
[    3.812000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 6
[    3.812000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 6 (level, low) -> IRQ 6
[    3.812000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    3.812000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.812000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    3.812000] uhci_hcd 0000:00:1d.1: irq 6, io base 0x00001840
[    3.812000] usb usb2: configuration #1 chosen from 1 choice
[    3.812000] hub 2-0:1.0: USB hub found
[    3.812000] hub 2-0:1.0: 2 ports detected
[    3.916000] hub 1-0:1.0: over-current change on port 2
[    3.916000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 6
[    3.916000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 6 (level, low) -> IRQ 6
[    3.916000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    3.916000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.916000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    3.916000] uhci_hcd 0000:00:1d.2: irq 6, io base 0x00001860
[    3.916000] usb usb3: configuration #1 chosen from 1 choice
[    3.916000] hub 3-0:1.0: USB hub found
[    3.916000] hub 3-0:1.0: 2 ports detected
[    4.020000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 10
[    4.020000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 10 (level, low) -> IRQ 10
[    4.020000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    4.020000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.020000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[    4.020000] ehci_hcd 0000:00:1d.7: debug port 1
[    4.020000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    4.020000] ehci_hcd 0000:00:1d.7: irq 10, io mem 0xe0100000
[    4.024000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.024000] usb usb4: configuration #1 chosen from 1 choice
[    4.024000] hub 4-0:1.0: USB hub found
[    4.024000] hub 4-0:1.0: 6 ports detected
[    4.132000] ata_piix 0000:00:1f.1: version 2.11
[    4.132000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[    4.132000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 6 (level, low) -> IRQ 6
[    4.132000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    4.132000] scsi0 : ata_piix
[    4.132000] scsi1 : ata_piix
[    4.132000] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011810 irq 14
[    4.132000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011818 irq 15
[    4.308000] hub 4-0:1.0: over-current change on port 1
[    4.352000] ata1.00: ATA-8: WDC WD1200BEVE-00WZT0, 01.01A01, max UDMA/100
[    4.352000] ata1.00: 234441648 sectors, multi 16: LBA48 
[    4.368000] ata1.00: configured for UDMA/100
[    4.412000] hub 4-0:1.0: over-current change on port 2
[    4.688000] ata2.00: ATAPI: QSI CD-RW/DVD-ROM SBW242C, UQ81, max UDMA/33
[    4.860000] ata2.00: configured for UDMA/33
[    4.860000] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1200BEVE-0 01.0 PQ: 0 ANSI: 5
[    4.860000] scsi 1:0:0:0: CD-ROM            QSI      CDRW/DVD SBW242C UQ81 PQ: 0 ANSI: 5
[    4.860000] b44.c:v1.01 (Jun 16, 2006)
[    4.860000] ACPI: PCI Interrupt 0000:02:02.0[A] -> Link [LNKD] -> GSI 6 (level, low) -> IRQ 6
[    4.864000] eth0: Broadcom 4400 10/100BaseT Ethernet 00:c0:9f:58:60:d1
[    4.884000] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    4.884000] sd 0:0:0:0: [sda] Write Protect is off
[    4.884000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.884000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.884000] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    4.884000] sd 0:0:0:0: [sda] Write Protect is off
[    4.884000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.884000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.884000]  sda: sda1 sda2 sda3
[    4.940000] usb 4-6: new high speed USB device using ehci_hcd and address 3
[    4.948000] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.956000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.956000] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    4.972000] sr0: scsi3-mmc drive: 1x/24x writer cd/rw xa/form2 cdda tray
[    4.972000] Uniform CD-ROM driver Revision: 3.20
[    4.972000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    5.156000] usb 4-6: configuration #1 chosen from 1 choice
[    5.240000] Attempting manual resume
[    5.240000] swsusp: Resume From Partition 8:2
[    5.240000] PM: Checking swsusp image.
[    5.240000] PM: Resume from disk failed.
[    5.264000] EXT3-fs: INFO: recovery required on readonly filesystem.
[    5.264000] EXT3-fs: write access will be enabled during recovery.
[    5.408000] usb 2-1: new low speed USB device using uhci_hcd and address 2
[    5.588000] usb 2-1: configuration #1 chosen from 1 choice
[    5.592000] usbcore: registered new interface driver libusual
[    5.604000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    5.604000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    5.608000] Initializing USB Mass Storage driver...
[    5.608000] scsi2 : SCSI emulation for USB Mass Storage devices
[    5.608000] usb-storage: device found at 3
[    5.608000] usb-storage: waiting for device to settle before scanning
[    5.608000] usbcore: registered new interface driver usb-storage
[    5.608000] USB Mass Storage support registered.
[    5.632000] usbcore: registered new interface driver hiddev
[    5.644000] input: Microsoft Microsoft Notebook/Mobile Optical Mouse 2.0 as /class/input/input2
[    5.644000] input: USB HID v1.10 Mouse [Microsoft Microsoft Notebook/Mobile Optical Mouse 2.0] on usb-0000:00:1d.1-1
[    5.644000] usbcore: registered new interface driver usbhid
[    5.644000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   10.184000] kjournald starting.  Commit interval 5 seconds
[   10.184000] EXT3-fs: sda3: orphan cleanup on readonly fs
[   10.184000] ext3_orphan_cleanup: deleting unreferenced inode 4718645
[   10.184000] EXT3-fs: sda3: 1 orphan inode deleted
[   10.184000] EXT3-fs: recovery complete.
[   10.188000] EXT3-fs: mounted filesystem with ordered data mode.
[   10.616000] usb-storage: device scan complete
[   10.616000] scsi 2:0:0:0: Direct-Access              USB Flash Memory 1.00 PQ: 0 ANSI: 2
[   10.624000] sd 2:0:0:0: [sdb] 1001472 512-byte hardware sectors (513 MB)
[   10.624000] sd 2:0:0:0: [sdb] Write Protect is off
[   10.624000] sd 2:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[   10.624000] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   10.632000] sd 2:0:0:0: [sdb] 1001472 512-byte hardware sectors (513 MB)
[   10.636000] sd 2:0:0:0: [sdb] Write Protect is off
[   10.636000] sd 2:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[   10.636000] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   10.636000]  sdb: sdb1
[   10.636000] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   10.636000] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   18.956000] Linux agpgart interface v0.102 (c) Dave Jones
[   18.964000] agpgart: Detected an Intel 855GM Chipset.
[   18.964000] agpgart: Detected 16252K stolen memory.
[   18.976000] agpgart: AGP aperture is 128M @ 0xe8000000
[   19.552000] intel_rng: FWH not detected
[   19.760000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   19.944000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   20.304000] iTCO_vendor_support: vendor-support=0
[   20.320000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   20.320000] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x1060)
[   20.320000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   20.632000] Yenta: CardBus bridge found at 0000:02:06.0 [1025:0064]
[   20.632000] Yenta: Enabling burst memory read transactions
[   20.632000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   20.632000] Yenta: Routing CardBus interrupts to PCI
[   20.632000] Yenta TI: socket 0000:02:06.0, mfunc 0x01a21b22, devctl 0x64
[   20.888000] Yenta: ISA IRQ mask 0x08b8, PCI irq 10
[   20.888000] Socket status: 30000006
[   20.888000] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   20.888000] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[   20.888000] cs: IO port probe 0x3000-0x3fff: clean.
[   20.888000] pcmcia: parent PCI bridge Memory window: 0xe0200000 - 0xe05fffff
[   20.888000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x35ffffff
[   20.988000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   20.988000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   21.064000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x126eb1, caps: 0xa04713/0x4000
[   21.104000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   21.308000] cs: IO port probe 0x100-0x3af: clean.
[   21.308000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   21.308000] cs: IO port probe 0x820-0x8ff: clean.
[   21.308000] cs: IO port probe 0xc00-0xcf7: clean.
[   21.308000] cs: IO port probe 0xa00-0xaff: clean.
[   21.312000] intel8x0_measure_ac97_clock: measured 54635 usecs
[   21.312000] intel8x0: clocking to 48000
[   22.028000] lp: driver loaded but no devices found
[   22.076000] Adding 1951888k swap on /dev/sda2.  Priority:-1 extents:1 across:1951888k
[   22.348000] EXT3 FS on sda3, internal journal
[   23.576000] No dock devices found.
[   23.636000] ACPI: Smart Battery System [SBS0]: AC Adapter [AC0] (on-line)
[   24.336000] ACPI: Smart Battery System [SBS0]: Battery Slot [BAT0] (battery present)
[   24.364000] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[   24.548000] input: Power Button (FF) as /class/input/input4
[   24.552000] ACPI: Power Button (FF) [PWRF]
[   24.612000] input: Lid Switch as /class/input/input5
[   24.620000] ACPI: Lid Switch [LID]
[   24.676000] input: Sleep Button (CM) as /class/input/input6
[   24.676000] ACPI: Sleep Button (CM) [SLPB]
[   24.964000] ACPI Exception (processor_perflib-0234): AE_NOT_FOUND, Evaluating _PSS [20070126]
[   26.220000] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   26.220000] PCI: Setting latency timer of device 0000:00:1f.6 to 64
[   26.576000] MC'97 0 converters and GPIO not ready (0x1)
[   28.408000] mtrr: no more MTRRs available
[   28.408000] mtrr: no more MTRRs available
[   28.728000] ppdev: user-space parallel port driver
[   29.096000] audit(1203561048.712:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4847 profile="/usr/sbin/cupsd"
[   29.172000] apm: BIOS not found.
[   29.424000] Failure registering capabilities with primary security module.
[   29.608000] Bluetooth: Core ver 2.11
[   29.608000] NET: Registered protocol family 31
[   29.608000] Bluetooth: HCI device and connection manager initialized
[   29.608000] Bluetooth: HCI socket layer initialized
[   29.632000] Bluetooth: L2CAP ver 2.8
[   29.632000] Bluetooth: L2CAP socket layer initialized
[   29.688000] Bluetooth: RFCOMM socket layer initialized
[   29.688000] Bluetooth: RFCOMM TTY layer initialized
[   29.688000] Bluetooth: RFCOMM ver 1.8
[   80.836000] NET: Registered protocol family 10
[   80.836000] lo: Disabled Privacy Extensions
[   80.836000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1856.900000] usb 4-6: USB disconnect, address 3
[ 2128.308000] usb 2-1: USB disconnect, address 2
[ 2130.072000] Clocksource tsc unstable (delta = -452545350 ns)



sudo lsmod

> sudo lsmod

Module                  Size  Used by
ipv6                  273892  8 
nls_iso8859_1           5120  0 
nls_cp437               6784  0 
vfat                   14080  0 
fat                    54300  1 vfat
binfmt_misc            12936  1 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
snd_atiixp_modem       17160  0 
snd_via82xx_modem      16264  0 
snd_intel8x0m          18572  5 
cpufreq_ondemand        9612  0 
cpufreq_powersave       2688  0 
cpufreq_userspace       5280  0 
cpufreq_conservative     8072  0 
cpufreq_stats           7232  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
button                  8976  0 
battery                11012  0 
container               5504  0 
ac                      6148  0 
video                  18060  0 
sbs                    19592  0 
dock                   10656  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
joydev                 11328  0 
pcmcia                 41388  0 
snd_intel8x0           34972  1 
snd_ac97_codec        100644  4 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  8 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
yenta_socket           27532  1 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40980  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                39952  0 
serio_raw               8068  0 
iTCO_wdt               11940  0 
iTCO_vendor_support     4868  1 iTCO_wdt
snd                    54660  23 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  5 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_pcm
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
intel_agp              25620  1 
agpgart                35016  1 intel_agp
evdev                  11136  5 
usbhid                 29536  0 
hid                    28928  1 usbhid
usb_storage            73024  0 
ide_core              116804  1 usb_storage
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
libusual               18448  1 usb_storage
sg                     36764  0 
sr_mod                 17828  0 
cdrom                  37536  1 sr_mod
sd_mod                 30336  4 
ata_piix               17540  3 
b44                    28300  0 
mii                     6528  1 b44
ata_generic             8452  0 
libata                125168  2 ata_piix,ata_generic
scsi_mod              147084  5 usb_storage,sg,sr_mod,sd_mod,libata
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138632  6 usbhid,usb_storage,libusual,ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  3 
apparmor               40728  0 
commoncap               8320  1 apparmor



cat /etc/network/interfaces

> cat /etc/network/interfaces

auto lo
iface lo inet loopback

auto eth0
#iface eth0 inet dhcp

auto eth1
#iface eth1 inet dhcp

auto eth2
#iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

auto wlan0
#iface wlan0 inet dhcp


---

### Post by SpaceTeddy on 2008-02-21
ok, as far as i can see, you have one network card (eth0) displayed via the ifconfig command. dmesg says that there is no media connected to it,
also, there is no ip address assigned to eth0, which explains the empty routing table.

since you said you have an acer travelmate 2300, i looked at the specs and saw that you have two integrated network cards... yet only the Broadcom Network card (i assume it is the cable network because of the loaded driver) seems to work. your wireless card does not even load a driver, altough the card itself (intel pro 2200BG) is supported by any generic linux kernel. 
If that does not help you at all, here is the essence:
Your wifi network card is either turned off in the bios or broken (i don't assume a module problem since windows has the same problem. it should be something more basic than missing drivers. besidesm the wireless card is definetly supported). However, if you use a cable it should work. if you would be so kind as to confirm that :)

---

### Post by pietshah on 2008-02-21
Indeed, the wireless connexion doesn't work but it's not the problem since I dont have wifi connexion but a Ethernet one.
I used to use it without any problem (cable connected on the Broadcom card, as you noticed it) until that moment when it stopped to work.

But I think I've made a stupid thing... The test I've done were without the Ethernet cable connected (since anyway it doesnt work) but I wonder it avoids you to see what's the problem with that connexion!

Well, I'll proceed it again with the cable in, and come back here (Internet cafe) to give you the results of the new test.

Would it be that the Broadcom card is out of order? I thought that no, since Windows shows that it works fine (even if no connexion, the same)
Reading some other threads, I learn about a Ethernet Controler, but I've no idea what it is.


Greetings and thanks a lot for your help!

---

### Post by pietshah on 2008-02-21
Here are the results of the new tests (the same with the Ethernet cable connected)


> sudo ifconfig


eth0      Lien encap:Ethernet  HWaddr 00:C0:9F:58:60:D1  
          adr inet6: fe80::2c0:9fff:fe58:60d1/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:85 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 b) Octets transmis:8585 (8.3 KB)
          Interruption:6 

eth0:avah Lien encap:Ethernet  HWaddr 00:C0:9F:58:60:D1  
          inet adr:169.254.8.156  Bcast:169.254.255.255  Masque:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interruption:6 

lo        Lien encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:3717 erreurs:0 :0 overruns:0 frame:0
          TX packets:3717 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:109491 (106.9 KB) Octets transmis:109491 (106.9 KB)



> 

sudo route -n

Table de routage IP du noyau
Destination     Passerelle      Genmask         Indic Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth0




> 


 sudo dmesg

[    0.000000]  BIOS-e820: 00000000fffffc00 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 494MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 126688) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   126688
[    0.000000]   HighMem    126688 ->   126688
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   126688
[    0.000000] On node 0 totalpages: 126688
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 957 pages used for memmap
[    0.000000]   Normal zone: 121635 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F62E0 checksum 0
[    0.000000] ACPI: RSDP 000F62E0, 0014 (r0 ACER  )
[    0.000000] ACPI: RSDT 1EEE7C68, 0030 (r1 ACER   Kestrel  20020803  LTP        0)
[    0.000000] ACPI: FACP 1EEEBF2C, 0074 (r1 ACER   Kestrel  20020803 PTL        50)
[    0.000000] ACPI: DSDT 1EEE7C98, 4294 (r1 ACER   Kestrel  20020803 MSFT  100000E)
[    0.000000] ACPI: FACS 1EEFCFC0, 0040
[    0.000000] ACPI: HPET 1EEEBFA0, 0038 (r1 ACER   Kestrel  20020803 PTL         0)
[    0.000000] ACPI: BOOT 1EEEBFD8, 0028 (r1 ACER   Kestrel  20020803  LTP        1)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0x0
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec10000)
[    0.000000] Built 1 zonelists.  Total pages: 125699
[    0.000000] Kernel command line: root=UUID=d621713a-5bc8-47cf-80f6-6baf189e6445 ro quiet splash
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffd000 (013ed000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 1498.784 MHz processor.
[  113.312494] Console: colour VGA+ 80x25
[  113.312675] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[  113.312966] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[  113.331857] Memory: 490764k/506752k available (2015k kernel code, 15360k reserved, 916k data, 364k init, 0k highmem)
[  113.331870] virtual kernel memory layout:
[  113.331871]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[  113.331873]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[  113.331874]     vmalloc : 0xdf800000 - 0xff7fe000   ( 511 MB)
[  113.331876]     lowmem  : 0xc0000000 - 0xdeee0000   ( 494 MB)
[  113.331878]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[  113.331879]       .data : 0xc02f7de6 - 0xc03dce84   ( 916 kB)
[  113.331881]       .text : 0xc0100000 - 0xc02f7de6   (2015 kB)
[  113.331885] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[  113.331932] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[  113.411928] Calibrating delay using timer specific routine.. 2999.51 BogoMIPS (lpj=5999025)
[  113.411960] Security Framework v1.0.0 initialized
[  113.411969] SELinux:  Disabled at boot.
[  113.411987] Mount-cache hash table entries: 512
[  113.412137] CPU: After generic identify, caps: a7e9f9bf 00000000 00000000 00000000 00000000 00000000 00000000
[  113.412150] CPU: L1 I cache: 32K, L1 D cache: 32K
[  113.412153] CPU: L2 cache: 512K
[  113.412157] CPU: After all inits, caps: a7e9f9bf 00000000 00000000 00002040 00000000 00000000 00000000
[  113.412167] Compat vDSO mapped to ffffe000.
[  113.412181] Checking 'hlt' instruction... OK.
[  113.428026] SMP alternatives: switching to UP code
[  113.428207] Freeing SMP alternatives: 11k freed
[  113.428514] Early unpacking initramfs... done
[  113.829569] ACPI: Core revision 20070126
[  113.829655] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[  113.831764] ACPI: setting ELCR to 0200 (from 0440)
[  113.856943] CPU0: Intel(R) Celeron(R) M processor         1500MHz stepping 05
[  113.856950] SMP motherboard not detected.
[  113.856954] Local APIC not detected. Using dummy APIC emulation.
[  113.856997] Brought up 1 CPUs
[  113.857136] Booting paravirtualized kernel on bare hardware
[  113.857214] Time: 22:00:20  Date: 01/20/108
[  113.857243] NET: Registered protocol family 16
[  113.857353] EISA bus registered
[  113.857369] ACPI: bus type pci registered
[  113.858611] PCI: PCI BIOS revision 2.10 entry at 0xfd792, last bus=2
[  113.858614] PCI: Using configuration type 1
[  113.858616] Setting up standard PCI resources
[  113.876051] ACPI: EC: Look up EC in DSDT
[  113.876838] ACPI: EC: GPE=0x1d, ports=0x66, 0x62
[  113.878026] ACPI: Interpreter enabled
[  113.878031] ACPI: (supports S0 S3 S4 S5)
[  113.878046] ACPI: Using PIC for interrupt routing
[  113.882259] ACPI: EC: GPE=0x1d, ports=0x66, 0x62
[  113.882310] ACPI: PCI Root Bridge [PCI0] (0000:00)
[  113.882319] PCI: Probing PCI hardware (bus 00)
[  113.882759] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[  113.882764] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
[  113.883093] PCI: Transparent bridge - 0000:00:1e.0
[  113.883165] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[  113.883410] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[  113.885974] ACPI: PCI Interrupt Link [LNKA] (IRQs *6)
[  113.886073] ACPI: PCI Interrupt Link [LNKB] (IRQs *10)
[  113.886168] ACPI: PCI Interrupt Link [LNKC] (IRQs *6)
[  113.886261] ACPI: PCI Interrupt Link [LNKD] (IRQs *6)
[  113.886355] ACPI: PCI Interrupt Link [LNKE] (IRQs *10)
[  113.886455] ACPI: PCI Interrupt Link [LNKF] (IRQs 10) *0, disabled.
[  113.886551] ACPI: PCI Interrupt Link [LNKG] (IRQs 6) *0, disabled.
[  113.886647] ACPI: PCI Interrupt Link [LNKH] (IRQs *10)
[  113.886798] ACPI: Power Resource [PFN0] (off)
[  113.886835] ACPI: Power Resource [PFN1] (off)
[  113.886842] Linux Plug and Play Support v0.97 (c) Adam Belay
[  113.886859] pnp: PnP ACPI init
[  113.886878] ACPI: bus type pnp registered
[  113.888550] pnp: PnP ACPI: found 8 devices
[  113.888553] ACPI: ACPI bus type pnp unregistered
[  113.888558] PnPBIOS: Disabled by ACPI PNP
[  113.888627] PCI: Using ACPI for IRQ routing
[  113.888631] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[  113.893517] NET: Registered protocol family 8
[  113.893520] NET: Registered protocol family 20
[  113.893606] pnp: 00:04: ioport range 0x164e-0x164f has been reserved
[  113.893611] pnp: 00:04: iomem range 0xfec10000-0xfec1ffff could not be reserved
[  113.893616] pnp: 00:04: iomem range 0xff800000-0xffbfffff could not be reserved
[  113.893620] pnp: 00:04: iomem range 0xfff00000-0xffffffff could not be reserved
[  113.893624] pnp: 00:04: iomem range 0x0-0x9ffff could not be reserved
[  113.895783] Time: tsc clocksource has been installed.
[  113.923977] PCI: Error while updating region 0000:02:04.0/2 (e0203000 != c0203000)
[  113.924035] PCI: Error while updating region 0000:02:04.0/1 (e0203800 != c0203800)
[  113.924086] PCI: Bus 3, cardbus bridge: 0000:02:06.0
[  113.924089]   IO window: 00003000-000030ff
[  113.924093]   IO window: 00003400-000034ff
[  113.924098]   PREFETCH window: 30000000-33ffffff
[  113.924102]   MEM window: 38000000-3bffffff
[  113.924106] PCI: Bridge: 0000:00:1e.0
[  113.924110]   IO window: 3000-3fff
[  113.924115]   MEM window: e0200000-e05fffff
[  113.924120]   PREFETCH window: 30000000-35ffffff
[  113.924133] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[  113.924146] PCI: Enabling device 0000:02:06.0 (0104 -> 0107)
[  113.924343] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 10
[  113.924348] PCI: setting IRQ 10 as level-triggered
[  113.924352] ACPI: PCI Interrupt 0000:02:06.0[A] -> Link [LNKE] -> GSI 10 (level, low) -> IRQ 10
[  113.924372] NET: Registered protocol family 2
[  113.963807] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[  113.963857] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[  113.964057] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[  113.964219] TCP: Hash tables configured (established 16384 bind 16384)
[  113.964223] TCP reno registered
[  113.975936] checking if image is initramfs... it is
[  114.427650] Switched to high resolution mode on CPU 0
[  114.755099] Freeing initrd memory: 7109k freed
[  114.755271] Simple Boot Flag at 0x37 set to 0x1
[  114.755554] audit: initializing netlink socket (disabled)
[  114.755572] audit(1203544820.044:1): initialized
[  114.758095] VFS: Disk quotas dquot_6.5.1
[  114.758171] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[  114.758300] io scheduler noop registered
[  114.758304] io scheduler anticipatory registered
[  114.758306] io scheduler deadline registered
[  114.758335] io scheduler cfq registered (default)
[  114.758355] Boot video device is 0000:00:02.0
[  114.758599] isapnp: Scanning for PnP cards...
[  115.112346] isapnp: No Plug & Play device found
[  115.159752] Real Time Clock Driver v1.12ac
[  115.159867] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[  115.161160] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[  115.161166] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[  115.161177] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[  115.161816] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[  115.162094] input: Macintosh mouse button emulation as /class/input/input0
[  115.162181] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOU2] at 0x60,0x64 irq 1,12
[  115.165887] i8042.c: Detected active multiplexing controller, rev 1.1.
[  115.166897] serio: i8042 KBD port at 0x60,0x64 irq 1
[  115.166904] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[  115.166907] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[  115.166910] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[  115.166913] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[  115.167164] mice: PS/2 mouse device common for all mice
[  115.167401] EISA: Probing bus 0 at eisa.0
[  115.167410] Cannot allocate resource for EISA slot 1
[  115.167414] Cannot allocate resource for EISA slot 2
[  115.167417] Cannot allocate resource for EISA slot 3
[  115.167438] EISA: Detected 0 cards.
[  115.167564] TCP cubic registered
[  115.167586] NET: Registered protocol family 1
[  115.167620] Using IPI No-Shortcut mode
[  115.167831]   Magic number: 12:772:47
[  115.168219] Freeing unused kernel memory: 364k freed
[  115.261669] input: AT Translated Set 2 keyboard as /class/input/input1
[  116.414007] AppArmor: AppArmor initialized<5>audit(1203544822.044:2):  type=1505 info="AppArmor initialized" pid=1178
[  116.424733] fuse init (API version 7.8)
[  116.430445] Failure registering capabilities with primary security module.
[  116.447708] ACPI: Transitioning device [FAN0] to D3
[  116.447713] ACPI: Transitioning device [FAN0] to D3
[  116.447717] ACPI: Fan [FAN0] (off)
[  116.447824] ACPI: Transitioning device [FAN1] to D3
[  116.447826] ACPI: Transitioning device [FAN1] to D3
[  116.447830] ACPI: Fan [FAN1] (off)
[  116.454606] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[  116.454613] ACPI: Processor [CPU0] (supports 8 throttling states)
[    3.112000] Marking TSC unstable due to: possible TSC halt in C2.
[    3.116000] Time: acpi_pm clocksource has been installed.
[    3.116000] ACPI: Thermal Zone [THRM] (55 C)
[    3.708000] usbcore: registered new interface driver usbfs
[    3.708000] usbcore: registered new interface driver hub
[    3.708000] usbcore: registered new device driver usb
[    3.708000] USB Universal Host Controller Interface driver v3.0
[    3.708000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 6
[    3.708000] PCI: setting IRQ 6 as level-triggered
[    3.708000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 6 (level, low) -> IRQ 6
[    3.708000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    3.708000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.708000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    3.708000] uhci_hcd 0000:00:1d.0: irq 6, io base 0x00001820
[    3.708000] usb usb1: configuration #1 chosen from 1 choice
[    3.708000] hub 1-0:1.0: USB hub found
[    3.708000] hub 1-0:1.0: 2 ports detected
[    3.784000] SCSI subsystem initialized
[    3.796000] libata version 2.21 loaded.
[    3.812000] hub 1-0:1.0: over-current change on port 1
[    3.812000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 6
[    3.812000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 6 (level, low) -> IRQ 6
[    3.812000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    3.812000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.812000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    3.812000] uhci_hcd 0000:00:1d.1: irq 6, io base 0x00001840
[    3.812000] usb usb2: configuration #1 chosen from 1 choice
[    3.812000] hub 2-0:1.0: USB hub found
[    3.812000] hub 2-0:1.0: 2 ports detected
[    3.916000] hub 1-0:1.0: over-current change on port 2
[    3.916000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 6
[    3.916000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 6 (level, low) -> IRQ 6
[    3.916000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    3.916000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.916000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    3.916000] uhci_hcd 0000:00:1d.2: irq 6, io base 0x00001860
[    3.916000] usb usb3: configuration #1 chosen from 1 choice
[    3.916000] hub 3-0:1.0: USB hub found
[    3.916000] hub 3-0:1.0: 2 ports detected
[    4.020000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 10
[    4.020000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 10 (level, low) -> IRQ 10
[    4.020000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    4.020000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.020000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[    4.020000] ehci_hcd 0000:00:1d.7: debug port 1
[    4.020000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    4.020000] ehci_hcd 0000:00:1d.7: irq 10, io mem 0xe0100000
[    4.024000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.024000] usb usb4: configuration #1 chosen from 1 choice
[    4.024000] hub 4-0:1.0: USB hub found
[    4.024000] hub 4-0:1.0: 6 ports detected
[    4.132000] ata_piix 0000:00:1f.1: version 2.11
[    4.132000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[    4.132000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 6 (level, low) -> IRQ 6
[    4.132000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    4.132000] scsi0 : ata_piix
[    4.132000] scsi1 : ata_piix
[    4.132000] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011810 irq 14
[    4.132000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011818 irq 15
[    4.308000] hub 4-0:1.0: over-current change on port 1
[    4.352000] ata1.00: ATA-8: WDC WD1200BEVE-00WZT0, 01.01A01, max UDMA/100
[    4.352000] ata1.00: 234441648 sectors, multi 16: LBA48 
[    4.368000] ata1.00: configured for UDMA/100
[    4.412000] hub 4-0:1.0: over-current change on port 2
[    4.688000] ata2.00: ATAPI: QSI CD-RW/DVD-ROM SBW242C, UQ81, max UDMA/33
[    4.860000] ata2.00: configured for UDMA/33
[    4.860000] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1200BEVE-0 01.0 PQ: 0 ANSI: 5
[    4.860000] scsi 1:0:0:0: CD-ROM            QSI      CDRW/DVD SBW242C UQ81 PQ: 0 ANSI: 5
[    4.860000] b44.c:v1.01 (Jun 16, 2006)
[    4.860000] ACPI: PCI Interrupt 0000:02:02.0[A] -> Link [LNKD] -> GSI 6 (level, low) -> IRQ 6
[    4.864000] eth0: Broadcom 4400 10/100BaseT Ethernet 00:c0:9f:58:60:d1
[    4.884000] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    4.884000] sd 0:0:0:0: [sda] Write Protect is off
[    4.884000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.884000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.884000] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    4.884000] sd 0:0:0:0: [sda] Write Protect is off
[    4.884000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.884000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.884000]  sda: sda1 sda2 sda3
[    4.940000] usb 4-6: new high speed USB device using ehci_hcd and address 3
[    4.948000] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.956000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.956000] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    4.972000] sr0: scsi3-mmc drive: 1x/24x writer cd/rw xa/form2 cdda tray
[    4.972000] Uniform CD-ROM driver Revision: 3.20
[    4.972000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    5.156000] usb 4-6: configuration #1 chosen from 1 choice
[    5.240000] Attempting manual resume
[    5.240000] swsusp: Resume From Partition 8:2
[    5.240000] PM: Checking swsusp image.
[    5.240000] PM: Resume from disk failed.
[    5.264000] EXT3-fs: INFO: recovery required on readonly filesystem.
[    5.264000] EXT3-fs: write access will be enabled during recovery.
[    5.408000] usb 2-1: new low speed USB device using uhci_hcd and address 2
[    5.588000] usb 2-1: configuration #1 chosen from 1 choice
[    5.592000] usbcore: registered new interface driver libusual
[    5.604000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    5.604000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    5.608000] Initializing USB Mass Storage driver...
[    5.608000] scsi2 : SCSI emulation for USB Mass Storage devices
[    5.608000] usb-storage: device found at 3
[    5.608000] usb-storage: waiting for device to settle before scanning
[    5.608000] usbcore: registered new interface driver usb-storage
[    5.608000] USB Mass Storage support registered.
[    5.632000] usbcore: registered new interface driver hiddev
[    5.644000] input: Microsoft Microsoft Notebook/Mobile Optical Mouse 2.0 as /class/input/input2
[    5.644000] input: USB HID v1.10 Mouse [Microsoft Microsoft Notebook/Mobile Optical Mouse 2.0] on usb-0000:00:1d.1-1
[    5.644000] usbcore: registered new interface driver usbhid
[    5.644000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   10.184000] kjournald starting.  Commit interval 5 seconds
[   10.184000] EXT3-fs: sda3: orphan cleanup on readonly fs
[   10.184000] ext3_orphan_cleanup: deleting unreferenced inode 4718645
[   10.184000] EXT3-fs: sda3: 1 orphan inode deleted
[   10.184000] EXT3-fs: recovery complete.
[   10.188000] EXT3-fs: mounted filesystem with ordered data mode.
[   10.616000] usb-storage: device scan complete
[   10.616000] scsi 2:0:0:0: Direct-Access              USB Flash Memory 1.00 PQ: 0 ANSI: 2
[   10.624000] sd 2:0:0:0: [sdb] 1001472 512-byte hardware sectors (513 MB)
[   10.624000] sd 2:0:0:0: [sdb] Write Protect is off
[   10.624000] sd 2:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[   10.624000] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   10.632000] sd 2:0:0:0: [sdb] 1001472 512-byte hardware sectors (513 MB)
[   10.636000] sd 2:0:0:0: [sdb] Write Protect is off
[   10.636000] sd 2:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[   10.636000] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   10.636000]  sdb: sdb1
[   10.636000] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   10.636000] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   18.956000] Linux agpgart interface v0.102 (c) Dave Jones
[   18.964000] agpgart: Detected an Intel 855GM Chipset.
[   18.964000] agpgart: Detected 16252K stolen memory.
[   18.976000] agpgart: AGP aperture is 128M @ 0xe8000000
[   19.552000] intel_rng: FWH not detected
[   19.760000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   19.944000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   20.304000] iTCO_vendor_support: vendor-support=0
[   20.320000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   20.320000] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x1060)
[   20.320000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   20.632000] Yenta: CardBus bridge found at 0000:02:06.0 [1025:0064]
[   20.632000] Yenta: Enabling burst memory read transactions
[   20.632000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   20.632000] Yenta: Routing CardBus interrupts to PCI
[   20.632000] Yenta TI: socket 0000:02:06.0, mfunc 0x01a21b22, devctl 0x64
[   20.888000] Yenta: ISA IRQ mask 0x08b8, PCI irq 10
[   20.888000] Socket status: 30000006
[   20.888000] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   20.888000] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[   20.888000] cs: IO port probe 0x3000-0x3fff: clean.
[   20.888000] pcmcia: parent PCI bridge Memory window: 0xe0200000 - 0xe05fffff
[   20.888000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x35ffffff
[   20.988000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   20.988000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   21.064000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x126eb1, caps: 0xa04713/0x4000
[   21.104000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   21.308000] cs: IO port probe 0x100-0x3af: clean.
[   21.308000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   21.308000] cs: IO port probe 0x820-0x8ff: clean.
[   21.308000] cs: IO port probe 0xc00-0xcf7: clean.
[   21.308000] cs: IO port probe 0xa00-0xaff: clean.
[   21.312000] intel8x0_measure_ac97_clock: measured 54635 usecs
[   21.312000] intel8x0: clocking to 48000
[   22.028000] lp: driver loaded but no devices found
[   22.076000] Adding 1951888k swap on /dev/sda2.  Priority:-1 extents:1 across:1951888k
[   22.348000] EXT3 FS on sda3, internal journal
[   23.576000] No dock devices found.
[   23.636000] ACPI: Smart Battery System [SBS0]: AC Adapter [AC0] (on-line)
[   24.336000] ACPI: Smart Battery System [SBS0]: Battery Slot [BAT0] (battery present)
[   24.364000] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[   24.548000] input: Power Button (FF) as /class/input/input4
[   24.552000] ACPI: Power Button (FF) [PWRF]
[   24.612000] input: Lid Switch as /class/input/input5
[   24.620000] ACPI: Lid Switch [LID]
[   24.676000] input: Sleep Button (CM) as /class/input/input6
[   24.676000] ACPI: Sleep Button (CM) [SLPB]
[   24.964000] ACPI Exception (processor_perflib-0234): AE_NOT_FOUND, Evaluating _PSS [20070126]
[   26.220000] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   26.220000] PCI: Setting latency timer of device 0000:00:1f.6 to 64
[   26.576000] MC'97 0 converters and GPIO not ready (0x1)
[   28.408000] mtrr: no more MTRRs available
[   28.408000] mtrr: no more MTRRs available
[   28.728000] ppdev: user-space parallel port driver
[   29.096000] audit(1203561048.712:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4847 profile="/usr/sbin/cupsd"
[   29.172000] apm: BIOS not found.
[   29.424000] Failure registering capabilities with primary security module.
[   29.608000] Bluetooth: Core ver 2.11
[   29.608000] NET: Registered protocol family 31
[   29.608000] Bluetooth: HCI device and connection manager initialized
[   29.608000] Bluetooth: HCI socket layer initialized
[   29.632000] Bluetooth: L2CAP ver 2.8
[   29.632000] Bluetooth: L2CAP socket layer initialized
[   29.688000] Bluetooth: RFCOMM socket layer initialized
[   29.688000] Bluetooth: RFCOMM TTY layer initialized
[   29.688000] Bluetooth: RFCOMM ver 1.8
[   80.836000] NET: Registered protocol family 10
[   80.836000] lo: Disabled Privacy Extensions
[   80.836000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1856.900000] usb 4-6: USB disconnect, address 3
[ 2128.308000] usb 2-1: USB disconnect, address 2
[ 2130.072000] Clocksource tsc unstable (delta = -452545350 ns)
[47065.424000] usb 4-6: new high speed USB device using ehci_hcd and address 4
[47065.556000] usb 4-6: configuration #1 chosen from 1 choice
[47065.560000] scsi3 : SCSI emulation for USB Mass Storage devices
[47065.560000] usb-storage: device found at 4
[47065.560000] usb-storage: waiting for device to settle before scanning
[47070.560000] usb-storage: device scan complete
[47070.560000] scsi 3:0:0:0: Direct-Access              USB Flash Memory 5.00 PQ: 0 ANSI: 0 CCS
[47071.140000] sd 3:0:0:0: [sdb] 2013184 512-byte hardware sectors (1031 MB)
[47071.140000] sd 3:0:0:0: [sdb] Write Protect is off
[47071.140000] sd 3:0:0:0: [sdb] Mode Sense: 23 00 00 00
[47071.140000] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[47071.144000] sd 3:0:0:0: [sdb] 2013184 512-byte hardware sectors (1031 MB)
[47071.144000] sd 3:0:0:0: [sdb] Write Protect is off
[47071.144000] sd 3:0:0:0: [sdb] Mode Sense: 23 00 00 00
[47071.144000] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[47071.144000]  sdb: sdb1
[47071.144000] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[47071.144000] sd 3:0:0:0: Attached scsi generic sg2 type 0
[47110.200000] usb 4-6: USB disconnect, address 4
[51126.556000] hub 4-0:1.0: over-current change on port 2
[51126.760000] hub 1-0:1.0: over-current change on port 2
[87810.516000] b44: eth0: Link is up at 100 Mbps, full duplex.
[87810.516000] b44: eth0: Flow control is off for TX and off for RX.
[87810.516000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[87813.176000] NET: Registered protocol family 17
[87814.016000] usb 4-6: new high speed USB device using ehci_hcd and address 5
[87814.152000] usb 4-6: configuration #1 chosen from 1 choice
[87814.152000] scsi4 : SCSI emulation for USB Mass Storage devices
[87814.152000] usb-storage: device found at 5
[87814.152000] usb-storage: waiting for device to settle before scanning
[87819.152000] usb-storage: device scan complete
[87819.152000] scsi 4:0:0:0: Direct-Access              USB Flash Memory 5.00 PQ: 0 ANSI: 0 CCS
[87819.736000] sd 4:0:0:0: [sdb] 2013184 512-byte hardware sectors (1031 MB)
[87819.736000] sd 4:0:0:0: [sdb] Write Protect is off
[87819.736000] sd 4:0:0:0: [sdb] Mode Sense: 23 00 00 00
[87819.736000] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[87819.740000] sd 4:0:0:0: [sdb] 2013184 512-byte hardware sectors (1031 MB)
[87819.740000] sd 4:0:0:0: [sdb] Write Protect is off
[87819.740000] sd 4:0:0:0: [sdb] Mode Sense: 23 00 00 00
[87819.740000] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[87819.740000]  sdb: sdb1
[87819.740000] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[87819.740000] sd 4:0:0:0: Attached scsi generic sg2 type 0
[87821.404000] eth0: no IPv6 routers present





> 


sudo lsmod

Module                  Size  Used by
af_packet              24840  2 
ipv6                  273892  8 
nls_iso8859_1           5120  1 
nls_cp437               6784  1 
vfat                   14080  1 
fat                    54300  1 vfat
binfmt_misc            12936  1 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
snd_atiixp_modem       17160  0 
snd_via82xx_modem      16264  0 
snd_intel8x0m          18572  5 
cpufreq_ondemand        9612  0 
cpufreq_powersave       2688  0 
cpufreq_userspace       5280  0 
cpufreq_conservative     8072  0 
cpufreq_stats           7232  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
button                  8976  0 
battery                11012  0 
container               5504  0 
ac                      6148  0 
video                  18060  0 
sbs                    19592  0 
dock                   10656  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
joydev                 11328  0 
pcmcia                 41388  0 
snd_intel8x0           34972  1 
snd_ac97_codec        100644  4 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  8 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
yenta_socket           27532  1 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40980  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                39952  0 
serio_raw               8068  0 
iTCO_wdt               11940  0 
iTCO_vendor_support     4868  1 iTCO_wdt
snd                    54660  23 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  5 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_pcm
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
intel_agp              25620  1 
agpgart                35016  1 intel_agp
evdev                  11136  5 
usbhid                 29536  0 
hid                    28928  1 usbhid
usb_storage            73024  1 
ide_core              116804  1 usb_storage
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
libusual               18448  1 usb_storage
sg                     36764  0 
sr_mod                 17828  0 
cdrom                  37536  1 sr_mod
sd_mod                 30336  6 
ata_piix               17540  3 
b44                    28300  0 
mii                     6528  1 b44
ata_generic             8452  0 
libata                125168  2 ata_piix,ata_generic
scsi_mod              147084  5 usb_storage,sg,sr_mod,sd_mod,libata
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138632  6 usbhid,usb_storage,libusual,ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  3 
apparmor               40728  0 
commoncap               8320  1 apparmor




> 

cat /etc/network/interfaces

auto lo
iface lo inet loopback

auto eth0
#iface eth0 inet dhcp

auto eth1
#iface eth1 inet dhcp

auto eth2
#iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

auto wlan0
#iface wlan0 inet dhcp


---

### Post by SpaceTeddy on 2008-02-22
ok, this is good. your network card is resonding to the pluged in cable and seems to work.. altought i have never seen that eth0:avah device before and i am not sure yet why it is there and has the ipaddress assigned to it....
[google...]
ok, avahi device is an autoconfig that seems to load if your computer gets no dhcp offers (if i understand that right). if not, someone PLEASE correct me).

by the looks of it, your router at home does not seem to give out dhcp leases anymore, resulting in your computer to have an unconfigured network card and therefore not being able to use the router.

what you will need to do is figure out the IP address if your router at home. I cannot help you there since it could, really, be anything.Lets say your router does have the IP 192.168.1.1 (common for many, but not for all). if that is so, you should try setting your network card manually for the same network (do this by copying the first three numbers of the ip address. then add the fourth number (which must not be the same as the routers) to get the full ip address...
Example in this case would be, if your router is 192.168.1.1, you could choose 192.168.1.2 for your computer.

ok, now assign the ip address to your computer with this command
> sudo ifconfig eth0 192.168.1.2
then add your router as the default gateway (telling your computer where the access to the internet is)
> sudo route add default gw 192.168.1.1
last, edit your nameserver configuration to have a nameserver. for that, type
> gksu gedit /etc/resolv.conf
and put the following line in that file
> nameserver 192.168.1.1

now, remember, this is a temporary configuration. once you reboot it will be gone (except for the nameservers). Also, it is not the desired way it should work. But it is a way to figure out if the problem is your computer or the router.

with all these setting, first try to ping the router itself
> ping -c4 192.168.1.1 
if that works, (if it tells you that you have replies) ) try to ping something in the internet
> ping -c4 [www.google.de](www.google.de)
if that also works, your internet should work again... and your router has no dhcp server running anymore..

ok, there is lots to be done, now lets do it :)

[B]please remeber, that the address 192.168.1.1 is supposed to be your ROUTER, so if it has a different ip, then replace all 192.168.1.1 with the one your router has.
also, the address i chose for your computer (192.168.1.2) is dependant on the the router one... the first the numbers HAVE TO MATCH! the last has to be between 1 and 254 and must not be the same as the routers ![/B]

---

### Post by Iowan on 2008-02-22
If that's the entire **/etc/network/interfaces** file, you need to make a slight adjustment...
```
auto eth0
#iface eth0 inet dhcp
```
Remove the # from this line to uncomment it - eth0 is currently unconfigured.  Might be possible to do similar things from the toolbar (Not near my machine, and don't have key sequence memorized.)  Sounds like eth0 is set to 3rd option (not static, not dhcp).

---

### Post by pietshah on 2008-02-22
> **Iowan said:**
> If that's the entire **/etc/network/interfaces** file, you need to make a slight adjustment...
```
auto eth0
#iface eth0 inet dhcp
```
Remove the # from this line to uncomment it - eth0 is currently unconfigured.  Might be possible to do similar things from the toolbar (Not near my machine, and don't have key sequence memorized.)  Sounds like eth0 is set to 3rd option (not static, not dhcp).

I tried tons of things to modify that file... but unsuccessfully..... :(
Since I couldnt edit the file directly, I found out on that forum that I should type in the terminal
> sudo nano etc/network/interfaces
I did that, made the change but couldnt save successfully... and now when I do it again there is no text, it looks that the file is empty (but if I access it through the disk, it has not been changed).

How should I edit this file?
I'm very sorry...... Using the terminal is just something impossible to understand for me.... :(

---

### Post by pietshah on 2008-02-22
SO GOOD!!!
The problem is solved...


I dont know if it's trying all the things you told me (I was very lost with implementing it...), by pure luck or intervention of Ubuntu God, but that's it, Internet is now perfectly working.

I sincerely thank you for the attention and help you provided me.

greetings
Pierre

---

### Post by Iowan on 2008-02-23
GREAT!! Sorry I neglected to go through the editing process.  Mark this one [SOLVED] (Under Thread Tools) and begin using Ubuntu. :)

---

