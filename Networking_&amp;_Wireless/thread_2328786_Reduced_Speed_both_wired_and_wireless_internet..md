---
title: "Reduced Speed both wired and wireless internet."
date: 2016-06-24
forum: Networking &amp; Wireless
---

### Post by ken55 on 2016-06-24
hwinfo:

```
[Created at pci.366]  Unique ID: 8otl.1D6Pfj_obn7
  SysFS ID: /devices/pci0000:00/0000:00:04.0
  SysFS BusID: 0000:00:04.0
  Hardware Class: bridge
  Model: "nVidia MCP61 PCI bridge"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x03f3 "MCP61 PCI bridge"
  SubVendor: pci 0x10de "nVidia Corporation"
  SubDevice: pci 0xcb84 
  Revision: 0xa1
  Module Alias: "pci:v000010DEd000003F3sv000010DEsd0000CB84bc06sc04i01"
  Config Status: cfg=new, avail=yes, need=no, active=unknown


17: PCI 05.0: 0403 Audio device
  [Created at pci.366]
  Unique ID: CvwD.Rah7M_6kKJE
  SysFS ID: /devices/pci0000:00/0000:00:05.0
  SysFS BusID: 0000:00:05.0
  Hardware Class: sound
  Model: "nVidia MCP61 High Definition Audio"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x03f0 "MCP61 High Definition Audio"
  SubVendor: pci 0x105b "Foxconn International, Inc."
  SubDevice: pci 0x0d15 
  Revision: 0xa2
  Driver: "snd_hda_intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xfe028000-0xfe02bfff (rw,non-prefetchable)
  IRQ: 23 (875 events)
  Module Alias: "pci:v000010DEd000003F0sv0000105Bsd00000D15bc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown


18: PCI 06.0: 0101 IDE interface
  [Created at pci.366]
  Unique ID: H0_h.SyMN5K152U4
  SysFS ID: /devices/pci0000:00/0000:00:06.0
  SysFS BusID: 0000:00:06.0
  Hardware Class: storage
  Model: "nVidia MCP61 IDE"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x03ec "MCP61 IDE"
  SubVendor: pci 0x105b "Foxconn International, Inc."
  SubDevice: pci 0x0d15 
  Revision: 0xa2
  Driver: "pata_amd"
  Driver Modules: "pata_amd"
  I/O Ports: 0x1f0-0x1f7 (rw)
  I/O Port: 0x3f6 (rw)
  I/O Ports: 0x170-0x177 (rw)
  I/O Port: 0x376 (rw)
  I/O Ports: 0xf000-0xf00f (rw)
  Module Alias: "pci:v000010DEd000003ECsv0000105Bsd00000D15bc01sc01i8A"
  Driver Info #0:
    Driver Status: pata_amd is active
    Driver Activation Cmd: "modprobe pata_amd"
  Driver Info #1:
    Driver Status: pata_acpi is active
    Driver Activation Cmd: "modprobe pata_acpi"
  Config Status: cfg=new, avail=yes, need=no, active=unknown


19: PCI 07.0: 0200 Ethernet controller
  [Created at pci.366]
  Unique ID: IxXX.LZJQZ1iMpA0
  SysFS ID: /devices/pci0000:00/0000:00:07.0
  SysFS BusID: 0000:00:07.0
  Hardware Class: network
  Model: "nVidia MCP61 Ethernet"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x03ef "MCP61 Ethernet"
  SubVendor: pci 0x105b "Foxconn International, Inc."
  SubDevice: pci 0x0d15 
  Revision: 0xa2
  Driver: "forcedeth"
  Driver Modules: "forcedeth"
  Device File: enp0s7
  Memory Range: 0xfe02d000-0xfe02dfff (rw,non-prefetchable)
  I/O Ports: 0xec00-0xec07 (rw)
  IRQ: 29 (no events)
  HW Address: 00:1c:25:07:23:46
  Link detected: no
  Module Alias: "pci:v000010DEd000003EFsv0000105Bsd00000D15bc06sc80i00"
  Driver Info #0:
    Driver Status: forcedeth is active
    Driver Activation Cmd: "modprobe forcedeth"
  Config Status: cfg=new, avail=yes, need=no, active=unknown


20: PCI 08.0: 0101 IDE interface
  [Created at pci.366]
  Unique ID: RE4e.X9+0cf88bj4
  SysFS ID: /devices/pci0000:00/0000:00:08.0
  SysFS BusID: 0000:00:08.0
  Hardware Class: storage
  Model: "nVidia MCP61 SATA Controller"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x03f6 "MCP61 SATA Controller"
  SubVendor: pci 0x105b "Foxconn International, Inc."
  SubDevice: pci 0x0d15 
  Revision: 0xa2
  Driver: "sata_nv"
  Driver Modules: "sata_nv"
  I/O Ports: 0x9f0-0x9f7 (rw)
  I/O Ports: 0xbf0-0xbf3 (rw)
  I/O Ports: 0x970-0x977 (rw)
  I/O Ports: 0xb70-0xb73 (rw)
  I/O Ports: 0xd800-0xd80f (rw)
  Memory Range: 0xfe02c000-0xfe02cfff (rw,non-prefetchable)
  IRQ: 21 (49982 events)
  Module Alias: "pci:v000010DEd000003F6sv0000105Bsd00000D15bc01sc01i85"
  Driver Info #0:
    Driver Status: sata_nv is active
    Driver Activation Cmd: "modprobe sata_nv"
  Driver Info #1:
    Driver Status: pata_acpi is active
    Driver Activation Cmd: "modprobe pata_acpi"
  Config Status: cfg=new, avail=yes, need=no, active=unknown


21: PCI 09.0: 0604 PCI bridge (Normal decode)
  [Created at pci.366]
  Unique ID: WL76.lW0IfrjOTIA
  SysFS ID: /devices/pci0000:00/0000:00:09.0
  SysFS BusID: 0000:00:09.0
  Hardware Class: bridge
  Model: "nVidia MCP61 PCI Express bridge"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x03e8 "MCP61 PCI Express bridge"
  SubVendor: pci 0x10de "nVidia Corporation"
  SubDevice: pci 0x0000 
  Revision: 0xa2
  Driver: "pcieport"
  IRQ: 24 (no events)
  Module Alias: "pci:v000010DEd000003E8sv000010DEsd00000000bc06sc04i00"
  Driver Info #0:
    Driver Status: shpchp is active
    Driver Activation Cmd: "modprobe shpchp"
  Config Status: cfg=new, avail=yes, need=no, active=unknown


22: PCI 18.0: 0600 Host bridge
  [Created at pci.366]
  Unique ID: fiDB.ptk_g9XAN03
  SysFS ID: /devices/pci0000:00/0000:00:18.0
  SysFS BusID: 0000:00:18.0
  Hardware Class: bridge
  Model: "AMD K8 [Athlon64/Opteron] HyperTransport Technology Configuration"
  Vendor: pci 0x1022 "AMD"
  Device: pci 0x1100 "K8 [Athlon64/Opteron] HyperTransport Technology Configuration"
  Module Alias: "pci:v00001022d00001100sv00000000sd00000000bc06sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown


23: PCI 18.1: 0600 Host bridge
  [Created at pci.366]
  Unique ID: W1j0.KIhk9ketuO3
  SysFS ID: /devices/pci0000:00/0000:00:18.1
  SysFS BusID: 0000:00:18.1
  Hardware Class: bridge
  Model: "AMD K8 [Athlon64/Opteron] Address Map"
  Vendor: pci 0x1022 "AMD"
  Device: pci 0x1101 "K8 [Athlon64/Opteron] Address Map"
  Module Alias: "pci:v00001022d00001101sv00000000sd00000000bc06sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown


24: PCI 18.2: 0600 Host bridge
  [Created at pci.366]
  Unique ID: OMCs.ridUeImaQn3
  SysFS ID: /devices/pci0000:00/0000:00:18.2
  SysFS BusID: 0000:00:18.2
  Hardware Class: bridge
  Model: "AMD K8 [Athlon64/Opteron] DRAM Controller"
  Vendor: pci 0x1022 "AMD"
  Device: pci 0x1102 "K8 [Athlon64/Opteron] DRAM Controller"
  Module Alias: "pci:v00001022d00001102sv00000000sd00000000bc06sc00i00"
  Driver Info #0:
    Driver Status: amd64_edac_mod is not active
    Driver Activation Cmd: "modprobe amd64_edac_mod"
  Config Status: cfg=new, avail=yes, need=no, active=unknown


25: PCI 18.3: 0600 Host bridge
  [Created at pci.366]
  Unique ID: Fhhh.M7aE7ttHy94
  SysFS ID: /devices/pci0000:00/0000:00:18.3
  SysFS BusID: 0000:00:18.3
  Hardware Class: bridge
  Model: "AMD K8 [Athlon64/Opteron] Miscellaneous Control"
  Vendor: pci 0x1022 "AMD"
  Device: pci 0x1103 "K8 [Athlon64/Opteron] Miscellaneous Control"
  Driver: "k8temp"
  Driver Modules: "k8temp"
  Module Alias: "pci:v00001022d00001103sv00000000sd00000000bc06sc00i00"
  Driver Info #0:
    Driver Status: k8temp is active
    Driver Activation Cmd: "modprobe k8temp"
  Config Status: cfg=new, avail=yes, need=no, active=unknown


26: PCI 0b.0: 0604 PCI bridge (Normal decode)
  [Created at pci.366]
  Unique ID: gZD2.Gxy18Qr5+gA
  SysFS ID: /devices/pci0000:00/0000:00:0b.0
  SysFS BusID: 0000:00:0b.0
  Hardware Class: bridge
  Model: "nVidia MCP61 PCI Express bridge"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x03e9 "MCP61 PCI Express bridge"
  SubVendor: pci 0x10de "nVidia Corporation"
  SubDevice: pci 0x0000 
  Revision: 0xa2
  Driver: "pcieport"
  IRQ: 25 (no events)
  Module Alias: "pci:v000010DEd000003E9sv000010DEsd00000000bc06sc04i00"
  Driver Info #0:
    Driver Status: shpchp is active
    Driver Activation Cmd: "modprobe shpchp"
  Config Status: cfg=new, avail=yes, need=no, active=unknown


27: PCI 0c.0: 0604 PCI bridge (Normal decode)
  [Created at pci.366]
  Unique ID: lgGW.Gxy18Qr5+gA
  SysFS ID: /devices/pci0000:00/0000:00:0c.0
  SysFS BusID: 0000:00:0c.0
  Hardware Class: bridge
  Model: "nVidia MCP61 PCI Express bridge"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x03e9 "MCP61 PCI Express bridge"
  SubVendor: pci 0x10de "nVidia Corporation"
  SubDevice: pci 0x0000 
  Revision: 0xa2
  Driver: "pcieport"
  IRQ: 26 (no events)
  Module Alias: "pci:v000010DEd000003E9sv000010DEsd00000000bc06sc04i00"
  Driver Info #0:
    Driver Status: shpchp is active
    Driver Activation Cmd: "modprobe shpchp"
  Config Status: cfg=new, avail=yes, need=no, active=unknown


28: PCI 107.0: 0780 Communication controller
  [Created at pci.366]
  Unique ID: 2_DJ.yKGEnofW4y9
  Parent ID: 8otl.1D6Pfj_obn7
  SysFS ID: /devices/pci0000:00/0000:00:04.0/0000:01:07.0
  SysFS BusID: 0000:01:07.0
  Hardware Class: unknown
  Model: "Conexant Communication controller"
  Vendor: pci 0x14f1 "Conexant Systems, Inc."
  Device: pci 0x2f40 
  SubVendor: pci 0x14f1 "Conexant Systems, Inc."
  SubDevice: pci 0x2000 
  Memory Range: 0xfdef0000-0xfdefffff (rw,non-prefetchable)
  I/O Ports: 0xcc00-0xcc07 (rw)
  IRQ: 5 (no events)
  Module Alias: "pci:v000014F1d00002F40sv000014F1sd00002000bc07sc80i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #16 (PCI bridge)


29: PCI 200.0: 0300 VGA compatible controller (VGA)
  [Created at pci.366]
  Unique ID: B35A.4Thn76XFb02
  Parent ID: WL76.lW0IfrjOTIA
  SysFS ID: /devices/pci0000:00/0000:00:09.0/0000:02:00.0
  SysFS BusID: 0000:02:00.0
  Hardware Class: graphics card
  Model: "ATI RV610 [Radeon HD 2400 PRO]"
  Vendor: pci 0x1002 "ATI Technologies Inc"
  Device: pci 0x94c3 "RV610 [Radeon HD 2400 PRO]"
  SubVendor: pci 0x1545 "VISIONTEK"
  SubDevice: pci 0x3210 
  Driver: "radeon"
  Driver Modules: "drm"
  Memory Range: 0xe0000000-0xefffffff (ro,non-prefetchable)
  Memory Range: 0xfdde0000-0xfddeffff (rw,non-prefetchable)
  I/O Ports: 0xbc00-0xbcff (rw)
  Memory Range: 0xfdd00000-0xfdd1ffff (ro,non-prefetchable,disabled)
  IRQ: 27 (124281 events)
  I/O Ports: 0x3c0-0x3df (rw)
  Module Alias: "pci:v00001002d000094C3sv00001545sd00003210bc03sc00i00"
  Driver Info #0:
    Driver Status: radeon is active
    Driver Activation Cmd: "modprobe radeon"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #21 (PCI bridge)


30: PCI 200.1: 0403 Audio device
  [Created at pci.366]
  Unique ID: 2Oa+.JTx1064b7W4
  Parent ID: WL76.lW0IfrjOTIA
  SysFS ID: /devices/pci0000:00/0000:00:09.0/0000:02:00.1
  SysFS BusID: 0000:02:00.1
  Hardware Class: sound
  Model: "ATI RV610 HDMI Audio [Radeon HD 2350/2400 Series]"
  Vendor: pci 0x1002 "ATI Technologies Inc"
  Device: pci 0xaa10 "RV610 HDMI Audio [Radeon HD 2350/2400 Series]"
  SubVendor: pci 0x1545 "VISIONTEK"
  SubDevice: pci 0xaa10 
  Driver: "snd_hda_intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xfddfc000-0xfddfffff (rw,non-prefetchable)
  IRQ: 28 (179 events)
  Module Alias: "pci:v00001002d0000AA10sv00001545sd0000AA10bc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #21 (PCI bridge)


31: None 00.0: 10002 LCD Monitor
  [Created at monitor.125]
  Unique ID: rdCR.XG06SWu7AQ7
  Parent ID: B35A.4Thn76XFb02
  Hardware Class: monitor
  Model: "Acer S231HL"
  Vendor: ACR 
  Device: eisa 0x01a6 "Acer S231HL"
  Serial ID: "LNZ080024210"
  Resolution: 720x400@70Hz
  Resolution: 640x480@60Hz
  Resolution: 640x480@67Hz
  Resolution: 640x480@72Hz
  Resolution: 640x480@75Hz
  Resolution: 800x600@56Hz
  Resolution: 800x600@60Hz
  Resolution: 800x600@72Hz
  Resolution: 800x600@75Hz
  Resolution: 832x624@75Hz
  Resolution: 1024x768@60Hz
  Resolution: 1024x768@70Hz
  Resolution: 1024x768@75Hz
  Resolution: 1280x1024@75Hz
  Resolution: 1280x720@60Hz
  Resolution: 1280x960@60Hz
  Resolution: 1152x864@75Hz
  Resolution: 1280x1024@60Hz
  Resolution: 1920x1080@60Hz
  Size: 510x287 mm
  Year of Manufacture: 2010
  Week of Manufacture: 34
  Detailed Timings #0:
     Resolution: 1920x1080
     Horizontal: 1920 2008 2052 2200 (+88 +132 +280) +hsync
       Vertical: 1080 1084 1089 1125 (+4 +9 +45) +vsync
    Frequencies: 148.50 MHz, 67.50 kHz, 60.00 Hz
  Driver Info #0:
    Max. Resolution: 1920x1080
    Vert. Sync Range: 50-75 Hz
    Hor. Sync Range: 30-80 kHz
    Bandwidth: 148 MHz
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #29 (VGA compatible controller)


32: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  Unique ID: z9pp.B+yZ9Ve8gC1
  SysFS ID: /devices/pnp0/00:00
  SysFS BusID: 00:00
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0c02 
  Config Status: cfg=new, avail=yes, need=no, active=unknown


33: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  Unique ID: QL3u.B+yZ9Ve8gC1
  SysFS ID: /devices/pnp0/00:01
  SysFS BusID: 00:01
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0c02 
  Config Status: cfg=new, avail=yes, need=no, active=unknown


34: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  Unique ID: tWJy.WYwRElrJa93
  SysFS ID: /devices/pnp0/00:02
  SysFS BusID: 00:02
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0b00 
  Config Status: cfg=new, avail=yes, need=no, active=unknown


35: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  Unique ID: KiZ0.BuKI+1soRmD
  SysFS ID: /devices/pnp0/00:03
  SysFS BusID: 00:03
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0501 
  Config Status: cfg=new, avail=yes, need=no, active=unknown


36: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  Unique ID: ntp4.13ubA72AEK3
  SysFS ID: /devices/pnp0/00:04
  SysFS BusID: 00:04
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0400 
  Config Status: cfg=new, avail=yes, need=no, active=unknown


37: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  Unique ID: E349.B+yZ9Ve8gC1
  SysFS ID: /devices/pnp0/00:05
  SysFS BusID: 00:05
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0c02 
  Config Status: cfg=new, avail=yes, need=no, active=unknown


38: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  Unique ID: hEKD.gNN83gfynbD
  SysFS ID: /devices/pnp0/00:06
  SysFS BusID: 00:06
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0c01 
  Config Status: cfg=new, avail=yes, need=no, active=unknown


39: None 00.0: 0700 Serial controller
  [Created at misc.448]
  Unique ID: rdCR.7RG8lK_UzJ9
  Hardware Class: unknown
  Model: "Serial controller"
  I/O Ports: 0x2f8-0x2ff (rw)
  I/O Ports: 0x3f8-0x3ff (rw)
  Config Status: cfg=new, avail=yes, need=no, active=unknown


40: IDE 200.0: 10600 Disk
  [Created at block.245]
  Unique ID: 3OOL.ZSgVl1zsw+D
  Parent ID: RE4e.X9+0cf88bj4
  SysFS ID: /class/block/sda
  SysFS BusID: 2:0:0:0
  SysFS Device Link: /devices/pci0000:00/0000:00:08.0/ata3/host2/target2:0:0/2:0:0:0
  Hardware Class: disk
  Model: "WDC WD1200JS-00N"
  Vendor: "WDC"
  Device: "WD1200JS-00N"
  Revision: "2E02"
  Driver: "sata_nv", "sd"
  Driver Modules: "sata_nv"
  Device File: /dev/sda
  Device Files: /dev/sda, /dev/disk/by-id/ata-WDC_WD1200JS-00NCB1_WD-WCANM5748983, /dev/disk/by-path/pci-0000:00:08.0-ata-1
  Device Number: block 8:0-8:15
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #20 (IDE interface)


41: None 00.0: 11300 Partition
  [Created at block.434]
  Unique ID: bdUI.SE1wIdpsiiC
  Parent ID: 3OOL.ZSgVl1zsw+D
  SysFS ID: /class/block/sda/sda1
  Hardware Class: partition
  Model: "Partition"
  Device File: /dev/sda1
  Device Files: /dev/sda1, /dev/disk/by-id/ata-WDC_WD1200JS-00NCB1_WD-WCANM5748983-part1, /dev/disk/by-path/pci-0000:00:08.0-ata-1-part1, /dev/disk/by-uuid/eec61421-6e41-475e-b6cd-e59515ab4e4c
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #40 (Disk)


42: None 00.0: 11300 Partition
  [Created at block.434]
  Unique ID: 2pkM.SE1wIdpsiiC
  Parent ID: 3OOL.ZSgVl1zsw+D
  SysFS ID: /class/block/sda/sda2
  Hardware Class: partition
  Model: "Partition"
  Device File: /dev/sda2
  Device Files: /dev/sda2, /dev/disk/by-id/ata-WDC_WD1200JS-00NCB1_WD-WCANM5748983-part2, /dev/disk/by-path/pci-0000:00:08.0-ata-1-part2
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #40 (Disk)


43: None 00.0: 11300 Partition
  [Created at block.434]
  Unique ID: QLVZ.SE1wIdpsiiC
  Parent ID: 3OOL.ZSgVl1zsw+D
  SysFS ID: /class/block/sda/sda5
  Hardware Class: partition
  Model: "Partition"
  Device File: /dev/sda5
  Device Files: /dev/sda5, /dev/disk/by-id/ata-WDC_WD1200JS-00NCB1_WD-WCANM5748983-part5, /dev/disk/by-path/pci-0000:00:08.0-ata-1-part5, /dev/disk/by-uuid/dd9ebd83-7556-49b4-a7b0-e0da09a05bc0
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #40 (Disk)


44: IDE 300.0: 10600 Disk
  [Created at block.245]
  Unique ID: WZeP.w+xYkD2Ee_7
  Parent ID: RE4e.X9+0cf88bj4
  SysFS ID: /class/block/sdb
  SysFS BusID: 3:0:0:0
  SysFS Device Link: /devices/pci0000:00/0000:00:08.0/ata4/host3/target3:0:0/3:0:0:0
  Hardware Class: disk
  Model: "SAMSUNG HD080HJ/"
  Vendor: "SAMSUNG"
  Device: "HD080HJ/"
  Revision: "0-34"
  Driver: "sata_nv", "sd"
  Driver Modules: "sata_nv"
  Device File: /dev/sdb
  Device Files: /dev/sdb, /dev/disk/by-id/ata-SAMSUNG_HD080HJ_P_S0DEJ1IL825794, /dev/disk/by-id/wwn-0x50000f000bde0100, /dev/disk/by-path/pci-0000:00:08.0-ata-2
  Device Number: block 8:16-8:31
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #20 (IDE interface)


45: None 00.0: 11300 Partition
  [Created at block.434]
  Unique ID: h4pj.SE1wIdpsiiC
  Parent ID: WZeP.w+xYkD2Ee_7
  SysFS ID: /class/block/sdb/sdb1
  Hardware Class: partition
  Model: "Partition"
  Device File: /dev/sdb1
  Device Files: /dev/sdb1, /dev/disk/by-id/ata-SAMSUNG_HD080HJ_P_S0DEJ1IL825794-part1, /dev/disk/by-id/wwn-0x50000f000bde0100-part1, /dev/disk/by-label/Hdd2, /dev/disk/by-path/pci-0000:00:08.0-ata-2-part1, /dev/disk/by-uuid/07ab1396-5594-4e6a-be9b-e5023aae15d3
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #44 (Disk)


46: SCSI 400.0: 10600 Disk
  [Created at block.245]
  Unique ID: 2UT6.fD7XDEsZgjF
  Parent ID: ruGf.5Ic7jN+tRT5
  SysFS ID: /class/block/sdc
  SysFS BusID: 4:0:0:0
  SysFS Device Link: /devices/pci0000:00/0000:00:02.1/usb1/1-3/1-3:1.0/host4/target4:0:0/4:0:0:0
  Hardware Class: disk
  Model: "WD Ext HDD 1021"
  Vendor: usb 0x1058 "WD"
  Device: usb 0x1021 "Ext HDD 1021"
  Revision: "2021"
  Serial ID: "5743415A414A363035313530"
  Driver: "usb-storage", "sd"
  Driver Modules: "usb_storage"
  Device File: /dev/sdc (/dev/sg3)
  Device Files: /dev/sdc, /dev/disk/by-id/ata-WDC_WD20EARX-00PASB0_WD-WCAZAJ605150, /dev/disk/by-id/wwn-0x50014ee25cefb170, /dev/disk/by-path/pci-0000:00:02.1-usb-0:3:1.0-scsi-0:0:0:0
  Device Number: block 8:32-8:47 (char 21:3)
  Speed: 480 Mbps
  Module Alias: "usb:v1058p1021d2021dc00dsc00dp00ic08isc06ip50in00"
  Driver Info #0:
    Driver Status: uas is active
    Driver Activation Cmd: "modprobe uas"
  Driver Info #1:
    Driver Status: usb_storage is active
    Driver Activation Cmd: "modprobe usb_storage"
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #15 (USB Controller)


47: None 00.0: 11300 Partition
  [Created at block.434]
  Unique ID: mX79.SE1wIdpsiiC
  Parent ID: 2UT6.fD7XDEsZgjF
  SysFS ID: /class/block/sdc/sdc1
  Hardware Class: partition
  Model: "Partition"
  Device File: /dev/sdc1
  Device Files: /dev/sdc1, /dev/disk/by-id/ata-WDC_WD20EARX-00PASB0_WD-WCAZAJ605150-part1, /dev/disk/by-id/wwn-0x50014ee25cefb170-part1, /dev/disk/by-label/TV\x20Shows, /dev/disk/by-path/pci-0000:00:02.1-usb-0:3:1.0-scsi-0:0:0:0-part1, /dev/disk/by-uuid/6FA208C46EBD440D
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #46 (Disk)


48: SCSI 00.0: 10602 CD-ROM (DVD)
  [Created at block.249]
  Unique ID: KD9E.RNza14CDlk1
  Parent ID: H0_h.SyMN5K152U4
  SysFS ID: /class/block/sr0
  SysFS BusID: 0:0:0:0
  SysFS Device Link: /devices/pci0000:00/0000:00:06.0/ata1/host0/target0:0:0/0:0:0:0
  Hardware Class: cdrom
  Model: "HL-DT-ST DVDRAM GSA-H40N"
  Vendor: "HL-DT-ST"
  Device: "DVDRAM GSA-H40N"
  Revision: "RG01"
  Driver: "pata_amd", "sr"
  Driver Modules: "pata_amd"
  Device File: /dev/sr0 (/dev/sg0)
  Device Files: /dev/sr0, /dev/cdrom, /dev/cdrw, /dev/disk/by-id/ata-HL-DT-ST_DVDRAM_GSA-H40N_M0075TD3440, /dev/disk/by-label/Realtek_Driver, /dev/disk/by-path/pci-0000:00:06.0-ata-1, /dev/disk/by-uuid/2016-05-03-21-40-26-00, /dev/dvd, /dev/dvdrw
  Device Number: block 11:0 (char 21:0)
  Features: CD-R, CD-RW, DVD, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL, DVD-RAM, MRW, MRW-W
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #18 (IDE interface)
  Drive Speed: 16
  Volume ID: "REALTEK_DRIVER"
  Application: "ULTRAISO V9.6 CD & DVD CREATOR, (C) EZB SYSTEMS, INC."
  Creation date: "2016050321402600"


49: None 00.0: 10600 Disk
  [Created at block.245]
  Unique ID: CWFH.Fxp0d3BezAE
  SysFS ID: /class/block/ram0
  Hardware Class: disk
  Model: "Disk"
  Device File: /dev/ram0
  Device Number: block 1:0
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown


50: None 00.0: 10600 Disk
  [Created at block.245]
  Unique ID: ghVL.Fxp0d3BezAE
  SysFS ID: /class/block/ram1
  Hardware Class: disk
  Model: "Disk"
  Device File: /dev/ram1
  Device Number: block 1:1
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown


51: None 00.0: 10600 Disk
  [Created at block.245]
  Unique ID: 7tlP.Fxp0d3BezAE
  SysFS ID: /class/block/ram2
  Hardware Class: disk
  Model: "Disk"
  Device File: /dev/ram2
  Device Number: block 1:2
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown


52: None 00.0: 10600 Disk
  [Created at block.245]
  Unique ID: a20U.Fxp0d3BezAE
  SysFS ID: /class/block/ram3
  Hardware Class: disk
  Model: "Disk"
  Device File: /dev/ram3
  Device Number: block 1:3
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown


53: None 00.0: 10600 Disk
  [Created at block.245]
  Unique ID: 1EGY.Fxp0d3BezAE
  SysFS ID: /class/block/ram4
  Hardware Class: disk
  Model: "Disk"
  Device File: /dev/ram4
  Device Number: block 1:4
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown


54: None 00.0: 10600 Disk
  [Created at block.245]
  Unique ID: UPWc.Fxp0d3BezAE
  SysFS ID: /class/block/ram5
  Hardware Class: disk
  Model: "Disk"
  Device File: /dev/ram5
  Device Number: block 1:5
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown


55: None 00.0: 10600 Disk
  [Created at block.245]
  Unique ID: xamg.Fxp0d3BezAE
  SysFS ID: /class/block/ram6
  Hardware Class: disk
  Model: "Disk"
  Device File: /dev/ram6
  Device Number: block 1:6
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown


56: None 00.0: 10600 Disk
  [Created at block.245]
  Unique ID: d1y9.Fxp0d3BezAE
  SysFS ID: /class/block/ram7
  Hardware Class: disk
  Model: "Disk"
  Device File: /dev/ram7
  Device Number: block 1:7
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown


57: None 00.0: 10600 Disk
  [Created at block.245]
  Unique ID: 4DCE.Fxp0d3BezAE
  SysFS ID: /class/block/ram8
  Hardware Class: disk
  Model: "Disk"
  Device File: /dev/ram8
  Device Number: block 1:8
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown


58: None 00.0: 10600 Disk
  [Created at block.245]
  Unique ID: XOSI.Fxp0d3BezAE
  SysFS ID: /class/block/ram9
  Hardware Class: disk
  Model: "Disk"
  Device File: /dev/ram9
  Device Number: block 1:9
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown


59: None 00.0: 10600 Disk
  [Created at block.245]
  Unique ID: 2K8Y.Fxp0d3BezAE
  SysFS ID: /class/block/ram10
  Hardware Class: disk
  Model: "Disk"
  Device File: /dev/ram10
  Device Number: block 1:10
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown


60: None 00.0: 10600 Disk
  [Created at block.245]
  Unique ID: VVOc.Fxp0d3BezAE
  SysFS ID: /class/block/ram11
  Hardware Class: disk
  Model: "Disk"
  Device File: /dev/ram11
  Device Number: block 1:11
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown


61: None 00.0: 10600 Disk
  [Created at block.245]
  Unique ID: ygeg.Fxp0d3BezAE
  SysFS ID: /class/block/ram12
  Hardware Class: disk
  Model: "Disk"
  Device File: /dev/ram12
  Device Number: block 1:12
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown


62: None 00.0: 10600 Disk
  [Created at block.245]
  Unique ID: Psuk.Fxp0d3BezAE
  SysFS ID: /class/block/ram13
  Hardware Class: disk
  Model: "Disk"
  Device File: /dev/ram13
  Device Number: block 1:13
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown


63: None 00.0: 10600 Disk
  [Created at block.245]
  Unique ID: s19p.Fxp0d3BezAE
  SysFS ID: /class/block/ram14
  Hardware Class: disk
  Model: "Disk"
  Device File: /dev/ram14
  Device Number: block 1:14
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown


64: None 00.0: 10600 Disk
  [Created at block.245]
  Unique ID: JDPt.Fxp0d3BezAE
  SysFS ID: /class/block/ram15
  Hardware Class: disk
  Model: "Disk"
  Device File: /dev/ram15
  Device Number: block 1:15
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown


65: USB 00.0: 10a00 Hub
  [Created at usb.122]
  Unique ID: k4bc.OqydEZZ981A
  Parent ID: ruGf.5Ic7jN+tRT5
  SysFS ID: /devices/pci0000:00/0000:00:02.1/usb1/1-0:1.0
  SysFS BusID: 1-0:1.0
  Hardware Class: hub
  Model: "Linux Foundation 2.0 root hub"
  Hotplug: USB
  Vendor: usb 0x1d6b "Linux Foundation"
  Device: usb 0x0002 "2.0 root hub"
  Revision: "4.04"
  Serial ID: "0000:00:02.1"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 480 Mbps
  Module Alias: "usb:v1D6Bp0002d0404dc09dsc00dp00ic09isc00ip00in00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #15 (USB Controller)


67: USB 00.0: 0282 WLAN controller
  [Created at usb.122]
  Unique ID: X7GA.eL1gmsHjN_0
  Parent ID: k4bc.OqydEZZ981A
  SysFS ID: /devices/pci0000:00/0000:00:02.1/usb1/1-7/1-7:1.0
  SysFS BusID: 1-7:1.0
  Hardware Class: network
  Model: "Realtek 802.11n NIC"
  Hotplug: USB
  Vendor: usb 0x0bda "Realtek Semiconductor Corp."
  Device: usb 0x818b "802.11n NIC"
  Revision: "2.00"
  Serial ID: "00e04c000001"
  Driver: "rtl8192eu"
  Driver Modules: "8192eu"
  Device File: enx0013ef520879
  Features: WLAN
  Speed: 480 Mbps
  HW Address: 00:13:ef:52:08:79
  Link detected: yes
  WLAN channels: 1 2 3 4 5 6 7 8 9 10 11 12 13
  WLAN frequencies: 2.412 2.417 2.422 2.427 2.432 2.437 2.442 2.447 2.452 2.457 2.462 2.467 2.472
  WLAN bitrates: 1 2 5.5 11
  WLAN encryption modes: TKIP CCMP
  WLAN authentication modes: open wpa-psk wpa-eap
  Module Alias: "usb:v0BDAp818Bd0200dc00dsc00dp00icFFiscFFipFFin00"
  Driver Info #0:
    Driver Status: 8192eu is active
    Driver Activation Cmd: "modprobe 8192eu"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #65 (Hub)


68: USB 00.0: 10a00 Hub
  [Created at usb.122]
  Unique ID: pBe4.kllrQr_lFX9
  Parent ID: _Znp.KtsH5J01IxE
  SysFS ID: /devices/pci0000:00/0000:00:02.0/usb2/2-0:1.0
  SysFS BusID: 2-0:1.0
  Hardware Class: hub
  Model: "Linux Foundation 1.1 root hub"
  Hotplug: USB
  Vendor: usb 0x1d6b "Linux Foundation"
  Device: usb 0x0001 "1.1 root hub"
  Revision: "4.04"
  Serial ID: "0000:00:02.0"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 12 Mbps
  Module Alias: "usb:v1D6Bp0001d0404dc09dsc00dp00ic09isc00ip00in00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #14 (USB Controller)


69: USB 00.0: 10800 Keyboard
  [Created at usb.122]
  Unique ID: Zj8l.0PGCqK2HNaA
  Parent ID: pBe4.kllrQr_lFX9
  SysFS ID: /devices/pci0000:00/0000:00:02.0/usb2/2-4/2-4:1.0
  SysFS BusID: 2-4:1.0
  Hardware Class: keyboard
  Model: "Logitech Unifying Receiver"
  Hotplug: USB
  Vendor: usb 0x046d "Logitech, Inc."
  Device: usb 0xc52b "Unifying Receiver"
  Revision: "12.01"
  Driver: "usbhid"
  Driver Modules: "usbhid"
  Speed: 12 Mbps
  Module Alias: "usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip01in00"
  Driver Info #0:
    XkbRules: xfree86
    XkbModel: pc104
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #68 (Hub)


70: USB 00.1: 10503 USB Mouse
  [Created at usb.122]
  Unique ID: 0vOp.x2LcURBGx5F
  Parent ID: pBe4.kllrQr_lFX9
  SysFS ID: /devices/pci0000:00/0000:00:02.0/usb2/2-4/2-4:1.1
  SysFS BusID: 2-4:1.1
  Hardware Class: mouse
  Model: "Logitech Unifying Receiver"
  Hotplug: USB
  Vendor: usb 0x046d "Logitech, Inc."
  Device: usb 0xc52b "Unifying Receiver"
  Revision: "12.01"
  Compatible to: int 0x0200 0x0001 "Generic USB Mouse"
  Driver: "usbhid"
  Driver Modules: "usbhid"
  Speed: 12 Mbps
  Module Alias: "usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip02in01"
  Driver Info #0:
    XFree86 Protocol: explorerps/2
    GPM Protocol: exps2
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #68 (Hub)


71: USB 00.2: 0000 Unclassified device
  [Created at usb.122]
  Unique ID: T4ft.lVLMBtrsHd4
  Parent ID: pBe4.kllrQr_lFX9
  SysFS ID: /devices/pci0000:00/0000:00:02.0/usb2/2-4/2-4:1.2
  SysFS BusID: 2-4:1.2
  Hardware Class: unknown
  Model: "Logitech Unifying Receiver"
  Hotplug: USB
  Vendor: usb 0x046d "Logitech, Inc."
  Device: usb 0xc52b "Unifying Receiver"
  Revision: "12.01"
  Driver: "usbhid"
  Driver Modules: "usbhid"
  Speed: 12 Mbps
  Module Alias: "usb:v046DpC52Bd1201dc00dsc00dp00ic03isc00ip00in02"
  Driver Info #0:
    Driver Status: usbhid is active
    Driver Activation Cmd: "modprobe usbhid"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #68 (Hub)


72: None 00.0: 10103 CPU
  [Created at cpu.460]
  Unique ID: rdCR.j8NaKXDZtZ6
  Hardware Class: cpu
  Arch: Intel
  Vendor: "AuthenticAMD"
  Model: 15.79.2 "AMD Sempron(tm) Processor 3600+"
  Features: fpu,vme,de,pse,tsc,msr,pae,mce,cx8,apic,sep,mtrr,pge,mca,cmov,pat,pse36,clflush,mmx,fxsr,sse,sse2,syscall,nx,mmxext,fxsr_opt,rdtscp,lm,3dnowext,3dnow,rep_good,extd_apicid,pni,cx16,lahf_lm,extapic,cr8_legacy,3dnowprefetch,vmmcall
  Clock: 1800 MHz
  BogoMips: 3616.54
  Cache: 256 kb
  Config Status: cfg=new, avail=yes, need=no, active=unknown


73: None 00.0: 10701 Ethernet
  [Created at net.125]
  Unique ID: _aoP.ndpeucax6V1
  Parent ID: IxXX.LZJQZ1iMpA0
  SysFS ID: /class/net/enp0s7
  SysFS Device Link: /devices/pci0000:00/0000:00:07.0
  Hardware Class: network interface
  Model: "Ethernet network interface"
  Driver: "forcedeth"
  Driver Modules: "forcedeth"
  Device File: enp0s7
  HW Address: 00:1c:25:07:23:46
  Link detected: no
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #19 (Ethernet controller)


74: None 00.0: 10700 Loopback
  [Created at net.125]
  Unique ID: ZsBS.GQNx7L4uPNA
  SysFS ID: /class/net/lo
  Hardware Class: network interface
  Model: "Loopback network interface"
  Device File: lo
  Link detected: yes
  Config Status: cfg=new, avail=yes, need=no, active=unknown


75: None 00.0: 10780 Network Interface
  [Created at net.125]
  Unique ID: tovL.GSopYcFr9cF
  SysFS ID: /class/net/tun0
  Hardware Class: network interface
  Model: "Network Interface"
  Driver: "tun"
  Device File: tun0
  Link detected: yes
  Config Status: cfg=new, avail=yes, need=no, active=unknown


76: None 00.0: 10701 Ethernet
  [Created at net.125]
  Unique ID: ZZyz.ndpeucax6V1
  Parent ID: X7GA.eL1gmsHjN_0
  SysFS ID: /class/net/enx0013ef520879
  SysFS Device Link: /devices/pci0000:00/0000:00:02.1/usb1/1-7/1-7:1.0
  Hardware Class: network interface
  Model: "Ethernet network interface"
  Driver: "rtl8192eu"
  Driver Modules: "8192eu"
  Device File: enx0013ef520879
  HW Address: 00:13:ef:52:08:79
  Link detected: yes
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #67 (WLAN controller)



```

wireless-info.txt:

```


########## wireless info START ##########


Report from: 22 Jun 2016 18:10 EDT -0400


Booted last: 22 Jun 2016 00:00 EDT -0400


Script from: 26 May 2016 21:56 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial


##### kernel ############################


Linux 4.4.0-24-generic #43-Ubuntu SMP Wed Jun 8 19:25:16 UTC 2016 i686 athlon i686 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Lubuntu


##### lspci #############################


00:07.0 Bridge [0680]: NVIDIA Corporation MCP61 Ethernet [10de:03ef] (rev a2)
    Subsystem: Foxconn International, Inc. MCP61 Ethernet [105b:0d15]
    Kernel driver in use: forcedeth


##### lsusb #############################


Bus 001 Device 004: ID 0bda:818b Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 1058:1021 Western Digital Technologies, Inc. Elements Desktop (WDBAAU)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


'pccardctl' is not installed (package "pcmciautils").


##### rfkill ############################


##### lsmod #############################


cfg80211              499712  0


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp0s7    Link encap:Ethernet  HWaddr <MAC 'enp0s7' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


enx<IF from MAC [IF2]> Link encap:Ethernet  HWaddr <MAC 'enx<IF from MAC [IF2]>' [IF2]>  
          inet addr:192.168.0.106  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:261832 errors:0 dropped:3099 overruns:0 frame:0
          TX packets:408033 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:84663633 (84.6 MB)  TX bytes:410084263 (410.0 MB)


tun0      Link encap:UNSPEC  HWaddr <MAC 'tun0' [IF3]>  
          inet addr:10.136.1.6  P-t-P:10.136.1.5  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:134923 errors:0 dropped:0 overruns:0 frame:0
          TX packets:290867 errors:0 dropped:599 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:15314164 (15.3 MB)  TX bytes:354351847 (354.3 MB)


##### iwconfig ##########################


enp0s7    no wireless extensions.


tun0      no wireless extensions.


lo        no wireless extensions.


enx<IF from MAC [IF2]>  IEEE 802.11bgn  ESSID:"TP-LINK_2.4GHz_EC07E1"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'TP-LINK_2.4GHz_EC07E1' [AC1]>   
          Bit Rate:144.4 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=80/100  Signal level=100/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.136.1.5      128.0.0.0       UG    0      0        0 tun0
0.0.0.0         192.168.0.1     0.0.0.0         UG    600    0        0 enx<IF from MAC [IF2]>
10.136.1.1      10.136.1.5      255.255.255.255 UGH   0      0        0 tun0
10.136.1.5      0.0.0.0         255.255.255.255 UH    0      0        0 tun0
128.0.0.0       10.136.1.5      128.0.0.0       UG    0      0        0 tun0
192.168.0.0     0.0.0.0         255.255.255.0   U     600    0        0 enx<IF from MAC [IF2]>
208.167.254.238 192.168.0.1     255.255.255.255 UGH   0      0        0 enx<IF from MAC [IF2]>


##### resolv.conf #######################


nameserver 209.222.18.222
nameserver 209.222.18.218


##### network managers ##################


Installed:


    NetworkManager


Running:


root       590     1  0 13:25 ?        00:00:07 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         tun0
GENERAL.TYPE:                           tun
GENERAL.NM-TYPE:                        NMDeviceTun
GENERAL.VENDOR:                         
GENERAL.PRODUCT:                        
GENERAL.DRIVER:                         tun
GENERAL.DRIVER-VERSION:                 1.6
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/virtual/net/tun0
GENERAL.IP-IFACE:                       tun0
GENERAL.IS-SOFTWARE:                    yes
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     tun0
GENERAL.CON-UUID:                       97501a40-5c45-4254-8c82-2a2e2414f642
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{38}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   97501a40-5c45-4254-8c82-2a2e2414f642 | tun0
IP4.ADDRESS[1]:                         10.136.1.6/32
IP4.GATEWAY:                            
IP4.ROUTE[1]:                           dst = 128.0.0.0/1, nh = 10.136.1.5, mt = 0
IP4.ROUTE[2]:                           dst = 10.136.1.1/32, nh = 10.136.1.5, mt = 0
IP4.ROUTE[3]:                           dst = 0.0.0.0/1, nh = 10.136.1.5, mt = 0
IP6.GATEWAY:                            


GENERAL.DEVICE:                         enx<IF from MAC [IF2]>
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek
GENERAL.PRODUCT:                        802.11n NIC
GENERAL.DRIVER:                         rtl8192eu
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enx<IF from MAC [IF2]>' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.1/usb1/1-7/1-7:1.0/net/enx<IF from MAC [IF2]>
GENERAL.IP-IFACE:                       enx<IF from MAC [IF2]>
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     TP-LINK_2.4GHz_EC07E1
GENERAL.CON-UUID:                       6226b91f-d02e-46c7-af79-d0012d596c5a
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     144 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{15}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   6226b91f-d02e-46c7-af79-d0012d596c5a | TP-LINK_2.4GHz_EC07E1
IP4.ADDRESS[1]:                         192.168.0.106/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 208.167.254.238/32, nh = 192.168.0.1, mt = 0
IP4.DNS[1]:                             192.168.0.1
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1466639505
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 7200
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.0.106
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       routers = 192.168.0.1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       domain_name_servers = 192.168.0.1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[25]:                       network_number = 192.168.0.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.0.1
IP6.GATEWAY:                            


GENERAL.DEVICE:                         enp0s7
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         NVIDIA Corporation
GENERAL.PRODUCT:                        MCP61 Ethernet
GENERAL.DRIVER:                         forcedeth
GENERAL.DRIVER-VERSION:                 0.64
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp0s7' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:07.0/net/enp0s7
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 


SSID                   BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
xfinitywifi            <MAC 'xfinitywifi' [AC3]>  Infra  6     2437 MHz  44 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  --         no        
--                     <MAC '' [AC2]>  Infra  6     2437 MHz  44 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2       no        
TP-LINK_2.4GHz_EC07E1  <MAC 'TP-LINK_2.4GHz_EC07E1' [AC1]>  Infra  1     2412 MHz  44 Mbit/s  80      &#9602;&#9604;&#9606;_  WPA1 WPA2  yes     * 
--                     <MAC '' [AC5]>  Infra  10    2457 MHz  14 Mbit/s  64      &#9602;&#9604;&#9606;_  WPA2       no        
--                     <MAC '' [AC6]>  Infra  10    2457 MHz  14 Mbit/s  64      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
HOME-1F68              <MAC 'HOME-1F68' [AC4]>  Infra  10    2457 MHz  14 Mbit/s  50      &#9602;&#9604;__  WPA1 WPA2  no        


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/TP-LINK_2.4GHz_EC07E1]] (600 root)
[connection] id=TP-LINK_2.4GHz_EC07E1 | type=wifi | permissions=user:htpc:;
[wifi] mac-address=<MAC 'enx<IF from MAC [IF2]>' [IF2]> | mac-address-blacklist= | ssid=TP-LINK_2.4GHz_EC07E1
[ipv4] method=auto
[ipv6] method=ignore


##### iw reg get ########################


Region: America/Toronto (based on set time zone)


country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)


##### iwlist channels ###################


enp0s7    no frequency information.


tun0      no frequency information.


lo        no frequency information.


enx<IF from MAC [IF2]>  13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Current Frequency=2.412 GHz (Channel 1)


##### iwlist scan #######################


enp0s7    Interface doesn't support scanning.


tun0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      1   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.437 GHz (Channel 6)
      4   APs on   Frequency:2.457 GHz (Channel 10)


enx<IF from MAC [IF2]>  Scan completed :
          Cell 01 - Address: <MAC 'TP-LINK_2.4GHz_EC07E1' [AC1]>
                    ESSID:"TP-LINK_2.4GHz_EC07E1"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    Extra:wpa_ie=dd160050f20101000050f20401000050f20401000050f202
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=83/100  Signal level=100/100  
                    Extra:fm=0003
          Cell 02 - Address: <MAC '' [AC2]>
                    ESSID:""
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=20/100  Signal level=100/100  
                    Extra:fm=0001
          Cell 03 - Address: <MAC 'xfinitywifi' [AC3]>
                    ESSID:"xfinitywifi"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:off
                    Bit Rates:300 Mb/s
                    Quality=77/100  Signal level=100/100  
                    Extra:fm=0003
          Cell 04 - Address: <MAC 'HOME-1F68' [AC4]>
                    ESSID:"HOME-1F68"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.457 GHz (Channel 10)
                    Encryption key:on
                    Bit Rates:270 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2020050f20401000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac02000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Quality=6/100  Signal level=65/100  
                    Extra:fm=0003
          Cell 05 - Address: <MAC '' [AC5]>
                    ESSID:""
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.457 GHz (Channel 10)
                    Encryption key:on
                    Bit Rates:270 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=100/100  Signal level=70/100  
                    Extra:fm=0001
          Cell 06 - Address: <MAC '' [AC6]>
                    ESSID:""
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.457 GHz (Channel 10)
                    Encryption key:on
                    Bit Rates:270 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2020050f20401000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac02000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Quality=100/100  Signal level=70/100  
                    Extra:fm=0001
          Cell 07 - Address: <MAC '' [AC7]>
                    ESSID:""
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.457 GHz (Channel 10)
                    Encryption key:on
                    Bit Rates:270 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2020050f20401000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac02000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Quality=100/100  Signal level=70/100  
                    Extra:fm=0001


##### module infos ######################


[cfg80211]
filename:       /lib/modules/4.4.0-24-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-24-generic SMP mod_unload modversions 686 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


##### modprobe options ##################


[/etc/modprobe.d/8192cu-disable-power-management.conf]
options 8192cu rtw_power_mgnt=0 rtw_enusbss=0


[/etc/modprobe.d/amd64-microcode-blacklist.conf]
blacklist microcode


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac
blacklist rtl8192cu


[/etc/modprobe.d/blacklist-native-rtl8192.conf]
install rtl8192cu /bin/false
install rtl8192c_common /bin/false
install rtlwifi /bin/false
install rtl8xxxu /bin/false


[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/libpisock9.conf]
blacklist visor


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


[/etc/modprobe.d/rtl8192eu.conf]
options 8192eu rtw_power_mgnt=0 rtw_enusbss=0


##### rc.local ##########################


ethtool -A eth0 autoneg off
exit 0


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[   17.906680] RTL871X: rtl8192eu v4.3.1.1_11320.20140505
[   18.067351] RTL871X: rtw_ndev_init(wlan0)
[   18.182489] rtl8192eu 1-7:1.0 enx<IF from MAC [IF2]>: renamed from wlan0
[   36.659983] IPv6: ADDRCONF(NETDEV_UP): enp0s7: link is not ready
[   36.660880] forcedeth 0000:00:07.0 enp0s7: MSI enabled
[   36.661099] forcedeth 0000:00:07.0 enp0s7: no link during initialization
[   36.661392] IPv6: ADDRCONF(NETDEV_UP): enp0s7: link is not ready
[   37.107887] IPv6: ADDRCONF(NETDEV_UP): enx<IF from MAC [IF2]>: link is not ready (repeated 3 times)
[   50.801530] IPv6: ADDRCONF(NETDEV_CHANGE): enx<IF from MAC [IF2]>: link becomes ready


########## wireless info END ############



```


[COLOR=#000000]What I have done:[/COLOR]


[COLOR=#000000][COLOR=#000000][x] Set the country code[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][x] Router - changed the encryption to WPA2 only

[/COLOR][/COLOR][COLOR=#000000]I am getting between 15-20 mbps with wifi dongle, as compared to 3-4x higher with dongle attached to a windows pc.

[/COLOR][COLOR=#000000]Plugged ethernet into linux pc and ran speedtest, I am currently only getting 20mbps. I am getting 90mbps on windows laptop. If any other system information is needed, please let me know which commands to run to help assist getting this resolved. [/COLOR]

[COLOR=#000000]Thanks in advance!,[/COLOR]
[COLOR=#000000]Ken[/COLOR]

---

### Post by ken55 on 2016-06-24
Anyone out there with any insight?

---

### Post by ken55 on 2016-06-26
bump

---

### Post by Irihapeti on 2016-06-27
*Thread moved to **Networking & Wireless**.*

---

### Post by QLee on 2016-06-27
> **ken55 said:**
> Anyone out there with any insight?

For what it's worth:

I see Hadaka helped you get your WiFi going in thread [http://ubuntuforums.org/showthread.php?t=2327896](http://ubuntuforums.org/showthread.php?t=2327896)

It seems your country code is still not set as Hadaka suggested you do in the other thread. I would do that if I were you. I seem to remember that helping in some threads I've looked at on here.

Another thing I notice from the script results, you have code in rc.local that turns autonegotiation off on eth0. Did you have a specific reason for that and does that reason still exist? (Rhetorical question, you decide.) I suspect that might have the potential to make the hardwired connection slower. 

That's all that occurs to me at this time. At least this will bump the thread back to the top, maybe someone else has further ideas.

---

### Post by ken55 on 2016-06-28
> **QLee said:**
> For what it's worth:

I see Hadaka helped you get your WiFi going in thread [http://ubuntuforums.org/showthread.php?t=2327896](http://ubuntuforums.org/showthread.php?t=2327896)

It seems your country code is still not set as Hadaka suggested you do in the other thread. I would do that if I were you. I seem to remember that helping in some threads I've looked at on here.

Another thing I notice from the script results, you have code in rc.local that turns autonegotiation off on eth0. Did you have a specific reason for that and does that reason still exist? (Rhetorical question, you decide.) I suspect that might have the potential to make the hardwired connection slower. 

That's all that occurs to me at this time. At least this will bump the thread back to the top, maybe someone else has further ideas.

I changed the country code 2x. Is this not correct? I'm seeing this in wireless-info.txt: 

"[COLOR=#000000][FONT=Ubuntu Mono]Region: America/Toronto (based on set time zone)"  
[/FONT][/COLOR]

I have no idea about rc.local. Is that something I can edit? I haven't intentionally changed anything in there.

Thanks for the response QLee,
Ken

---

