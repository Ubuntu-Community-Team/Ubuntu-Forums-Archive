---
title: "Linux-friendly NIC?"
date: 2007-03-19
forum: Networking &amp; Wireless
---

### Post by Netspeed on 2007-03-19
I've got an on-board LAN that fails to show up at times and I'm going to change it to PCI. What are some really good sub-$40 PCI LAN cards (and Linux friendly)? I searched and found a host of info for wireless cards, but I'm cabled into my router.  Also, the mobo manufacturer doesn't have Linux drivers.

Thanks for any and all info!

---

### Post by Enki on 2007-03-19
Check out the Linux hardware compatibility list [here]("http://www.linuxquestions.org/hcl/index.php")

---

### Post by cookfromfrozen on 2007-03-19
Pretty much any Realtek card, especially those based on the Realtek 8139 chipset, will work fine.  They are about $5.  In most cases there will be no need to spend anything more.

---

### Post by chili555 on 2007-03-19
[http://www.newegg.com/Product/Product.aspx?Item=N82E16833124107](http://www.newegg.com/Product/Product.aspx?Item=N82E16833124107) Will probably be configured and have an IP address by the time booting is finished. Linux friendly as well as wallet friendly.

---

### Post by Mr. C. on 2007-03-19
> **Netspeed said:**
> I've got an on-board LAN that fails to show up at times and I'm going to change it to PCI...

Have you identified the NIC and driver version ?

Have you identified why it is failing ( i.e. what do your logs tell you ) ?

Your fix may be as simple as a driver update.

MrC

---

### Post by Netspeed on 2007-03-19
> **Mr. C. said:**
> Have you identified the NIC and driver version ?

Have you identified why it is failing ( i.e. what do your logs tell you ) ?

Your fix may be as simple as a driver update.

MrC

I have an ECS mobo and the LAN is controlled by a VIA VT8237 Southbridge. I couldn't find any Linux drivers on ECS's website. As I'm a Linux-noob, I really don't know how to read the logs. I have a friend that read them and he said it might be an ACPI issue and that it's disabling the PnPBIOS.

Thanks to everyone who's replied so far!

---

### Post by Mr. C. on 2007-03-19
From a terminal window, you can share output of:
```

sudo lspci
sudo lspci -n
sudo lshw -class network
sudo dmesg
```

We will translate for you.

MrC

---

### Post by Netspeed on 2007-03-19
Bare in mind that the connection is working now...

sudo lspci
00:00.0 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

sudo lspci -n
00:00.0 0600: 1106:0314
00:00.1 0600: 1106:1314
00:00.2 0600: 1106:2314
00:00.3 0600: 1106:3208
00:00.4 0600: 1106:4314
00:00.7 0600: 1106:7314
00:01.0 0604: 1106:b198
00:0f.0 0101: 1106:3149 (rev 80)
00:0f.1 0101: 1106:0571 (rev 06)
00:10.0 0c03: 1106:3038 (rev 81)
00:10.1 0c03: 1106:3038 (rev 81)
00:10.2 0c03: 1106:3038 (rev 81)
00:10.3 0c03: 1106:3038 (rev 81)
00:10.4 0c03: 1106:3104 (rev 86)
00:11.0 0601: 1106:3227
00:11.5 0401: 1106:3059 (rev 60)
00:12.0 0200: 1106:3065 (rev 78)
01:00.0 0300: 10de:0322 (rev a1)

sudo lshw -class network
*-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@00:12.0
       logical name: eth0
       version: 78
       serial: 00:19:21:25:5c:b0
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=via-rhine driverversion=1.2.0-2.6 duplex=full ip=192.168.1.101 link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:ee00-eeff iomemory:febff800-febff8ff irq:185

sudo dmesg
[17179569.184000] Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e6000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000007ffc0000 (usable)
[17179569.184000]  BIOS-e820: 000000007ffc0000 - 000000007ffce000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000007ffce000 - 000000007fff0000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000007fff0000 - 0000000080000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000] 1151MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000ff780
[17179569.184000] On node 0 totalpages: 524224
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 294848 pages, LIFO batch:31
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x000f8760
[17179569.184000] ACPI: RSDT (v001 A M I  OEMRSDT  0x07000619 MSFT 0x00000097) @ 0x7ffc0000
[17179569.184000] ACPI: FADT (v002 A M I  OEMFACP  0x07000619 MSFT 0x00000097) @ 0x7ffc0200
[17179569.184000] ACPI: MADT (v001 A M I  OEMAPIC  0x07000619 MSFT 0x00000097) @ 0x7ffc0390
[17179569.184000] ACPI: OEMB (v001 A M I  AMI_OEM  0x07000619 MSFT 0x00000097) @ 0x7ffce040
[17179569.184000] ACPI: DSDT (v001  12345 12345123 0x00000123 INTL 0x20051117) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x808
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:4 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[17179569.184000] Processor #1 15:4 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[17179569.184000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 88000000 (gap: 80000000:7ec00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/sda1 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[17179569.184000] Detected 2662.317 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179569.900000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179569.900000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.988000] Memory: 2068960k/2096896k available (1910k kernel code, 26644k reserved, 1070k data, 308k init, 1179392k highmem)
[17179569.988000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179570.068000] Calibrating delay using timer specific routine.. 5331.56 BogoMIPS (lpj=10663136)
[17179570.068000] Security Framework v1.0.0 initialized
[17179570.068000] SELinux:  Disabled at boot.
[17179570.068000] Mount-cache hash table entries: 512
[17179570.068000] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000651d 00000000 00000001
[17179570.068000] CPU: After vendor identify, caps: bfebfbff 20100000 00000000 00000000 0000651d 00000000 00000001
[17179570.068000] monitor/mwait feature present.
[17179570.068000] using mwait in idle threads.
[17179570.068000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[17179570.068000] CPU: L2 cache: 1024K
[17179570.068000] CPU: Hyper-Threading is disabled
[17179570.068000] CPU: After all inits, caps: bfebfbff 20100000 00000000 00000180 0000651d 00000000 00000001
[17179570.068000] Checking 'hlt' instruction... OK.
[17179570.084000] SMP alternatives: switching to UP code
[17179570.084000] checking if image is initramfs... it is
[17179570.592000] Freeing initrd memory: 5626k freed
[17179570.592000] ACPI: Core revision 20060707
[17179570.592000] ACPI: Looking for DSDT ... not found!
[17179570.596000] CPU0: Intel(R) Pentium(R) D  CPU 2.66GHz stepping 07
[17179570.596000] SMP alternatives: switching to SMP code
[17179570.596000] Booting processor 1/1 eip 3000
[17179570.608000] Initializing CPU#1
[17179570.688000] Calibrating delay using timer specific routine.. 5323.57 BogoMIPS (lpj=10647145)
[17179570.688000] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000651d 00000000 00000001
[17179570.688000] CPU: After vendor identify, caps: bfebfbff 20100000 00000000 00000000 0000651d 00000000 00000001
[17179570.688000] monitor/mwait feature present.
[17179570.688000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[17179570.688000] CPU: L2 cache: 1024K
[17179570.688000] CPU: Hyper-Threading is disabled
[17179570.688000] CPU: After all inits, caps: bfebfbff 20100000 00000000 00000180 0000651d 00000000 00000001
[17179570.688000] CPU1: Intel(R) Pentium(R) D  CPU 2.66GHz stepping 07
[17179570.688000] Total of 2 processors activated (10655.14 BogoMIPS).
[17179570.688000] ENABLING IO-APIC IRQs
[17179570.688000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179570.832000] checking TSC synchronization across 2 CPUs: passed.
[17179570.836000] Brought up 2 CPUs
[17179570.872000] migration_cost=4000
[17179570.872000] NET: Registered protocol family 16
[17179570.872000] EISA bus registered
[17179570.872000] ACPI: bus type pci registered
[17179570.872000] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=1
[17179570.872000] PCI: Using configuration type 1
[17179570.872000] Setting up standard PCI resources
[17179570.892000] ACPI: Interpreter enabled
[17179570.892000] ACPI: Using IOAPIC for interrupt routing
[17179570.896000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.896000] PCI: Probing PCI hardware (bus 00)
[17179570.900000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:0f.1
[17179570.900000] PCI: Quirk-MSI-K8T Soundcard On
[17179570.900000] PCI: Unexpected Value in PCI-Register: no Change!
[17179570.900000] Boot video device is 0000:01:00.0
[17179570.900000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.916000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[17179570.928000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[17179570.932000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[17179570.932000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179570.932000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179570.932000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179570.932000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179570.932000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179570.932000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179570.932000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.932000] pnp: PnP ACPI init
[17179570.940000] pnp: PnP ACPI: found 14 devices
[17179570.940000] PnPBIOS: Disabled by ACPI PNP
[17179570.940000] PCI: Using ACPI for IRQ routing
[17179570.940000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179570.948000] pnp: 00:0a: ioport range 0xa00-0xa0f has been reserved
[17179570.948000] pnp: 00:0a: ioport range 0x290-0x29f has been reserved
[17179570.948000] pnp: 00:0a: ioport range 0xa20-0xa2f has been reserved
[17179570.948000] pnp: 00:0a: ioport range 0xa30-0xa3f has been reserved
[17179570.948000] PCI: Bridge: 0000:00:01.0
[17179570.948000]   IO window: disabled.
[17179570.948000]   MEM window: fca00000-feafffff
[17179570.948000]   PREFETCH window: e7f00000-f7efffff
[17179570.948000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179570.948000] NET: Registered protocol family 2
[17179570.988000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179570.988000] TCP established hash table entries: 262144 (order: 9, 2097152 bytes)
[17179570.988000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[17179570.992000] TCP: Hash tables configured (established 262144 bind 65536)
[17179570.992000] TCP reno registered
[17179570.992000] audit: initializing netlink socket (disabled)
[17179570.992000] audit(1174295805.992:1): initialized
[17179570.992000] highmem bounce pool size: 64 pages
[17179570.992000] VFS: Disk quotas dquot_6.5.1
[17179570.992000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179570.992000] Initializing Cryptographic API
[17179570.992000] io scheduler noop registered
[17179570.992000] io scheduler anticipatory registered
[17179570.992000] io scheduler deadline registered
[17179570.992000] io scheduler cfq registered (default)
[17179570.992000] PCI: Bypassing VIA 8237 APIC De-Assert Message
[17179570.992000] isapnp: Scanning for PnP cards...
[17179571.344000] isapnp: No Plug & Play device found
[17179571.376000] Real Time Clock Driver v1.12ac
[17179571.376000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179571.376000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179571.376000] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179571.376000] mice: PS/2 mouse device common for all mice
[17179571.376000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179571.376000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179571.376000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179571.376000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[17179571.376000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179571.376000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179571.376000] EISA: Probing bus 0 at eisa.0
[17179571.376000] EISA: Detected 0 cards.
[17179571.376000] TCP bic registered
[17179571.376000] NET: Registered protocol family 1
[17179571.376000] NET: Registered protocol family 8
[17179571.376000] NET: Registered protocol family 20
[17179571.376000] Starting balanced_irq
[17179571.376000] Using IPI No-Shortcut mode
[17179571.380000] ACPI: (supports S0 S1 S3 S4 S5)
[17179571.380000] Freeing unused kernel memory: 308k freed
[17179571.408000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179572.468000] Capability LSM initialized
[17179572.508000] ACPI: Processor [CPU1] (supports 16 throttling states)
[17179572.508000] ACPI: Processor [CPU2] (supports 16 throttling states)
[17179572.508000] ACPI Exception (acpi_processor-0693): AE_NOT_FOUND, Processor Device is not present [20060707]
[17179572.508000] ACPI: Getting cpuindex for acpiid 0x3
[17179572.508000] ACPI Exception (acpi_processor-0693): AE_NOT_FOUND, Processor Device is not present [20060707]
[17179572.508000] ACPI: Getting cpuindex for acpiid 0x4
[17179572.508000] ACPI: Thermal Zone [THRM] (30 C)
[17179572.928000] SCSI subsystem initialized
[17179572.928000] libata version 1.20 loaded.
[17179572.932000] sata_via 0000:00:0f.0: version 1.1
[17179572.932000] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 20 (level, low) -> IRQ 169
[17179572.932000] PCI: Via IRQ fixup for 0000:00:0f.0, from 11 to 9
[17179572.932000] sata_via 0000:00:0f.0: routed to hard irq line 9
[17179572.932000] ata1: SATA max UDMA/133 cmd 0xEC00 ctl 0xE882 bmdma 0xE400 irq 169
[17179572.932000] ata2: SATA max UDMA/133 cmd 0xE800 ctl 0xE482 bmdma 0xE408 irq 169
[17179573.104000] ata1: dev 0 cfg 49:2f00 82:746b 83:7f61 84:4023 85:7469 86:3c41 87:4023 88:407f
[17179573.104000] ata1: dev 0 ATA-7, max UDMA/133, 488397168 sectors: LBA48
[17179573.116000] ata1: dev 0 configured for UDMA/133
[17179573.116000] scsi0 : sata_via
[17179573.284000] scsi1 : sata_via
[17179573.284000]   Vendor: ATA       Model: WDC WD2500KS-00M  Rev: 02.0
[17179573.284000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[17179573.292000] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[17179573.292000] sda: Write Protect is off
[17179573.292000] sda: Mode Sense: 00 3a 00 00
[17179573.292000] SCSI device sda: drive cache: write back
[17179573.292000] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[17179573.292000] sda: Write Protect is off
[17179573.292000] sda: Mode Sense: 00 3a 00 00
[17179573.292000] SCSI device sda: drive cache: write back
[17179573.292000]  sda: sda1 sda2 < sda5 >
[17179573.324000] sd 0:0:0:0: Attached scsi disk sda
[17179573.488000] VP_IDE: IDE controller at PCI slot 0000:00:0f.1
[17179573.488000] ACPI: PCI Interrupt 0000:00:0f.1[A] -> GSI 20 (level, low) -> IRQ 169
[17179573.488000] PCI: Via IRQ fixup for 0000:00:0f.1, from 255 to 9
[17179573.488000] VP_IDE: chipset revision 6
[17179573.488000] VP_IDE: not 100% native mode: will probe irqs later
[17179573.488000] VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
[17179573.488000]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:pio, hdb:DMA
[17179573.488000]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:pio, hdd:pio
[17179573.488000] Probing IDE interface ide0...
[17179574.656000] hdb: HP DVD Writer 940d, ATAPI CD/DVD-ROM drive
[17179574.716000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179574.728000] Probing IDE interface ide1...
[17179575.308000] hdb: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(66)
[17179575.308000] Uniform CD-ROM driver Revision: 3.20
[17179575.392000] Probing IDE interface ide1...
[17179575.408000] usbcore: registered new driver usbfs
[17179575.408000] usbcore: registered new driver hub
[17179575.424000] USB Universal Host Controller Interface driver v3.0
[17179575.424000] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 177
[17179575.424000] PCI: Via IRQ fixup for 0000:00:10.0, from 10 to 1
[17179575.424000] uhci_hcd 0000:00:10.0: UHCI Host Controller
[17179575.424000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[17179575.424000] uhci_hcd 0000:00:10.0: irq 177, io base 0x0000dc00
[17179575.424000] usb usb1: configuration #1 chosen from 1 choice
[17179575.424000] hub 1-0:1.0: USB hub found
[17179575.424000] hub 1-0:1.0: 2 ports detected
[17179575.532000] ACPI: PCI Interrupt 0000:00:10.1[A] -> GSI 21 (level, low) -> IRQ 177
[17179575.532000] PCI: Via IRQ fixup for 0000:00:10.1, from 10 to 1
[17179575.532000] uhci_hcd 0000:00:10.1: UHCI Host Controller
[17179575.532000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[17179575.532000] uhci_hcd 0000:00:10.1: irq 177, io base 0x0000d880
[17179575.532000] usb usb2: configuration #1 chosen from 1 choice
[17179575.532000] hub 2-0:1.0: USB hub found
[17179575.532000] hub 2-0:1.0: 2 ports detected
[17179575.640000] ACPI: PCI Interrupt 0000:00:10.2[B] -> GSI 21 (level, low) -> IRQ 177
[17179575.640000] PCI: Via IRQ fixup for 0000:00:10.2, from 5 to 1
[17179575.640000] uhci_hcd 0000:00:10.2: UHCI Host Controller
[17179575.640000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[17179575.640000] uhci_hcd 0000:00:10.2: irq 177, io base 0x0000d800
[17179575.640000] usb usb3: configuration #1 chosen from 1 choice
[17179575.640000] hub 3-0:1.0: USB hub found
[17179575.640000] hub 3-0:1.0: 2 ports detected
[17179575.748000] ACPI: PCI Interrupt 0000:00:10.3[B] -> GSI 21 (level, low) -> IRQ 177
[17179575.748000] PCI: Via IRQ fixup for 0000:00:10.3, from 5 to 1
[17179575.748000] uhci_hcd 0000:00:10.3: UHCI Host Controller
[17179575.748000] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[17179575.748000] uhci_hcd 0000:00:10.3: irq 177, io base 0x0000d480
[17179575.748000] usb usb4: configuration #1 chosen from 1 choice
[17179575.748000] hub 4-0:1.0: USB hub found
[17179575.748000] hub 4-0:1.0: 2 ports detected
[17179575.856000] ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 177
[17179575.856000] PCI: Via IRQ fixup for 0000:00:10.4, from 11 to 1
[17179575.856000] ehci_hcd 0000:00:10.4: EHCI Host Controller
[17179575.856000] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[17179575.856000] ehci_hcd 0000:00:10.4: irq 177, io mem 0xfebffc00
[17179575.856000] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179575.856000] usb usb5: configuration #1 chosen from 1 choice
[17179575.856000] hub 5-0:1.0: USB hub found
[17179575.856000] hub 5-0:1.0: 8 ports detected
[17179576.036000] Attempting manual resume
[17179576.052000] kjournald starting.  Commit interval 5 seconds
[17179576.052000] EXT3-fs: mounted filesystem with ordered data mode.
[17179577.252000] usb 3-2: new full speed USB device using uhci_hcd and address 2
[17179577.472000] usb 3-2: configuration #1 chosen from 1 choice
[17179583.824000] Linux agpgart interface v0.101 (c) Dave Jones
[17179583.832000] agpgart: Detected VIA P4M800CE chipset
[17179583.840000] agpgart: AGP aperture is 64M @ 0xf8000000
[17179583.952000] Floppy drive(s): fd0 is 1.44M
[17179583.968000] input: PC Speaker as /class/input/input1
[17179583.972000] FDC 0 is a post-1991 82077
[17179584.004000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
[17179584.004000] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 23 (level, low) -> IRQ 185
[17179584.004000] PCI: Via IRQ fixup for 0000:00:12.0, from 10 to 9
[17179584.008000] eth0: VIA Rhine II at 0x1ee00, 00:19:21:25:5c:b0, IRQ 185.
[17179584.008000] eth0: MII PHY found at address 1, status 0x7869 advertising 05e1 Link 41e1.
[17179584.032000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179584.036000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179584.116000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[17179584.240000] parport: PnPBIOS parport detected.
[17179584.240000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[17179584.384000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179584.580000] usbcore: registered new driver hiddev
[17179584.584000] input: Logitech Logitech USB Headset as /class/input/input2
[17179584.584000] input: USB HID v1.00 Device [Logitech Logitech USB Headset] on usb-0000:00:10.2-2
[17179584.584000] usbcore: registered new driver usbhid
[17179584.584000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179584.588000] usbcore: registered new driver snd-usb-audio
[17179584.592000] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 193
[17179584.592000] PCI: Via IRQ fixup for 0000:00:11.5, from 11 to 1
[17179584.592000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[17179585.148000] NET: Registered protocol family 17
[17179585.308000] lp0: using parport0 (interrupt-driven).
[17179585.344000] Adding 5984172k swap on /dev/disk/by-uuid/ca802f39-ba83-467d-9e1e-20d28e57021c.  Priority:-1 extents:1 across:5984172k
[17179585.524000] input: ImExPS/2 Generic Explorer Mouse as /class/input/input3
[17179585.616000] ts: Compaq touchscreen protocol output
[17179589.748000] NET: Registered protocol family 10
[17179589.748000] lo: Disabled Privacy Extensions
[17179589.748000] IPv6 over IPv4 tunneling driver
[17179599.868000] eth0: no IPv6 routers present
[17179714.936000] EXT3 FS on sda1, internal journal
[17179720.480000] ACPI: Power Button (FF) [PWRF]
[17179720.480000] ACPI: Sleep Button (CM) [SLPB]
[17179720.480000] ACPI: Power Button (CM) [PWRB]
[17179720.624000] ibm_acpi: ec object not found
[17179720.664000] pcc_acpi: loading...
[17179722.088000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179722.088000] apm: disabled - APM is not SMP safe.
[17198241.604000] hdb: command error: status=0x51 { DriveReady SeekComplete Error }
[17198241.604000] hdb: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[17198241.604000] ide: failed opcode was: unknown
[17198241.604000] end_request: I/O error, dev hdb, sector 0
[17198241.604000] Buffer I/O error on device hdb, logical block 0
[17198241.608000] hdb: command error: status=0x51 { DriveReady SeekComplete Error }
[17198241.608000] hdb: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[17198241.608000] ide: failed opcode was: unknown
[17198241.608000] end_request: I/O error, dev hdb, sector 0
[17198241.608000] Buffer I/O error on device hdb, logical block 0
[17198241.612000] hdb: command error: status=0x51 { DriveReady SeekComplete Error }
[17198241.612000] hdb: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[17198241.612000] ide: failed opcode was: unknown
[17198241.612000] end_request: I/O error, dev hdb, sector 8
[17198241.612000] Buffer I/O error on device hdb, logical block 1
[17198241.612000] hdb: command error: status=0x51 { DriveReady SeekComplete Error }
[17198241.612000] hdb: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[17198241.612000] ide: failed opcode was: unknown
[17198241.612000] end_request: I/O error, dev hdb, sector 16
[17198241.612000] Buffer I/O error on device hdb, logical block 2
[17198241.616000] hdb: command error: status=0x51 { DriveReady SeekComplete Error }
[17198241.616000] hdb: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[17198241.616000] ide: failed opcode was: unknown
[17198241.616000] end_request: I/O error, dev hdb, sector 24
[17198241.616000] Buffer I/O error on device hdb, logical block 3
[17198241.616000] hdb: command error: status=0x51 { DriveReady SeekComplete Error }
[17198241.616000] hdb: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[17198241.616000] ide: failed opcode was: unknown
[17198241.616000] end_request: I/O error, dev hdb, sector 0
[17198241.616000] Buffer I/O error on device hdb, logical block 0
[17198241.616000] hdb: command error: status=0x51 { DriveReady SeekComplete Error }
[17198241.616000] hdb: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[17198241.616000] ide: failed opcode was: unknown
[17198241.616000] end_request: I/O error, dev hdb, sector 0
[17198241.616000] Buffer I/O error on device hdb, logical block 0

---

### Post by Mr. C. on 2007-03-19
I should have indicated to place the output into an attachment.

You have a VIA chipset with the Via Rhine driver in use:
```

[17179584.004000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
[17179584.004000] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 23 (level, low) -> IRQ 185
[17179584.004000] PCI: Via IRQ fixup for 0000:00:12.0, from 10 to 9
[17179584.008000] eth0: VIA Rhine II at 0x1ee00, 00:19:21:25:5c:b0, IRQ 185.
[17179584.008000] eth0: MII PHY found at address 1, status 0x7869 advertising 05e1 Link 41e1.
[17179584.116000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
```

The 2.6.20 kernel version has an updated via Rhine driver.  If you can update kernels, this may resolve your issues.

MrC

---

### Post by Netspeed on 2007-03-19
Thanks for the advice! Now for the noob question: How do I update the kernels?

---

### Post by Mr. C. on 2007-03-20
There are several options:

1) build it yourself
2) update to Feisty Fawn, Herd5 (early stages still )
3) search the forums here for a download location

Building the kernel yourself is not terribly difficult, but not for the faint of heart either.  It requires downloading the kernel source and build-essential tools.

Feisty is in early stages, but you can download an installation and see if it resolves your issues.  It is available here: [http://cdimage.ubuntu.com/releases/feisty/](http://cdimage.ubuntu.com/releases/feisty/)  or you can use:
sudo update-manager -c -d to have the option to update.

I know other's have posted the 2.6.20 kernel, and have been successful using it.  I don't have an exact link for you - sorry.

MrC

---

