---
title: "Recognizing Lacie HFS+ Firewire drive"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by nathan28 on 2009-02-17
So part of my inspiration to install ubuntu was hopes of recovering an HFS+ Lacie 160 Gb firewire drive that could "survive a fire" (apple store dude).

Ubuntu sees my firewire card apparently, but doesn't find the disk when i plug it in:

here's what i get with lspci:

> 02:02.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
02:02.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
02:02.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
02:04.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
03:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

and with lsmod | egrep 'ieee1394|sb'

> usbhid                 35840  0 
hid                    50560  1 usbhid
usb_storage            82752  1 
libusual               30356  1 usb_storage
sbs                    19464  0 
sbshc                  13440  1 sbs
sbp2                   29324  0 
usbserial              39528  4 sierra
ssb                    40580  2 b43,b44
ieee1394               96324  2 sbp2,ohci1394
scsi_mod              155212  6 usb_storage,sbp2,sr_mod,sd_mod,sg,libata
usbcore               149360  8 usbhid,usb_storage,libusual,sierra,usbserial,ehci_hcd,uhci_hcd

Any advice?

---

### Post by vanadium on 2009-02-17
I don't think Ubuntu can read the HFS+ file format. To check whether the drive and its partition table is "seen", make sure the drive is plugged in and powered on. Then open the command terminal and issue the command
```

sudo fdisk -l

```
Provide your login password when asked (you need administrator privileges with this command). Post the output here if you are unsure on what it means.

---

### Post by nathan28 on 2009-02-18
Ran sudo fdisk -l; in addition to my internal and USB disk, it saw the Firewire disk:

> Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x12345678

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       19457   156288321    c  W95 FAT32 (LBA)

I didn't realize it was FAT32. I had trouble with the disk in windows, so I'm worried it might be that it's screwed at the level of the file system. Regardless, I can't figure out the proper mount command though. if i use a sudo mount -t FAT32 /dev/sdc1 mnt/exhdd -o force (or mount -t HFS+) I get

> mount: mount point mnt/exhdd does not exist

I've got testdisk-6.10, which seems to think it's FAT32. Not having much luck there, though.

---

### Post by avtolle on 2009-02-18
I believe you should use "hfsplus" rather than "HFS+" in your mount command (without the quotation marks, of course).

---

