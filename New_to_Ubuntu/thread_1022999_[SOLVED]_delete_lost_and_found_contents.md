---
title: "[SOLVED] delete lost and found contents"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by mesmith on 2008-12-27
Installed an old, small (4gb) hdd to my system.  Did a mkfs.ext3 and ended up with a usable hdd, but Parted says that 200mb of the drive is being used.  Can only find a lost and found folder, so I think that where this 200mb is residing.  How can |I get rid of that file usage?  I need every inch of this hdd.  It appears I am denied access to the folder, so can't do a manual delete of its contents.

---

### Post by eagle416 on 2008-12-27
if it's mounted, navigate to /media/(nameofdrive)/

and type

> sudo rm -r lost \and \found

-edit- that's assuming the folder is called "lost and found"

---

### Post by Elfy on 2008-12-27
lost and found will return - it's there for the fsck check

The space is 'missing' as it's reserved for use by root for when drive is full, default is 5%.

It's possible to change this - but I would not recommend doing so on your / drive, but I assume this is being used for storage. To change use the tune2fs command once you knwo which drive you are working with.

```
sudo fdisk -l
``` will tell you which drive is the new 4Gb one - change sdxy below to suit

```
sudo tune2fs -m [COLOR="Red"]1[/COLOR] /dev/sdxy
```

The [COLOR="Red"]number[/COLOR] tells what % is reserved - this example would reserve 1% for use by root

Post result of fdisk if at all unsure.

---

### Post by gsocker on 2008-12-27
By default, ext2 and 3 will reserve 5% of the space on the drive for the superuser(root). To change this, use  ```
mkfs.ext3 -m 0 /device
```
If you delete "lost+found" it will reappear.
Technical explanation:
The "lost+found" directory is used by the filesystem checker for "lost" files.
UNIX filesystems generally use an inode, not the file name, as the basic index to the file. The inode then has names attached to it - this is why you can have multiple names for one file.

If you just ran mkfs it will be empty. If, during a filesystem check, fsck cannot determine what file an inode it supposed to be attached to, it will place the information associated with that inode in the "lost+found" directory, with the inode number as the filename. You will need to use ```
sudo ls /path/to/dir
``` to view the contents, as the directory is only readable as the root user.

---

### Post by mesmith on 2008-12-27
Followed the above instructions to change percentage to 1%, but allocated space on 4gb drive remains at 200mb.  The second hdd is /dev/sdb1 and I followed the instructions carefully.  Did I miss something?  Rebooted and had a look with Parted, but size remains at 200mb.

---

### Post by mesmith on 2008-12-27
What fdisk command should I run (including parameters) to show you kind people what the drive looks like?  I appreciate all this help.

---

### Post by gsocker on 2008-12-28
In a terminal, run 
```
sudo fdisk -l /dev/sdb
``` This will print the partition table on the drive. 
Result should be something like this:
```
Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00041d03

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3647    29294496   83  Linux
/dev/sdb2            3648        6079    19535040   83  Linux
/dev/sdb3            6080        9726    29294527+  83  Linux
/dev/sdb4   *        9727       19457    78164257+  a5  FreeBSD

```
Try mounting the partition and running df -h (also in a terminal) and see what it reports - post results

---

### Post by mesmith on 2008-12-28
Following are results from df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              18G  3.0G   14G  18% /
tmpfs                 504M     0  504M   0% /lib/init/rw
varrun                504M  100K  504M   1% /var/run
varlock               504M     0  504M   0% /var/lock
udev                  504M  2.7M  502M   1% /dev
tmpfs                 504M     0  504M   0% /dev/shm
lrm                   504M  2.0M  502M   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sdb1             4.0G  137M  3.8G   4% /media/sdb1

sdb1 now showing 4% usage, but I have no idea why.  GParted continues to report 5% usage.

---

### Post by gsocker on 2008-12-28
Looks like the problem is the ext3 journal. Try formatting as ext2 instead of ext3:
```
mkfs -t ext2 -m 1 /dev/sdb1
```
and see what happens to the disk usage numbers. Ext3 apparently defaults to a 128MB journal. You will never see no usage as the filesystem housekeeping information does eat up some space.

With only 4G, it shouldn't take too long to check even without a journal.

---

### Post by mesmith on 2008-12-28
Thanks.  Will stick with ext3 and just manage the drive contents.

Appreciate all the advice.

---

