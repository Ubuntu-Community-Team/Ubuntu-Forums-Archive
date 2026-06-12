---
title: "level one wnc-0300USB wireless adapter"
date: 2007-12-30
forum: Networking &amp; Wireless
---

### Post by mgrogin on 2007-12-30
Ive installed Ubuntu 7.10 and have it set up as a dual boot with windows XP
I have a usb network adapter "level-one wnc-0300USB" hooked up 
( [http://www.levelone.eu/products3.php?idu=7001&id=1820](http://www.levelone.eu/products3.php?idu=7001&id=1820) )
the usb adapter works perfect on windows but doesn't seem to be detected on Ubuntu
Ive tried following different instructions to get it to work but I just can't get it to work
I don't really have much experience with Linux but here are some outputs I got:


_**lsusb**_


Bus 002 Device 003: ID 132a:1502 
Bus 002 Device 002: ID 0424:0140 Standard Microsystems Corp.
Bus 002 Device 001: ID 0000:0000 
Bus 001 Device 001: ID 0000:0000 



_**ifconfig**_

eth0      Link encap:Ethernet  HWaddr 00:50:FC:61:AA:3D 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0xa400

lo        Link encap:Local Loopback 
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)



_** iwconfig**_

lo        no wireless extensions.

eth0      no wireless extensions. 


**_ lspci_**

00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 12)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 12)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 12)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 12)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 12)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 12)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
02:0a.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)
02:0b.0 Multimedia audio controller: Ensoniq 5880 AudioPCI (rev 02)
02:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:0d.0 Communication controller: Conexant HCF 56k Data/Fax/Voice/Spkp Modem (rev 08)


_**dmesg**_

[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000000ffc0000 (usable)
[    0.000000]  BIOS-e820: 000000000ffc0000 - 000000000fff8000 (ACPI data)
[    0.000000]  BIOS-e820: 000000000fff8000 - 0000000010000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb80000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 255MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 65472) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    65472
[    0.000000]   HighMem     65472 ->    65472
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    65472
[    0.000000] On node 0 totalpages: 65472
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 479 pages used for memmap
[    0.000000]   Normal zone: 60897 pages, LIFO batch:15
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FF980 checksum 0
[    0.000000] ACPI: RSDP 000FF980, 0014 (r0 AMI   )
[    0.000000] ACPI: RSDT 0FFF0000, 002C (r1 D845HV WN84510A 20010730 MSFT     1011)
[    0.000000] ACPI: FACP 0FFF1000, 0074 (r1 D845HV HV84510A 20010730 MSFT     1011)
[    0.000000] ACPI: DSDT 0FFE0000, 2EFE (r1 D845HV HV84510A        4 MSFT  100000B)
[    0.000000] ACPI: FACS 0FFF8000, 0040
[    0.000000] ACPI: APIC 0FFF2000, 0068 (r1 D845HV HV84510A 20010730 MSFT     1011)
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:0 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 10000000:eec00000)
[    0.000000] Built 1 zonelists.  Total pages: 64961
[    0.000000] Kernel command line: root=UUID=840d753d-afca-4513-985c-ec4eebb2835d ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[    0.000000] Detected 1495.270 MHz processor.
[   23.931249] Console: colour VGA+ 80x25
[   23.931606] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[   23.931915] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[   23.943325] Memory: 247948k/261888k available (2015k kernel code, 13480k reserved, 916k data, 364k init, 0k highmem)
[   23.943344] virtual kernel memory layout:
[   23.943347]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   23.943351]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   23.943353]     vmalloc : 0xd0800000 - 0xff7fe000   ( 751 MB)
[   23.943355]     lowmem  : 0xc0000000 - 0xcffc0000   ( 255 MB)
[   23.943357]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   23.943359]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   23.943361]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   23.943366] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   23.943437] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   24.023372] Calibrating delay using timer specific routine.. 2993.75 BogoMIPS (lpj=5987503)
[   24.023421] Security Framework v1.0.0 initialized
[   24.023434] SELinux:  Disabled at boot.
[   24.023457] Mount-cache hash table entries: 512
[   24.023728] CPU: After generic identify, caps: 3febfbff 00000000 00000000 00000000 00000000 00000000 00000000
[   24.023751] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   24.023756] CPU: L2 cache: 256K
[   24.023761] CPU: Hyper-Threading is disabled
[   24.023765] CPU: After all inits, caps: 3febfbff 00000000 00000000 0000b080 00000000 00000000 00000000
[   24.023789] Compat vDSO mapped to ffffe000.
[   24.023814] Checking 'hlt' instruction... OK.
[   24.039612] SMP alternatives: switching to UP code
[   24.040064] Freeing SMP alternatives: 11k freed
[   24.040697] Early unpacking initramfs... done
[   24.638278] ACPI: Core revision 20070126
[   24.638390] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   24.642167] CPU0: Intel(R) Pentium(R) 4 CPU 1500MHz stepping 0a
[   24.642239] Total of 1 processors activated (2993.75 BogoMIPS).
[   24.642397] ENABLING IO-APIC IRQs
[   24.642647] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   24.786532] Brought up 1 CPUs
[   24.786799] Booting paravirtualized kernel on bare hardware
[   24.786911] Time: 14:06:58  Date: 11/25/107
[   24.786965] NET: Registered protocol family 16
[   24.787204] EISA bus registered
[   24.787235] ACPI: bus type pci registered
[   24.787472] PCI: PCI BIOS revision 2.10 entry at 0xfda95, last bus=2
[   24.787476] PCI: Using configuration type 1
[   24.787479] Setting up standard PCI resources
[   24.790208] ACPI: EC: Look up EC in DSDT
[   24.796365] ACPI: Interpreter enabled
[   24.796376] ACPI: (supports S0 S1 S4 S5)
[   24.796412] ACPI: Using IOAPIC for interrupt routing
[   24.806155] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   24.806191] PCI: Probing PCI hardware (bus 00)
[   24.806570] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[   24.806576] PCI quirk: region 0500-053f claimed by ICH4 GPIO
[   24.807431] PCI: Transparent bridge - 0000:00:1e.0
[   24.807480] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   24.807654] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[   24.810141] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   24.810310] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   24.810573] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   24.810742] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   24.810902] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   24.811064] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   24.811225] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   24.811385] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   24.811674] ACPI: Power Resource [FDDP] (off)
[   24.811729] ACPI: Power Resource [URP1] (off)
[   24.811781] ACPI: Power Resource [URP2] (off)
[   24.811833] ACPI: Power Resource [LPTP] (off)
[   24.811865] Linux Plug and Play Support v0.97 (c) Adam Belay
[   24.811893] pnp: PnP ACPI init
[   24.811928] ACPI: bus type pnp registered
[   24.817984] pnp: PnP ACPI: found 13 devices
[   24.817992] ACPI: ACPI bus type pnp unregistered
[   24.818002] PnPBIOS: Disabled by ACPI PNP
[   24.818122] PCI: Using ACPI for IRQ routing
[   24.818129] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   24.822636] NET: Registered protocol family 8
[   24.822640] NET: Registered protocol family 20
[   24.822845] pnp: 00:0c: iomem range 0x0-0x9ffff could not be reserved
[   24.822852] pnp: 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[   24.822858] pnp: 00:0c: iomem range 0x100000-0xfffffff could not be reserved
[   24.822864] pnp: 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
[   24.826413] Time: tsc clocksource has been installed.
[   24.853575] PCI: Bridge: 0000:00:01.0
[   24.853578]   IO window: disabled.
[   24.853586]   MEM window: fc900000-fe9fffff
[   24.853592]   PREFETCH window: e4600000-f46fffff
[   24.853606] PCI: Bridge: 0000:00:1e.0
[   24.853611]   IO window: d000-dfff
[   24.853619]   MEM window: fea00000-feafffff
[   24.853626]   PREFETCH window: f4700000-f47fffff
[   24.853653] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   24.853680] NET: Registered protocol family 2
[   24.890436] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[   24.890534] TCP established hash table entries: 8192 (order: 4, 98304 bytes)
[   24.890676] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[   24.890779] TCP: Hash tables configured (established 8192 bind 8192)
[   24.890783] TCP reno registered
[   24.902636] checking if image is initramfs...<6>Switched to high resolution mode on CPU 0
[   25.458259]  it is
[   26.083868] Freeing initrd memory: 7352k freed
[   26.084683] audit: initializing netlink socket (disabled)
[   26.084713] audit(1198591618.780:1): initialized
[   26.089373] VFS: Disk quotas dquot_6.5.1
[   26.089506] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   26.089752] io scheduler noop registered
[   26.089758] io scheduler anticipatory registered
[   26.089761] io scheduler deadline registered
[   26.089807] io scheduler cfq registered (default)
[   26.089874] Boot video device is 0000:01:00.0
[   26.090271] isapnp: Scanning for PnP cards...
[   26.446593] isapnp: No Plug & Play device found
[   26.549954] Real Time Clock Driver v1.12ac
[   26.550146] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   26.550279] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   26.550829] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   26.552890] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   26.553709] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   26.556142] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   26.556759] input: Macintosh mouse button emulation as /class/input/input0
[   26.556969] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   26.559999] serio: i8042 KBD port at 0x60,0x64 irq 1
[   26.560012] serio: i8042 AUX port at 0x60,0x64 irq 12
[   26.560471] mice: PS/2 mouse device common for all mice
[   26.560774] EISA: Probing bus 0 at eisa.0
[   26.560824] EISA: Detected 0 cards.
[   26.561034] TCP cubic registered
[   26.561062] NET: Registered protocol family 1
[   26.561111] Using IPI No-Shortcut mode
[   26.561463]   Magic number: 3:465:132
[   26.561769]   hash matches device device:07
[   26.562724] Freeing unused kernel memory: 364k freed
[   26.632266] input: AT Translated Set 2 keyboard as /class/input/input1
[   28.037741] AppArmor: AppArmor initialized<5>audit(1198591620.780:2):  type=1505 info="AppArmor initialized" pid=1178
[   28.057804] fuse init (API version 7.8)
[   28.069324] Failure registering capabilities with primary security module.
[   28.099174] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   29.560952] SCSI subsystem initialized
[   29.572858] libata version 2.21 loaded.
[   29.576618] ata_piix 0000:00:1f.1: version 2.11
[   29.576725] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   29.576913] scsi0 : ata_piix
[   29.577022] scsi1 : ata_piix
[   29.577233] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14
[   29.577239] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15
[   29.629797] usbcore: registered new interface driver usbfs
[   29.629857] usbcore: registered new interface driver hub
[   29.629911] usbcore: registered new device driver usb
[   29.631875] USB Universal Host Controller Interface driver v3.0
[   29.741397] ata1.00: ATA-5: WDC WD400AB-00CMB0, 05.04E05, max UDMA/100
[   29.741406] ata1.00: 78165360 sectors, multi 16: LBA
[   29.757350] ata1.00: configured for UDMA/100
[   29.923769] Floppy drive(s): fd0 is 1.44M
[   29.969631] FDC 0 is a post-1991 82077
[   29.998645] 8139too Fast Ethernet driver 0.9.28
[   30.231963] ata2.00: ATAPI: YAMAHA  CRW2200E, 1.0D, max UDMA/33
[   30.231977] ata2.01: ATAPI: HL-DT-ST CD-ROM GCR-8520B, 1.00, max MWDMA2
[   30.395758] ata2.00: configured for UDMA/33
[   30.567419] ata2.01: configured for MWDMA2
[   30.567703] scsi 0:0:0:0: Direct-Access     ATA      WDC WD400AB-00CM 05.0 PQ: 0 ANSI: 5
[   30.569035] scsi 1:0:0:0: CD-ROM            YAMAHA   CRW2200E         1.0D PQ: 0 ANSI: 2
[   30.570091] scsi 1:0:1:0: CD-ROM            HL-DT-ST CD-ROM GCR-8520B 1.00 PQ: 0 ANSI: 5
[   30.577117] ACPI: PCI Interrupt 0000:00:1f.2[D] -> GSI 19 (level, low) -> IRQ 16
[   30.577146] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   30.577154] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[   30.577529] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[   30.577585] uhci_hcd 0000:00:1f.2: irq 16, io base 0x0000ef40
[   30.577857] usb usb1: configuration #1 chosen from 1 choice
[   30.577908] hub 1-0:1.0: USB hub found
[   30.577928] hub 1-0:1.0: 2 ports detected
[   30.615126] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   30.618174] sd 0:0:0:0: [sda] Write Protect is off
[   30.618183] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   30.618255] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   30.618390] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   30.618412] sd 0:0:0:0: [sda] Write Protect is off
[   30.618416] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   30.618451] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   30.618463]  sda: sda1 sda2 sda3 < sda5 >
[   30.662572] sd 0:0:0:0: [sda] Attached SCSI disk
[   30.672302] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   30.672750] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   30.673156] scsi 1:0:1:0: Attached scsi generic sg2 type 5
[   30.679359] ACPI: PCI Interrupt 0000:00:1f.4[C] -> GSI 23 (level, low) -> IRQ 17
[   30.679382] PCI: Setting latency timer of device 0000:00:1f.4 to 64
[   30.679388] uhci_hcd 0000:00:1f.4: UHCI Host Controller
[   30.679442] uhci_hcd 0000:00:1f.4: new USB bus registered, assigned bus number 2
[   30.679483] uhci_hcd 0000:00:1f.4: irq 17, io base 0x0000ef80
[   30.679692] usb usb2: configuration #1 chosen from 1 choice
[   30.679752] hub 2-0:1.0: USB hub found
[   30.679775] hub 2-0:1.0: 2 ports detected
[   30.733509] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   30.733522] Uniform CD-ROM driver Revision: 3.20
[   30.734160] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   30.741111] sr1: scsi3-mmc drive: 52x/52x cd/rw xa/form2 cdda tray
[   30.741768] sr 1:0:1:0: Attached scsi CD-ROM sr1
[   30.783446] ACPI: PCI Interrupt 0000:02:0a.0[A] -> GSI 22 (level, low) -> IRQ 18
[   30.837429] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[18]  MMIO=[feaff800-feafffff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[   30.845198] ACPI: PCI Interrupt 0000:02:0c.0[A] -> GSI 17 (level, low) -> IRQ 19
[   30.845680] eth0: RealTek RTL8139 at 0xd084c400, 00:50:fc:61:aa:3d, IRQ 19
[   30.845685] eth0:  Identified 8139 chip type 'RTL-8139C'
[   30.853069] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   31.038652] usb 2-2: new full speed USB device using uhci_hcd and address 2
[   31.192996] usb 2-2: configuration #1 chosen from 1 choice
[   31.195936] hub 2-2:1.0: USB hub found
[   31.198830] hub 2-2:1.0: 4 ports detected
[   31.288767] Attempting manual resume
[   31.288775] swsusp: Resume From Partition 8:5
[   31.288779] PM: Checking swsusp image.
[   31.289074] PM: Resume from disk failed.
[   31.362393] kjournald starting.  Commit interval 5 seconds
[   31.362424] EXT3-fs: mounted filesystem with ordered data mode.
[   31.511439] usb 2-2.1: new full speed USB device using uhci_hcd and address 3
[   31.766152] usb 2-2.1: configuration #1 chosen from 1 choice
[   32.113497] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011060d1c98099f]
[   42.752096] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   42.755542] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   42.955790] Linux agpgart interface v0.102 (c) Dave Jones
[   42.965409] intel_rng: Firmware space is locked read-only. <4>intel_rng: If you can't or
[   42.965414]  don't want to <4>intel_rng: disable this in firmware setup, and <4>intel_rng: if
[   42.965417]  you are certain that your <4>intel_rng: system has a functional
[   42.965419]  RNG, try<4>intel_rng: using the 'no_fwh_detect' option.
[   42.997271] iTCO_vendor_support: vendor-support=0
[   42.999356] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   42.999549] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[   42.999563] iTCO_wdt: No card detected
[   43.410229] agpgart: Detected an Intel 845G Chipset.
[   43.414624] agpgart: AGP aperture is 64M @ 0xf8000000
[   44.800828] input: PC Speaker as /class/input/input2
[   45.037641] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
[   45.088724] parport_pc 00:0a: reported by Plug and Play ACPI
[   45.088816] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   45.810808] ACPI: PCI Interrupt 0000:02:0b.0[A] -> GSI 23 (level, low) -> IRQ 17
[   47.359072] lp0: using parport0 (interrupt-driven).
[   47.480299] Adding 746980k swap on /dev/sda5.  Priority:-1 extents:1 across:746980k
[   47.870565] EXT3 FS on sda2, internal journal
[   49.594098] input: Power Button (FF) as /class/input/input4
[   49.603493] ACPI: Power Button (FF) [PWRF]
[   49.663052] input: Power Button (CM) as /class/input/input5
[   49.663603] ACPI: Power Button (CM) [PBTN]
[   49.819991] No dock devices found.
[   52.200510] eth0: link down
[   52.215317] ppdev: user-space parallel port driver
[   52.526285] audit(1198584446.141:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4570 profile="/usr/sbin/cupsd"
[   52.686107] apm: BIOS version 1.2 Flags 0x0b (Driver version 1.16ac)
[   52.686117] apm: overridden by ACPI.
[   53.077156] Failure registering capabilities with primary security module.
[   53.320137] Bluetooth: Core ver 2.11
[   53.320383] NET: Registered protocol family 31
[   53.320388] Bluetooth: HCI device and connection manager initialized
[   53.320396] Bluetooth: HCI socket layer initialized
[   53.344892] Bluetooth: L2CAP ver 2.8
[   53.344901] Bluetooth: L2CAP socket layer initialized
[   53.395747] Bluetooth: RFCOMM socket layer initialized
[   53.395951] Bluetooth: RFCOMM TTY layer initialized
[   53.395957] Bluetooth: RFCOMM ver 1.8
[  141.040559] UDF-fs: No VRS found
[  141.169320] ISO 9660 Extensions: Microsoft Joliet Level 3
[  141.232646] ISO 9660 Extensions: RRIP_1991A 


_**uname -a**_

Linux grogin-Upstairs-desktop 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux



[B][I]I hope you can help me
Thank you[/I][/B]

---

### Post by Hightide on 2008-01-04
You could try this thread to see if your device is supported by ubuntu

[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

---

