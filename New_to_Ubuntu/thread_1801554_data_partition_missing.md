---
title: "data partition missing"
date: 2011-07-10
forum: New to Ubuntu
---

### Post by dbares on 2011-07-10
Hello everyone, i am having a problem with my data partition. I created my partitions using gparted disk. I did some research and decided to go the data partition route instead of /home partition route. I created my / partition, my swap partition and 1 data partition in gparted and formatted them in gparted and when i used the Ubuntu installer i simply mounted the data partition to my /home folder. But i cant access my partition in my home folder. In fact i cant find it at all... so i am thinking it is not mounted. But i do not know how to mount an already existing partition. When i type the command sudo blkid this is what i get: /dev/sda1: UUID="48ce9128-4479-4c2f-8c45-5d20419dd391" TYPE="swap" 
/dev/sda2: UUID="87053948-bff4-4b62-9e89-a7db3d9524b2" TYPE="ext4" 
/dev/sda3: UUID="1547d05f-9083-458b-b54e-629b552de932" TYPE="ext4" 

sda 3: is my data partition i created that i mounted in /home during install but it is not there when i open my /home folder ? Thank You in advance for any help as i am very new to linux but looking forward to using this new Ubuntu release.

---

### Post by lmarmisa on 2011-07-10
Welcome to the forums.

Please, open a terminal, type these commands and post here the results:

```

sudo parted -l
mount
cat /etc/fstab

```

---

### Post by dbares on 2011-07-10
> **lmarmisa said:**
> Welcome to the forums.

Please, open a terminal, type these commands and post here the results:

```

sudo parted -l
mount
cat /etc/fstab

```
Thank You, this is what i got:
Model: ATA FUJITSU MHW2160B (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos/dev/sda2 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
/dev/sda3 on /home type ext4 (rw,commit=0)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/derik/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=derik)




Number  Start   End     Size    Type     File system     Flags
 1      32.3kB  2147MB  2147MB  primary  linux-swap(v1)
 2      2147MB  23.6GB  21.5GB  primary  ext4            boot
 3      23.6GB  160GB   136GB   primary  ext4
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=87053948-bff4-4b62-9e89-a7db3d9524b2 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=1547d05f-9083-458b-b54e-629b552de932 /home           ext4    defaults        0       2
# swap was on /dev/sda1 during installation
UUID=48ce9128-4479-4c2f-8c45-5d20419dd391 none            swap    sw              0       0
derik@5BARES-LAPTOP:~$

---

### Post by lmarmisa on 2011-07-10
Everything looks good:

[INDENT]**/dev/sda1** (2 Gbytes)  is the swap partition.

**/dev/sda2** (21.5 Gbytes) is the root partition.

**/dev/sda3** (136 Gbytes) is mounted on /home.
[/INDENT]
Best regards,

Luis

---

### Post by dbares on 2011-07-10
> **lmarmisa said:**
> Everything looks good:[INDENT]**/dev/sda1** (2 Gbytes)  is the swap partition.

**/dev/sda2** (21.5 Gbytes) is the root partition.

**/dev/sda3** (136 Gbytes) is mounted on /home.
[/INDENT]Best regards,

Luis
So, i apologize in advance for such noobie questions, but how does that work ? Everything i save in /home folder goes to the data partition i created ? How do i know what i save in the /home folder is going to that data partition and not to the / partition the the /home folder is in ?

---

### Post by sandyd on 2011-07-10
> **dbares said:**
> So, i apologize in advance for such noobie questions, but how does that work ? Everything i save in /home folder goes to the data partition i created ? How do i know what i save in the /home folder is going to that data partition and not to the / partition the the /home folder is in ?

easy.

```

/dev/sda3 on /home type ext4 (rw,commit=0)

```

mount says that /dev/sda3 is mounted onto the /home path.

All of /home + its subdirectories are located on /dev/sda3 , and not on root "/". If it was not mounted onto /home, then the stuff would be in /dev/sda2, which is mounted on "/".

If you really wanna check, just run
```

sudo df -h
```.
Side note:I don't know if it needs sudo or not, I just do it because im using a different OS.

The command will show you how much space is used in each partition. Since you can see that space is used in /dev/sda3, you can rest assured that you have a seperate home partition (/dev/sda3)

---

### Post by lmarmisa on 2011-07-10
*Everything i save in /home folder goes to the data partition i created ? *

Yes. A directory named **/home** was defined by Ubuntu in the **root** partition during install. Ubuntu mounts the partition **/dev/sda3** on that directory at startup because there is an instruction for that purpose in the file **/etc/fstab**.  That means that all the files and folders inside the folder **/home** will be stored in the **/dev/sda3** partition.

[I]How do i know what i save in the /home folder is going to that data  partition and not to the / partition the the /home folder is in ?

[/I]If you are incredulous, try to use the command

```

df -h

```This command shows you the size of the mounted partitions and their used and available spaces.

---

### Post by dbares on 2011-07-10
> **sandyd said:**
> easy.

```

/dev/sda3 on /home type ext4 (rw,commit=0)

```mount says that /dev/sda3 is mounted onto the /home path.

All of /home + its subdirectories are located on /dev/sda3 , and not on root "/". If it was not mounted onto /home, then the stuff would be in /dev/sda2, which is mounted on "/".

If you really wanna check, just run
```

sudo df -h
```.
Side note:I don't know if it needs sudo or not, I just do it because im using a different OS.

The command will show you how much space is used in each partition. Since you can see that space is used in /dev/sda3, you can rest assured that you have a seperate home partition (/dev/sda3)
Ok, thank you again for the clarification, so /home is in root but because i mounted sda3 to /home then all contents stored on /home will be stored in sda3. Then what is the difference advantage/disadvantage between just creating a separate  /home partition instead of just mounting a data partition to /home ? I thought the advantage was on a new install it would still wipe user data in /home but not touch my sda3 data ie pictures music etc.

---

