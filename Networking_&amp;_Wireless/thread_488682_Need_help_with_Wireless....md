---
title: "Need help with Wireless..."
date: 2007-06-30
forum: Networking &amp; Wireless
---

### Post by shamushand on 2007-06-30
Hey all, I'm having a little... OK, a lot of trouble getting my wireless going on my desktop PC. I don't know the first thing about wireless in Linux, and I need help getting started. Every guide I find on the internet requires a fairly large knowledge of Linux (or that you've done things between the lines), which I don't have. I've tried ndiswrapper and native Linux drivers, but when I type in "lspci" I get: 

```
01:0e.0 Network controller: Unknown device 0814:0201 (rev 01)
```

When I go to 'System -> Administration -> Networking', I just see a regular networking device (which doesn't work). When I type in 'ndiswrapper -l', it looks like ndiswrapper doesn't recognize my card. When I type in 'iwlist wlan0 scan' I get:

```
wlan0  Interface doesn't support scanning
```

And worst of all, I can't tell which chipset my card is. All I know is that it's a WMP45G card, I don't know if it's V2 or V4, I don't know. I really need to get this set up, but first I have to get on my feet. Any help? :(

---

### Post by kevdog on 2007-06-30
Thats really troubling about your card, even lspci will not recognize it!!

This is a PCI or PCMCIA card.

At this point, you might want to start over, meaning dont reinstall Ubuntu, just uninstall ndiswrapper or reverse the steps you did trying to fix things

Likely
sudo modprobe -r ndiswrapper
sudo rm -R /etc/ndiswrapper/*

And then use Synaptic or whatever you did to uninstall ndiswrapper.

Try rebooting and then lspci.  If not try:
lshw -C network

The first goal is to have the operating system at least recognize you have a card "plugged in".  We'll worry about driver/ndiswrapper installation either.  If the OS cant recognize the card, then I think we are stuck.

Im also assuming this is not a USB wireless device -- correct??

---

### Post by shamushand on 2007-06-30
It's a PCI card, I guess I'll start over like you said.

---

### Post by shamushand on 2007-06-30
I did everything you said, but when I type in 'lshw -C network' I get:

```
*-network UNCLAIMED
 description: Network controller
 physical id: e
 bus info: pci@01:0e.0
 version: 01
 width: 32 bits
 clock: 33Mhz
 capabilities: bus_master cap_list
 resources: iomemory:f4112000-f4113fff  irq:255
```

I'm guessing this is bad, because when I type in "lspci" I get:

```
01:0e.0 Network controller: Unknown device 0814:0201 (rev 01)
```

Help me.... :(

---

### Post by shamushand on 2007-06-30
After much fiddling around, I'm getting nowhere. Could it be hardware failure? :(

---

### Post by shamushand on 2007-06-30
Bump!

---

### Post by kevdog on 2007-06-30
If the hardware cannot be recognized then there is obviously a problem.  May want to try a new wireless card.  One thing you may want to check is the message logs.  Type 
dmesg | more
at command line.  Take a look through it,  it may be long, but it may indicate some error somewhere.  Im not exactly sure what to tell you to look for, other than sometype of hardware or  socket error

---

### Post by shamushand on 2007-06-30
I typed in 'dmesg | more' and I got: 

```
[17179569.184000] Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 
4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35
 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e7000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000000fef0000 (usable)
[17179569.184000]  BIOS-e820: 000000000fef0000 - 000000000feffc00 (ACPI data)
[17179569.184000]  BIOS-e820: 000000000feffc00 - 000000000ff00000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000000ff00000 - 0000000010000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 254MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 65264
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 61168 pages, LIFO batch:15
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x0
00f6850
[17179569.184000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @
 0x0fefadc3
[17179569.184000] ACPI: FADT (v001 INTEL  Whitney  0x06040000 PTL  0x000f4240) @
 0x0feffb8c
[17179569.184000] ACPI: DSDT (v001  INTEL  Whitney 0x06040000 MSFT 0x01000007) @
 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179569.184000] Allocating PCI resources starting at 20000000 (gap: 10000000:e
ff00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable 
it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (0120a000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[17179569.184000] Detected 531.764 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179572.668000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes
)
[17179572.668000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[17179572.704000] Memory: 249192k/261056k available (1910k kernel code, 11288k r
eserved, 1070k data, 308k init, 0k highmem)
[17179572.704000] Checking if this processor honours the WP bit even in supervis
or mode... Ok.
[17179572.784000] Calibrating delay using timer specific routine.. 1064.91 BogoM
IPS (lpj=2129838)
[17179572.784000] Security Framework v1.0.0 initialized
[17179572.784000] SELinux:  Disabled at boot.
[17179572.784000] Mount-cache hash table entries: 512
[17179572.784000] CPU: After generic identify, caps: 0183f9ff 00000000 00000000 
00000000 00000000 00000000 00000000
[17179572.784000] CPU: After vendor identify, caps: 0183f9ff 00000000 00000000 0
0000000 00000000 00000000 00000000
[17179572.784000] CPU: L1 I cache: 16K, L1 D cache: 16K
[17179572.784000] CPU: L2 cache: 128K
[17179572.784000] CPU: After all inits, caps: 0183f9ff 00000000 00000000 0000004
0 00000000 00000000 00000000
[17179572.784000] Checking 'hlt' instruction... OK.
[17179572.800000] SMP alternatives: switching to UP code
[17179572.800000] Freeing SMP alternatives: 16k freed
[17179572.800000] checking if image is initramfs... it is
[17179574.612000] Freeing initrd memory: 5254k freed
[17179574.616000] ACPI: Core revision 20060707
[17179574.616000] ACPI: Looking for DSDT ... not found!
[17179574.620000] ACPI: setting ELCR to 0200 (from 0e00)
[17179574.620000] CPU0: Intel Celeron (Mendocino) stepping 05
[17179574.620000] SMP motherboard not detected.
[17179574.620000] Local APIC not detected. Using dummy APIC emulation.
[17179574.624000] Brought up 1 CPUs
[17179574.624000] migration_cost=0
[17179574.624000] NET: Registered protocol family 16
[17179574.624000] EISA bus registered
[17179574.624000] ACPI: bus type pci registered
[17179574.624000] PCI: PCI BIOS revision 2.10 entry at 0xfd9b0, last bus=1
[17179574.624000] PCI: Using configuration type 1
[17179574.624000] Setting up standard PCI resources
[17179574.652000] ACPI: Interpreter enabled
[17179574.652000] ACPI: Using PIC for interrupt routing
[17179574.652000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179574.652000] PCI: Probing PCI hardware (bus 00)
[17179574.656000] Boot video device is 0000:00:01.0
[17179574.656000] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[17179574.656000] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
[17179574.656000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179574.656000] PCI: Transparent bridge - 0000:00:1e.0
[17179574.656000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179574.664000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 *10 11 12 14 1
5)
[17179574.664000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *9 10 11 12 14 1
5)
[17179574.664000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 11 12 14 15
) *0, disabled.
[17179574.668000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12 14 1
5)
[17179574.668000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB_._PRT]
[17179574.672000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179574.672000] pnp: PnP ACPI init
[17179574.696000] pnp: PnP ACPI: found 11 devices
[17179574.696000] PnPBIOS: Disabled by ACPI PNP
[17179574.700000] PCI: Using ACPI for IRQ routing
[17179574.700000] PCI: If a device doesn't work, try "pci=routeirq".  If it help
s, post a report
[17179574.704000] PCI: Ignore bogus resource 6 [0:0] of 0000:00:01.0
[17179574.704000] PCI: Bridge: 0000:00:1e.0
[17179574.704000]   IO window: disabled.
[17179574.704000]   MEM window: f4100000-f41fffff
[17179574.704000]   PREFETCH window: disabled.
[17179574.704000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179574.704000] NET: Registered protocol family 2
[17179574.744000] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[17179574.744000] TCP established hash table entries: 8192 (order: 4, 65536 byte
s)
[17179574.744000] TCP bind hash table entries: 4096 (order: 3, 32768 bytes)
[17179574.744000] TCP: Hash tables configured (established 8192 bind 4096)
[17179574.744000] TCP reno registered
[17179574.748000] audit: initializing netlink socket (disabled)
[17179574.748000] audit(1183217009.748:1): initialized
[17179574.748000] VFS: Disk quotas dquot_6.5.1
[17179574.748000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179574.748000] Initializing Cryptographic API
[17179574.748000] io scheduler noop registered
[17179574.748000] io scheduler anticipatory registered
[17179574.748000] io scheduler deadline registered
[17179574.748000] io scheduler cfq registered (default)
[17179574.748000] isapnp: Scanning for PnP cards...
[17179575.104000] isapnp: No Plug & Play device found
[17179575.300000] Real Time Clock Driver v1.12ac
[17179575.300000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ shari
ng enabled
[17179575.352000] pnp: Device 00:08 activated.
[17179575.352000] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179575.352000] mice: PS/2 mouse device common for all mice
[17179575.356000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 b
locksize
[17179575.356000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179575.356000] ide: Assuming 33MHz system bus speed for PIO modes; override w
ith idebus=xx
[17179575.356000] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 
irq 1,12
[17179575.360000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179575.360000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179575.360000] EISA: Probing bus 0 at eisa.0
[17179575.360000] Cannot allocate resource for EISA slot 1
[17179575.360000] EISA: Detected 0 cards.
[17179575.360000] TCP bic registered
[17179575.360000] NET: Registered protocol family 1
[17179575.360000] NET: Registered protocol family 8
[17179575.360000] NET: Registered protocol family 20
[17179575.360000] Using IPI No-Shortcut mode
[17179575.360000] ACPI: (supports S0 S1 S5)
[17179575.364000] Freeing unused kernel memory: 308k freed
[17179576.772000] Capability LSM initialized
[17179576.956000] ACPI: Invalid PBLK length [5]
[17179579.056000] ICH: IDE controller at PCI slot 0000:00:1f.1
[17179579.056000] ICH: chipset revision 2
[17179579.056000] ICH: not 100% native mode: will probe irqs later
[17179579.056000]     ide0: BM-DMA at 0x1800-0x1807, BIOS settings: hda:DMA, hdb:pio
[17179579.056000]     ide1: BM-DMA at 0x1808-0x180f, BIOS settings: hdc:DMA, hdd:pio
[17179579.056000] Probing IDE interface ide0...
[17179579.344000] hda: ST315323A, ATA DISK drive
[17179580.016000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179580.016000] Probing IDE interface ide1...
[17179580.752000] hdc: SAMSUNG CD-ROM SC-148C, ATAPI CD/DVD-ROM drive
[17179581.088000] hdc: Disabling (U)DMA for SAMSUNG CD-ROM SC-148C (blacklisted)
[17179581.088000] ide1 at 0x170-0x177,0x376 on irq 15
[17179581.116000] hda: max request size: 128KiB
[17179581.156000] hda: 30008475 sectors (15364 MB) w/512KiB Cache, CHS=29770/16/63, UDMA(33)
[17179581.156000] hda: cache flushes not supported
[17179581.160000]  hda: hda1 hda2 < hda5 >
[17179581.296000] hdc: ATAPI 48X CD-ROM drive, 128kB Cache
[17179581.296000] Uniform CD-ROM driver Revision: 3.20
[17179581.804000] usbcore: registered new driver usbfs
[17179581.808000] usbcore: registered new driver hub
[17179581.816000] USB Universal Host Controller Interface driver v3.0
[17179581.816000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[17179581.816000] PCI: setting IRQ 11 as level-triggered
[17179581.816000] ACPI: PCI Interrupt 0000:00:1f.2[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179581.816000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[17179581.816000] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[17179581.816000] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[17179581.816000] uhci_hcd 0000:00:1f.2: irq 11, io base 0x00001820
[17179581.816000] usb usb1: configuration #1 chosen from 1 choice
[17179581.820000] hub 1-0:1.0: USB hub found
[17179581.820000] hub 1-0:1.0: 2 ports detected
[17179582.088000] Attempting manual resume
[17179582.144000] EXT3-fs: INFO: recovery required on readonly filesystem.
[17179582.144000] EXT3-fs: write access will be enabled during recovery.
[17179582.164000] usb 1-1: new low speed USB device using uhci_hcd and address 2
[17179582.336000] usb 1-1: configuration #1 chosen from 1 choice
[17179582.580000] usb 1-2: new full speed USB device using uhci_hcd and address 3
[17179582.744000] usb 1-2: configuration #1 chosen from 1 choice
[17179582.768000] usbcore: registered new driver hiddev
[17179582.788000] input: DELL DELL USB Keyboard as /class/input/input0
[17179582.788000] input: USB HID v1.10 Keyboard [DELL DELL USB Keyboard] on usb-0000:00:1f.2-1
[17179582.788000] usbcore: registered new driver usbhid
[17179582.788000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179582.820000] usbcore: registered new driver libusual
[17179582.872000] SCSI subsystem initialized
[17179582.884000] Initializing USB Mass Storage driver...
[17179582.884000] scsi0 : SCSI emulation for USB Mass Storage devices
[17179582.884000] usbcore: registered new driver usb-storage
[17179582.884000] USB Mass Storage support registered.
[17179582.884000] usb-storage: device found at 3
[17179582.884000] usb-storage: waiting for device to settle before scanning
[17179585.640000] kjournald starting.  Commit interval 5 seconds
[17179585.640000] EXT3-fs: recovery complete.
[17179585.644000] EXT3-fs: mounted filesystem with ordered data mode.
[17179587.884000] usb-storage: device scan complete
[17179587.888000]   Vendor: SanDisk   Model: U3 Cruzer Micro   Rev: 2.18
[17179587.888000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[17179587.888000]   Vendor: SanDisk   Model: U3 Cruzer Micro   Rev: 2.18
[17179587.888000]   Type:   CD-ROM                             ANSI SCSI revision: 02
[17179602.104000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179602.188000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179602.404000] hw_random hardware driver 1.0.0 loaded
[17179602.436000] input: PC Speaker as /class/input/input1
[17179603.164000] Linux agpgart interface v0.101 (c) Dave Jones
[17179603.204000] agpgart: Detected an Intel i810 Chipset.
[17179603.220000] agpgart: AGP aperture is 64M @ 0xf8000000
[17179603.396000] i810_smbus 0000:00:01.0: i810/i815 i2c device found.
[17179604.640000] Floppy drive(s): fd0 is 1.44M
[17179604.656000] FDC 0 is a post-1991 82077
[17179605.308000] input: ImPS/2 Logitech Wheel Mouse as /class/input/input2
[17179605.416000] pnp: Device 00:0a activated.
[17179605.416000] parport: PnPBIOS parport detected.
[17179605.416000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[17179605.788000] SCSI device sda: 990865 512-byte hdwr sectors (507 MB)
[17179605.800000] sda: Write Protect is off
[17179605.800000] sda: Mode Sense: 03 00 00 00
[17179605.800000] sda: assuming drive cache: write through
[17179605.816000] SCSI device sda: 990865 512-byte hdwr sectors (507 MB)
[17179605.828000] sda: Write Protect is off
[17179605.828000] sda: Mode Sense: 03 00 00 00
[17179605.828000] sda: assuming drive cache: write through
[17179605.828000]  sda: sda1
[17179605.868000] sd 0:0:0:0: Attached scsi removable disk sda
[17179606.096000] sr0: scsi3-mmc drive: 8x/40x writer xa/form2 cdda tray
[17179606.096000] sr 0:0:0:1: Attached scsi CD-ROM sr0
[17179606.248000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179606.248000] sr 0:0:0:1: Attached scsi generic sg1 type 5
[17179606.812000] ts: Compaq touchscreen protocol output
[17179607.200000] PCI: Enabling device 0000:01:09.0 (0004 -> 0006)
[17179607.200000] ACPI: PCI Interrupt 0000:01:09.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179607.756000] gameport: CS4281 Gameport is pci0000:01:09.0/gameport0, speed 1420kHz
[17179608.324000] lp0: using parport0 (interrupt-driven).
[17179608.464000] Adding 642560k swap on /dev/disk/by-uuid/82486f3c-9767-44d2-b153-b75a13dd0670.  Priority:-1 extents:1 acros
s:642560k
[17179608.612000] EXT3 FS on hda1, internal journal
[17179612.800000] ACPI: Power Button (FF) [PWRF]
[17179612.800000] ACPI: Power Button (CM) [PWRB]
[17179613.228000] ibm_acpi: ec object not found
[17179613.320000] pcc_acpi: loading...
[17179622.804000] [drm] Initialized drm 1.0.1 20051102
[17179622.912000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
[17179622.912000] PCI: setting IRQ 10 as level-triggered
[17179622.912000] ACPI: PCI Interrupt 0000:00:01.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[17179622.920000] [drm] Initialized i810 1.4.0 20030605 on minor 0
[17179622.924000] mtrr: base(0xf8000000) is not aligned on a size(0x180000) boundary
[17179622.948000] [drm] Using v1.4 init.
[17179623.464000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179623.464000] apm: overridden by ACPI.
[17179633.584000] cdrom: This disc doesn't have any tracks I recognize!
[17179636.264000] Bluetooth: Core ver 2.8
[17179636.264000] NET: Registered protocol family 31
[17179636.264000] Bluetooth: HCI device and connection manager initialized
[17179636.264000] Bluetooth: HCI socket layer initialized
[17179636.360000] Bluetooth: L2CAP ver 2.8
[17179636.360000] Bluetooth: L2CAP socket layer initialized
[17179636.384000] Bluetooth: RFCOMM socket layer initialized
[17179636.384000] Bluetooth: RFCOMM TTY layer initialized
[17179636.384000] Bluetooth: RFCOMM ver 1.7
[17179646.204000] NET: Registered protocol family 10
[17179646.204000] lo: Disabled Privacy Extensions
[17179646.204000] IPv6 over IPv4 tunneling driver
[17179653.780000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17179653.856000] ISOFS: changing to secondary root
[17179655.200000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17180606.308000] usb 1-2: USB disconnect, address 3
[17180653.924000] usb 1-2: new full speed USB device using uhci_hcd and address 4
[17180654.088000] usb 1-2: configuration #1 chosen from 1 choice
[17180654.092000] scsi1 : SCSI emulation for USB Mass Storage devices
[17180654.092000] usb-storage: device found at 4
[17180654.092000] usb-storage: waiting for device to settle before scanning
[17180659.092000] usb-storage: device scan complete
[17180659.096000]   Vendor: SanDisk   Model: U3 Cruzer Micro   Rev: 2.18
[17180659.096000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[17180659.096000]   Vendor: SanDisk   Model: U3 Cruzer Micro   Rev: 2.18
[17180659.096000]   Type:   CD-ROM                             ANSI SCSI revision: 02
[17180659.108000] SCSI device sda: 990865 512-byte hdwr sectors (507 MB)
[17180659.108000] sda: Write Protect is off
[17180659.108000] sda: Mode Sense: 03 00 00 00
[17180659.108000] sda: assuming drive cache: write through
[17180659.120000] SCSI device sda: 990865 512-byte hdwr sectors (507 MB)
[17180659.124000] sda: Write Protect is off
[17180659.124000] sda: Mode Sense: 03 00 00 00
[17180659.124000] sda: assuming drive cache: write through
[17180659.124000]  sda: sda1
[17180659.136000] sd 1:0:0:0: Attached scsi removable disk sda
[17180659.136000] sd 1:0:0:0: Attached scsi generic sg0 type 0
[17180659.164000] sr0: scsi3-mmc drive: 8x/40x writer xa/form2 cdda tray
[17180659.164000] sr 1:0:0:1: Attached scsi CD-ROM sr0
[17180659.164000] sr 1:0:0:1: Attached scsi generic sg1 type 5
[17180662.836000] cdrom: This disc doesn't have any tracks I recognize!
[17180664.452000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17180718.444000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17180718.520000] ISO 9660 Extensions: RRIP_1991A
```

Absolutely no ideas what this means... :(

---

### Post by kevdog on 2007-06-30
Was the card plugged-in when you booted computer??

If not reboot computer with card in the drive or slot and then take a look at dmesg again.  Also is card detected at all when you issue command
lshw

I think you might have a "dead card" or "dead slot"

---

### Post by shamushand on 2007-06-30
I think it might be dead slot, because I was given the computer with a card already in that slot, and the installer didn't detect it. And for some reason, all other slots are welded shut from the outside of the chassis. Any suggestions?

---

### Post by chris.zeman on 2007-06-30
Who in the hell welds expansion slots shut? lol

Unless you have some way to open another slot, I'd either invest in a card you KNOW is Linux compatible or buy a new case.

Chris

---

### Post by shamushand on 2007-06-30
Well, I guess eMachines does. ;)

I tested a sound card on the slot, worked with a few kinks. 
Right now I'll test the card on my Windows machine... :(

---

### Post by shamushand on 2007-06-30
The very typing of these words is a great relief to me, as I am typing from my Windows machine using the card. [-o< Also, after much analyzing the card, I realized it was V4. Tomorrow I'll try to reinstall Ubuntu Edgy while the card is installed. As long as everything works, I will consistently try to get it working, as I haven't seen as much as one person who said "I just didn't work" about this card. Even if it takes two weeks, I will make this card work on Ubuntu, no matter what! :p

Wish me luck, any suggestions highly appreciated. ;)

---

