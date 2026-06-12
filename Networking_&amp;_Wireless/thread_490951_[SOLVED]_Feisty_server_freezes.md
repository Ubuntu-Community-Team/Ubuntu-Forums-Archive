---
title: "[SOLVED] Feisty server freezes"
date: 2007-07-03
forum: Networking &amp; Wireless
---

### Post by lexarrow on 2007-07-03
Hello,

I am running a Feisty server with 2 sata hard drives. One has 2 NTFS partitions (I use ntfs-3g), the other one has a linux partition. Everything works fine (LAMP&stuff) but after awhile it freezes. Here's what I get in the log:
```
Jul  3 09:05:50 sopolec kernel: [  438.046304] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jul  3 09:05:50 sopolec kernel: [  438.046313] ata3.00: (BMDMA stat 0x26)
Jul  3 09:05:50 sopolec kernel: [  438.046320] ata3.00: cmd 35/00:50:27:b2:f5/00:03:11:00:00/e0 tag 0 cdb 0x0 data 434176 out
Jul  3 09:05:50 sopolec kernel: [  438.046322]          res 51/84:f0:87:b4:f5/84:00:11:00:00/e0 Emask 0x20 (host bus error)
Jul  3 09:05:50 sopolec kernel: [  438.076090] ata3.00: ata_hpa_resize 1: sectors = 312581808, hpa_sectors = 312581808
Jul  3 09:05:50 sopolec kernel: [  438.084698] ata3.00: ata_hpa_resize 1: sectors = 312581808, hpa_sectors = 312581808
Jul  3 09:05:50 sopolec kernel: [  438.084707] ata3.00: configured for UDMA/133
Jul  3 09:05:50 sopolec kernel: [  438.084727] ata3: EH complete
Jul  3 09:05:50 sopolec kernel: [  438.108355] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
Jul  3 09:05:50 sopolec kernel: [  438.109427] sda: Write Protect is off
Jul  3 09:05:50 sopolec kernel: [  438.109434] sda: Mode Sense: 00 3a 00 00
Jul  3 09:05:50 sopolec kernel: [  438.110456] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
```

Any help would be much appreciated.

Thanks!

---

### Post by lexarrow on 2007-07-18
It was solved by updates

---

