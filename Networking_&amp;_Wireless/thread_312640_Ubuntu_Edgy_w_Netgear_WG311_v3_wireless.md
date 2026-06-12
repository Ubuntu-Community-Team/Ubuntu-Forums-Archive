---
title: "Ubuntu Edgy w/ Netgear WG311 v3 wireless"
date: 2006-12-04
forum: Networking &amp; Wireless
---

### Post by burke9688 on 2006-12-04
I recently installed Ubuntu 6.10 [Edgy EFT] with Gnome 2.16.1. I installed it on my second harddrive, making it hard for me to get a wireless connection. My computer is mounted in my room so I cant bring it close enough to our router to get a ethernet connection. 

So what I'm saying is.
Under Device Manager, Ubuntu says that my NetGear card is installed in my computer. But when (obviously) I put my NetGear cd in the cd-drive, I dont know what to do, if anything with the files on the cd.

Jus tryin to get away from windows, a friend said this is thee best choice.


Jakey

---

### Post by FrodoB on 2006-12-04
Publish the outputs of:

lspci -v

iwconfig

dmesg


From what I see on the web, it looks to be a Marvell chipset. Here is an instruction for a Marvell chipset device using ndiswrapper:

[https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29)

---

### Post by burke9688 on 2006-12-04
Since I'm insatlling it on this computer, And I have to re-boot to check this post again. I didnt see that you added another thing for me to post. So here are the results of iWconfig and dMesg


iWconfig;
```
jacob@jacob-desktop:~$ iwconfig

lo no wireless extensions.



eth0 no wireless extensions.



sit0 no wireless extensions.
```













dMesg
```

jacob@jacob-desktop:~$ dmesg

[17179569.184000] Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)

[17179569.184000] BIOS-provided physical RAM map:

[17179569.184000] BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)

[17179569.184000] BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)

[17179569.184000] BIOS-e820: 00000000000e6000 - 0000000000100000 (reserved)

[17179569.184000] BIOS-e820: 0000000000100000 - 000000001ef30000 (usable)

[17179569.184000] BIOS-e820: 000000001ef30000 - 000000001ef40000 (ACPI data)

[17179569.184000] BIOS-e820: 000000001ef40000 - 000000001eff0000 (ACPI NVS)

[17179569.184000] BIOS-e820: 000000001eff0000 - 000000001f000000 (reserved)

[17179569.184000] BIOS-e820: 00000000fecf0000 - 00000000fecf1000 (reserved)

[17179569.184000] BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)

[17179569.184000] 0MB HIGHMEM available.

[17179569.184000] 495MB LOWMEM available.

[17179569.184000] found SMP MP-table at 000ff780

[17179569.184000] On node 0 totalpages: 126768

[17179569.184000] DMA zone: 4096 pages, LIFO batch:0

[17179569.184000] Normal zone: 122672 pages, LIFO batch:31

[17179569.184000] DMI 2.3 present.

[17179569.184000] ACPI: RSDP (v000 ACPIAM ) @ 0x000f5a20

[17179569.184000] ACPI: RSDT (v001 GATEWA N2DTM019 0x20030801 MSFT 0x00000097) @ 0x1ef30000

[17179569.184000] ACPI: FADT (v002 GATEWA N2DTM019 0x20030801 MSFT 0x00000097) @ 0x1ef30200

[17179569.184000] ACPI: MADT (v001 GATEWA N2DTM019 0x20030801 MSFT 0x00000097) @ 0x1ef30300

[17179569.184000] ACPI: ASF! (v016 LEGEND I865PASF 0x00000001 MSFT 0x0100000d) @ 0x1ef344e0

[17179569.184000] ACPI: WDDT (v001 INTEL OEMWDDT 0x00000001 MSFT 0x0100000d) @ 0x1ef34579

[17179569.184000] ACPI: DSDT (v001 GATEWA N2DTM019 0x00000001 MSFT 0x0100000d) @ 0x00000000

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

[17179569.184000] Enabling APIC mode: Flat. Using 1 I/O APICs

[17179569.184000] Using ACPI (MADT) for SMP configuration information

[17179569.184000] Allocating PCI resources starting at 20000000 (gap: 1f000000:dfcf0000)

[17179569.184000] Built 1 zonelists

[17179569.184000] Kernel command line: root=/dev/hdb2 ro quiet splash

[17179569.184000] mapped APIC to ffffd000 (fee00000)

[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)

[17179569.184000] Enabling fast FPU save and restore... done.

[17179569.184000] Enabling unmasked SIMD FPU exception support... done.

[17179569.184000] Initializing CPU#0

[17179569.184000] PID hash table entries: 2048 (order: 11, 8192 bytes)

[17179569.184000] Detected 2793.425 MHz processor.

[17179569.184000] Using pmtmr for high-res timesource

[17179569.184000] Console: colour VGA+ 80x25

[17179569.632000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)

[17179569.632000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)

[17179569.640000] Memory: 492776k/507072k available (1910k kernel code, 13748k reserved, 1070k data, 308k init, 0k highmem)

[17179569.640000] Checking if this processor honours the WP bit even in supervisor mode... Ok.

[17179569.720000] Calibrating delay using timer specific routine.. 5597.84 BogoMIPS (lpj=11195692)

[17179569.720000] Security Framework v1.0.0 initialized

[17179569.720000] SELinux: Disabled at boot.

[17179569.720000] Mount-cache hash table entries: 512

[17179569.720000] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000

[17179569.720000] CPU: After vendor identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000

[17179569.720000] CPU: Trace cache: 12K uops, L1 D cache: 8K

[17179569.720000] CPU: L2 cache: 512K

[17179569.720000] CPU: Hyper-Threading is disabled

[17179569.720000] CPU: After all inits, caps: bfebfbff 00000000 00000000 00000080 00004400 00000000 00000000

[17179569.720000] Checking 'hlt' instruction... OK.

[17179569.736000] SMP alternatives: switching to UP code

[17179569.736000] checking if image is initramfs... it is

[17179570.188000] Freeing initrd memory: 5564k freed

[17179570.188000] ACPI: Core revision 20060707

[17179570.188000] ACPI: Looking for DSDT ... not found!

[17179570.192000] CPU0: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 09

[17179570.192000] SMP alternatives: switching to SMP code

[17179570.192000] Booting processor 1/1 eip 3000

[17179570.200000] Initializing CPU#1

[17179570.284000] Calibrating delay using timer specific routine.. 5586.70 BogoMIPS (lpj=11173408)

[17179570.284000] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000

[17179570.284000] CPU: After vendor identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000

[17179570.284000] CPU: Trace cache: 12K uops, L1 D cache: 8K

[17179570.284000] CPU: L2 cache: 512K

[17179570.284000] CPU: Hyper-Threading is disabled

[17179570.284000] CPU: After all inits, caps: bfebfbff 00000000 00000000 00000080 00004400 00000000 00000000

[17179570.284000] CPU1: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 09

[17179570.284000] Total of 2 processors activated (11184.55 BogoMIPS).

[17179570.284000] ENABLING IO-APIC IRQs

[17179570.284000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1

[17179570.428000] checking TSC synchronization across 2 CPUs: passed.

[17179570.432000] Brought up 2 CPUs

[17179570.448000] migration_cost=4000

[17179570.448000] NET: Registered protocol family 16

[17179570.448000] EISA bus registered

[17179570.448000] ACPI: bus type pci registered

[17179570.448000] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1

[17179570.448000] PCI: Using configuration type 1

[17179570.448000] Setting up standard PCI resources

[17179570.464000] ACPI: Interpreter enabled

[17179570.464000] ACPI: Using IOAPIC for interrupt routing

[17179570.464000] ACPI: PCI Root Bridge [PCI0] (0000:00)

[17179570.464000] PCI: Probing PCI hardware (bus 00)

[17179570.464000] Boot video device is 0000:00:02.0

[17179570.464000] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO

[17179570.464000] PCI quirk: region 0500-053f claimed by ICH4 GPIO

[17179570.464000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1

[17179570.464000] PCI: Transparent bridge - 0000:00:1e.0

[17179570.464000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]

[17179570.468000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]

[17179570.472000] ACPI: Power Resource [URP1] (off)

[17179570.472000] ACPI: Power Resource [FDDP] (off)

[17179570.472000] ACPI: Power Resource [LPTP] (off)

[17179570.472000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)

[17179570.472000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)

[17179570.472000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)

[17179570.472000] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 7 9 10 11 12 14 15)

[17179570.472000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)

[17179570.476000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)

[17179570.476000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.

[17179570.476000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)

[17179570.476000] Linux Plug and Play Support v0.97 (c) Adam Belay

[17179570.476000] pnp: PnP ACPI init

[17179570.480000] pnp: PnP ACPI: found 14 devices

[17179570.480000] PnPBIOS: Disabled by ACPI PNP

[17179570.480000] PCI: Using ACPI for IRQ routing

[17179570.480000] PCI: If a device doesn't work, try "pci=routeirq". If it helps, post a report

[17179570.484000] pnp: 00:0c: ioport range 0x400-0x47f could not be reserved

[17179570.484000] pnp: 00:0c: ioport range 0x680-0x6ff has been reserved

[17179570.484000] pnp: 00:0c: ioport range 0x500-0x53f has been reserved

[17179570.484000] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0

[17179570.484000] PCI: Bridge: 0000:00:1e.0

[17179570.484000] IO window: b000-bfff

[17179570.484000] MEM window: ff800000-ff8fffff

[17179570.484000] PREFETCH window: disabled.

[17179570.484000] PCI: Setting latency timer of device 0000:00:1e.0 to 64

[17179570.484000] NET: Registered protocol family 2

[17179570.524000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)

[17179570.524000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)

[17179570.524000] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)

[17179570.524000] TCP: Hash tables configured (established 16384 bind 8192)

[17179570.524000] TCP reno registered

[17179570.524000] audit: initializing netlink socket (disabled)

[17179570.524000] audit(1165257221.524:1): initialized

[17179570.524000] VFS: Disk quotas dquot_6.5.1

[17179570.524000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)

[17179570.524000] Initializing Cryptographic API

[17179570.524000] io scheduler noop registered

[17179570.524000] io scheduler anticipatory registered

[17179570.524000] io scheduler deadline registered

[17179570.524000] io scheduler cfq registered (default)

[17179570.524000] isapnp: Scanning for PnP cards...

[17179570.876000] isapnp: No Plug & Play device found

[17179570.900000] Real Time Clock Driver v1.12ac

[17179570.900000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled

[17179570.900000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A

[17179570.904000] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A

[17179570.904000] ACPI: PCI Interrupt 0000:01:02.0[A] -> GSI 17 (level, low) -> IRQ 169

[17179570.904000] 0000:01:02.0: ttyS1 at I/O 0xb808 (irq = 169) is a 16450

[17179570.904000] 0000:01:02.0: ttyS2 at I/O 0xb810 (irq = 169) is a 8250

[17179570.904000] 0000:01:02.0: ttyS3 at I/O 0xb818 (irq = 169) is a 16450

[17179570.904000] Couldn't register serial port 0000:01:02.0: -28

[17179570.904000] mice: PS/2 mouse device common for all mice

[17179570.904000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize

[17179570.904000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2

[17179570.904000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx

[17179570.904000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12

[17179570.908000] serio: i8042 AUX port at 0x60,0x64 irq 12

[17179570.908000] serio: i8042 KBD port at 0x60,0x64 irq 1

[17179570.908000] EISA: Probing bus 0 at eisa.0

[17179570.908000] EISA: Detected 0 cards.

[17179570.908000] TCP bic registered

[17179570.908000] NET: Registered protocol family 1

[17179570.908000] NET: Registered protocol family 8

[17179570.908000] NET: Registered protocol family 20

[17179570.908000] Starting balanced_irq

[17179570.908000] Using IPI No-Shortcut mode

[17179570.908000] ACPI: (supports S0 S1 S3 S4 S5)

[17179570.908000] Freeing unused kernel memory: 308k freed

[17179570.932000] input: AT Translated Set 2 keyboard as /class/input/input0

[17179571.988000] Capability LSM initialized

[17179572.024000] ACPI: Processor [CPU1] (supports 8 throttling states)

[17179572.024000] ACPI: Processor [CPU2] (supports 8 throttling states)

[17179572.464000] ICH5: IDE controller at PCI slot 0000:00:1f.1

[17179572.464000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)

[17179572.464000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 177

[17179572.464000] ICH5: chipset revision 2

[17179572.464000] ICH5: not 100% native mode: will probe irqs later

[17179572.464000] ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:DMA

[17179572.464000] ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd:DMA

[17179572.464000] Probing IDE interface ide0...

[17179572.756000] hda: WDC WD800BB-53DKA0, ATA DISK drive

[17179573.036000] hdb: ST340014A, ATA DISK drive

[17179573.092000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14

[17179573.112000] Probing IDE interface ide1...

[17179573.848000] hdc: HL-DT-ST DVDRAM GSA-4040B, ATAPI CD/DVD-ROM drive

[17179574.632000] hdd: Lite-On LTN486S 48x Max, ATAPI CD/DVD-ROM drive

[17179574.688000] ide1 at 0x170-0x177,0x376 on irq 15

[17179574.700000] hda: max request size: 512KiB

[17179574.708000] hda: 156301488 sectors (80026 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)

[17179574.708000] hda: cache flushes supported

[17179574.708000] hda: hda1

[17179574.720000] hdb: max request size: 512KiB

[17179574.720000] hdb: 78125000 sectors (40000 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)

[17179574.720000] hdb: cache flushes supported

[17179574.720000] hdb: hdb1 hdb2 hdb3 < hdb5 >

[17179574.772000] hdc: ATAPI 32X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(66)

[17179574.772000] Uniform CD-ROM driver Revision: 3.20

[17179574.788000] hdd: ATAPI 48X CD-ROM drive, 120kB Cache, UDMA(33)

[17179575.280000] SCSI subsystem initialized

[17179575.280000] libata version 1.20 loaded.

[17179575.284000] ata_piix 0000:00:1f.2: version 1.05

[17179575.284000] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 18 (level, low) -> IRQ 177

[17179575.284000] PCI: Setting latency timer of device 0000:00:1f.2 to 64

[17179575.284000] ata1: SATA max UDMA/133 cmd 0xE800 ctl 0xE402 bmdma 0xD800 irq 177

[17179575.284000] ata2: SATA max UDMA/133 cmd 0xE000 ctl 0xDC02 bmdma 0xD808 irq 177

[17179575.448000] scsi0 : ata_piix

[17179575.612000] scsi1 : ata_piix

[17179575.672000] usbcore: registered new driver usbfs

[17179575.672000] usbcore: registered new driver hub

[17179575.676000] USB Universal Host Controller Interface driver v3.0

[17179575.676000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 185

[17179575.676000] PCI: Setting latency timer of device 0000:00:1d.0 to 64

[17179575.676000] uhci_hcd 0000:00:1d.0: UHCI Host Controller

[17179575.676000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1

[17179575.676000] uhci_hcd 0000:00:1d.0: irq 185, io base 0x0000c400

[17179575.676000] usb usb1: configuration #1 chosen from 1 choice

[17179575.676000] hub 1-0:1.0: USB hub found

[17179575.676000] hub 1-0:1.0: 2 ports detected

[17179575.780000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 193

[17179575.780000] PCI: Setting latency timer of device 0000:00:1d.1 to 64

[17179575.780000] uhci_hcd 0000:00:1d.1: UHCI Host Controller

[17179575.780000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2

[17179575.780000] uhci_hcd 0000:00:1d.1: irq 193, io base 0x0000c800

[17179575.780000] usb usb2: configuration #1 chosen from 1 choice

[17179575.780000] hub 2-0:1.0: USB hub found

[17179575.780000] hub 2-0:1.0: 2 ports detected

[17179575.884000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 177

[17179575.884000] PCI: Setting latency timer of device 0000:00:1d.2 to 64

[17179575.884000] uhci_hcd 0000:00:1d.2: UHCI Host Controller

[17179575.884000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3

[17179575.884000] uhci_hcd 0000:00:1d.2: irq 177, io base 0x0000cc00

[17179575.884000] usb usb3: configuration #1 chosen from 1 choice

[17179575.884000] hub 3-0:1.0: USB hub found

[17179575.884000] hub 3-0:1.0: 2 ports detected

[17179575.988000] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 185

[17179575.988000] PCI: Setting latency timer of device 0000:00:1d.3 to 64

[17179575.988000] uhci_hcd 0000:00:1d.3: UHCI Host Controller

[17179575.988000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4

[17179575.988000] uhci_hcd 0000:00:1d.3: irq 185, io base 0x0000d000

[17179575.988000] usb usb4: configuration #1 chosen from 1 choice

[17179575.988000] hub 4-0:1.0: USB hub found

[17179575.988000] hub 4-0:1.0: 2 ports detected

[17179576.092000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 201

[17179576.092000] PCI: Setting latency timer of device 0000:00:1d.7 to 64

[17179576.092000] ehci_hcd 0000:00:1d.7: EHCI Host Controller

[17179576.092000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5

[17179576.092000] ehci_hcd 0000:00:1d.7: debug port 1

[17179576.092000] PCI: cache line size of 128 is not supported by device 0000:00:1d.7

[17179576.092000] ehci_hcd 0000:00:1d.7: irq 201, io mem 0xffa7f400

[17179576.096000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004

[17179576.096000] usb usb5: configuration #1 chosen from 1 choice

[17179576.096000] hub 5-0:1.0: USB hub found

[17179576.096000] hub 5-0:1.0: 8 ports detected

[17179576.232000] Attempting manual resume

[17179576.264000] kjournald starting. Commit interval 5 seconds

[17179576.264000] EXT3-fs: mounted filesystem with ordered data mode.

[17179576.500000] usb 5-5: new high speed USB device using ehci_hcd and address 2

[17179576.648000] usb 5-5: configuration #1 chosen from 2 choices

[17179586.012000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5

[17179586.020000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4

[17179586.076000] hw_random hardware driver 1.0.0 loaded

[17179586.104000] Linux agpgart interface v0.101 (c) Dave Jones

[17179586.108000] agpgart: Detected an Intel 865 Chipset.

[17179586.108000] agpgart: Detected 16252K stolen memory.

[17179586.120000] agpgart: AGP aperture is 128M @ 0xf0000000

[17179586.320000] Floppy drive(s): fd0 is 1.44M

[17179586.340000] FDC 0 is a National Semiconductor PC87306

[17179586.540000] parport: PnPBIOS parport detected.

[17179586.540000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]

[17179586.616000] input: PC Speaker as /class/input/input1

[17179587.228000] usbcore: registered new driver libusual

[17179587.284000] Initializing USB Mass Storage driver...

[17179587.284000] scsi2 : SCSI emulation for USB Mass Storage devices

[17179587.284000] usb-storage: device found at 2

[17179587.284000] usb-storage: waiting for device to settle before scanning

[17179587.284000] usbcore: registered new driver usb-storage

[17179587.284000] USB Mass Storage support registered.

[17179587.300000] e100: Intel(R) PRO/100 Network Driver, 3.5.10-k2-NAPI

[17179587.300000] e100: Copyright(c) 1999-2005 Intel Corporation

[17179587.300000] ACPI: PCI Interrupt 0000:01:08.0[A] -> GSI 20 (level, low) -> IRQ 209

[17179587.324000] e100: eth0: e100_probe: addr 0xff8ff000, irq 209, MAC addr 00:07:E9:52:46:E4

[17179587.340000] input: ImPS/2 Generic Wheel Mouse as /class/input/input2

[17179587.348000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 169

[17179587.348000] PCI: Setting latency timer of device 0000:00:1f.5 to 64

[17179587.384000] ts: Compaq touchscreen protocol output

[17179587.668000] intel8x0_measure_ac97_clock: measured 58268 usecs

[17179587.668000] intel8x0: clocking to 48000

[17179587.792000] lp0: using parport0 (interrupt-driven).

[17179587.824000] Adding 160608k swap on /dev/disk/by-uuid/6ce75f06-5a2a-4395-b50c-0bf6c5ad6f59. Priority:-1 extents:1 across:160608k

[17179587.868000] EXT3 FS on hdb2, internal journal

[17179589.288000] NET: Registered protocol family 17

[17179592.288000] usb-storage: device scan complete

[17179592.288000] Vendor: Apple Model: iPod Rev: 1.62

[17179592.288000] Type: Direct-Access ANSI SCSI revision: 00

[17179592.308000] SCSI device sda: 58605119 512-byte hdwr sectors (30006 MB)

[17179592.308000] sda: Write Protect is off

[17179592.308000] sda: Mode Sense: 68 00 00 08

[17179592.308000] sda: assuming drive cache: write through

[17179592.312000] SCSI device sda: 58605119 512-byte hdwr sectors (30006 MB)

[17179592.312000] sda: Write Protect is off

[17179592.312000] sda: Mode Sense: 68 00 00 08

[17179592.312000] sda: assuming drive cache: write through

[17179592.312000] sda: sda1 sda2

[17179592.596000] sd 2:0:0:0: Attached scsi removable disk sda

[17179592.612000] sd 2:0:0:0: Attached scsi generic sg0 type 0

[17179592.704000] Buffer I/O error on device sda2, logical block 29222232

[17179592.704000] Buffer I/O error on device sda2, logical block 29222233

[17179592.704000] Buffer I/O error on device sda2, logical block 29222234

[17179592.704000] Buffer I/O error on device sda2, logical block 29222232

[17179592.704000] Buffer I/O error on device sda2, logical block 29222233

[17179592.704000] Buffer I/O error on device sda2, logical block 29222234

[17179592.704000] Buffer I/O error on device sda2, logical block 29222232

[17179592.704000] Buffer I/O error on device sda2, logical block 29222233

[17179592.704000] Buffer I/O error on device sda2, logical block 29222234

[17179592.704000] Buffer I/O error on device sda2, logical block 29222232

[17179593.588000] ACPI: Power Button (FF) [PWRF]

[17179593.588000] ACPI: Sleep Button (CM) [SLPB]

[17179593.740000] ibm_acpi: ec object not found

[17179593.784000] pcc_acpi: loading...

[17179595.864000] [drm] Initialized drm 1.0.1 20051102

[17179595.868000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 185

[17179595.868000] [drm] Initialized i915 1.5.0 20060119 on minor 0

[17179596.420000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)

[17179596.420000] apm: disabled - APM is not SMP safe.

[17179598.780000] printk: 14 messages suppressed.

[17179598.780000] Buffer I/O error on device sda2, logical block 29222232

[17179600.684000] Bluetooth: Core ver 2.8

[17179600.684000] NET: Registered protocol family 31

[17179600.684000] Bluetooth: HCI device and connection manager initialized

[17179600.684000] Bluetooth: HCI socket layer initialized

[17179600.712000] Bluetooth: L2CAP ver 2.8

[17179600.712000] Bluetooth: L2CAP socket layer initialized

[17179600.724000] Bluetooth: RFCOMM socket layer initialized

[17179600.724000] Bluetooth: RFCOMM TTY layer initialized

[17179600.724000] Bluetooth: RFCOMM ver 1.7

[17179605.276000] NET: Registered protocol family 10

[17179605.276000] lo: Disabled Privacy Extensions

[17179605.276000] IPv6 over IPv4 tunneling driver

[17179610.328000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
```


It's like 9 pages in word... 

And I'll get on that other thing yo uasked me to publish.
I'm trying to write down as much as possiblef rom that link you posted, as i cannot get internet yet with ubuntu.

---

### Post by FrodoB on 2006-12-04
Yes, it would appear that

lspci -v 

is the critical thing at this point.

---

### Post by burke9688 on 2006-12-04
LSPci -v

```

jacob@jacob-desktop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
Subsystem: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface
Flags: bus master, fast devsel, latency 0
Memory at f8000000 (32-bit, prefetchable) [size=64M]
Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02) (prog-if 00 [VGA])
Subsystem: Gateway 2000 Unknown device 2019
Flags: bus master, fast devsel, latency 0, IRQ 185
Memory at f0000000 (32-bit, prefetchable) [size=128M]
Memory at ffa80000 (32-bit, non-prefetchable) [size=512K]
I/O ports at ec00 [size=8]
Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
Subsystem: Gateway 2000 Unknown device 2019
Flags: bus master, medium devsel, latency 0, IRQ 185
I/O ports at c400 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
Subsystem: Gateway 2000 Unknown device 2019
Flags: bus master, medium devsel, latency 0, IRQ 193
I/O ports at c800 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
Subsystem: Gateway 2000 Unknown device 2019
Flags: bus master, medium devsel, latency 0, IRQ 177
I/O ports at cc00 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
Subsystem: Gateway 2000 Unknown device 2019
Flags: bus master, medium devsel, latency 0, IRQ 185
I/O ports at d000 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
Subsystem: Gateway 2000 Unknown device 2019
Flags: bus master, medium devsel, latency 0, IRQ 201
Memory at ffa7f400 (32-bit, non-prefetchable) [size=1K]
Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2) (prog-if 00 [Normal decode])
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
I/O behind bridge: 0000b000-0000bfff
Memory behind bridge: ff800000-ff8fffff

00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
Subsystem: Gateway 2000 Unknown device 2019
Flags: bus master, medium devsel, latency 0, IRQ 177
I/O ports at
I/O ports at
I/O ports at
I/O ports at
I/O ports at ffa0 [size=16]
Memory at 20000000 (32-bit, non-prefetchable) [size=1K]

00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
Subsystem: Gateway 2000 Unknown device 2019
Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 177
I/O ports at e800 [size=8]
I/O ports at e400 [size=4]
I/O ports at e000 [size=8]
I/O ports at dc00 [size=4]
I/O ports at d800 [size=16]

00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
Subsystem: Gateway 2000 Unknown device 2019
Flags: medium devsel, IRQ 9
I/O ports at d400 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
Subsystem: Gateway 2000 Unknown device 2019
Flags: bus master, medium devsel, latency 0, IRQ 169
Memory at ffa7fc00 (32-bit, non-prefetchable) [size=512]
Memory at ffa7f800 (32-bit, non-prefetchable) [size=256]
Capabilities: <access denied>

01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
Subsystem: Netgear Unknown device 6b00
Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 11
Memory at ff8e0000 (32-bit, non-prefetchable) [size=64K]
Memory at ff8d0000 (32-bit, non-prefetchable) [size=64K]
Capabilities: <access denied>

01:02.0 Modem: Smart Link Ltd. SmartLink SmartPCI562 56K Modem (rev 03) (prog-if 00 [Generic])
Subsystem: Smart Link Ltd. SmartLink SmartPCI562 56K Modem
Flags: bus master, stepping, medium devsel, latency 32, IRQ 169
Memory at ff8fe000 (32-bit, non-prefetchable) [size=4K]
I/O ports at b800 [size=256]
Capabilities: <access denied>

01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)
Subsystem: Gateway 2000 Unknown device 2019
Flags: bus master, medium devsel, latency 32, IRQ 209
Memory at ff8ff000 (32-bit, non-prefetchable) [size=4K]
I/O ports at bc00 [size=64]
Capabilities: <access denied>

```

thank you so much for all your help :D

---

### Post by FrodoB on 2006-12-04
OK this is it:

01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
Subsystem: Netgear Unknown device 6b00
Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 11
Memory at ff8e0000 (32-bit, non-prefetchable) [size=64K]
Memory at ff8d0000 (32-bit, non-prefetchable) [size=64K]

Follow the instructions for the Marvell 88x8335 devices:

[https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29)

Mine works quite well in Linux and yours likely will as well.

---

### Post by burke9688 on 2006-12-04
I'm on step 5 as of right now.

And dont understand this.

Make the driver with the commands "make distclean", "make", and "make install":

user@ubuntu:~/ndiswrapper-1.29$ make distclean
user@ubuntu:~/ndiswrapper-1.29$ make
user@ubuntu:~/ndiswrapper-1.29$ sudo make install


So i just type make distclean?
i dont .. you know, get it.

---

### Post by FrodoB on 2006-12-04
Yes from inside the ndiswrapper directory you just type these three commands in order:

make distclean

make

sudo make install


The distclean command is not really necessary, it is just there in case you are remaking everything.

---

### Post by burke9688 on 2006-12-04
now i'm having another weird issue.
i got to step five on the site you posted.
and power went out.
i went to return back to step five
and it's saying i need to "Prepare the Linux build environment"
i cant download updates, because i have no internet!
so is there any way around this?
it seems crucial to installing the wireless drivers.
yet i cannot do it, i need internet to get internet?
doenst make sense, there should be a way around it.

---

### Post by FrodoB on 2006-12-05
If you put in the commands to prepare the environment you something other that the install CD that you used to install the system?

---

### Post by FrodoB on 2006-12-05
I suppose that you can try to use the ndiswrapper that comes on the CD fire up Synaptic and search for ndiswrapper and install it and something that is called ndiswrapper-utils or some such and see it you can use it instead of the latest version.

If not then you need to move the machine somewhere where you can get wired Ethernet for a few minutes to install this.

---

### Post by burke9688 on 2006-12-05
Just moved my desk to in front of our door.. the closest spot that i can reach.

So, I load up computer, select Ubuntu. Expect the internet to work.
Guess what, it didnt!
I guess even with the ethernet it didnt work. sounds nice.

Think you can help me get my ethernet adapter to work?
It's a Intel PROSet card. 
Version: 7.0.26.0


Thanks again!

---

### Post by burke9688 on 2006-12-05
nice.
i just copied that entire link you posted to me.
downloaded all the files it said to.

used a bit of common sense, and i got it.

thank you SO much for all your help!

i'm now posting from ubuntu :D

---

### Post by burke9688 on 2006-12-05
okay. i encountered one problem.


when i restarted my computer (my monitor got effed up by my tv, accidentally unplugged computer) i had no internet.

i went to just configure it. but with my netgear card, i dont know how to get the wireless key.
it says this


Create a record that looks like this: (Note we are using 128bit WEP encryption in this example.)

iface wlan0 inet dhcp
wireless-essid My_Essid
wireless-key XXXXXXXXXXXXXXXXXXXXXXXXXX
auto wlan0

Save the file. 

i pasted the xxxxxxxxxxxxxxxxxxxxxxxxxx deal in there.
and the terminal later said, that that's not valid.

how do i get the network key?
i've tried all the ways i know how to on windows, and cant get one, because i use a netgear program to run my wireless!

---

### Post by FrodoB on 2006-12-05
WEP keys are usually the issue that really holds the most folks up at this point.

You can make some WEP keys in ASCII and Hex and enter them into the devices as needed:

[http://www.andrewscompanies.com/tools/wep.asp](http://www.andrewscompanies.com/tools/wep.asp)

---

### Post by burke9688 on 2006-12-05
i got past the WEP. because my network doesnt use any encryption of any sort, because i was out of town when mom set it up, and didnt wanna fool with it.

So. i'm at another problem.

Every time I reboot. (installing a lot of new software requires it) I have to re-set up my wireless card, from.. say.. "bringing up the driver" untill i do


user@ubuntu:~$ sudo ifdown wlan0
user@ubuntu:~$ sudo ifup wlan0
user@ubuntu:~$ sudo iwlist wlan0 scanning


in the terminal.


any way to make my wireless card stay permenant in my system?


thank you, yet again!:-D :-D :-D :-D

---

### Post by FrodoB on 2006-12-05
What does you /etc/network/interfaces file look like?


when you are happy that your wireless networking is correct then  
 sudo gedit /etc/modules
Add the word **ndiswrapper** and save the file using "save as" this will then load everytime you boot

---

### Post by burke9688 on 2006-12-05
it's a bit slow, but i'm pretty happy with what i've gotten done.

but i'm also downloading updates, and programs i felt i neeedsssssss

thanks you vury much!


now.. to figger out how to install programs w/o a guide!:D

---

### Post by FrodoB on 2006-12-05
Great, I would like to hear from you after you have had some time to work with this thing, so you can let me know how it is going.  I have a PC Card device with this same chipset and it actually is the only device that I have seen that works as well or better than a device with good Linux native drivers.

---

### Post by burke9688 on 2006-12-05
> **FrodoB said:**
> Great, I would like to hear from you after you have had some time to work with this thing, so you can let me know how it is going.  I have a PC Card device with this same chipset and it actually is the only device that I have seen that works as well or better than a device with good Linux native drivers.

Well I'm having a problem now.
I coudlnt get my resolution above 1024x768px
So I went to this thread here
[http://www.ubuntuforums.org/showthread.php?t=83973](http://www.ubuntuforums.org/showthread.php?t=83973)
and put this command into the terminal, as it said to




How to reconfigure Xorg
Notice that auto detection of devices works best if Xorg is not running. Therefore it's recommended to stop X before reconfiguring this will put you to text only mode / command line:
Code:

sudo /etc/init.d/gdm stop (or kdm for KDE)



and doing that.
stopped ubuntu from working 100%
i can login to my accoutn on ubuntu
but after that, it freezes at the screen before the startup noise.

Nothing after that, nothing.

---

