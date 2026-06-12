---
title: "Help with ndiswrapper error messages"
date: 2006-10-18
forum: Networking &amp; Wireless
---

### Post by funkadelic on 2006-10-18
I have been trying to figure out why my Netgear WG111T USB wireless adapter does not work in Edgy, even though it was fine in Dapper. I did some research, and it seems that many people are having trouble with the repository version of ndiswrapper with Edgy. Many have had luck building the latest version from the source...

I compiled the newest version of ndiswrapper, and I installed the windows drivers with no problem. Running modprobe gives no error messages, but things still don't work. Can someone help me figure out what is going wrong? "couldn't allocate memory" ???

**dmesg output:**
```
[17205046.844000] ndiswrapper version 1.26 loaded (preempt=no,smp=yes)
[17205046.964000] usb 1-8: reset high speed USB device using ehci_hcd and address 4
[17205047.100000] ndiswrapper: driver athfmwdl (,12/05/2003,1.00.001) loaded
[17205047.100000] ndiswrapper (add_bin_file:320): couldn't allocate memory
[17205047.100000] ndiswrapper (get_bin_file:282): loadndiswrapper failed (59904); check system log for messages from 'loadndisdriver'
```

**ndiswrapper -l output:**
```
installed drivers:
athfmwdl                driver installed, hardware (1385:4251) present 
netwg11t                driver installed 
```

**My whole session:**
```
bozo@bozo-box:~/Desktop$ ls
ndiswrapper-1.26  ndiswrapper-1.26.tar.gz  WG111T_GRV1.2.zip
bozo@bozo-box:~/Desktop$ cd WG111T_GR\ V1.2/
bozo@bozo-box:~/Desktop/WG111T_GR V1.2$ ls
ar55239x.bin  athfmw9x.sys  autorun.exe  ndis5         Utility
ar5523.bin    athfmwdl.inf  autorun.inf  netwg11t.cat  wg111t9x.sys
athfmdwl.cat  athfmwdl.sys  Doc          netwg11t.inf  wg11tnd5.sys
bozo@bozo-box:~/Desktop/WG111T_GR V1.2$ ndiswrapper -i athfmwdl.inf 
couldn't create /etc/ndiswrapper: Permission denied at /usr/sbin/ndiswrapper line 134.
bozo@bozo-box:~/Desktop/WG111T_GR V1.2$ sudo ndiswrapper -i athfmwdl.inf 
installing athfmwdl ...
bozo@bozo-box:~/Desktop/WG111T_GR V1.2$ sudo ndiswrapper -i netwg11t.inf 
installing netwg11t ...
bozo@bozo-box:~/Desktop/WG111T_GR V1.2$ ndiswrapper -l
installed drivers:
athfmwdl                driver installed 
netwg11t                driver installed 
bozo@bozo-box:~/Desktop/WG111T_GR V1.2$ ndiswrapper -l
installed drivers:
athfmwdl                driver installed, hardware (1385:4251) present 
netwg11t                driver installed 
bozo@bozo-box:~/Desktop/WG111T_GR V1.2$ ndiswrapper -l
installed drivers:
athfmwdl                driver installed, hardware (1385:4251) present 
netwg11t                driver installed 
bozo@bozo-box:~/Desktop/WG111T_GR V1.2$ depmod -a
FATAL: Could not open /lib/modules/2.6.17-10-generic/modules.dep.temp for writing: Permission denied
bozo@bozo-box:~/Desktop/WG111T_GR V1.2$ sudo depmod -a
bozo@bozo-box:~/Desktop/WG111T_GR V1.2$ sudo modprobe ndiswrapper
bozo@bozo-box:~/Desktop/WG111T_GR V1.2$ dmesg
[17179569.184000] Linux version 2.6.17-10-generic (root@palmer) (gcc version 4.1.2 20060920 (prerelease) (Ubuntu 4.1.1-13ubuntu3)) #2 SMP Tue Sep 26 16:53:47 UTC 2006 (Ubuntu 2.6.17-10.24-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e6000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000003fe30000 (usable)
[17179569.184000]  BIOS-e820: 000000003fe30000 - 000000003fe3e05e (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000003fe3e05e - 000000003ff30000 (usable)
[17179569.184000]  BIOS-e820: 000000003ff30000 - 000000003ff40000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000003ff40000 - 000000003fff0000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000003fff0000 - 0000000040000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fecf0000 - 00000000fecf1000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
[17179569.184000] 127MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000ff780
[17179569.184000] On node 0 totalpages: 261936
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 32560 pages, LIFO batch:7
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x000f62f0
[17179569.184000] ACPI: RSDT (v001 INTEL  D865PERL 0x20040402 MSFT 0x00000097) @ 0x3ff30000
[17179569.184000] ACPI: FADT (v002 INTEL  D865PERL 0x20040402 MSFT 0x00000097) @ 0x3ff30200
[17179569.184000] ACPI: MADT (v001 INTEL  D865PERL 0x20040402 MSFT 0x00000097) @ 0x3ff30300
[17179569.184000] ACPI: ASF! (v016 LEGEND I865PASF 0x00000001 MSFT 0x0100000d) @ 0x3ff344e0
[17179569.184000] ACPI: WDDT (v001 INTEL  OEMWDDT  0x00000001 MSFT 0x0100000d) @ 0x3ff34579
[17179569.184000] ACPI: DSDT (v001 INTEL  D865PERL 0x00000006 MSFT 0x0100000d) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x408
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:2 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[17179569.184000] Processor #1 15:2 APIC version 20
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 50000000 (gap: 40000000:becf0000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hdb1 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[17179569.184000] Detected 2793.472 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179569.780000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179569.780000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.800000] Memory: 1026760k/1047744k available (1894k kernel code, 20232k reserved, 1098k data, 308k init, 130180k highmem)
[17179569.800000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.880000] Calibrating delay using timer specific routine.. 5591.87 BogoMIPS (lpj=11183744)
[17179569.880000] Security Framework v1.0.0 initialized
[17179569.880000] SELinux:  Disabled at boot.
[17179569.880000] Mount-cache hash table entries: 512
[17179569.880000] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[17179569.880000] CPU: After vendor identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[17179569.880000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[17179569.880000] CPU: L2 cache: 512K
[17179569.880000] CPU: Hyper-Threading is disabled
[17179569.880000] CPU: After all inits, caps: bfebfbff 00000000 00000000 00000080 00004400 00000000 00000000
[17179569.880000] Checking 'hlt' instruction... OK.
[17179569.896000] SMP alternatives: switching to UP code
[17179569.896000] checking if image is initramfs... it is
[17179570.496000] Freeing initrd memory: 7412k freed
[17179570.496000] ACPI: Core revision 20060707
[17179570.496000] ACPI: Looking for DSDT ... not found!
[17179570.500000] CPU0: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 09
[17179570.500000] SMP alternatives: switching to SMP code
[17179570.500000] Booting processor 1/1 eip 3000
[17179570.508000] Initializing CPU#1
[17179570.588000] Calibrating delay using timer specific routine.. 5586.41 BogoMIPS (lpj=11172838)
[17179570.588000] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[17179570.588000] CPU: After vendor identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[17179570.588000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[17179570.588000] CPU: L2 cache: 512K
[17179570.588000] CPU: Hyper-Threading is disabled
[17179570.588000] CPU: After all inits, caps: bfebfbff 00000000 00000000 00000080 00004400 00000000 00000000
[17179570.588000] CPU1: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 09
[17179570.588000] Total of 2 processors activated (11178.29 BogoMIPS).
[17179570.588000] ENABLING IO-APIC IRQs
[17179570.588000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179570.732000] checking TSC synchronization across 2 CPUs: passed.
[17179570.736000] Brought up 2 CPUs
[17179570.792000] migration_cost=4000
[17179570.792000] NET: Registered protocol family 16
[17179570.792000] EISA bus registered
[17179570.792000] ACPI: bus type pci registered
[17179570.792000] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=2
[17179570.792000] Setting up standard PCI resources
[17179570.808000] ACPI: Interpreter enabled
[17179570.808000] ACPI: Using IOAPIC for interrupt routing
[17179570.808000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.808000] PCI: Probing PCI hardware (bus 00)
[17179570.808000] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[17179570.808000] PCI quirk: region 0500-053f claimed by ICH4 GPIO
[17179570.808000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179570.808000] Boot video device is 0000:01:00.0
[17179570.808000] PCI: Transparent bridge - 0000:00:1e.0
[17179570.808000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.812000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[17179570.812000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[17179570.816000] ACPI: Power Resource [URP1] (off)
[17179570.816000] ACPI: Power Resource [FDDP] (off)
[17179570.816000] ACPI: Power Resource [LPTP] (off)
[17179570.816000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[17179570.816000] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[17179570.816000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[17179570.816000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[17179570.820000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[17179570.820000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[17179570.820000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[17179570.820000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[17179570.820000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.820000] pnp: PnP ACPI init
[17179570.824000] pnp: PnP ACPI: found 14 devices
[17179570.824000] PnPBIOS: Disabled by ACPI PNP
[17179570.824000] PCI: Using ACPI for IRQ routing
[17179570.824000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179570.828000] pnp: 00:0c: ioport range 0x400-0x47f could not be reserved
[17179570.828000] pnp: 00:0c: ioport range 0x680-0x6ff has been reserved
[17179570.828000] pnp: 00:0c: ioport range 0x500-0x53f has been reserved
[17179570.828000] PCI: Bridge: 0000:00:01.0
[17179570.828000]   IO window: disabled.
[17179570.828000]   MEM window: fc900000-fe9fffff
[17179570.828000]   PREFETCH window: e4800000-f47fffff
[17179570.828000] PCI: Bridge: 0000:00:1e.0
[17179570.828000]   IO window: b000-bfff
[17179570.828000]   MEM window: fea00000-feafffff
[17179570.828000]   PREFETCH window: disabled.
[17179570.828000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179570.828000] NET: Registered protocol family 2
[17179570.880000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179570.880000] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[17179570.880000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[17179570.880000] TCP: Hash tables configured (established 131072 bind 65536)
[17179570.880000] TCP reno registered
[17179570.880000] audit: initializing netlink socket (disabled)
[17179570.880000] audit(1161021990.880:1): initialized
[17179570.880000] highmem bounce pool size: 64 pages
[17179570.880000] VFS: Disk quotas dquot_6.5.1
[17179570.880000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179570.880000] Initializing Cryptographic API
[17179570.880000] io scheduler noop registered
[17179570.880000] io scheduler anticipatory registered
[17179570.880000] io scheduler deadline registered
[17179570.880000] io scheduler cfq registered (default)
[17179570.880000] isapnp: Scanning for PnP cards...
[17179571.236000] isapnp: No Plug & Play device found
[17179571.260000] Real Time Clock Driver v1.12ac
[17179571.260000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179571.260000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179571.260000] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179571.260000] mice: PS/2 mouse device common for all mice
[17179571.260000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179571.260000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179571.260000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179571.260000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[17179571.264000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179571.264000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179571.264000] EISA: Probing bus 0 at eisa.0
[17179571.264000] EISA: Detected 0 cards.
[17179571.264000] TCP bic registered
[17179571.264000] NET: Registered protocol family 1
[17179571.264000] NET: Registered protocol family 8
[17179571.264000] NET: Registered protocol family 20
[17179571.264000] Starting balanced_irq
[17179571.264000] Using IPI No-Shortcut mode
[17179571.264000] ACPI: (supports S0 S1 S4 S5)
[17179571.264000] Freeing unused kernel memory: 308k freed
[17179571.296000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179572.348000] Capability LSM initialized
[17179572.384000] ACPI: Processor [CPU1] (supports 8 throttling states)
[17179572.384000] ACPI: Processor [CPU2] (supports 8 throttling states)
[17179572.852000] ICH5: IDE controller at PCI slot 0000:00:1f.1
[17179572.852000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[17179572.852000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 169
[17179572.852000] ICH5: chipset revision 2
[17179572.852000] ICH5: not 100% native mode: will probe irqs later
[17179572.852000]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:DMA
[17179572.852000]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd:DMA
[17179572.852000] Probing IDE interface ide0...
[17179573.144000] hda: ST3120026A, ATA DISK drive
[17179573.428000] hdb: WDC WD800JB-00JJC0, ATA DISK drive
[17179573.488000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179573.500000] Probing IDE interface ide1...
[17179574.244000] hdc: PLEXTOR CD-R PREMIUM, ATAPI CD/DVD-ROM drive
[17179575.032000] hdd: PLEXTOR DVDR PX-740A, ATAPI CD/DVD-ROM drive
[17179575.092000] ide1 at 0x170-0x177,0x376 on irq 15
[17179575.112000] hdc: ATAPI 40X CD-ROM CD-R/RW drive, 8192kB Cache, UDMA(33)
[17179575.112000] Uniform CD-ROM driver Revision: 3.20
[17179575.112000] hda: max request size: 512KiB
[17179575.112000] hda: 234441648 sectors (120034 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(100)
[17179575.112000] hda: cache flushes supported
[17179575.112000]  hda:<6>hdd: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179575.120000]  hda1
[17179575.120000] hdb: max request size: 128KiB
[17179575.120000] hdb: 156301488 sectors (80026 MB) w/8192KiB Cache, CHS=65535/16/63, UDMA(100)
[17179575.120000] hdb: cache flushes supported
[17179575.120000]  hdb: hdb1 hdb2 < hdb5 >
[17179575.448000] SCSI subsystem initialized
[17179575.452000] libata version 1.20 loaded.
[17179575.452000] ata_piix 0000:00:1f.2: version 1.05
[17179575.452000] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[17179575.452000] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 18 (level, low) -> IRQ 169
[17179575.452000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[17179575.452000] ata1: SATA max UDMA/133 cmd 0xEC00 ctl 0xE802 bmdma 0xDC00 irq 169
[17179575.452000] ata2: SATA max UDMA/133 cmd 0xE400 ctl 0xE002 bmdma 0xDC08 irq 169
[17179575.556000] ata1: SATA port has no device.
[17179575.556000] scsi0 : ata_piix
[17179575.660000] ata2: SATA port has no device.
[17179575.660000] scsi1 : ata_piix
[17179575.712000] usbcore: registered new driver usbfs
[17179575.712000] usbcore: registered new driver hub
[17179575.716000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 177
[17179575.716000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179575.716000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179575.716000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[17179575.716000] ehci_hcd 0000:00:1d.7: debug port 1
[17179575.716000] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[17179575.716000] ehci_hcd 0000:00:1d.7: irq 177, io mem 0xfebffc00
[17179575.720000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179575.720000] usb usb1: configuration #1 chosen from 1 choice
[17179575.720000] hub 1-0:1.0: USB hub found
[17179575.720000] hub 1-0:1.0: 8 ports detected
[17179575.732000] USB Universal Host Controller Interface driver v3.0
[17179575.764000] ieee1394: Initialized config rom entry `ip1394'
[17179575.832000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 185
[17179575.832000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179575.832000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179575.832000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[17179575.832000] uhci_hcd 0000:00:1d.0: irq 185, io base 0x0000cc00
[17179575.832000] usb usb2: configuration #1 chosen from 1 choice
[17179575.832000] hub 2-0:1.0: USB hub found
[17179575.832000] hub 2-0:1.0: 2 ports detected
[17179575.940000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 193
[17179575.940000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179575.940000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179575.940000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[17179575.940000] uhci_hcd 0000:00:1d.1: irq 193, io base 0x0000d000
[17179575.940000] usb usb3: configuration #1 chosen from 1 choice
[17179575.940000] hub 3-0:1.0: USB hub found
[17179575.940000] hub 3-0:1.0: 2 ports detected
[17179576.048000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 169
[17179576.048000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179576.048000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179576.048000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[17179576.048000] uhci_hcd 0000:00:1d.2: irq 169, io base 0x0000d400
[17179576.048000] usb usb4: configuration #1 chosen from 1 choice
[17179576.048000] hub 4-0:1.0: USB hub found
[17179576.048000] hub 4-0:1.0: 2 ports detected
[17179576.156000] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 185
[17179576.156000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[17179576.156000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[17179576.156000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[17179576.156000] uhci_hcd 0000:00:1d.3: irq 185, io base 0x0000d800
[17179576.156000] usb usb5: configuration #1 chosen from 1 choice
[17179576.156000] hub 5-0:1.0: USB hub found
[17179576.156000] hub 5-0:1.0: 2 ports detected
[17179576.260000] usb 1-4: new high speed USB device using ehci_hcd and address 3
[17179576.264000] ACPI: PCI Interrupt 0000:02:02.2[B] -> GSI 18 (level, low) -> IRQ 169
[17179576.320000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[169]  MMIO=[feaff800-feafffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[17179576.324000] ACPI: PCI Interrupt 0000:02:07.0[A] -> GSI 17 (level, low) -> IRQ 201
[17179576.372000] ohci1394: fw-host1: OHCI-1394 1.0 (PCI): IRQ=[201]  MMIO=[feafe000-feafe7ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[17179576.408000] usb 1-4: configuration #1 chosen from 1 choice
[17179576.648000] usb 2-1: new low speed USB device using uhci_hcd and address 2
[17179576.836000] usb 2-1: configuration #1 chosen from 1 choice
[17179576.968000] usbcore: registered new driver libusual
[17179576.968000] usbcore: registered new driver hiddev
[17179576.976000] Initializing USB Mass Storage driver...
[17179576.976000] scsi2 : SCSI emulation for USB Mass Storage devices
[17179576.976000] usb-storage: device found at 3
[17179576.976000] usb-storage: waiting for device to settle before scanning
[17179576.988000] input: ARROW STRONG USB 3D Mouse as /class/input/input1
[17179576.988000] input: USB HID v1.00 Mouse [ARROW STRONG USB 3D Mouse] on usb-0000:00:1d.0-1
[17179576.988000] usbcore: registered new driver usbhid
[17179576.988000] usbcore: registered new driver usb-storage
[17179576.988000] USB Mass Storage support registered.
[17179576.988000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179577.056000] Attempting manual resume
[17179577.084000] kjournald starting.  Commit interval 5 seconds
[17179577.084000] EXT3-fs: mounted filesystem with ordered data mode.
[17179577.604000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023c0020001cf3]
[17179577.880000] ieee1394: Host added: ID:BUS[1-00:1023]  GUID[00111100000e2ea5]
[17179581.976000] usb-storage: device scan complete
[17179581.980000]   Vendor: Maxtor    Model: 6L300R0           Rev: BAJ4
[17179581.980000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[17179585.184000] Floppy drive(s): fd0 is 1.44M
[17179585.208000] FDC 0 is a National Semiconductor PC87306
[17179585.264000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179585.268000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179585.320000] parport: PnPBIOS parport detected.
[17179585.320000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[17179585.680000] hw_random: RNG not detected
[17179585.724000] Linux agpgart interface v0.101 (c) Dave Jones
[17179585.952000] agpgart: Detected an Intel 865 Chipset.
[17179585.956000] agpgart: AGP aperture is 64M @ 0xf8000000
[17179585.988000] nvidia: module license 'NVIDIA' taints kernel.
[17179585.992000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 185
[17179585.992000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8774  Tue Aug  1 20:54:08 PDT 2006
[17179586.284000] input: PC Speaker as /class/input/input2
[17179586.560000] ts: Compaq touchscreen protocol output
[17179586.656000] SCSI device sda: 586114704 512-byte hdwr sectors (300091 MB)
[17179586.656000] sda: Write Protect is off
[17179586.656000] sda: Mode Sense: 53 00 00 08
[17179586.656000] sda: assuming drive cache: write through
[17179586.656000] SCSI device sda: 586114704 512-byte hdwr sectors (300091 MB)
[17179586.660000] sda: Write Protect is off
[17179586.660000] sda: Mode Sense: 53 00 00 08
[17179586.660000] sda: assuming drive cache: write through
[17179586.660000]  sda: sda1
[17179586.680000] sd 2:0:0:0: Attached scsi disk sda
[17179586.736000] gameport: EMU10K1 is pci0000:02:02.1/gameport0, io 0xbc00, speed 1193kHz
[17179586.772000] e100: Intel(R) PRO/100 Network Driver, 3.5.10-k2-NAPI
[17179586.772000] e100: Copyright(c) 1999-2005 Intel Corporation
[17179586.776000] ACPI: PCI Interrupt 0000:02:08.0[A] -> GSI 20 (level, low) -> IRQ 209
[17179586.796000] e100: eth0: e100_probe: addr 0xfeafd000, irq 209, MAC addr 00:11:11:0E:2E:A5
[17179586.800000] sd 2:0:0:0: Attached scsi generic sg0 type 0
[17179586.992000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[17179587.076000] input: ImExPS/2 Generic Explorer Mouse as /class/input/input3
[17179587.088000] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 17 (level, low) -> IRQ 201
[17179587.472000] lp0: using parport0 (interrupt-driven).
[17179587.524000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179587.524000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179587.576000] Adding 3028212k swap on /dev/disk/by-uuid/3b6a25fd-4858-45f5-b074-9f958e5aa1e9.  Priority:-1 extents:1 across:3028212k
[17179587.636000] EXT3 FS on hdb1, internal journal
[17179588.056000] NET: Registered protocol family 17
[17179589.260000] NET: Registered protocol family 10
[17179589.260000] lo: Disabled Privacy Extensions
[17179589.260000] IPv6 over IPv4 tunneling driver
[17179593.144000] ACPI: Power Button (FF) [PWRF]
[17179593.144000] ACPI: Sleep Button (CM) [SLPB]
[17179593.264000] ibm_acpi: ec object not found
[17179593.300000] pcc_acpi: loading...
[17179596.612000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179596.612000] apm: disabled - APM is not SMP safe.
[17179599.812000] eth0: no IPv6 routers present
[17179600.956000] Bluetooth: Core ver 2.8
[17179600.956000] NET: Registered protocol family 31
[17179600.956000] Bluetooth: HCI device and connection manager initialized
[17179600.956000] Bluetooth: HCI socket layer initialized
[17179600.984000] Bluetooth: L2CAP ver 2.8
[17179600.984000] Bluetooth: L2CAP socket layer initialized
[17179601.028000] Bluetooth: RFCOMM socket layer initialized
[17179601.028000] Bluetooth: RFCOMM TTY layer initialized
[17179601.028000] Bluetooth: RFCOMM ver 1.7
[17179910.424000] kjournald starting.  Commit interval 5 seconds
[17179910.424000] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[17179910.504000] EXT3 FS on sda1, internal journal
[17179910.504000] EXT3-fs: mounted filesystem with ordered data mode.
[17182835.184000] ibm_acpi: ec object not found
[17204947.268000] usb 1-8: new high speed USB device using ehci_hcd and address 4
[17204947.404000] usb 1-8: configuration #1 chosen from 1 choice
[17205046.844000] ndiswrapper version 1.26 loaded (preempt=no,smp=yes)
[17205046.964000] usb 1-8: reset high speed USB device using ehci_hcd and address 4
[17205047.100000] ndiswrapper: driver athfmwdl (,12/05/2003,1.00.001) loaded
[17205047.100000] ndiswrapper (add_bin_file:320): couldn't allocate memory
[17205047.100000] ndiswrapper (get_bin_file:282): loadndiswrapper failed (59904); check system log for messages from 'loadndisdriver'
[17205047.104000] usbcore: registered new driver ndiswrapper
bozo@bozo-box:~/Desktop/WG111T_GR V1.2$ ndiswrapper -l
installed drivers:
athfmwdl                driver installed, hardware (1385:4251) present 
netwg11t                driver installed 
bozo@bozo-box:~/Desktop/WG111T_GR V1.2$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

```

---

