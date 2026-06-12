---
title: "Resizing Ext3 partion"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by Gp. on 2009-03-22
Dual booting Ubuntu and vista.

Vista using NTFS and Ubuntu using ext3.

I need more space on my main drive for vista, but how do I shrink the ext3 and increase the size of the NTFS partition? (Vista)

Cheers.

---

### Post by taurus on 2009-03-22
It all depends where those partitions are located on your harddrive.  You have to do the shrinking and expanding with gparted from the LiveCD since you cannot resize Ubuntu partition while you are running from it.

So, boot from Ubuntu LiveCD.  Then, open a terminal and post the output of this command (or a screenshot of gparted:  System -> Administration -> Partition Editor).

Applications -> Accessories -> Terminal
```
sudo fdisk -lu
```

---

### Post by Gp. on 2009-03-22
Is there a Graphical partitioner I can install while under live cd?

---

### Post by taurus on 2009-03-22
Gparted is already on the LiveCD--System -> Administration -> Partition Editor.

---

### Post by Dedoimedo on 2009-03-22
Remember that any partition you want to play with must be unmounted!
Dedoimedo

---

### Post by mlentink on 2009-03-22
> **Gp. said:**
> Is there a Graphical partitioner I can install while under live cd?

@Gp: since you do not seem to me to be an extremely experienced user, you could help us help you by booting up with the LiveCD and run the command Taurus proposed (see above) in a terminal, and post back the results here.

---

### Post by lindsay7 on 2009-03-23
Excuse me for jumping in, but I want to able to follow this post. I have an open post on a similar subject. Gparted will not let me resize my ext3 partition from the live cd.

---

### Post by llamabr on 2009-03-23
> **lindsay7 said:**
> Excuse me for jumping in, but I want to able to follow this post. I have an open post on a similar subject. Gparted will not let me resize my ext3 partition from the live cd.

The partition must not be mounted.  post the output of 

```
df
```

and 

```
cat /etc/fstab
```

and which partition you're trying to resize

---

### Post by lindsay7 on 2009-03-23
Ok, thanks for the help.  I have Ubuntu on a 500 gig drive used only by Ubuntu. So it is on sda1 and I want to partition it and use about 100 gigs for a home partition.  Gparted runs but them stops and give an i/o error.

```
ubuntu@ubuntu:~$ sudo df
Filesystem           1K-blocks      Used Available Use% Mounted on
tmpfs                  1003436      2000   1001436   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                  1003436      2000   1001436   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                  1003436         0   1003436   0% /lib/init/rw
varrun                 1003436        84   1003352   1% /var/run
varlock                1003436         0   1003436   0% /var/lock
udev                   1003436      2856   1000580   1% /dev
tmpfs                  1003436       104   1003332   1% /dev/shm
rootfs                 1003436     21892    981544   3% /
/dev/scd0               715592    715592         0 100% /cdrom
/dev/loop0              691712    691712         0 100% /rofs
tmpfs                  1003436        12   1003424   1% /tmp
/dev/sdb1               995024     16480    978544   2% /media/disk

```


From the live cd

```
ubuntu@ubuntu:~$ cat /etc/fstab
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0
ubuntu@ubuntu:~$ ubuntu@ubuntu:~$ sudo df
bash: ubuntu@ubuntu:~$: command not found
ubuntu@ubuntu:~$ Filesystem           1K-blocks      Used Available Use% Mounted on
bash: Filesystem: command not found
ubuntu@ubuntu:~$ tmpfs                  1003436      2000   1001436   1% /lib/modules/2.6.27-7-generic/volatile
bash: tmpfs: command not found
ubuntu@ubuntu:~$ tmpfs                  1003436      2000   1001436   1% /lib/modules/2.6.27-7-generic/volatile
bash: tmpfs: command not found
ubuntu@ubuntu:~$ tmpfs                  1003436         0   1003436   0% /lib/init/rw
bash: tmpfs: command not found
ubuntu@ubuntu:~$ varrun                 1003436        84   1003352   1% /var/run
bash: varrun: command not found
ubuntu@ubuntu:~$ varlock                1003436         0   1003436   0% /var/lock
bash: varlock: command not found
ubuntu@ubuntu:~$ udev                   1003436      2856   1000580   1% /dev
bash: udev: command not found
ubuntu@ubuntu:~$ tmpfs                  1003436       104   1003332   1% /dev/shm
bash: tmpfs: command not found
ubuntu@ubuntu:~$ rootfs                 1003436     21892    981544   3% /
bash: rootfs: command not found
ubuntu@ubuntu:~$ /dev/scd0               715592    715592         0 100% /cdrom
bash: /dev/scd0: Permission denied
ubuntu@ubuntu:~$ /dev/loop0              691712    691712         0 100% /rofs
bash: /dev/loop0: Permission denied
ubuntu@ubuntu:~$ tmpfs                  1003436        12   1003424   1% /tmp
bash: tmpfs: command not found
ubuntu@ubuntu:~$ /dev/sdb1               995024     16480    978544   2% /media/disk
bash: /dev/sdb1: Permission denied
ubuntu@ubuntu:~$ ubuntu@ubuntu:~$ 
bash: ubuntu@ubuntu:~$: command not found
ubuntu@ubuntu:~$ 


```


From the drive without the live cd

stevepoulton@stevepoulton-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c67425dc-c774-4ef9-8be9-b0d47c55e478 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=9d077e0a-cd5f-41ad-9e34-e8e6a9d66095 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
stevepoulton@stevepoulton-desktop:~$ 



here is the disk info

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1d56957a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   965024549   482512243+  83  Linux
/dev/sda2       965024550   976768064     5871757+   5  Extended
/dev/sda5       965024613   976768064     5871726   82  Linux swap / Solaris

Disk /dev/sdb: 1019 MB, 1019215872 bytes
255 heads, 63 sectors/track, 123 cylinders, total 1990656 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0accb65c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63     1990655      995296+   e  W95 FAT16 (LBA)
Partition 1 has different physical/logical endings:
     phys=(122, 254, 63) logical=(123, 232, 45)
ubuntu@ubuntu:~$

---

