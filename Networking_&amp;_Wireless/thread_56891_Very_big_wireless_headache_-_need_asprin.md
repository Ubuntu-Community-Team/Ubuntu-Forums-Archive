---
title: "Very big wireless headache - need asprin"
date: 2005-08-14
forum: Networking &amp; Wireless
---

### Post by numberexhaust on 2005-08-14
Hey guys, thanks in advance for any help.  Let me tell you what my situation here is.

Background:
I'm a high school student who was issued a standard school laptop (I would've bought my own, but this came with support on campus, which was appealing to my dad).  It's a Dell Inspiron 1100 (one of the blue ones) with virtually no upgrades.  My computer ran so slow, I decided to jump into linux to make it better.  Over the summer I've been playing around with various distros, inlcuding Mandriva, Fedora Core 4, SuSE, PClinuxOS, FreeBSD (yes, I know), Gentoo, and Ubuntu.  I've tried EVERYTHING on most of the distros (my linux-accute friend helped me over instant messenger, and was thoroughly stumped (he ran the same card I have on a similar dell and it worked fine).  The reason why wireless is so important to me is because if I'm going to take this laptop to school, I need it to work anywhere, since there is usually no hardwire connection available, and everyone else works wirelessly.

Hardware:
OK, i'm running a Proxim Agere Orinoco wireless PC card, 802.11b Silver edition, which can be found here:
[http://www.proxim.com/products/wifi/client/11bpccard/index.html](http://www.proxim.com/products/wifi/client/11bpccard/index.html) -- except mine's the silver, not gold.

My laptop is a Dell Inspiron 1100, with a TI something CardBus controller. (I can find it if you need it).

Ifconfig and iwconfig:
Here are the outputs for ifconfig and iwconfig on my box, while i'm running hardwired.
> asonawalla@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0D:56:B5:2C:9E
          inet addr:192.168.0.50  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:56ff:feb5:2c9e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5544 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3726 errors:0 dropped:0 overruns:0 carrier:0
          collisions:940 txqueuelen:1000
          RX bytes:5642131 (5.3 MiB)  TX bytes:412754 (403.0 KiB)
          Interrupt:7

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:13683 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13683 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1041341 (1016.9 KiB)  TX bytes:1041341 (1016.9 KiB)

asonawalla@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

asonawalla@ubuntu:~$ 

Since this is the first time I'm trying wireless on Debian/Ubuntu, I would be willing to try ANYTHING.  Any help is worth it's weight in gold to me.

---

### Post by az on 2005-08-14
What is the problem?

Is it that your card is not detected?  Look to see if pcmcia-cs is installed and install it if it is not.

Insert the card and wait a few moments and then type
dmesg

and post the last few dozen lines to see what happens when you plug in the card for the first time.  An orinocco card hould have the drivers automatically loaded by hotplug.  They are already in the kernel.

Also, post the output of 

lsmod

afterwards.


If you cannot configure your card, go into System-Administration-Networking and configure your wireless netowrk settings there.  Pick DHCP and put in your WEP if you have one.

---

### Post by numberexhaust on 2005-08-14
1. pcmcia-cs is and was installed (by default, i never installed it)

2. here is the entire output of dmesg:

> asonawalla@ubuntu:~$ dmesg
(reserved)
 BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
638MB LOWMEM available.
On node 0 totalpages: 163529
  DMA zone: 4096 pages, LIFO batch:1
  Normal zone: 159433 pages, LIFO batch:16
  HighMem zone: 0 pages, LIFO batch:1
DMI 2.3 present.
ACPI: RSDP (v000 DELL                                  ) @ 0x000fdf00
ACPI: RSDT (v001 DELL    CPi R   0x27d40a12 ASL  0x00000061) @ 0x27ef0000
ACPI: FADT (v001 DELL    CPi R   0x27d40a12 ASL  0x00000061) @ 0x27ef0400
ACPI: DSDT (v001 INT430 SYSFexxx 0x00001001 MSFT 0x0100000e) @ 0x00000000
ACPI: PM-Timer IO Port: 0x808
Built 1 zonelists
Kernel command line: root=/dev/hdc6 ro quiet splash
Local APIC disabled by BIOS -- you can enable it with "lapic"
mapped APIC to ffffd000 (01506000)
Initializing CPU#0
PID hash table entries: 4096 (order: 12, 65536 bytes)
Detected 2193.011 MHz processor.
Using pmtmr for high-res timesource
Console: colour VGA+ 80x25
Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Memory: 640668k/654116k available (1436k kernel code, 12868k reserved, 754k data, 224k init, 0k highmem)
Checking if this processor honours the WP bit even in supervisor mode... Ok.
Calibrating delay loop... 4341.76 BogoMIPS (lpj=2170880)
Security Framework v1.0.0 initialized
SELinux:  Disabled at boot.
Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
CPU: After generic identify, caps: bfebf9ff 00000000 00000000 00000000 00004400 00000000
CPU: After vendor identify, caps: bfebf9ff 00000000 00000000 00000000 00004400 00000000
CPU: Trace cache: 12K uops, L1 D cache: 8K
CPU: L2 cache: 512K
CPU: After all inits, caps: bfebf9ff 00000000 00000000 00000080 00004400 00000000
CPU: Intel(R) Pentium(R) 4 CPU 2.20GHz stepping 09
Enabling fast FPU save and restore... done.
Enabling unmasked SIMD FPU exception support... done.
Checking 'hlt' instruction... OK.
Checking for popad bug... OK.
ACPI: Looking for DSDT in initrd... not found!
ACPI: setting ELCR to 0200 (from 0800)
checking if image is initramfs...it isn't (bad gzip magic numbers); looks like an initrd
Freeing initrd memory: 4248k freed
NET: Registered protocol family 16
EISA bus registered
PCI: PCI BIOS revision 2.10 entry at 0xfcfae, last bus=2
PCI: Using configuration type 1
mtrr: v2.0 (20020519)
ACPI: Subsystem revision 20050211
ACPI: Interpreter enabled
ACPI: Using PIC for interrupt routing
ACPI: PCI Root Bridge [PCI0] (00:00)
PCI: Probing PCI hardware (bus 00)
PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
PCI: Transparent bridge - 0000:00:1e.0
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *11
ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 *11)
ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 *11)
ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
pnp: PnP ACPI: found 11 devices
PnPBIOS: Disabled by ACPI PNP
PCI: Using ACPI for IRQ routing
** PCI interrupts are no longer routed automatically.  If this
** causes a device to stop working, it is probably because the
** driver failed to call pci_enable_device().  As a temporary
** workaround, the "pci=routeirq" argument restores the old
** behavior.  If this argument makes the device work again,
** please email the output of "lspci" to [email]bjorn.helgaas@hp.com[/email]
** so I can fix the driver.
pnp: 00:01: ioport range 0x4d0-0x4d1 has been reserved
pnp: 00:01: ioport range 0x800-0x805 could not be reserved
pnp: 00:01: ioport range 0x808-0x80f could not be reserved
pnp: 00:02: ioport range 0xf400-0xf4fe has been reserved
pnp: 00:02: ioport range 0x806-0x807 has been reserved
pnp: 00:02: ioport range 0x810-0x85f could not be reserved
pnp: 00:02: ioport range 0x860-0x87f has been reserved
pnp: 00:02: ioport range 0x880-0x8bf has been reserved
pnp: 00:02: ioport range 0x8c0-0x8df has been reserved
pnp: 00:07: ioport range 0x900-0x97f has been reserved
pnp: 00:0a: ioport range 0x7b0-0x7bb has been reserved
pnp: 00:0a: ioport range 0x7c0-0x7df has been reserved
pnp: 00:0a: ioport range 0xbb0-0xbbb has been reserved
pnp: 00:0a: ioport range 0xbc0-0xbdf has been reserved
pnp: 00:0a: ioport range 0xfb0-0xfbb has been reserved
pnp: 00:0a: ioport range 0xfc0-0xfdf has been reserved
pnp: 00:0a: ioport range 0x13b0-0x13bb has been reserved
pnp: 00:0a: ioport range 0x13c0-0x13df has been reserved
audit: initializing netlink socket (disabled)
audit(1124024828.182:0): initialized
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0
Initializing Cryptographic API
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
i8042.c: Warning: Keylock active.
serio: i8042 AUX port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 7
PCI: setting IRQ 7 as level-triggered
ACPI: PCI interrupt 0000:00:1f.6[B] -> GSI 7 (level, low) -> IRQ 7
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered
RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
input: AT Translated Set 2 keyboard on isa0060/serio0
EISA: Probing bus 0 at eisa0
EISA: Detected 0 cards.
NET: Registered protocol family 2
IP: routing cache hash table of 8192 buckets, 64Kbytes
TCP: Hash tables configured (established 262144 bind 65536)
NET: Registered protocol family 8
NET: Registered protocol family 20
Restarting tasks...<6> Strange, kswapd0 not stopped
 Strange, kseriod not stopped
 done
ACPI wakeup devices:
 LID PBTN PCI0 USB0 USB1 USB2 USB3 MODM PCIE
ACPI: (supports S0 S1 S3 S4 S4bios S5)
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4248KiB [1 disk] into ram disk... done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 224k freed
ACPI: Processor [CPU0] (supports 8 throttling states)
ACPI: Thermal Zone [THM] (34 C)
NET: Registered protocol family 1
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
ICH4: IDE controller at PCI slot 0000:00:1f.1
PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
PCI: setting IRQ 11 as level-triggered
ACPI: PCI interrupt 0000:00:1f.1[A] -> GSI 11 (level, low) -> IRQ 11
ICH4: chipset revision 2
ICH4: not 100% native mode: will probe irqs later
    ide0: BM-DMA at 0xbfa0-0xbfa7, BIOS settings: hda:DMA, hdb:pio
    ide1: BM-DMA at 0xbfa8-0xbfaf, BIOS settings: hdc:DMA, hdd:pio
Probing IDE interface ide0...
hda: MATSHITA CD-RW UJDA360, ATAPI CD/DVD-ROM drive
elevator: using anticipatory as default io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Probing IDE interface ide1...
hdc: IC25N030ATMR04-0, ATA DISK drive
ide1 at 0x170-0x177,0x376 on irq 15
hdc: max request size: 1024KiB
hdc: 58605120 sectors (30005 MB) w/1740KiB Cache, CHS=16383/255/63, UDMA(100)
hdc: cache flushes supported
 /dev/ide/host0/bus1/target0/lun0: p1 p2 < p5 p6 >
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
Stopping tasks: ==|
Freeing memory... done (455 pages freed)
Restarting tasks... done
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
Adding 1052216k swap on /dev/hdc5.  Priority:-1 extents:1
EXT3 FS on hdc6, internal journal
hda: ATAPI 24X CD-ROM CD-R/RW drive, 2048kB Cache
Uniform CD-ROM driver Revision: 3.20
lp: driver loaded but no devices found
mice: PS/2 mouse device common for all mice
Synaptics Touchpad, model: 1
 Firmware: 5.9
 Sensor: 37
 new absolute packet format
 Touchpad has extended capability bits
 -> multifinger detection
 -> palm detection
input: SynPS/2 Synaptics TouchPad on isa0060/serio1
Capability LSM initialized
ts: Compaq touchscreen protocol output
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: [email]dm-devel@redhat.com[/email]
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
cdrom: open failed.
Real Time Clock Driver v1.12
input: PC Speaker
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected an Intel 845G Chipset.
agpgart: Maximum main memory to use for agp memory: 563M
agpgart: Detected 892K stolen memory.
agpgart: AGP aperture is 128M @ 0xe0000000
usbcore: registered new driver usbfs
usbcore: registered new driver hub
USB Universal Host Controller Interface driver v2.2
ACPI: PCI interrupt 0000:00:1d.0[A] -> GSI 11 (level, low) -> IRQ 11
uhci_hcd 0000:00:1d.0: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
PCI: Setting latency timer of device 0000:00:1d.0 to 64
uhci_hcd 0000:00:1d.0: irq 11, io base 0xbf80
uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
ACPI: PCI interrupt 0000:00:1d.1[B] -> GSI 11 (level, low) -> IRQ 11
uhci_hcd 0000:00:1d.1: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
PCI: Setting latency timer of device 0000:00:1d.1 to 64
uhci_hcd 0000:00:1d.1: irq 11, io base 0xbf40
uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
ACPI: PCI interrupt 0000:00:1d.2[C] -> GSI 11 (level, low) -> IRQ 11
uhci_hcd 0000:00:1d.2: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
PCI: Setting latency timer of device 0000:00:1d.2 to 64
uhci_hcd 0000:00:1d.2: irq 11, io base 0xbf20
uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 2 ports detected
usb 1-1: new full speed USB device using uhci_hcd and address 2
SCSI subsystem initialized
usb 2-1: new low speed USB device using uhci_hcd and address 2
Initializing USB Mass Storage driver...
ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
ACPI: PCI interrupt 0000:00:1d.7[D] -> GSI 11 (level, low) -> IRQ 11
ehci_hcd 0000:00:1d.7: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller
PCI: Setting latency timer of device 0000:00:1d.7 to 64
ehci_hcd 0000:00:1d.7: irq 11, pci mem 0xf6f7fc00
ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
PCI: cache line size of 128 is not supported by device 0000:00:1d.7
ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 26 Oct 2004
usb 2-1: device descriptor read/all, error -84
usb 1-1: string descriptor 0 read error: -71
usb 1-1: string descriptor 0 read error: -71
usb 1-1: string descriptor 0 read error: -71
scsi0 : SCSI emulation for USB Mass Storage devices
usbcore: registered new driver usb-storage
USB Mass Storage support registered.
usb 1-1: USB disconnect, address 2
usb-storage: device found at 2
usb-storage: waiting for device to settle before scanning
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 6 ports detected
usb 4-1: new high speed USB device using ehci_hcd and address 2
scsi1 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 2
usb-storage: waiting for device to settle before scanning
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
usb 2-1: new low speed USB device using uhci_hcd and address 4
pciehp: acpi_pciehprm:\_SB_.PCI0 evaluate _BBN fail=0x5
pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x5
usbcore: registered new driver hiddev
input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1d.1-1
usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.0:USB HID core driver
hw_random hardware driver 1.0.0 loaded
ACPI: PCI interrupt 0000:00:1f.5[B] -> GSI 7 (level, low) -> IRQ 7
PCI: Setting latency timer of device 0000:00:1f.5 to 64
intel8x0_measure_ac97_clock: measured 49313 usecs
intel8x0: clocking to 48000
b44.c:v0.95 (Aug 3, 2004)
ACPI: PCI interrupt 0000:02:01.0[A] -> GSI 7 (level, low) -> IRQ 7
eth0: Broadcom 4400 10/100BaseT Ethernet 00:0d:56:b5:2c:9e
Linux Kernel Card Services
  options:  [pci] [cardbus] [pm]
PCI: Enabling device 0000:02:04.0 (0000 -> 0002)
ACPI: PCI interrupt 0000:02:04.0[A] -> GSI 11 (level, low) -> IRQ 11
Yenta: CardBus bridge found at 0000:02:04.0 [1028:0149]
Yenta: Using CSCINT to route CSC interrupts to PCI
Yenta: Routing CardBus interrupts to PCI
Yenta TI: socket 0000:02:04.0, mfunc 0x00001002, devctl 0x64
Yenta: ISA IRQ mask 0x0478, PCI irq 11
Socket status: 30000011
b44: eth0: Link is down.
NET: Registered protocol family 17
  Vendor: WDC WD80  Model: 0UE-00HCT0        Rev: 0000
  Type:   Direct-Access                      ANSI SCSI revision: 00
usb-storage: device scan complete
SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
sda: assuming drive cache: write through
SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
sda: assuming drive cache: write through
 /dev/scsi/host1/bus0/target0/lun0: p1
Attached scsi disk sda at scsi1, channel 0, id 0, lun 0
b44: eth0: Link is up at 100 Mbps, half duplex.
b44: eth0: Flow control is off for TX and off for RX.
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02f0500(lo)
IPv6 over IPv4 tunneling driver
ACPI: AC Adapter [AC] (on-line)
ACPI: Battery Slot [BAT0] (battery present)
ACPI: Lid Switch [LID]
ACPI: Power Button (CM) [PBTN]
ACPI: Sleep Button (CM) [SBTN]
ibm_acpi: ec object not found
ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
apm: BIOS not found.
[drm] Initialized drm 1.0.0 20040925
ACPI: PCI interrupt 0000:00:02.0[A] -> GSI 11 (level, low) -> IRQ 11
[drm] Initialized i915 1.2.0 20040405 on minor 0: Intel Corp. 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
mtrr: base(0xe0020000) is not aligned on a size(0x300000) boundary
cs: IO port probe 0x0100-0x04ff: clean.
cs: IO port probe 0x0800-0x08ff: clean.
cs: IO port probe 0x0c00-0x0cff: clean.
cs: IO port probe 0x0a00-0x0aff: clean.
cs: memory probe 0xa0000000-0xa0ffffff: clean.
eth0: no IPv6 routers present
FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
orinoco 0.13e (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
orinoco_cs 0.13e (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
ibm_acpi: ec object not found
asonawalla@ubuntu:~$ 

3. Finally, here is the output of lsmod:

> asonawalla@ubuntu:~$ lsmod
Module                  Size  Used by
orinoco_cs              8968  0
orinoco                38284  1 orinoco_cs
hermes                  7936  2 orinoco_cs,orinoco
nls_utf8                2176  1
nls_cp437               5888  1
vfat                   12928  1
fat                    37792  1 vfat
proc_intf               4100  0
freq_table              4100  0
cpufreq_userspace       4572  0
cpufreq_ondemand        6172  0
cpufreq_powersave       1920  0
pcmcia                 21380  3 orinoco_cs
i915                   18304  1
drm                    59412  2 i915
video                  16260  0
sony_acpi               6280  0
pcc_acpi               11264  0
button                  6800  0
battery                10244  0
container               4608  0
ac                      4996  0
ipv6                  229504  9
sd_mod                 16784  2
af_packet              20744  2
yenta_socket           19584  1
pcmcia_core            53568  3 orinoco_cs,pcmcia,yenta_socket
b44                    20356  0
mii                     4736  1 b44
snd_intel8x0           29984  2
snd_ac97_codec         64608  1 snd_intel8x0
snd_pcm_oss            47652  1
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  3 snd
snd_page_alloc          9604  2 snd_intel8x0,snd_pcm
hw_random               5524  0
usbhid                 29376  0
pci_hotplug            30512  0
ehci_hcd               29444  0
usb_storage            64064  1
scsi_mod              119936  2 sd_mod,usb_storage
uhci_hcd               30224  0
usbcore               107384  5 usbhid,ehci_hcd,usb_storage,uhci_hcd
intel_agp              20636  1
agpgart                31784  3 drm,intel_agp
pcspkr                  3816  0
rtc                    12216  0
md                     43856  0
dm_mod                 53116  1
joydev                  9408  0
tsdev                   7488  0
evdev                   9088  1
capability              5000  0
commoncap               7808  1 capability
psmouse                19336  0
mousedev               11160  1
parport_pc             34372  0
lp                     10792  0
parport                33480  2 parport_pc,lp
ide_cd                 38532  0
cdrom                  36508  1 ide_cd
ext3                  120968  1
jbd                    54168  1 ext3
ide_generic             1664  0
piix                    9988  1
ide_disk               18176  3
ide_core              118988  5 usb_storage,ide_cd,ide_generic,piix,ide_disk
unix                   26164  873
thermal                13576  0
processor              22708  1 thermal
fan                     4612  0
fbcon                  34048  0
font                    8448  1 fbcon
bitblit                 5120  1 fbcon
vesafb                  6948  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3072  1 vesafb
cfbfillrect             3584  1 vesafb
asonawalla@ubuntu:~$ 

Thanks a lot man... btw, I don't think it's talking to the card because the light isn't coming on.  Also, for the record, the card runs fine in Windows (I'm running a dual boot for the moment).

---

### Post by numberexhaust on 2005-08-14
[QUOTE=azz]What is the problem?

Is it that your card is not detected?  Look to see if pcmcia-cs is installed and install it if it is not.

Insert the card and wait a few moments and then type
dmesg

and post the last few dozen lines to see what happens when you plug in the card for the first time.  An orinocco card hould have the drivers automatically loaded by hotplug.  They are already in the kernel.

Also, post the output of 

lsmod

afterwards.


If you cannot configure your card, go into System-Administration-Networking and configure your wireless netowrk settings there.  Pick DHCP and put in your WEP if you have one.[/QUOTE]
 Also, in System-Administration-Networking, I see Modem and Ethernet, but no wireless... I guess that means its not detecting the card (but im not sure).  Very strange.

---

### Post by az on 2005-08-14
The card is detected and the driver is loaded:

orinoco_cs 8968 0
orinoco 38284 1 orinoco_cs
hermes 7936 2 orinoco_cs,orinoco

pcmcia 21380 3 orinoco_cs

yenta_socket 19584 1
pcmcia_core 53568 3 orinoco_cs,pcmcia,yenta_socket


Perhaps your powere management settings are interfering?


ibm_acpi: ec object not found

I do not own this kind of hardware, so I cannot help you more that to suggest you try dissabling acpi or changing the settings....

---

### Post by numberexhaust on 2005-08-14
How exactly do I disable ACPI?

---

### Post by Fed on 2005-08-15
This is a bit of a long-shot, but I had trouble with my Netgear card (Prism54 chipset) and my IBM Thinkpad, and the problem was due to Texas Instruments PCMCIA card slots, and the power they supply (or in my case, I think it was the power they didnt supply).

Back when I went to school, we also used the Orinoco Silver cards, and if I remember correctly, one of the LEDs is Power, and the other is Activity. Point is, if your card's LEDs are both off, it does look a bit like its not getting power. I dont know whether you can get into your Dell's BIOS setup, but thats what I had to do for my Thinkpad (theyve fixed the issue now with newer drivers for my card, but I couldnt help but notice the similarity).

In the Thinkpad BIOS I had to disable "PCI Bus Power Management", which was under the Power options. Since you said you are willing to trying anything, I suppose you could give this a shot.

BTW, the affected TI PCMCIA models were:
TI PCI-1410
TI PCI-1420
TI PCI-1450
TI PCI-1510
...so if thats the same model as yours, you might be in luck.

Again, its a long-shot, so Im sorry if Ive wasted your time, but you never know :)

Edit - Oh yeah, and I had to insert my card after booting once the computer was already in the OS.

---

### Post by numberexhaust on 2005-08-15
Thanks for that Fed... and I think you have the problem identified right (that it's not being powered, I do have a TI 1510), but after a bunch of reboots and playing around with my BIOS (and re-inserting the card when the system was booted) I can't figure out how to disable the pci power management (there is no option close to that in my bios).  If anyone has any idea about that my BIOS is the Dell revision A32.

Here's the latest, though:
This morning I borrowed a friend's Lucent Wavelan card and it worked fine right out of the box.  So I went online to try to see if I could buy one of those from anywhere... couldn't find it a lot (there was one site, but it was like a hundred bucks... don't want to dish that out if I don't have to).

I was looking at the PCMCIA supported cards list from sourceforge and I found one card that was available at a store close to me.  It was the Linksys Instant Wireless WPC11 card (about 50 bucks).  Has anyone ever tested this card, or have anything to say about it at all?  I would hate to go buy it and then realize that it doesn't work.

---

### Post by spartas on 2005-08-15
I have a WPC11 card, but you will want to check which version it is before you buy.  I have version 3.0, however, most cards nowdays are 4.0, which uses a different chipset.  3.0 and below works out of the box, but I think you may need ndiswrapper or something else to get 4.0 working.  You may want to check out this page: [https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards)

If you want to, you can get a WPC11 online for cheaper.  I know Newegg has it for $38 and a $25 rebate to go with it.  Just a note: I am not affiliated with Newegg in any way.

---

### Post by numberexhaust on 2005-08-15
I checked and this is not version 4... here is the exact link:

[http://www.compusa.com/products/product_info.asp?product_code=279434&pfp=BROWSE](http://www.compusa.com/products/product_info.asp?product_code=279434&pfp=BROWSE)

It's a little expensive, but if I'm sure it'll work (and I'm not concerned with a crappy chipset, I'm not doing any heavy-duty wireless work) I'll get it.

Please tell me what you guys think... the more knowledge I have the better.  As of now I'm planning to go buy this either tonight or tomorrow.

---

### Post by az on 2005-08-15
You can get a number of wireless usb adapters on ebay for less than 25 bucks including shipping.  I just checked.

I think thay all at least work with ndiswrapper.  That is if they do not have native linux drivers.

---

### Post by eMuNiX on 2005-08-15
[QUOTE=numberexhaust]How exactly do I disable ACPI?[/QUOTE]

Disable it in GRUB/Lilo /boot/grub/menu.lst (last couple of entries):-

```
## ## End Default Options ##

title		Ubuntu, kernel 2.6.10-5-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 ro quiet splash noapic acpi=off
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 ro single noapic acpi=off
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST
``` its the noapic and acpi=off bit that need adding.

---

### Post by numberexhaust on 2005-08-15
ACPI off didn't really work... tried that already.  Hmm.

---

### Post by Fed on 2005-08-16
Sorry that your Dell didnt have a similar option in the BIOS setup as did my Thinkpad. But they fixed the problem with a driver update, so youd really think its not that bad :/

Oh well. Just a final note, I second the suggestion to get something off ebay, just get some dirt cheap one so that in the off-chance that it doesnt work, you havent wasted too much (and you could even sell it back on ebay  ;-) )

---

### Post by numberexhaust on 2005-08-16
Good stuff guys... I'm gonna look around and see where I can get a cheap card that is on either the wiki list or the pcmcia sourceforge list.  I've already located a couple of them.

I'll keep you guys updated once I get the card.

PS, how reliable is ndiswrapper?  I've heard some bad things about it, but I really would like to use it if it enables me to get a better card (Like a netgear WG511 or something).

---

