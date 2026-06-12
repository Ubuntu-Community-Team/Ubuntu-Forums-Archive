---
title: "Swap partition not visible in vista"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by CageUK on 2008-12-16
Having successfully installing Ubunto on a new partition as part of a dual boot with vista I lazily (and rather foolishly)used my vista image partition as the destination for the swap drive. 

I did a subsequent installation and removed the swap althogether as the partition had become invisible to Vista. I have 3gb of memory so the swap wasn't essential. The drive still can not been seen in vista though. It is not a major issue as I have the restore cd but I would like the convenience of having the image back again. 
Is there anyway I can make it visible again without reformatting the partition?

Cheers

---

### Post by taurus on 2008-12-16
Can you post the output of this command from a terminal (in Ubuntu)?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by CageUK on 2008-12-16
Here you go:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x380e892c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       33069   265620472    7  HPFS/NTFS
/dev/sda2           33069       35618    20478976   83  Linux
/dev/sda3           35618       38914    26468352   82  Linux swap / Solaris

I'd say it's not looking good!

---

### Post by taurus on 2008-12-16
> **CageUK said:**
> Here you go:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x380e892c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       33069   265620472    7  HPFS/NTFS
/dev/sda2           33069       35618    20478976   83  Linux
**[COLOR="Blue"]/dev/sda3           35618       38914    26468352   82  Linux swap / Solaris[/COLOR]**

I'd say it's not looking good!

Your swap partition is /dev/sda3.  Now, see if you have an entry in /etc/fstab for it.  Post the outputs of these commands from a terminal.

```
cat /etc/fstab
sudo blkid
free
```

---

### Post by CageUK on 2008-12-17
These are the results

mark@mark-laptop:~$ cat /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=b868c039-35c4-4990-a267-32a4ce8ca555 /               ext3    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

mark@mark-laptop:~$ sudo blkid

/dev/sda1: UUID="BC6E69F96E69AD38" LABEL="Vista" TYPE="ntfs" 
/dev/sda2: UUID="b868c039-35c4-4990-a267-32a4ce8ca555" TYPE="ext3" 
/dev/sda3: TYPE="swap" UUID="d3e7a3be-bdcc-4579-8119-467d4db711df" 

mark@mark-laptop:~$ free

             total       used       free     shared    buffers     cached
Mem:       3107420     745228    2362192          0      15488     222152
-/+ buffers/cache:     507588    2599832
Swap:            0          0          0
mark@mark-laptop:~$ 

Hope this means something to you!

---

### Post by pastalavista on 2008-12-17
Vista doesn't normally see Linux partitions and Swap isn't an actual partition in the sense of storage, it is meant to be used exclusively by the system as an overflow for memory and not accessible by any user. These have all been Ubuntu's view of things and they all seem ok to me. Why do you want to see the Ubuntu Swap partition with Vista? You can see regular ext3 and ext2 Linux partitions from Vista with [EXT2fs]("http://www.fs-driver.org/") and I'm sure there are a lot more out there.

But before you reformat the space the old Vista image might have been try this: ```
sudo parted
``` and in parted type:```
 print all
```. I don't know if you wrote your swap partition over top of the whole partition or not, but it is probably gone forever. parted or gparted might be able to reclaim the space for the image and you could possibly copy the restore disk to it. Good-luck

---

