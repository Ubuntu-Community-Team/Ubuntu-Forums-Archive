---
title: "LG cellphone mounts on everything but linux! :-("
date: 2010-02-27
forum: New to Ubuntu
---

### Post by mathewd on 2010-02-27
I have an LG cell phone with a "Removable Disk" mode that lets me treat it as external storage when connected via a USB cord. When it mounts, I can also access the stored photos from the phone's camera. The problem is: it only seems to mount on Windows and Mac machines- not the Ubuntu 9.10 netbook that I use most :-(

I'm new to Linux, and on the forums here there seem to be similar problems but none seem identical to mine, so I'm really hoping for some help! 

Here are the results of *lsusb* before plugging it in:

```
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 093a:2500 Pixart Imaging, Inc. USB Optical Mouse
Bus 001 Device 003: ID 0c45:63e4 Microdia 
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 413c:02b0 Dell Computer Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```And here are the results after:

```
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 093a:2500 Pixart Imaging, Inc. USB Optical Mouse
Bus 001 Device 003: ID 0c45:63e4 Microdia 
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 009: ID 05c6:1000 Qualcomm, Inc. 
Bus 005 Device 002: ID 413c:02b0 Dell Computer Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```Also, here are the results of* tail -f -n 0 /var/log/messages*

```
Feb 28 02:25:39 mathew-laptop kernel: [  922.228144] usb 5-2: new full speed USB device using uhci_hcd and address 9
Feb 28 02:25:39 mathew-laptop kernel: [  922.389450] usb 5-2: configuration #1 chosen from 1 choice
Feb 28 02:25:39 mathew-laptop kernel: [  922.402467] scsi5 : SCSI emulation for USB Mass Storage devices
```So... what am I missing? Why does it not mount nor show up in "Computer" nor "/media"? Any help/suggestions would be greatly appreciated! Thanks so much!

---

### Post by GSF1200S on 2010-02-27
> **mathewd said:**
> I have an LG cell phone with a "Removable Disk" mode that lets me treat it as external storage when connected via a USB cord. When it mounts, I can also access the stored photos from the phone's camera. The problem is: it only seems to mount on Windows and Mac machines- not the Ubuntu 9.10 netbook that I use most :-(

I'm new to Linux, and on the forums here there seem to be similar problems but none seem identical to mine, so I'm really hoping for some help! 

Here are the results of *lsusb* before plugging it in:

```
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 093a:2500 Pixart Imaging, Inc. USB Optical Mouse
Bus 001 Device 003: ID 0c45:63e4 Microdia 
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 413c:02b0 Dell Computer Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```And here are the results after:

```
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 093a:2500 Pixart Imaging, Inc. USB Optical Mouse
Bus 001 Device 003: ID 0c45:63e4 Microdia 
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 009: ID 05c6:1000 Qualcomm, Inc. 
Bus 005 Device 002: ID 413c:02b0 Dell Computer Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```Also, here are the results of* tail -f -n 0 /var/log/messages*

```
Feb 28 02:25:39 mathew-laptop kernel: [  922.228144] usb 5-2: new full speed USB device using uhci_hcd and address 9
Feb 28 02:25:39 mathew-laptop kernel: [  922.389450] usb 5-2: configuration #1 chosen from 1 choice
Feb 28 02:25:39 mathew-laptop kernel: [  922.402467] scsi5 : SCSI emulation for USB Mass Storage devices
```So... what am I missing? Why does it not mount nor show up in "Computer" nor "/media"? Any help/suggestions would be greatly appreciated! Thanks so much!

After you plug it in and lsusb shows a new entry, try running:
```
sudo fdisk -l
```
and see what it prints out (or post it here).

You might want to run the command BEFORE you plug it in so you know what your partition table looks like.

I dont know why it doesnt open automagically, but if it shows up in fdisk, you can simply create a directory or append /etc/fstab to reflect the phone.

Assuming your phone shows up as /dev/sdb1, you can mount the phone in directory /home/user/phone as follows:
```
sudo mount /dev/sdb1 /home/user/phone
```

---

### Post by sandyd on 2010-02-27
can you post the output of ```

fdisk -l
```

---

### Post by mathewd on 2010-02-27
Hi guys, thanks for the quick replies. 

fdisk doesn't see it at all, despite it showing up in lsusb :-(  to verify, here's the terminal output, only showing my internal SSD and a memory card (not the phone)

```
Disk /dev/sda: 15.4 GB, 15408046080 bytes
255 heads, 63 sectors/track, 1873 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x98deb064

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1789    14370111   83  Linux
/dev/sda2            1790        1873      674730    5  Extended
/dev/sda5            1790        1873      674698+  82  Linux swap / Solaris

Disk /dev/mmcblk0: 2032 MB, 2032664576 bytes
64 heads, 63 sectors/track, 984 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1               1         984     1983619+   6  FAT16

```

I just don't get why it won't show up... again, it mounts automatically and without issue on both the Mac and the Windows PCs at work.

By the way, I don't think this should make a difference, but here's the output of* tail -f -n 0 /var/log/messages* when I first connect the phone in "Removable Disk" mode, then exit the Removable Disk mode, then restart it... all while never disconnecting the USB cord
```

Feb 28 02:25:39 mathew-laptop kernel: [  922.228144] usb 5-2: new full speed USB device using uhci_hcd and address 9
Feb 28 02:25:39 mathew-laptop kernel: [  922.389450] usb 5-2: configuration #1 chosen from 1 choice
Feb 28 02:25:39 mathew-laptop kernel: [  922.402467] scsi5 : SCSI emulation for USB Mass Storage devices
Feb 28 02:43:25 mathew-laptop kernel: [ 1988.136173] usb 5-2: USB disconnect, address 9
Feb 28 02:43:26 mathew-laptop kernel: [ 1989.616115] usb 5-2: new full speed USB device using uhci_hcd and address 10
Feb 28 02:43:26 mathew-laptop kernel: [ 1989.778566] usb 5-2: configuration #1 chosen from 1 choice
Feb 28 02:43:26 mathew-laptop kernel: [ 1989.781660] cdc_acm 5-2:1.0: ttyACM3: USB ACM device
Feb 28 02:50:10 mathew-laptop kernel: [ 2393.616189] usb 5-2: USB disconnect, address 10
Feb 28 02:50:12 mathew-laptop kernel: [ 2395.096117] usb 5-2: new full speed USB device using uhci_hcd and address 11
Feb 28 02:50:12 mathew-laptop kernel: [ 2395.262374] usb 5-2: configuration #1 chosen from 1 choice
Feb 28 02:50:12 mathew-laptop kernel: [ 2395.275131] scsi6 : SCSI emulation for USB Mass Storage devices
```

Why oh why won't you mount, stupid phone!?!? Any other suggestions guys?

---

### Post by skymera on 2010-02-27
I never got my LG KU900 to work in Ubuntu. Though i didn't try very hard.

If you have a memory card and have USB set to Mass Storage, it should work and act like a disk... in theory.

---

