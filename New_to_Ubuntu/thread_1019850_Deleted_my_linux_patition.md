---
title: "Deleted my linux patition"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by ibizatunes on 2008-12-23
I selected the wrong disk from within windows and deleted my linux partition fom within window xp, if there anyway of recovering my data - it has all my data on it :-(

---

### Post by Titan8990 on 2008-12-23
Restore from your most recent backup.

---

### Post by ibizatunes on 2008-12-23
Yeah i would like that, but i have lost about 100GB of new data.... So that isnt really the answer im lucking for!

---

### Post by shad0w_walker on 2008-12-23
If you haven't written anything to the new disk, it may be possible to recover the partition table. I would suggest you investigate testdisk, which can scan drives and find any partitions on it then rewrite the partition table, however, if you have started writing to the drive, it's possible that the data has already been overwritten (Atleast partly)

---

### Post by ibizatunes on 2008-12-23
I have restore my partition but on my live disk I get this error
mount wrong fs type,bad option, bad super block on sda/dev2 missing codepage or help program, or other error
In some case useful info is found in syslog - try dmesg or so

---

### Post by ibizatunes on 2008-12-23
```
  271.818244] EXT3-fs error (device sda2): ext3_check_descriptors: Block bitmap for group 880 not in group (block 0)!
[  271.820069] EXT3-fs: group descriptors corrupted!
[  301.774042] EXT3-fs error (device sda2): ext3_check_descriptors: Block bitmap for group 880 not in group (block 0)!
[  301.775976] EXT3-fs: group descriptors corrupted!
[  347.710690] EXT3-fs error (device sda2): ext3_check_descriptors: Block bitmap for group 880 not in group (block 0)!
[  347.712629] EXT3-fs: group descriptors corrupted!
[  347.927125] EXT3-fs error (device sda2): ext3_check_descriptors: Block bitmap for group 880 not in group (block 0)!
[  347.929009] EXT3-fs: group descriptors corrupted!
[  348.655219] EXT3-fs error (device sda2): ext3_check_descriptors: Block bitmap for group 880 not in group (block 0)!
[  348.657088] EXT3-fs: group descriptors corrupted!
[  354.149760] NET: Registered protocol family 10
[  354.151013] lo: Disabled Privacy Extensions
[  364.556019] eth0: no IPv6 routers present
[  417.287670] EXT3-fs error (device sda2): ext3_check_descriptors: Block bitmap for group 880 not in group (block 0)!
[  417.289512] EXT3-fs: group descriptors corrupted!

```

---

### Post by Cannaregio on 2008-12-23
You might try the following (no guarantee it will work) to recover your harddisk: 

Start a live CD with ubuntu on it
check on Gparted to make absolutely sure that your partition is -say- on /dev/sda2

use following command:

```
e2fsck -b 32768 /dev/sda2
```

(of course change that [COLOR="Blue"]sda2[/COLOR] if your disk is different)

Once e2fsck starts and begins asking the sector verifications, just keep the "[COLOR="Blue"]Y[/COLOR]" key pressed and cross your fingers.

Cheers!

---

### Post by ibizatunes on 2008-12-23
```
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

Im running ext3 is that a issue? What if i ran on the live session gparted - check the disk would that help?

---

### Post by timandjulz on 2008-12-23
ext3 is the same as ext3 except with journaling.  All the ext2 utilities work on ext3.

---

