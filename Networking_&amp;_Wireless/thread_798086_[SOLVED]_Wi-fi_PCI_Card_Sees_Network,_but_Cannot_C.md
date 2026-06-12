---
title: "[SOLVED] Wi-fi PCI Card Sees Network, but Cannot Connect"
date: 2008-05-17
forum: Networking &amp; Wireless
---

### Post by ciamele on 2008-05-17
I have a wireless PCI card that can see my network (and others nearby), but it cannot connect. I believe this to be an issue with the driver since I'm able to connect wirelessly with my laptop.

I've seen other having this issue with this specific card, but there doesn't seem to be a posted solution.

**The details:**
OS: Ubuntu 7.10
PCI Card: Airlink101 AWLH3026
Network Security: WEP

**lspci:**
> 00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82815 815 Chipset AGP Bridge (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 02)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 02)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 02)
01:0a.0 Ethernet controller: Lite-On Communications Inc LNE100TX (rev 20)
01:0b.0 Network controller: RaLink RT2561/RT61 802.11g PCI
02:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 PF/PRO AGP 4x TMDS


**Interfaces file:**
> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback


iface ra0 inet dhcp
wireless-essid <my_network_name>
wireless-key <wep_key>

auto ra0

**iwconfig**:
> lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan1     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

**dmesg** (after I've made an attmept tp connect to my network):
> [    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 07:42:25 UTC 2008 (Ubuntu 2.6.22-14.52-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001ffc0000 (usable)
[    0.000000]  BIOS-e820: 000000001ffc0000 - 000000001fff8000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001fff8000 - 0000000020000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000ffb80000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 131008) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   131008
[    0.000000]   HighMem    131008 ->   131008
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   131008
[    0.000000] On node 0 totalpages: 131008
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 991 pages used for memmap
[    0.000000]   Normal zone: 125921 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FF980 checksum 0
[    0.000000] ACPI: RSDP 000FF980, 0014 (r0 AMI   )
[    0.000000] ACPI: RSDT 1FFF0000, 0028 (r1 D815EA EA81510A 20001114 MSFT     1011)
[    0.000000] ACPI: FACP 1FFF1000, 0074 (r1 D815EA EA81510A 20001114 MSFT     1011)
[    0.000000] ACPI: DSDT 1FFE0000, 2FEB (r1 D815EA EA81510A       15 MSFT  100000B)
[    0.000000] ACPI: FACS 1FFF8000, 0040
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dfb80000)
[    0.000000] Built 1 zonelists.  Total pages: 129985
[    0.000000] Kernel command line: root=UUID=d7da4ec1-b051-4db6-8987-d53918f1cefc ro quiet splash 
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffd000 (0140d000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 930.343 MHz processor.
[   17.768971] Console: colour VGA+ 80x25
[   17.769776] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   17.770799] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   17.814119] Memory: 507916k/524032k available (2015k kernel code, 15484k reserved, 915k data, 364k init, 0k highmem)
[   17.814143] virtual kernel memory layout:
[   17.814146]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   17.814149]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   17.814153]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   17.814156]     lowmem  : 0xc0000000 - 0xdffc0000   ( 511 MB)
[   17.814159]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   17.814162]       .data : 0xc02f7e86 - 0xc03dce84   ( 915 kB)
[   17.814165]       .text : 0xc0100000 - 0xc02f7e86   (2015 kB)
[   17.814173] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   17.814253] SLUB: Genslabs=22, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   17.894234] Calibrating delay using timer specific routine.. 1862.21 BogoMIPS (lpj=3724426)
[   17.894288] Security Framework v1.0.0 initialized
[   17.894303] SELinux:  Disabled at boot.
[   17.894336] Mount-cache hash table entries: 512
[   17.894581] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   17.894604] CPU: L1 I cache: 16K, L1 D cache: 16K
[   17.894610] CPU: L2 cache: 256K
[   17.894617] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[   17.894638] Compat vDSO mapped to ffffe000.
[   17.894666] Checking 'hlt' instruction... OK.
[   17.910421] SMP alternatives: switching to UP code
[   17.910750] Freeing SMP alternatives: 11k freed
[   17.911340] Early unpacking initramfs... done
[   18.647328] ACPI: Core revision 20070126
[   18.647547] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   18.651288] ACPI: setting ELCR to 0200 (from 0e00)
[   18.652397] CPU0: Intel Pentium III (Coppermine) stepping 06
[   18.652410] SMP motherboard not detected.
[   18.652416] Local APIC not detected. Using dummy APIC emulation.
[   18.652506] Brought up 1 CPUs
[   18.652797] Booting paravirtualized kernel on bare hardware
[   18.652923] Time:  1:00:25  Date: 04/18/108
[   18.652985] NET: Registered protocol family 16
[   18.653226] EISA bus registered
[   18.653249] ACPI: bus type pci registered
[   18.653884] PCI: PCI BIOS revision 2.10 entry at 0xfda95, last bus=2
[   18.653890] PCI: Using configuration type 1
[   18.653895] Setting up standard PCI resources
[   18.657551] ACPI: EC: Look up EC in DSDT
[   18.666102] ACPI: Interpreter enabled
[   18.666113] ACPI: (supports S0 S1 S4 S5)
[   18.666149] ACPI: Using PIC for interrupt routing
[   18.677266] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   18.677306] PCI: Probing PCI hardware (bus 00)
[   18.677586] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[   18.677594] PCI quirk: region 0500-053f claimed by ICH4 GPIO
[   18.678261] PCI: Transparent bridge - 0000:00:1e.0
[   18.678304] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   18.678555] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[   18.681268] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12)
[   18.681477] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *9 10 11 12)
[   18.682219] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11 12) *0, disabled.
[   18.682427] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12)
[   18.682631] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12) *0, disabled.
[   18.682837] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12) *0, disabled.
[   18.683043] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11 12)
[   18.683247] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 *10 11 12)
[   18.683514] ACPI: Power Resource [URP1] (off)
[   18.683580] ACPI: Power Resource [URP2] (off)
[   18.683645] ACPI: Power Resource [FDDP] (off)
[   18.683710] ACPI: Power Resource [LPTP] (off)
[   18.683734] Linux Plug and Play Support v0.97 (c) Adam Belay
[   18.683759] pnp: PnP ACPI init
[   18.683798] ACPI: bus type pnp registered
[   18.691950] pnp: PnP ACPI: found 15 devices
[   18.691958] ACPI: ACPI bus type pnp unregistered
[   18.691969] PnPBIOS: Disabled by ACPI PNP
[   18.692091] PCI: Using ACPI for IRQ routing
[   18.692099] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   18.695325] NET: Registered protocol family 8
[   18.695331] NET: Registered protocol family 20
[   18.695506] pnp: 00:0e: iomem range 0x0-0x9ffff could not be reserved
[   18.695514] pnp: 00:0e: iomem range 0xe0000-0xfffff could not be reserved
[   18.695521] pnp: 00:0e: iomem range 0x100000-0x1fffffff could not be reserved
[   18.695528] pnp: 00:0e: iomem range 0x0-0x0 could not be reserved
[   18.698055] Time: tsc clocksource has been installed.
[   18.726177] PCI: Bridge: 0000:00:01.0
[   18.726183]   IO window: d000-dfff
[   18.726191]   MEM window: ff900000-ff9fffff
[   18.726198]   PREFETCH window: eea00000-f6afffff
[   18.726211] PCI: Bridge: 0000:00:1e.0
[   18.726217]   IO window: c000-cfff
[   18.726225]   MEM window: ff800000-ff8fffff
[   18.726232]   PREFETCH window: ee900000-ee9fffff
[   18.726255] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   18.726283] NET: Registered protocol family 2
[   18.765853] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   18.765977] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[   18.766550] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   18.767086] TCP: Hash tables configured (established 16384 bind 16384)
[   18.767094] TCP reno registered
[   18.782065] checking if image is initramfs...<6>Switched to high resolution mode on CPU 0
[   19.400244]  it is
[   20.170652] Freeing initrd memory: 7106k freed
[   20.171447] audit: initializing netlink socket (disabled)
[   20.171479] audit(1211072425.888:1): initialized
[   20.176592] VFS: Disk quotas dquot_6.5.1
[   20.176751] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   20.177015] io scheduler noop registered
[   20.177021] io scheduler anticipatory registered
[   20.177026] io scheduler deadline registered
[   20.177130] io scheduler cfq registered (default)
[   20.177202] Boot video device is 0000:02:00.0
[   20.177570] isapnp: Scanning for PnP cards...
[   20.531273] isapnp: No Plug & Play device found
[   20.598109] Real Time Clock Driver v1.12ac
[   20.598291] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   20.598415] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   20.598783] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   20.600082] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   20.600592] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   20.602375] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   20.602875] input: Macintosh mouse button emulation as /class/input/input0
[   20.603079] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   20.606030] serio: i8042 KBD port at 0x60,0x64 irq 1
[   20.606042] serio: i8042 AUX port at 0x60,0x64 irq 12
[   20.606421] mice: PS/2 mouse device common for all mice
[   20.606651] EISA: Probing bus 0 at eisa.0
[   20.606703] EISA: Detected 0 cards.
[   20.607087] TCP cubic registered
[   20.607127] NET: Registered protocol family 1
[   20.607188] Using IPI No-Shortcut mode
[   20.607548]   Magic number: 8:409:3
[   20.607573]   hash matches device ttybe
[   20.608953] Freeing unused kernel memory: 364k freed
[   20.644892] input: AT Translated Set 2 keyboard as /class/input/input1
[   22.082054] AppArmor: AppArmor initialized<5>audit(1211072427.888:2):  type=1505 info="AppArmor initialized" pid=1179
[   22.097754] fuse init (API version 7.8)
[   22.109786] Failure registering capabilities with primary security module.
[   23.518725] SCSI subsystem initialized
[   23.539186] libata version 2.21 loaded.
[   23.551773] ata_piix 0000:00:1f.1: version 2.11
[   23.551891] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   23.552124] scsi0 : ata_piix
[   23.552219] scsi1 : ata_piix
[   23.552461] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14
[   23.552469] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15
[   23.612352] usbcore: registered new interface driver usbfs
[   23.612407] usbcore: registered new interface driver hub
[   23.612457] usbcore: registered new device driver usb
[   23.615701] USB Universal Host Controller Interface driver v3.0
[   23.723852] ata1.00: ATA-5: WDC WD200EB-32BHF0, 15.15M15, max UDMA/100
[   23.723863] ata1.00: 39102336 sectors, multi 16: LBA 
[   23.724174] ata1.01: ATA-5: Maxtor 91741U4, FA570480, max UDMA/66
[   23.724181] ata1.01: 34004880 sectors, multi 16: LBA 
[   23.739852] ata1.00: configured for UDMA/100
[   23.755227] ata1.01: configured for UDMA/66
[   23.898322] Floppy drive(s): fd0 is 1.44M
[   23.944992] FDC 0 is a post-1991 82077
[   24.025209] Linux Tulip driver version 1.1.15 (Feb 27, 2007)
[   24.074696] ata2.00: ATAPI: ATAPI-CD ROM-DRIVE-52MAX, VER 52AE, max UDMA/33
[   24.238625] ata2.00: configured for UDMA/33
[   24.238891] scsi 0:0:0:0: Direct-Access     ATA      WDC WD200EB-32BH 15.1 PQ: 0 ANSI: 5
[   24.239871] scsi 0:0:1:0: Direct-Access     ATA      Maxtor 91741U4   FA57 PQ: 0 ANSI: 5
[   24.240296] scsi 1:0:0:0: CD-ROM            ATAPI-CD ROM-DRIVE-52MAX  52AE PQ: 0 ANSI: 5
[   24.240982] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[   24.240990] PCI: setting IRQ 11 as level-triggered
[   24.240996] ACPI: PCI Interrupt 0000:00:1f.2[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   24.241018] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   24.241026] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[   24.241275] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[   24.241316] uhci_hcd 0000:00:1f.2: irq 11, io base 0x0000ef40
[   24.241589] usb usb1: configuration #1 chosen from 1 choice
[   24.241651] hub 1-0:1.0: USB hub found
[   24.241669] hub 1-0:1.0: 2 ports detected
[   24.277256] sd 0:0:0:0: [sda] 39102336 512-byte hardware sectors (20020 MB)
[   24.277309] sd 0:0:0:0: [sda] Write Protect is off
[   24.277316] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   24.277354] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.277474] sd 0:0:0:0: [sda] 39102336 512-byte hardware sectors (20020 MB)
[   24.277497] sd 0:0:0:0: [sda] Write Protect is off
[   24.277503] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   24.277538] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.277550]  sda: sda1 sda2 < sda5 >
[   24.331248] sd 0:0:0:0: [sda] Attached SCSI disk
[   24.331685] sd 0:0:1:0: [sdb] 34004880 512-byte hardware sectors (17410 MB)
[   24.331713] sd 0:0:1:0: [sdb] Write Protect is off
[   24.331720] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   24.331757] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.331866] sd 0:0:1:0: [sdb] 34004880 512-byte hardware sectors (17410 MB)
[   24.331888] sd 0:0:1:0: [sdb] Write Protect is off
[   24.331894] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   24.331929] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.331937]  sdb:ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 10
[   24.342944] PCI: setting IRQ 10 as level-triggered
[   24.342951] ACPI: PCI Interrupt 0000:00:1f.4[C] -> Link [LNKH] -> GSI 10 (level, low) -> IRQ 10
[   24.342973] PCI: Setting latency timer of device 0000:00:1f.4 to 64
[   24.342980] uhci_hcd 0000:00:1f.4: UHCI Host Controller
[   24.343035] uhci_hcd 0000:00:1f.4: new USB bus registered, assigned bus number 2
[   24.343073] uhci_hcd 0000:00:1f.4: irq 10, io base 0x0000ef80
[   24.343306] usb usb2: configuration #1 chosen from 1 choice
[   24.343369] hub 2-0:1.0: USB hub found
[   24.343388] hub 2-0:1.0: 2 ports detected
[   24.352032]  sdb1 sdb2 < sdb5 >
[   24.378581] sd 0:0:1:0: [sdb] Attached SCSI disk
[   24.390893] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   24.391331] sd 0:0:1:0: Attached scsi generic sg1 type 0
[   24.391729] scsi 1:0:0:0: Attached scsi generic sg2 type 5
[   24.447886] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 11
[   24.447899] ACPI: PCI Interrupt 0000:01:0a.0[A] -> Link [LNKG] -> GSI 11 (level, low) -> IRQ 11
[   24.448358] tulip0:  MII transceiver #1 config 3000 status 7809 advertising 01e1.
[   24.451787] eth0: Lite-On 82c168 PNIC rev 32 at Port 0xc800, 00:02:E3:08:24:3B, IRQ 11.
[   24.472983] sr0: scsi3-mmc drive: 4x/52x cd/rw xa/form2 cdda tray
[   24.472996] Uniform CD-ROM driver Revision: 3.20
[   24.473126] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   24.582199] usb 1-1: new low speed USB device using uhci_hcd and address 2
[   24.758205] usb 1-1: configuration #1 chosen from 1 choice
[   24.813724] usbcore: registered new interface driver hiddev
[   24.839483] input: Logitech Optical USB Mouse as /class/input/input2
[   24.839844] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1f.2-1
[   24.839877] usbcore: registered new interface driver usbhid
[   24.839886] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   25.052109] Attempting manual resume
[   25.052119] swsusp: Resume From Partition 8:5
[   25.052123] PM: Checking swsusp image.
[   25.052409] PM: Resume from disk failed.
[   25.128904] kjournald starting.  Commit interval 5 seconds
[   25.128933] EXT3-fs: mounted filesystem with ordered data mode.
[   40.683346] Linux agpgart interface v0.102 (c) Dave Jones
[   40.703325] agpgart: Detected an Intel i815 Chipset.
[   40.707578] agpgart: AGP aperture is 64M @ 0xf8000000
[   40.938660] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   40.963349] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   41.584608] intel_rng: Firmware space is locked read-only. <4>intel_rng: If you can't or
[   41.584615]  don't want to <4>intel_rng: disable this in firmware setup, and <4>intel_rng: if
[   41.584620]  you are certain that your <4>intel_rng: system has a functional
[   41.584624]  RNG, try<4>intel_rng: using the 'no_fwh_detect' option.
[   42.316534] input: PC Speaker as /class/input/input3
[   43.371270] iTCO_vendor_support: vendor-support=0
[   43.482454] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   43.483153] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[   43.483169] iTCO_wdt: No card detected
[   43.518802] parport_pc 00:0a: reported by Plug and Play ACPI
[   43.518836] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   43.632134] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 9
[   43.632144] PCI: setting IRQ 9 as level-triggered
[   43.632150] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 9 (level, low) -> IRQ 9
[   43.632179] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   44.305024] intel8x0_measure_ac97_clock: measured 54852 usecs
[   44.305034] intel8x0: clocking to 48000
[   44.306872] ACPI: PCI Interrupt 0000:01:0b.0[A] -> Link [LNKH] -> GSI 10 (level, low) -> IRQ 10
[   44.651344] ieee80211_init: failed to initialize WME (err=-17)
[   44.693028] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_unregister
[   44.693190] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_put
[   44.693320] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_get
[   44.693536] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_register
[   44.694404] wmaster0: Selected rate control algorithm 'simple'
[   45.296875] lp0: using parport0 (interrupt-driven).
[   45.464365] Adding 859436k swap on /dev/sda5.  Priority:-1 extents:1 across:859436k
[   45.982596] EXT3 FS on sda1, internal journal
[   49.263756] NET: Registered protocol family 17
[   51.830459] No dock devices found.
[   52.139836] input: Power Button (FF) as /class/input/input4
[   52.140459] ACPI: Power Button (FF) [PWRF]
[   52.179813] input: Sleep Button (CM) as /class/input/input5
[   52.180414] ACPI: Sleep Button (CM) [SBTN]
[   57.798770] Failure registering capabilities with primary security module.
[   59.017482] [drm] Initialized drm 1.1.0 20060810
[   59.072984] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[   59.072999] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   59.078596] [drm] Initialized r128 2.5.0 20030725 on minor 0
[   59.088272] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   59.088754] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[   59.089088] agpgart: Putting AGP V2 device at 0000:02:00.0 into 1x mode
[   59.251621] ppdev: user-space parallel port driver
[   59.852711] audit(1211072466.535:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5075 profile="/usr/sbin/cupsd"
[   60.043370] apm: BIOS version 1.2 Flags 0x0b (Driver version 1.16ac)
[   60.043383] apm: overridden by ACPI.
[   61.067223] Bluetooth: Core ver 2.11
[   61.067463] NET: Registered protocol family 31
[   61.067469] Bluetooth: HCI device and connection manager initialized
[   61.067477] Bluetooth: HCI socket layer initialized
[   61.091430] Bluetooth: L2CAP ver 2.8
[   61.091441] Bluetooth: L2CAP socket layer initialized
[   61.212634] Bluetooth: RFCOMM socket layer initialized
[   61.212822] Bluetooth: RFCOMM TTY layer initialized
[   61.212828] Bluetooth: RFCOMM ver 1.8
[   91.661939] NET: Registered protocol family 10
[   91.662335] lo: Disabled Privacy Extensions
[   91.662675] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  102.278442] eth0: no IPv6 routers present
[  249.488615] ADDRCONF(NETDEV_UP): wlan1: link is not ready

Many thanks, in advance, for your time and help.

---

### Post by ciamele on 2008-05-18
bump... Anyone? Any ideas? Is there some other info that I could post that would help?

---

### Post by acowboydave on 2008-05-18
Ran into the same problem..my solution..went into Synaptic,,searched for ndisgtk,,enabled that and it loaded two more..
Then if you have your cards installation CD..put that in your DVD/CD player, you should get a breakdown of what is on the CD, Look for drivers..should have listing for Vista or XP.."maybe some day when the companys get stuff together there will be Linux listed"...
Anyways..System>Administration>Windows Wireless Driver..click that and click install driver in the window that appears ..search for the drivers on the CD..mine for Airlink was rt2870..this works in the 64 bit hardy and the 32..for I am posting this wireless..

---

### Post by roelpeeters on 2008-05-19
Hi!

I installed Hardy yesterday on my laptop, which uses a DWL-630 PCMCIA wireless card. The chipset in use is RT61. I followed the following tutorial even though it says its for gutsy(you may want to change something for the security I am using WPA at home).

[http://www.ushills.co.uk/2008/01/rt61-wireless-card-in-gutsy.html](http://www.ushills.co.uk/2008/01/rt61-wireless-card-in-gutsy.html)

HTH

---

### Post by Nathanp39 on 2008-05-19
I had a similar problem with the Airlink 101 AWLC3025 and installing the NDISWrapper drivers fixed the problem.

I was able to see wireless networks, but I couldn't connect to them.
I tried Wifi-Radar and WICD, but no luck.

Found this thread and tried it.  Worked perfect.

Thanks,
Nathan

---

### Post by ciamele on 2008-05-19
Thanks for all the responses!

I tried CowboyDave's approach, but unfortunately, it did not work.

I'm in the process of doing it roelpeeter's way. but I've hit a snag. When I try to restart networking, I get the following message:

>  * Reconfiguring network interfaces...
wlan0: ERROR while getting interface flags: No such device
Failed to bring up wlan0.


I have noticed that the network icon has disappeared from the top taskbar. I'm not sure if that means anything.

Here's my interfaces file:

> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
#
# The loopback network interface
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
pre-up ifconfig wlan0 up
pre-up iwpriv wlan0 set AuthMode=WPAPSK
pre-up iwpriv wlan0 set EncrypType=TKIP
pre-up iwpriv wlan0 set NetworkType=Managed
pre-up iwconfig wlan0 essid XXXXXXX
pre-up iwpriv wlan0 set WPAPSK="XXXXXXXXXXXXXXXXXXXXXXXXX"

Should I remove the quotations from my WPAPSK code?

I'm also wondering if the EncrypType is the problem. My router doesn't specify the type of encryption as TKIP (or another), though I have set it up for WPA-PSK to get this working. I have a Netgear WGT624.

I'm not broadcasting my SSID. I turned it on and attempted to restart networking, but I had no luck. I've turned the broadcast off.

I have Ndiswrapper installed from a previous attempt to get this working. Should I uninstall it?

Any other ideas?

Thanks again for everyone's help!

---

### Post by roelpeeters on 2008-05-22
Hi,

Could you run iwconfig from the command line to see what interfaces are available to you? It seems as if wlan0 doesn't exist. Also after launching the **sudo modprobe rt61** command, try to look at the messages using **dmesg** if there is any output from the loading of the driver.

HTH

---

### Post by ciamele on 2008-05-23
It works! Thanks to everyone that tried to help! Here are the details:

It turned out I had to change my interface to wlan1. Now it connects, and so far, is working great. I am happy with the way things are, though I admit it would be nice if I could see the signal strength or some kind of network icon in my taskbar again. Frankly,  it's more important to me that it works, so I can live with it as is.

For those of you that need help, Roelpeeters' post (4th on this thread) has a link that did the trick for me. I changed the interfaces file a little bit (just the order of the lines), but I'm not 100% sure it made a difference. Here's my interfaces file:

> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback


auto wlan1
iface wlan1 inet dhcp
pre-up ifconfig wlan1 up
pre-up iwconfig wlan1 essid XXXXXX
pre-up iwpriv wlan1 set NetworkType=Managed
pre-up iwpriv wlan1 set AuthMode=WPAPSK
pre-up iwpriv wlan1 set EncrypType=TKIP
pre-up iwpriv wlan1 set WPAPSK="XXXXXXXXXXX"


Thanks again, everyone!

---

### Post by lswb on 2008-05-25
"it would be nice if I could see the signal strength or some kind of network icon in my taskbar"

There is a gnome panel applet for this but you can install a better on called netspeed from the regular repositories. The standard applet just shows 2 screens and indicates if there is or is not a working connection. The netspeed applet will show download & upload rates and use a different icon for the type of connection, e.g a telephone for ppp, a network card for wired, etc.

---

### Post by ciamele on 2008-05-25
Thanks for the tip. I checked out netspeed, but it isn't quite what I'm looking for. But I stumbled onto my own mistake. I overlooked adding the network icon to the top panel. Now I have a signal strength indicator. Thanks!

---

### Post by xavierbutt on 2008-06-05
Be wary of the Netgear WGT624 (V2) router. Me Pa owns one and the whole router crashes when upgrading with apt-get. There are two router settings, both enabled by default, that could cause this crash: 1) 108 Mbps, 2) range extender. Disable them both if you have this issue.

---

### Post by ciamele on 2008-06-06
> **xavierbutt said:**
> Be wary of the Netgear WGT624 (V2) router. Me Pa owns one and the whole router crashes when upgrading with apt-get. There are two router settings, both enabled by default, that could cause this crash: 1) 108 Mbps, 2) range extender. Disable them both if you have this issue.

I have not experienced this issue despite have both options enabled. But thank you for the warning, this could save me trouble in the future if it does begin to happen.

---

