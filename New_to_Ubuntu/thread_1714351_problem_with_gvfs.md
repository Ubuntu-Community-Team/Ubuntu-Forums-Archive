---
title: "problem with gvfs"
date: 2011-03-25
forum: New to Ubuntu
---

### Post by lexand on 2011-03-25
Hi

first of all - sorry my English

i'd created a theme "problem with NTFS mounting" on the [http://forum.ubuntu.ru](http://forum.ubuntu.ru)
but anyone can help me

i'd made some investigations and now I can say that problem is not in NTFS, the problem is in FUSE/gvfs

here is **$cat /etc/mtab** from PC (NTFS/exFAT/... won't mounts)
> 
/dev/sdb3 on / type ext4 (rw,errors=remount-ro,commit=0)
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
none on /var/lib/ureadahead/debugfs type debugfs (rw,relatime)
/dev/sdb1 on /boot type ext4 (rw,commit=0)
/dev/md0 on /home type ext4 (rw,commit=0)
/dev/sdc2 on /backup type ext4 (rw,commit=0)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

and from notebook
> 
/dev/sda5 on / type ext4 (rw,errors=remount-ro,commit=600)
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
/dev/sda1 on /boot type ext4 (rw,commit=600)
/dev/sda6 on /var type ext4 (rw,commit=600)
/dev/sda7 on /home type ext4 (rw,commit=600)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
**gvfs-fuse-daemon on /home/lexand/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=lexand)**
nfsd on /proc/fs/nfsd type nfsd (rw)


and output of **strace -ft /usr/lib/gvfs/gvfsd -r** (last lines)
> 
[pid  3118] 13:57:41 lstat("/home", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
[pid  3118] 13:57:41 lstat("/home/alex", {st_mode=S_IFDIR|0755, st_size=12288, ...}) = 0
[pid  3118] 13:57:41 lstat("/home/alex/.gvfs", 0x7fff1d27d410) = -1 ENOTCONN (Transport endpoint is not connected)
[pid  3118] 13:57:41 write(2, "fuse: bad mount point `/home/ale"..., 78) = 78
[pid  3118] 13:57:41 exit_group(1)      = ?


when I try to mount NTFS volumes from Nautilus I get
**Error mounting: mount exited with exit code 21: **

My OS - Ubuntu 10.10 amd64
How I can start **gvfs-fuse-daemon?** without reinstalling Ubuntu.
Or what else I must do for solving this problem?

thanks

---

### Post by aaryansh on 2011-03-25
Hi lexand,
Welcome to ubuntu forums.

you could try re-installing gvfs-fuse, libfuse2, fuse-utils and ntfs-3g

```
sudo apt-get install --reinstall gvfs-fuse libfuse2 fuse-utils ntfs-3g
```you could also install gvfs-bin to use the gvfs-mount command

```
sudo apt-get install gvfs-bin
```then use, gvfs-mount -d /dev/sdxx
needless to say, you'll have to change sdxx to your drive name

Hope this helps.

p.s - Just to cover all bases here. Are you able to mount your drive using the mount command?

---

### Post by lmarmisa on 2011-03-25
I am not sure but maybe your system detects a problem related to the mount point in **/home/alex/.gvfs**.

Please, open a terminal, type these commands and post here the results:

```

cd
ls -la | grep gvfs
ls -l .gvfs

```

These are the results in my case:

```

luis@UB1010ENG:~$ cd
luis@UB1010ENG:~$ ls -la | grep gvfs
dr-x------  2 luis luis     0 2011-03-26 02:55 .gvfs
luis@UB1010ENG:~$ ls -la .gvfs/
total 4
dr-x------  2 luis luis    0 2011-03-26 02:55 .
drwxr-xr-x 45 luis luis 4096 2011-03-26 03:26 ..
luis@UB1010ENG:~$

```

---

### Post by lexand on 2011-03-26
I'd tried to reinstall all of the mentioned packages, but the problem has not disappeared.

I can't mount partitions even if they described in** /etc/fstab** or through **mount** command
> 
alex@aquanox-ubuntu:~$ sudo mount /dev/sda1 /mnt/temp
alex@aquanox-ubuntu:~$ umount /dev/sda1
umount: /dev/sda1 is not mounted (according to mtab)
/dev/sda1 is NTFS volume

> 
alex@aquanox-ubuntu:~$ sudo mount /dev/sda1 /mnt/temp ; echo $?
21
I'd made some additional tests
I can mount almost all filesystems except **exfat, ntfs, reiser4 **(all filesystem drivers are installed).
But for me only NTFS and little less exfat are important.

P.S.
on the notebook all work fine.
Maybe I should compare something between PC and NB: runned process, installed packages, configuration files ????

---

### Post by lmarmisa on 2011-03-26
Please post the results of these commands:

```

mount
fusermount -u ~/.gvfs
mount

```

I recommend this other test. Create a new user account (named test, for example) and check if you get the same problem in that account.

---

### Post by lexand on 2011-03-26
I've checked this on the newly created user account - still the same.
**Error mounting: mount exited with exit code 21:**


```

mount
fusermount -u ~/.gvfs
mount

```> 
alex@aquanox-ubuntu:~$ mount
/dev/sdb3 on / type ext4 (rw,errors=remount-ro,commit=0)
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
/dev/sdc2 on /backup type ext4 (rw,commit=0)
/dev/sdb1 on /boot type ext4 (rw,commit=0)
/dev/md0 on /home type ext4 (rw,commit=0)
rpc_pipefs on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

alex@aquanox-ubuntu:~$ fusermount -u ~/.gvfs
fusermount: entry for /home/alex/.gvfs not found in /etc/mtab

alex@aquanox-ubuntu:~$ mount
/dev/sdb3 on / type ext4 (rw,errors=remount-ro,commit=0)
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
/dev/sdc2 on /backup type ext4 (rw,commit=0)
/dev/sdb1 on /boot type ext4 (rw,commit=0)
/dev/md0 on /home type ext4 (rw,commit=0)
rpc_pipefs on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)


Maybe this problem is not related to gvfs, maybe it relates to FUSE?

P.S. From LiveCD all works fine.

---

