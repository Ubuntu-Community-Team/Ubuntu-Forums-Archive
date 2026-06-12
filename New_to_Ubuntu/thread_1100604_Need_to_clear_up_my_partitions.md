---
title: "Need to clear up my partitions"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by sp176 on 2009-03-19
Originally I used only ubuntu.  Then I wished to switch to dual windows and ubuntu.  I have 2 problems: I find that my windows partition is too small, and I cannot install any games.  I also believe that their is an extra partition from my old version of ubuntu.  Can you help me clear this up, and let me play games on windows? 

The sda1 (windows) partition is ntfs 3.02 GB with 3.01 GB filled.  Therefore no space, and I cannot access any other part of the drive.
sda2 is extended at 1.83 GB, and seems to contain sda5,6,7
sda5 is linux-swap at 1.43 GB
sda7 is linux-swap at 1.43 GB
sda6 is ext3 at 180 GB

There also seems to be a symbol of keys on sda2,6,7 which make think this is my current ubuntu partition, and sda5 is my old one.

I tried to upload my screenshot, but it didnt work, so if you could also tell me that I would appreciate it.  It was a png file, and according to the file size it should have been acceptable.

---

### Post by taurus on 2009-03-19
Open a terminal and post the outputs of these commands.

Applications -> Accessories -> Terminal
```
sudo fdisk -lu
cat /etc/fstab
df -h
```

---

### Post by sp176 on 2009-03-19
sudo fdisk -lu

```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x87d236a8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63     6329609     3164773+   7  HPFS/NTFS
/dev/sda2         6329610   390716864   192193627+   5  Extended
/dev/sda5       387712773   390716864     1502046   82  Linux swap / Solaris
/dev/sda6         6329736   384708554   189189409+  83  Linux
/dev/sda7       384708618   387712709     1502046   82  Linux swap / Solaris

Partition table entries are not in disk order
```

cat /etc/fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=eb139bdc-8b09-4ebd-9554-37a01e550fd3 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=0276ccf4-9516-40b7-944d-cd48ae8d31f2 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

```

df -h

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             178G  4.3G  165G   3% /
tmpfs                 252M     0  252M   0% /lib/init/rw
varrun                252M  100K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
udev                  252M  2.9M  249M   2% /dev
tmpfs                 252M  520K  251M   1% /dev/shm
lrm                   252M  2.0M  250M   1% /lib/modules/2.6.27-7-generic/volatile
/dev/scd1             655M  655M     0 100% /media/cdrom0

```

---

### Post by taurus on 2009-03-19
This is going to be fun if you are up to it.  You are only using one swap partition, /dev/sda7, even though you have two.  However, the second one that you are not using, /dev/sda5, is at the end of the disk so you just cannot delete that partition that "give" that allocated space to your windows, /dev/sda1.  You need to expand /dev/sda7 to take up that allocated space first.  Then, shrink /dev/sda7, making unallocated space at the beginning.  Now, you have to expand /dev/sda6 to take up that unallocated space left behind by shrinking /dev/sda7.  The next step is to shrink /dev/sda6, creating unallocated space at the beginning and then shrink your extended partition, creating an unallocated partition outside of your extended partition, /dev/sda2.  And the last step is to expand your windows partition, /dev/sda1, to incorporate that new unallocated space behind it.  

Good luck.

---

### Post by sp176 on 2009-03-19
Ok, I understand your logic...I hope, lol!

I am not that familiar with partitions. I figure I should use system/admin/partition editor... correct?  Can you tell me how to manipulate them?  I see the options to delete/resize, etc., but only on the partitions not in use and I don't want to make it worse.

I will attempt this, but I guess what I really want is what do I do if this fails, is there a way to wipe everything if necessary and start from scratch.  I got everything backed up.

---

### Post by sp176 on 2009-03-19
Laugh at my illustration if you will, but does it go something like this:


|--sda1--||-----sda6--------------||sda7||sda5|
|--sda1--||-----sda6--------------||---sda7---|
|--sda1--||-----sda6--------------------||sda7|
|--sda1-----------|-------sda6----------||sda7|

---

### Post by taurus on 2009-03-19
Instead of shrinking and expanding a few times, maybe it's easier for you to just remove all the partitions with gparted from Ubuntu LiveCD (System -> Administration -> Partition Editor).  Then, create two primary partitions and format the first one to ntfs filesystem.  Then, install windows on that first partition and install Ubuntu on the second partition.  Less chance of screw ups.

---

### Post by sp176 on 2009-03-19
The 2 sizes of the partitions do not seem to add up to my total.

Nevermind...I can't do math today.


Much appreciated, this worked great.  I am now going to install my O/S, which I hope never to do again!

---

### Post by sp176 on 2009-03-19
Ok, this did not work great...I got an error message.

Error informing the kernel about modifications to partition /dev/sda -- Device or resource busy.  This means Linux won't know about any changes you made to /dev/sda1 until you reboot -- so you shouldn't mount it or use in any way before rebooting.
The kernel was unable to re-read the partition table on /dev/sda (Device or resource busy).

Repeats message again.

What?  I just reboot and do again, that seems silly.

---

### Post by taurus on 2009-03-19
Did you remember to unmount the swap partitions (highlight the swap parition, one at a time, and click the right button -> swapoff) first in gparted from the LiveCD?

---

### Post by sp176 on 2009-03-19
All good now.

No, I didnt swapoff, I just deleted.  I guess this doesnt agree with the partition editor, it needs to restart if you do it that way. Partitions are set-up now.

Thanks again.

---

