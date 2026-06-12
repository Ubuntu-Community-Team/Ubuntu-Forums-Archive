---
title: "No linux drivers for my wireless card! Help, please!"
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by Kaliree on 2007-04-21
Woe is me! I have a **trendnet tew603pi** wireless PCI card. I have just installed Feisty Fawn (I also had this same issue with Edgy Eft) and there is no support for my card. I went to the Trendnet site, and there are no linux drivers, for my card. Am I just stuck buying a new card, or is there some linux magic, that you gurus of the Terminal, can help me with?  ](*,)


Also, I am running an AMD based x86 PC, and I am dual-booting Feisty Fawn and Windows XP Pro.  Feisty Fawn is by itself on my hdb, and Windows is by itself on my hda, if that makes any difference.

---

### Post by spd106 on 2007-04-22
The compatibility [table]("http://www.trendnet.com/support/os_compatibility.htm") isn't 100% correct, so there is a chance.

Could you please post the output of these commands please?
```
lspci
```
```
sudo lshw -class network
```
```
dmesg
```

Have you tried ndiswrapper?
Thanks

---

### Post by Kaliree on 2007-04-23
Thanks so much for the help.  I haven't tried ndiswrapper. I downloaded it, but I was pretty confused on how to use it. I know my way around computers, but I'm just learning Linux.  So here are the outputs: **_(I assumed you just wanted the information pertinent to the wireless card)_**


**lspci**
00:0f.0 Ethernet controller: Atheros Communications, Inc. AR5005VL 802.11bg Wireless NIC (rev 01) 

**sudo lshw -class network**
*-network:1 UNCLAIMED 
       description: Ethernet controller 
       product: AR5005VL 802.11bg Wireless NIC 
       vendor: Atheros Communications, Inc. 
       physical id: f 
       bus info: pci@00:0f.0 
       version: 01 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list 
       configuration: latency=64 maxlatency=28 mingnt=10 
       resources: iomemory:cffa0000-cffbffff irq:12 

dmesg
**_(I didn't know what you needed with “dmesg” so I left all the information as is)_**

[    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic) 
[    0.000000] BIOS-provided physical RAM map: 
[    0.000000] sanitize start 
[    0.000000] sanitize end 
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1 
[    0.000000] copy_e820_map() type is E820_RAM 
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2 
[    0.000000] copy_e820_map() start: 00000000000ee000 size: 0000000000012000 end: 0000000000100000 type: 2 
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000003fef0000 end: 000000003fff0000 type: 1 
[    0.000000] copy_e820_map() type is E820_RAM 
[    0.000000] copy_e820_map() start: 000000003fff0000 size: 0000000000008000 end: 000000003fff8000 type: 3 
[    0.000000] copy_e820_map() start: 000000003fff8000 size: 0000000000008000 end: 0000000040000000 type: 4 
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000001000 end: 00000000fec01000 type: 2 
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2 
[    0.000000] copy_e820_map() start: 00000000ffee0000 size: 0000000000020000 end: 00000000fff00000 type: 2 
[    0.000000] copy_e820_map() start: 00000000fffc0000 size: 0000000000040000 end: 0000000100000000 type: 2 
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable) 
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved) 
[    0.000000]  BIOS-e820: 00000000000ee000 - 0000000000100000 (reserved) 
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable) 
[    0.000000]  BIOS-e820: 000000003fff0000 - 000000003fff8000 (ACPI data) 
[    0.000000]  BIOS-e820: 000000003fff8000 - 0000000040000000 (ACPI NVS) 
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved) 
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved) 
[    0.000000]  BIOS-e820: 00000000ffee0000 - 00000000fff00000 (reserved) 
[    0.000000]  BIOS-e820: 00000000fffc0000 - 0000000100000000 (reserved) 
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
[    0.000000] ACPI: RSDP (v000 AMI                                   ) @ 0x000fa340 
[    0.000000] ACPI: RSDT (v001 AMIINT SiS735XX 0x00001000 MSFT 0x0100000b) @ 0x3fff0000 
[    0.000000] ACPI: FADT (v001 AMIINT SiS735XX 0x00001000 MSFT 0x0100000b) @ 0x3fff0030 
[    0.000000] ACPI: DSDT (v001    SiS      735 0x00000100 MSFT 0x0100000d) @ 0x00000000 
[    0.000000] ACPI: PM-Timer IO Port: 0x808 
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000) 
[    0.000000] Detected 1460.512 MHz processor. 
[   17.449422] Built 1 zonelists.  Total pages: 260081 
[   17.449427] Kernel command line: root=UUID=1b3c7ea7-f8ab-4a1a-8d4d-2062b527b10a ro quiet splash 
[   17.449651] Local APIC disabled by BIOS -- you can enable it with "lapic" 
[   17.449664] mapped APIC to ffffd000 (0180c000) 
[   17.449669] Enabling fast FPU save and restore... done. 
[   17.449672] Enabling unmasked SIMD FPU exception support... done. 
[   17.449688] Initializing CPU#0 
[   17.449761] PID hash table entries: 4096 (order: 12, 16384 bytes) 
[   17.451094] Console: colour VGA+ 80x25 
[   17.452271] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes) 
[   17.454415] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes) 
[   17.498819] Memory: 1028060k/1048512k available (1992k kernel code, 19700k reserved, 893k data, 328k init, 131008k highmem) 
[   17.498834] virtual kernel memory layout: 
[   17.498835]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB) 
[   17.498837]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB) 
[   17.498839]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB) 
[   17.498840]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB) 
[   17.498842]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB) 
[   17.498844]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB) 
[   17.498846]       .text : 0xc0100000 - 0xc02f2264   (1992 kB) 
[   17.498850] Checking if this processor honours the WP bit even in supervisor mode... Ok. 
[   17.577744] Calibrating delay using timer specific routine.. 2922.48 BogoMIPS (lpj=5844975) 
[   17.577813] Security Framework v1.0.0 initialized 
[   17.577825] SELinux:  Disabled at boot. 
[   17.577852] Mount-cache hash table entries: 512 
[   17.578103] CPU: After generic identify, caps: 0383f9ff c1cbf9ff 00000000 00000000 00000000 00000000 00000000 
[   17.578116] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line) 
[   17.578119] CPU: L2 Cache: 256K (64 bytes/line) 
[   17.578124] CPU: After all inits, caps: 0383f9ff c1cbf9ff 00000000 00000420 00000000 00000000 00000000 
[   17.578142] Compat vDSO mapped to ffffe000. 
[   17.578151] Remapping vsyscall page to ffffe000 
[   17.578167] Checking 'hlt' instruction... OK. 
[   17.593951] SMP alternatives: switching to UP code 
[   17.594363] Freeing SMP alternatives: 11k freed 
[   17.594723] Early unpacking initramfs... done 
[   18.019174] ACPI: Core revision 20060707 
[   18.021712] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT. 
[   18.023363] ACPI: setting ELCR to 0200 (from 1820) 
[   18.028631] CPU0: AMD Athlon(tm) XP 1700+ stepping 02 
[   18.028639] SMP motherboard not detected. 
[   18.028643] Local APIC not detected. Using dummy APIC emulation. 
[   18.028711] Brought up 1 CPUs 
[   18.029079] Booting paravirtualized kernel on bare hardware 
[   18.029177] Time:  9:53:07  Date: 03/23/107 
[   18.029230] NET: Registered protocol family 16 
[   18.029374] EISA bus registered 
[   18.029381] ACPI: bus type pci registered 
[   18.040085] PCI: PCI BIOS revision 2.10 entry at 0xfdb01, last bus=1 
[   18.040088] PCI: Using configuration type 1 
[   18.040091] Setting up standard PCI resources 
[   18.047536] ACPI: Interpreter enabled 
[   18.047544] ACPI: Using PIC for interrupt routing 
[   18.047982] ACPI: PCI Root Bridge [PCI0] (0000:00) 
[   18.047992] PCI: Probing PCI hardware (bus 00) 
[   18.048878] Enabling SiS 96x SMBus. 
[   18.049577] Boot video device is 0000:01:00.0 
[   18.049626] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT] 
[   18.055559] ACPI: Power Resource [URP1] (off) 
[   18.055644] ACPI: Power Resource [URP2] (off) 
[   18.055728] ACPI: Power Resource [FDDP] (off) 
[   18.055810] ACPI: Power Resource [LPTP] (off) 
[   18.056691] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 7 10 11 12 14 15) 
[   18.056976] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 *11 12 14 15) 
[   18.057257] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 *12 14 15) 
[   18.057544] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 *12 14 15) 
[   18.057873] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled. 
[   18.058150] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled. 
[   18.058426] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 *12 14 15) 
[   18.058706] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 *11 12 14 15) 
[   18.058903] Linux Plug and Play Support v0.97 (c) Adam Belay 
[   18.058925] pnp: PnP ACPI init 
[   18.063542] pnp: PnP ACPI: found 12 devices 
[   18.063551] PnPBIOS: Disabled by ACPI PNP 
[   18.063636] PCI: Using ACPI for IRQ routing 
[   18.063641] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report 
[   18.067083] NET: Registered protocol family 8 
[   18.067086] NET: Registered protocol family 20 
[   18.067576] PCI: Bridge: 0000:00:01.0 
[   18.067579]   IO window: disabled. 
[   18.067585]   MEM window: cde00000-cfefffff 
[   18.067590]   PREFETCH window: bdc00000-cdcfffff 
[   18.067643] NET: Registered protocol family 2 
[   18.105793] IP route cache hash table entries: 32768 (order: 5, 131072 bytes) 
[   18.106117] TCP established hash table entries: 131072 (order: 8, 1048576 bytes) 
[   18.109026] TCP bind hash table entries: 65536 (order: 7, 524288 bytes) 
[   18.110497] TCP: Hash tables configured (established 131072 bind 65536) 
[   18.110503] TCP reno registered 
[   18.121870] checking if image is initramfs... it is 
[   18.929620] Freeing initrd memory: 7013k freed 
[   18.930268] audit: initializing netlink socket (disabled) 
[   18.930291] audit(1177321987.664:1): initialized 
[   18.930391] highmem bounce pool size: 64 pages 
[   18.930478] VFS: Disk quotas dquot_6.5.1 
[   18.930511] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes) 
[   18.930593] io scheduler noop registered 
[   18.930597] io scheduler anticipatory registered 
[   18.930600] io scheduler deadline registered 
[   18.930610] io scheduler cfq registered (default) 
[   19.969742] isapnp: Scanning for PnP cards... 
[   20.323156] isapnp: No Plug & Play device found 
[   20.360283] Real Time Clock Driver v1.12ac 
[   20.360358] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled 
[   20.360520] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A 
[   20.360842] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A 
[   20.361815] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A 
[   20.362284] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A 
[   20.362670] mice: PS/2 mouse device common for all mice 
[   20.363453] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize 
[   20.363802] input: Macintosh mouse button emulation as /class/input/input0 
[   20.363849] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2 
[   20.363856] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx 
[   20.364174] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1 
[   20.364178] PNP: PS/2 controller doesn't have AUX irq; using default 12 
[   20.368167] serio: i8042 KBD port at 0x60,0x64 irq 1 
[   20.368355] EISA: Probing bus 0 at eisa.0 
[   20.368397] EISA: Detected 0 cards. 
[   20.398668] TCP cubic registered 
[   20.398679] NET: Registered protocol family 1 
[   20.398713] Using IPI No-Shortcut mode 
[   20.398865] ACPI: (supports S0 S1 S4 S5) 
[   20.398919]   Magic number: 3:9:880 
[   20.399064]   hash matches device ptyx4 
[   20.399694] Freeing unused kernel memory: 328k freed 
[   20.401301] Time: tsc clocksource has been installed. 
[   21.706006] Capability LSM initialized 
[   22.504487] usbcore: registered new interface driver usbfs 
[   22.504526] usbcore: registered new interface driver hub 
[   22.504576] usbcore: registered new device driver usb 
[   22.505803] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver 
[   22.506134] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 12 
[   22.506140] PCI: setting IRQ 12 as level-triggered 
[   22.506144] ACPI: PCI Interrupt 0000:00:02.2[D] -> Link [LNKD] -> GSI 12 (level, low) -> IRQ 12 
[   22.506164] ohci_hcd 0000:00:02.2: OHCI Host Controller 
[   22.506377] ohci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 1 
[   22.506402] ohci_hcd 0000:00:02.2: irq 12, io mem 0xcfffe000 
[   22.530576] sis900.c: v1.08.10 Apr. 2 2006 
[   22.619748] usb usb1: configuration #1 chosen from 1 choice 
[   22.619789] hub 1-0:1.0: USB hub found 
[   22.619809] hub 1-0:1.0: 3 ports detected 
[   22.685973] ieee1394: Initialized config rom entry `ip1394' 
[   22.721163] SIS5513: IDE controller at PCI slot 0000:00:02.5 
[   22.721189] SIS5513: chipset revision 208 
[   22.721192] SIS5513: not 100% native mode: will probe irqs later 
[   22.721200] SIS5513: SiS735 ATA 100 (2nd gen) controller 
[   22.721217]     ide0: BM-DMA at 0xff00-0xff07, BIOS settings: hda:DMA, hdb:DMA 
[   22.721235]     ide1: BM-DMA at 0xff08-0xff0f, BIOS settings: hdc:DMA, hdd:DMA 
[   22.721248] Probing IDE interface ide0... 
[   22.749534] Floppy drive(s): fd0 is 1.44M 
[   22.824533] FDC 0 is a post-1991 82077 
[   23.008987] hda: WDC WD800JB-00DUA3, ATA DISK drive 
[   23.288945] hdb: WDC WD600BB-00CAA0, ATA DISK drive 
[   23.346771] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14 
[   23.383697] Probing IDE interface ide1... 
[   24.116859] hdc: Optiarc DVD RW AD-7170A, ATAPI CD/DVD-ROM drive 
[   24.900733] hdd: LITE-ON LTR-32123S, ATAPI CD/DVD-ROM drive 
[   24.957516] ide1 at 0x170-0x177,0x376 on irq 15 
[   24.972824] SCSI subsystem initialized 
[   24.980957] libata version 2.20 loaded. 
[   24.989214] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 12 
[   24.989223] ACPI: PCI Interrupt 0000:00:03.0[A] -> Link [LNKG] -> GSI 12 (level, low) -> IRQ 12 
[   24.990034] 0000:00:03.0: Realtek RTL8201 PHY transceiver found at address 1. 
[   24.998300] 0000:00:03.0: Using transceiver found at address 1 as default 
[   25.002070] eth0: SiS 900 PCI Fast Ethernet at 0xd800, IRQ 12, 00:d0:09:ef:4d:39. 
[   25.002565] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11 
[   25.002571] PCI: setting IRQ 11 as level-triggered 
[   25.002575] ACPI: PCI Interrupt 0000:00:11.3[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11 
[   25.002595] ehci_hcd 0000:00:11.3: EHCI Host Controller 
[   25.002636] ehci_hcd 0000:00:11.3: new USB bus registered, assigned bus number 2 
[   25.002691] ehci_hcd 0000:00:11.3: debug port 1 
[   25.012112] hda: max request size: 512KiB 
[   25.024689] ehci_hcd 0000:00:11.3: irq 11, io mem 0xcfffcf00 
[   25.024701] ehci_hcd 0000:00:11.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004 
[   25.024866] usb usb2: configuration #1 chosen from 1 choice 
[   25.024903] hub 2-0:1.0: USB hub found 
[   25.024921] hub 2-0:1.0: 6 ports detected 
[   25.036401] hda: 156301488 sectors (80026 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(100) 
[   25.038086] hda: cache flushes supported 
[   25.038172]  hda: hda1 
[   25.052079] hdb: max request size: 128KiB 
[   25.052947] hdb: 117231408 sectors (60022 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100) 
[   25.052956] hdb: cache flushes not supported 
[   25.053011]  hdb: hdb1 hdb2 
[   25.129234] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 12 
[   25.129243] ACPI: PCI Interrupt 0000:00:0b.2[B] -> Link [LNKC] -> GSI 12 (level, low) -> IRQ 12 
[   25.180544] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[12]  MMIO=[cfffc000-cfffc7ff]  Max Packet=[2048]  IR/IT contexts=[4/8] 
[   25.184054] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11 
[   25.184060] ACPI: PCI Interrupt 0000:00:02.3[A] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11 
[   25.184081] ohci_hcd 0000:00:02.3: OHCI Host Controller 
[   25.184154] ohci_hcd 0000:00:02.3: new USB bus registered, assigned bus number 3 
[   25.184175] ohci_hcd 0000:00:02.3: irq 11, io mem 0xcffff000 
[   25.214455] hdc: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33) 
[   25.214469] Uniform CD-ROM driver Revision: 3.20 
[   25.238705] usb usb3: configuration #1 chosen from 1 choice 
[   25.238762] hub 3-0:1.0: USB hub found 
[   25.238780] hub 3-0:1.0: 3 ports detected 
[   25.240692] hdd: ATAPI 40X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33) 
[   25.340713] ACPI: PCI Interrupt 0000:00:11.0[B] -> Link [LNKC] -> GSI 12 (level, low) -> IRQ 12 
[   25.340741] ohci_hcd 0000:00:11.0: OHCI Host Controller 
[   25.340786] ohci_hcd 0000:00:11.0: new USB bus registered, assigned bus number 4 
[   25.340808] ohci_hcd 0000:00:11.0: irq 12, io mem 0xcfff9000 
[   25.398667] usb usb4: configuration #1 chosen from 1 choice 
[   25.398712] hub 4-0:1.0: USB hub found 
[   25.398731] hub 4-0:1.0: 2 ports detected 
[   25.500726] ACPI: PCI Interrupt 0000:00:11.1[C] -> Link [LNKD] -> GSI 12 (level, low) -> IRQ 12 
[   25.500760] ohci_hcd 0000:00:11.1: OHCI Host Controller 
[   25.500806] ohci_hcd 0000:00:11.1: new USB bus registered, assigned bus number 5 
[   25.500830] ohci_hcd 0000:00:11.1: irq 12, io mem 0xcfffa000 
[   25.520244] Attempting manual resume 
[   25.520250] swsusp: Resume From Partition 3:66 
[   25.520253] PM: Checking swsusp image. 
[   25.520456] PM: Resume from disk failed. 
[   25.558681] usb usb5: configuration #1 chosen from 1 choice 
[   25.558724] hub 5-0:1.0: USB hub found 
[   25.558743] hub 5-0:1.0: 2 ports detected 
[   25.573449] kjournald starting.  Commit interval 5 seconds 
[   25.573472] EXT3-fs: mounted filesystem with ordered data mode. 
[   25.661038] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 5 
[   25.661048] PCI: setting IRQ 5 as level-triggered 
[   25.661052] ACPI: PCI Interrupt 0000:00:11.2[D] -> Link [LNKA] -> GSI 5 (level, low) -> IRQ 5 
[   25.661085] ohci_hcd 0000:00:11.2: OHCI Host Controller 
[   25.661123] ohci_hcd 0000:00:11.2: new USB bus registered, assigned bus number 6 
[   25.661150] ohci_hcd 0000:00:11.2: irq 5, io mem 0xcfffb000 
[   25.718618] usb usb6: configuration #1 chosen from 1 choice 
[   25.718661] hub 6-0:1.0: USB hub found 
[   25.718679] hub 6-0:1.0: 2 ports detected 
[   25.964438] usb 5-1: new low speed USB device using ohci_hcd and address 2 
[   26.211559] usb 5-1: configuration #1 chosen from 1 choice 
[   26.452555] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023c0031028f5c] 
[   37.064105] sis630_smbus 0000:00:02.0: SIS630 comp. bus not detected, module not inserted. 
[   37.065790] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x0c00 
[   37.885623] gameport: EMU10K1 is pci0000:00:0b.1/gameport0, io 0xdc00, speed 1242kHz 
[   37.932058] Linux agpgart interface v0.102 (c) Dave Jones 
[   37.976646] agpgart: Detected SiS 735 chipset 
[   37.981460] agpgart: AGP aperture is 64M @ 0xd0000000 
[   38.127348] pci_hotplug: PCI Hot Plug PCI Core version: 0.5 
[   38.478619] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4 
[   38.491253] input: PC Speaker as /class/input/input1 
[   39.009172] parport: PnPBIOS parport detected. 
[   39.009234] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE] 
[   39.201983] nvidia: module license 'NVIDIA' taints kernel. 
[   39.470392] usbcore: registered new interface driver hiddev 
[   39.491498] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 5 (level, low) -> IRQ 5 
[   39.492147] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9631  Thu Nov  9 17:38:10 PST 2006 
[   39.644581] input: Logitech USB-PS/2 Optical Mouse as /class/input/input2 
[   39.644708] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:11.1-1 
[   39.644734] usbcore: registered new interface driver usbhid 
[   39.644739] drivers/usb/input/hid-core.c: v2.6:USB HID core driver 
[   39.797232] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11 
[   40.268879] fuse init (API version 7.8) 
[   40.303384] lp0: using parport0 (interrupt-driven). 
[   40.389005] Adding 4000176k swap on /dev/disk/by-uuid/167aaa69-fc72-4922-843a-7fc76c8200d6.  Priority:-1 extents:1 across:4000176k 
[   40.542112] EXT3 FS on hdb1, internal journal 
[   40.830206] NTFS driver 2.1.28 [Flags: R/O MODULE]. 
[   40.893422] NTFS volume version 3.1. 
[   42.410319] NET: Registered protocol family 17 
[   47.895855] input: Power Button (FF) as /class/input/input3 
[   47.902530] ACPI: Power Button (FF) [PWRF] 
[   47.950817] input: Sleep Button (CM) as /class/input/input4 
[   47.957329] ACPI: Sleep Button (CM) [SLPB] 
[   47.979138] No dock devices found. 
[   48.040880] Using specific hotkey driver 
[   48.219038] ibm_acpi: ec object not found 
[   48.270923] pcc_acpi: loading... 
[   53.016726] eth0: Media Link Off 
[   54.331373] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0. 
[   54.331838] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode 
[   54.332129] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode 
[   54.748825] ppdev: user-space parallel port driver 
[   55.057141] **WARNING** I2C adapter driver [NVIDIA i2c adapter 0 at 1:00.0] forgot to specify physical device; fix it! 
[   55.057929] **WARNING** I2C adapter driver [NVIDIA i2c adapter 1 at 1:00.0] forgot to specify physical device; fix it! 
[   55.057984] **WARNING** I2C adapter driver [NVIDIA i2c adapter 2 at 1:00.0] forgot to specify physical device; fix it! 
[   56.184687] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac) 
[   56.184696] apm: overridden by ACPI. 
[   56.418548] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]). 
[   56.547406] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory 
[   56.547988] NFSD: starting 90-second grace period 
[   58.126713] Bluetooth: Core ver 2.11 
[   58.126818] NET: Registered protocol family 31 
[   58.126821] Bluetooth: HCI device and connection manager initialized 
[   58.126828] Bluetooth: HCI socket layer initialized 
[   58.200740] Bluetooth: L2CAP ver 2.8 
[   58.200748] Bluetooth: L2CAP socket layer initialized 
[   58.588018] Bluetooth: RFCOMM socket layer initialized 
[   58.588047] Bluetooth: RFCOMM TTY layer initialized 
[   58.588050] Bluetooth: RFCOMM ver 1.8 
[   58.977710] NET: Registered protocol family 10 
[   58.977879] lo: Disabled Privacy Extensions 
[   58.977976] ADDRCONF(NETDEV_UP): eth0: link is not ready 
[   90.284909] input: AT Translated Set 2 keyboard as /class/input/input5 
[  386.603058] usb 2-6: new high speed USB device using ehci_hcd and address 3 
[  386.740558] usb 2-6: configuration #1 chosen from 1 choice 
[  386.887214] usbcore: registered new interface driver libusual 
[  386.910482] Initializing USB Mass Storage driver... 
[  386.910647] scsi0 : SCSI emulation for USB Mass Storage devices 
[  386.910735] usbcore: registered new interface driver usb-storage 
[  386.910740] USB Mass Storage support registered. 
[  386.910946] usb-storage: device found at 3 
[  386.910949] usb-storage: waiting for device to settle before scanning 
[  391.907165] usb-storage: device scan complete 
[  391.908025] scsi 0:0:0:0: Direct-Access     LEXAR    JUMPDRIVE SECURE 2000 PQ: 0 ANSI: 0 CCS 
[  391.993092] SCSI device sda: 248928 512-byte hdwr sectors (127 MB) 
[  391.994714] sda: Write Protect is off 
[  391.994719] sda: Mode Sense: 43 00 00 00 
[  391.994722] sda: assuming drive cache: write through 
[  391.996839] SCSI device sda: 248928 512-byte hdwr sectors (127 MB) 
[  391.998338] sda: Write Protect is off 
[  391.998342] sda: Mode Sense: 43 00 00 00 
[  391.998345] sda: assuming drive cache: write through 
[  391.998903]  sda: sda1 
[  392.053559] sd 0:0:0:0: Attached scsi disk sda 
[  392.070089] sd 0:0:0:0: Attached scsi generic sg0 type 0 
[  725.731678] hdc: tray open 
[  725.731997] end_request: I/O error, dev hdc, sector 0 
[  725.732005] Buffer I/O error on device hdc, logical block 0 
[  725.732012] Buffer I/O error on device hdc, logical block 1 
[  725.732017] Buffer I/O error on device hdc, logical block 2 
[  725.732020] Buffer I/O error on device hdc, logical block 3 
[  725.732024] Buffer I/O error on device hdc, logical block 4 
[  725.732027] Buffer I/O error on device hdc, logical block 5 
[  725.732031] Buffer I/O error on device hdc, logical block 6 
[  725.732035] Buffer I/O error on device hdc, logical block 7 
[  725.733121] hdc: tray open 
[  725.733430] end_request: I/O error, dev hdc, sector 0 
[  725.733436] Buffer I/O error on device hdc, logical block 0 
[  725.733589] hdc: tray open 
[  725.733899] end_request: I/O error, dev hdc, sector 4 
[  725.733904] Buffer I/O error on device hdc, logical block 1 
[  725.734274] hdc: tray open 
[  725.734581] end_request: I/O error, dev hdc, sector 0 
[  725.734904] hdc: tray open 
[  725.735222] end_request: I/O error, dev hdc, sector 4 
[  725.735604] hdc: tray open 
[  725.735924] end_request: I/O error, dev hdc, sector 0 
[  725.736090] hdc: tray open 
[  725.736413] end_request: I/O error, dev hdc, sector 4 
[  725.736712] hdc: tray open 
[  725.737022] end_request: I/O error, dev hdc, sector 0 
[  725.737181] hdc: tray open 
[  725.737490] end_request: I/O error, dev hdc, sector 4 
[  725.737871] hdc: tray open 
[  725.738183] end_request: I/O error, dev hdc, sector 0 
[  725.738341] hdc: tray open 
[  725.738650] end_request: I/O error, dev hdc, sector 4 
[  725.813788] hdd: tray open 
[  725.815947] end_request: I/O error, dev hdd, sector 0 
[  725.818196] hdd: tray open 
[  725.820356] end_request: I/O error, dev hdd, sector 0 
[  725.822605] hdd: tray open 
[  725.824765] end_request: I/O error, dev hdd, sector 4 
[  725.827015] hdd: tray open 
[  725.829174] end_request: I/O error, dev hdd, sector 0 
[  725.832425] hdd: tray open 
[  725.834585] end_request: I/O error, dev hdd, sector 4 
[  725.836835] hdd: tray open 
[  725.838995] end_request: I/O error, dev hdd, sector 0 
[  725.841244] hdd: tray open 
[  725.843403] end_request: I/O error, dev hdd, sector 4 
[  725.845653] hdd: tray open 
[  725.847813] end_request: I/O error, dev hdd, sector 0 
[  725.850063] hdd: tray open 
[  725.853223] end_request: I/O error, dev hdd, sector 4 
[  725.855473] hdd: tray open 
[  725.857633] end_request: I/O error, dev hdd, sector 0 
[  725.859883] hdd: tray open 
[  725.862042] end_request: I/O error, dev hdd, sector 4

---

### Post by spd106 on 2007-04-24
The good news is that there is a driver being worked on (madwifi), the bad news is it won't likely support your card for a while yet. It will be lucky to make the 7.10 release. This means that you will have to use ndiswrapper for the moment. To do this you will need your windows driver. I suggest you follow one of the many guides in this forum and report back here how you get on.

This one is pretty good, [http://ubuntuforums.org/showthread.php?t=340689](http://ubuntuforums.org/showthread.php?t=340689), just skip the parts about Broadcom and use your own driver rather than the one from sp33008.exe.

---

### Post by stchman on 2007-04-25
> **Kaliree said:**
> Woe is me! I have a **trendnet tew603pi** wireless PCI card. I have just installed Feisty Fawn (I also had this same issue with Edgy Eft) and there is no support for my card. I went to the Trendnet site, and there are no linux drivers, for my card. Am I just stuck buying a new card, or is there some linux magic, that you gurus of the Terminal, can help me with?  ](*,)


Also, I am running an AMD based x86 PC, and I am dual-booting Feisty Fawn and Windows XP Pro.  Feisty Fawn is by itself on my hdb, and Windows is by itself on my hda, if that makes any difference.

You can try my madwifi procedure.  It worked for my 5006eg card.  A lot of times the kernel will support Atheros wireless cards out of box but other times it needs help.

[http://www.stchman.com/ath_drv.html](http://www.stchman.com/ath_drv.html)

I am going to assume that this card is built in or PCMCIA.  Madwifi does not support USB wireless cards.

---

