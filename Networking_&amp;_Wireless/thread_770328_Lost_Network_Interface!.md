---
title: "Lost Network Interface!"
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by TrevP on 2008-04-27
Hi,

Since I have upgraded to Hardy, I've been unable to get my linksys wireless card (broadcom chipset)to operate with the B43 firmware. I tried using ndiswrapper using a fix suggested elsewhere in this forum [here]("http://https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff") and it worked. However, on re-booting my computer, there is no wireless interface visible. The wireless card is working and I can now see my router when I click on edit wireless networks- but I can't connect to it because the computer doesn't see my wireless interface. When I run iwconfig, I just get this:

trev@trev-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

trev@trev-desktop:~$ 

Any ideas on how to fix this would be much appreciated.

Trev

---

### Post by TrevP on 2008-04-27
For further information, the output of ifconfig is as follows:

trev@trev-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:fc:ab:09:b6  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:fcff:feab:9b6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2757 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2861 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2659847 (2.5 MB)  TX bytes:410308 (400.6 KB)
          Interrupt:19 Base address:0x1800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1486 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1486 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:74300 (72.5 KB)  TX bytes:74300 (72.5 KB)

trev@trev-desktop:~$ 

So the infterface is UP and working, but is not being recognised either by the nm-applet or by the network settings program.

Trev

---

### Post by alehorb on 2008-04-27
dmesg & lspci are your friends ! Post the outputs here,please.

                                                  :lolflag:

---

### Post by TrevP on 2008-04-27
lspci:

trev@trev-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 81)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1d)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1d)
00:07.4 SMBus: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
00:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0e.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
00:0f.0 Modem: PCTel Inc HSP MicroModem 56 (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) (rev 01)
trev@trev-desktop:~$ 

dmesg:

rev@trev-desktop:~$ dmesg
[    0.000000] Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000ce000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000000fef0000 (usable)
[    0.000000]  BIOS-e820: 000000000fef0000 - 000000000feff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000000feff000 - 000000000ff00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000000ff00000 - 0000000010000000 (usable)
[    0.000000]  BIOS-e820: 00000000fffc0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 256MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 65536) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    65536
[    0.000000]   HighMem     65536 ->    65536
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    65536
[    0.000000] On node 0 totalpages: 65536
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 480 pages used for memmap
[    0.000000]   Normal zone: 60960 pages, LIFO batch:15
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7030 checksum 0
[    0.000000] ACPI: RSDP 000F7030, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 0FEFA92A, 0030 (r1 PTLTD    RSDT    6040000  LTP        0)
[    0.000000] ACPI: FACP 0FEFEF14, 0074 (r1 HP     Montana   6040000 PTL         1)
[    0.000000] ACPI: DSDT 0FEFA95A, 45BA (r1     HP  Montana  6040000 MSFT  100000D)
[    0.000000] ACPI: FACS 0FEFFFC0, 0040
[    0.000000] ACPI: APIC 0FEFEF88, 0050 (r1 PTLTD  	 APIC    6040000  LTP        0)
[    0.000000] ACPI: BOOT 0FEFEFD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x08] enabled)
[    0.000000] Processor #8 6:6 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 0, version 2, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ11 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 10000000:effc0000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000ce000
[    0.000000] swsusp: Registered nosave memory region: 00000000000ce000 - 00000000000d4000
[    0.000000] swsusp: Registered nosave memory region: 00000000000d4000 - 00000000000dc000
[    0.000000] swsusp: Registered nosave memory region: 00000000000dc000 - 0000000000100000
[    0.000000] swsusp: Registered nosave memory region: 000000000fef0000 - 000000000feff000
[    0.000000] swsusp: Registered nosave memory region: 000000000feff000 - 000000000ff00000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 65024
[    0.000000] Kernel command line: root=UUID=53b5090a-aa09-4e82-99c4-271344bc40fe ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[    0.000000] Detected 1532.912 MHz processor.
[21814.068647] Console: colour VGA+ 80x25
[21814.068653] console [tty0] enabled
[21814.068987] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[21814.069200] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[21814.080557] Memory: 247844k/262144k available (2157k kernel code, 13752k reserved, 998k data, 364k init, 0k highmem)
[21814.080569] virtual kernel memory layout:
[21814.080570]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[21814.080572]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[21814.080573]     vmalloc : 0xd0800000 - 0xff7fe000   ( 751 MB)
[21814.080575]     lowmem  : 0xc0000000 - 0xd0000000   ( 256 MB)
[21814.080576]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
[21814.080578]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
[21814.080579]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
[21814.080584] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[21814.080645] SLUB: Genslabs=11, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[21814.160677] Calibrating delay using timer specific routine.. 3068.92 BogoMIPS (lpj=6137841)
[21814.160728] Security Framework initialized
[21814.160739] SELinux:  Disabled at boot.
[21814.160769] AppArmor: AppArmor initialized
[21814.160775] Failure registering capabilities with primary security module.
[21814.160790] Mount-cache hash table entries: 512
[21814.160996] CPU: After generic identify, caps: 0383fbff c1cbfbff 00000000 00000000 00000000 00000000 00000000 00000000
[21814.161009] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[21814.161013] CPU: L2 Cache: 256K (64 bytes/line)
[21814.161018] CPU: After all inits, caps: 0383fbff c1cbfbff 00000000 00000420 00000000 00000000 00000000 00000000
[21814.161033] Compat vDSO mapped to ffffe000.
[21814.161052] Checking 'hlt' instruction... OK.
[21814.177021] SMP alternatives: switching to UP code
[21814.178607] Freeing SMP alternatives: 11k freed
[21814.178815] Early unpacking initramfs... done
[21814.634222] ACPI: Core revision 20070126
[21814.634399] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[21814.640715] CPU0: AMD Athlon(tm) XP 1800+ stepping 02
[21814.640750] Total of 1 processors activated (3068.92 BogoMIPS).
[21814.641518] ENABLING IO-APIC IRQs
[21814.641859] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[21814.788805] Brought up 1 CPUs
[21814.788893] CPU0 attaching sched-domain:
[21814.788897]  domain 0: span 01
[21814.788899]   groups: 01
[21814.789217] net_namespace: 64 bytes
[21814.789229] Booting paravirtualized kernel on bare hardware
[21814.789896] Time: 14:31:10  Date: 04/27/08
[21814.789952] NET: Registered protocol family 16
[21814.790270] EISA bus registered
[21814.790304] ACPI: bus type pci registered
[21814.798524] PCI: PCI BIOS revision 2.10 entry at 0xfd77e, last bus=1
[21814.798528] PCI: Using configuration type 1
[21814.798530] Setting up standard PCI resources
[21814.800891] ACPI: EC: Look up EC in DSDT
[21814.804932] ACPI: Interpreter enabled
[21814.804937] ACPI: (supports S0 S1 S3 S4 S5)
[21814.804957] ACPI: Using IOAPIC for interrupt routing
[21814.809455] ACPI: PCI Root Bridge [PCI0] (0000:00)
[21814.809798] PCI quirk: region 6800-687f claimed by vt82c686 HW-mon
[21814.809803] PCI quirk: region 0400-040f claimed by vt82c686 SMB
[21814.810150] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[21814.810364] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PPB_._PRT]
[21814.813478] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 14 15)
[21814.813586] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
[21814.813700] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 14 15)
[21814.813810] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *9 10 11 14 15)
[21814.813986] ACPI: PCI Interrupt Link [LNKU] (IRQs 3 4 6 9 14 15) *0
[21814.814161] ACPI: PCI Interrupt Link [LNKS] (IRQs 3 4 5 6 7 10 14 15) *0
[21814.814332] Linux Plug and Play Support v0.97 (c) Adam Belay
[21814.814382] pnp: PnP ACPI init
[21814.814394] ACPI: bus type pnp registered
[21814.816681] ACPI Error (dsopcode-0548): Field [ALB2] at 120 exceeds Buffer [CRSA] size 104 (bits) [20070126]
[21814.816690] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.PIB_.SIO0.LPT_._CRS] (Node cd9039d8), AE_AML_BUFFER_LIMIT
[21814.816806] ACPI Error (uteval-0233): Method execution failed [\_SB_.PCI0.PIB_.SIO0.LPT_._CRS] (Node cd9039d8), AE_AML_BUFFER_LIMIT
[21814.816816] pnp: PnPACPI: METHOD_NAME__CRS failure for PNP0401
[21814.817152] pnp: PnP ACPI: found 12 devices
[21814.817155] ACPI: ACPI bus type pnp unregistered
[21814.817162] PnPBIOS: Disabled by ACPI PNP
[21814.817638] PCI: Using ACPI for IRQ routing
[21814.817644] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[21814.828746] NET: Registered protocol family 8
[21814.828749] NET: Registered protocol family 20
[21814.828870] AppArmor: AppArmor Filesystem Enabled
[21814.832724] Time: tsc clocksource has been installed.
[21814.840794] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[21814.840798] system 00:08: ioport range 0x8000-0x807f has been reserved
[21814.840802] system 00:08: ioport range 0x6800-0x687f has been reserved
[21814.840806] system 00:08: ioport range 0x400-0x40f has been reserved
[21814.840812] system 00:08: iomem range 0xfffc0000-0xffffffff could not be reserved
[21814.840815] system 00:08: iomem range 0xfff80000-0xfffbffff has been reserved
[21814.840819] system 00:08: iomem range 0xfee00000-0xfee00fff has been reserved
[21814.840823] system 00:08: iomem range 0xfec00000-0xfec00fff has been reserved
[21814.871437] PCI: Bridge: 0000:00:01.0
[21814.871441]   IO window: 9000-9fff
[21814.871447]   MEM window: e0100000-e01fffff
[21814.871451]   PREFETCH window: e8000000-f7ffffff
[21814.871480] PCI: Setting latency timer of device 0000:00:01.0 to 64
[21814.871499] NET: Registered protocol family 2
[21814.908887] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[21814.909217] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[21814.909392] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[21814.909559] TCP: Hash tables configured (established 8192 bind 8192)
[21814.909563] TCP reno registered
[21814.920945] checking if image is initramfs... it is
[21815.372770] Switched to high resolution mode on CPU 0
[21815.766410] Freeing initrd memory: 7392k freed
[21815.766720] Simple Boot Flag at 0x36 set to 0x1
[21815.767561] audit: initializing netlink socket (disabled)
[21815.767587] audit(1209306670.580:1): initialized
[21815.770559] VFS: Disk quotas dquot_6.5.1
[21815.770668] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[21815.770897] io scheduler noop registered
[21815.770900] io scheduler anticipatory registered
[21815.770903] io scheduler deadline registered
[21815.770918] io scheduler cfq registered (default)
[21815.770945] Applying VIA southbridge workaround.
[21815.770950] PCI: VIA PCI bridge detected. Disabling DAC.
[21815.770955] PCI: Enabling Via external APIC routing
[21815.770990] Boot video device is 0000:01:00.0
[21815.771419] isapnp: Scanning for PnP cards...
[21816.125853] isapnp: No Plug & Play device found
[21816.166726] Real Time Clock Driver v1.12ac
[21816.166886] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[21816.167084] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[21816.168100] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[21816.168893] serial 00:0b: activated
[21816.169634] 00:0b: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[21816.169900] PCI: Enabling device 0000:00:0f.0 (0000 -> 0001)
[21816.169918] ACPI: PCI Interrupt 0000:00:0f.0[A] -> GSI 18 (level, low) -> IRQ 16
[21816.174230] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[21816.174334] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[21816.174504] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUS] at 0x60,0x64 irq 1,12
[21816.174915] serio: i8042 KBD port at 0x60,0x64 irq 1
[21816.174922] serio: i8042 AUX port at 0x60,0x64 irq 12
[21816.188774] mice: PS/2 mouse device common for all mice
[21816.188955] EISA: Probing bus 0 at eisa.0
[21816.188967] Cannot allocate resource for EISA slot 1
[21816.188993] Cannot allocate resource for EISA slot 6
[21816.189000] Cannot allocate resource for EISA slot 8
[21816.189003] EISA: Detected 0 cards.
[21816.189009] cpuidle: using governor ladder
[21816.189012] cpuidle: using governor menu
[21816.189237] NET: Registered protocol family 1
[21816.189282] Using IPI No-Shortcut mode
[21816.189338] registered taskstats version 1
[21816.189465]   Magic number: 4:977:536
[21816.189772] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[21816.189776] EDD information not available.
[21816.190535] Freeing unused kernel memory: 364k freed
[21816.214799] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[21817.527831] fuse init (API version 7.9)
[21818.296945] SCSI subsystem initialized
[21818.372526] libata version 3.00 loaded.
[21818.415542] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
[21818.415561] ACPI: PCI Interrupt 0000:00:07.1[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[21818.415570] PCI: VIA VLink IRQ fixup for 0000:00:07.1, from 0 to 10
[21818.415689] ACPI: PCI interrupt for device 0000:00:07.1 disabled
[21818.424665] pata_via 0000:00:07.1: version 0.3.3
[21818.424709] ACPI: PCI Interrupt 0000:00:07.1[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[21818.424718] PCI: VIA VLink IRQ fixup for 0000:00:07.1, from 0 to 10
[21818.456518] scsi0 : pata_via
[21818.488509] scsi1 : pata_via
[21818.489339] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1400 irq 14
[21818.489344] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1408 irq 15
[21818.502155] usbcore: registered new interface driver usbfs
[21818.502196] usbcore: registered new interface driver hub
[21818.520061] usbcore: registered new device driver usb
[21818.526778] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[21818.556535] USB Universal Host Controller Interface driver v3.0
[21818.653061] ata1.00: ATA-6: Maxtor 4D040H2, DAH017K0, max UDMA/100
[21818.653069] ata1.00: 80043264 sectors, multi 16: LBA 
[21818.669019] ata1.00: configured for UDMA/100
[21818.728633] Floppy drive(s): fd0 is 1.44M
[21818.748201] FDC 0 is a post-1991 82077
[21819.144890] ata2.00: ATAPI: TOSHIBA DVD-ROM SD-M1612, 1806, max UDMA/33
[21819.144922] ata2.01: ATAPI: SAMSUNG CD-R/RW DRIVE SW-224B, VE002R60, max MWDMA2
[21819.317652] ata2.00: configured for UDMA/33
[21819.480759] ata2.01: configured for MWDMA2
[21819.480991] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 4D040H2   DAH0 PQ: 0 ANSI: 5
[21819.486467] scsi 1:0:0:0: CD-ROM            TOSHIBA  DVD-ROM SD-M1612 1806 PQ: 0 ANSI: 5
[21819.487075] scsi 1:0:1:0: CD-ROM            SAMSUNG  CD-R/RW SW-224B  R206 PQ: 0 ANSI: 5
[21819.487409] 8139cp 0000:00:0d.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[21819.487416] 8139cp 0000:00:0d.0: Try the "8139too" driver instead.
[21819.490282] PCI: Enabling device 0000:00:0e.0 (0000 -> 0002)
[21819.490304] ACPI: PCI Interrupt 0000:00:0e.0[A] -> GSI 17 (level, low) -> IRQ 17
[21819.491908] 8139too Fast Ethernet driver 0.9.28
[21819.528537] ssb: Sonics Silicon Backplane found on PCI device 0000:00:0e.0
[21819.528795] ACPI: PCI Interrupt 0000:00:07.2[D] -> GSI 21 (level, low) -> IRQ 18
[21819.528814] uhci_hcd 0000:00:07.2: UHCI Host Controller
[21819.529380] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[21819.529428] uhci_hcd 0000:00:07.2: irq 18, io base 0x00001420
[21819.529672] usb usb1: configuration #1 chosen from 1 choice
[21819.529709] hub 1-0:1.0: USB hub found
[21819.529719] hub 1-0:1.0: 2 ports detected
[21819.632624] ACPI: PCI Interrupt 0000:00:07.3[D] -> GSI 21 (level, low) -> IRQ 18
[21819.632647] uhci_hcd 0000:00:07.3: UHCI Host Controller
[21819.632693] uhci_hcd 0000:00:07.3: new USB bus registered, assigned bus number 2
[21819.632723] uhci_hcd 0000:00:07.3: irq 18, io base 0x00001440
[21819.632913] usb usb2: configuration #1 chosen from 1 choice
[21819.632948] hub 2-0:1.0: USB hub found
[21819.632959] hub 2-0:1.0: 2 ports detected
[21819.727219] Driver 'sd' needs updating - please use bus_type methods
[21819.728028] sd 0:0:0:0: [sda] 80043264 512-byte hardware sectors (40982 MB)
[21819.728055] sd 0:0:0:0: [sda] Write Protect is off
[21819.728059] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[21819.728087] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[21819.728173] sd 0:0:0:0: [sda] 80043264 512-byte hardware sectors (40982 MB)
[21819.728188] sd 0:0:0:0: [sda] Write Protect is off
[21819.728191] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[21819.728215] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[21819.728220]  sda:PCI: Enabling device 0000:00:0d.0 (0000 -> 0003)
[21819.736732] ACPI: PCI Interrupt 0000:00:0d.0[A] -> GSI 16 (level, low) -> IRQ 19
[21819.737281] eth0: RealTek RTL8139 at 0x1800, 00:50:fc:ab:09:b6, IRQ 19
[21819.737285] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[21819.745577] Driver 'sr' needs updating - please use bus_type methods
[21819.747654]  sda1 sda2 sda3 < sda5 >
[21819.779317] sd 0:0:0:0: [sda] Attached SCSI disk
[21819.788551] sd 0:0:0:0: Attached scsi generic sg0 type 0
[21819.788586] sr 1:0:0:0: Attached scsi generic sg1 type 5
[21819.788612] scsi 1:0:1:0: Attached scsi generic sg2 type 5
[21819.797460] sr0: scsi3-mmc drive: 40x/48x cd/rw xa/form2 cdda tray
[21819.797472] Uniform CD-ROM driver Revision: 3.20
[21819.797572] sr 1:0:0:0: Attached scsi CD-ROM sr0
[21819.799894] sr1: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[21819.800007] sr 1:0:1:0: Attached scsi CD-ROM sr1
[21820.383294] Attempting manual resume
[21820.383302] swsusp: Resume From Partition 8:5
[21820.383304] PM: Checking swsusp image.
[21820.383617] PM: Resume from disk failed.
[21820.433007] kjournald starting.  Commit interval 5 seconds
[21820.433042] EXT3-fs: mounted filesystem with ordered data mode.
[21833.968289] input: PC Speaker as /devices/platform/pcspkr/input/input2
[21834.798367] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[21834.817514] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[21834.843635] Linux agpgart interface v0.102
[21834.867532] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input3
[21834.881969] parport_pc: VIA 686A/8231 detected
[21834.881977] parport_pc: probing current configuration
[21834.881995] parport_pc: Current parallel port base: 0x378
[21834.882073] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[21834.883977] agpgart: Detected VIA Twister-K/KT133x/KM133 chipset
[21834.888917] agpgart: AGP aperture is 64M @ 0xe4000000
[21835.051401] parport_pc: VIA parallel port: io=0x378, irq=7
[21835.283633] input: Power Button (FF) as /devices/virtual/input/input4
[21835.315451] ACPI: Power Button (FF) [PWRF]
[21835.315681] input: Power Button (CM) as /devices/virtual/input/input5
[21835.347366] ACPI: Power Button (CM) [PWRB]
[21837.459805] ACPI: PCI Interrupt 0000:00:07.5[C] -> GSI 22 (level, low) -> IRQ 20
[21837.459856] PCI: Setting latency timer of device 0000:00:07.5 to 64
[21841.259636] lp0: using parport0 (interrupt-driven).
[21841.330186] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[21841.336794] usbcore: registered new interface driver ndiswrapper
[21841.431202] Adding 725720k swap on /dev/sda5.  Priority:-1 extents:1 across:725720k
[21842.130865] EXT3 FS on sda2, internal journal
[21843.861988] ip_tables: (C) 2000-2006 Netfilter Core Team
[21844.586420] No dock devices found.
[21847.674773] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[21849.927977] [drm] Initialized drm 1.1.0 20060810
[21849.946949] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 19
[21849.947405] [drm] Initialized radeon 1.28.0 20060524 on minor 0
[21850.379564] ppdev: user-space parallel port driver
[21850.788992] audit(1209303106.668:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5206 profile="/usr/sbin/cupsd" namespace="default"
[21850.914226] apm: BIOS not found.
[21851.640395] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[21851.640425] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[21851.640462] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[21852.222193] [drm] Setting GART location based on new memory map
[21852.222212] [drm] Loading R200 Microcode
[21852.222254] [drm] writeback test succeeded in 1 usecs
[21852.904093] Bluetooth: Core ver 2.11
[21852.905602] NET: Registered protocol family 31
[21852.905611] Bluetooth: HCI device and connection manager initialized
[21852.905618] Bluetooth: HCI socket layer initialized
[21853.083293] Bluetooth: L2CAP ver 2.9
[21853.083303] Bluetooth: L2CAP socket layer initialized
[21853.095411] Bluetooth: RFCOMM socket layer initialized
[21853.095450] Bluetooth: RFCOMM TTY layer initialized
[21853.095453] Bluetooth: RFCOMM ver 1.8
[21854.739695] ACPI: PCI interrupt for device 0000:00:0e.0 disabled
[21854.751463] usbcore: deregistering interface driver ndiswrapper
[21854.780686] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[21854.792445] usbcore: registered new interface driver ndiswrapper
[21854.833636] ACPI: PCI Interrupt 0000:00:0e.0[A] -> GSI 17 (level, low) -> IRQ 17
[21854.869944] ssb: Sonics Silicon Backplane found on PCI device 0000:00:0e.0
[21857.301720] NET: Registered protocol family 17
[21860.846755] NET: Registered protocol family 10
[21860.847092] lo: Disabled Privacy Extensions
[21870.848458] eth0: no IPv6 routers present
trev@trev-desktop:~$

---

### Post by alehorb on 2008-04-27
[http://ubuntuforums.org/showthread.php?t=767372&highlight=BCM4306](http://ubuntuforums.org/showthread.php?t=767372&highlight=BCM4306)
[http://ubuntuforums.org/showthread.php?t=767875&highlight=BCM4306](http://ubuntuforums.org/showthread.php?t=767875&highlight=BCM4306)
[http://ubuntuforums.org/showthread.php?t=768197&highlight=BCM4306](http://ubuntuforums.org/showthread.php?t=768197&highlight=BCM4306)


Also try to pass acpi=off at boot time.

:lolflag:

---

### Post by alehorb on 2008-04-27
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

:lolflag:

---

### Post by alehorb on 2008-04-27
Look for 'Hardy Bug Fix' in the last link.

Also read the other pages,they may help you.


:lolflag:

---

### Post by alehorb on 2008-04-27
Replacing NetworkManager with 'wicd' is an option.

:lolflag:

---

### Post by TrevP on 2008-04-28
Thanks for the help :),

I think I've sorted it now using a recent posting. It seems like a lot of people are having wireless problems after upgrading to Hardy!!

---

