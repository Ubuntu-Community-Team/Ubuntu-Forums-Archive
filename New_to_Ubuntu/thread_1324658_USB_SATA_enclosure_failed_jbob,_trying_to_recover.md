---
title: "USB SATA enclosure failed jbob, trying to recover"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by davvozz1 on 2009-11-12
hiya,

sorry this is my first post have a problem with a failed enclosure. usb to sata 2 drives they were in a jbod. the sata/usb controller is a jmicron jmc20316.
the enclosure controller pcb has failed and no spares available, unit not available anywhere listed but none in stock.

1 Terrabyte unit with 2 * 500G drives

Support for enclosure will not give much away..literal response was      "linux jbod"

drive 0 in a pc is readable has a "fat" files easy to recover, but none of the important data is on there.

the second drive has no index just raw blocks of data,  recovery tools see sector chains but not easily recoverable. As the owner  i'm just helping....the guys in trouble

I'm thinking the jbod had a master "fat" table on the first drive and the second drive should run from that.

I tried mdadm but this does n't seem to like the abbrieviated uuid on the 0 drive,

When I saw that dmraid was often used to recover data I swapped from an older ubuntu to the one I had at hand which is Ultimate Op Sys based on Ubu 9.04 Installed dmraid.

dmraid auto mount only sees the imbedded raid on the PC motherboard.

So what do I do next. dmsetup has an example for a linear 2 disk raid, how do I configure this ?

output:
 ========
example from dmsetup man file

# A table to join two disks together
       0 1028160 linear /dev/hda 0
       1028160 3903762 linear /dev/hdb 0

==========
UUID of master/leading if that is the correct term, or the volume with 
14FF-1D79

/dev/sdc1: LABEL="FREECOM HDD" UUID="14FF-1D79" TYPE="vfat"

=========================

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x78b82d89

   Device Boot      Start         End      Blocks   Id  System

=======================================
Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x78b82d89

   Device Boot      Start         End      Blocks   Id  System
=============================================

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf68e9bf2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121602   976768033+   6  FAT16

============================================

dmraid -ay
RAID set "nvidia_eaefijac" was not activated

============================================
dmraid version:        1.0.0.rc15 (2008-09-17) shared 
dmraid library version:    1.0.0.rc15 (2008.09.17)
device-mapper version:    4.14.0

---

