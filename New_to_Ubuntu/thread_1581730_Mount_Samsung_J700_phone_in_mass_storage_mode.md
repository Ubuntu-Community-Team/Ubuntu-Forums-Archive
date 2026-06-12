---
title: "Mount Samsung J700 phone in mass storage mode"
date: 2010-09-25
forum: New to Ubuntu
---

### Post by pzs on 2010-09-25
I'm running Ubuntu 10.04. I've plugged the phone in and get this from dmesg:

```

[ 1681.950045] usb 2-5: new full speed USB device using ohci_hcd and address 9
[ 1682.189725] usb 2-5: configuration #2 chosen from 1 choice
[ 1682.195774] scsi11 : SCSI emulation for USB Mass Storage devices
[ 1682.195856] usb-storage: device found at 9
[ 1682.195859] usb-storage: waiting for device to settle before scanning
[ 1687.191713] usb-storage: device scan complete
[ 1687.198670] scsi 11:0:0:0: Direct-Access     NXP MS   Dev. 0 LUN 0     1.17 PQ: 0 ANSI: 0
[ 1687.199277] sd 11:0:0:0: Attached scsi generic sg2 type 0
[ 1687.220658] sd 11:0:0:0: [sdb] Attached SCSI removable disk
```

But it's not mounted anywhere and as you can see it doesn't give me a specific device to mount. 

It's not listed under fdisk -l, but it is listed by lsusb:

```

Bus 002 Device 009: ID 04e8:665c Samsung Electronics Co., Ltd 
```

Any ideas?

---

