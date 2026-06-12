---
title: "Help with mounting USB Drive in Ubuntu Server"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by chrisod on 2009-05-16
The server recognizes the drive - I get the following in dmesg after plugging it in. However, it is stopping short of actually mounting the drive. Any idea why, or what I need to do to get the drive mounted? I plugged the USB drive into my Jaunty laptop and it works fine, so it is not the drive. I noticed the dmesg messages had a few more on my laptop, including one where it specifically assigns sbd1 to the drive. It's not doing that on the server (which is 8.10)

```
May 16 15:03:36 fenway kernel: [ 8140.100046] usb 1-1: new full speed USB device using uhci_hcd and address 4
May 16 15:03:36 fenway kernel: [ 8140.272388] usb 1-1: configuration #1 chosen from 1 choice
May 16 15:03:36 fenway kernel: [ 8140.280472] scsi4 : SCSI emulation for USB Mass Storage devices
May 16 15:03:41 fenway kernel: [ 8145.285310] scsi 4:0:0:0: Direct-Access     Initio   00JB-00GVA0      1.05 PQ: 0 ANSI: 0
May 16 15:03:41 fenway kernel: [ 8145.302276] sd 4:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
May 16 15:03:41 fenway kernel: [ 8145.305228] sd 4:0:0:0: [sdb] Write Protect is off
May 16 15:03:41 fenway kernel: [ 8145.331306] sd 4:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
May 16 15:03:41 fenway kernel: [ 8145.334225] sd 4:0:0:0: [sdb] Write Protect is off
May 16 15:03:41 fenway kernel: [ 8145.334338]  sdb: sdb1
May 16 15:03:41 fenway kernel: [ 8145.356127] sd 4:0:0:0: [sdb] Attached SCSI disk
May 16 15:03:41 fenway kernel: [ 8145.356510] sd 4:0:0:0: Attached scsi generic sg2 type 0
```

---

### Post by chrisod on 2009-05-16
never mind - I figured it out. I'd delete this is I could.

---

