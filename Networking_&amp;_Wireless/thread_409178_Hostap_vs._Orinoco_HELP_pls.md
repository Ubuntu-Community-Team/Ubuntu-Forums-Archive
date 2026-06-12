---
title: "Hostap vs. Orinoco HELP pls"
date: 2007-04-14
forum: Networking &amp; Wireless
---

### Post by matoxxx on 2007-04-14
Hello all, i am trying to switch from orinoco drivers to hostap, but came across some issues.
So far, i have no problems using default orinoco drivers for my card 

```
0000:02:02.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
        Subsystem: Intersil Corporation Prism 2.5 Wavelan chipset
        Flags: bus master, medium devsel, latency 128, IRQ 209
        Memory at dfeff000 (32-bit, prefetchable) [size=4K]
        Capabilities: [dc] Power Management version 2

```

but when i tried to instal hostap drivers using *alternative* method
 /// dl hostap driver, compiling without instaling, just copying .ko files to /lib/modules and config file to /etc/pcmcia /// 
i came to these errors ...
my wifi card after reboot , using hostap driver /and blacklisted orinoco/ was detected twice as wifi0 /new-suggesting hostap detection/ and eth0 /old dont know what else is detecting it/, but both of them didnt work , wifi0 could connect to network, but no internet, eth0 didnt work at all

```
matoxxx@matoxxx-desktop:~$ dmesg | grep hostap
[17179588.684000] hostap_crypt: registered algorithm 'NULL'
[17179588.696000] hostap_pci: 0.4.9 - 2006-05-06 (Jouni Malinen <jkmaline@cc.hut.fi>)
[17179588.696000] hostap_pci: Registered netdevice wifi0
[17179588.964000] wifi0: could not initialize WEP: load module hostap_crypt_wep.o
[17179805.684000] hostap_crypt: registered algorithm 'WEP'

```

maybe this is the cause ? dont know :( 

```
matoxxx@matoxxx-desktop:~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:57 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4962 (4.8 KiB)  TX bytes:4962 (4.8 KiB)

wifi0     Link encap:UNSPEC  HWaddr 00-60-B3-64-6D-9F-00-00-00-00-00-00-00-00-00 -00
          inet addr:192.168.0.105  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:105 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:125 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:8625 (8.4 KiB)  TX bytes:0 (0.0 b)
          Interrupt:209 Memory:e0966000-e0967000


wifi0     IEEE 802.11b  ESSID:"lukromtel"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:4F:62:0F:84:1B
          Bit Rate:2 Mb/s   Sensitivity=1/3
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Power Management:off

eth0      IEEE 802.11b  ESSID:"lukromtel"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:4F:62:0F:84:1B
          Bit Rate:2 Mb/s   Sensitivity=1/3
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=35/70  Signal level=-57 dBm  Noise level=-93 dBm
          Rx invalid nwid:0  Rx invalid crypt:1069  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:11103   Missed beacon:0
```


```
dmesg

[17179569.184000] Linux version 2.6.15-28-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Thu Feb 1 15:51:56 UTC 2007
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001ffd0000 (usable)
[17179569.184000]  BIOS-e820: 000000001ffd0000 - 000000001ffde000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000001ffde000 - 0000000020000000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 511MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000ff780
[17179569.184000] On node 0 totalpages: 131024
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 126928 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI 2.3 present.
[17179569.184000] ATI board detected. Disabling timer routing over 8254.
[17179569.184000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x000f9520
[17179569.184000] ACPI: RSDT (v001 A M I  OEMRSDT  0x08000519 MSFT 0x00000097) @ 0x1ffd0000
[17179569.184000] ACPI: FADT (v002 A M I  OEMFACP  0x08000519 MSFT 0x00000097) @ 0x1ffd0200
[17179569.184000] ACPI: MADT (v001 A M I  OEMAPIC  0x08000519 MSFT 0x00000097) @ 0x1ffd0390
[17179569.184000] ACPI: MCFG (v001 A M I  OEMMCFG  0x08000519 MSFT 0x00000097) @ 0x1ffd03f0
[17179569.184000] ACPI: SSDT (v001    ATI ATIPATCH 0x00000001 INTL 0x02002026) @ 0x1ffd3ed0
[17179569.184000] ACPI: OEMB (v001 A M I  AMI_OEM  0x08000519 MSFT 0x00000097) @ 0x1ffde040
[17179569.184000] ACPI: DSDT (v001  1ABZR 1ABZR002 0x00000002 INTL 0x02002026) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x808
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:12 APIC version 16
[17179569.184000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 1, version 33, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: BIOS IRQ0 pin2 override ignored.
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 30000000 (gap: 20000000:df780000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/sda7 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[17179569.184000] Detected 1994.456 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179569.640000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179569.640000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.648000] Memory: 508724k/524096k available (1977k kernel code, 14800k reserved, 605k data, 288k init, 0k highmem)
[17179569.648000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.728000] Calibrating delay using timer specific routine.. 3995.00 BogoMIPS (lpj=7990009)
[17179569.728000] Security Framework v1.0.0 initialized
[17179569.728000] SELinux:  Disabled at boot.
[17179569.728000] Mount-cache hash table entries: 512
[17179569.728000] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
[17179569.728000] CPU: After vendor identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
[17179569.728000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179569.728000] CPU: L2 Cache: 512K (64 bytes/line)
[17179569.728000] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000001
[17179569.728000] mtrr: v2.0 (20020519)
[17179569.728000] CPU: AMD Athlon(tm) 64 Processor 3000+ stepping 02
[17179569.728000] Enabling fast FPU save and restore... done.
[17179569.728000] Enabling unmasked SIMD FPU exception support... done.
[17179569.728000] Checking 'hlt' instruction... OK.
[17179569.744000] checking if image is initramfs... it is
[17179570.228000] Freeing initrd memory: 6616k freed
[17179570.236000] ACPI: Looking for DSDT ... not found!
[17179570.236000] ENABLING IO-APIC IRQs
[17179570.240000] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[17179570.380000] NET: Registered protocol family 16
[17179570.380000] EISA bus registered
[17179570.380000] ACPI: bus type pci registered
[17179570.380000] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=2
[17179570.380000] PCI: Using MMCONFIG
[17179570.380000] ACPI: Subsystem revision 20051216
[17179572.584000] ACPI: Interpreter enabled
[17179572.584000] ACPI: Using IOAPIC for interrupt routing
[17179572.584000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179572.584000] PCI: Probing PCI hardware (bus 00)
[17179572.584000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:14.1
[17179572.588000] Boot video device is 0000:01:00.0
[17179572.588000] PCI: Transparent bridge - 0000:00:14.4
[17179572.588000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179572.596000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
[17179572.604000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[17179572.604000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[17179572.604000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[17179572.604000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[17179572.604000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[17179572.604000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[17179572.604000] ACPI: PCI Interrupt Link [LNKF] (IRQs 9) *0, disabled.
[17179572.604000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[17179572.604000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[17179572.604000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179572.604000] pnp: PnP ACPI init
[17179572.608000] pnp: PnP ACPI: found 15 devices
[17179572.608000] PnPBIOS: Disabled by ACPI PNP
[17179572.608000] PCI: Using ACPI for IRQ routing
[17179572.608000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179572.620000] pnp: 00:0c: ioport range 0x600-0x60f has been reserved
[17179572.620000] PCI: Bridge: 0000:00:02.0
[17179572.620000]   IO window: 7000-7fff
[17179572.620000]   MEM window: ff200000-ff2fffff
[17179572.620000]   PREFETCH window: bfe00000-dfdfffff
[17179572.620000] PCI: Bridge: 0000:00:14.4
[17179572.620000]   IO window: 8000-8fff
[17179572.620000]   MEM window: ff300000-ff3fffff
[17179572.620000]   PREFETCH window: dfe00000-dfefffff
[17179572.620000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[17179572.620000] audit: initializing netlink socket (disabled)
[17179572.620000] audit(1176561417.620:1): initialized
[17179572.620000] VFS: Disk quotas dquot_6.5.1
[17179572.620000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179572.620000] Initializing Cryptographic API
[17179572.620000] io scheduler noop registered
[17179572.620000] io scheduler anticipatory registered
[17179572.620000] io scheduler deadline registered
[17179572.620000] io scheduler cfq registered
[17179572.620000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[17179572.620000] pcie_portdrv_probe->Dev[5a34:1002] has invalid IRQ. Check vendor BIOS
[17179572.620000] assign_interrupt_mode Found MSI capability
[17179572.620000] Allocate Port Service[pcie00]
[17179572.620000] Allocate Port Service[pcie01]
[17179572.620000] Allocate Port Service[pcie03]
[17179572.620000] isapnp: Scanning for PnP cards...
[17179572.976000] isapnp: No Plug & Play device found
[17179572.988000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[17179572.988000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179572.988000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179572.988000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179572.988000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179572.988000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179572.992000] 00:04: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179572.992000] 00:05: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179572.992000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179572.992000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179572.992000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179572.992000] mice: PS/2 mouse device common for all mice
[17179572.992000] EISA: Probing bus 0 at eisa.0
[17179572.992000] Cannot allocate resource for EISA slot 7
[17179572.992000] Cannot allocate resource for EISA slot 8
[17179572.992000] EISA: Detected 0 cards.
[17179572.992000] NET: Registered protocol family 2
[17179573.016000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179573.028000] IP route cache hash table entries: 8192 (order: 3, 32768 bytes)
[17179573.028000] TCP established hash table entries: 32768 (order: 5, 131072 bytes)
[17179573.028000] TCP bind hash table entries: 32768 (order: 5, 131072 bytes)
[17179573.028000] TCP: Hash tables configured (established 32768 bind 32768)
[17179573.028000] TCP reno registered
[17179573.028000] TCP bic registered
[17179573.028000] NET: Registered protocol family 1
[17179573.028000] NET: Registered protocol family 8
[17179573.028000] NET: Registered protocol family 20
[17179573.028000] Using IPI Shortcut mode
[17179573.028000] ACPI wakeup devices:
[17179573.028000] PCE2 PCE3 PCE4 PCE5 PCE6 PCE7 SBAZ PS2K PS2M AC97 MC97 USB1 USB2 EUSB P0P9 PWRB
[17179573.028000] ACPI: (supports S0 S1 S3 S4 S5)
[17179573.028000] Freeing unused kernel memory: 288k freed
[17179573.064000] vga16fb: initializing
[17179573.064000] vga16fb: mapped to 0xc00a0000
[17179573.188000] Console: switching to colour frame buffer device 80x25
[17179573.188000] fb0: VGA16 VGA frame buffer device
[17179574.324000] Capability LSM initialized
[17179574.732000] SCSI subsystem initialized
[17179574.736000] ACPI: bus type scsi registered
[17179574.736000] libata version 1.20 loaded.
[17179574.736000] sata_sil 0000:00:11.0: version 0.9
[17179574.736000] ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 23 (level, low) -> IRQ 201
[17179574.736000] ata1: SATA max UDMA/100 cmd 0xE083AC80 ctl 0xE083AC8A bmdma 0xE083AC00 irq 201
[17179574.736000] ata2: SATA max UDMA/100 cmd 0xE083ACC0 ctl 0xE083ACCA bmdma 0xE083AC08 irq 201
[17179575.104000] ata1: dev 0 cfg 00:0c5a 49:2f00 82:346b 83:7d01 84:4003 85:3469 86:3c01 87:4003 88:407f 93:0000
[17179575.104000] ata1: dev 0 ATA-6, max UDMA/133, 156301488 sectors: LBA48
[17179575.104000] sata_get_dev_handle: SATA dev addr=0x110000, handle=0xdffb6520
[17179575.108000] ata1: dev 0 configured for UDMA/100
[17179575.108000] sata_get_dev_handle: SATA dev addr=0x110000, handle=0xdffb6520
[17179575.112000] scsi0 : sata_sil
[17179575.316000] ata2: no device found (phy stat 00000000)
[17179575.316000] scsi1 : sata_sil
[17179575.316000]   Vendor: ATA       Model: ST380817AS        Rev: 3.42
[17179575.316000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[17179575.316000] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 209
[17179575.316000] ata3: SATA max UDMA/100 cmd 0xE0878880 ctl 0xE087888A bmdma 0xE0878800 irq 209
[17179575.316000] ata4: SATA max UDMA/100 cmd 0xE08788C0 ctl 0xE08788CA bmdma 0xE0878808 irq 209
[17179575.520000] ata3: no device found (phy stat 00000000)
[17179575.520000] scsi2 : sata_sil
[17179575.724000] ata4: no device found (phy stat 00000000)
[17179575.724000] scsi3 : sata_sil
[17179575.728000] Driver 'sd' needs updating - please use bus_type methods
[17179575.728000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[17179575.728000] SCSI device sda: drive cache: write back
[17179575.732000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[17179575.732000] SCSI device sda: drive cache: write back
[17179575.732000]  sda: sda1 sda2 sda3 < sda5 sda6 sda7 sda8 > sda4
[17179575.800000] sd 0:0:0:0: Attached scsi disk sda
[17179576.328000] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[17179576.328000] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 217
[17179576.328000] ATIIXP: chipset revision 0
[17179576.328000] ATIIXP: not 100% native mode: will probe irqs later
[17179576.328000]     ide0: BM-DMA at 0xff00-0xff07, BIOS settings: hda:pio, hdb:pio
[17179576.328000]     ide1: BM-DMA at 0xff08-0xff0f, BIOS settings: hdc:DMA, hdd:pio
[17179576.328000] Probing IDE interface ide0...
[17179576.900000] Probing IDE interface ide1...
[17179577.636000] hdc: HL-DT-ST DVDRAM GSA-4163B, ATAPI CD/DVD-ROM drive
[17179577.972000] ide1 at 0x170-0x177,0x376 on irq 15
[17179577.980000] hdc: ATAPI 40X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179577.980000] Uniform CD-ROM driver Revision: 3.20
[17179578.052000] usbcore: registered new driver usbfs
[17179578.052000] usbcore: registered new driver hub
[17179578.052000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179578.052000] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 225
[17179578.052000] ohci_hcd 0000:00:13.0: OHCI Host Controller
[17179578.120000] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[17179578.120000] ohci_hcd 0000:00:13.0: irq 225, io mem 0xff6fe000
[17179578.180000] hub 1-0:1.0: USB hub found
[17179578.180000] hub 1-0:1.0: 4 ports detected
[17179578.284000] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 225
[17179578.284000] ohci_hcd 0000:00:13.1: OHCI Host Controller
[17179578.312000] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[17179578.312000] ohci_hcd 0000:00:13.1: irq 225, io mem 0xff6fd000
[17179578.372000] hub 2-0:1.0: USB hub found
[17179578.372000] hub 2-0:1.0: 4 ports detected
[17179578.476000] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 225
[17179578.476000] ehci_hcd 0000:00:13.2: EHCI Host Controller
[17179578.476000] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[17179578.476000] ehci_hcd 0000:00:13.2: irq 225, io mem 0xff6fc000
[17179578.476000] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179578.476000] hub 3-0:1.0: USB hub found
[17179578.476000] hub 3-0:1.0: 8 ports detected
[17179578.600000] Probing IDE interface ide0...
[17179579.288000] Attempting manual resume
[17179579.308000] kjournald starting.  Commit interval 5 seconds
[17179579.308000] EXT3-fs: mounted filesystem with ordered data mode.
[17179579.344000] usb 1-3: new full speed USB device using ohci_hcd and address 3
[17179586.184000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179586.768000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179586.768000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179586.856000] Linux agpgart interface v0.101 (c) Dave Jones
[17179587.444000] Real Time Clock Driver v1.12
[17179587.544000] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> IRQ 233
[17179588.260000] input: ImPS/2 Generic Wheel Mouse as /class/input/input1
[17179588.292000] Initializing USB Mass Storage driver...
[17179588.292000] input: PC Speaker as /class/input/input2
[17179588.296000] ieee80211_crypt: registered algorithm 'NULL'
[17179588.328000] parport: PnPBIOS parport detected.
[17179588.328000] parport0: PC-style at 0x3bc, irq 7 [PCSPP]
[17179588.332000] scsi4 : SCSI emulation for USB Mass Storage devices
[17179588.332000] usb-storage: device found at 3
[17179588.332000] usb-storage: waiting for device to settle before scanning
[17179588.332000] usbcore: registered new driver usb-storage
[17179588.332000] USB Mass Storage support registered.
[17179588.344000] ts: Compaq touchscreen protocol output
[17179588.360000] FDC 0 is a post-1991 82077
[17179588.684000] hostap_crypt: registered algorithm 'NULL'
[17179588.696000] hostap_pci: 0.4.9 - 2006-05-06 (Jouni Malinen <jkmaline@cc.hut.fi>)
[17179588.696000] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 22 (level, low) -> IRQ 209
[17179588.696000] hostap_pci: Registered netdevice wifi0
[17179588.696000] wifi0: Original COR value: 0x0
[17179588.892000] prism2_hw_init: initialized in 192 ms
[17179588.896000] wifi0: NIC: id=0x8013 v1.0.0
[17179588.896000] wifi0: PRI: id=0x15 v1.1.1
[17179588.896000] wifi0: STA: id=0x1f v1.7.4
[17179588.900000] wifi0: Intersil Prism2.5 PCI: mem=0xdfeff000, irq=209
[17179588.900000] wifi0: registered netdevice wlan0
[17179588.964000] wifi0: could not initialize WEP: load module hostap_crypt_wep.o
[17179589.288000] lp0: using parport0 (interrupt-driven).
[17179589.324000] Adding 1052212k swap on /dev/sda6.  Priority:-1 extents:1 across:1052212k
[17179589.468000] EXT3 FS on sda7, internal journal
[17179589.580000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179589.580000] md: bitmap version 4.39
[17179589.956000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[17179590.616000] cdrom: open failed.
[17179591.420000] wifi0: LinkStatus=1 (Connected)
[17179591.420000] wifi0: LinkStatus: BSSID=00:4f:62:0f:84:1b
[17179591.864000] kjournald starting.  Commit interval 5 seconds
[17179591.864000] EXT3 FS on sda2, internal journal
[17179591.864000] EXT3-fs: mounted filesystem with ordered data mode.
[17179592.024000] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
[17179592.024000] SGI XFS Quota Management subsystem
[17179592.048000] XFS mounting filesystem sda5
[17179592.112000] Ending clean XFS mount for filesystem: sda5
[17179593.336000]   Vendor: LEXAR     Model: JUMPDRIVE         Rev: 1.30
[17179593.336000]   Type:   Direct-Access                      ANSI SCSI revision: 01 CCS
[17179593.348000] SCSI device sdb: 503808 512-byte hdwr sectors (258 MB)
[17179593.352000] sdb: Write Protect is off
[17179593.352000] sdb: Mode Sense: 23 00 00 00
[17179593.352000] sdb: assuming drive cache: write through
[17179593.376000] SCSI device sdb: 503808 512-byte hdwr sectors (258 MB)
[17179593.384000] sdb: Write Protect is off
[17179593.384000] sdb: Mode Sense: 23 00 00 00
[17179593.384000] sdb: assuming drive cache: write through
[17179593.384000]  sdb: sdb1
[17179593.392000] sd 4:0:0:0: Attached scsi removable disk sdb
[17179593.392000] sd 4:0:0:0: Attached scsi generic sg1 type 0
[17179593.392000] usb-storage: device scan complete
[17179594.044000] NET: Registered protocol family 17
[17179594.292000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179594.840000] ACPI: Power Button (FF) [PWRF]
[17179594.840000] ACPI: Power Button (CM) [PWRB]
[17179594.916000] ibm_acpi: ec object not found
[17179594.944000] pcc_acpi: loading...
[17179595.292000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179595.396000] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.50.4)
[17179595.404000] powernow-k8: BIOS error - no PSB or ACPI _PSS objects
[17179596.292000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179597.296000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179598.296000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179599.296000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179601.372000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[17179601.372000] [fglrx] Maximum main memory to use for locked dma buffers: 431 MBytes.
[17179601.372000] [fglrx] module loaded - fglrx 8.33.6 [Jan  8 2007] on minor 0
[17179601.392000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 18 (level, low) -> IRQ 50
[17179602.620000] [fglrx] total      GART = 130023424
[17179602.620000] [fglrx] free       GART = 114032640
[17179602.620000] [fglrx] max single GART = 114032640
[17179602.620000] [fglrx] total      LFB  = 268304384
[17179602.620000] [fglrx] free       LFB  = 250474496
[17179602.620000] [fglrx] max single LFB  = 250474496
[17179602.620000] [fglrx] total      Inv  = 0
[17179602.620000] [fglrx] free       Inv  = 0
[17179602.620000] [fglrx] max single Inv  = 0
[17179602.620000] [fglrx] total      TIM  = 0
[17179603.068000] ppdev: user-space parallel port driver
[17179603.300000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179603.540000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179603.540000] apm: overridden by ACPI.
[17179603.808000] Bluetooth: Core ver 2.8
[17179603.808000] NET: Registered protocol family 31
[17179603.808000] Bluetooth: HCI device and connection manager initialized
[17179603.808000] Bluetooth: HCI socket layer initialized
[17179603.828000] Bluetooth: L2CAP ver 2.8
[17179603.828000] Bluetooth: L2CAP socket layer initialized
[17179603.832000] Bluetooth: RFCOMM socket layer initialized
[17179603.832000] Bluetooth: RFCOMM TTY layer initialized
[17179603.832000] Bluetooth: RFCOMM ver 1.7
[17179604.300000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179605.300000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179608.304000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179609.304000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179610.304000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179611.308000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179612.308000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179613.308000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179614.812000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17179617.312000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179618.312000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179619.312000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179622.316000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179623.316000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179624.316000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179625.320000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179626.320000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179627.320000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179631.324000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179632.324000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179633.324000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179636.328000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179637.328000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179638.328000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179639.332000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179640.332000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179641.332000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179645.336000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179646.336000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179647.336000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179650.340000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179651.340000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179652.340000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179653.344000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179654.344000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179655.344000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179659.348000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179660.348000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179661.348000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179664.352000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179665.352000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179666.352000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179667.356000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179668.356000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179669.356000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179673.360000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179674.360000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179675.360000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179678.364000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179679.364000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179680.364000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179681.368000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179682.368000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179683.368000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179687.372000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179688.372000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179689.372000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179692.376000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179693.376000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179694.376000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179695.380000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179696.380000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179697.380000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179727.844000] wifi0: LinkStatus=1 (Connected)
[17179727.844000] wifi0: LinkStatus: BSSID=00:4f:62:0f:84:1b
[17179746.076000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179747.076000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179748.076000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179751.088000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179752.088000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179753.088000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179805.684000] hostap_crypt: registered algorithm 'WEP'
[17179807.768000] wifi0: LinkStatus=2 (Disconnected)
[17179807.768000] wifi0: LinkStatus: BSSID=44:44:44:44:44:44
[17179810.292000] wifi0: LinkStatus=1 (Connected)
[17179810.292000] wifi0: LinkStatus: BSSID=00:4f:62:0f:84:1b
[17179812.808000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179813.808000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179814.808000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179815.812000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179816.812000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179817.812000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179821.816000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179822.816000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179823.816000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179826.820000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179827.820000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179828.820000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179829.824000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179830.824000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179831.824000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179833.260000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179834.260000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179835.260000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179836.288000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179837.288000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179838.288000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179839.292000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179840.292000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179841.292000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179843.296000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179844.296000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179845.296000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179849.840000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179850.840000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179851.840000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179854.844000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179855.844000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179856.844000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179857.848000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179858.848000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179859.848000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179863.852000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179864.852000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179865.852000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179868.856000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179869.856000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179870.856000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179871.860000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179872.860000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179873.860000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179877.864000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179878.864000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179879.864000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179882.868000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179883.868000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179884.868000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179885.872000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179886.872000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179887.872000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179891.876000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179892.876000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179893.876000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179896.880000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179897.880000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179898.880000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179899.884000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179900.884000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179901.884000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179905.888000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179906.888000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179907.888000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179910.892000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179911.892000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179912.892000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179913.896000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179914.896000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[17179915.896000] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)

```

if you have any idea how can i use hostap, please post it

---

### Post by matoxxx on 2007-04-14
bump ... weird

after writing this post i tried swich modules without restart using 
```
modprobe -r orinoco_pci
modprobe hostap_pci
```

and it works ?! really weird

i do some testing and post results

---

### Post by matoxxx on 2007-04-14
So the results, 
:( 
i ended with 2 detected devices, even when i blacklisted all other drivers, the old one eth0 working on hostap drivers /kismet working too :D / flawlessly, newly added device wifi0 /added by hostap drivers/ seems not working, weird thing is they are both active at same time ?????

switching between devices in gnome network manager makes them both unusable :confused: 

ahh, what is this

---

### Post by hotplainrice on 2007-04-16
Yep... Having the same problem..

hostap and orinoco are loaded together.
The thing is iwconfig shows only wlan0 with no wireless extensions. WeirD!

im on feisty.

---

### Post by matoxxx on 2007-04-17
Have you tried blaklisting all other drivers inluding orinoco and orinoco_pci  ? in etc/modprobe.d/blacklist ?


this is my blasklist

```
# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394
blacklist orinoco_pci
blacklist orinoco
blacklist hermes
blacklist p80211
blacklist prism2_pci
```

---

### Post by npcomplete on 2007-05-21
I am having the same problem. Are there any solutions to this problem? I have been trying to switch orinoco driver to hostap for weeks...

---

