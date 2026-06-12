---
title: "flashdrive superblock corrupt: can gparted help?"
date: 2011-01-02
forum: New to Ubuntu
---

### Post by watchpocket on 2011-01-02
I'm trying to format a 32GB USB flash drive to ext3 for Linux.

     Code:
     sudo tail -f /var/log/messages 
shows me:

Jan  1 23:40:42 rj kernel: 
[13773.966516] sd 11:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[13800.780008] usb 2-1: new high speed USB device using ehci_hcd and address 8
[13800.932141] usb 2-1: configuration #1 chosen from 1 choice
[13800.932281] scsi12 : SCSI emulation for USB Mass Storage devices
[13805.932983] scsi 12:0:0:0: Direct-Access              Flash Disk       5.00 PQ: 0 ANSI: 2
[13805.933279] sd 12:0:0:0: Attached scsi generic sg3 type 0
[13805.933911] sd 12:0:0:0: [sdc] 65536000 512-byte logical blocks: (33.5 GB/31.2 GiB)
[13805.934498] sd 12:0:0:0: [sdc] Write Protect is off
[13805.936223]  sdc: sdc1
[13805.939802] sd 12:0:0:0: [sdc] Attached SCSI removable disk

And then hangs.

     Code:
     sudo fsck /dev/sdb1 
shows me:

fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
fsck.ext2: No such file or directory while trying to open /dev/sdb1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

Trying that last suggestion gives me the exact same message. Same using -b 16384

Palimpsest Disk Utility shows:
34 GB Unrecognized
Unknown or Unused

My general question is: [B][I]how can I fix the corrupted superblock and do the format?
[/I][/B]

---

### Post by mikewhatever on 2011-01-02
Just format, and it should get fixed. Fixing the file system would have been useful if you didn't want to format the partition. Since you do, a new file system will be created, along with the new superblock.

---

### Post by watchpocket on 2011-01-03
I re-formatted, can't get it to mount, though:

```
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
``````
dmesg | tail:
[ 2499.371538] sd 8:0:0:0: [sdb] 65536000 512-byte logical blocks: (33.5 GB/31.2 GiB)
[ 2499.372112] sd 8:0:0:0: [sdb] Write Protect is off
[ 2499.372115] sd 8:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[ 2499.372117] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[ 2499.373782] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[ 2499.373785]  sdb: sdb1
[ 2499.376378] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[ 2499.376380] sd 8:0:0:0: [sdb] Attached SCSI removable disk
[ 2499.453408] JBD: no valid journal superblock found
[ 2499.453410] EXT3-fs: error loading journal.
```

---

### Post by watchpocket on 2011-01-04
> a new file system will be created, along with the new superblock.

Maybe, but what should I do if it's not mounting (which it isn't)?

---

### Post by mikewhatever on 2011-01-04
Not sure really. I hope this isn't a drive failure. Did you see any errors when formatting?

---

### Post by watchpocket on 2011-01-04
I just see this, when I do a 

```
dmesg | tail:

[ 2499.453408] JBD: no valid journal superblock found
[ 2499.453410] EXT3-fs: error loading journal.
```

---

### Post by BugBuster on 2011-01-05
Use fdisk and redo the partitions and then format that partition to an fs of choice..that may help!

---

