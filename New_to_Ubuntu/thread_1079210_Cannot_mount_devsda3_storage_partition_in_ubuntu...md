---
title: "Cannot mount dev/sda3 storage partition in ubuntu...problem with fstab?"
date: 2009-02-24
forum: New to Ubuntu
---

### Post by dfa on 2009-02-24
I recently had to reinstall Windows on my dual boot PC (Windows XP and Ubuntu).  During this process I changed the layout of the partitions on my disk so that they are not in the same spot anymore, my first time using gparted.  Now when I boot into ubuntu and try to access my dev/sda3 partition, which I use for storage, it gives me an error saying it cannot mount the volume and something about the partition already being mounted on /.  

Over the past few days I've been reading over some of the forums here and have managed to get into the fstab file to change a few things but nothing has worked so far, it seems no one else has the exact same problem as me.  Basically Im stuck...If anybody could help it would be greatly appreciated.

---

### Post by caljohnsmith on 2009-02-24
How about from your Live CD, open a terminal (Applications > Accessories > Terminal) and please post the output of:
```
sudo fdisk -lu
```
Identify which is your storage partition if it is not still sda3, and also find which is your main Ubuntu partition sdaX (like sda2 for example), and then do:
```
sudo mount /dev/[COLOR="Blue"]sdaX[/COLOR] /mnt
cat /mnt/etc/fstab
sudo blkid -c /dev/null
```
Please post the output of all the above commands, and we can work from there if you want.

---

### Post by spiderbatdad on 2009-02-24
should be noted that one does not mount a device, but a file system. The above will not work on all kernels. In which case the correct mount command for ubuntu partition will more likely be :
```
sudo mount -t ext3 /dev/sda3 /mnt
cat /mnt/etc/fstab

```

---

### Post by dfa on 2009-02-24
> **caljohnsmith said:**
> How about from your Live CD, open a terminal (Applications > Accessories > Terminal) and please post the output of:
```
sudo fdisk -lu
```
Identify which is your storage partition if it is not still sda3, and also find which is your main Ubuntu partition sdaX (like sda2 for example), and then do:
```
sudo mount /dev/[COLOR="Blue"]sdaX[/COLOR] /mnt
cat /mnt/etc/fstab
sudo blkid -c /dev/null
```
Please post the output of all the above commands, and we can work from there if you want.

**Ok** here is the fdisk command output showing ubuntu as sda1 and storage as sda3.

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000452be

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    40965749    20482843+  83  Linux
/dev/sda2        40965750    41367374      200812+  82  Linux swap / Solaris
/dev/sda3        41367375   853886879   406259752+  83  Linux
/dev/sda4   *   853886880   976768064    61440592+   7  HPFS/NTFS

And then here is the rest

ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ cat /mnt/etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=6f287263-221c-485d-92c9-1f84072dd689 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2 
UUID=c3feb86c-f6d9-4a2e-be07-7eaedd84958e none            swap    sw              0       0

/dev/sda3      /media/sda3 /   ext3    defaults        0        2   
 
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

ubuntu@ubuntu:~$ sudo blkid -c /dev/null
/dev/sda1: UUID="6f287263-221c-485d-92c9-1f84072dd689" TYPE="ext3" 
/dev/sda2: UUID="c3feb86c-f6d9-4a2e-be07-7eaedd84958e" TYPE="swap" 
/dev/sda3: UUID="d7a948ff-8aaa-4f34-a8c6-cabce8e7bf9f" TYPE="ext3" 
/dev/sda4: UUID="283C78693C783442" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs" 
ubuntu@ubuntu:~$ 

Thank you very much for helping with this problem.

---

### Post by taurus on 2009-02-24
> **dfa said:**
> **Ok** here is the fdisk command output showing ubuntu as sda1 and storage as sda3.

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000452be

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    40965749    20482843+  83  Linux
/dev/sda2        40965750    41367374      200812+  82  Linux swap / Solaris
/dev/sda3        41367375   853886879   406259752+  83  Linux
/dev/sda4   *   853886880   976768064    61440592+   7  HPFS/NTFS

And then here is the rest

ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ cat /mnt/etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=6f287263-221c-485d-92c9-1f84072dd689 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2 
UUID=c3feb86c-f6d9-4a2e-be07-7eaedd84958e none            swap    sw              0       0

/dev/sda3      /media/sda3 **[COLOR="Red"][SIZE="5"]/[/SIZE][/COLOR]**   ext3    defaults        0        2   
 
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0



You need to remove that / from /dev/sda3 entry.

---

### Post by caljohnsmith on 2009-02-24
OK, while you have sda1 mounted on /mnt via the previous commands, how about doing:
```
gksudo gedit /mnt/etc/fstab
```
And remove the "/" in the following line:
```
/dev/sda3 /media/sda3 [COLOR="Red"]/[/COLOR] ext3 defaults 0 2 
```
So you should end up with:
```
/dev/sda3 /media/sda3 ext3 defaults 0 2 
```
Then reboot, and let us know if you can access your sda3 partition.

---

### Post by carml on 2009-02-24
@ caljohnsmith and @ taurus
Thanks a lot,you guys are always enlightening with your suggestions,
thanking you I'm learnig more and becoming more useful for others. :p

---

### Post by dfa on 2009-02-25
> **caljohnsmith said:**
> OK, while you have sda1 mounted on /mnt via the previous commands, how about doing:
```
gksudo gedit /mnt/etc/fstab
```
And remove the "/" in the following line:
```
/dev/sda3 /media/sda3 [COLOR="Red"]/[/COLOR] ext3 defaults 0 2 
```
So you should end up with:
```
/dev/sda3 /media/sda3 ext3 defaults 0 2 
```
Then reboot, and let us know if you can access your sda3 partition.

to caljohnsmith and taurus
WORKED LIKE A CHARM!!!  Well done.  Seriously it was a small issue in the grand scheme of things but for me it would have taken a lifetime to solve.  I appreciate it so much. You both kick so much ***! Thanks a lot again.

---

### Post by caljohnsmith on 2009-02-25
It's always nice when the solution to a computer problem turns out to be something simple, isn't it? Glad to hear that worked OK; cheers and have fun with your Ubuntu install. :)

---

