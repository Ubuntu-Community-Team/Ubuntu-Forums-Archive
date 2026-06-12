---
title: "Mount Error - Permanent Mounting!!!"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by randolf_ambrose on 2010-05-03
hi...

i tried to mount my fat32 drive permanently... but now i'm not able to mount that drive... i get mounting error while booting...

i dont see any reason for errors...

this is what i did...

sudo nano /etc/fstab

/dev/sda3  /mnt/BLOOD  FAT  users,noatime,auto,rw,nodev,exec,nosuid 0 0

since my sda3 was fat32, i tried again with;
/dev/sda3  /mnt/BLOOD  FAT32  users,noatime,auto,rw,nodev,exec,nosuid 0 0

still i get same error and i am not able to access that drive...

what shall i do to mount that drive permanently???

please someone help!!!

---

### Post by randolf_ambrose on 2010-05-03
this is what i'm getting...

i've tried so many times...

but what does this mean???

> mount: unknown filesystem type 'fat32'

---

### Post by Troublegum on 2010-05-03
its vfat, not FAT or FAT32.
```

/dev/sda3  /mnt/BLOOD vfat   users,noatime,auto,rw,nodev,exec,nosuid 0 0

```

---

### Post by randolf_ambrose on 2010-05-03
@Troublegum

thanks a lot... really appreciate it...

i was following this post and its mentioned NTFS or FAT32...
[http://www.nyutech.com/2009/03/make-ubuntu-mount-partitions-and-drives.html](http://www.nyutech.com/2009/03/make-ubuntu-mount-partitions-and-drives.html)

i knew my volume was fat32... so i blindly followed it...

thanks for the correction... :)

but now i am having permission problem...

i cant create or delete files or folders..

i tried with defaults too...

not working... any suggestions???

---

### Post by Troublegum on 2010-05-03
Your partition is formated in FAT32, thats correct. The problem is, that the mount command expects you to use the type "vfat". Don't know why. :D

Regarding the permissions problem, try the following line instead, please:
```

/dev/sda3  /mnt/BLOOD  vfat  utf8,umask=007,gid=46  0  0

```

---

### Post by Ocxic on 2010-05-03
make sure you have ownership of the folder your mounting the drive to.

---

### Post by randolf_ambrose on 2010-05-03
@Troublegum

i just tried > /dev/sda3  /mnt/BLOOD  vfat  utf8,umask=007,gid=46  0  0

still i do not have access to it...

i checked the properties... it says only root has permissions!!!

and like hell, when i tried to log in as root, i'm getting authentication failue...

i tried my main passcode, i tried root, still authentication failure...


here's the entire thing!!!

> lynx@lynx-laptop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfaabcd58

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         487     3905537    5  Extended
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         487        3917    27550720   83  Linux
/dev/sda3            3917       19458   124830720    b  W95 FAT32
/dev/sda5               1         487     3905536   82  Linux swap / Solaris


gedit /etc/fstab
> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda2       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=2daf05a9-472d-407b-809f-bdbd176ccade none            swap    sw              0       0
/dev/sda3  /mnt/BLOOD  vfat  utf8,umask=007,gid=46  0  0

---

### Post by randolf_ambrose on 2010-05-03
@Ocxic

hi hi hi... i dont know how to gain ownership of that volume... as of now, only root has ownership...

seems like i gotta set back everything to zero???

---

### Post by Morbius1 on 2010-05-03
>  /dev/sda3  /mnt/BLOOD  vfat  utf8,umask=007,gid=46  0  0                      That line in fstab should mount with owner=root but with read / write access to owner ( root ) and group=plugdev (46). Every local login user is a member of the plugdev group so you should have read write access.

Do you not have access or are you just concerned that the owner is still root?

You could transfer ownership by adding **uid=1000** to the mix:

```
/dev/sda3  /mnt/BLOOD  vfat  utf8,umask=007,uid=1000,gid=46  0  0
```

[COLOR=Blue]EDIT: Sorry , I just assumed that you were "1000"[/COLOR]. To find out if that's the right number for you type the following in a terminal:** id**

---

### Post by randolf_ambrose on 2010-05-03
@Troublegum
@Ocxic

finally...

this worked!!! > /dev/sda3 /mnt/BLOOD vfat iocharset=utf8,umask=000 0 0

found this from [http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

...

thank you for helping me out guys... i really appreciate it... :)

---

### Post by Troublegum on 2010-05-03
You don't have to be the owner of /mnt/BLOOD, gid=46 says that the group of the mounted device will be group 46 (plugdev). Usually, you should be a member of this group.

Could you type the following code in a terminal and post the output?
```

id

```

Also, it would be good if you could post the output of 
```

ls -l /mnt | grep BLOOD

```

---

### Post by randolf_ambrose on 2010-05-03
@Morbius1

i had access to read folders/files!!! but owner was root and so i had no access to write/delete folders/files...

now its fine...

i've full access and i've linked /mnt/BLOOD to /home/lynx/WINDOWS... working great!!!

thanks the help... :)

---

### Post by randolf_ambrose on 2010-05-03
> **Troublegum said:**
> You don't have to be the owner of /mnt/BLOOD, gid=46 says that the group of the mounted device will be group 46 (plugdev). Usually, you should be a member of this group.

Could you type the following code in a terminal and post the output?
```

id

```

Also, it would be good if you could post the output of 
```

ls -l /mnt | grep BLOOD

```

since you asked...

id
> uid=1000(lynx) gid=1000(lynx) groups=4(adm),20(dialout),24(cdrom),46(plugdev),105(lpadmin),119(admin),122(sambashare),1000(lynx)


ls -l /mnt | grep BLOOD
> drwxrwxrwx 15 root root 65536 2010-05-04 01:51 BLOOD

---

### Post by Troublegum on 2010-05-03
Strange. gid=46 should mount the partition under the group plugdev, not the group root. 
But as you set umask=000, everyone has full access to the partition. That works too, of course. :)

---

### Post by randolf_ambrose on 2010-05-03
> **Troublegum said:**
> Strange. gid=46 should mount the partition under the group plugdev, not the group root. 
But as you set umask=000, everyone has full access to the partition. That works too, of course. :)

hi hi hi... i dont know much about partitions... but i managed to get the > umask=000, everyone has full access part in the beginning itself!!!

;-)

now i'm linking my default directories like Documents, Pictures, Videos, etc to the one in my fat partition!!! this is cool... couldnt do this in my jaunty(i mean, tried and failed ;-))... i'm gonna love this...

---

