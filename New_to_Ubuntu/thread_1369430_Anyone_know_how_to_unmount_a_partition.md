---
title: "Anyone know how to unmount a partition?"
date: 2010-01-01
forum: New to Ubuntu
---

### Post by listerdl on 2010-01-01
Hi does anyone know how to unmount a partition?

I am trying to delete a winRE partion that has been 'reserved' using GParted but it refuses to let me delete or format it...

Any ideas?

I think the trick is to unmount it but am unsure how to do this - thanks ;)

---

### Post by lisati on 2010-01-01
Does right-clicking on its name in gParted's list of partitions give you an "unmount" option?

---

### Post by Mrandersonjr on 2010-01-01
In the terminal type:
umount /dev/sd* 
where the * is your drive number.
If it won't unmount then use,
umount -f /dev/sd*

---

### Post by oldos2er on 2010-01-01
In gparted, right-click on the partition and choose 'Unmount'. I don't understand what you mean by using gparted to reserve a partition.

---

### Post by listerdl on 2010-01-01
> **oldos2er said:**
> In gparted, right-click on the partition and choose 'Unmount'. I don't understand what you mean by using gparted to reserve a partition.

Thanks - let me try that - (Ill mark this thread as answered if that works)

Using GParted I meant that one of the partitions has been reserved for the winRE - and I would like to unreserve that by using GParted.

---

### Post by JamesParnell on 2010-01-01
umount /dev/sd***

**or** umount -f /dev/sd*** (this will force the partition to unmount)

---

### Post by listerdl on 2010-01-01
thanks !

---

### Post by listerdl on 2010-01-01
I tried the above and this happened:

henry@henryUbuntu:~$ umount -f /dev/sda1
umount: only root can do that
henry@henryUbuntu:~$ unmount /dev/sda1
No command 'unmount' found, did you mean:
 Command 'umount' from package 'mount' (main)
 Command 'umount' from package 'loop-aes-utils' (universe)

I changed the format for this partition to linux-swap but still when i boot the grub screen still lists this partition as Vista Loader...

Any ideas what I am doing wrong?

Thanks!

---

### Post by nickpaton on 2010-01-01
> **listerdl said:**
> I tried the above and this happened:

henry@henryUbuntu:~$ umount -f /dev/sda1
umount: only root can do that
henry@henryUbuntu:~$ unmount /dev/sda1
No command 'unmount' found, did you mean:
 Command 'umount' from package 'mount' (main)
 Command 'umount' from package 'loop-aes-utils' (universe)

I changed the format for this partition to linux-swap but still when i boot the grub screen still lists this partition as Vista Loader...

Any ideas what I am doing wrong?

Thanks!
Try putting "sudo" in front of the command.

---

### Post by listerdl on 2010-01-01
> **nickpaton said:**
> Try putting "sudo" in front of the command.

thanks...i tried and:

henry@henryUbuntu:~$ sudo umount -f /dev/sda1
[sudo] password for henry: 
umount2: Invalid argument
umount: /dev/sda1: not mounted


Thats weird...says that it isnt mounted but when I boot it is clearly there in the grub menu. Should I simply ignore? Thing is that I would like to use that partition as a swap area

---

### Post by Paqman on 2010-01-01
Is the partition you're trying to unmount inside an extended partition that has other partitions that are mounted? If so, Gparted will show the whole extended partition as locked.

---

### Post by oldos2er on 2010-01-01
> **listerdl said:**
> henry@henryUbuntu:~$ sudo umount -f /dev/sda1
[sudo] password for henry: 
umount2: Invalid argument
umount: /dev/sda1: not mounted

Thats weird...says that it isnt mounted but when I boot it is clearly there in the grub menu. Should I simply ignore? Thing is that I would like to use that partition as a swap area

Can you run each of these commands and post their output?

sudo fdisk -l

mount

---

### Post by listerdl on 2010-01-01
> **oldos2er said:**
> Can you run each of these commands and post their output?

sudo fdisk -l

mount

Hi this is the output:

henry@henryUbuntu:~$ sudo fdisk -l
[sudo] password for henry: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x01eb4677

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1020     8192000   82  Linux swap / Solaris
Partition 1 does not end on cylinder boundary.
/dev/sda2   *        1020        3570    20483001    7  HPFS/NTFS
/dev/sda3            3571        6120    20482875   83  Linux
/dev/sda4            6121       19457   107129452+   7  HPFS/NTFS

The partition that contains the Vista Loader, (that I am trying to get rid of and covert to linux-swap) is the first one that says, "Partition 1 does not end on cylinder boundary."

Does that mean that that partition cannot be deleted?

Thanks for all advice.

---

### Post by oldos2er on 2010-01-01
I am not certain--and please don't act on my advice until someone else chimes in--but you may need to create a new partition table, which would involve wiping out everything on the disk and then recreating what ever partitions you need. So you would want to have backups of any data you wish to keep beforehand.

Or you could leave things as they are. I'm a little concerned though that the error "does not end on cylinder boundary" may be putting some of your data at risk.

---

### Post by mkoehler on 2010-01-01
Personally, I always say that it's worth tossing in a live cd and playing around with it.  If sda1 is an extention of sda3, it may be trying to remount the drive - obviously when the drive is mounted, no formatting options can be run on it.  Basically, I'd just suggest pulling out the 'ol live cd and running gparted.

---

