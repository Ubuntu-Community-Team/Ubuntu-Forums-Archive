---
title: "BCM4318 major issues"
date: 2008-07-27
forum: Networking &amp; Wireless
---

### Post by djmoore85 on 2008-07-27
Hey all, I have tried several things to accomplish getting this card to work in 8.04, but to no avail. How do I disable the restricted, and get it to use strictly the ndiswrapper setup like when I had 7.10? Any better ideas than the standard walk-throughs I have found?

---

### Post by Ayuthia on 2008-07-27
Have you tried this one?

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

There are some additional steps in Hardy that are needed to make ndiswrapper work.

---

### Post by djmoore85 on 2008-07-27
Yeah went through that step-by step, no luck gettin it to work

---

### Post by Ayuthia on 2008-07-27
Can you post the results of:
```
lshw -C netowrk
ndiswrapper -v
ndiswrapper -l
```It will help us see what driver it is trying to use along with the version of ndiswrapper you are using and what driver it is trying to use.

---

### Post by djmoore85 on 2008-07-27
```
daniel@DanielVid713:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 10
       serial: 00:16:36:06:f0:17
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:05:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:61:14:3d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
daniel@DanielVid713:~$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-19-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.52
vermagic:       2.6.24-19-generic SMP mod_unload 586 
daniel@DanielVid713:~$ ndiswrapper -l
```

---

### Post by Ayuthia on 2008-07-27
Are you able to see anything when you do the following:
```
sudo modprobe -r b43 b44 ssb bcm43xx ndiswrapper
sudo depmod -ae
sudo modprobe ndiswrapper
sudo iwlist scan
```
The results of lshw -C network shows that it is trying to use the b43 driver.  The commands above will try to remove all the conflicting drivers and then load ndiswrapper.

---

### Post by djmoore85 on 2008-07-28
```
daniel@DanielVid713:~$ sudo modprobe -r b43 b44 ssb bcm43xx ndiswrapper
[sudo] password for daniel: 
daniel@DanielVid713:~$ sudo depmod -ae
daniel@DanielVid713:~$ sudo modprobe ndiswrapper
daniel@DanielVid713:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

daniel@DanielVid713:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 10
       serial: 00:16:36:06:f0:17
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.101 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1 UNCLAIMED
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:05:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       configuration: latency=64
daniel@DanielVid713:~$ 

```

---

### Post by sandeepy on 2008-07-28
Did you try :

[http://ubuntuforums.org/showthread.php?t=574501&highlight=Kevdog](http://ubuntuforums.org/showthread.php?t=574501&highlight=Kevdog)

---

### Post by sandeepy on 2008-07-28
Did you try :

[http://ubuntuforums.org/showthread.php?t=574501&highlight=Kevdog](http://ubuntuforums.org/showthread.php?t=574501&highlight=Kevdog)

---

### Post by Ayuthia on 2008-07-28
> **djmoore85 said:**
> ```
daniel@DanielVid713:~$ sudo modprobe -r b43 b44 ssb bcm43xx ndiswrapper
[sudo] password for daniel: 
daniel@DanielVid713:~$ sudo depmod -ae
daniel@DanielVid713:~$ sudo modprobe ndiswrapper
daniel@DanielVid713:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

daniel@DanielVid713:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 10
       serial: 00:16:36:06:f0:17
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.101 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1 UNCLAIMED
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:05:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       configuration: latency=64
daniel@DanielVid713:~$ 

```

Can you check dmesg from the Terminal?  I am thinking that there is some kind of error message there for ndiswrapper.  I say this because the ndiswrapper module did not load and your wireless card is now UNCLAIMED.  So when you run the modprobe commands again, type dmesg and there should be some messages out there for ndiswrapper at the end.

---

### Post by djmoore85 on 2008-07-29
```
[   17.886895] eth0: RealTek RTL8139 at 0xa000, 00:16:36:06:f0:17, IRQ 18
[   17.886897] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   17.889518] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 19
[   17.889568] PCI: Setting latency timer of device 0000:00:14.1 to 64
[   17.889583] ACPI: PCI interrupt for device 0000:00:14.1 disabled
[   17.889918] ACPI: PCI Interrupt 0000:05:02.0[A] -> GSI 20 (level, low) -> IRQ 20
[   17.892369] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   17.909426] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x0D, vendor 0x4243)
[   17.909439] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x09, vendor 0x4243)
[   17.909448] ssb: Core 2 found: PCI (cc 0x804, rev 0x0C, vendor 0x4243)
[   17.909458] ssb: Core 3 found: PCMCIA (cc 0x80D, rev 0x07, vendor 0x4243)
[   17.949423] ssb: Sonics Silicon Backplane found on PCI device 0000:05:02.0
[   17.954088] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 19
[   17.955353] scsi0 : pata_atiixp
[   17.956543] scsi1 : pata_atiixp
[   17.957509] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8410 irq 14
[   17.957513] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8418 irq 15
[   18.122048] ata1.00: ATA-6: HTS424040M9AT00, MA2OA72A, max UDMA/100
[   18.122053] ata1.00: 78140160 sectors, multi 16: LBA 
[   18.137984] ata1.00: configured for UDMA/100
[   18.457431] ata2.00: ATAPI: SONY CD-RW/DVD-ROM CRX835E, KPK4, max MWDMA2
[   18.457447] ata2.00: simplex DMA is claimed by other device, disabling DMA
[   18.629211] ata2.00: configured for PIO4
[   18.629334] scsi 0:0:0:0: Direct-Access     ATA      HTS424040M9AT00  MA2O PQ: 0 ANSI: 5
[   18.630539] scsi 1:0:0:0: CD-ROM            SONY     CD-RW  CRX835E   KPK4 PQ: 0 ANSI: 5
[   18.637951] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   18.637958] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   18.651101] Driver 'sd' needs updating - please use bus_type methods
[   18.651189] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[   18.651202] sd 0:0:0:0: [sda] Write Protect is off
[   18.651205] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   18.651219] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   18.651261] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[   18.651269] sd 0:0:0:0: [sda] Write Protect is off
[   18.651272] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   18.651284] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   18.651288]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   18.667452]  sda1 sda2 < sda5 >
[   18.709250] sd 0:0:0:0: [sda] Attached SCSI disk
[   18.716018] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   18.716038] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   18.719326] sr0: scsi3-mmc drive: 0x/24x writer cd/rw xa/form2 cdda tray
[   18.719333] Uniform CD-ROM driver Revision: 3.20
[   18.719390] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   19.140312] Attempting manual resume
[   19.140317] swsusp: Resume From Partition 8:5
[   19.140319] PM: Checking swsusp image.
[   19.140569] PM: Resume from disk failed.
[   19.184179] kjournald starting.  Commit interval 5 seconds
[   19.184195] EXT3-fs: mounted filesystem with ordered data mode.
[   33.378668] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   35.001372] Linux agpgart interface v0.102
[   35.045344] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   35.093339] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   35.141562] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   35.341156] input: Power Button (FF) as /devices/virtual/input/input3
[   35.369029] ACPI: Power Button (FF) [PWRF]
[   35.369087] input: Power Button (CM) as /devices/virtual/input/input4
[   35.400997] ACPI: Power Button (CM) [PWRB]
[   35.401056] input: Sleep Button (CM) as /devices/virtual/input/input5
[   35.429070] ACPI: Sleep Button (CM) [SLPB]
[   35.429133] input: Lid Switch as /devices/virtual/input/input6
[   35.445239] ACPI: Lid Switch [LID]
[   35.445301] ACPI: WMI-Acer: Mapper loaded
[   35.552572] Yenta: CardBus bridge found at 0000:05:09.0 [103c:3091]
[   35.552600] Yenta: Enabling burst memory read transactions
[   35.552607] Yenta: Using CSCINT to route CSC interrupts to PCI
[   35.552609] Yenta: Routing CardBus interrupts to PCI
[   35.552616] Yenta TI: socket 0000:05:09.0, mfunc 0x01a01b22, devctl 0x66
[   35.781468] Yenta: ISA IRQ mask 0x0ee8, PCI irq 16
[   35.781474] Socket status: 30000006
[   35.781477] Yenta: Raising subordinate bus# of parent bus (#05) from #05 to #09
[   35.781484] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
[   35.781487] cs: IO port probe 0xa000-0xafff: clean.
[   35.781699] pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xc02fffff
[   36.062447] ACPI: AC Adapter [ACAD] (off-line)
[   36.551203] ACPI: Battery Slot [BAT1] (battery present)
[   36.579742] Synaptics Touchpad, model: 1, fw: 5.10, id: 0x258eb1, caps: 0xa04713/0x0
[   36.612694] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   37.023908] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:0e/LNXVIDEO:00/input/input8
[   37.055475] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   37.409013] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   37.438170] [fglrx]   vendor: 1002 device: 5955 count: 1
[   37.438229] [fglrx] Maximum main memory to use for locked dma buffers: 1049 MBytes.
[   37.438367] [fglrx] PAT is enabled successfully!
[   37.438392] [fglrx] module loaded - fglrx 8.50.3 [Jun  2 2008] with 1 minors
[   37.539527] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> IRQ 16
[   37.552226] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 16
[   37.643828] b43-phy0: Broadcom 4318 WLAN found
[   37.662948] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/ac97/ac97_codec.c:2160: MC'97 0 converters and GPIO not ready (0x1)
[   37.686877] b43-phy0 debug: Found PHY: Analog 3, Type 2, Revision 7
[   37.686903] b43-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 8
[   37.713687] phy0: Selected rate control algorithm 'simple'
[   39.251540] cs: IO port probe 0x100-0x3af: clean.
[   39.253958] cs: IO port probe 0x3e0-0x4ff: clean.
[   39.254943] cs: IO port probe 0x820-0x8ff: clean.
[   39.255756] cs: IO port probe 0xc00-0xcf7: clean.
[   39.256612] cs: IO port probe 0xa00-0xaff: clean.
[   39.890511] lp: driver loaded but no devices found
[   39.936759] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   40.059340] usbcore: registered new interface driver ndiswrapper
[   40.150765] Adding 2449904k swap on /dev/sda5.  Priority:-1 extents:1 across:2449904k
[   40.184598] EXT3 FS on sda1, internal journal
[   41.064840] ip_tables: (C) 2000-2006 Netfilter Core Team
[   41.675811] No dock devices found.
[   42.034469] powernow-k8: Found 1 Mobile AMD Sempron(tm) Processor 3000+ processors (1 cpu cores) (version 2.20.00)
[   42.034508] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0xa
[   42.034511] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0xc
[   42.034513] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x13
[   43.038968] apm: BIOS not found.
[   43.423794] ppdev: user-space parallel port driver
[   43.753925] audit(1217279974.071:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4821 profile="/usr/sbin/cupsd" namespace="default"
[  100.998099] Marking TSC unstable due to: cpufreq changes.
[  101.001512] Time: acpi_pm clocksource has been installed.
[  101.161450] Clocksource tsc unstable (delta = -90920619 ns)
[  102.238589] input: b43-phy0 as /devices/virtual/input/input9
[  102.595829] b43-phy0 debug: Loading firmware version 351.126 (2006-07-29 05:54:02)
[  102.645821] Bluetooth: Core ver 2.11
[  102.646965] NET: Registered protocol family 31
[  102.646974] Bluetooth: HCI device and connection manager initialized
[  102.646994] Bluetooth: HCI socket layer initialized
[  102.816669] Bluetooth: L2CAP ver 2.9
[  102.816679] Bluetooth: L2CAP socket layer initialized
[  102.968355] Bluetooth: RFCOMM socket layer initialized
[  102.968951] Bluetooth: RFCOMM TTY layer initialized
[  102.968960] Bluetooth: RFCOMM ver 1.8
[   46.387775] b43-phy0 debug: Chip initialized
[   46.388385] b43-phy0 debug: 32-bit DMA initialized
[   46.408053] Registered led device: b43-phy0:radio
[   46.408108] b43-phy0 debug: Wireless interface started
[   46.453874] b43-phy0: Radio hardware status changed to DISABLED
[   46.455244] b43-phy0 debug: Adding Interface type 2
[   46.478016] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   54.136860] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 16
[  109.424800] NET: Registered protocol family 17
[   50.354960] [fglrx] GART Table is not in FRAME_BUFFER range 
[   50.358432] [fglrx] Reserved FB block: Shared offset:0, size:40000 
[   50.358440] [fglrx] Reserved FB block: Unshared offset:7ff5000, size:b000 
[  117.309802] NET: Registered protocol family 10
[  117.310897] lo: Disabled Privacy Extensions
[  117.313459] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  129.727540] eth0: no IPv6 routers present
[  138.280796] eth0: link down
[   64.214540] glxinfo[5742]: segfault at b7f6b000 eip b7987e28 esp bff645d0 error 6
[86082.523448] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[86082.525575] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[86098.645521] eth0: no IPv6 routers present
[86234.361453] b43-phy0 debug: Removing Interface type 2
[86234.413686] b43-phy0 debug: Wireless interface stopped
[86234.413820] b43-phy0 debug: DMA-32 0x0200 (RX) max used slots: 0/64
[86234.413900] b43-phy0 debug: DMA-32 0x02A0 (TX) max used slots: 0/128
[86234.421404] b43-phy0 debug: DMA-32 0x0280 (TX) max used slots: 0/128
[86234.429396] b43-phy0 debug: DMA-32 0x0260 (TX) max used slots: 0/128
[86234.437370] b43-phy0 debug: DMA-32 0x0240 (TX) max used slots: 0/128
[86234.445378] b43-phy0 debug: DMA-32 0x0220 (TX) max used slots: 2/128
[86234.453359] b43-phy0 debug: DMA-32 0x0200 (TX) max used slots: 0/128
[86234.537093] ACPI: PCI interrupt for device 0000:05:02.0 disabled
[86234.780902] usbcore: deregistering interface driver ndiswrapper
[86259.942173] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[86259.988444] usbcore: registered new interface driver ndiswrapper
daniel@DanielVid713:~$ 
```


Sorry, I know this is a lot of code to go over, I copied just what I saw was relative to networking hardware. Hope this helps find the issue and a solution

---

### Post by Ayuthia on 2008-07-29
> **djmoore85 said:**
> 
Sorry, I know this is a lot of code to go over, I copied just what I saw was relative to networking hardware. Hope this helps find the issue and a solution
Well, that looks ok.  The only part that I see that is missing in dmesg is the driver that is being used.  Have you installed a driver?  Can you post the results of:
```
ndiswrapper -l
```It should have something that comes back saying that the driver is installed and the device is present.  If it does not, you will need to find the Windows driver and install it.

---

### Post by djmoore85 on 2008-07-31
```
daniel@DanielVid713:~$ ndiswrapper -l
daniel@DanielVid713:~$
``` 


I get nothing. I take it there is a problem somewhere.... lol sorry long day at work

---

### Post by Ayuthia on 2008-07-31
> **djmoore85 said:**
> ```
daniel@DanielVid713:~$ ndiswrapper -l
daniel@DanielVid713:~$
``` 


I get nothing. I take it there is a problem somewhere.... lol sorry long day at work
Thanks!  It's nice to see some humor.  It looks like you need to install a windows driver.  The files that you need are bcmwl5.inf and bcmwl5.sys (32-bit) or bcmwl564.sys (64-bit).  Do you have one?  It will need to be from XP.  If you don't, please go to this link:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
It has a recommended driver for your card.  It looks like the driver is in step 2a.  If you download it from that link, you can also continue on to step 3 if you want.  It will provide similar steps to what I would be giving you.

---

### Post by djmoore85 on 2008-07-31
You know it's crazy, my restricted drivers are showing that the b43 is in use. I disabled it I thought. And I have the windows drivers on a flash drive from my previous 7.10 install, do I just run those through the GUI (ndisgtk) or is there a way to install the drivers through the terminal for ndiswrapper? And how do I disable for good the restricted driver so there are no conflicts once I get ndiswrapper up and running

---

