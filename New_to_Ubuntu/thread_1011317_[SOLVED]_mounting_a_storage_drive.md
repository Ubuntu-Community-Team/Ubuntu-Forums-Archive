---
title: "[SOLVED] mounting a storage drive"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by pshootr on 2008-12-14
I am using server 8.10 and formatted a starage drive (for a local file server) with the default file system and tried mounting it with this.

sudo mount -t ext3 -o rw /dev/sdb1 /mnt/sdb1

and got this

sudo mount -t ext3 -o rw /dev/sdb1 /mnt/sdb1
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

dmesg gave me this

[    5.827310] tulip 0000:00:0f.0: found PCI INT A -> IRQ 10
[    5.827853] tulip0:  MII transceiver #1 config 3100 status 7869 advertising 05e1.
[    5.833456] eth0: ADMtek Comet rev 17 at Port 0x1400, 00:12:17:53:bc:cf, IRQ 10.
[    5.931416] usbcore: registered new interface driver usbfs
[    5.931526] usbcore: registered new interface driver hub
[    5.931737] usbcore: registered new device driver usb
[    6.066946] libata version 3.00 loaded.
[    6.081585] USB Universal Host Controller Interface driver v3.0
[    6.081782] PCI: setting IRQ 9 as level-triggered
[    6.081797] uhci_hcd 0000:00:07.2: found PCI INT D -> IRQ 9
[    6.081853] uhci_hcd 0000:00:07.2: sharing IRQ 9 with 0000:00:10.0
[    6.081895] uhci_hcd 0000:00:07.2: UHCI Host Controller
[    6.082099] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[    6.082171] uhci_hcd 0000:00:07.2: irq 9, io base 0x00001020
[    6.082926] usb usb1: configuration #1 chosen from 1 choice
[    6.083112] hub 1-0:1.0: USB hub found
[    6.083161] hub 1-0:1.0: 2 ports detected
[    6.302068] pata_pdc202xx_old 0000:00:10.0: found PCI INT A -> IRQ 9
[    6.302110] pata_pdc202xx_old 0000:00:10.0: sharing IRQ 9 with 0000:00:07.2
[    6.302560] scsi0 : pata_pdc202xx_old
[    6.303219] scsi1 : pata_pdc202xx_old
[    6.303441] ata1: PATA max UDMA/66 cmd 0x1068 ctl 0x101c bmdma 0x1080 irq 9
[    6.303458] ata2: PATA max UDMA/66 cmd 0x1060 ctl 0x1018 bmdma 0x1088 irq 9
[    6.420286] usb 1-2: new low speed USB device using uhci_hcd and address 2
[    6.582924] usb 1-2: configuration #1 chosen from 1 choice
[    6.648632] ata_piix 0000:00:07.1: version 2.12
[    6.649104] scsi2 : ata_piix
[    6.649467] scsi3 : ata_piix
[    6.649718] ata3: PATA max UDMA/33 cmd 0x1f0 ctl 0x3f6 bmdma 0x1000 irq 14
[    6.649734] ata4: PATA max UDMA/33 cmd 0x170 ctl 0x376 bmdma 0x1008 irq 15
[    6.832362] ata3.00: ATA-4: ST34311A, 6.01, max UDMA/66
[    6.832380] ata3.00: 8421840 sectors, multi 16: LBA
[    6.832461] ata3.01: ATAPI: CRD-8322B, 1.05, max MWDMA2
[    6.870729] ata3.00: configured for UDMA/33
[    6.890675] ata3.01: configured for MWDMA2
[    7.070561] ata4.00: ATA-4: ST340824A, 3.05, max UDMA/100
[    7.070581] ata4.00: 78165360 sectors, multi 16: LBA
[    7.090490] ata4.00: configured for UDMA/33
[    7.091039] scsi 2:0:0:0: Direct-Access     ATA      ST34311A         6.01 PQ: 0 ANSI: 5
[    7.091888] scsi 2:0:1:0: CD-ROM               LG    CD-ROM CRD-8322B 1.05 PQ: 0 ANSI: 5
[    7.092549] scsi 3:0:0:0: Direct-Access     ATA      ST340824A        3.05 PQ: 0 ANSI: 5
[    8.561096] scsi 2:0:0:0: Attached scsi generic sg0 type 0
[    8.561394] scsi 2:0:1:0: Attached scsi generic sg1 type 5
[    8.561666] scsi 3:0:0:0: Attached scsi generic sg2 type 0
[    8.749215] usbcore: registered new interface driver hiddev
[    8.765470] input: HID 1267:0103 as /devices/pci0000:00/0000:00:07.2/usb1/1-2/1-2:1.0/input/input1
[    8.790849] input,hidraw0: USB HID v1.10 Keyboard [HID 1267:0103] on usb-0000:00:07.2-2
[    8.814532] input: HID 1267:0103 as /devices/pci0000:00/0000:00:07.2/usb1/1-2/1-2:1.1/input/input2
[    8.860841] input,hidraw1: USB HID v1.10 Device [HID 1267:0103] on usb-0000:00:07.2-2
[    8.860951] usbcore: registered new interface driver usbhid
[    8.860974] usbhid: v2.6:USB HID core driver
[    8.909806] Driver 'sd' needs updating - please use bus_type methods
[    8.910349] sd 2:0:0:0: [sda] 8421840 512-byte hardware sectors (4312 MB)
[    8.910473] sd 2:0:0:0: [sda] Write Protect is off
[    8.910488] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    8.910700] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.911071] sd 2:0:0:0: [sda] 8421840 512-byte hardware sectors (4312 MB)
[    8.911187] sd 2:0:0:0: [sda] Write Protect is off
[    8.911202] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    8.911413] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.911440]  sda: sda1 sda2 <<4>Driver 'sr' needs updating - please use bus_type methods
[    8.963929]  sda5 >
[    8.964643] sd 2:0:0:0: [sda] Attached SCSI disk
[    8.965150] sd 3:0:0:0: [sdb] 78165360 512-byte hardware sectors (40021 MB)
[    8.965272] sd 3:0:0:0: [sdb] Write Protect is off
[    8.965287] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    8.965494] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.965841] sd 3:0:0:0: [sdb] 78165360 512-byte hardware sectors (40021 MB)
[    8.965954] sd 3:0:0:0: [sdb] Write Protect is off
[    8.965969] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    8.966175] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.966200]  sdb:sr0: scsi3-mmc drive: 32x/32x cd/rw xa/form2 cdda tray
[    8.969597] Uniform CD-ROM driver Revision: 3.20
[    8.969949] sr 2:0:1:0: Attached scsi CD-ROM sr0
[    8.992753]  unknown partition table
[    8.993132] sd 3:0:0:0: [sdb] Attached SCSI disk
[   10.028372] PM: Starting manual resume from disk
[   10.028392] PM: Resume from partition 8:5
[   10.028400] PM: Checking hibernation image.
[   10.028919] PM: Resume from disk failed.
[   10.177169] EXT3-fs: INFO: recovery required on readonly filesystem.
[   10.177189] EXT3-fs: write access will be enabled during recovery.
[   10.453393] kjournald starting.  Commit interval 5 seconds
[   10.453454] EXT3-fs: recovery complete.
[   10.470099] EXT3-fs: mounted filesystem with ordered data mode.
[   14.689753] udevd version 124 started
[   18.722677] Linux agpgart interface v0.103
[   18.782931] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   19.040797] agpgart-intel 0000:00:00.0: Intel 440BX Chipset
[   19.046881] agpgart-intel 0000:00:00.0: AGP aperture is 64M @ 0xf8000000
[   19.101899] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   19.117879] Emu10k1_gameport 0000:00:0e.1: enabling device (0104 -> 0105)
[   19.133677] gameport: EMU10K1 is pci0000:00:0e.1/gameport0, io 0x1010, speed 1193kHz
[   19.150045] piix4_smbus 0000:00:07.3: SMBus Host Controller at 0x7000, revision 0
[   19.169398] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   21.460868] EMU10K1_Audigy 0000:00:0e.0: enabling device (0104 -> 0105)
[   21.460896] PCI: setting IRQ 11 as level-triggered
[   21.460909] EMU10K1_Audigy 0000:00:0e.0: found PCI INT A -> IRQ 11
[   21.460973] EMU10K1_Audigy 0000:00:0e.0: sharing IRQ 11 with 0000:01:00.0
[   21.720437] AC'97 0 analog subsections not ready
[   28.038554] loop: module loaded
[   28.318678] parport_pc 00:14: reported by Plug and Play BIOS
[   28.318761] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   28.392614] lp0: using parport0 (interrupt-driven).
[   29.617278] Adding 240932k swap on /dev/sda5.  Priority:-1 extents:1 across:240932k
[   30.098863] EXT3 FS on sda1, internal journal
[   32.247979] ip_tables: (C) 2000-2006 Netfilter Core Team
[   34.283019] NET: Registered protocol family 10
[   34.285554] lo: Disabled Privacy Extensions
[   35.422237] 0000:00:0f.0: tulip_stop_rxtx() failed (CSR5 0xfc664010 CSR6 0xff972113)
[   35.422268] eth0: Setting full-duplex based on MII#1 link partner capability of 45e1.
[   44.340659] eth0: no IPv6 routers present
[12786.747904] sd 3:0:0:0: [sdb] 78165360 512-byte hardware sectors (40021 MB)
[12786.748038] sd 3:0:0:0: [sdb] Write Protect is off
[12786.748054] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[12786.748263] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[12786.748291]  sdb:
[12909.379689] sd 3:0:0:0: [sdb] 78165360 512-byte hardware sectors (40021 MB)
[12909.379822] sd 3:0:0:0: [sdb] Write Protect is off
[12909.379838] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[12909.380047] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[12909.380074]  sdb:
[13638.600384] sd 3:0:0:0: [sdb] 78165360 512-byte hardware sectors (40021 MB)
[13638.600518] sd 3:0:0:0: [sdb] Write Protect is off
[13638.600534] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[13638.600745] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[13638.600772]  sdb: sdb1 < >
[55265.225273] attempt to access beyond end of device
[55265.225317] sdb1: rw=0, want=4, limit=2
[55265.225332] EXT3-fs: unable to read superblock

Any suggestions?

---

### Post by karlr42 on 2008-12-14
Could you run sudo fdisk -l and post the output ? I suspect the file system is not ext3, hence the error.

---

### Post by pshootr on 2008-12-14
> **karlr42 said:**
> Could you run sudo fdisk -l and post the output ? I suspect the file system is not ext3, hence the error.

Disk /dev/sda: 4311 MB, 4311982080 bytes
255 heads, 63 sectors/track, 524 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x46a0469f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         494     3968023+  83  Linux
/dev/sda2             495         524      240975    5  Extended
/dev/sda5             495         524      240943+  82  Linux swap / Solaris

Disk /dev/sdb (Sun disk label): 255 heads, 63 sectors, 4865 cylinders
Units = cylinders of 16065 * 512 bytes

   Device Flag    Start       End    Blocks   Id  System
/dev/sdb1             0      4859  39029917+  83  Linux native
/dev/sdb2  u       4859      4865     48195   82  Linux swap
/dev/sdb3             0      4865  39078112+   5  Whole disk

---

### Post by pshootr on 2008-12-14
Ok, I deleted the partiotions shown in the above post. And now I get this.


Disk /dev/sda: 4311 MB, 4311982080 bytes
255 heads, 63 sectors/track, 524 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x46a0469f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         494     3968023+  83  Linux
/dev/sda2             495         524      240975    5  Extended
/dev/sda5             495         524      240943+  82  Linux swap / Solaris

Disk /dev/sdb (Sun disk label): 255 heads, 63 sectors, 4865 cylinders
Units = cylinders of 16065 * 512 bytes

   Device Flag    Start       End    Blocks   Id  System
/dev/sdb1             0      4865  39078112+  83  Linux native

Does this look rite?

---

### Post by pshootr on 2008-12-14
Now I did  this

sudo mount -t ext3 -o rw /dev/sdb1 /mnt/sdb1

And recieved no error. I think it is mounted properly now?

---

### Post by karlr42 on 2008-12-14
Ok, i *think* "Linux Native" means the filesystem is ext2, so run this:
```
sudo mount -t ext2 /dev/sdb1 /mnt/sdb1
```

---

### Post by karlr42 on 2008-12-14
Ignore my last post! Cool, try to 
```
ls /mnt/sdb1
```
and if that works you *should* be set!

---

### Post by pshootr on 2008-12-14
> **karlr42 said:**
> Ignore my last post! Cool, try to 
```
ls /mnt/sdb1
```
and if that works you *should* be set!

That gives me this

lost+found (in blue letters)

Is that good?

---

### Post by karlr42 on 2008-12-14
Yep, sounds like it, lost+found is a folder ubuntu puts on all mounted Linux partitions. Try writing files to it and reading them from it, though it sounds like you're fine.

---

### Post by pshootr on 2008-12-14
I used nano and created a text file (test.txt) in /mnt/sdb1/test.txt. And I wrote out, then exited. Then ran nano again and got to the writen file. Seems all is good. Thank you very much brother.):P

---

### Post by karlr42 on 2008-12-14
Glad to help :D , please mark the thread as solved with "Thread Tools" in the top right of the screen. 
I'd recommond saving that command somewhere so you can enter it whenever you need to mount the drive again.

---

### Post by unutbu on 2008-12-14
pshootr, you might also want to try
```

sudo mount /dev/sdb1 /mnt/sdb1
```

mount should be able to recognize sdb1 has an ext2 filesystem on its own.

Also, if you are reading and writing to sdb1 then it may be wise to convert sdb1 into an ext3 filesystem. By doing so, you will protect sdb1 against possible data loss in case there is an abrupt power outage which would leave an ext2 filesystem in a corrupted state, but usually not seriously affect an ext3 filesystem at all. (An ext3 filesystem has a transaction journal which allows it to recover from the above scenario.)

To convert to ext3, simply type
```

sudo tune2fs -j /dev/sdb1
```

---

### Post by karlr42 on 2008-12-14
I believe the external drive was ext3- in post #5 the OP said he mounted it using the -t ext3 option, which succeeded. Then again, fdisk called it Linux Native, whereas ext3 is usually labeled Linux, so I'm not sure if it was a misstype on the OP's part.

---

