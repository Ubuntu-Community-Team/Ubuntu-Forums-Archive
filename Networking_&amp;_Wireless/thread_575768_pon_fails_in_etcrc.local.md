---
title: "pon fails in /etc/rc.local"
date: 2007-10-14
forum: Networking &amp; Wireless
---

### Post by poncenby on 2007-10-14
hello list

i'm running 2.6.20-16-server and am having trouble with my rc.local script executing pon.

/etc/rc.local is executable and here is the contents:

```

pon speedtch
/sbin/iptables-restore < /etc/iptables.rules
bash -c '/command/svscanboot &'

exit 0

```

when rc.local finally executes the pon command fails, with output of "No such device".
Logging in and executing the same pon commands works pefectly.

here is a snippet of my ppp.log when pon is executed from the rc.local script:
```

Oct 14 17:55:50 idler pppd[3733]: pppd 2.4.4 started by root, uid 0
Oct 14 17:55:50 idler pppd[3733]: connect(0.38): No such device
Oct 14 17:55:50 idler pppd[3733]: Exit.

```

and here is a snippet of the ppp.log when i manually execute it;

```

Oct 14 18:09:14 idler pppd[3826]: Plugin pppoatm.so loaded.
Oct 14 18:09:14 idler pppd[3826]: pppd 2.4.4 started by mgb, uid 0
Oct 14 18:09:14 idler pppd[3826]: using channel 1
Oct 14 18:09:14 idler pppd[3826]: Using interface ppp0
Oct 14 18:09:14 idler pppd[3826]: Connect: ppp0 <--> 0.38
Oct 14 18:09:14 idler pppd[3826]: sent [LCP ConfReq id=0x1 <magic 0x3b509092>]
Oct 14 18:09:17 idler pppd[3826]: sent [LCP ConfReq id=0x1 <magic 0x3b509092>]
Oct 14 18:09:17 idler pppd[3826]: rcvd [LCP ConfReq id=0x1 <auth chap MD5> <magic 0xe6b398fd>]
Oct 14 18:09:17 idler pppd[3826]: sent [LCP ConfAck id=0x1 <auth chap MD5> <magic 0xe6b398fd>]
Oct 14 18:09:19 idler pppd[3826]: rcvd [LCP ConfReq id=0x2 <auth chap MD5> <magic 0xe6b398fd>]
Oct 14 18:09:19 idler pppd[3826]: sent [LCP ConfAck id=0x2 <auth chap MD5> <magic 0xe6b398fd>]
Oct 14 18:09:20 idler pppd[3826]: sent [LCP ConfReq id=0x1 <magic 0x3b509092>]
Oct 14 18:09:20 idler pppd[3826]: rcvd [LCP ConfAck id=0x1 <magic 0x3b509092>]
Oct 14 18:09:20 idler pppd[3826]: sent [LCP EchoReq id=0x0 magic=0x3b509092]
Oct 14 18:09:20 idler pppd[3826]: rcvd [CHAP Challenge id=0x1 <ef531c3d10cb123303eaf77fb31d8902>, name = "ESR14.Kingston5"]
Oct 14 18:09:20 idler pppd[3826]: sent [CHAP Response id=0x1 <52127542fd2304cc46590d09dc79168e>, name = "myname@plusdsl.net"]
Oct 14 18:09:20 idler pppd[3826]: rcvd [LCP EchoRep id=0x0 magic=0xe6b398fd]
Oct 14 18:09:20 idler pppd[3826]: rcvd [LCP ConfReq id=0x6e <mru 32725> <auth chap MD5> <magic 0x25eb2dd5>]
Oct 14 18:09:20 idler pppd[3826]: sent [LCP ConfReq id=0x2 <magic 0xcdbed652>]
Oct 14 18:09:20 idler pppd[3826]: sent [LCP ConfAck id=0x6e <mru 32725> <auth chap MD5> <magic 0x25eb2dd5>]
Oct 14 18:09:20 idler pppd[3826]: rcvd [LCP ConfAck id=0x2 <magic 0xcdbed652>]
Oct 14 18:09:20 idler pppd[3826]: Couldn't increase MTU to 32725. Using 16384
Oct 14 18:09:20 idler pppd[3826]: sent [LCP EchoReq id=0x0 magic=0xcdbed652]
Oct 14 18:09:20 idler pppd[3826]: rcvd [CHAP Challenge id=0x59 <3d643d395fb445e9d4bd51c2750e7c9e>, name = "PTE-AG2"]
Oct 14 18:09:20 idler pppd[3826]: sent [CHAP Response id=0x59 <ca7a867db8c27a7d62e6e2625e27fafd>, name = "myname@plusdsl.net"]
Oct 14 18:09:20 idler pppd[3826]: rcvd [LCP EchoRep id=0x0 magic=0x25eb2dd5]
Oct 14 18:09:20 idler pppd[3826]: rcvd [CHAP Success id=0x59 ""]
Oct 14 18:09:20 idler pppd[3826]: CHAP authentication succeeded
Oct 14 18:09:20 idler pppd[3826]: CHAP authentication succeeded
Oct 14 18:09:20 idler pppd[3826]: sent [IPCP ConfReq id=0x1 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
Oct 14 18:09:20 idler pppd[3826]: rcvd [IPCP ConfNak id=0x1 <addr x.x.x.x> <ms-dns1 212.159.6.9> <ms-dns3 212.159.6.10>]
Oct 14 18:09:20 idler pppd[3826]: sent [IPCP ConfReq id=0x2 <addr x.x.x.x> <ms-dns1 212.159.6.9> <ms-dns3 212.159.6.10>]
Oct 14 18:09:20 idler pppd[3826]: rcvd [IPCP ConfReq id=0xae <addr 195.166.128.72>]
Oct 14 18:09:20 idler pppd[3826]: sent [IPCP ConfAck id=0xae <addr 195.166.128.72>]
Oct 14 18:09:20 idler pppd[3826]: rcvd [IPCP ConfAck id=0x2 <addr x.x.x.x> <ms-dns1 212.159.6.9> <ms-dns3 212.159.6.10>]
Oct 14 18:09:20 idler pppd[3826]: Cannot determine ethernet address for proxy ARP
Oct 14 18:09:20 idler pppd[3826]: local  IP address x.x.x.x
Oct 14 18:09:20 idler pppd[3826]: remote IP address 195.166.128.72
Oct 14 18:09:20 idler pppd[3826]: primary   DNS address 212.159.6.9
Oct 14 18:09:20 idler pppd[3826]: secondary DNS address 212.159.6.10
Oct 14 18:09:21 idler pppd[3833]: Script /etc/ppp/ip-up started (pid 3834)
Oct 14 18:09:21 idler pppd[3833]: Script /etc/ppp/ip-up finished (pid 3834), status = 0x0

```

my dmesg is here:
```

[    0.000000] Linux version 2.6.20-16-server (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Sep 23 19:57:25 UTC 2007 (Ubuntu 2.6.20-16.32-server)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 00000000000a0000 end: 00000000000a0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000003fef0000 end: 000000003fff0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000003fff0000 size: 0000000000003000 end: 000000003fff3000 type: 4
[    0.000000] copy_e820_map() start: 000000003fff3000 size: 000000000000d000 end: 0000000040000000 type: 3
[    0.000000] copy_e820_map() start: 00000000ffff0000 size: 0000000000010000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)
[    0.000000]  BIOS-e820: 000000003fff0000 - 000000003fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fff3000 - 0000000040000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
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
[    0.000000] ACPI: RSDP (v000 VT8371                                ) @ 0x000f7aa0
[    0.000000] ACPI: RSDT (v001 VT8371 AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3fff3000
[    0.000000] ACPI: FADT (v001 VT8371 AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3fff3040
[    0.000000] ACPI: DSDT (v001 VT8371 AWRDACPI 0x00001000 MSFT 0x0100000c) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bfff0000)
[    0.000000] Detected 1000.077 MHz processor.
[   32.377579] Built 1 zonelists.  Total pages: 260081
[   32.377587] Kernel command line: root=UUID=d44bdc37-2799-42e2-9e3a-54516b79aa61 ro quiet splash
[   32.377953] Local APIC disabled by BIOS -- you can enable it with "lapic"
[   32.377978] mapped APIC to ffffd000 (0180c000)
[   32.377988] Enabling fast FPU save and restore... done.
[   32.378019] Initializing CPU#0
[   32.378177] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   32.379556] Console: colour VGA+ 80x25
[   32.381688] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   32.384936] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   32.465151] Memory: 1028404k/1048512k available (2020k kernel code, 19372k reserved, 897k data, 332k init, 131008k highmem)
[   32.465177] virtual kernel memory layout:
[   32.465179]     fixmap  : 0xfff4f000 - 0xfffff000   ( 704 kB)
[   32.465182]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[   32.465185]     vmalloc : 0xf8800000 - 0xffbfe000   ( 115 MB)
[   32.465188]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   32.465191]       .init : 0xc03df000 - 0xc0432000   ( 332 kB)
[   32.465193]       .data : 0xc02f9299 - 0xc03d9754   ( 897 kB)
[   32.465196]       .text : 0xc0100000 - 0xc02f9299   (2020 kB)
[   32.465204] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   32.607970] Calibrating delay using timer specific routine.. 2001.63 BogoMIPS (lpj=10008190)
[   32.608089] Security Framework v1.0.0 initialized
[   32.608113] SELinux:  Disabled at boot.
[   32.608151] Mount-cache hash table entries: 512
[   32.608584] CPU: After generic identify, caps: 0183f9ff c1c7f9ff 00000000 00000000 00000000 00000000 00000000
[   32.608604] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   32.608610] CPU: L2 Cache: 256K (64 bytes/line)
[   32.608617] CPU: After all inits, caps: 0183f9ff c1c7f9ff 00000000 00000420 00000000 00000000 00000000
[   32.608650] Compat vDSO mapped to ffffe000.
[   32.608668] Remapping vsyscall page to ffffe000
[   32.608695] Checking 'hlt' instruction... OK.
[   32.648027] SMP alternatives: switching to UP code
[   32.648790] Freeing SMP alternatives: 11k freed
[   32.649334] Early unpacking initramfs... done
[   33.239618] ACPI: Core revision 20060707
[   33.246272] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   33.248144] ACPI: setting ELCR to 0020 (from 1c20)
[   33.250368] CPU0: AMD Athlon(tm) processor stepping 04
[   33.250382] SMP motherboard not detected.
[   33.250388] Local APIC not detected. Using dummy APIC emulation.
[   33.250507] Brought up 1 CPUs
[   33.251133] Booting paravirtualized kernel on bare hardware
[   33.251283] Time: 17:04:52  Date: 09/14/107
[   33.251366] NET: Registered protocol family 16
[   33.251612] EISA bus registered
[   33.251621] ACPI: bus type pci registered
[   33.283731] PCI: PCI BIOS revision 2.10 entry at 0xfb4e0, last bus=1
[   33.283737] PCI: Using configuration type 1
[   33.283741] Setting up standard PCI resources
[   33.302965] ACPI: Interpreter enabled
[   33.302972] ACPI: Using PIC for interrupt routing
[   33.304028] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   33.304042] PCI: Probing PCI hardware (bus 00)
[   33.304183] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[   33.304488] Disabling VIA memory write queue (PCI ID 0305, rev 03): [55] 89 & 1f -> 09
[   33.304761] PCI quirk: region 6000-607f claimed by vt82c686 HW-mon
[   33.304768] PCI quirk: region 5000-500f claimed by vt82c686 SMB
[   33.304949] Boot video device is 0000:01:00.0
[   33.305002] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   33.322780] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 11 12 14 15)
[   33.323293] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
[   33.323780] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   33.324321] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 10 11 *12 14 15)
[   33.326737] Linux Plug and Play Support v0.97 (c) Adam Belay
[   33.326784] pnp: PnP ACPI init
[   33.330060] pnp: PnP ACPI: found 8 devices
[   33.330071] PnPBIOS: Disabled by ACPI PNP
[   33.330213] PCI: Using ACPI for IRQ routing
[   33.330221] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   33.352896] NET: Registered protocol family 8
[   33.352901] NET: Registered protocol family 20
[   33.352921] NetLabel: Initializing
[   33.352925] NetLabel:  domain hash size = 128
[   33.352929] NetLabel:  protocols = UNLABELED CIPSOv4
[   33.352963] NetLabel:  unlabeled traffic allowed by default
[   33.354181] PCI: Bridge: 0000:00:01.0
[   33.354187]   IO window: disabled.
[   33.354195]   MEM window: e0000000-e1ffffff
[   33.354201]   PREFETCH window: d8000000-dfffffff
[   33.354229] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   33.354300] NET: Registered protocol family 2
[   33.437442] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   33.438034] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   33.443847] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   33.446826] TCP: Hash tables configured (established 131072 bind 65536)
[   33.446838] TCP reno registered
[   33.467530] checking if image is initramfs... it is
[   34.588770] Freeing initrd memory: 6642k freed
[   34.589896] audit: initializing netlink socket (disabled)
[   34.589934] audit(1192381494.180:1): initialized
[   34.590085] highmem bounce pool size: 64 pages
[   34.590221] VFS: Disk quotas dquot_6.5.1
[   34.590284] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   34.590422] io scheduler noop registered
[   34.590428] io scheduler anticipatory registered
[   34.590433] io scheduler deadline registered (default)
[   34.590450] io scheduler cfq registered
[   34.590484] Applying VIA southbridge workaround.
[   34.590493] PCI: Disabling Via external APIC routing
[   34.590942] isapnp: Scanning for PnP cards...
[   34.947581] isapnp: No Plug & Play device found
[   34.998238] Real Time Clock Driver v1.12ac
[   34.998343] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   34.999557] mice: PS/2 mouse device common for all mice
[   35.000833] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   35.001356] input: Macintosh mouse button emulation as /class/input/input0
[   35.001432] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   35.001442] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   35.001942] PNP: No PS/2 controller found. Probing ports directly.
[   35.245628] serio: i8042 KBD port at 0x60,0x64 irq 1
[   35.246031] EISA: Probing bus 0 at eisa.0
[   35.246067] Cannot allocate resource for EISA slot 4
[   35.246073] Cannot allocate resource for EISA slot 5
[   35.246078] Cannot allocate resource for EISA slot 6
[   35.246095] EISA: Detected 0 cards.
[   35.276276] TCP cubic registered
[   35.276290] NET: Registered protocol family 1
[   35.276345] Using IPI No-Shortcut mode
[   35.276496] ACPI: (supports S0 S1 S4 S5)
[   35.276581]   Magic number: 11:392:87
[   35.277920] Freeing unused kernel memory: 332k freed
[   35.285500] Time: tsc clocksource has been installed.
[   35.617533] Capability LSM initialized
[   35.693151] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   35.693166] ACPI: Processor [CPU0] (supports 2 throttling states)
[   36.834912] usbcore: registered new interface driver usbfs
[   36.834964] usbcore: registered new interface driver hub
[   36.835010] usbcore: registered new device driver usb
[   36.837321] USB Universal Host Controller Interface driver v3.0
[   36.838304] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 12
[   36.838312] PCI: setting IRQ 12 as level-triggered
[   36.838320] ACPI: PCI Interrupt 0000:00:07.2[D] -> Link [LNKD] -> GSI 12 (level, low) -> IRQ 12
[   36.838350] uhci_hcd 0000:00:07.2: UHCI Host Controller
[   36.838684] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[   36.838727] uhci_hcd 0000:00:07.2: irq 12, io base 0x0000e400
[   36.839001] usb usb1: configuration #1 chosen from 1 choice
[   36.839059] hub 1-0:1.0: USB hub found
[   36.839082] hub 1-0:1.0: 2 ports detected
[   36.944327] ACPI: PCI Interrupt 0000:00:07.3[D] -> Link [LNKD] -> GSI 12 (level, low) -> IRQ 12
[   36.944361] uhci_hcd 0000:00:07.3: UHCI Host Controller
[   36.944410] uhci_hcd 0000:00:07.3: new USB bus registered, assigned bus number 2
[   36.944449] uhci_hcd 0000:00:07.3: irq 12, io base 0x0000e800
[   36.944699] usb usb2: configuration #1 chosen from 1 choice
[   36.944752] hub 2-0:1.0: USB hub found
[   36.944777] hub 2-0:1.0: 2 ports detected
[   37.056169] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[   37.056184] PCI: setting IRQ 11 as level-triggered
[   37.056191] ACPI: PCI Interrupt 0000:00:0d.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[   37.056210] 3c59x: Donald Becker and others. www.scyld.com/network/vortex.html
[   37.056225] 0000:00:0d.0: 3Com PCI 3c905C Tornado at f881e000.
[   37.081554] VP_IDE: IDE controller at PCI slot 0000:00:07.1
[   37.081600] VP_IDE: chipset revision 6
[   37.081606] VP_IDE: not 100% native mode: will probe irqs later
[   37.081624] VP_IDE: VIA vt82c686b (rev 40) IDE UDMA100 controller on pci0000:00:07.1
[   37.081639]     ide0: BM-DMA at 0xe000-0xe007, BIOS settings: hda:DMA, hdb:DMA
[   37.081668]     ide1: BM-DMA at 0xe008-0xe00f, BIOS settings: hdc:DMA, hdd:DMA
[   37.081687] Probing IDE interface ide0...
[    4.930000] Time: acpi_pm clocksource has been installed.
[    5.030000] usb 1-2: new full speed USB device using uhci_hcd and address 2
[    5.160000] hda: WDC WD3200SB-01KMA0, ATA DISK drive
[    5.230000] usb 1-2: configuration #1 chosen from 1 choice
[    5.460000] hdb: ST3250823A, ATA DISK drive
[    5.520000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    5.520000] Probing IDE interface ide1...
[    6.440000] hdc: CRD-8482B, ATAPI CD/DVD-ROM drive
[    6.740000] hdd: HDS722525VLAT80, ATA DISK drive
[    6.800000] hdc: Disabling (U)DMA for CRD-8482B (blacklisted)
[    6.800000] ide1 at 0x170-0x177,0x376 on irq 15
[    6.810000] SCSI subsystem initialized
[    6.830000] libata version 2.20 loaded.
[    6.880000] hda: max request size: 512KiB
[    6.880000] hda: 625142448 sectors (320072 MB) w/8192KiB Cache, CHS=38913/255/63, UDMA(100)
[    6.880000] hda: cache flushes supported
[    6.880000]  hda: hda1 hda2 < hda5 >
[    6.900000] hdb: max request size: 512KiB
[    6.900000] hdb: 488397168 sectors (250059 MB) w/8192KiB Cache, CHS=30401/255/63, UDMA(100)
[    6.900000] hdb: cache flushes supported
[    6.900000]  hdb:
[    6.920000] hdd: max request size: 512KiB
[    6.930000] hdd: 488397168 sectors (250059 MB) w/7938KiB Cache, CHS=30401/255/63, UDMA(100)
[    6.930000] hdd: cache flushes supported
[    6.930000]  hdd:
[    6.970000] hdc: ATAPI 48X CD-ROM drive, 128kB Cache
[    6.970000] Uniform CD-ROM driver Revision: 3.20
[    7.260000] Attempting manual resume
[    7.260000] swsusp: Resume From Partition 3:5
[    7.260000] PM: Checking swsusp image.
[    7.260000] PM: Resume from disk failed.
[    7.320000] kjournald starting.  Commit interval 5 seconds
[    7.320000] EXT3-fs: mounted filesystem with ordered data mode.
[    9.920000] eth0:  setting full-duplex.
[   10.420000] NET: Registered protocol family 10
[   10.420000] lo: Disabled Privacy Extensions
[   12.220000] parport_pc: VIA 686A/8231 detected
[   12.220000] parport_pc: probing current configuration
[   12.220000] parport_pc: Current parallel port base: 0x0
[   12.220000] parport_pc: VIA parallel port disabled in BIOS
[   12.240000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   12.240000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.430000] Linux agpgart interface v0.102 (c) Dave Jones
[   12.720000] agpgart: Detected VIA Twister-K/KT133x/KM133 chipset
[   12.730000] agpgart: AGP aperture is 128M @ 0xd0000000
[   13.220000] input: PC Speaker as /class/input/input1
[   14.520000] usb 1-2: reset full speed USB device using uhci_hcd and address 2
[   14.710000] usbcore: registered new interface driver speedtch
[   14.760000] speedtch 1-2:1.0: found stage 1 firmware speedtch-1.bin
[   15.360000] speedtch 1-2:1.0: found stage 2 firmware speedtch-2.bin
[   15.630000] lp: driver loaded but no devices found
[   15.800000] Adding 1951856k swap on /dev/disk/by-uuid/16a06d7f-df06-4b4b-9a73-cdedbedf5acf.  Priority:-1 extents:1 across:1951856k
[   15.960000] EXT3 FS on hda1, internal journal
[   19.080000] PPP generic driver version 2.4.2
[   20.270000] ATM dev 0: ADSL line is synchronising
[   21.100000] eth0: no IPv6 routers present
[   35.270000] ATM dev 0: ADSL line is up (6688 kb/s down | 448 kb/s up)
[  280.460000] ip_tables: (C) 2000-2006 Netfilter Core Team
[  280.480000] Netfilter messages via NETLINK v0.30.
[  280.490000] nf_conntrack version 0.5.0 (8191 buckets, 65528 max)

```

how can I get pon to work reliably on boot-up?
and any idea why I get "No such device" when I can interactively execute pon with no problems?

any ideas greatly appreciated

poncenby

---

