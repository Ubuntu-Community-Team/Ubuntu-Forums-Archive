---
title: "mounting 1tb iomega USB disk"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by nathan28 on 2009-02-09
so i am trying to find my 1tb disk (in NTFS) (it has about 100 gb on it) in Ubuntu--i used it to copy my media files onto it before installing ubuntu.

When i first plugged in the iomega disk, I got an error message: "failed to mount 'dev/sdb1': operation not supported Mount is denied because NTFS is marked to be in use [go to windows and turn it off or] use the 'force' option... mount -t ntfs-3g /dev/sdb1/media/Iomega HDD -o force or add the option to the relevant row in the etc/fstab file: /deve/sdb1/media/Iomega HDD ntfs-3g force 0 0"

so i ran

sudo mount -t ntfs-3g /deve/sdb1/media/"Iomega HDD" -o force

to no avail, then read the instructions and realized i needed a target directory. mkdir /home/[$USER]/1tbdisk, then

sudo mount -t ntfs-3g /deve/sdb1/ home/[$user]/1tbdisk -o force

and get
$LogFile indicates unclean shutdown (0, 0)
WARNING: Forced mount, reset $LogFile.
fuse: failed to access mountpoint home/mysis/1tbdisk: No such file or directory

Okay, so it's not mounted.

Then I look at Places, and right-click on the Iomega HDD in an effort to be sure i get a totally clean unmount (should have just done umount i think?). Hey, it's the file browser looking in my HDD. And Ubuntu mounts it just by plugging it in so I guess all that needed to happen was to wipe $LogFile...

...except now it says it's a "Picture CD" in Nautilus, and prompts me to open the picture viewer. What did I do?

here's the relevant results from dmesg

> 
[55151.868047] usb 3-3: new high speed USB device using ehci_hcd and address 4
[55152.004493] usb 3-3: configuration #1 chosen from 1 choice
[55152.007662] scsi3 : SCSI emulation for USB Mass Storage devices
[55152.008149] usb-storage: device found at 4
[55152.008154] usb-storage: waiting for device to settle before scanning
[55157.008251] usb-storage: device scan complete
[55157.009367] scsi 3:0:0:0: Direct-Access     ST310003 33AS                  PQ: 0 ANSI: 2 CCS
[55157.010706] sd 3:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
[55157.016593] sd 3:0:0:0: [sdb] Write Protect is off
[55157.016603] sd 3:0:0:0: [sdb] Mode Sense: 34 00 00 00
[55157.016607] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[55157.017933] sd 3:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
[55157.018929] sd 3:0:0:0: [sdb] Write Protect is off
[55157.018934] sd 3:0:0:0: [sdb] Mode Sense: 34 00 00 00
[55157.018938] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[55157.019425]  sdb: sdb1
[55157.045926] sd 3:0:0:0: [sdb] Attached SCSI disk
[55157.046340] sd 3:0:0:0: Attached scsi generic sg2 type 0


---

### Post by Felix-the-Cat on 2009-03-14
Try mounting the disk in a windows machine first and then remounting in Ubuntu.

---

