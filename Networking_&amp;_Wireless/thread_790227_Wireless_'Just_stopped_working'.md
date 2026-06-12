---
title: "Wireless 'Just stopped working'?"
date: 2008-05-11
forum: Networking &amp; Wireless
---

### Post by greyloki on 2008-05-11
Hey there folks,

I've been using Xubuntu on my Packard Bell EasyNote e2570 since 6.10, and i've been very very pleased with the experience so far - everything worked out of the box, configuring everything was a dream, and it's a heck of a lot more responsive than my XP partition.

However, i've recently run into a bit of a problem with my wireless. The e2570 doesn't come with built-in wireless, so i've been supplementing it with an Asus WL-167g USB wireless adapter, using (I think) the rt2500 series of drivers. (See - [http://www.asus.com/products.aspx?l1=12&l2=42&l3=136&model=57&modelmenu=1](http://www.asus.com/products.aspx?l1=12&l2=42&l3=136&model=57&modelmenu=1) )

So far as I can tell, it 'just stopped' working one day - I know that it's probably user error, but I just can't think of anything i've changed that would have stopped wireless from working. This change happened in 7.10, and I tried updating to 8.04 via a CD image downloaded in XP then copied over to Xubuntu and mounted - i'm now running Xubuntu 8.04, but i'm still having difficulties with the wireless.

I've tried configuring a router to have no security at all - totally open, and I still have the same problems.

OK, time for the details:

gksudo wlassistant
```
Loaded application options.
All interfaces: eth0, rausb0, wmaster0
Wireless interface(s): rausb0
Permissions checked.
DHCP Client: dhclient
All executables found.
scan: /sbin/iwlist rausb0 scan
Networks found: 1
ACTION: CONNECT.
Running DHCP client found.
kill_dhcp: /sbin/dhclient -r rausb0
==>stderr: There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/rausb0/00:11:2f:6b:de:f6
Sending on   LPF/rausb0/00:11:2f:6b:de:f6
Sending on   Socket/fallback
DHCPRELEASE on rausb0 to 192.168.1.254 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
No pre-connection command specified.
iwconfig_set: /sbin/iwconfig rausb0 mode managed channel 8 key restricted xxxxxxxxxx essid BTVOYAGER2110-07
==>stderr: iwconfig: unknown command "d5a6c689c5a5u"
iwconfig_ap: /sbin/iwconfig rausb0 ap 00:16:E3:E7:17:07
ifconfig_dhcp: /sbin/dhclient rausb0
==>stderr: There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/rausb0/00:11:2f:6b:de:f6
Sending on   LPF/rausb0/00:11:2f:6b:de:f6
Sending on   Socket/fallback
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 18
Running DHCP client found.
kill_dhcp: /sbin/dhclient -r rausb0
==>stderr: There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/rausb0/00:11:2f:6b:de:f6
Sending on   LPF/rausb0/00:11:2f:6b:de:f6
Sending on   Socket/fallback
DHCPRELEASE on rausb0 to 192.168.1.254 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
CONNECTION FAILED.
disconnect: /sbin/iwconfig rausb0 mode managed key off ap off essid off
Application options saved.
Kernel socket closed.

```

lspci

```
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
01:02.0 Ethernet controller: VIA Technologies, Inc. VT6105 [Rhine-III] (rev 8b)
01:03.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)

```

dmesg

```
[    0.000000] Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000000dff0000 (usable)
[    0.000000]  BIOS-e820: 000000000dff0000 - 000000000dffffc0 (ACPI data)
[    0.000000]  BIOS-e820: 000000000dffffc0 - 000000000e000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000ffb80000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 223MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 57328) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    57328
[    0.000000]   HighMem     57328 ->    57328
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    57328
[    0.000000] On node 0 totalpages: 57328
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 415 pages used for memmap
[    0.000000]   Normal zone: 52817 pages, LIFO batch:15
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00E6010 checksum 0
[    0.000000] ACPI: RSDP 000E6010, 0014 (r0 OID_00)
[    0.000000] ACPI: RSDT 0DFFCF80, 0030 (r1 INSYDE RSDT_000        1 _CSI    10103)
[    0.000000] ACPI: FACP 0DFFFB00, 0074 (r1 INSYDE FACP_000      100 _CSI    10103)
[    0.000000] ACPI: DSDT 0DFFCFC0, 2B37 (r1 INSYDE INTELIC4     1004 INTL  2002025)
[    0.000000] ACPI: FACS 0DFFFFC0, 0040
[    0.000000] ACPI: BOOT 0DFFFB90, 0028 (r1 INSYDE SYS_BOOT      100 _CSI    10103)
[    0.000000] ACPI: DBGP 0DFFFBC0, 0034 (r1 INSYDE DBGP_000      100 _CSI    10103)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] Allocating PCI resources starting at 10000000 (gap: 0e000000:f1b80000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 56881
[    0.000000] Kernel command line: root=UUID=9d7dc77f-59ca-4a9a-9790-25725c8a1bc2 ro quiet splash
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffb000 (011cc000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[    0.000000] Detected 1394.370 MHz processor.
[   13.554167] Console: colour VGA+ 80x25
[   13.554173] console [tty0] enabled
[   13.554279] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[   13.554385] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[   13.561399] Memory: 215332k/229312k available (2157k kernel code, 13524k reserved, 998k data, 364k init, 0k highmem)
[   13.561409] virtual kernel memory layout:
[   13.561410]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   13.561412]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   13.561413]     vmalloc : 0xce800000 - 0xff7fe000   ( 783 MB)
[   13.561415]     lowmem  : 0xc0000000 - 0xcdff0000   ( 223 MB)
[   13.561416]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
[   13.561418]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
[   13.561420]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
[   13.561424] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   13.561469] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   13.641452] Calibrating delay using timer specific routine.. 2790.72 BogoMIPS (lpj=5581445)
[   13.641486] Security Framework initialized
[   13.641496] SELinux:  Disabled at boot.
[   13.641516] AppArmor: AppArmor initialized
[   13.641522] Failure registering capabilities with primary security module.
[   13.641533] Mount-cache hash table entries: 512
[   13.641693] CPU: After generic identify, caps: afe9f9ff 00100000 00000000 00000000 00000000 00000000 00000000 00000000
[   13.641709] CPU: L1 I cache: 32K, L1 D cache: 32K
[   13.641712] CPU: L2 cache: 1024K
[   13.641715] CPU: After all inits, caps: afe9f9ff 00100000 00000000 00002040 00000000 00000000 00000000 00000000
[   13.641726] Compat vDSO mapped to ffffe000.
[   13.641741] Checking 'hlt' instruction... OK.
[   13.657865] SMP alternatives: switching to UP code
[   13.659998] Freeing SMP alternatives: 11k freed
[   13.660134] Early unpacking initramfs... done
[   14.106213] ACPI: Core revision 20070126
[   14.106279] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   14.107652] ACPI: setting ELCR to 0200 (from 0ca8)
[   14.129066] CPU0: Intel(R) Celeron(R) M processor         1.40GHz stepping 08
[   14.129073] SMP motherboard not detected.
[   14.129076] Local APIC not detected. Using dummy APIC emulation.
[   14.129127] Brought up 1 CPUs
[   14.129146] CPU0 attaching sched-domain:
[   14.129150]  domain 0: span 01
[   14.129152]   groups: 01
[   14.129371] net_namespace: 64 bytes
[   14.129386] Booting paravirtualized kernel on bare hardware
[   14.130132] Time: 11:08:05  Date: 05/11/08
[   14.130162] NET: Registered protocol family 16
[   14.130396] EISA bus registered
[   14.130410] ACPI: bus type pci registered
[   14.130568] PCI: PCI BIOS revision 2.10 entry at 0xe97b4, last bus=1
[   14.130571] PCI: Using configuration type 1
[   14.130573] Setting up standard PCI resources
[   14.134079] ACPI: EC: Look up EC in DSDT
[   14.135469] ACPI: Interpreter enabled
[   14.135473] ACPI: (supports S0 S3 S4 S5)
[   14.135490] ACPI: Using PIC for interrupt routing
[   14.136826] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   14.144463] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[   14.144466] ACPI: EC: driver started in interrupt mode
[   14.144509] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   14.144939] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[   14.144944] PCI quirk: region 1300-133f claimed by ICH4 GPIO
[   14.145226] PCI: Transparent bridge - 0000:00:1e.0
[   14.145290] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   14.145356] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI2._PRT]
[   14.147913] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 *10 11)
[   14.148008] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 10 11)
[   14.148099] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 10 *11)
[   14.148189] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 10 *11)
[   14.148276] ACPI: PCI Interrupt Link [LNKE] (IRQs *3 4 5 10 11)
[   14.148355] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 10 11) *0, disabled.
[   14.148433] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 10 11) *0, disabled.
[   14.148518] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 10 11) *7
[   14.148647] Linux Plug and Play Support v0.97 (c) Adam Belay
[   14.148685] pnp: PnP ACPI init
[   14.148695] ACPI: bus type pnp registered
[   14.152534] pnp: PnP ACPI: found 10 devices
[   14.152537] ACPI: ACPI bus type pnp unregistered
[   14.152543] PnPBIOS: Disabled by ACPI PNP
[   14.152801] PCI: Using ACPI for IRQ routing
[   14.152805] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   14.169205] NET: Registered protocol family 8
[   14.169208] NET: Registered protocol family 20
[   14.169284] AppArmor: AppArmor Filesystem Enabled
[   14.173193] Time: tsc clocksource has been installed.
[   14.181234] system 00:05: iomem range 0xfff80000-0xffffffff could not be reserved
[   14.181242] system 00:07: ioport range 0x680-0x6ff has been reserved
[   14.181246] system 00:07: ioport range 0x200-0x20f has been reserved
[   14.181249] system 00:07: ioport range 0x290-0x297 has been reserved
[   14.181253] system 00:07: ioport range 0x1000-0x107f has been reserved
[   14.181257] system 00:07: ioport range 0x1300-0x133f has been reserved
[   14.181260] system 00:07: ioport range 0x77c-0x77f has been reserved
[   14.211727] PCI: Bus 2, cardbus bridge: 0000:01:03.0
[   14.211730]   IO window: 0000c400-0000c4ff
[   14.211735]   IO window: 0000c800-0000c8ff
[   14.211739]   PREFETCH window: a0000000-a3ffffff
[   14.211744]   MEM window: e4000000-e7ffffff
[   14.211747] PCI: Bridge: 0000:00:1e.0
[   14.211751]   IO window: c000-dfff
[   14.211756]   MEM window: e0000000-efffffff
[   14.211760]   PREFETCH window: a0000000-afffffff
[   14.211772] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   14.211955] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[   14.211959] PCI: setting IRQ 5 as level-triggered
[   14.211963] ACPI: PCI Interrupt 0000:01:03.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[   14.211979] NET: Registered protocol family 2
[   14.249248] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[   14.249532] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[   14.249594] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[   14.249658] TCP: Hash tables configured (established 8192 bind 8192)
[   14.249662] TCP reno registered
[   14.261303] checking if image is initramfs... it is
[   14.712953] Switched to high resolution mode on CPU 0
[   15.135498] Freeing initrd memory: 7416k freed
[   15.135767] Simple Boot Flag at 0x37 set to 0x1
[   15.136187] audit: initializing netlink socket (disabled)
[   15.136208] audit(1210504085.560:1): initialized
[   15.138905] VFS: Disk quotas dquot_6.5.1
[   15.139015] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   15.139222] io scheduler noop registered
[   15.139225] io scheduler anticipatory registered
[   15.139228] io scheduler deadline registered
[   15.139246] io scheduler cfq registered (default)
[   15.139265] Boot video device is 0000:00:02.0
[   15.139637] isapnp: Scanning for PnP cards...
[   15.493348] isapnp: No Plug & Play device found
[   15.532257] Real Time Clock Driver v1.12ac
[   15.532389] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   15.533897] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   15.533987] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   15.534107] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   15.543373] i8042.c: Detected active multiplexing controller, rev 1.1.
[   15.547404] serio: i8042 KBD port at 0x60,0x64 irq 1
[   15.547410] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   15.547413] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   15.547416] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   15.547419] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   15.548523] mice: PS/2 mouse device common for all mice
[   15.548656] EISA: Probing bus 0 at eisa.0
[   15.548665] Cannot allocate resource for EISA slot 1
[   15.548694] EISA: Detected 0 cards.
[   15.548698] cpuidle: using governor ladder
[   15.548700] cpuidle: using governor menu
[   15.548838] NET: Registered protocol family 1
[   15.548876] Using IPI No-Shortcut mode
[   15.548917] registered taskstats version 1
[   15.549042]   Magic number: 8:50:125
[   15.549191]   hash matches device device:00
[   15.549196] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   15.549199] EDD information not available.
[   15.549421] Freeing unused kernel memory: 364k freed
[   15.572430] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   16.785316] fuse init (API version 7.9)
[   16.815510] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   16.815517] ACPI: Processor [CPU0] (supports 8 throttling states)
[   17.619343] usbcore: registered new interface driver usbfs
[   17.619375] usbcore: registered new interface driver hub
[   17.631250] usbcore: registered new device driver usb
[   17.688178] SCSI subsystem initialized
[   17.811194] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[   17.811477] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 3
[   17.811481] PCI: setting IRQ 3 as level-triggered
[   17.811485] ACPI: PCI Interrupt 0000:01:02.0[A] -> Link [LNKE] -> GSI 3 (level, low) -> IRQ 3
[   17.811495] PCI: Setting latency timer of device 0000:01:02.0 to 64
[   17.820041] eth0: VIA Rhine III at 0xe0000000, 00:40:d0:7b:ca:0d, IRQ 3.
[   17.820756] eth0: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
[   17.831105] libata version 3.00 loaded.
[   17.837932] USB Universal Host Controller Interface driver v3.0
[   17.838229] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
[   17.838233] PCI: setting IRQ 10 as level-triggered
[   17.838237] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[   17.838250] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   17.838255] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   17.838656] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   17.838684] uhci_hcd 0000:00:1d.0: irq 10, io base 0x00001200
[   17.838868] usb usb1: configuration #1 chosen from 1 choice
[   17.838897] hub 1-0:1.0: USB hub found
[   17.838905] hub 1-0:1.0: 2 ports detected
[   18.338988] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[   18.338995] PCI: setting IRQ 11 as level-triggered
[   18.339000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   18.339018] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   18.339023] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   18.339079] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   18.339107] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001600
[   18.339268] usb usb2: configuration #1 chosen from 1 choice
[   18.339301] hub 2-0:1.0: USB hub found
[   18.339309] hub 2-0:1.0: 2 ports detected
[   18.642795] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[   18.642802] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
[   18.642827] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   18.642832] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   18.642887] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 3
[   18.646792] ehci_hcd 0000:00:1d.7: debug port 1
[   18.646798] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   18.646807] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xfebff000
[   18.682628] usb 2-2: new full speed USB device using uhci_hcd and address 2
[   18.694595] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   18.694739] usb usb3: configuration #1 chosen from 1 choice
[   18.694770] hub 3-0:1.0: USB hub found
[   18.694778] hub 3-0:1.0: 4 ports detected
[   18.798925] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[   18.799122] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[   18.799126] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   18.799167] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   18.799181] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[   18.809957] ata_piix 0000:00:1f.1: version 2.12
[   18.809979] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   18.810014] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   18.810402] scsi0 : ata_piix
[   18.811151] scsi1 : ata_piix
[   18.812047] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1100 irq 14
[   18.812051] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1108 irq 15
[   18.974881] ata1.00: ATA-6: ST950212A, 3.05, max UDMA/100
[   18.974887] ata1.00: 97692174 sectors, multi 16: LBA48 
[   18.990812] ata1.00: configured for UDMA/100
[   19.038406] usb 3-4: new high speed USB device using ehci_hcd and address 2
[   19.310528] ata2.00: ATAPI: HL-DT-STCD-RW/DVD DRIVE GCC-4244N, 1.00, max UDMA/33
[   19.330120] usb 3-4: configuration #1 chosen from 1 choice
[   19.482366] ata2.00: configured for UDMA/33
[   19.482521] scsi 0:0:0:0: Direct-Access     ATA      ST950212A        3.05 PQ: 0 ANSI: 5
[   19.487074] scsi 1:0:0:0: CD-ROM            HL-DT-ST RW/DVD_GCC-4244N 1.00 PQ: 0 ANSI: 5
[   19.502257] Driver 'sd' needs updating - please use bus_type methods
[   19.502365] sd 0:0:0:0: [sda] 97692174 512-byte hardware sectors (50018 MB)
[   19.502382] sd 0:0:0:0: [sda] Write Protect is off
[   19.502385] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   19.502405] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   19.502473] sd 0:0:0:0: [sda] 97692174 512-byte hardware sectors (50018 MB)
[   19.502484] sd 0:0:0:0: [sda] Write Protect is off
[   19.502487] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   19.502505] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   19.502510]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   19.524308]  sda1 sda2 sda3 < sda5 >
[   19.555061] sd 0:0:0:0: [sda] Attached SCSI disk
[   19.564330] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   19.564354] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   19.580332] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[   19.580339] Uniform CD-ROM driver Revision: 3.20
[   19.580410] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   20.088979] Attempting manual resume
[   20.088984] swsusp: Resume From Partition 8:5
[   20.088986] PM: Checking swsusp image.
[   20.089158] PM: Resume from disk failed.
[   20.150577] kjournald starting.  Commit interval 5 seconds
[   20.150594] EXT3-fs: mounted filesystem with ordered data mode.
[   30.199956] Clocksource tsc unstable (delta = -433052294 ns)
[   30.203942] Time: acpi_pm clocksource has been installed.
[   31.363328] Linux agpgart interface v0.102
[   31.435375] agpgart: Detected an Intel 855GM Chipset.
[   31.435693] agpgart: Detected 32636K stolen memory.
[   31.486217] agpgart: AGP aperture is 128M @ 0xb0000000
[   31.771104] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   31.827218] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   31.883085] iTCO_vendor_support: vendor-support=0
[   31.970973] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   31.971141] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x1060)
[   31.971193] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   32.250989] input: Power Button (FF) as /devices/virtual/input/input2
[   32.262771] ACPI: Power Button (FF) [PWRF]
[   32.262892] input: Sleep Button (CM) as /devices/virtual/input/input3
[   32.274749] ACPI: Sleep Button (CM) [SBTN]
[   32.274874] input: Lid Switch as /devices/virtual/input/input4
[   32.277938] ACPI: Lid Switch [LID]
[   32.306767] intel_rng: Firmware space is locked read-only. If you can't or
[   32.306770] intel_rng: don't want to disable this in firmware setup, and if
[   32.306772] intel_rng: you are certain that your system has a functional
[   32.306774] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   32.498757] ACPI: AC Adapter [AC] (on-line)
[   32.643533] ACPI: Battery Slot [BAT0] (battery present)
[   33.022487] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   33.302796] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:00/input/input6
[   33.314125] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   35.082162] Yenta: CardBus bridge found at 0000:01:03.0 [1631:d004]
[   35.082181] Yenta: Enabling burst memory read transactions
[   35.082186] Yenta: Using CSCINT to route CSC interrupts to PCI
[   35.082189] Yenta: Routing CardBus interrupts to PCI
[   35.082193] Yenta TI: socket 0000:01:03.0, mfunc 0x01111c02, devctl 0x64
[   35.313383] Yenta: ISA IRQ mask 0x00d0, PCI irq 5
[   35.313389] Socket status: 30000006
[   35.313392] Yenta: Raising subordinate bus# of parent bus (#01) from #01 to #05
[   35.313401] pcmcia: parent PCI bridge I/O window: 0xc000 - 0xdfff
[   35.313404] cs: IO port probe 0xc000-0xdfff: clean.
[   35.313948] pcmcia: parent PCI bridge Memory window: 0xe0000000 - 0xefffffff
[   35.313951] pcmcia: parent PCI bridge Memory window: 0xa0000000 - 0xafffffff
[   35.492918] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[   35.492949] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   36.191441] phy0: Selected rate control algorithm 'simple'
[   36.236200] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x256eb1, caps: 0x804713/0x0
[   36.308469] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio3/input/input7
[   36.316365] intel8x0_measure_ac97_clock: measured 55469 usecs
[   36.316371] intel8x0: clocking to 48000
[   36.356486] usbcore: registered new interface driver rt2500usb
[   37.402628] udev: renamed network interface wlan0 to rausb0
[   37.566827] cs: IO port probe 0x100-0x3af: clean.
[   37.568440] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   37.569144] cs: IO port probe 0x820-0x8ff: clean.
[   37.569728] cs: IO port probe 0xc00-0xcf7: clean.
[   37.570489] cs: IO port probe 0xa00-0xaff: clean.
[   37.704364] lp: driver loaded but no devices found
[   37.965150] Adding 650592k swap on /dev/sda5.  Priority:-1 extents:1 across:650592k
[   38.345559] EXT3 FS on sda1, internal journal
[   39.076346] ip_tables: (C) 2000-2006 Netfilter Core Team
[   39.622794] No dock devices found.
[   44.293527] [drm] Initialized drm 1.1.0 20060810
[   44.313499] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[   44.313511] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   44.313603] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   44.313612] PCI: Enabling device 0000:00:02.1 (0000 -> 0002)
[   44.313617] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   44.313669] [drm] Initialized i915 1.6.0 20060119 on minor 1
[   44.775980] ppdev: user-space parallel port driver
[   45.014322] audit(1210504119.426:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4892 profile="/usr/sbin/cupsd" namespace="default"
[   45.060188] apm: BIOS not found.
[   46.437791] Bluetooth: Core ver 2.11
[   46.438738] NET: Registered protocol family 31
[   46.438743] Bluetooth: HCI device and connection manager initialized
[   46.438748] Bluetooth: HCI socket layer initialized
[   46.526839] Bluetooth: L2CAP ver 2.9
[   46.526845] Bluetooth: L2CAP socket layer initialized
[   46.595997] Bluetooth: RFCOMM socket layer initialized
[   46.596509] Bluetooth: RFCOMM TTY layer initialized
[   46.596513] Bluetooth: RFCOMM ver 1.8
[   71.321387] NET: Registered protocol family 10
[   71.322241] lo: Disabled Privacy Extensions
[   71.323719] ADDRCONF(NETDEV_UP): rausb0: link is not ready
[  116.379675] NET: Registered protocol family 17

```

iwconfig rausb0

```
rausb0    IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.447 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

Because I can still scan for wireless networks, i'm guessing that this is an issue with wlassistant rather than a card problem, however i've also tried wicd with the same result.

Any advice on this would be greatly appreciated.



Loki :)

---

### Post by koma77 on 2008-05-11
I have a similar situation: I can scan for wireless networks but I can't connect. Whenever I try I get to enter the WPA passphrase over and over again. Maybe one time out of 100 it will actually work.

Is this what you have as well?

---

### Post by thardis on 2008-05-11
just out of curiosity, have any of u guys changed the ubuntu splash screen that comes up during boot?
because i did that and the wifi stopped working..and restoring it restored the network

---

### Post by sunstriker on 2008-05-11
Try using wpa_supplicant. I don't know exactly how it works. But at school we have a wpa protected network with username/pass & certificate. The nm applet doesn't work with everyone so our Linux teacher created a script that uses wpa_supplicant.

---

### Post by greyloki on 2008-05-11
> **thardis said:**
> just out of curiosity, have any of u guys changed the ubuntu splash screen that comes up during boot?
because i did that and the wifi stopped working..and restoring it restored the network

I had, actually - i'll investigate that, though I can't think why it would affect my wireless :confused:

sunstriker, i'm currently trying to connect to WEP and unsecured networks - i'm not using WPA, although I remember that it was shortly after playing around with wpa and the supplicant that wireless stopped working. I wonder if totally removing both it and its configuration files might make a difference.

Thank you all for your suggestions so far - anyone else have any ideas?


Loki

---

### Post by greyloki on 2008-05-12
Obligatory bump!

Update: I've now tried changing the login screen a few times (!), and this has had no effect - i'll be trying the uninstallation of wpa_supplicant soon.

---

### Post by spamaverter on 2008-05-19
I am experiencing exactly the same problem (WL-167G wireless usb stick + Xubuntu 8.04 + WPA), among other difficulties with "Hardy" Heron.  :(  Worked fine in 7.10 - wasted all that time downloading/upgrading to the latest distro - not a happy camper.  :~(

EDIT:

After doing some forum searching, I did the following:

sudo lshw -C network

It's the strangest thing, but there's no "driver=(whatever driver)" line even though it shows up in Network Manager - it will even list the ssid of my router and ask for the WPA key... even stranger, I've gotten to the point where it says I'm connected, but I can't browse the internet (and it's not the router - I can connect fine in Windoze).

This is driving me crazy, as I said, it worked in 7.10!  Is there anyway to "downgrade"?  Or is anyone out there with a fix?  I'm about to give up on 8.04...

---

### Post by olemagnus on 2008-05-20
> **greyloki said:**
> I had, actually - i'll investigate that, though I can't think why it would affect my wireless :confused:

sunstriker, i'm currently trying to connect to WEP and unsecured networks - i'm not using WPA, although I remember that it was shortly after playing around with wpa and the supplicant that wireless stopped working. I wonder if totally removing both it and its configuration files might make a difference.

Thank you all for your suggestions so far - anyone else have any ideas?


Loki

I started messing with wpa_supplicant and my usb adapter siesed working. and on startup ubuntu crashed trying to "startup bluetooth". I reinstalled ubuntu on the whole, cause it'd be faster than trying to trace back anything i've done wrong...
I changed incrytion to WEP instead. Now i can connect for half a secound before it stops!! WTF????

---

### Post by olemagnus on 2008-05-20
> **olemagnus said:**
> I started messing with wpa_supplicant and my usb adapter siesed working. and on startup ubuntu crashed trying to "startup bluetooth". I reinstalled ubuntu on the whole, cause it'd be faster than trying to trace back anything i've done wrong...
I changed incrytion to WEP instead. Now i can connect for half a secound before it stops!! WTF????

OK... Now it's working! I haven't tutched it! Honest! Well, hope it stays stable then...

---

