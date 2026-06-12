---
title: "problems trying to delete luks partition"
date: 2010-03-16
forum: New to Ubuntu
---

### Post by UnMeilleurReve on 2010-03-16
Hey all,

So I encrypted my secondary partition that was empty using LUKS on a solid state drive. I guess I accidentally entered the wrong spelling of my password twice or something, and now have lost total access to it. I can't mount or delete the partition at all, and it's frustrating. Here's the details of my error message:

Error erasing: helper exited with exit code 1: In part_del_partition: device_file=/dev/sdb, offset=32256
Entering MS-DOS parser (offset=0, size=8069677056)
MSDOS_MAGIC found
looking at part 0 (offset 32256, size 8068967424, type 0x00)
new part entry
looking at part 1 (offset 0, size 0, type 0x00)
new part entry
looking at part 2 (offset 0, size 0, type 0x00)
new part entry
looking at part 3 (offset 0, size 0, type 0x00)
new part entry
Exiting MS-DOS parser
MSDOS partition table detected
got it
got disk
got partition - part->type=4
refusing to delete a protected partition


I'd like to just delete the partition and reformat the drive as a fat32 or another appropriate filesystem. Any thoughts?

---

### Post by blazemore on 2010-03-22
> **UnMeilleurReve said:**
> Hey all,

So I encrypted my secondary partition that was empty using LUKS on a solid state drive. I guess I accidentally entered the wrong spelling of my password twice or something, and now have lost total access to it. I can't mount or delete the partition at all, and it's frustrating. Here's the details of my error message:

Error erasing: helper exited with exit code 1: In part_del_partition: device_file=/dev/sdb, offset=32256
Entering MS-DOS parser (offset=0, size=8069677056)
MSDOS_MAGIC found
looking at part 0 (offset 32256, size 8068967424, type 0x00)
new part entry
looking at part 1 (offset 0, size 0, type 0x00)
new part entry
looking at part 2 (offset 0, size 0, type 0x00)
new part entry
looking at part 3 (offset 0, size 0, type 0x00)
new part entry
Exiting MS-DOS parser
MSDOS partition table detected
got it
got disk
got partition - part->type=4
refusing to delete a protected partition


I'd like to just delete the partition and reformat the drive as a fat32 or another appropriate filesystem. Any thoughts?

Have you tried using Gparted?
[apt:gparted](apt:gparted) <--click to install

---

