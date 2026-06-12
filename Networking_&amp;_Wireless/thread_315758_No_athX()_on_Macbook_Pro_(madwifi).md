---
title: "No athX(?) on Macbook Pro (madwifi)"
date: 2006-12-09
forum: Networking &amp; Wireless
---

### Post by emil.s on 2006-12-09
I have installed Ubuntu Edgy on my new Macbook Pro...
I have followed this guides:
[http://wiki.debian.org/MacBook](http://wiki.debian.org/MacBook)
[http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp)
[http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu)
[https://wiki.ubuntu.com/MacBookPro](https://wiki.ubuntu.com/MacBookPro)
[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)
[http://gentoo-wiki.com/HARDWARE_Apple_MacBook](http://gentoo-wiki.com/HARDWARE_Apple_MacBook)

I have loaded "ath_pci", it's in /etc/modules, and everything seems ok... 

But:
```
root@Macbooken: /home/emil/Desktop # ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:17:F2:C3:AE:19
          inet addr:192.168.0.8  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::217:f2ff:fec3:ae19/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12315 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8222 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:16229916 (15.4 MiB)  TX bytes:846702 (826.8 KiB)
          Interrupt:16

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

root@Macbooken: /home/emil/Desktop # iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
```

What is wrong?

---

### Post by stupidkid on 2006-12-09
Loading it in /etc/modules doesn't load it immediately.

modprobe ath_pci

should work.

---

### Post by emil.s on 2006-12-10
> **stupidkid said:**
> Loading it in /etc/modules doesn't load it immediately.

modprobe ath_pci

should work.

Yes i know. But i have restarted the system, and tried with moprobe, but i have still no WLAN interface... :(

---

### Post by FrodoB on 2006-12-10
Is this a mini-PCI or mini-PCIe device that is built-in to the notebook or something else?

If it is a non-USB device publish the output of lspci -v 

If you can see your device in the lspci -v output then take a look at dmesg and find the section where the device is found and publish that.

---

### Post by emil.s on 2006-12-10
> **FrodoB said:**
> Is this a mini-PCI or mini-PCIe device that is built-in to the notebook or something else?

If it is a non-USB device publish the output of lspci -v 

If you can see your device in the lspci -v output then take a look at dmesg and find the section where the device is found and publish that.

It's built in...

Here is more info:
```
lspci -v
...
...
...
03:00.0 Network controller: Atheros Communications, Inc. Unknown device 0024 (rev 01)
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at 50100000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: [40] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: 64bit- Queue=0/0 Enable-
        Capabilities: [60] Express Legacy Endpoint IRQ 0
        Capabilities: [90] MSI-X: Enable- Mask- TabSize=1
        Capabilities: [100] Advanced Error Reporting
        Capabilities: [140] Virtual Channel
```

lshw:
```
        *-pci:2
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network UNCLAIMED
                description: Network controller
                product: Atheros Communications, Inc.
                vendor: Atheros Communications, Inc.
                physical id: 0
                bus info: pci@03:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                resources: iomemory:50100000-5010ffff irq:10
```

And "dmesg" (i found nothing. I paste all... :P):
```
root@Macbooken: /home/emil # dmesg
Linux version 2.6.19-mactel (root@ubuntu) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #1 SMP PREEMPT Fri Dec 8 20:43:18 CET 2006
BIOS-provided physical RAM map:
 BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
 BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
 BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
 BIOS-e820: 0000000000100000 - 000000003f0e7000 (usable)
 BIOS-e820: 000000003f0e7000 - 000000003f2e8000 (ACPI NVS)
 BIOS-e820: 000000003f2e8000 - 000000003febe000 (ACPI data)
 BIOS-e820: 000000003febe000 - 000000003feef000 (ACPI NVS)
 BIOS-e820: 000000003feef000 - 000000003ff00000 (ACPI data)
 BIOS-e820: 000000003ff00000 - 0000000040000000 (reserved)
 BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
 BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
 BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
 BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
 BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
 BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
112MB HIGHMEM available.
896MB LOWMEM available.
Entering add_active_range(0, 0, 258279) 0 entries of 256 used
Zone PFN ranges:
  DMA             0 ->     4096
  Normal       4096 ->   229376
  HighMem    229376 ->   258279
early_node_map[1] active PFN ranges
    0:        0 ->   258279
On node 0 totalpages: 258279
  DMA zone: 32 pages used for memmap
  DMA zone: 0 pages reserved
  DMA zone: 4064 pages, LIFO batch:0
  Normal zone: 1760 pages used for memmap
  Normal zone: 223520 pages, LIFO batch:31
  HighMem zone: 225 pages used for memmap
  HighMem zone: 28678 pages, LIFO batch:7
DMI 2.4 present.
ACPI: RSDP (v002 APPLE                                 ) @ 0x000fe020
ACPI: XSDT (v001 APPLE   Apple00 0x000000a5      0x01000013) @ 0x3fefd1c0
ACPI: FADT (v003 APPLE   Apple00 0x000000a5 Loki 0x0000005f) @ 0x3fefb000
ACPI: HPET (v001 APPLE   Apple00 0x00000001 Loki 0x0000005f) @ 0x3fefa000
ACPI: MADT (v001 APPLE   Apple00 0x00000001 Loki 0x0000005f) @ 0x3fef9000
ACPI: MCFG (v001 APPLE   Apple00 0x00000001 Loki 0x0000005f) @ 0x3fef8000
ACPI: ASF! (v032 APPLE   Apple00 0x00000001 Loki 0x0000005f) @ 0x3fef7000
ACPI: SBST (v001 APPLE   Apple00 0x00000001 Loki 0x0000005f) @ 0x3fef6000
ACPI: ECDT (v001 APPLE   Apple00 0x00000001 Loki 0x0000005f) @ 0x3fef5000
ACPI: SSDT (v001 APPLE     CpuPm 0x00003000 INTL 0x20050309) @ 0x3feef000
ACPI: SSDT (v001 SataRe  SataPri 0x00001000 INTL 0x20050309) @ 0x3febd000
ACPI: SSDT (v001 SataRe  SataSec 0x00001000 INTL 0x20050309) @ 0x3febc000
ACPI: DSDT (v001 APPLE  MacBookP 0x00020002 INTL 0x20050309) @ 0x00000000
ACPI: PM-Timer IO Port: 0x408
ACPI: Local APIC address 0xfee00000
ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Processor #0 6:15 APIC version 20
ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Processor #1 6:15 APIC version 20
ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
ACPI: IRQ0 used by override.
ACPI: IRQ2 used by override.
ACPI: IRQ9 used by override.
Enabling APIC mode:  Flat.  Using 1 I/O APICs
ACPI: HPET id: 0x8086a201 base: 0xfed00000
Using ACPI (MADT) for SMP configuration information
Allocating PCI resources starting at 50000000 (gap: 40000000:b0000000)
Detected 2161.383 MHz processor.
Built 1 zonelists.  Total pages: 256262
Kernel command line: auto BOOT_IMAGE=Linux ro root=803
mapped APIC to ffffd000 (fee00000)
mapped IOAPIC to ffffc000 (fec00000)
Enabling fast FPU save and restore... done.
Enabling unmasked SIMD FPU exception support... done.
Initializing CPU#0
PID hash table entries: 4096 (order: 12, 16384 bytes)
Console: colour VGA+ 80x25
Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Memory: 1019440k/1033116k available (2718k kernel code, 13040k reserved, 797k data, 244k init, 115612k highmem)
virtual kernel memory layout:
    fixmap  : 0xfff4f000 - 0xfffff000   ( 704 kB)
    pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
    vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
    lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
      .init : 0xc0476000 - 0xc04b3000   ( 244 kB)
      .data : 0xc03a7b36 - 0xc046f2e4   ( 797 kB)
      .text : 0xc0100000 - 0xc03a7b36   (2718 kB)
Checking if this processor honours the WP bit even in supervisor mode... Ok.
hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
hpet0: 3 64-bit timers, 14318180 Hz
Using HPET for base-timer
Calibrating delay using timer specific routine.. 4327.25 BogoMIPS (lpj=8654510)
Security Framework v1.0.0 initialized
SELinux:  Disabled at boot.
Mount-cache hash table entries: 512
CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
monitor/mwait feature present.
using mwait in idle threads.
CPU: L1 I cache: 32K, L1 D cache: 32K
CPU: L2 cache: 4096K
CPU: Physical Processor ID: 0
CPU: Processor Core ID: 0
CPU: After all inits, caps: bfebfbff 20100000 00000000 00000940 0000e3bd 00000000 00000001
Intel machine check architecture supported.
Intel machine check reporting enabled on CPU#0.
Checking 'hlt' instruction... OK.
SMP alternatives: switching to UP code
ACPI: Core revision 20060707
CPU0: Intel(R) Core(TM)2 CPU         T7400  @ 2.16GHz stepping 06
SMP alternatives: switching to SMP code
Booting processor 1/1 eip 3000
Initializing CPU#1
Calibrating delay using timer specific routine.. 4322.59 BogoMIPS (lpj=8645184)
CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
monitor/mwait feature present.
CPU: L1 I cache: 32K, L1 D cache: 32K
CPU: L2 cache: 4096K
CPU: Physical Processor ID: 0
CPU: Processor Core ID: 1
CPU: After all inits, caps: bfebfbff 20100000 00000000 00000940 0000e3bd 00000000 00000001
Intel machine check architecture supported.
Intel machine check reporting enabled on CPU#1.
CPU1: Intel(R) Core(TM)2 CPU         T7400  @ 2.16GHz stepping 06
Total of 2 processors activated (8649.84 BogoMIPS).
ENABLING IO-APIC IRQs
..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
checking TSC synchronization across 2 CPUs: passed.
Brought up 2 CPUs
migration_cost=72
NET: Registered protocol family 16
ACPI: bus type pci registered
PCI: Using MMCONFIG
Setting up standard PCI resources
ACPI: Interpreter enabled
ACPI: Using IOAPIC for interrupt routing
ACPI: PCI Root Bridge [PCI0] (0000:00)
PCI: Probing PCI hardware (bus 00)
PCI quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
PCI quirk: region 0500-053f claimed by ICH6 GPIO
PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
Boot video device is 0000:01:00.0
PCI: Transparent bridge - 0000:00:1e.0
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 *11 12 14 15)
ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *11 12 14 15)
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
pnp: PnP ACPI: found 9 devices
SCSI subsystem initialized
libata version 2.00 loaded.
PCI: Using ACPI for IRQ routing
PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
NetLabel: Initializing
NetLabel:  domain hash size = 128
NetLabel:  protocols = UNLABELED CIPSOv4
NetLabel:  unlabeled traffic allowed by default
PCI: Bridge: 0000:00:01.0
  IO window: 3000-3fff
  MEM window: 50300000-503fffff
  PREFETCH window: 40000000-47ffffff
PCI: Bridge: 0000:00:1c.0
  IO window: 2000-2fff
  MEM window: 50200000-502fffff
  PREFETCH window: 50500000-505fffff
PCI: Bridge: 0000:00:1c.1
  IO window: disabled.
  MEM window: 50100000-501fffff
  PREFETCH window: disabled.
PCI: Bridge: 0000:00:1c.2
  IO window: 1000-1fff
  MEM window: 4c100000-500fffff
  PREFETCH window: 48000000-4bffffff
PCI: Bridge: 0000:00:1e.0
  IO window: disabled.
  MEM window: 4c000000-4c0fffff
  PREFETCH window: disabled.
ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
PCI: Setting latency timer of device 0000:00:01.0 to 64
ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 17
PCI: Setting latency timer of device 0000:00:1c.0 to 64
ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 16
PCI: Setting latency timer of device 0000:00:1c.1 to 64
ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
PCI: Setting latency timer of device 0000:00:1c.2 to 64
PCI: Setting latency timer of device 0000:00:1e.0 to 64
NET: Registered protocol family 2
IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
TCP bind hash table entries: 65536 (order: 7, 786432 bytes)
TCP: Hash tables configured (established 131072 bind 65536)
TCP reno registered
audit: initializing netlink socket (disabled)
audit(1165751401.888:1): initialized
highmem bounce pool size: 64 pages
Total HugeTLB memory allocated, 0
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
io scheduler noop registered
io scheduler anticipatory registered (default)
io scheduler deadline registered
io scheduler cfq registered
PCI: Setting latency timer of device 0000:00:01.0 to 64
assign_interrupt_mode Found MSI capability
Allocate Port Service[0000:00:01.0:pcie00]
Allocate Port Service[0000:00:01.0:pcie03]
PCI: Setting latency timer of device 0000:00:1c.0 to 64
assign_interrupt_mode Found MSI capability
Allocate Port Service[0000:00:1c.0:pcie00]
Allocate Port Service[0000:00:1c.0:pcie02]
Allocate Port Service[0000:00:1c.0:pcie03]
PCI: Setting latency timer of device 0000:00:1c.1 to 64
assign_interrupt_mode Found MSI capability
Allocate Port Service[0000:00:1c.1:pcie00]
Allocate Port Service[0000:00:1c.1:pcie02]
Allocate Port Service[0000:00:1c.1:pcie03]
PCI: Setting latency timer of device 0000:00:1c.2 to 64
assign_interrupt_mode Found MSI capability
Allocate Port Service[0000:00:1c.2:pcie00]
Allocate Port Service[0000:00:1c.2:pcie02]
Allocate Port Service[0000:00:1c.2:pcie03]
loop: loaded (max 8 devices)
input: Macintosh mouse button emulation as /class/input/input0
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
ata_piix 0000:00:1f.1: version 2.00ac6
ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
PCI: Setting latency timer of device 0000:00:1f.1 to 64
ata1: PATA max UDMA/133 cmd 0x1F0 ctl 0x3F6 bmdma 0x40B0 irq 14
ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x40B8 irq 15
scsi0 : ata_piix
ata1.00: ATAPI, max UDMA/66
ata1.00: configured for UDMA/66
scsi1 : ata_piix
ATA: abnormal status 0x7F on port 0x177
scsi 0:0:0:0: CD-ROM            MATSHITA DVD-R   UJ-857D  KCV9 PQ: 0 ANSI: 5
sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Uniform CD-ROM driver Revision: 3.20
sr 0:0:0:0: Attached scsi CD-ROM sr0
sr 0:0:0:0: Attached scsi generic sg0 type 5
ata_piix 0000:00:1f.2: MAP [ P0 P2 XX XX ]
ata_piix 0000:00:1f.2: invalid MAP value 0
ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
PCI: Setting latency timer of device 0000:00:1f.2 to 64
ata3: SATA max UDMA/133 cmd 0x40C8 ctl 0x40E6 bmdma 0x40A0 irq 19
ata4: SATA max UDMA/133 cmd 0x40C0 ctl 0x40E2 bmdma 0x40A8 irq 19
scsi2 : ata_piix
ATA: abnormal status 0x7F on port 0x40CF
ATA: abnormal status 0x7F on port 0x40CF
ata3.01: ATA-7, max UDMA/133, 234441648 sectors: LBA48 NCQ (depth 0/32)
ata3.01: ata3: dev 1 multi count 16
ata3.01: configured for UDMA/133
scsi3 : ata_piix
ATA: abnormal status 0x7F on port 0x40C7
scsi 2:0:1:0: Direct-Access     ATA      Hitachi HTS54161 SBDA PQ: 0 ANSI: 5
SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
sda: Write Protect is off
sda: Mode Sense: 00 3a 00 00
SCSI device sda: drive cache: write back
SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
sda: Write Protect is off
sda: Mode Sense: 00 3a 00 00
SCSI device sda: drive cache: write back
 sda: sda1 sda2 sda3 sda4
sd 2:0:1:0: Attached scsi disk sda
sd 2:0:1:0: Attached scsi generic sg1 type 0
PNP: No PS/2 controller found. Probing ports directly.
i8042.c: No controller found.
mice: PS/2 mouse device common for all mice
NET: Registered protocol family 1
NET: Registered protocol family 10
lo: Disabled Privacy Extensions
Mobile IPv6
NET: Registered protocol family 17
Starting balanced_irq
Using IPI No-Shortcut mode
ACPI: (supports S0 S3 S4 S5)
Time: tsc clocksource has been installed.
kjournald starting.  Commit interval 5 seconds
EXT3-fs: mounted filesystem with ordered data mode.
VFS: Mounted root (ext3 filesystem) readonly.
Freeing unused kernel memory: 244k freed
Linux agpgart interface v0.101 (c) Dave Jones
agpgart: Detected an Intel 945GM Chipset.
agpgart: AGP aperture is 256M @ 0x0
Real Time Clock Driver v1.12ac
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
intel_rng: FWH not detected
usbcore: registered new interface driver usbfs
usbcore: registered new interface driver hub
usbcore: registered new device driver usb
ieee1394: Initialized config rom entry `ip1394'
USB Universal Host Controller Interface driver v3.0
ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
PCI: Setting latency timer of device 0000:00:1d.0 to 64
uhci_hcd 0000:00:1d.0: UHCI Host Controller
uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
uhci_hcd 0000:00:1d.0: irq 20, io base 0x00004080
usb usb1: configuration #1 chosen from 1 choice
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
PCI: Setting latency timer of device 0000:00:1d.1 to 64
uhci_hcd 0000:00:1d.1: UHCI Host Controller
uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
uhci_hcd 0000:00:1d.1: irq 19, io base 0x00004060
usb usb2: configuration #1 chosen from 1 choice
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
PCI: Setting latency timer of device 0000:00:1d.2 to 64
uhci_hcd 0000:00:1d.2: UHCI Host Controller
uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
uhci_hcd 0000:00:1d.2: irq 18, io base 0x00004040
usb usb3: configuration #1 chosen from 1 choice
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 2 ports detected
ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
PCI: Setting latency timer of device 0000:00:1d.3 to 64
uhci_hcd 0000:00:1d.3: UHCI Host Controller
uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
uhci_hcd 0000:00:1d.3: irq 16, io base 0x00004020
usb usb4: configuration #1 chosen from 1 choice
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 2 ports detected
usb 1-2: new full speed USB device using uhci_hcd and address 2
ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
PCI: Setting latency timer of device 0000:00:1d.7 to 64
ehci_hcd 0000:00:1d.7: EHCI Host Controller
ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
ehci_hcd 0000:00:1d.7: debug port 1
PCI: cache line size of 32 is not supported by device 0000:00:1d.7
ehci_hcd 0000:00:1d.7: irq 20, io mem 0x50405400
ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
usb usb5: configuration #1 chosen from 1 choice
hub 5-0:1.0: USB hub found
hub 5-0:1.0: 8 ports detected
ACPI: PCI Interrupt 0000:0c:03.0[A] -> GSI 19 (level, low) -> IRQ 19
ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 21
PCI: Setting latency timer of device 0000:00:1b.0 to 64
ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[4c004000-4c0047ff]  Max Packet=[4096]  IR/IT contexts=[4/8]
usb 1-2: device not accepting address 2, error -71
ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
PCI: Setting latency timer of device 0000:02:00.0 to 64
sky2 v1.10 addr 0x50200000 irq 16 Yukon-EC (0xb6) rev 2
sky2 eth0: addr 00:17:f2:c3:ae:19
sky2 eth0: enabling interface
ADDRCONF(NETDEV_UP): eth0: link is not ready
ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
ieee1394: sbp2: Try serialize_io=0 for better performance
ath_hal: module license 'Proprietary' taints kernel.
ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
wlan: 0.8.4.2 (svn r1850)
ath_rate_sample: 1.2 (svn r1850)
ath_pci: 0.9.4.5 (svn r1850)
EXT3 FS on sda3, internal journal
NTFS driver 2.1.27 [Flags: R/W MODULE].
NTFS volume version 3.1.
ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0017f2fffe8d0c1c]
usb 5-4: new high speed USB device using ehci_hcd and address 4
usb 5-4: configuration #1 chosen from 1 choice
sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
usb 2-1: new low speed USB device using uhci_hcd and address 2
usb 2-1: configuration #1 chosen from 1 choice
usb 1-2: new full speed USB device using uhci_hcd and address 4
usb 1-2: configuration #1 chosen from 1 choice
usb 3-2: new full speed USB device using uhci_hcd and address 2
usb 3-2: configuration #1 chosen from 1 choice
usb 4-1: new full speed USB device using uhci_hcd and address 2
usb 4-1: configuration #1 chosen from 1 choice
usbcore: registered new interface driver hiddev
input: Logitech USB Receiver as /class/input/input1
input: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-1
input: Logitech USB Receiver as /class/input/input2
input,hiddev0: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.1-1
input: Apple Computer Apple Internal Keyboard / Trackpad as /class/input/input3
input: USB HID v1.11 Keyboard [Apple Computer Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.0-2
input: Apple Computer Apple Internal Keyboard / Trackpad as /class/input/input4
input: USB HID v1.11 Device [Apple Computer Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.0-2
input: HID 05ac:1000 as /class/input/input5
input: USB HID v1.11 Keyboard [HID 05ac:1000] on usb-0000:00:1d.3-1
input: HID 05ac:1000 as /class/input/input6
input: USB HID v1.11 Mouse [HID 05ac:1000] on usb-0000:00:1d.3-1
usbcore: registered new interface driver usbhid
drivers/usb/input/hid-core.c: v2.6:USB HID core driver
input: Apple Mac mini infrared remote control driver as /class/input/input7
usbcore: registered new interface driver appleir
drivers/usb/input/appleir.c: v1.1:USB Apple MacMini IR Receiver driver
appletouch Geyser 3 inited.
input: appletouch as /class/input/input8
usbcore: registered new interface driver appletouch
ACPI: AC Adapter [ADP1] (on-line)
ACPI: Battery Slot [BAT0] (battery present)
ACPI: Power Button (FF) [PWRF]
ACPI: Lid Switch [LID0]
ACPI: Power Button (CM) [PWRB]
ACPI: Sleep Button (CM) [SLPB]
Using specific hotkey driver
ACPI (exconfig-0455): Dynamic SSDT Load - OemId [APPLE ] OemTableId [ Cpu0Ist] [20060707]
ACPI (exconfig-0455): Dynamic SSDT Load - OemId [APPLE ] OemTableId [ Cpu0Cst] [20060707]
Monitor-Mwait will be used to enter C-1 state
Monitor-Mwait will be used to enter C-2 state
Monitor-Mwait will be used to enter C-3 state
ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
ACPI: Processor [CPU0] (supports 8 throttling states)
ACPI (exconfig-0455): Dynamic SSDT Load - OemId [APPLE ] OemTableId [ Cpu1Ist] [20060707]
ACPI (exconfig-0455): Dynamic SSDT Load - OemId [APPLE ] OemTableId [ Cpu1Cst] [20060707]
ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
ACPI: Processor [CPU1] (supports 8 throttling states)
ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
Time: hpet clocksource has been installed.
eth0: no IPv6 routers present
mtrr: no more MTRRs available
mtrr: no more MTRRs available
mtrr: no more MTRRs available
mtrr: no more MTRRs available
mtrr: no more MTRRs available
appletouch: incomplete data package (first byte: 2, length: 4).
Capability LSM initialized
usb 4-1: usbfs: USBDEVFS_CONTROL failed cmd hid2hci rqt 64 rq 0 len 0 ret -84
usb 4-1: USB disconnect, address 2
Bluetooth: Core ver 2.11
NET: Registered protocol family 31
Bluetooth: HCI device and connection manager initialized
Bluetooth: HCI socket layer initialized
Bluetooth: L2CAP ver 2.8
Bluetooth: L2CAP socket layer initialized
usb 4-1: new full speed USB device using uhci_hcd and address 3
Bluetooth: RFCOMM socket layer initialized
Bluetooth: RFCOMM TTY layer initialized
Bluetooth: RFCOMM ver 1.8
usb 4-1: configuration #1 chosen from 1 choice
Bluetooth: HCI USB driver ver 2.9
usbcore: registered new interface driver hci_usb
```

---

### Post by FrodoB on 2006-12-10
Is this one of the new Atheros pre-N devices? If so I don't think that it is supported in mAdWiFi yet. And Macbooks cannot use ndiswrapper can they? 

I would suggest that you go to the mAdWiFi wiki and inquire about this and report the answer back here so we have a definitive answer for future reference.

If the folks on the mAdWiFi wiki can get you going in the right direction, someone here can help you get the device configured.

wiki:

[http://madwifi.org/](http://madwifi.org/)

I think I see a ticket on the same device on the wiki:

[http://madwifi.org/ticket/1001](http://madwifi.org/ticket/1001)

About half way down some says they have it working using ndiswrapper with a 64bit Windows driver from D-Link, but It is not obvious that this is on a Macbook.

---

### Post by FrodoB on 2006-12-10
Also note this, which was listed at the end of that ticket, I still don't know if this helps for Macbooks, but it is the more likely to it seems:

[http://thinkwiki.org/wiki/ThinkPad_11a/b/g/n_Wireless_LAN_Mini_Express_Adapter](http://thinkwiki.org/wiki/ThinkPad_11a/b/g/n_Wireless_LAN_Mini_Express_Adapter)

---

### Post by emil.s on 2006-12-10
hm, I think i have this card. I have the "new" Macbook pro. The one with "Core 2 Duo" CPU...

But he get this when he starts:
```
[13750.969313] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[13750.977910] wlan: 0.8.4.2 (svn r1794)
[13750.979925] ath_rate_sample: 1.2 (svn r1794)
[13750.984876] ath_pci: 0.9.4.5 (svn r1794)
[13750.985069] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 177
[13750.985085] PCI: Setting latency timer of device 0000:03:00.0 to 64
[13750.985366] wifi%d: unable to attach hardware: 'No hardware present or device not yet supported' (HAL status 1)
[13750.985391] ACPI: PCI interrupt for device 0000:03:00.0 disabled
```

I get this:
```
ath_hal: module license 'Proprietary' taints kernel.
ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
wlan: 0.8.4.2 (svn r1850)
ath_rate_sample: 1.2 (svn r1850)
ath_pci: 0.9.4.5 (svn r1850)
```

But i think the problem is that the card isn't full supported.

I will try with Ndiswrapper, but it is not really good. :P
My primary reason for install Linux on it is for Wardriving. :P 

But i hope madwifi will support this card soon. :)

Thanks for helping! :)

---

### Post by FrodoB on 2006-12-10
The part that I was noticing was:

03:00.0 Network controller: Atheros Communications, Inc. Unknown device 0024 (rev 01)

Which I though was common to yours and the ones in the list, or maybe I misread.

---

### Post by idn on 2006-12-11
I got wifi on a MBP working for me, but over the last day network manager just stopped working for some reason.

---

### Post by old_toby on 2007-02-14
> **FrodoB said:**
> Also note this, which was listed at the end of that ticket, I still don't know if this helps for Macbooks, but it is the more likely to it seems:

[http://thinkwiki.org/wiki/ThinkPad_11a/b/g/n_Wireless_LAN_Mini_Express_Adapter](http://thinkwiki.org/wiki/ThinkPad_11a/b/g/n_Wireless_LAN_Mini_Express_Adapter)

That works for me on a new MBP. You NEED to take the Thinkpad-Driver listed in the URL above. The D-Link driver doesn't work. And then you have to compile ndiswrapper yourself (i use 1.37). The computer hangs as soon as your do modprobe ndiswrapper with the module from the ubuntu repository. Make sure you uninstall the ubuntu-ndiswrapper completely before inserting the modules if you tried that version before (not only with uninstall in synaptic, but also with make uninstall in the ndiswrapper-1.37 source directory...) otherwise it won't work...

---

### Post by bitsent on 2007-10-30
Try ```
dmesg |grep Atheros
``` to see what card you have.  My MacBook (not Pro) has the Atheros 5418.  This chipset isn't fully supported yet; [_this_]("http://madwifi.org/ticket/1017") bug has been pestering me for months.  However, it is usable.  Here is what got it working:

```
sudo apt-get install subversion build-essential
svn checkout http://svn.madwifi.org/madwifi/trunk madwifi 
cd madwifi
sudo ifconfig ath0 down; sudo ifconfig wifi0 down # may report errors
make 
sudo make install 
sudo modprobe ath_pci # load driver (should begin working at this point if Network Manager is up; if not, reboot)
```

---

### Post by emil.s on 2007-10-31
> **bitsent said:**
> Try ```
dmesg |grep Atheros
``` to see what card you have.  My MacBook (not Pro) has the Atheros 5418.  This chipset isn't fully supported yet; [_this_]("http://madwifi.org/ticket/1017") bug has been pestering me for months.  However, it is usable.  Here is what got it working:

```
sudo apt-get install subversion build-essential
svn checkout http://svn.madwifi.org/madwifi/trunk madwifi 
cd madwifi
sudo ifconfig ath0 down; sudo ifconfig wifi0 down # may report errors
make 
sudo make install 
sudo modprobe ath_pci # load driver (should begin working at this point if Network Manager is up; if not, reboot)
```

Hi! Thanks for helping, but this is an old tread. ;)
The problem was a that HAL didn't support the new chipset in MBP 2nd gen.
[http://madwifi.org/ticket/1001](http://madwifi.org/ticket/1001)

But it's solved for about a half year ago, and now it works great using Madwifi's trunk. :)

---

