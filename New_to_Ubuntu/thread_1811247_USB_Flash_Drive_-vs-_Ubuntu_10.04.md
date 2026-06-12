---
title: "USB Flash Drive -vs- Ubuntu 10.04"
date: 2011-07-24
forum: New to Ubuntu
---

### Post by pivotal.epiphany on 2011-07-24
**OS: **Ubuntu 10.04 LTS
**Device: **PNY USB Flash Drive 16 GB
**Issue: **Device does not auto-mount and can't browse contents.

[B]lsusb:
[/B]Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 0461:4d15 Primax Electronics, Ltd Dell Optical Mouse
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 154b:6545 PNY 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[B]

dmesg | grep usb:[/B]
[    0.320052] usbcore: registered new interface driver usbfs
[    0.320070] usbcore: registered new interface driver hub
[    0.320107] usbcore: registered new device driver usb
[    0.552347] usb usb1: configuration #1 chosen from 1 choice
[    0.564397] usb usb2: configuration #1 chosen from 1 choice
[    0.564846] usb usb3: configuration #1 chosen from 1 choice
[    0.565139] usb usb4: configuration #1 chosen from 1 choice
[    0.565428] usb usb5: configuration #1 chosen from 1 choice
[    0.565729] usb usb6: configuration #1 chosen from 1 choice
[    0.566040] usb usb7: configuration #1 chosen from 1 choice
[    0.566329] usb usb8: configuration #1 chosen from 1 choice
[    1.035790] usb 2-2: new high speed USB device using ehci_hcd and address 3
[    1.208975] usb 2-2: configuration #1 chosen from 1 choice
[    1.448024] usb 7-1: new low speed USB device using uhci_hcd and address 2
[    1.616230] usb 7-1: configuration #1 chosen from 1 choice
[    2.683578] usbcore: registered new interface driver usb-storage
[    2.683734] usb-storage: device found at 3
[    2.683737] usb-storage: waiting for device to settle before scanning
[    2.684665] usbcore: registered new interface driver hiddev
[    2.941196] input: USB Optical Mouse as /devices/pci0000:00/0000:00:1e.0/0000:02:02.0/usb7/7-1/7-1:1.0/input/input4
[    2.941477] generic-usb 0003:0461:4D15.0001: input,hidraw0: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:02:02.0-1/input0
[    2.941513] usbcore: registered new interface driver usbhid
[    2.941653] usbhid: v2.6:USB HID core driver
[    7.680281] usb-storage: device scan complete
[ 1390.359231] usb 2-2: USB disconnect, address 3
[ 1411.176035] usb 2-3: new high speed USB device using ehci_hcd and address 4
[ 1411.309112] usb 2-3: configuration #1 chosen from 1 choice
[ 1411.325679] usb-storage: device found at 4
[ 1411.325683] usb-storage: waiting for device to settle before scanning
[ 1416.324231] usb-storage: device scan complete
[ 2514.572047] usb 2-3: USB disconnect, address 4
[ 2516.400042] usb 2-3: new high speed USB device using ehci_hcd and address 5
[ 2516.533054] usb 2-3: configuration #1 chosen from 1 choice
[ 2516.549844] usb-storage: device found at 5
[ 2516.549848] usb-storage: waiting for device to settle before scanning
[ 2521.548292] usb-storage: device scan complete[B]

/etc/fstab:
[/B]# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=a7c7f46f-25a9-46d9-8617-94aa8e8b49d6 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb1 /mnt/usbflash vfat noauto,users,rw,umask=0 0 0
[LEFT]**(^This last line was added as part of my troubleshooting.)**
[/LEFT]

Once upon a time, the USB Device would appear in my **Places** folder. This is no longer the case.
**IMPORTANT NOTE: **The device _DOES_ show up in my **DISK UTILITY. **These are the results of trying to mount it there:
[I]"Error mounting: mount exited with exit code 1: helper failed with:
mount: according to mtab, /dev/sda1 is already mounted on /
mount failed" ~ MOUNT POINT: Not Mounted
[/I]Device is listed in the DISK UTILITY as: /dev/sdb

ALSO, from this utility I _CAN_ delete the partition, format it, etc... just cannot mount it.

Any help would be greatly appreciated. Thanks in advance.

---

### Post by ajgreeny on 2011-07-24
> **pivotal.epiphany said:**
> [B]
/etc/fstab:
[/B]# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
[COLOR=Red]/dev/sdb1       /               ext4    errors=remount-ro 0       1[/COLOR]
# swap was on /dev/sdb5 during installation
UUID=a7c7f46f-25a9-46d9-8617-94aa8e8b49d6 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb1 /mnt/usbflash vfat noauto,users,rw,umask=0 0 0

I think you have a problem with your /etc/fstab, or in your naming of the usb flash drive.  Only one of them can be /dev/sdb1, not both.   Can you therefore run ```
sudo fdisk -l
``` with the flash drive attached and report the output back here

To sort this problem, or at least get a bit of extra info to try and help, it would be useful to have the UUID of your drives, so please can you run ```
sudo blkid
``` in terminal and either report the output back here, or simply edit your fstab file, having first backed it up, and then use the UUID in the line in red above, rather than the /dev/sdb1 naming it has at present.     You should also delete that final line in fstab, as adding a  fat32 flash drive to fstab will confuse the system (and me) even  further.  Then run ```
sudo mount -a
``` to see if any errors occur.

---

