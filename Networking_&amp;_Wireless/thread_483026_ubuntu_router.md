---
title: "ubuntu router"
date: 2007-06-24
forum: Networking &amp; Wireless
---

### Post by survient on 2007-06-24
Ok, been trying for the past few week to set up a router on ubuntu using firestarter, with two NIC adapters, eth0(internet) and eth1(LAN). Whenever it's just eth0 enabled, the net works fine. But as soon as I enable eth1, the internet goes down. I've specified in firestarter which is which, enable DHCP going to eth1, and still nothing. 

route -n gives me 

(internet doesn't work)
when eth0 is enabled, and eth1 is unchecked it is:
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
192.168.0.0 0.0.0.0 255.255.255.0 U 0 0 0 eth1
169.254.0.0 0.0.0.0 255.255.0.0 U 1000 0 0 eth0
192.168.0.0 0.0.0.0 255.255.0.0 U 0 0 0 eth0
0.0.0.0 192.168.0.2 0.0.0.0 UG 0 0 0 eth0

(internet works)
when eth0 is enabled, and eth1 is set to roaming mode it is:
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
169.254.0.0 0.0.0.0 255.255.0.0 U 1000 0 0 eth0
192.168.0.0 0.0.0.0 255.255.0.0 U 0 0 0 eth0
0.0.0.0 192.168.0.2 0.0.0.0 UG 0 0 0 eth0

(internet doesn't work)
when eth0 is enabled, and eth1 is enabled with static IP 192.168.0.1, and subnet mask 255.255.255.0 it is:
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
192.168.0.0 0.0.0.0 255.255.255.0 U 0 0 0 eth1
169.254.0.0 0.0.0.0 255.255.0.0 U 1000 0 0 eth1
192.168.0.0 0.0.0.0 255.255.0.0 U 0 0 0 eth0
0.0.0.0 192.168.0.2 0.0.0.0 UG 0 0 0 eth0

and dmesg

[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e8000 size: 0000000000004000 end: 00000000000ec000 type: 4
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 0000000017e00000 end: 0000000017f00000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 00000000fffc0000 size: 0000000000040000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e8000 - 00000000000ec000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000017f00000 (usable)
[    0.000000]  BIOS-e820: 00000000fffc0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 383MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 98048) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    98048
[    0.000000]   HighMem     98048 ->    98048
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    98048
[    0.000000] On node 0 totalpages: 98048
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 734 pages used for memmap
[    0.000000]   Normal zone: 93218 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 COMPAQ                                ) @ 0x000e8010
[    0.000000] ACPI: RSDT (v001 COMPAQ CARS6C31 0x00000001  0x00000000) @ 0x000e8080
[    0.000000] ACPI: FADT (v001 COMPAQ CARS6C31 0x00000001  0x00000000) @ 0x000e80cc
[    0.000000] ACPI: SSDT (v001 COMPAQ CARS6C3  0x00000001 MSFT 0x01000007) @ 0x000e8187
[    0.000000] ACPI: DSDT (v001 COMPAQ DSDTTBL  0x00000001 MSFT 0x01000007) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0xee08
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 17f00000:e80c0000)
[    0.000000] Detected 797.619 MHz processor.
[   15.695442] Built 1 zonelists.  Total pages: 97282
[   15.695451] Kernel command line: root=UUID=918dbdb2-adaf-46a4-8acc-8f27d1dd78ef ro quiet splash
[   15.695959] Local APIC disabled by BIOS -- you can enable it with "lapic"
[   15.695983] mapped APIC to ffffd000 (0130a000)
[   15.695993] Enabling fast FPU save and restore... done.
[   15.696000] Enabling unmasked SIMD FPU exception support... done.
[   15.696023] Initializing CPU#0
[   15.696130] PID hash table entries: 2048 (order: 11, 8192 bytes)
[   15.698144] Console: colour VGA+ 80x25
[   15.699753] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   15.701832] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   15.746845] Memory: 377656k/392192k available (1992k kernel code, 13940k reserved, 900k data, 328k init, 0k highmem)
[   15.746875] virtual kernel memory layout:
[   15.746878]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   15.746882]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   15.746885]     vmalloc : 0xd8800000 - 0xff7fe000   ( 623 MB)
[   15.746889]     lowmem  : 0xc0000000 - 0xd7f00000   ( 383 MB)
[   15.746893]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   15.746896]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[   15.746900]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[   15.746909] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   15.824054] Calibrating delay using timer specific routine.. 1596.64 BogoMIPS (lpj=3193293)
[   15.824168] Security Framework v1.0.0 initialized
[   15.824193] SELinux:  Disabled at boot.
[   15.824239] Mount-cache hash table entries: 512
[   15.824623] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   15.824659] CPU: L1 I cache: 16K, L1 D cache: 16K
[   15.824666] CPU: L2 cache: 128K
[   15.824675] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[   15.824707] Compat vDSO mapped to ffffe000.
[   15.824729] Remapping vsyscall page to ffffe000
[   15.824758] Checking 'hlt' instruction... OK.
[   15.840299] SMP alternatives: switching to UP code
[   15.840776] Freeing SMP alternatives: 11k freed
[   15.841345] Early unpacking initramfs... done
[   16.707627] ACPI: Core revision 20060707
[   16.709871] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   16.712644] ACPI: setting ELCR to 0200 (from 0828)
[   16.714639] CPU0: Intel Celeron (Coppermine) stepping 0a
[   16.714657] SMP motherboard not detected.
[   16.714664] Local APIC not detected. Using dummy APIC emulation.
[   16.714763] Brought up 1 CPUs
[   16.715411] Booting paravirtualized kernel on bare hardware
[   16.715692] Time:  9:30:08  Date: 05/24/107
[   16.715783] NET: Registered protocol family 16
[   16.716135] EISA bus registered
[   16.716154] ACPI: bus type pci registered
[   16.718087] PCI: PCI BIOS revision 2.10 entry at 0xfa134, last bus=1
[   16.718094] PCI: Using configuration type 1
[   16.718099] Setting up standard PCI resources
[   16.726766] ACPI: Interpreter enabled
[   16.726780] ACPI: Using PIC for interrupt routing
[   16.728750] ACPI: PCI Interrupt Link [LNKA] (IRQs *3 4 5 6 7 10 11 15)
[   16.729486] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 15)
[   16.730208] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 *11 15)
[   16.730989] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 15)
[   16.731457] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   16.731577] PCI: Probing PCI hardware (bus 00)
[   16.732111] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[   16.732778] Boot video device is 0000:00:01.0
[   16.732930] PCI quirk: region ee00-ee7f claimed by ICH4 ACPI/GPIO/TCO
[   16.732939] PCI quirk: region ee80-eebf claimed by ICH4 GPIO
[   16.733596] PCI: Transparent bridge - 0000:00:1e.0
[   16.733650] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   16.742321] Linux Plug and Play Support v0.97 (c) Adam Belay
[   16.742362] pnp: PnP ACPI init
[   16.751676] pnp: PnP ACPI: found 14 devices
[   16.751693] PnPBIOS: Disabled by ACPI PNP
[   16.751861] PCI: Using ACPI for IRQ routing
[   16.751870] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   16.781627] NET: Registered protocol family 8
[   16.781635] NET: Registered protocol family 20
[   16.782867] pnp: 00:02: ioport range 0x3f7-0x3f7 has been reserved
[   16.782880] pnp: 00:02: ioport range 0x4d0-0x4d1 has been reserved
[   16.782888] pnp: 00:02: ioport range 0x400-0x47f has been reserved
[   16.784075] PCI: Ignore bogus resource 6 [0:0] of 0000:00:01.0
[   16.784104] PCI: Bridge: 0000:00:1e.0
[   16.784111]   IO window: 1000-1fff
[   16.784123]   MEM window: 40000000-402fffff
[   16.784131]   PREFETCH window: 20000000-200fffff
[   16.784158] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   16.784241] NET: Registered protocol family 2
[   16.819658] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   16.819932] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   16.820502] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[   16.820872] TCP: Hash tables configured (established 16384 bind 8192)
[   16.820882] TCP reno registered
[   16.831862] checking if image is initramfs... it is
[   18.417392] Freeing initrd memory: 6766k freed
[   18.418804] audit: initializing netlink socket (disabled)
[   18.418846] audit(1182677409.908:1): initialized
[   18.419272] VFS: Disk quotas dquot_6.5.1
[   18.419338] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   18.419488] io scheduler noop registered
[   18.419498] io scheduler anticipatory registered
[   18.419504] io scheduler deadline registered
[   18.419538] io scheduler cfq registered (default)
[   18.420317] isapnp: Scanning for PnP cards...
[   18.773331] isapnp: No Plug & Play device found
[   18.945530] Real Time Clock Driver v1.12ac
[   18.945693] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   18.945964] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   18.949160] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   18.950302] mice: PS/2 mouse device common for all mice
[   18.952399] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   18.952940] input: Macintosh mouse button emulation as /class/input/input0
[   18.953084] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   18.953097] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   18.953667] PNP: PS/2 Controller [PNP0303:KBD,PNP0f0e:PS2M] at 0x60,0x64 irq 1,12
[   18.956859] serio: i8042 KBD port at 0x60,0x64 irq 1
[   18.956875] serio: i8042 AUX port at 0x60,0x64 irq 12
[   18.957401] EISA: Probing bus 0 at eisa.0
[   18.957423] Cannot allocate resource for EISA slot 1
[   18.957429] Cannot allocate resource for EISA slot 2
[   18.957456] EISA: Detected 0 cards.
[   18.987685] TCP cubic registered
[   18.987713] NET: Registered protocol family 1
[   18.987779] Using IPI No-Shortcut mode
[   18.988063] ACPI: (supports S0 S1 S5)
[   18.988172]   Magic number: 11:234:526
[   18.989959] Freeing unused kernel memory: 328k freed
[   18.990052] Time: tsc clocksource has been installed.
[   19.002475] input: AT Translated Set 2 keyboard as /class/input/input1
[   20.768868] Capability LSM initialized
[   20.929240] ACPI: Invalid PBLK length [5]
[   22.836516] SCSI subsystem initialized
[   22.862158] libata version 2.20 loaded.
[   22.878292] ata_piix 0000:00:1f.1: version 2.10ac1
[   22.878360] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   22.878538] ata1: PATA max UDMA/66 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00012020 irq 14
[   22.878645] ata2: PATA max UDMA/66 cmd 0x00010170 ctl 0x00010376 bmdma 0x00012028 irq 15
[   22.878696] scsi0 : ata_piix
[   22.923036] usbcore: registered new interface driver usbfs
[   22.923107] usbcore: registered new interface driver hub
[   22.923207] usbcore: registered new device driver usb
[   22.927641] USB Universal Host Controller Interface driver v3.0
[   23.039780] ata1.00: ATA-4: ST320413A, 3.39, max UDMA/100
[   23.039795] ata1.00: 39102336 sectors, multi 8: LBA 
[   23.047706] ata1.00: configured for UDMA/66
[   23.047739] scsi1 : ata_piix
[   23.275773] Linux Tulip driver version 1.1.14 (December 15, 2004)
[   23.292705] via-rhine.c:v1.10-LK1.4.2 Sept-11-2006 Written by Donald Becker
[   23.367583] ata2.00: ATAPI, max MWDMA2, CDB intr
[   23.531476] ata2.00: configured for MWDMA2
[   23.539297] scsi 0:0:0:0: Direct-Access     ATA      ST320413A        3.39 PQ: 0 ANSI: 5
[   23.540020] scsi 1:0:0:0: CD-ROM            COMPAQ   CD-ROM LTN486S   YQS8 PQ: 0 ANSI: 5
[   23.541233] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[   23.541249] PCI: setting IRQ 11 as level-triggered
[   23.541256] ACPI: PCI Interrupt 0000:00:1f.2[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   23.541286] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   23.541296] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[   23.541636] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[   23.541696] uhci_hcd 0000:00:1f.2: irq 11, io base 0x0000eec0
[   23.542090] usb usb1: configuration #1 chosen from 1 choice
[   23.542171] hub 1-0:1.0: USB hub found
[   23.542200] hub 1-0:1.0: 2 ports detected
[   23.579985] FDC 0 is a post-1991 82077
[   23.633004] SCSI device sda: 39102336 512-byte hdwr sectors (20020 MB)
[   23.633106] sda: Write Protect is off
[   23.633113] sda: Mode Sense: 00 3a 00 00
[   23.633160] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.633383] SCSI device sda: 39102336 512-byte hdwr sectors (20020 MB)
[   23.633410] sda: Write Protect is off
[   23.633417] sda: Mode Sense: 00 3a 00 00
[   23.633458] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.633468]  sda:PCI: Enabling device 0000:01:09.0 (0004 -> 0007)
[   23.644925] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[   23.644938] PCI: setting IRQ 5 as level-triggered
[   23.644945] ACPI: PCI Interrupt 0000:01:09.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[   23.645630] tulip0:  MII transceiver #1 config 3100 status 7869 advertising 05e1.
[   23.652558] eth0: ADMtek Comet rev 17 at Port 0x1400, EEPROM not present, 00:4C:69:6E:75:79, IRQ 5.
[   23.653364] PCI: Enabling device 0000:01:0a.0 (0004 -> 0007)
[   23.654054] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[   23.654066] ACPI: PCI Interrupt 0000:01:0a.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   23.659712] eth1: VIA Rhine III at 0x11800, 00:15:e9:80:bc:15, IRQ 11.
[   23.660443] eth1: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
[   23.671507]  sda1 sda2 sda3
[   23.705763] sd 0:0:0:0: Attached scsi disk sda
[   23.721281] sr0: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
[   23.721300] Uniform CD-ROM driver Revision: 3.20
[   23.722070] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   23.739236] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   23.739826] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   23.886964] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   24.040606] usb 1-1: configuration #1 chosen from 1 choice
[   24.042568] hub 1-1:1.0: USB hub found
[   24.045421] hub 1-1:1.0: 4 ports detected
[   24.184005] Attempting manual resume
[   24.184017] swsusp: Resume From Partition 8:2
[   24.184022] PM: Checking swsusp image.
[   24.184578] PM: Resume from disk failed.
[   24.266858] kjournald starting.  Commit interval 5 seconds
[   24.266906] EXT3-fs: mounted filesystem with ordered data mode.
[   24.372109] usb 1-1.4: new low speed USB device using uhci_hcd and address 3
[   24.511198] usb 1-1.4: configuration #1 chosen from 1 choice
[   41.453591] NET: Registered protocol family 17
[   42.613061] 0000:01:09.0: tulip_stop_rxtx() failed (CSR5 0xfc664010 CSR6 0xff972113)
[   42.613081] eth0: Setting full-duplex based on MII#1 link partner capability of 45e1.
[   43.666168] intel_rng: FWH not detected
[   43.748680] iTCO_vendor_support: vendor-support=0
[   43.753261] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   43.753637] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[   43.753655] iTCO_wdt: No card detected
[   44.467996] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   44.958086] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   44.975822] Linux agpgart interface v0.102 (c) Dave Jones
[   44.982896] agpgart: Detected an Intel i810 E Chipset.
[   44.996455] agpgart: AGP aperture is 64M @ 0x44000000
[   45.377754] pnp: Device 00:09 activated.
[   45.377769] parport: PnPBIOS parport detected.
[   45.377828] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   45.696832] input: PC Speaker as /class/input/input2
[   45.709423] i810_smbus 0000:00:01.0: i810/i815 i2c device found.
[   46.174665] usbcore: registered new interface driver hiddev
[   46.389914] ath_hal: module license 'Proprietary' taints kernel.
[   46.395136] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   46.433128] input: Logitech USB-PS/2 Optical Mouse as /class/input/input3
[   46.433594] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1f.2-1.4
[   46.433650] usbcore: registered new interface driver usbhid
[   46.433660] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   46.634745] wlan: 0.8.4.2 (0.9.3)
[   46.725511] ath_pci: 0.9.4.5 (0.9.3)
[   46.725714] PCI: Enabling device 0000:01:08.0 (0004 -> 0006)
[   46.726406] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 3
[   46.726418] PCI: setting IRQ 3 as level-triggered
[   46.726425] ACPI: PCI Interrupt 0000:01:08.0[A] -> Link [LNKA] -> GSI 3 (level, low) -> IRQ 3
[   46.974292] ath_rate_sample: 1.2 (0.9.3)
[   46.975262] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   46.975280] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   46.975303] wifi0: turboG rates: 6Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   46.975319] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   46.975330] wifi0: mac 5.6 phy 4.1 radio 4.6
[   46.975350] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   46.975355] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   46.975361] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   46.975367] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   46.975372] wifi0: Use hw queue 8 for CAB traffic
[   46.975378] wifi0: Use hw queue 9 for beacons
[   47.004382] wifi0: Atheros 5212: mem=0x40000000, irq=3
[   47.093167] ACPI: PCI Interrupt 0000:01:05.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[   48.420250] lp0: using parport0 (interrupt-driven).
[   48.534318] Adding 859468k swap on /dev/disk/by-uuid/58128143-16d4-4d69-b4c2-97117ecc734f.  Priority:-1 extents:1 across:859468k
[   48.709415] EXT3 FS on sda1, internal journal
[   49.032463] NET: Registered protocol family 10
[   49.032792] lo: Disabled Privacy Extensions
[   49.408492] kjournald starting.  Commit interval 5 seconds
[   49.408917] EXT3 FS on sda3, internal journal
[   49.408933] EXT3-fs: mounted filesystem with ordered data mode.
[   50.906322] ibm_acpi: ec object not found
[   51.010011] Using specific hotkey driver
[   51.260130] No dock devices found.
[   51.361545] input: Power Button (FF) as /class/input/input4
[   51.362365] ACPI: Power Button (FF) [PWRF]
[   51.397547] input: Power Button (CM) as /class/input/input5
[   51.398367] ACPI: Power Button (CM) [PBTN]
[   51.659798] pcc_acpi: loading...
[   59.404329] eth0: no IPv6 routers present
[   60.385474] eth1: link down
[   60.386125] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   62.748574] ppdev: user-space parallel port driver
[   67.390093] apm: BIOS not found.
[   70.729627] Bluetooth: Core ver 2.11
[   70.729863] NET: Registered protocol family 31
[   70.729871] Bluetooth: HCI device and connection manager initialized
[   70.729882] Bluetooth: HCI socket layer initialized
[   70.953914] Bluetooth: L2CAP ver 2.8
[   70.953929] Bluetooth: L2CAP socket layer initialized
[   70.966376] Bluetooth: RFCOMM socket layer initialized
[   70.966423] Bluetooth: RFCOMM TTY layer initialized
[   70.966429] Bluetooth: RFCOMM ver 1.8
[   79.915234] eth0: no IPv6 routers present
[  194.919500] 0000:01:09.0: tulip_stop_rxtx() failed (CSR5 0xfc06c012 CSR6 0xff970111)
[  195.142669] eth1: link down
[  195.143323] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  198.065841] 0000:01:09.0: tulip_stop_rxtx() failed (CSR5 0xfc664010 CSR6 0xff972113)
[  198.065869] eth0: Setting full-duplex based on MII#1 link partner capability of 45e1.
[  220.042038] eth0: no IPv6 routers present
[  275.488421] 0000:01:09.0: tulip_stop_rxtx() failed (CSR5 0xfc06c012 CSR6 0xff970111)
[  278.634605] 0000:01:09.0: tulip_stop_rxtx() failed (CSR5 0xfc664010 CSR6 0xff972113)
[  278.634632] eth0: Setting full-duplex based on MII#1 link partner capability of 45e1.
[  286.473780] 0000:01:09.0: tulip_stop_rxtx() failed (CSR5 0xfc06c012 CSR6 0xff970111)
[  289.623605] 0000:01:09.0: tulip_stop_rxtx() failed (CSR5 0xfc664010 CSR6 0xff972113)
[  289.623628] eth0: Setting full-duplex based on MII#1 link partner capability of 45e1.
[  292.930542] ip_tables: (C) 2000-2006 Netfilter Core Team
[  293.192794] Netfilter messages via NETLINK v0.30.
[  293.249583] nf_conntrack version 0.5.0 (3064 buckets, 24512 max)
[  300.071055] eth0: no IPv6 routers present

---

### Post by Biochem on 2007-06-29
I have the exactly the same problem. 
pppoeconf set eth1 in roaming mode and the internet works. However I can't figure out how to enable my two nic simultaneously.


Anybody have suggestions how to activate two network card at the same time?
Thanks

---

### Post by Biochem on 2007-06-29
I figured it out!
In the network configuration applet, I set my nic connected to the internet to ipv4ll. Then I ran pppoeconf again. Now I can access my lan and my wan simultaneously.

I hope it help you survient.

---

