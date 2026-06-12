---
title: "more space for /"
date: 2009-07-06
forum: New to Ubuntu
---

### Post by Illender on 2009-07-06
tI keep trying to install packages and it tels me I have no space on /, yet I have free space on the hard drive, how do I allocate that free space to directory /?

---

### Post by taurus on 2009-07-06
It depends where that "free" space is located.  Open a terminal and post the outputs of these commands here, running one command at a time.

Applications -> Accessories -> Terminal
```
sudo fdisk -lu
cat /etc/fstab
df -h
```

---

### Post by Illender on 2009-07-06
ok.

jaeson@MAXITRON:~$ sudo fdisk -lu
[sudo] password for jaeson: 

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xceffceff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    72886904    36443421    7  HPFS/NTFS
/dev/sda2        78124095    78140159        8032+  83  Linux
/dev/sda3        72886905    78124094     2618595    5  Extended
/dev/sda5        72886968    77770664     2441848+  83  Linux
/dev/sda6        77770728    78124094      176683+  82  Linux swap / Solaris

Partition table entries are not in disk order


jaeson@MAXITRON:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=06e7d3b3-e8ec-49cb-bb7b-62399e4a4760 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=385bb3d5-b632-4b46-8d24-724d7babdb09 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
jaeson@MAXITRON:~$ 

jaeson@MAXITRON:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             2.3G  2.3G     0 100% /
tmpfs                 249M     0  249M   0% /lib/init/rw
varrun                249M  108K  249M   1% /var/run
varlock               249M  4.0K  249M   1% /var/lock
udev                  249M  160K  249M   1% /dev
tmpfs                 249M   92K  249M   1% /dev/shm
lrm                   249M  2.4M  247M   1% /lib/modules/2.6.28-11-generic/volatile
overflow              1.0M  1.0M     0 100% /tmp
/dev/sda2             7.6M  1.1M  6.2M  15% /media/test
/dev/sda1              35G   28G  7.8G  78% /media/disk

---

### Post by taurus on 2009-07-06
Do you want to shrink a partition and expand another to take up that space?

---

### Post by TheNosh on 2009-07-06
well i'm no expert in this (so i could be wrong) but i'm pretty sure / would have to be unmounted, so you would need to do it from a live cd or usb (or xp if that's doable)

also i think the free space hast to be next to the / partition, but again, i could be wrong

edit--
sorry, i opened this thread like 2 minutes after the first post was made, and then took like twenty minutes to post. i didn't refresh the page so i didn't notice there was already help being given

---

### Post by Illender on 2009-07-06
> **taurus said:**
> Do you want to shrink a partition and expand another to take up that space?

Is that what I have to do to use the 7gig I know I have?  will it cause me to lose any files on the partition I'm taking from?

---

### Post by Illender on 2009-07-06
> **TheNosh said:**
> well i'm no expert in this (so i could be wrong) but i'm pretty sure / would have to be unmounted, so you would need to do it from a live cd or usb (or xp if that's doable)

also i think the free space hast to be next to the / partition, but again, i could be wrong

edit--
sorry, i opened this thread like 2 minutes after the first post was made, and then took like twenty minutes to post. i didn't refresh the page so i didn't notice there was already help being given



no sweat, I appreciate all the help, I'm a total noob to this. my windows xp crashed hard and the disk was fried, so I thought, well, I try tis here ubuntu I ordered like 3 months ago, and not only did it work, but was way simpler setting up my mobile broadband.  sold me thats for sure. anyway, that might why I couldnt enlarge it eh?  load from my live cd? I can do that.

---

### Post by CatKiller on 2009-07-07
> **Illender said:**
> Is that what I have to do to use the 7gig I know I have?  will it cause me to lose any files on the partition I'm taking from?

In principle, no. In the real world, backup anything that you'll miss, just in case.

On the live cd there's a Partition Editor. It's pretty straightforward to use; you just drag boxes around. You may need to unmount your swap partition if you have to change it in any way.

---

### Post by Illender on 2009-08-09
Thanks all for the help, I'm now a successful convert with no windows, and no desire to switch back.

If a mod sees this I would consider this thread closed.
So long and thanks for all the phish.

---

