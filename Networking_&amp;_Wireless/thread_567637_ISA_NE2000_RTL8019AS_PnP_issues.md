---
title: "ISA NE2000 RTL8019AS PnP issues"
date: 2007-10-04
forum: Networking &amp; Wireless
---

### Post by survient on 2007-10-04
Ok, I have an old ISA NIC NE2000 compatible adapter with a realtek RTL8019AS chipset. It says it supports jumperless PnP, and my mobo is PnP compatible. I would just get a PCI NIC adapter, but all of the PCI slots are being used. Each time I run ifconfig, the card won't show up. here's the dmesg and ifconfig outputs:
> me@example:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:4C:69:6E:75:79
          inet addr:192.168.0.117  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::24c:69ff:fe6e:7579/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1993 (1.9 KiB)  TX bytes:4081 (3.9 KiB)
          Interrupt:10 Base address:0x7000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:480 (480.0 b)  TX bytes:480 (480.0 b)

me@example:~$ dmesg
Linux version 2.6.10-5-386 (buildd@terranova) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Mon Oct 10 11:15:41 UTC 2005
BIOS-provided physical RAM map:
 BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
 BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
 BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
 BIOS-e820: 0000000000100000 - 0000000005000000 (usable)
80MB LOWMEM available.
On node 0 totalpages: 20480
  DMA zone: 4096 pages, LIFO batch:1
  Normal zone: 16384 pages, LIFO batch:4
  HighMem zone: 0 pages, LIFO batch:1
DMI not present.
ACPI: Unable to locate RSDP
Built 1 zonelists
Kernel command line: root=/dev/hda2 ro quiet splash
No local APIC present or hardware disabled
mapped APIC to ffffd000 (010a2000)
Initializing CPU#0
PID hash table entries: 512 (order: 9, 8192 bytes)
Using pit for high-res timesource
Console: colour VGA+ 80x25
Dentry cache hash table entries: 16384 (order: 4, 65536 bytes)
Inode-cache hash table entries: 8192 (order: 3, 32768 bytes)
Memory: 73696k/81920k available (1437k kernel code, 7720k reserved, 753k data, 224k init, 0k highmem)
Checking if this processor honours the WP bit even in supervisor mode... Ok.
Calibrating delay loop... 130.81 BogoMIPS (lpj=65408)
Security Framework v1.0.0 initialized
SELinux:  Disabled at boot.
Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
CPU: After generic identify, caps: 00000000 00000000 00000000 00000000 00000000 00000000
CPU: After all inits, caps: 00000000 00000000 00000000 00000000 00000000 00000000
CPU: 486
Checking 'hlt' instruction... OK.
Checking for popad bug... OK.
checking if image is initramfs...it isn't (bad gzip magic numbers); looks like an initrd
Freeing initrd memory: 4248k freed
NET: Registered protocol family 16
EISA bus registered
PCI: PCI BIOS revision 2.10 entry at 0xf0200, last bus=0
PCI: Using configuration type 1
mtrr: v2.0 (20020519)
ACPI: Subsystem revision 20050211
ACPI: Interpreter disabled.
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI: disabled
PnPBIOS: Scanning system for PnP BIOS support...
PnPBIOS: Found PnP BIOS installation structure at 0xc00f9730
PnPBIOS: PnP BIOS version 1.0, entry 0xf2300:0x0, dseg 0xf0000
PnPBIOS: 15 nodes reported by PnP BIOS; 15 recorded by driver
PCI: Probing PCI hardware
PCI: Probing PCI hardware (bus 00)
audit: initializing netlink socket (disabled)
audit(1191521137.591:0): initialized
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0
Initializing Cryptographic API
isapnp: Scanning for PnP cards...
isapnp: Card 'CS4237'
isapnp: Card 'Plug & Play Ethernet Card'
isapnp: 2 Plug & Play cards detected total
serio: i8042 AUX port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
ttyS2 at I/O 0x3e8 (irq = 4) is a 16550A
ttyS2 at I/O 0x3e8 (irq = 4) is a 16550A
ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered
RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
input: AT Translated Set 2 keyboard on isa0060/serio0
EISA: Probing bus 0 at eisa0
Cannot allocate resource for EISA slot 7
EISA: Detected 0 cards.
NET: Registered protocol family 2
IP: routing cache hash table of 512 buckets, 4Kbytes
TCP: Hash tables configured (established 8192 bind 16384)
NET: Registered protocol family 8
NET: Registered protocol family 20
Restarting tasks...<6> Strange, kswapd0 not stopped
 Strange, kpnpbiosd not stopped
 Strange, kseriod not stopped
 done
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4248KiB [1 disk] into ram disk... done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 224k freed
NET: Registered protocol family 1
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Probing IDE interface ide0...
hda: QUANTUM BIGFOOT_CY2160A, ATA DISK drive
hdb: CD-916E/ATK, ATAPI CD/DVD-ROM drive
Probing IDE interface ide1...
hdc: ST34311A, ATA DISK drive
ide2: I/O resource 0x3EE-0x3EE not free.
ide2: ports already in use, skipping probe
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
elevator: using anticipatory as default io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
ide1 at 0x170-0x177,0x376 on irq 15
hda: max request size: 128KiB
hda: 4124736 sectors (2111 MB) w/67KiB Cache, CHS=4092/16/63
hda: cache flushes not supported
 /dev/ide/host0/bus0/target0/lun0: p1 p2
hdc: max request size: 128KiB
hdc: 8452080 sectors (4327 MB) w/256KiB Cache, CHS=8944/15/63
hdc: cache flushes not supported
 /dev/ide/host1/bus0/target0/lun0: p1
Stopping tasks: ==|
Freeing memory... done (453 pages freed)
Restarting tasks... done
EXT3-fs: INFO: recovery required on readonly filesystem.
EXT3-fs: write access will be enabled during recovery.
EXT3-fs: recovery complete.
kjournald starting.  Commit interval 5 seconds
EXT3-fs: mounted filesystem with ordered data mode.
Adding 197528k swap on /dev/hda1.  Priority:-1 extents:1
EXT3 FS on hda2, internal journal
hdb: ATAPI 12X CD-ROM drive, 120kB Cache
Uniform CD-ROM driver Revision: 3.20
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
lp0: using parport0 (interrupt-driven).
mice: PS/2 mouse device common for all mice
input: ImPS/2 Generic Wheel Mouse on isa0060/serio1
ts: Compaq touchscreen protocol output
Capability LSM initialized
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: [email]dm-devel@redhat.com[/email]
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
cdrom: open failed.
kjournald starting.  Commit interval 5 seconds
EXT3 FS on hdc1, internal journal
EXT3-fs: recovery complete.
EXT3-fs: mounted filesystem with ordered data mode.
Real Time Clock Driver v1.12
input: PC Speaker
inserting floppy driver for 2.6.10-5-386
FDC 0 is a post-1991 82077
pnp: Device 01:01.01 activated.
gameport: NS558 PnP at pnp01:01.01 io 0x200 size 8 speed 420 kHz
Linux agpgart interface v0.100 (c) Dave Jones
Linux Tulip driver version 1.1.13 (May 11, 2002)
tulip0:  MII transceiver #1 config 3100 status 7869 advertising 05e1.
eth0: ADMtek Comet rev 17 at 00017000, EEPROM not present, 00:4C:69:6E:75:79, IRQ 10.
usbcore: registered new driver usbfs
NET: Registered protocol family 17
usbcore: registered new driver hub
0000:00:0f.0: tulip_stop_rxtx() failed
eth0: Setting full-duplex based on MII#1 link partner capability of 45e1.
ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
USB Universal Host Controller Interface driver v2.2
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02f0500(lo)
IPv6 over IPv4 tunneling driver
eth0: no IPv6 routers present
I ran the realtek utility for 8019 cards off a boot disk I have, it detects it, but it says "RSET has detected an inactive Plug & Play card on your system. It happens when your system is not equipped with Plug & Play BIOS or equivalent. Do you want to activate inactive LAN card?" I tell it yes and it says "The LAN card's Plug & Play I/O range check function has some problems. Press spacebar to return to dos." I have another 98SE box that works great with the card while it has jumperless settings, but in this IBM box it doesn't know what to do with it. I would manually assign the IRQ settings, but I don't know how.

---

### Post by survient on 2007-10-04
[http://ubuntuforums.org/showpost.php?p=3442859&postcount=12](http://ubuntuforums.org/showpost.php?p=3442859&postcount=12) I tried following the directions here, but I don't even have a /driver directory in my root filesystem.

---

### Post by noob12 on 2007-10-04
Sigh.  Had copied that from the kernel doc which is out of date.  Updated the path to /sys; corrected in that posting. See if any of the rest applies?

---

### Post by survient on 2007-10-04
No go, it doesn't list anything when I type
ls /sys/bus/pnp/devices/*/name
I added ne to the /etc/modules, it loads the module but now the internet won't work on either ethernet adapter.

---

### Post by noob12 on 2007-10-04
I don't think that will work.  The **ne** module requires the io base address at least (**modinfo ne**).

Need to find someone with a similar vintage dinosaur.   Sorry I couldn't help.

---

### Post by survient on 2007-10-04
essentially I have the ISA adapter and a PCI adapter, right now I'm just looking for a utility similar to gnome's network manager that will work with ubuntu lite, as the machine I'm working with isn't powerful enough to handle xubuntu or standard ubuntu for that matter. I've gotten it to recognize the card, I just need to run a utility to configure it.

---

