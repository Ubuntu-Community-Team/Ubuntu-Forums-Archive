---
title: "How mount a USb device"
date: 2009-10-16
forum: New to Ubuntu
---

### Post by LiaGalanodel on 2009-10-16
Hi!

I'm new in linux and I want mount a usb device.
I install gnome-volume-manger.

When I write in the terminal: dmesg:
```
[ 2274.826108] ftdi_sio 1-2:1.0: device disconnected
[ 2311.780023] usb 1-1: new full speed USB device using uhci_hcd and address 4
[ 2312.006572] usb 1-1: configuration #1 chosen from 1 choice
[ 2312.009090] ftdi_sio 1-1:1.0: FTDI USB Serial Device converter detected
[ 2312.009130] usb 1-1: Detected FT232RL
[ 2312.009217] usb 1-1: FTDI USB Serial Device converter now attached to ttyUSB0
[ 2355.672061] usb 1-1: USB disconnect, address 4
[ 2355.674080] ftdi_sio ttyUSB0: FTDI USB Serial Device converter now disconnected from ttyUSB0
[ 2355.674107] ftdi_sio 1-1:1.0: device disconnected
[ 6931.580037] usb 1-1: new full speed USB device using uhci_hcd and address 5
[ 6931.806672] usb 1-1: configuration #1 chosen from 1 choice
[ 6931.809087] ftdi_sio 1-1:1.0: FTDI USB Serial Device converter detected
[ 6931.809129] usb 1-1: Detected FT232RL
[ 6931.809216] usb 1-1: FTDI USB Serial Device converter now attached to ttyUSB0

```When I write: fdisk -l
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf42a5757

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9729    78148161    7  HPFS/NTFS

Disk /dev/sdb: 18.2 GB, 18210036736 bytes
255 heads, 63 sectors/track, 2213 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe818e818

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2116    16996738+  83  Linux
/dev/sdb2            2117        2213      779152+   5  Extended
/dev/sdb5            2117        2213      779121   82  Linux swap / Solaris

```I try this way:

[LIST=1]
[*]Login as root. You can use the *su* command to switch to root user.
[*]Create a folder /mnt/USB with the command: *mkdir /mnt/USB*
[*]Add the following line in the file /etc/fstab (fstab is the file that tells Linux where to mount the various devices, and thus simplying the mount command): /dev/sda1          /mnt/USB         auto          noauto,owner,kuzu         0 0
 Note: The “auto” on the above line means auto detection of filesystem. If your system unable to determine the filesystem type, change it accordingly to the USB drive’s filesystem (e.g. vfat or ntfs or ext2 or ext3).
[*]Mount the USB storage device with the following command: *mount /dev/sda1*
[/LIST]
But it's not work.

Can you help me please?

Thank you,

Best regards,

---

### Post by mikewhatever on 2009-10-16
What kind of device is it? Stoage? Webcam?

Mounting usually applies to storage, but sda1 is probably not the usb device, but rather is an internal hdd. Dmesg didn't show the device name, hence the question, what is it?

---

### Post by LiaGalanodel on 2009-10-16
It's a Storage.

---

### Post by mechanicaldesign on 2009-10-16
Hello to everibody,

Can help me somebody in the next problem: I want to install CentOS5.3 on my usb stick (4Gb).

On my desktop I have installed Ubuntu9.04 and on virtual machine I installed Xubuntu (to tested before installed on my laptop :popcorn:).

Somebody can help me with steps necessary to made this ? Both with command necessary to write on terminal.

Thank you in advance for your support, sugestion and ideea.

Best regards. [IMG]https://www.centos.org/uploads/smil3dbd4d4e4c4f2.gif[/IMG]

---

### Post by prshah on 2009-10-16
> **LiaGalanodel said:**
> It's a Storage.
FT23R USB UART

Sorry UART is a serial port; and the dmesg output also seems to support that. It doesn't seem to be a storage device.

---

### Post by mikechant on 2009-10-16
> Can help me somebody in the next problem: I want to install CentOS5.3 on my usb stick (4Gb).


Please create a new thread rather than tagging on the end of an unrelated one.

---

### Post by LiaGalanodel on 2009-10-16
Hi!

You can try to follow this tutorial:

[http://www.mydigitallife.info/2006/09/10/how-to-mount-usb-disk-drive-in-unix-or-linux/](http://www.mydigitallife.info/2006/09/10/how-to-mount-usb-disk-drive-in-unix-or-linux/)

---

### Post by LiaGalanodel on 2009-10-16
> **prshah said:**
> Sorry UART is a serial port; and the dmesg output also seems to support that. It doesn't seem to be a storage device.
I'm sorry! It's not UART

---

### Post by mikewhatever on 2009-10-16
I've never used the instructions you provided in post #1. The usb devices I have just automount when they are plugged in. For example:

```
 usb 1-2: new high speed USB device using ehci_hcd and address 5
[20330.948003] usb 1-2: configuration #1 chosen from 1 choice
[20330.949835] scsi3 : SCSI emulation for USB Mass Storage devices
[20330.950681] usb-storage: device found at 5
[20330.950690] usb-storage: waiting for device to settle before scanning
[20335.949014] usb-storage: device scan complete
[20335.949965] scsi 3:0:0:0: Direct-Access     WD       3200BMV External 1.05 PQ: 0 ANSI: 4
[20335.957514] sd 3:0:0:0: [sdc] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[20335.959375] sd 3:0:0:0: [sdc] Write Protect is off
[20335.959395] sd 3:0:0:0: [sdc] Mode Sense: 21 00 00 00
[20335.959409] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[20335.964002] sd 3:0:0:0: [sdc] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[20335.966109] sd 3:0:0:0: [sdc] Write Protect is off
[20335.966128] sd 3:0:0:0: [sdc] Mode Sense: 21 00 00 00
[20335.966141] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[20335.966168]  sdc: sdc1 sdc2
[20336.011999] sd 3:0:0:0: [sdc] Attached SCSI disk
[20336.013487] sd 3:0:0:0: Attached scsi generic sg2 type 0

```

You obviously don't want to identify the divice, which may or may not be useful information, but that being the case, there is very little one can do. Hope you'll figure is out.

---

### Post by CaptainMark on 2009-10-16
so im a tad confused as to what youve tried and what you havent, do the following codes work or not```
sudo mkdir /mnt/USB/
``````
sudo mount /dev/sdb1 /mnt/USB
```if it doesnt do you get an error message

---

### Post by anewguy on 2009-10-16
Can you give us the name and model of what you are working on?  The output you showed in your first post shows a ft232rl being recognized, and that is a USB to serial (UART) converter.  What is the storage device - name/brand/interface?

Dave :)

---

### Post by LiaGalanodel on 2009-10-26
Okay find!

Thank you!

---

