---
title: "Wireless Connection Problem"
date: 2006-11-09
forum: Networking &amp; Wireless
---

### Post by FrancJP on 2006-11-09
Hi, i have the same problem than other posts, but i didn´t see anything that could help me to solve my issue.

I just install Edgy from zero (i used to have Breezy). The problem is that i have a Belkin USB device to connect to internet. In breezy i´ve downloaded the ndiswrapper and works without problems. Now i did the same after the install, follow the steps to get the belkin works, but i can´t connect to internet at all ](*,) 

The driver is recognized, the hardware is recognized, but i can´t do a wlan0 scan.

My "/etc/network/modules" is like this.

> auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid wireless

iface rausb0 inet dhcp
wireless-essid wireless
wireless-key s:

auto rausb0

Ah, one more thing, when i look in "/system/administration/network" i have to activate the wireless conection every time... but with no luck. Can someone help me please?? :( 
Thanks in advance, and sorry for my english, it´s no my primary lenguage

---

### Post by FrodoB on 2006-11-09
Publish your exact device model and version name and number. Give us the outputs of: iwconfig, lsusb, ifconfig, and dmesg.

It sounds like your device has been found already, so you may not need ndiswrapper.

---

### Post by FrancJP on 2006-11-09
> It sounds like your device has been found already, so you may not need ndiswrapper.
Yes, i tought that in a first moment, but when i try to activate the wlan, it doesn´t recognize at all the belkin card.

My ifconfig it´s like this:
> $ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0F:B0:42:CD:CD  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:185 Base address:0xe000 

rausb0    Link encap:Ethernet  HWaddr 00:11:50:88:3A:6B  
          inet6 addr: fe80::211:50ff:fe88:3a6b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:29667 (28.9 KiB)  TX bytes:10296 (10.0 KiB)


My lsusb is this:
> :~$ lsusb
Bus 003 Device 003: ID 050d:7050 Belkin Components F5D7050 ver 1000 WiFi
Bus 003 Device 002: ID 0d49:7250 Maxtor 
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000


My iwconfig say this:
> $ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

rausb0    RT2500USB WLAN  ESSID:"wireless"  
          Mode:Managed  Frequency=2.412 GHz  Bit Rate=11 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=0/70  Signal level:-120 dBm  Noise level:-195 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


And my dmesg say this:
> ~$ dmesg
[17179569.184000] Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000d0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001ff70000 (usable)
[17179569.184000]  BIOS-e820: 000000001ff70000 - 000000001ff7f000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000001ff7f000 - 000000001ff80000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000001ff80000 - 0000000020000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 511MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 130928
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 126832 pages, LIFO batch:31
[17179569.184000] DMI present.
[17179569.184000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f7260
[17179569.184000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x1ff7a89f
[17179569.184000] ACPI: FADT (v001 NVIDIA CK8      0x06040000 PTL_ 0x000f4240) @ 0x1ff7ee34
[17179569.184000] ACPI: MADT (v001 NVIDIA NV_APIC_ 0x06040000  LTP 0x00000000) @ 0x1ff7eea8
[17179569.184000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x1ff7ef02
[17179569.184000] ACPI: SSDT (v001 PTLTD  POWERNOW 0x06040000  LTP 0x00000001) @ 0x1ff7ef2a
[17179569.184000] ACPI: DSDT (v001 NVIDIA      CK8 0x06040000 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x8008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:12 APIC version 16
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: BIOS IRQ0 pin2 override ignored.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 30000000 (gap: 20000000:dff80000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda2 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[17179569.184000] Detected 797.996 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179570.408000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179570.408000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179570.424000] Memory: 509288k/523712k available (1910k kernel code, 13840k reserved, 1070k data, 308k init, 0k highmem)
[17179570.424000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179570.504000] Calibrating delay using timer specific routine.. 1598.04 BogoMIPS (lpj=3196093)
[17179570.504000] Security Framework v1.0.0 initialized
[17179570.504000] SELinux:  Disabled at boot.
[17179570.504000] Mount-cache hash table entries: 512
[17179570.504000] CPU: After generic identify, caps: 078bfbff c1d3fbff 00000000 00000000 00000000 00000000 00000000
[17179570.504000] CPU: After vendor identify, caps: 078bfbff c1d3fbff 00000000 00000000 00000000 00000000 00000000
[17179570.504000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179570.504000] CPU: L2 Cache: 256K (64 bytes/line)
[17179570.504000] CPU: After all inits, caps: 078bfbff c1d3fbff 00000000 00000410 00000000 00000000 00000000
[17179570.504000] Checking 'hlt' instruction... OK.
[17179570.520000] SMP alternatives: switching to UP code
[17179570.520000] Freeing SMP alternatives: 16k freed
[17179570.520000] checking if image is initramfs... it is
[17179571.660000] Freeing initrd memory: 5563k freed
[17179571.660000] ACPI: Core revision 20060707
[17179571.664000] ACPI: Looking for DSDT ... not found!
[17179571.688000] CPU0: AMD Athlon(tm) XP Processor 3000+ stepping 00
[17179571.688000] Total of 1 processors activated (1598.04 BogoMIPS).
[17179571.688000] ENABLING IO-APIC IRQs
[17179571.688000] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[17179571.836000] Brought up 1 CPUs
[17179571.836000] migration_cost=0
[17179571.836000] NET: Registered protocol family 16
[17179571.836000] EISA bus registered
[17179571.836000] ACPI: bus type pci registered
[17179571.836000] PCI: PCI BIOS revision 2.10 entry at 0xfd8bc, last bus=2
[17179571.836000] PCI: Using configuration type 1
[17179571.836000] Setting up standard PCI resources
[17179571.840000] ACPI: Interpreter enabled
[17179571.840000] ACPI: Using IOAPIC for interrupt routing
[17179571.840000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179571.840000] PCI: Probing PCI hardware (bus 00)
[17179571.964000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:08.0
[17179571.964000] PCI: Bus #03 (-#06) is hidden behind  bridge #02 (-#02) (try 'pci=assign-busses')
[17179571.964000] Please report the result to linux-kernel to fix this permanently
[17179571.964000] PCI: Bus #07 (-#0a) is hidden behind  bridge #02 (-#02) (try 'pci=assign-busses')
[17179571.964000] Please report the result to linux-kernel to fix this permanently
[17179571.964000] Boot video device is 0000:01:00.0
[17179571.964000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179571.988000] ACPI: Embedded Controller [EC0] (gpe 33) interrupt mode.
[17179572.032000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[17179572.036000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP0._PRT]
[17179572.036000] ACPI: PCI Interrupt Link [LNK1] (IRQs 16 18 19) *0
[17179572.036000] ACPI: PCI Interrupt Link [LNK2] (IRQs 16 18 19) *0
[17179572.036000] ACPI: PCI Interrupt Link [LNK3] (IRQs 17) *0, disabled.
[17179572.036000] ACPI: PCI Interrupt Link [LNK4] (IRQs 16 18 19) *0, disabled.
[17179572.036000] ACPI: PCI Interrupt Link [LNK5] (IRQs 16 18 19) *0
[17179572.040000] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22) *0
[17179572.040000] ACPI: PCI Interrupt Link [LUS0] (IRQs 20 21 22) *0
[17179572.040000] ACPI: PCI Interrupt Link [LUS1] (IRQs 20 21 22) *0
[17179572.040000] ACPI: PCI Interrupt Link [LUS2] (IRQs 20 21 22) *0
[17179572.040000] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22) *0, disabled.
[17179572.040000] ACPI: PCI Interrupt Link [LACI] (IRQs 20 21 22) *0
[17179572.040000] ACPI: PCI Interrupt Link [LMCI] (IRQs 20 21 22) *0
[17179572.044000] ACPI: PCI Interrupt Link [LPID] (IRQs 20 21 22) *0, disabled.
[17179572.044000] ACPI: PCI Interrupt Link [LTID] (IRQs 20 21 22) *0, disabled.
[17179572.044000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179572.044000] pnp: PnP ACPI init
[17179572.068000] pnp: PnP ACPI: found 12 devices
[17179572.068000] PnPBIOS: Disabled by ACPI PNP
[17179572.068000] PCI: Using ACPI for IRQ routing
[17179572.068000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179572.072000] pnp: 00:01: ioport range 0x8000-0x807f could not be reserved
[17179572.072000] pnp: 00:01: ioport range 0x8080-0x80ff has been reserved
[17179572.072000] pnp: 00:01: ioport range 0x8400-0x847f has been reserved
[17179572.072000] pnp: 00:01: ioport range 0x8480-0x84ff could not be reserved
[17179572.072000] pnp: 00:01: ioport range 0x8800-0x887f has been reserved
[17179572.072000] pnp: 00:01: ioport range 0x8880-0x88ff has been reserved
[17179572.072000] pnp: 00:01: ioport range 0x2040-0x207f has been reserved
[17179572.072000] pnp: 00:01: ioport range 0x2000-0x203f has been reserved
[17179572.072000] PCI: Failed to allocate mem resource #10:2000000@ea000000 for 0000:02:04.0
[17179572.072000] PCI: Failed to allocate mem resource #10:2000000@ea000000 for 0000:02:04.1
[17179572.072000] PCI: Bus 3, cardbus bridge: 0000:02:04.0
[17179572.072000]   IO window: 00003000-000030ff
[17179572.072000]   IO window: 00003400-000034ff
[17179572.072000]   PREFETCH window: 30000000-31ffffff
[17179572.072000] PCI: Bus 7, cardbus bridge: 0000:02:04.1
[17179572.072000]   IO window: 00003800-000038ff
[17179572.072000]   IO window: 00003c00-00003cff
[17179572.072000]   PREFETCH window: 32000000-33ffffff
[17179572.072000] PCI: Bridge: 0000:00:0a.0
[17179572.072000]   IO window: 3000-7fff
[17179572.072000]   MEM window: e8100000-e97fffff
[17179572.072000]   PREFETCH window: 30000000-33ffffff
[17179572.072000] PCI: Bridge: 0000:00:0b.0
[17179572.072000]   IO window: disabled.
[17179572.072000]   MEM window: ea000000-eaffffff
[17179572.072000]   PREFETCH window: f8000000-fc0fffff
[17179572.072000] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[17179572.072000] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 19
[17179572.072000] ACPI: PCI Interrupt 0000:02:04.0[A] -> Link [LNK1] -> GSI 19 (level, low) -> IRQ 177
[17179572.076000] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 18
[17179572.076000] ACPI: PCI Interrupt 0000:02:04.1[B] -> Link [LNK2] -> GSI 18 (level, low) -> IRQ 185
[17179572.076000] NET: Registered protocol family 2
[17179572.116000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179572.116000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[17179572.116000] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[17179572.116000] TCP: Hash tables configured (established 16384 bind 8192)
[17179572.116000] TCP reno registered
[17179572.116000] Simple Boot Flag at 0x37 set to 0x1
[17179572.116000] audit: initializing netlink socket (disabled)
[17179572.116000] audit(1163102382.116:1): initialized
[17179572.116000] VFS: Disk quotas dquot_6.5.1
[17179572.116000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179572.116000] Initializing Cryptographic API
[17179572.116000] io scheduler noop registered
[17179572.116000] io scheduler anticipatory registered
[17179572.116000] io scheduler deadline registered
[17179572.116000] io scheduler cfq registered (default)
[17179572.116000] isapnp: Scanning for PnP cards...
[17179572.472000] isapnp: No Plug & Play device found
[17179572.508000] Real Time Clock Driver v1.12ac
[17179572.508000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179572.512000] ACPI: PCI Interrupt Link [LMCI] enabled at IRQ 22
[17179572.512000] ACPI: PCI Interrupt 0000:00:06.1[B] -> Link [LMCI] -> GSI 22 (level, low) -> IRQ 193
[17179572.512000] ACPI: PCI interrupt for device 0000:00:06.1 disabled
[17179572.512000] mice: PS/2 mouse device common for all mice
[17179572.512000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179572.512000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179572.512000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179572.512000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179572.524000] i8042.c: Detected active multiplexing controller, rev 1.1.
[17179572.528000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[17179572.528000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[17179572.528000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[17179572.528000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[17179572.532000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179572.532000] EISA: Probing bus 0 at eisa.0
[17179572.532000] Cannot allocate resource for EISA slot 1
[17179572.532000] Cannot allocate resource for EISA slot 2
[17179572.532000] Cannot allocate resource for EISA slot 3
[17179572.532000] Cannot allocate resource for EISA slot 4
[17179572.532000] Cannot allocate resource for EISA slot 5
[17179572.532000] Cannot allocate resource for EISA slot 6
[17179572.532000] Cannot allocate resource for EISA slot 7
[17179572.532000] Cannot allocate resource for EISA slot 8
[17179572.532000] EISA: Detected 0 cards.
[17179572.536000] TCP bic registered
[17179572.536000] NET: Registered protocol family 1
[17179572.536000] NET: Registered protocol family 8
[17179572.536000] NET: Registered protocol family 20
[17179572.536000] Using IPI No-Shortcut mode
[17179572.536000] ACPI: (supports S0 S3 S4 S5)
[17179572.536000] Freeing unused kernel memory: 308k freed
[17179572.788000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179573.812000] Capability LSM initialized
[17179573.876000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[17179573.884000] ACPI Exception (acpi_thermal-0417): AE_NOT_FOUND, Invalid active threshold [0] [20060707]
[17179573.888000] ACPI: Thermal Zone [THRM] (52 C)
[17179574.640000] SCSI subsystem initialized
[17179574.648000] libata version 1.20 loaded.
[17179574.652000] NFORCE3-150: IDE controller at PCI slot 0000:00:08.0
[17179574.652000] NFORCE3-150: chipset revision 165
[17179574.652000] NFORCE3-150: not 100% native mode: will probe irqs later
[17179574.652000] NFORCE3-150: BIOS didn't set cable bits correctly. Enabling workaround.
[17179574.652000] NFORCE3-150: 0000:00:08.0 (rev a5) UDMA133 controller
[17179574.652000]     ide0: BM-DMA at 0x2080-0x2087, BIOS settings: hda:DMA, hdb:pio
[17179574.652000]     ide1: BM-DMA at 0x2088-0x208f, BIOS settings: hdc:DMA, hdd:pio
[17179574.652000] Probing IDE interface ide0...
[17179574.940000] hda: ST94019A, ATA DISK drive
[17179575.612000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179575.808000] Probing IDE interface ide1...
[17179576.548000] hdc: _NEC DVD+/-RW ND-6450A, ATAPI CD/DVD-ROM drive
[17179577.236000] ide1 at 0x170-0x177,0x376 on irq 15
[17179577.252000] hda: max request size: 512KiB
[17179577.268000] hda: 78140160 sectors (40007 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
[17179577.268000] hda: cache flushes supported
[17179577.268000]  hda: hda1 hda2 hda3 hda4
[17179577.544000] hdc: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, DMA
[17179577.544000] Uniform CD-ROM driver Revision: 3.20
[17179577.996000] usbcore: registered new driver usbfs
[17179577.996000] usbcore: registered new driver hub
[17179578.000000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179578.000000] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 21
[17179578.000000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LUS0] -> GSI 21 (level, low) -> IRQ 201
[17179578.000000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[17179578.000000] ohci_hcd 0000:00:02.0: OHCI Host Controller
[17179578.004000] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[17179578.204000] ohci_hcd 0000:00:02.0: irq 201, io mem 0xe8000000
[17179578.260000] usb usb1: configuration #1 chosen from 1 choice
[17179578.264000] hub 1-0:1.0: USB hub found
[17179578.264000] hub 1-0:1.0: 3 ports detected
[17179578.368000] ACPI: PCI Interrupt Link [LUS1] enabled at IRQ 20
[17179578.368000] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [LUS1] -> GSI 20 (level, low) -> IRQ 209
[17179578.368000] PCI: Setting latency timer of device 0000:00:02.1 to 64
[17179578.368000] ohci_hcd 0000:00:02.1: OHCI Host Controller
[17179578.368000] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[17179578.568000] ohci_hcd 0000:00:02.1: irq 209, io mem 0xe8001000
[17179578.624000] usb usb2: configuration #1 chosen from 1 choice
[17179578.624000] hub 2-0:1.0: USB hub found
[17179578.624000] hub 2-0:1.0: 3 ports detected
[17179578.728000] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 22
[17179578.728000] ACPI: PCI Interrupt 0000:00:02.2[C] -> Link [LUS2] -> GSI 22 (level, low) -> IRQ 193
[17179578.728000] PCI: Setting latency timer of device 0000:00:02.2 to 64
[17179578.728000] ehci_hcd 0000:00:02.2: EHCI Host Controller
[17179578.728000] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 3
[17179578.728000] PCI: cache line size of 64 is not supported by device 0000:00:02.2
[17179578.728000] ehci_hcd 0000:00:02.2: irq 193, io mem 0xe8004000
[17179578.728000] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179578.728000] usb usb3: configuration #1 chosen from 1 choice
[17179578.732000] hub 3-0:1.0: USB hub found
[17179578.732000] hub 3-0:1.0: 6 ports detected
[17179578.900000] Attempting manual resume
[17179578.948000] kjournald starting.  Commit interval 5 seconds
[17179578.948000] EXT3-fs: mounted filesystem with ordered data mode.
[17179579.076000] usb 3-2: new high speed USB device using ehci_hcd and address 2
[17179579.224000] usb 3-2: configuration #1 chosen from 1 choice
[17179591.296000] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x2040
[17179591.300000] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x2000
[17179592.068000] parport: PnPBIOS parport detected.
[17179592.068000] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[17179592.532000] input: PS/2 Mouse as /class/input/input1
[17179592.556000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input3
[17179592.560000] input: PC Speaker as /class/input/input2
[17179592.968000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179592.984000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179593.272000] usbcore: registered new driver libusual
[17179593.568000] Linux agpgart interface v0.101 (c) Dave Jones
[17179593.572000] agpgart: Detected AGP bridge 0
[17179593.572000] agpgart: Setting up Nforce3 AGP.
[17179593.580000] agpgart: AGP aperture is 128M @ 0xf0000000
[17179593.600000] Initializing USB Mass Storage driver...
[17179593.600000] scsi0 : SCSI emulation for USB Mass Storage devices
[17179593.600000] usbcore: registered new driver usb-storage
[17179593.600000] USB Mass Storage support registered.
[17179593.600000] usb-storage: device found at 2
[17179593.600000] usb-storage: waiting for device to settle before scanning
[17179593.844000] ACPI: PCI Interrupt Link [LACI] enabled at IRQ 21
[17179593.844000] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [LACI] -> GSI 21 (level, low) -> IRQ 201
[17179593.844000] PCI: Setting latency timer of device 0000:00:06.0 to 64
[17179594.144000] ts: Compaq touchscreen protocol output
[17179594.412000] intel8x0_measure_ac97_clock: measured 55282 usecs
[17179594.412000] intel8x0: clocking to 48000
[17179594.412000] ACPI: PCI Interrupt 0000:02:04.0[A] -> Link [LNK1] -> GSI 19 (level, low) -> IRQ 177
[17179594.412000] Yenta: CardBus bridge found at 0000:02:04.0 [103c:006d]
[17179594.412000] PCI: Bus 3, cardbus bridge: 0000:02:04.0
[17179594.412000]   IO window: 00003000-000030ff
[17179594.412000]   IO window: 00003400-000034ff
[17179594.412000]   PREFETCH window: 30000000-31ffffff
[17179594.412000]   MEM window: e8400000-e87fffff
[17179594.412000] Yenta: Enabling burst memory read transactions
[17179594.412000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179594.412000] Yenta: Routing CardBus interrupts to PCI
[17179594.412000] Yenta TI: socket 0000:02:04.0, mfunc 0x01111d22, devctl 0x64
[17179594.632000] 8139too Fast Ethernet driver 0.9.27
[17179594.644000] Yenta: ISA IRQ mask 0x0c38, PCI irq 177
[17179594.644000] Socket status: 30000086
[17179594.644000] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
[17179594.644000] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x7fff
[17179594.644000] cs: IO port probe 0x3000-0x7fff: clean.
[17179594.644000] pcmcia: parent PCI bridge Memory window: 0xe8100000 - 0xe97fffff
[17179594.644000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
[17179594.788000] ACPI: PCI Interrupt 0000:02:04.1[B] -> Link [LNK2] -> GSI 18 (level, low) -> IRQ 185
[17179594.788000] Yenta: CardBus bridge found at 0000:02:04.1 [103c:006d]
[17179594.788000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179594.788000] Yenta: Routing CardBus interrupts to PCI
[17179594.788000] Yenta TI: socket 0000:02:04.1, mfunc 0x01111d22, devctl 0x64
[17179595.020000] Yenta: ISA IRQ mask 0x0c38, PCI irq 185
[17179595.020000] Socket status: 30000006
[17179595.020000] Yenta: Raising subordinate bus# of parent bus (#02) from #06 to #0a
[17179595.020000] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x7fff
[17179595.020000] cs: IO port probe 0x3000-0x7fff: clean.
[17179595.020000] pcmcia: parent PCI bridge Memory window: 0xe8100000 - 0xe97fffff
[17179595.020000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
[17179595.032000] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNK2] -> GSI 18 (level, low) -> IRQ 185
[17179595.032000] eth0: RealTek RTL8139 at 0xe0a5e000, 00:0f:b0:42:cd:cd, IRQ 185
[17179595.032000] eth0:  Identified 8139 chip type 'RTL-8101'
[17179595.056000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[17179595.176000] eth0: link down
[17179595.640000] cs: IO port probe 0x100-0x3af: excluding 0x200-0x20f
[17179595.644000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[17179595.644000] cs: IO port probe 0x820-0x8ff: clean.
[17179595.644000] cs: IO port probe 0xc00-0xcf7: clean.
[17179595.648000] cs: IO port probe 0xa00-0xaff: clean.
[17179595.652000] cs: IO port probe 0x100-0x3af: excluding 0x200-0x20f
[17179595.652000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[17179595.656000] cs: IO port probe 0x820-0x8ff: clean.
[17179595.656000] cs: IO port probe 0xc00-0xcf7: clean.
[17179595.656000] cs: IO port probe 0xa00-0xaff: clean.
[17179595.864000] floppy0: no floppy controllers found
[17179596.040000] lp0: using parport0 (interrupt-driven).
[17179596.080000] ndiswrapper version 1.28 loaded (preempt=no,smp=yes)
[17179596.120000] usbcore: registered new driver ndiswrapper
[17179596.172000] Adding 1084376k swap on /dev/disk/by-uuid/edc960ee-838f-43e3-b022-5713a09bb50b.  Priority:-1 extents:1 across:1084376k
[17179596.244000] NET: Registered protocol family 17
[17179596.360000] EXT3 FS on hda2, internal journal
[17179598.600000] usb-storage: device scan complete
[17179598.632000]   Vendor: Maxtor    Model: OneTouch III      Rev: 0362
[17179598.632000]   Type:   Direct-Access                      ANSI SCSI revision: 04
[17179598.732000] SCSI device sda: 195371568 512-byte hdwr sectors (100030 MB)
[17179598.736000] sda: Write Protect is off
[17179598.736000] sda: Mode Sense: 17 00 00 00
[17179598.736000] sda: assuming drive cache: write through
[17179598.736000] SCSI device sda: 195371568 512-byte hdwr sectors (100030 MB)
[17179598.736000] sda: Write Protect is off
[17179598.736000] sda: Mode Sense: 17 00 00 00
[17179598.736000] sda: assuming drive cache: write through
[17179598.736000]  sda: sda1
[17179598.972000] sd 0:0:0:0: Attached scsi disk sda
[17179599.020000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179622.584000] kjournald starting.  Commit interval 5 seconds
[17179622.592000] EXT3 FS on hda3, internal journal
[17179622.592000] EXT3-fs: mounted filesystem with ordered data mode.
[17179631.260000] ACPI: AC Adapter [ACAD] (on-line)
[17179631.436000] ACPI: Battery Slot [BAT1] (battery present)
[17179631.468000] ACPI: Power Button (FF) [PWRF]
[17179631.468000] ACPI: Power Button (CM) [PWRB]
[17179631.468000] ACPI: Lid Switch [LID]
[17179631.708000] ibm_acpi: ec object not found
[17179631.756000] pcc_acpi: loading...
[17179631.944000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[17179632.316000] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.60.2)
[17179632.320000] powernow-k8:    0 : fid 0x8 (1600 MHz), vid 0x6 (1400 mV)
[17179632.320000] powernow-k8:    1 : fid 0x0 (800 MHz), vid 0x18 (950 mV)
[17179632.320000] cpu_init done, current fid 0x0, vid 0x18
[17179634.580000] apm: BIOS not found.
[17179639.340000] Bluetooth: Core ver 2.8
[17179639.340000] NET: Registered protocol family 31
[17179639.340000] Bluetooth: HCI device and connection manager initialized
[17179639.340000] Bluetooth: HCI socket layer initialized
[17179639.376000] Bluetooth: L2CAP ver 2.8
[17179639.376000] Bluetooth: L2CAP socket layer initialized
[17179639.412000] Bluetooth: RFCOMM socket layer initialized
[17179639.412000] Bluetooth: RFCOMM TTY layer initialized
[17179639.412000] Bluetooth: RFCOMM ver 1.7
[17179785.960000] NET: Registered protocol family 10
[17179785.960000] lo: Disabled Privacy Extensions
[17179785.960000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179785.960000] IPv6 over IPv4 tunneling driver
[17179790.384000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17179817.468000] usb 3-3: new high speed USB device using ehci_hcd and address 3
[17179817.768000] usb 3-3: configuration #1 chosen from 1 choice
[17179818.212000] idVendor = 0x50d, idProduct = 0x7050 
[17179818.212000] INIT bRadio=1
[17179818.212000] usbcore: registered new driver rtusb
[17179818.300000] Loading module: rt73usb - CVS (N/A) by [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com).
[17179818.300000] usbcore: registered new driver rt73usb
[17179818.304000] rausb0 (WE) : Driver using old /proc/net/wireless support, please fix driver !
[17179818.372000] ieee80211_crypt: registered algorithm 'NULL'
[17179818.384000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[17179818.384000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[17179818.424000] usbcore: registered new driver islusb
[17179818.600000] RT25usb  Driver version 1.1.0
[17179830.060000] rausb0: no IPv6 routers present


When i look on properties of the two monitors (for internet), says only "Lo", with no other choice... maybe we got the problem here, i don´t know.

But if something above it´s wrong, i hope you find it.

Thanks in advance

---

### Post by FrodoB on 2006-11-10
What happens if you scan rausb0:

$ iwlist rausb0 scan

Your device seems to be part way there now.  If you installed drivers using ndiswrapper already, maybe you should remove them, reboot and try again. You seem close. Repost iwconfig after your reboot.

---

### Post by FrodoB on 2006-11-10
I have a last best hope idea for you.  Replace the rt2500 driver in Edgy with a new module. It worked for me with another Ralink device in Edgy, no guarantees:

1. You will need to install the kernel sources to compile the driver so if you do not have them already them:

$ sudo apt-get install linux-source-2.6.17

or use Synaptic if you prefer to get the same package.

2. Go to the rt2x00 site and get the latest version of the rt2500 driver (Latest BETA rt2500 driver: v1.1.0-b4):

[http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads](http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads)

Download it to your machine and put it into your home directory

3. Open a terminal window and then untar the archive:

$ tar xvzf rt2500-1.1.0-b4.tar.gz


4. Change to the new directory that it created:

$ cd rt2500-1.1.0-b4/Module

5. Run the make command and then make install:

$ make

This will take 1-5 minutes depending upon the speed of your machine.

6. Then you need to install the driver with make install:

$ sudo make install

This happens very quickly.

7. Now reboot your system without having your wireless device installed.

8. Open a terminal window and type ifconfig, you should see that it is not installed.

9. Insert your wireless device, and after waiting about 10 seconds run iwconfig again. If you already had the device configured it may just start working.

10. If your device did not work then go to the System -> Administration -> Networking control and try to configure it.

11. If this did not help you are at least no worse off.  It helped me with a similar device in a similar situation.

12. Also, look at the README file in the Modules directory, it give instructions for compiling a Ralink control for managing the device that you might find helpful.

If you have a problem let me know.

---

### Post by FrodoB on 2006-11-10
You should also remove ndiswrapper and blacklist rt73 and rt73usb and repost your dmesg, those should not be there.

You might want to do this even before rebuilding the drivers.

Sorry, I just noticed those.

---

### Post by FrodoB on 2006-11-11
Any progress?

---

