---
title: "Ubuntu doesn't mount any removable devices?"
date: 2009-10-04
forum: New to Ubuntu
---

### Post by dvdhaar on 2009-10-04
Hi there,

I noticed I've got this problem with USB sticks, CD / DVD's, external HDD's etc. It wouldn't automount the devices I put in, I could just use
```

sudo mount /dev/something /media/something

```
and it would work. But just now I put in my phone via USB and I wanted to mount it manually:

```

daniel@daniel:~$ sudo mount /dev/sawk: cannot open /etc/fstab (Permission denied)

```

I typed "sudo mount /dev/sdb" and pressed tab, then I got the "awk: cannot open /etc/fstab (Permission denied)" text filled in?!

Very strange...

dmesg:

```

[10720.003226] hub 6-0:1.0: unable to enumerate USB device on port 1
[11079.904021] usb 2-2: new high speed USB device using ehci_hcd and address 3
[11081.510909] usb 2-2: configuration #1 chosen from 1 choice
[11081.538740] Initializing USB Mass Storage driver...
[11081.548022] scsi6 : SCSI emulation for USB Mass Storage devices
[11081.548107] usb-storage: device found at 3
[11081.548109] usb-storage: waiting for device to settle before scanning
[11081.548115] usbcore: registered new interface driver usb-storage
[11081.548118] USB Mass Storage support registered.
[11086.548144] usb-storage: device scan complete
[11086.548757] scsi 6:0:0:0: Direct-Access     USB Mass Storage Device        PQ: 0 ANSI: 2
[11087.938409] sd 6:0:0:0: [sdb] 16055296 512-byte hardware sectors: (8.22 GB/7.65 GiB)
[11087.938905] sd 6:0:0:0: [sdb] Write Protect is off
[11087.938907] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[11087.938909] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[11087.941405] sd 6:0:0:0: [sdb] 16055296 512-byte hardware sectors: (8.22 GB/7.65 GiB)
[11087.941902] sd 6:0:0:0: [sdb] Write Protect is off
[11087.941904] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[11087.941905] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[11087.941909]  sdb: sdb1
[11087.942891] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[11087.942953] sd 6:0:0:0: Attached scsi generic sg3 type 0
[11648.204525] usb 2-2: USB disconnect, address 3
[11652.164520] usb 2-2: new high speed USB device using ehci_hcd and address 4
[11653.765810] usb 2-2: configuration #1 chosen from 1 choice
[11653.776961] scsi7 : SCSI emulation for USB Mass Storage devices
[11653.778125] usb-storage: device found at 4
[11653.778127] usb-storage: waiting for device to settle before scanning
[11658.778215] usb-storage: device scan complete
[11658.778826] scsi 7:0:0:0: Direct-Access     USB Mass Storage Device        PQ: 0 ANSI: 2
[11660.174353] sd 7:0:0:0: [sdb] 16055296 512-byte hardware sectors: (8.22 GB/7.65 GiB)
[11660.174846] sd 7:0:0:0: [sdb] Write Protect is off
[11660.174848] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[11660.174850] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[11660.176349] sd 7:0:0:0: [sdb] 16055296 512-byte hardware sectors: (8.22 GB/7.65 GiB)
[11660.177081] sd 7:0:0:0: [sdb] Write Protect is off
[11660.177083] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[11660.177085] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[11660.177088]  sdb: sdb1
[11660.178066] sd 7:0:0:0: [sdb] Attached SCSI removable disk
[11660.178129] sd 7:0:0:0: Attached scsi generic sg3 type 0

```

---

### Post by SuperSonic4 on 2009-10-04
```
sudo mkdir /media/Phone
sudo mount -t vfat /dev/[COLOR="Red"]sdb1[/COLOR] /media/Phone
```

Where sdb1 is the location of your phone (you can check this with ```
sudo fdisk -l
```

---

### Post by dvdhaar on 2009-10-04
> **SuperSonic4 said:**
> ```
sudo mkdir /media/Phone
sudo mount -t vfat /dev/[COLOR="Red"]sdb1[/COLOR] /media/Phone
```

Where sdb1 is the location of your phone (you can check this with ```
sudo fdisk -l
```

I know how to mount manually via the CLI but I wonder why it doesn't automatically mount like it used to do?

---

