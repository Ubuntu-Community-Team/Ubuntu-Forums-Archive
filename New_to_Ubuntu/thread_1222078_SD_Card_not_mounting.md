---
title: "SD Card not mounting"
date: 2009-07-24
forum: New to Ubuntu
---

### Post by rednano12 on 2009-07-24
Hello all. I have a GE 24-in-1 Card reader. I inserted an SD card in (yes it is inserted correctly,) and the light turns on, meaning the card is recognized. However, it does not show up on my desktop, nor the places menu. 

Here is the output of sudo fdisk -l

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfac6fac6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       54426   437176813+   7  HPFS/NTFS
/dev/sda2           54427       54550      996030   82  Linux swap / Solaris
/dev/sda3           54551       60801    50211157+  83  Linux

Disk /dev/sdb: 2032 MB, 2032664576 bytes
64 heads, 63 sectors/track, 984 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         984     1983619+   b  W95 FAT32

```

As you can see, the card is being recognized. 

Infact, if I go to computer:/// in Nautilius, I can see the drive, but if I double click it, I get an error. "Unable to mount file"

If I try to mount in terminal, it says that "special device /dev/sdb1 does not exist", although as you can see in the fdisk above, it does.

Please help!
Thank you.

---

### Post by bacil on 2009-07-24
I am assuming your card reader is usb. or pci can you plese send output of 
```
lsusb
```
and
```
lspci
```

---

### Post by rednano12 on 2009-07-24
Yes, the card reader is USB 2.0

lsusb:
```
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 046d:c510 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  

```
Believe the Logitech thing is my mouse

lspci:
```
00:00.0 Host bridge: Intel Corporation 82875P/E7210 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82875P Processor to AGP Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82875P/E7210 Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705 Gigabit Ethernet (rev 01)
02:01.0 RAID bus controller: Promise Technology, Inc. PDC20371 (FastTrak S150 TX2plus) (rev 02)
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
02:03.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
02:03.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
02:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)

```

---

### Post by bacil on 2009-07-24
based on this it seems you are missing drivers. your reader is not showing in lsusb

what is its make and model ? can you find out usb id ?

---

### Post by rednano12 on 2009-07-24
Well, my uncle gave it to me so I don't know much about it. 

It was made by GE.
SKU is 98780 

Here is a link [http://www.jascoproducts.com/products/pc/viewPrd.asp?idproduct=660&IDCategory=6](http://www.jascoproducts.com/products/pc/viewPrd.asp?idproduct=660&IDCategory=6)

I figured it would just work... do I need a driver of some sort?

---

### Post by achase79 on 2009-07-24
run ```
dmesg > ~/Desktop/test1.txt
```
unplug the reader then plug it in again
run ```
dmesg > ~/Desktop/test2.txt
```
Then look for any differences between test1.txt and test2.txt.  
This may tell you if it found drivers for the device and if not then it will have clues to find out what to search for.

---

### Post by rednano12 on 2009-07-24
test2.txt has this tacked on at the end 

```
[142439.307095] usb 5-8: USB disconnect, address 4
[142443.051939] usb 5-8: new high speed USB device using ehci_hcd and address 5
[142443.186347] usb 5-8: configuration #1 chosen from 1 choice
[142443.186866] scsi9 : SCSI emulation for USB Mass Storage devices
[142443.187149] usb-storage: device found at 5
[142443.187155] usb-storage: waiting for device to settle before scanning
[142448.181289] usb-storage: device scan complete
[142448.181899] scsi 9:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[142448.182531] scsi 9:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[142448.183270] scsi 9:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[142448.183924] scsi 9:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[142448.587343] sd 9:0:0:0: [sdb] 3970048 512-byte hardware sectors (2033 MB)
[142448.588470] sd 9:0:0:0: [sdb] Write Protect is off
[142448.588476] sd 9:0:0:0: [sdb] Mode Sense: 03 00 00 00
[142448.588480] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[142448.591338] sd 9:0:0:0: [sdb] 3970048 512-byte hardware sectors (2033 MB)
[142448.592342] sd 9:0:0:0: [sdb] Write Protect is off
[142448.592348] sd 9:0:0:0: [sdb] Mode Sense: 03 00 00 00
[142448.592353] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[142448.592363]  sdb: sdb1
[142448.594464] sd 9:0:0:0: [sdb] Attached SCSI removable disk
[142448.594536] sd 9:0:0:0: Attached scsi generic sg2 type 0
[142448.595762] sd 9:0:0:1: [sdc] Attached SCSI removable disk
[142448.595822] sd 9:0:0:1: Attached scsi generic sg3 type 0
[142448.597012] sd 9:0:0:2: [sdd] Attached SCSI removable disk
[142448.597074] sd 9:0:0:2: Attached scsi generic sg4 type 0
[142448.598253] sd 9:0:0:3: [sde] Attached SCSI removable disk
[142448.598314] sd 9:0:0:3: Attached scsi generic sg5 type 
```

I think that means it found it.

---

### Post by bacil on 2009-07-24
you will need to enable it as hot-plug device.  I have found this tutorial ages ago here is my writeup

If you have a look through the file /proc/bus/usb/devices, you should see a section with an S: line and the name of your reader and an I: line with Driver=usb-storage.  If you see that, the kernel is recognizing the USB device.


Install the sg3-utils package,```
 apt-get install sg3-utils
```
To check your SCSI devices, run the command```
 sg_scan -i
``` You should see something like this:
```

    /dev/sg0: scsi0 channel=0 id=0 lun=0 [em]  type=0
        eUSB      Compact Flash     5.09 [wide=0 sync=0 cmdq=0 sftre=0 pq=0x0]

```
This indicates that the “raw” SCSI device associated with your reader is /dev/sg0.  You can also confirm that the driver is working by looking at the file /proc/scsi/scsi .


Now, run the command ```
 sg_map
``` to determine the real SCSI device associated with your reader.  You'll see output like this:

```
    /dev/sg0  /dev/sda
```



That's it.  Your card reader is /dev/sda.  The first (and almost certainly only) partition is /dev/sda1.

---

### Post by rednano12 on 2009-07-24
For those wondering, I decided to reformat. I attempted to back up all of the files on it, but I got an error saying that a folder that I deleted a few months ago was not able to be removed. I backed up the disk 1 file at a time, and reformatted using GParted.

---

