---
title: "IBM T41 - Intel 82540EP no link light"
date: 2007-08-08
forum: Networking &amp; Wireless
---

### Post by stryc9 on 2007-08-08
I cannot seem to be able to get the wired ethernet connection on my IBM T41 to connect.  The link light is off, I have tried different cables, etc.  I even unplugged a PC that I know has a working cable and port and still no go.

Ubuntu 7.04

sudo ethtool eth0
```

Settings for eth0:
Supported ports: [ TP ]
Supported link modes:   10baseT/Half 10baseT/Full
                                      100baseT/Half 100baseT/Full
                                      1000baseT/Full
Supports auto-negotiation:  Yes
Advertised link modes:  10baseT/Half 10baseT/Full
                                      100baseT/Half 100baseT/Full
                                      1000baseT/Full
Advertised auto-negotiation:  Yes
Speed:  Unknown!  (65535)
Duplex:  Unknown!  (255)
Port:  Twisted Pair
PHYAD:  0
Transceiver:  internal
Auto-negotiation:  on
Supports Wake-on:  umbg
Wake-on:  g
Current message level:  0x00000007   (7)
Link detected:  no
```

For some reason it doesn't think the cable is plugged in? 

It is plugged into a 100mb switch, perhaps the negotiation is not working? How do I set it to 100mb/full manually?

Thx in advance.

---

### Post by noob12 on 2007-08-08
To answer your question directly, you can use

```

sudo ethtool -s eth0 speed 100 duplex full autoneg off

```

But you may have more fundamental problems, which this won't solve.
In that unfortunate case, showing us the output of
```

uname -r

lspci -nn

sudo lshw -C network

ifconfig -a

```
for starters, would help.

---

### Post by stryc9 on 2007-08-09
You are right, it was no help.  Here is the output you requested, if there is anything else that I can do just ask.

Thank you for your help.

uname -r:

2.6.20-16-generic

lspci -nn:

```
00:00.0 Host bridge [0600]: Intel Corporation 82855PM Processor to I/O Controller [8086:3340] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 82855PM Processor to AGP Controller [8086:3341] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 81)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller [8086:24c3] (rev 01)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 01)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 01)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500] [1002:4c57]
02:00.0 CardBus bridge [0607]: Texas Instruments PCI4520 PC card Cardbus Controller [104c:ac46] (rev 01)
02:00.1 CardBus bridge [0607]: Texas Instruments PCI4520 PC card Cardbus Controller [104c:ac46] (rev 01)
02:01.0 Ethernet controller [0200]: Intel Corporation 82540EP Gigabit Ethernet Controller (Mobile) [8086:101e] (rev 03)
02:02.0 Network controller [0280]: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter [8086:1043] (rev 04)

```

sudo lshw -C network:
```

  *-network:0             
       description: Ethernet interface
       product: 82540EP Gigabit Ethernet Controller (Mobile)
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@02:01.0
       logical name: eth0
       version: 03
       serial: 00:11:25:12:d8:92
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.15-k2-NAPI firmware=N/A latency=64 link=no mingnt=255 multicast=yes port=twisted pair
       resources: iomemory:c0220000-c023ffff iomemory:c0200000-c020ffff ioport:8000-803f irq:11
  *-network:1
       description: Wireless interface
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@02:02.0
       logical name: eth1
       version: 04
       serial: 00:0c:f1:3f:e2:ae
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 ip=192.168.1.101 latency=64 link=yes maxlatency=34 mingnt=2 multicast=yes wireless=IEEE 802.11b
       resources: iomemory:c0214000-c0214fff irq:11
```

ifconifg -a:

```


eth0      Link encap:Ethernet  HWaddr 00:11:25:12:D8:92  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0x8000 Memory:c0220000-c0240000 

eth1      Link encap:Ethernet  HWaddr 00:0C:F1:3F:E2:AE  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:f1ff:fe3f:e2ae/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1696 errors:2 dropped:2 overruns:0 frame:0
          TX packets:1229 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1265977 (1.2 MiB)  TX bytes:183423 (179.1 KiB)
          Interrupt:11 Base address:0xe000 Memory:c0214000-c0214fff 

eth0:avah Link encap:Ethernet  HWaddr 00:11:25:12:D8:92  
          inet addr:169.254.6.204  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Base address:0x8000 Memory:c0220000-c0240000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:516 (516.0 b)  TX bytes:516 (516.0 b)
```

eth1 is my onboard wireless which seems to work just fine.

---

### Post by noob12 on 2007-08-09
Can you also post the output of
```

dmesg | grep -e '(e1000|eth0)'

```

---

### Post by stryc9 on 2007-08-10
that gives me:

[    4.104000] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[   58.408000] ADDRCONF(NETDEV_UP): eth0: link is not ready

---

### Post by noob12 on 2007-08-10
Try this:
```

sudo modprobe -r e1000
sudo modprobe -v e1000 debug=16

```

After that do
```

dmesg | tail -200

```

Let's see it.

We may need to see your full dmesg from the boot onwards.  Let's wait a bit.

---

### Post by stryc9 on 2007-08-11
Here is the dmesg output:
```

[    6.662780] hub 3-0:1.0: 2 ports detected
[    6.673038] Floppy drive(s): fd0 is 1.44M
[    6.713830] FDC 0 is a National Semiconductor PC87306
[    3.652000] Time: acpi_pm clocksource has been installed.
[    3.684000] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[    3.688000] SCSI subsystem initialized
[    3.700000] libata version 2.20 loaded.
[    3.704000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[    3.704000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
[    3.704000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    3.704000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.704000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[    3.704000] ehci_hcd 0000:00:1d.7: debug port 1
[    3.704000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    3.704000] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xc0000000
[    3.708000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.708000] usb usb4: configuration #1 chosen from 1 choice
[    3.708000] hub 4-0:1.0: USB hub found
[    3.708000] hub 4-0:1.0: 6 ports detected
[    3.936000] e1000: 0000:02:01.0: e1000_probe: (PCI:33MHz:32-bit) 00:11:25:12:d8:92
[    3.972000] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[    3.976000] ata_piix 0000:00:1f.1: version 2.10ac1
[    3.976000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[    3.976000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[    3.976000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    3.976000] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011860 irq 14
[    3.976000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011868 irq 15
[    3.976000] scsi0 : ata_piix
[    4.140000] ata1.00: ata_hpa_resize 1: sectors = 117210240, hpa_sectors = 117210240
[    4.140000] ata1.00: ATA-6: FUJITSU MHT2060AH, 006C, max UDMA/100
[    4.140000] ata1.00: 117210240 sectors, multi 16: LBA 
[    4.148000] ata1.00: ata_hpa_resize 1: sectors = 117210240, hpa_sectors = 117210240
[    4.148000] ata1.00: configured for UDMA/100
[    4.148000] scsi1 : ata_piix
[    4.624000] ata2.00: ATAPI, max UDMA/33
[    4.788000] ata2.00: configured for UDMA/33
[    4.788000] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHT2060A 006C PQ: 0 ANSI: 5
[    4.788000] scsi 1:0:0:0: CD-ROM            MATSHITA UJDA755zDVD/CDRW 1.20 PQ: 0 ANSI: 5
[    4.808000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[    4.808000] sda: Write Protect is off
[    4.808000] sda: Mode Sense: 00 3a 00 00
[    4.808000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.808000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[    4.808000] sda: Write Protect is off
[    4.808000] sda: Mode Sense: 00 3a 00 00
[    4.808000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.808000]  sda: sda1 sda2 < sda5 >
[    4.908000] sd 0:0:0:0: Attached scsi disk sda
[    4.916000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.916000] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    4.924000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    4.924000] Uniform CD-ROM driver Revision: 3.20
[    4.924000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    5.160000] Attempting manual resume
[    5.160000] swsusp: Resume From Partition 8:5
[    5.160000] PM: Checking swsusp image.
[    5.160000] PM: Resume from disk failed.
[    5.216000] kjournald starting.  Commit interval 5 seconds
[    5.216000] EXT3-fs: mounted filesystem with ordered data mode.
[   17.232000] NET: Registered protocol family 17
[   17.252000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   17.288000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   17.296000] Linux agpgart interface v0.102 (c) Dave Jones
[   17.308000] agpgart: Detected an Intel 855PM Chipset.
[   17.320000] agpgart: AGP aperture is 256M @ 0xd0000000
[   18.116000] intel_rng: FWH not detected
[   18.140000] Yenta: CardBus bridge found at 0000:02:00.0 [1014:0552]
[   18.140000] Yenta: Using INTVAL to route CSC interrupts to PCI
[   18.140000] Yenta: Routing CardBus interrupts to PCI
[   18.140000] Yenta TI: socket 0000:02:00.0, mfunc 0x01d21b22, devctl 0x64
[   18.372000] Yenta: ISA IRQ mask 0x04b8, PCI irq 11
[   18.372000] Socket status: 30000086
[   18.372000] pcmcia: parent PCI bridge I/O window: 0x4000 - 0x8fff
[   18.372000] cs: IO port probe 0x4000-0x8fff: clean.
[   18.372000] pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xcfffffff
[   18.372000] pcmcia: parent PCI bridge Memory window: 0xe8000000 - 0xefffffff
[   18.372000] Yenta: CardBus bridge found at 0000:02:00.1 [1014:0552]
[   18.372000] Yenta: Using INTVAL to route CSC interrupts to PCI
[   18.372000] Yenta: Routing CardBus interrupts to PCI
[   18.372000] Yenta TI: socket 0000:02:00.1, mfunc 0x01d21b22, devctl 0x64
[   18.444000] input: PC Speaker as /class/input/input2
[   18.468000] ieee80211_crypt: registered algorithm 'NULL'
[   18.468000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   18.468000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   18.512000] iTCO_vendor_support: vendor-support=0
[   18.512000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   18.532000] parport: PnPBIOS parport detected.
[   18.532000] parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE]
[   18.604000] Yenta: ISA IRQ mask 0x0438, PCI irq 11
[   18.604000] Socket status: 30000086
[   18.604000] pcmcia: parent PCI bridge I/O window: 0x4000 - 0x8fff
[   18.604000] cs: IO port probe 0x4000-0x8fff: clean.
[   18.604000] pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xcfffffff
[   18.604000] pcmcia: parent PCI bridge Memory window: 0xe8000000 - 0xefffffff
[   18.608000] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2
[   18.608000] ipw2100: Copyright(c) 2003-2006 Intel Corporation
[   18.608000] ACPI: PCI Interrupt 0000:02:02.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   18.608000] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
[   18.836000] irda_init()
[   18.836000] NET: Registered protocol family 23
[   19.000000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x2c6ab1, caps: 0x884793/0x0
[   19.000000] serio: Synaptics pass-through port at isa0060/serio1/input0
[   19.048000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   19.052000] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x1060)
[   19.052000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   19.052000] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 3.
[   19.052000] nsc-ircc, chip->init
[   19.052000] nsc-ircc, Found chip at base=0x02e
[   19.052000] nsc-ircc, driver loaded (Dag Brattli)
[   19.052000] nsc_ircc_open(), can't get iobase of 0x2f8
[   19.052000] nsc-ircc, Found chip at base=0x02e
[   19.052000] nsc-ircc, driver loaded (Dag Brattli)
[   19.052000] nsc_ircc_open(), can't get iobase of 0x2f8
[   19.052000] pnp: Device 00:0c disabled.
[   19.152000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[   19.152000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   19.432000] cs: IO port probe 0x100-0x3af: clean.
[   19.432000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   19.432000] cs: IO port probe 0x820-0x8ff: clean.
[   19.436000] cs: IO port probe 0xc00-0xcf7: clean.
[   19.436000] cs: IO port probe 0xa00-0xaff: clean.
[   19.436000] cs: IO port probe 0x100-0x3af: clean.
[   19.436000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   19.436000] cs: IO port probe 0x820-0x8ff: clean.
[   19.436000] cs: IO port probe 0xc00-0xcf7: clean.
[   19.436000] cs: IO port probe 0xa00-0xaff: clean.
[   19.972000] intel8x0_measure_ac97_clock: measured 55206 usecs
[   19.972000] intel8x0: clocking to 48000
[   20.084000] fuse init (API version 7.8)
[   20.108000] lp0: using parport0 (interrupt-driven).
[   20.132000] Adding 2441840k swap on /dev/disk/by-uuid/f1cc668d-ceb9-4aca-aa06-2f1c39a03ed0.  Priority:-1 extents:1 across:2441840k
[   20.272000] EXT3 FS on sda1, internal journal
[   24.052000] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   24.312000] input: TPPS/2 IBM TrackPoint as /class/input/input4
[   24.680000] ibm_acpi: ThinkPad EC firmware 1RHT71WW-3.04
[   24.680000] ibm_acpi: IBM ThinkPad ACPI Extras v0.13
[   24.680000] ibm_acpi: http://ibm-acpi.sf.net/
[   24.740000] input: Power Button (FF) as /class/input/input5
[   24.744000] ACPI: Power Button (FF) [PWRF]
[   24.784000] input: Lid Switch as /class/input/input6
[   24.788000] ACPI: Lid Switch [LID]
[   24.832000] input: Sleep Button (CM) as /class/input/input7
[   24.832000] ACPI: Sleep Button (CM) [SLPB]
[   24.880000] ACPI: ACPI Dock Station Driver 
[   24.896000] Using specific hotkey driver
[   24.932000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   25.032000] ACPI: AC Adapter [AC] (on-line)
[   25.056000] ACPI: Battery Slot [BAT0] (battery present)
[   25.124000] pcc_acpi: loading...
[   27.960000] ttyS1: LSR safety check engaged!
[   30.476000] [drm] Initialized drm 1.1.0 20060810
[   30.496000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   30.500000] [drm] Initialized radeon 1.25.0 20060524 on minor 0
[   31.236000] ppdev: user-space parallel port driver
[   32.152000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   32.152000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[   32.152000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
[   32.196000] IBM machine detected. Enabling interrupts during APM calls.
[   32.196000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   32.196000] apm: overridden by ACPI.
[   32.352000] Non-volatile memory driver v1.2
[   32.408000] input: /usr/sbin/thinkpad-keys as /class/input/input8
[   32.420000] [drm] Setting GART location based on new memory map
[   32.420000] [drm] writeback test succeeded in 2 usecs
[   32.756000] Bluetooth: Core ver 2.11
[   32.756000] NET: Registered protocol family 31
[   32.756000] Bluetooth: HCI device and connection manager initialized
[   32.756000] Bluetooth: HCI socket layer initialized
[   32.796000] Bluetooth: L2CAP ver 2.8
[   32.796000] Bluetooth: L2CAP socket layer initialized
[   32.920000] Bluetooth: RFCOMM socket layer initialized
[   32.920000] Bluetooth: RFCOMM TTY layer initialized
[   32.920000] Bluetooth: RFCOMM ver 1.8
[   50.644000] NET: Registered protocol family 10
[   50.644000] lo: Disabled Privacy Extensions
[   50.644000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   50.644000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   68.912000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   69.864000] ieee80211_crypt: registered algorithm 'TKIP'
[   88.496000] eth1: no IPv6 routers present
[  158.508000] ACPI: PCI interrupt for device 0000:02:01.0 disabled
[  217.624000] Intel(R) PRO/1000 Network Driver - version 7.3.15-k2-NAPI
[  217.624000] Copyright (c) 1999-2006 Intel Corporation.
[  217.624000] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[  217.876000] e1000: 0000:02:01.0: e1000_probe: (PCI:33MHz:32-bit) 00:11:25:12:d8:92
[  217.912000] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[  217.944000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  270.976000] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex
[  270.976000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  280.080000] e1000: eth0: e1000_watchdog: NIC Link is Down
[  281.340000] eth0: no IPv6 routers present
[  281.712000] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex
[  281.904000] e1000: eth0: e1000_watchdog: NIC Link is Down
[  296.072000] ACPI: PCI interrupt for device 0000:02:01.0 disabled
[  308.064000] Intel(R) PRO/1000 Network Driver - version 7.3.15-k2-NAPI
[  308.064000] Copyright (c) 1999-2006 Intel Corporation.
[  308.068000] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[  308.324000] e1000: 0000:02:01.0: e1000_probe: (PCI:33MHz:32-bit) 00:11:25:12:d8:92
[  308.360000] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[  308.392000] ADDRCONF(NETDEV_UP): eth0: link is not ready
```

EDIT: The link seems to be going up and down for whatever reason.  Right now it seems to be up all the time even though all I have done since the above output is reboot.  

Thank you for your assistance.

---

### Post by noob12 on 2007-08-11
OK.  I think the reinsertion of the driver module starts at the timestamp [217.624000] . I was looking for some  errors.  The only surprise is that the link comes up momentarily but then goes back down.  It looks like maybe you repeated the commands one more time.

Your edit comment says it is now up for a sustained period after a reboot.  I doubt this is anything we triggered by the reloading.  You should check the physical connection's stability right at the jacks on both sides of the cable.  In other words "jiggle it" and see if it goes in and out.  It might also be due to some timing issue in the driver.  We'll have to see if anyone else has something to say about that.

I won't be around to read postings for the weekend so I hope it holds for you till then.

---

