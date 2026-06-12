---
title: "Files disappear"
date: 2010-02-27
forum: New to Ubuntu
---

### Post by newpreludeking on 2010-02-27
ok

I have installed Ubundu 8.0.4.

Got 10GB primary HDD
and 160 GB second HDD.

I partition my secondary HDD in 97,47,28 GBs..

What ever I am storing in my 97.1GB drive are disappearing. I restart the machines.. it runs scandisk saying the system shutdown was not proper eventho I did shutdown properly. Then the files re appear. And after sometime the files are again disappearing..

Is this something to do with HDD ? 

Thanks for your help.

---

### Post by philinux on 2010-02-27
Scandisk is windows. :confused:

Open a terminal.

```
sudo fdisk -l
```

Post back the result.

---

### Post by newpreludeking on 2010-02-27
thanks mate it is running fsck. too much windows usage recently. :)

If I put the command sudo fsck -l it is displaying the syntax for me.

I unmounted the drive 

$sudo umount /dev/sdb3
$sudo fsck /dev/sdb3
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
/dev/sdb3: clean, 92/5931008 files, 3098703/23711940 blocks

This is the output I got.

(oops.. I am yet to run fdisk. will run and post the result shortly.)


Thanks

---

### Post by newpreludeking on 2010-02-27
here is the output of sudo fdisk -l

Disk /dev/sda: 10.0 GB, 10005037056 bytes
255 heads, 63 sectors/track, 1216 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc75cc75c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1158     9301603+  83  Linux
/dev/sda2            1159        1216      465885    5  Extended
/dev/sda5            1159        1216      465853+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00071c32

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2550    20482843+   b  W95 FAT32
/dev/sdb2            2551        7649    40957717+  83  Linux
/dev/sdb3            7650       19457    94847760   83  Linux

Thanks

---

### Post by newpreludeking on 2010-03-10
now during the boot I am getting this error

DRDY ERR

part of the error is 

[   81.454083] ata2.00: status: { DRDY ERR }
[   81.454150] ata2.00: error: { ICRC ABRT }
[   81.454245] ata2: soft resetting link
[   81.725674] ata2.00: configured for UDMA/66
[   81.725695] ata2: EH complete
[   82.420931] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[   82.421016] ata2.00: BMDMA stat 0x24
[   82.421087] ata2.00: cmd 25/00:08:b9:8a:a1/00:00:12:00:00/e0 tag 0 dma 4096 in
[   82.421089]          res 51/84:01:c0:8a:a1/84:00:12:00:00/e0 Emask 0x10 (ATA bus error)
[   82.421167] ata2.00: status: { DRDY ERR }
[   82.421230] ata2.00: error: { ICRC ABRT }
[   82.421324] ata2: soft resetting link
[   82.695139] ata2.00: configured for UDMA/66
[   82.695162] ata2: EH complete
[   83.352304] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[   83.352396] ata2.00: BMDMA stat 0x24
[   83.352467] ata2.00: cmd 25/00:08:b9:8a:a1/00:00:12:00:00/e0 tag 0 dma 4096 in
[   83.352469]          res 51/84:01:c0:8a:a1/84:00:12:00:00/e0 Emask 0x10 (ATA bus error)
[   83.352559] ata2.00: status: { DRDY ERR }
[   83.352622] ata2.00: error: { ICRC ABRT }
[   83.352716] ata2: soft resetting link
[   83.624634] ata2.00: configured for UDMA/66
[   83.624663] ata2: EH complete
[   84.269864] ata2.00: limiting speed to UDMA/33:PIO4
[   84.269879] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[   84.269957] ata2.00: BMDMA stat 0x24
[   84.270026] ata2.00: cmd 25/00:08:b9:8a:a1/00:00:12:00:00/e0 tag 0 dma 4096 in
[   84.270028]          res 51/84:01:c0:8a:a1/84:00:12:00:00/e0 Emask 0x10 (ATA bus error)


I copied the above from dmesg.

Can any one help me in fixing this ? before showing this message it is also showing 
No resume image... doing normal boot.

Thanks

---

