---
title: "Problem mounting USB external drive"
date: 2010-07-28
forum: New to Ubuntu
---

### Post by NS2-10 on 2010-07-28
Hi all,

I have trouble mounting any external drive to my computer. I recently upgraded to 10.04, but the problem was present before that. Drives dont mount in the media folder and they dont show up in fstab. However, it seems there is nothing wrong with the actual port. I can use it for my mouse and I get this printout from **dmesg**:

```
[  814.220040] usb 1-6: new high speed USB device using ehci_hcd and address 8
[  814.353887] usb 1-6: configuration #1 chosen from 1 choice
[  814.357140] scsi8 : SCSI emulation for USB Mass Storage devices
[  814.374775] usb-storage: device found at 8
[  814.374781] usb-storage: waiting for device to settle before scanning
[  819.372234] usb-storage: device scan complete
[  819.373030] scsi 8:0:0:0: Direct-Access     A-DATA   USB Flash Drive  0.00 PQ: 0 ANSI: 2
[  819.378513] sd 8:0:0:0: Attached scsi generic sg2 type 0
[  819.380818] sd 8:0:0:0: [sdb] 31588352 512-byte logical blocks: (16.1 GB/15.0 GiB)
[  819.381439] sd 8:0:0:0: [sdb] Write Protect is off
[  819.381447] sd 8:0:0:0: [sdb] Mode Sense: 00 00 00 00
[  819.381453] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[  819.393923] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[  819.393934]  sdb: sdb1
[  819.651437] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[  819.651447] sd 8:0:0:0: [sdb] Attached SCSI removable disk

```

Any suggestions on what to try?

Thnx!

---

### Post by jtarin on 2010-07-28
[How to automount configure]("https://help.ubuntu.com/community/Mount/USB")

---

### Post by muteXe on 2010-07-28
Hello there.
What command are you using to mount it?
Cheers,
mute

---

