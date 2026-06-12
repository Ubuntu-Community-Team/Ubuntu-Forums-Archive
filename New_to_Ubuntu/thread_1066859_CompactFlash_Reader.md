---
title: "CompactFlash Reader"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by jshi on 2009-02-11
I have a CompactFlash reader, Model No.: CR-V7-UC, it works with Windows XP but it doesn't work with Ubuntu 8.10. Here is the output of sg_map. I was wondering why I'm not seeing the mapping for /dev/sg2 which is my CompactFlash reader.

jing@ubuntu:/var/log$ sudo sg_map -i
/dev/sg0  /dev/scd0  Optiarc   DVD+-RW AD-5540A  103C
/dev/sg1  /dev/sda  ATA       Hitachi HTS72108  MC4O
/dev/sg2  Generic   STORAGE DEVICE    0.01

And I see the following messages:
Feb 11 10:43:55 ubuntu kernel: [13009.496207] usb 4-1: new full speed USB device using uhci_hcd and address 5
Feb 11 10:43:55 ubuntu kernel: [13009.659754] usb 4-1: configuration #1 chosen from 1 choice
Feb 11 10:43:55 ubuntu kernel: [13009.673190] scsi6 : SCSI emulation for USB Mass Storage devices
Feb 11 10:44:00 ubuntu kernel: [13014.681023] scsi 6:0:0:0: Direct-Access     Generic  STORAGE DEVICE   0.01 PQ: 0 ANSI: 0
Feb 11 10:44:00 ubuntu kernel: [13014.687942] sd 6:0:0:0: [sdb] 2046241 512-byte hardware sectors (1048 MB)
Feb 11 10:44:00 ubuntu kernel: [13014.693907] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
Feb 11 10:44:00 ubuntu kernel: [13014.702983] sd 6:0:0:0: [sdb] 2046241 512-byte hardware sectors (1048 MB)
Feb 11 10:44:00 ubuntu kernel: [13014.713928] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
Feb 11 10:44:00 ubuntu kernel: [13014.713954]  sdb: sdb1
Feb 11 10:44:00 ubuntu kernel: [13014.723061] sd 6:0:0:0: [sdb] Attached SCSI removable disk
Feb 11 10:44:00 ubuntu kernel: [13014.723281] sd 6:0:0:0: Attached scsi generic sg2 type 0

Is there anything I can do about it?

Thanks

---

### Post by kansasnoob on 2009-02-11
I would try installing pmount from synaptic or:

```
sudo apt-get install pmount
```

Brief description from synaptic:

> mount removable devices as normal user
pmount is a wrapper around the standard mount program which permits normal
users to mount removable devices without a matching /etc/fstab entry. This
provides a robust basis for automounting frameworks like GNOME's Utopia
project and confines the amount of code that runs as root to a minimum.

This package also contains a wrapper "pmount-hal" which reads some
information like device labels and mount options from hal and passes
them to pmount. Install the package "hal" if you want to use this
feature.

If a LUKS capable cryptsetup package is installed, pmount is able to
transparently mount encrypted volumes.

You'll probably have to restart for hal to recognize the change.

---

