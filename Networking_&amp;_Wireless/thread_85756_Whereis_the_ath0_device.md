---
title: "Whereis the ath0 device?"
date: 2005-11-03
forum: Networking &amp; Wireless
---

### Post by Corrupted Mind on 2005-11-03
Hi,

I just install a D-Link DWL-G520 wireless network card and I don't know how to configure it properly. ( It seem that many users have that problem with linux ;) ) I know my wifi card is working properly because I did catch the SSID of my network when I was testing some obcure, not free driverloader. ( DriverLoader ) The big problem I'm getting is I can't see the ath0 logical device; I just get some wierd sit0 device. Can't someone help me with this ?


Here my specs and conf:

# dmeg
```
Linux version 2.6.10-5-386 (buildd@terranova) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Mon Oct 10 11:15:41 UTC 2005
BIOS-provided physical RAM map:
 BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
 BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
 BIOS-e820: 00000000000e8800 - 0000000000100000 (reserved)
 BIOS-e820: 0000000000100000 - 0000000007ef0000 (usable)
 BIOS-e820: 0000000007ef0000 - 0000000007effc00 (ACPI data)
 BIOS-e820: 0000000007effc00 - 0000000007f00000 (ACPI NVS)
 BIOS-e820: 0000000007f00000 - 0000000008000000 (reserved)
 BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
126MB LOWMEM available.
On node 0 totalpages: 32496
  DMA zone: 4096 pages, LIFO batch:1
  Normal zone: 28400 pages, LIFO batch:6
  HighMem zone: 0 pages, LIFO batch:1
DMI not present.
ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f76b0
ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x07efce89
ACPI: FADT (v001 HP     Hawk     0x06040000 PTL  0x000f4240) @ 0x07effb65
ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x07effbd9
ACPI: DSDT (v001  INTEL  Whitney 0x06040000 MSFT 0x01000007) @ 0x00000000
ACPI: PM-Timer IO Port: 0x1008
Built 1 zonelists
Kernel command line: root=/dev/hdb1 ro quiet splash
Local APIC disabled by BIOS -- you can enable it with "lapic"
mapped APIC to ffffd000 (01100000)
Initializing CPU#0
PID hash table entries: 512 (order: 9, 8192 bytes)
Detected 534.685 MHz processor.
Using pmtmr for high-res timesource
Console: colour VGA+ 80x25
Dentry cache hash table entries: 16384 (order: 4, 65536 bytes)
Inode-cache hash table entries: 8192 (order: 3, 32768 bytes)
Memory: 121372k/129984k available (1437k kernel code, 8072k reserved, 753k data, 224k init, 0k highmem)
Checking if this processor honours the WP bit even in supervisor mode... Ok.
Calibrating delay loop... 1056.76 BogoMIPS (lpj=528384)
Security Framework v1.0.0 initialized
SELinux:  Disabled at boot.
Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
CPU: After generic identify, caps: 0183f9ff 00000000 00000000 00000000 00000000 00000000
CPU: After vendor identify, caps: 0183f9ff 00000000 00000000 00000000 00000000 00000000
CPU: L1 I cache: 16K, L1 D cache: 16K
CPU: L2 cache: 128K
CPU: After all inits, caps: 0183f9ff 00000000 00000000 00000040 00000000 00000000
CPU: Intel Celeron (Mendocino) stepping 05
Enabling fast FPU save and restore... done.
Checking 'hlt' instruction... OK.
Checking for popad bug... OK.
ACPI: Looking for DSDT in initrd... not found!
ACPI: setting ELCR to 0200 (from 0220)
checking if image is initramfs...it isn't (bad gzip magic numbers); looks like an initrd
Freeing initrd memory: 4300k freed
NET: Registered protocol family 16
EISA bus registered
PCI: PCI BIOS revision 2.10 entry at 0xfd99e, last bus=1
PCI: Using configuration type 1
mtrr: v2.0 (20020519)
ACPI: Subsystem revision 20050211
ACPI: Interpreter enabled
ACPI: Using PIC for interrupt routing
ACPI: PCI Root Bridge [PCI0] (00:00)
PCI: Probing PCI hardware (bus 00)
PCI: Transparent bridge - 0000:00:1e.0
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *9 10 11 14 15)
ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 9 10 11 14 15)
ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 9 10 11 14 15)
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.SLOT._PRT]
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
    ACPI-1138: *** Error: Method execution failed [\_SB_.PCI0.LPC0.SIO_.LPT_._CRS] (Node c7aa54e0), AE_AML_BUFFER_LIMIT
    ACPI-0158: *** Error: Method execution failed [\_SB_.PCI0.LPC0.SIO_.LPT_._CRS] (Node c7aa54e0), AE_AML_BUFFER_LIMIT
pnp: PnPACPI: METHOD_NAME__CRS failure for PNP0400
pnp: PnP ACPI: found 11 devices
PnPBIOS: Disabled by ACPI PNP
PCI: Using ACPI for IRQ routing
** PCI interrupts are no longer routed automatically.  If this
** causes a device to stop working, it is probably because the
** driver failed to call pci_enable_device().  As a temporary
** workaround, the "pci=routeirq" argument restores the old
** behavior.  If this argument makes the device work again,
** please email the output of "lspci" to bjorn.helgaas@hp.com
** so I can fix the driver.
pnp: 00:00: ioport range 0x1000-0x105f could not be reserved
pnp: 00:00: ioport range 0x1060-0x107f has been reserved
pnp: 00:00: ioport range 0x1180-0x11bf has been reserved
pnp: 00:00: ioport range 0x1c00-0x1c7f has been reserved
pnp: 00:00: ioport range 0x4d0-0x4d1 has been reserved
pnp: 00:00: ioport range 0x600-0x67f has been reserved
Simple Boot Flag at 0x36 set to 0x1
audit: initializing netlink socket (disabled)
audit(1131035619.689:0): initialized
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0
Initializing Cryptographic API
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
serio: i8042 AUX port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered
RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
input: AT Translated Set 2 keyboard on isa0060/serio0
EISA: Probing bus 0 at eisa0
Cannot allocate resource for EISA slot 1
Cannot allocate resource for EISA slot 2
EISA: Detected 0 cards.
NET: Registered protocol family 2
IP: routing cache hash table of 512 buckets, 4Kbytes
TCP: Hash tables configured (established 8192 bind 16384)
NET: Registered protocol family 8
NET: Registered protocol family 20
Restarting tasks...<6> Strange, kswapd0 not stopped
 Strange, kseriod not stopped
 done
ACPI wakeup devices:
KBC0 SLOT  USB AC97
ACPI: (supports S0 S1 S5)
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4300KiB [1 disk] into ram disk... done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 224k freed
NET: Registered protocol family 1
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
ICH: IDE controller at PCI slot 0000:00:1f.1
ICH: chipset revision 2
ICH: not 100% native mode: will probe irqs later
    ide0: BM-DMA at 0x10a0-0x10a7, BIOS settings: hda:pio, hdb:DMA
    ide1: BM-DMA at 0x10a8-0x10af, BIOS settings: hdc:pio, hdd:pio
Probing IDE interface ide0...
hda: TDK CDRW5200B, ATAPI CD/DVD-ROM drive
hdb: Maxtor 91080D5, ATA DISK drive
elevator: using anticipatory as default io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hdb: max request size: 128KiB
hdb: 21095424 sectors (10800 MB) w/512KiB Cache, CHS=20928/16/63, UDMA(33)
hdb: cache flushes not supported
 /dev/ide/host0/bus0/target1/lun0: p1 p2 < p5 >
Probing IDE interface ide1...
Probing IDE interface ide1...
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
Stopping tasks: ==|
Freeing memory... done (458 pages freed)
Restarting tasks... done
EXT3-fs: INFO: recovery required on readonly filesystem.
EXT3-fs: write access will be enabled during recovery.
EXT3-fs: recovery complete.
kjournald starting.  Commit interval 5 seconds
EXT3-fs: mounted filesystem with ordered data mode.
Adding 465844k swap on /dev/hdb5.  Priority:-1 extents:1
EXT3 FS on hdb1, internal journal
hda: ATAPI 48X CD-ROM CD-R/RW drive, 2048kB Cache
Uniform CD-ROM driver Revision: 3.20
parport0: PC-style at 0x378 [PCSPP,TRISTATE,EPP]
lp0: using parport0 (polling).
mice: PS/2 mouse device common for all mice
input: PS/2 Generic Mouse on isa0060/serio1
ts: Compaq touchscreen protocol output
Capability LSM initialized
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: dm-devel@redhat.com
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
cdrom: open failed.
Real Time Clock Driver v1.12
input: PC Speaker
inserting floppy driver for 2.6.10-5-386
Floppy drive(s): fd0 is 1.44M
FDC 0 is a post-1991 82077
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected an Intel i810 Chipset.
agpgart: Maximum main memory to use for agp memory: 93M
agpgart: AGP aperture is 64M @ 0xf8000000
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
hw_random hardware driver 1.0.0 loaded
usbcore: registered new driver usbfs
usbcore: registered new driver hub
USB Universal Host Controller Interface driver v2.2
ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 5
PCI: setting IRQ 5 as level-triggered
ACPI: PCI interrupt 0000:00:1f.2[D] -> GSI 5 (level, low) -> IRQ 5
uhci_hcd 0000:00:1f.2: Intel Corp. 82801AA USB
PCI: Setting latency timer of device 0000:00:1f.2 to 64
uhci_hcd 0000:00:1f.2: irq 5, io base 0x1080
uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
usb 1-2: new low speed USB device using uhci_hcd and address 2
usbcore: registered new driver hiddev
input: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:1f.2-2
usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.0:USB HID core driver
8139too Fast Ethernet driver 0.9.27
PCI: Enabling device 0000:01:08.0 (0104 -> 0107)
ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 9
PCI: setting IRQ 9 as level-triggered
ACPI: PCI interrupt 0000:01:08.0[A] -> GSI 9 (level, low) -> IRQ 9
eth0: RealTek RTL8139 at 0x2000, 00:10:b5:0e:62:5b, IRQ 9
eth0:  Identified 8139 chip type 'RTL-8139C'
8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
ath_hal: module license 'Proprietary' taints kernel.
ath_hal: 0.9.12.14 (AR5210, AR5211, AR5212)
wlan: 0.8.4.5 (EXPERIMENTAL)
ath_rate_onoe: 1.0
ath_pci: 0.9.4.12 (EXPERIMENTAL)
PCI: Enabling device 0000:01:09.0 (0314 -> 0316)
ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
ACPI: PCI interrupt 0000:01:09.0[A] -> GSI 5 (level, low) -> IRQ 5
ath%d: unable to attach hardware; HAL status 13
NET: Registered protocol family 17
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02f0500(lo)
IPv6 over IPv4 tunneling driver
CSLIP: code copyright 1989 Regents of the University of California
PPP generic driver version 2.4.2
NET: Registered protocol family 24
ACPI: Power Button (FF) [PWRF]
ibm_acpi: ec object not found
eth0: no IPv6 routers present
apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
apm: overridden by ACPI.

```

# lsmod
```
Module                  Size  Used by
proc_intf               4100  0
freq_table              4100  0
cpufreq_userspace       4572  0
cpufreq_ondemand        6172  0
cpufreq_powersave       1920  0
video                  16260  0
sony_acpi               6280  0
pcc_acpi               11264  0
button                  6800  0
battery                10244  0
container               4608  0
ac                      4996  0
pppoe                  13632  0
pppox                   3848  1 pppoe
ppp_generic            27668  2 pppoe,pppox
slhc                    7040  1 ppp_generic
ipv6                  229376  22
af_packet              20744  2
ath_pci                55584  0
ath_rate_onoe           8840  1 ath_pci
wlan                  106588  2 ath_pci,ath_rate_onoe
ath_hal               133328  1 ath_pci
8139cp                 19200  0
8139too                24320  0
mii                     4736  2 8139cp,8139too
i2c_i801                8076  0
i2c_core               21264  1 i2c_i801
usbhid                 29376  0
uhci_hcd               30224  0
usbcore               107384  3 usbhid,uhci_hcd
hw_random               5524  0
shpchp                 86116  0
pci_hotplug            30512  1 shpchp
intel_agp              20636  1
agpgart                31784  2 intel_agp
floppy                 54864  0
pcspkr                  3816  0
rtc                    12216  0
md                     43856  0
dm_mod                 53116  1
capability              5000  0
commoncap               7808  1 capability
tsdev                   7488  0
evdev                   9088  0
psmouse                19336  0
mousedev               11160  1
parport_pc             34372  1
lp                     10792  0
parport                33480  2 parport_pc,lp
ide_cd                 38532  0
cdrom                  36508  1 ide_cd
ext3                  120968  1
jbd                    54168  1 ext3
ide_generic             1664  0
piix                    9988  1
ide_disk               18176  3
ide_core              118988  4 ide_cd,ide_generic,piix,ide_disk
unix                   26164  732
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

```

# lspci
```
Controller] (rev 02)
0000:00:1e.0 PCI bridge: Intel Corp. 82801AA PCI Bridge (rev 02)
0000:00:1f.0 ISA bridge: Intel Corp. 82801AA ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corp. 82801AA IDE (rev 02)
0000:00:1f.2 USB Controller: Intel Corp. 82801AA USB (rev 02)
0000:00:1f.3 SMBus: Intel Corp. 82801AA SMBus (rev 02)
0000:01:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:01:09.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

```

# lshw
```
amiga
    description: Computer
  *-core
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 126MB
     *-cpu
          product: Celeron (Mendocino)
          vendor: Intel Corp.
          physical id: 1
          version: 6.6.5
          size: 534MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 32KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 128KB
     *-pci
          physical id: 100
          bus info: pci@00:00.0
          version: 02
          clock: 33MHz
        *-display UNCLAIMED
             physical id: 1
             bus info: pci@00:01.0
             version: 02
             size: 64MB
             clock: 66MHz
             capabilities: bus_master cap_list
             configuration: irq=9
        *-pci
             physical id: 1e
             bus info: pci@00:1e.0
             version: 02
             clock: 33MHz
             capabilities: pci bus_master
           *-network:0
                physical id: 8
                bus info: pci@01:08.0
                version: 10
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=8139too irq=9
           *-network:1 UNCLAIMED
                physical id: 9
                bus info: pci@01:09.0
                version: 01
                clock: 33MHz
                capabilities: cap_list
                configuration: irq=5
        *-isa UNCLAIMED
             physical id: 1f
             bus info: pci@00:1f.0
             version: 02
             clock: 33MHz
             capabilities: isa bus_master
        *-ide
             physical id: 1f.1
             bus info: pci@00:1f.1
             version: 02
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=PIIX_IDE
        *-usb
             physical id: 1f.2
             bus info: pci@00:1f.2
             version: 02
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd irq=5
        *-serial
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 02
             clock: 33MHz
             configuration: driver=i801_smbus irq=5
  *-network:0
       description: Ethernet controller
       physical id: 1
       logical name: eth0
       serial: 00:10:b5:0e:62:5b
       capabilities: mii autonegotiation 100bt-fd 100bt 10bt-fd 10bt ethernet
       configuration: autonegociated=100bt broadcast=yes driver=8139too driverversion=0.9.27 duplex=full ip=192.168.1.101 link=yes multicast=yes
  *-network:1 DISABLED
       description: controller
       physical id: 2
       logical name: sit0

```

# ifconfig -a
```
eth0      Link encap:Ethernet  HWaddr 00:10:B5:0E:62:5B
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::210:b5ff:fe0e:625b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1957 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1998 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1809559 (1.7 MiB)  TX bytes:239686 (234.0 KiB)
          Interrupt:9 Base address:0x2000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:19889 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19889 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4318605 (4.1 MiB)  TX bytes:4318605 (4.1 MiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


```

# iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.


```

# cat /etc/network/interfaces
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0
        map ath0          # This line was custom added by me

iface eth0 inet dhcp
iface ath0 inet dhcp  # This line was custom added by me

auto ath0                  # This line was custom added by me


auto eth0

# those lines where automatically added by linux
iface wlan0 inet dhcp
wireless-essid linksys_SES_52337
wireless-key XXXXXXXXXX               # masked by me

auto wlan0

```

Thanks for helping me in advance :KS 

--------------------------
Do a Good Deed -- Bomb an SUV!

---

### Post by spd106 on 2005-11-04
> ath_hal: module license 'Proprietary' taints kernel.
ath_hal: 0.9.12.14 (AR5210, AR5211, AR5212)
wlan: 0.8.4.5 (EXPERIMENTAL)
ath_rate_onoe: 1.0
ath_pci: 0.9.4.12 (EXPERIMENTAL)
PCI: Enabling device 0000:01:09.0 (0314 -> 0316)
ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
ACPI: PCI interrupt 0000:01:09.0[A] -> GSI 5 (level, low) -> IRQ 5
ath%d: unable to attach hardware; HAL status 13
According to the madwifi [website]("http://www.madwifi.org/wiki/UserDocs/Troubleshooting#WhatdoesHALstatus13mean") the ath_hal is too old. Try compiling a newer version. Here's a guide from the [wiki]("https://wiki.ubuntu.com/MoreRecentMadwifiHowto").

---

