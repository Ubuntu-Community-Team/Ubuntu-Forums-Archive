---
title: "Motorola Rokr not connecting through USB"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by gerbs on 2009-01-11
My motorola Rokr phone connected to USB shows up in File Browser as an SCSI drive however I can not open drive, because when i double click "SCSI drive" it highlights the drive, freezes for 2 seconds, then deselects drive. If phone shows up in File browser does that mean it is actually recognized by Ubuntu?
I have 8.10 running on a Lenovo S10 ideapad.

any help is appreciated.

---

### Post by Captain_tux on 2009-01-11
To know for sure if it's recognized, post the output of **lspci** run as root...

---

### Post by gerbs on 2009-01-11
I don't see any USB devices. In File browser the phone shows up as "USB drive" with the ipod icon next to it but i still can not double click it and open it.

root@c-laptop:/home/chris# lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
05:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

---

### Post by steveneddy on 2009-01-11
try connecting via bluetooth instead to see if you get a different result.

---

### Post by gerbs on 2009-01-11
i don't believe i have bluetooth on my laptop.  

When trying to access, i get "unable to mount location." Also tried moto4lin and kmobiletools and neither have recognized the device.

---

### Post by taygan on 2009-01-28
Same problem, even with today's kernel:

Motorola ROKR z6 - connection set to "memory card"

Ubuntu Intrepid 8.10

Linux eklutna 2.6.27-11-generic #1 SMP Fri Jan 23 13:58:13 UTC 2009 x86_64 GNU/Linux

Supposedly this bug was fixed in the kernel.  I did connect at least one time, but now I am able to see the drives, but unable to mount them.

"close" bug here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/263217](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/263217)

lsusb | grep Moto output:

Bus 006 Device 006: ID 22b8:6426 Motorola PCS 

dmesg output:

[   95.608076] usb 6-2: new high speed USB device using ehci_hcd and address 6
[   95.746411] usb 6-2: configuration #1 chosen from 1 choice
[   95.750468] scsi7 : SCSI emulation for USB Mass Storage devices
[   95.753063] usb-storage: device found at 6
[   95.753068] usb-storage: waiting for device to settle before scanning
[  100.752721] usb-storage: device scan complete
[  100.752950] scsi 7:0:0:0: Direct-Access     Motorola MSnc.            0101 PQ: 0 ANSI: 2
[  100.753116] scsi 7:0:0:1: Direct-Access     Motorola MSnc.            0101 PQ: 0 ANSI: 2
[  100.764892] sd 7:0:0:0: [sdc] Attached SCSI removable disk
[  100.765227] sd 7:0:0:0: Attached scsi generic sg3 type 0
[  100.767092] sd 7:0:0:1: [sdd] Attached SCSI removable disk
[  100.767305] sd 7:0:0:1: Attached scsi generic sg4 type 0
[  105.382675] sd 7:0:0:0: [sdc] 3841910 512-byte hardware sectors (1967 MB)
[  105.383417] sd 7:0:0:1: [sdd] 128671 512-byte hardware sectors (66 MB)
[  105.384164] sd 7:0:0:0: [sdc] Write Protect is off
[  105.384172] sd 7:0:0:0: [sdc] Mode Sense: 03 00 00 00
[  105.384178] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[  105.384903] sd 7:0:0:1: [sdd] Write Protect is off
[  105.384911] sd 7:0:0:1: [sdd] Mode Sense: 03 00 00 00
[  105.384917] sd 7:0:0:1: [sdd] Assuming drive cache: write through
[  105.387788] sd 7:0:0:0: [sdc] 3841910 512-byte hardware sectors (1967 MB)
[  105.388542] sd 7:0:0:1: [sdd] 128671 512-byte hardware sectors (66 MB)
[  105.389289] sd 7:0:0:0: [sdc] Write Protect is off
[  105.389296] sd 7:0:0:0: [sdc] Mode Sense: 03 00 00 00
[  105.389301] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[  105.389313]  sdc:<5>sd 7:0:0:1: [sdd] Write Protect is off
[  105.390040] sd 7:0:0:1: [sdd] Mode Sense: 03 00 00 00
[  105.390046] sd 7:0:0:1: [sdd] Assuming drive cache: write through
[  105.390056]  sdd:
[  105.398606] 
[  135.537104] usb 6-2: reset high speed USB device using ehci_hcd and address 6
[  135.714980] sd 7:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_RETRY
[  135.714996] end_request: I/O error, dev sdc, sector 3841664
[  135.715009] Buffer I/O error on device sdc, logical block 1920832
[  135.741628] sd 7:0:0:1: [sdd] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_RETRY
[  135.741647] end_request: I/O error, dev sdd, sector 0
[  135.741660] Buffer I/O error on device sdd, logical block 0
[  135.741671] Buffer I/O error on device sdd, logical block 1
[  135.741678] Buffer I/O error on device sdd, logical block 2
[  135.741685] Buffer I/O error on device sdd, logical block 3
[  135.741692] Buffer I/O error on device sdd, logical block 4
[  135.741699] Buffer I/O error on device sdd, logical block 5
[  135.741705] Buffer I/O error on device sdd, logical block 6
[  135.741712] Buffer I/O error on device sdd, logical block 7
[  135.741727] Buffer I/O error on device sdd, logical block 8
[  135.749937] sd 7:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_RETRY
[  135.749951] end_request: I/O error, dev sdc, sector 3841666

---

