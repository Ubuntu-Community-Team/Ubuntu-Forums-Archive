---
title: "Upgraded and lost connectivity."
date: 2008-06-26
forum: Networking &amp; Wireless
---

### Post by seeker1458 on 2008-06-26
I just built a hardy box, and got everything set up the way I wanted it.  I was using a static IP.  I downloaded and installed the updates (120), and now I cant get online.  I changed the interface back to dhcp from static...still no luck.  Where should I look, & what should I do?

---

### Post by superprash2003 on 2008-06-26
go to the terminal and type ifconfig and post output here.. also type ping google.com and post output here..is this wired or wireless?

---

### Post by seeker1458 on 2008-06-27
```
user@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0c:29:07:ed:c5
	  inet addr:172.16.1.5  Bcast:172.16.1.255  Mask:255.255.255.0
	  inet6 addr: fe80::20c:29ff:fe07:edc5/64 Scope:Link         
	  UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1          
	  RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:636 (636.0 B)  TX bytes:8614 (8.4 KB)
          Interrupt:18 Base address:0x1400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:464 errors:0 dropped:0 overruns:0 frame:0
          TX packets:464 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:24120 (23.5 KB)  TX bytes:24120 (23.5 KB)
```

```
user@ubuntu:~$ ping www.google.com
ping: unknown host www.google.com
```

This is a hard wired connection.  The Host machine is a Windows XP Box.  The Hardy install is a VMWare install.

---

### Post by superprash2003 on 2008-06-27
are you able to ping your router or the windows machine?

---

### Post by seeker1458 on 2008-06-27
No, I am getting no network interaction.

---

### Post by superprash2003 on 2008-06-27
then how are you getting 172.16.1.5 as ip?? in your ubuntu machine go to system->administration->network and go to eth0 properties and set it to DHCP Mode.. you have selected bridged mode in your vmware settings right?

---

### Post by seeker1458 on 2008-06-27
/etc/network/interfaces is as follows

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 172.16.1.5
gateway 172.16.1.1
netmask 255.255.255.0
network 172.16.1.0
broadcast 172.16.1.255
```

---

### Post by seeker1458 on 2008-06-27
sorry forgot to say I changed back the interfaces file, and was posting what I had when I originally was using a static ip.

I need a static IP because this is a syslog server.

---

### Post by seeker1458 on 2008-06-27
...and yeah, I am using bridged.

---

### Post by seeker1458 on 2008-06-27
Like I said, everything was up and running fine.  I was recieving syslog entries from about 20 devices.  But I never applied the updates from when I first installed.  My first priority was getting the syslog up and running.  The problem started after the reboot on applying the updates.

---

### Post by superprash2003 on 2008-06-27
have you tried in dhcp mode?? does it work in dhcp mode?

---

### Post by seeker1458 on 2008-06-30
no it does not work in dhcp mode.  Another guy is having a similar problem, and he asked him to post the output of dmesg.  Here it is if it helps.
```
user@ubuntu:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:43:41 UTC 2008 (Ubuntu 2.6.24-19.34-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000ca000 - 00000000000cc000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fef0000 (usable)
[    0.000000]  BIOS-e820: 000000003fef0000 - 000000003fefc000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003fefc000 - 000000003ff00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003ff00000 - 0000000040000000 (usable)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fffe0000 - 0000000100000000 (reserved)
[    0.000000] 128MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f6ce0
[    0.000000] Entering add_active_range(0, 0, 262144) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   262144
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   262144
[    0.000000] On node 0 totalpages: 262144
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 256 pages used for memmap
[    0.000000]   HighMem zone: 32512 pages, LIFO batch:7
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F6C70 checksum 0
[    0.000000] ACPI: RSDP 000F6C70, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 3FEF7B74, 0030 (r1 PTLTD    RSDT    6040000  LTP        0)
[    0.000000] ACPI: FACP 3FEFBF14, 0074 (r1 INTEL  440BX     6040000 PTL     F4240)
[    0.000000] ACPI: DSDT 3FEF7BA4, 4370 (r1 PTLTD  Custom    6040000 MSFT  100000D)
[    0.000000] ACPI: FACS 3FEFCFC0, 0040
[    0.000000] ACPI: APIC 3FEFBF88, 0050 (r1 PTLTD  	 APIC    6040000  LTP        0)
[    0.000000] ACPI: BOOT 3FEFBFD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:2 APIC version 17
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000ca000
[    0.000000] swsusp: Registered nosave memory region: 00000000000ca000 - 00000000000cc000
[    0.000000] swsusp: Registered nosave memory region: 00000000000cc000 - 00000000000dc000
[    0.000000] swsusp: Registered nosave memory region: 00000000000dc000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 260096
[    0.000000] Kernel command line: root=UUID=89879598-257f-4c09-b039-476d8636dd45 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2792.133 MHz processor.
[272966.900435] Console: colour VGA+ 80x25
[272966.901109] console [tty0] enabled
[272966.901966] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[272966.902823] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[272966.922947] Memory: 1027360k/1048576k available (2177k kernel code, 20456k reserved, 1006k data, 368k init, 131008k highmem)
[272966.923204] virtual kernel memory layout:
[272966.923216]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[272966.923227]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[272966.923239]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[272966.923250]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[272966.923294]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[272966.923313]       .data : 0xc0320434 - 0xc041bdc4   (1006 kB)
[272966.923332]       .text : 0xc0100000 - 0xc0320434   (2177 kB)
[272966.923425] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[272966.924282] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[272967.005631] Calibrating delay using timer specific routine.. 5689.77 BogoMIPS (lpj=11379548)
[272967.005694] Security Framework initialized
[272967.005756] SELinux:  Disabled at boot.
[272967.005819] AppArmor: AppArmor initialized
[272967.005881] Failure registering capabilities with primary security module.
[272967.005943] Mount-cache hash table entries: 512
[272967.006006] Initializing cgroup subsys ns
[272967.006068] Initializing cgroup subsys cpuacct
[272967.006131] CPU: After generic identify, caps: 0febfbff 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[272967.006193] CPU: Trace cache: 12K uops, L1 D cache: 8K
[272967.006251] CPU: L2 cache: 512K
[272967.006313] CPU: After all inits, caps: 0febfbff 00000000 00000000 0000b080 00000000 00000000 00000000 00000000
[272967.006375] Compat vDSO mapped to ffffe000.
[272967.006438] Checking 'hlt' instruction... OK.
[272967.021083] SMP alternatives: switching to UP code
[272967.021145] Freeing SMP alternatives: 11k freed
[272967.021208] Early unpacking initramfs... done
[272967.021270] ACPI: Core revision 20070126
[272967.025175] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[272967.025487] CPU0: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 08
[272967.025611] Total of 1 processors activated (5689.77 BogoMIPS).
[272967.025674] ENABLING IO-APIC IRQs
[272967.025900] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[272967.216044] Brought up 1 CPUs
[272967.223673] CPU0 attaching sched-domain:
[272967.223844]  domain 0: span 01
[272967.223920]   groups: 01
[272967.267168] net_namespace: 64 bytes
[272967.267649] Booting paravirtualized kernel on bare hardware
[272967.275690] Time: 13:17:42  Date: 06/30/08
[272967.287021] NET: Registered protocol family 16
[272967.299747] EISA bus registered
[272967.303144] ACPI: bus type pci registered
[272967.311057] PCI: PCI BIOS revision 2.10 entry at 0xfd9a0, last bus=1
[272967.311134] PCI: Using configuration type 1
[272967.311209] Setting up standard PCI resources
[272967.395770] ACPI: EC: Look up EC in DSDT
[272967.575202] ACPI: Interpreter enabled
[272967.575388] ACPI: (supports S0 S1 S5)
[272967.579291] ACPI: Using IOAPIC for interrupt routing
[272967.803335] ACPI: PCI Root Bridge [PCI0] (0000:00)
[272967.827587] PCI quirk: region 1000-103f claimed by PIIX4 ACPI
[272967.830019] PCI quirk: region 1040-104f claimed by PIIX4 SMB
[272967.851342] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[272967.887452] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
[272967.891033] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11 14 15)
[272967.891566] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 14 15)
[272967.894598] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *9 10 11 14 15)
[272967.899514] Linux Plug and Play Support v0.97 (c) Adam Belay
[272967.902075] pnp: PnP ACPI init
[272967.903162] ACPI: bus type pnp registered
[272968.421391] pnp: PnP ACPI: found 12 devices
[272968.422336] ACPI: ACPI bus type pnp unregistered
[272968.422593] PnPBIOS: Disabled by ACPI PNP
[272968.447148] PCI: Using ACPI for IRQ routing
[272968.449280] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[272968.664906] NET: Registered protocol family 8
[272968.665017] NET: Registered protocol family 20
[272968.670405] Time: tsc clocksource has been installed.
[272968.682250] Clocksource tsc unstable (delta = 276040297 ns)
[272968.686107] Time: pit clocksource has been installed.
[272968.690710] AppArmor: AppArmor Filesystem Enabled
[272968.714142] system 00:01: ioport range 0x1000-0x103f has been reserved
[272968.714206] system 00:01: ioport range 0x1040-0x104f has been reserved
[272968.772238] PCI: Bridge: 0000:00:01.0
[272968.772295]   IO window: disabled.
[272968.772357]   MEM window: disabled.
[272968.772420]   PREFETCH window: disabled.
[272968.772470] PCI: Setting latency timer of device 0000:00:01.0 to 64
[272968.772470] NET: Registered protocol family 2
[272968.774153] Time: acpi_pm clocksource has been installed.
[272968.774411] Switched to high resolution mode on CPU 0
[272968.813847] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[272968.817841] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[272968.821836] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[272968.821858] TCP: Hash tables configured (established 131072 bind 65536)
[272968.821881] TCP reno registered
[272968.837807] checking if image is initramfs... it is
[272969.740324] Freeing initrd memory: 7320k freed
[272969.740680] Simple Boot Flag at 0x36 set to 0x1
[272969.742306] audit: initializing netlink socket (disabled)
[272969.742353] audit(1214831848.328:1): initialized
[272969.744901] highmem bounce pool size: 64 pages
[272969.750541] VFS: Disk quotas dquot_6.5.1
[272969.750793] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[272969.752466] io scheduler noop registered
[272969.752512] io scheduler anticipatory registered
[272969.752545] io scheduler deadline registered
[272969.752591] io scheduler cfq registered (default)
[272969.752638] Limiting direct PCI/PCI transfers.
[272969.752740] Boot video device is 0000:00:0f.0
[272969.753850] isapnp: Scanning for PnP cards...
[272970.116640] isapnp: No Plug & Play device found
[272970.189171] Real Time Clock Driver v1.12ac
[272970.189468] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[272970.191600] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[272970.191906] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[272970.192737] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[272970.193082] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[272970.195172] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[272970.195697] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[272970.195998] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUS] at 0x60,0x64 irq 1,12
[272970.714745] serio: i8042 KBD port at 0x60,0x64 irq 1
[272970.714867] serio: i8042 AUX port at 0x60,0x64 irq 12
[272970.730982] mice: PS/2 mouse device common for all mice
[272970.731843] EISA: Probing bus 0 at eisa.0
[272970.731999] Cannot allocate resource for EISA slot 1
[272970.732077] EISA: Detected 0 cards.
[272970.732156] cpuidle: using governor ladder
[272970.732234] cpuidle: using governor menu
[272970.732312] NET: Registered protocol family 1
[272970.732390] Using IPI No-Shortcut mode
[272970.732468] registered taskstats version 1
[272970.732547]   Magic number: 12:352:282
[272970.732625]   hash matches device ttyvd
[272970.732703]   hash matches device tty19
[272970.732778] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[272970.732825] EDD information not available.
[272970.750639] Freeing unused kernel memory: 368k freed
[272970.751808] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[272972.453056] fuse init (API version 7.9)
[272972.635534] ACPI: Processor [CPU0] (supports 8 throttling states)
[272972.635562] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[272972.635590] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[272972.635618] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[272973.286575] SCSI subsystem initialized
[272973.490163] libata version 3.00 loaded.
[272973.518124] usbcore: registered new interface driver usbfs
[272973.518189] usbcore: registered new interface driver hub
[272973.601899] usbcore: registered new device driver usb
[272973.678433] Fusion MPT base driver 3.04.06
[272973.678467] Copyright (c) 1999-2007 LSI Corporation
[272973.729706] Fusion MPT SPI Host driver 3.04.06
[272973.729771] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 17 (level, low) -> IRQ 16
[272973.729835] mptbase: ioc0: Initiating bringup
[272973.805475] ioc0: LSI53C1030 B0: Capabilities={Initiator}
[272973.809570] USB Universal Host Controller Interface driver v3.0
[272973.849623] pcnet32.c:v1.34 14.Aug.2007 tsbogend@alpha.franken.de
[272973.961330] scsi0 : ioc0: LSI53C1030 B0, FwRev=00000000h, Ports=1, MaxQ=128, IRQ=16
[272974.093607] ata_piix 0000:00:07.1: version 2.12
[272974.104968] scsi 0:0:0:0: Direct-Access     VMware,  VMware Virtual S 1.0  PQ: 0 ANSI: 2
[272974.105022]  target0:0:0: Beginning Domain Validation
[272974.105075]  target0:0:0: Domain Validation skipping write tests
[272974.105128]  target0:0:0: Ending Domain Validation
[272974.105182]  target0:0:0: FAST-40 WIDE SCSI 80.0 MB/s ST (25 ns, offset 127)
[272974.145028] scsi1 : ata_piix
[272974.188812] scsi2 : ata_piix
[272974.188865] ata1: PATA max UDMA/33 cmd 0x1f0 ctl 0x3f6 bmdma 0x1050 irq 14
[272974.188907] ata2: PATA max UDMA/33 cmd 0x170 ctl 0x376 bmdma 0x1058 irq 15
[272974.189068] ata1: port disabled. ignoring.
[272974.500975] ata2.00: ATAPI: VMware Virtual IDE CDROM Drive, 00000001, max UDMA/33
[272974.656239] ata2.00: configured for UDMA/33
[272974.656754] scsi 2:0:0:0: CD-ROM            NECVMWar VMware IDE CDR10 1.00 PQ: 0 ANSI: 5
[272974.664018] ACPI: PCI Interrupt 0000:00:07.2[D] -> GSI 19 (level, low) -> IRQ 17
[272974.664070] uhci_hcd 0000:00:07.2: UHCI Host Controller
[272974.664121] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[272974.664231] uhci_hcd 0000:00:07.2: irq 17, io base 0x00001060
[272974.668108] usb usb1: configuration #1 chosen from 1 choice
[272974.668160] hub 1-0:1.0: USB hub found
[272974.668212] hub 1-0:1.0: 2 ports detected
[272974.772109] ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 18 (level, low) -> IRQ 18
[272974.772161] pcnet32: PCnet/PCI II 79C970A at 0x1400, 00 0c 29 07 ed c5 assigned IRQ 18.
[272974.772213] eth0: registered as PCnet/PCI II 79C970A
[272974.772265] pcnet32: 1 cards_found.
[272975.019905] Floppy drive(s): fd0 is 1.44M
[272975.035704] FDC 0 is a post-1991 82077
[272976.591303] Driver 'sd' needs updating - please use bus_type methods
[272976.592789] sd 0:0:0:0: [sda] 16777216 512-byte hardware sectors (8590 MB)
[272976.592940] sd 0:0:0:0: [sda] Write Protect is off
[272976.593040] sd 0:0:0:0: [sda] Mode Sense: 5d 00 00 00
[272976.593191] sd 0:0:0:0: [sda] Cache data unavailable
[272976.593288] sd 0:0:0:0: [sda] Assuming drive cache: write through
[272976.612760] sd 0:0:0:0: [sda] 16777216 512-byte hardware sectors (8590 MB)
[272976.612880] sd 0:0:0:0: [sda] Write Protect is off
[272976.612931] sd 0:0:0:0: [sda] Mode Sense: 5d 00 00 00
[272976.613051] sd 0:0:0:0: [sda] Cache data unavailable
[272976.613081] sd 0:0:0:0: [sda] Assuming drive cache: write through
[272976.613200]  sda: sda1 sda2 < sda5 >
[272976.632808] sd 0:0:0:0: [sda] Attached SCSI disk
[272976.660907] sd 0:0:0:0: Attached scsi generic sg0 type 0
[272976.661019] scsi 2:0:0:0: Attached scsi generic sg1 type 5
[272976.700680] Driver 'sr' needs updating - please use bus_type methods
[272976.701888] sr0: scsi3-mmc drive: 1x/1x xa/form2 cdda tray
[272976.702007] Uniform CD-ROM driver Revision: 3.20
[272976.702127] sr 2:0:0:0: Attached scsi CD-ROM sr0
[272977.143981] Attempting manual resume
[272977.144027] swsusp: Resume From Partition 8:5
[272977.144056] PM: Checking swsusp image.
[272977.144194] PM: Resume from disk failed.
[272977.177434] kjournald starting.  Commit interval 5 seconds
[272977.177573] EXT3-fs: mounted filesystem with ordered data mode.
[273012.286935] Linux agpgart interface v0.102
[273012.380506] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[273012.456749] agpgart: Detected an Intel 440BX Chipset.
[273012.463988] agpgart: AGP aperture is 64M @ 0xec000000
[273012.537605] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[273012.695162] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[273012.695351] piix4_smbus 0000:00:07.3: Host SMBus controller not enabled!
[273013.164955] input: PC Speaker as /devices/platform/pcspkr/input/input2
[273013.956200] ACPI: AC Adapter [ACAD] (on-line)
[273014.077384] input: Power Button (FF) as /devices/virtual/input/input3
[273014.093527] ACPI: Power Button (FF) [PWRF]
[273014.110415] eth0: link up
[273016.462128] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input4
[273017.212874] parport_pc 00:08: reported by Plug and Play ACPI
[273017.214946] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[273018.173103] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 19 (level, low) -> IRQ 17
[273025.776699] NET: Registered protocol family 10
[273025.779828] lo: Disabled Privacy Extensions
[273030.017893] loop: module loaded
[273030.079475] lp0: using parport0 (interrupt-driven).
[273031.452421] EXT3 FS on sda1, internal journal
[273035.646624] ip_tables: (C) 2000-2006 Netfilter Core Team
[273036.475137] eth0: no IPv6 routers present
[273039.012986] No dock devices found.
[273043.157380] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[273043.157510] apm: overridden by ACPI.
[273043.361585] ppdev: user-space parallel port driver
[273043.592541] audit(1214849923.232:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4729 profile="/usr/sbin/cupsd" namespace="default"
[273043.593859] audit(1214849923.232:3): type=1503 operation="inode_permission" requested_mask="w::" denied_mask="w::" name="/etc/krb5.conf" pid=4729 profile="/usr/sbin/cupsd" namespace="default"
[273068.077853] Bluetooth: Core ver 2.11
[273068.085080] NET: Registered protocol family 31
[273068.085124] Bluetooth: HCI device and connection manager initialized
[273068.085547] Bluetooth: HCI socket layer initialized
[273068.224378] Bluetooth: L2CAP ver 2.9
[273068.224421] Bluetooth: L2CAP socket layer initialized
[273068.350874] Bluetooth: RFCOMM socket layer initialized
[273068.355773] Bluetooth: RFCOMM TTY layer initialized
[273068.355823] Bluetooth: RFCOMM ver 1.8
[273070.564913] mtrr: your processor doesn't support write-combining
[273100.145997] UDF-fs: No VRS found
[273100.200032] ISO 9660 Extensions: RRIP_1991A
[273131.527815] usb 1-1: new full speed USB device using uhci_hcd and address 2
[273131.694115] usb 1-1: configuration #1 chosen from 1 choice
[273131.946779] usbcore: registered new interface driver libusual
[273132.056065] Initializing USB Mass Storage driver...
[273132.064019] scsi3 : SCSI emulation for USB Mass Storage devices
[273132.073532] usbcore: registered new interface driver usb-storage
[273132.073985] USB Mass Storage support registered.
[273132.075249] usb-storage: device found at 2
[273132.075328] usb-storage: waiting for device to settle before scanning
[273137.070518] usb-storage: device scan complete
[273137.095793] scsi 3:0:0:0: Direct-Access     SanDisk  U3 Cruzer Micro  4.05 PQ: 0 ANSI: 2
[273137.132166] sd 3:0:0:0: [sdb] 8027789 512-byte hardware sectors (4110 MB)
[273137.145612] sd 3:0:0:0: [sdb] Write Protect is off
[273137.145671] sd 3:0:0:0: [sdb] Mode Sense: 03 00 00 00
[273137.145738] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[273137.214697] sd 3:0:0:0: [sdb] 8027789 512-byte hardware sectors (4110 MB)
[273137.229414] sd 3:0:0:0: [sdb] Write Protect is off
[273137.229437] sd 3:0:0:0: [sdb] Mode Sense: 03 00 00 00
[273137.229453] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[273137.229554]  sdb: sdb1
[273137.255375] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[273137.256235] sd 3:0:0:0: Attached scsi generic sg2 type 0


```

---

