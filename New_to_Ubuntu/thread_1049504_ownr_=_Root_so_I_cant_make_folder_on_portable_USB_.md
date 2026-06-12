---
title: "ownr = Root so I cant make folder on portable USB disk so I can Put Ubuntu on it"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by Ronok on 2009-01-24
hi
I am real new to ubuntu !
I would like to end up with Ubunto on my Remote portable USB hard disk

this is my thinking / goal:

have my Remote portable USB hard disk 90% fat32 so 
a friend on a MSFT computer and myself on 100% Ubuntu computer
could both read write to it at different times
and 10% ext3 so I could boot Ubuntu from it on another computer

this is what I did / approach:

1) bought a Western digital 320 MB "passport" portable USB hard disk
2) try to clean its brains out (deleted all MSFT synk junk)
3) Used system> Adnin> "partition editor" to make all new as follows
     /dev/sdc1 aka /media/Music_Disk,  fat32, 287.  GB 
     /dev/sdc2                      extended,   5.3 GB
        /dev/sdc5                 Linux-swap,   5.3 GB
     /dev/sdc3 aka /media/UB_BOOT       ext3,   5.3 GB

I noticed:
4) I can read, write to /dev/sdc1  ok good 
5) I Cant read, write, anything, make folder, etc to /dev/sdc3
6) "root" is owner of /dev/sdc3


if my goal is to be able to boot Ubuntu from it on another computer
maybe I dont need to be owner of /dev/sdc3 to:
a) download Ubunto 8.10 from Internet down to /dev/sdc3
b) use it / boot from it / update it

and maybe I do ????
well I have tried to change owner of /dev/sdc3
and I am not able to / dont know how to


thanks for your help 
Ronok

Here is some Data that may be of Help
also let me know if you see anything that looks wrong

root@LuoDianNao:/home/ronok# ls -l /media
total 44
lrwxrwxrwx 1 root  root      6 2008-12-22 14:02 cdrom -> cdrom0
drwxr-xr-x 2 root  root   4096 2008-12-22 14:02 cdrom0
drwxr-xr-x 3 root  root   4096 2008-12-22 14:47 disk
drwxr-xr-x 3 root  root   4096 2008-12-21 12:30 disk-1
drwxr-xr-x 3 root  root   4096 2008-12-20 21:31 disk-2
lrwxrwxrwx 1 root    999     7 2008-12-22 14:02 floppy -> floppy0
drwxr-xr-x 2 root    999  4096 2008-12-22 14:02 floppy0
drwx------ 3 ronok root  16384 1969-12-31 16:00 Music_Disk
drwx------ 6 ronok ronok  4096 2009-01-16 16:25 ShuJu
drwxr-xr-x 3 root  root   4096 2009-01-23 21:35 UB_BOOT

also

root@LuoDianNao:/home/ronok# mount -l
/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro) []
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ronok/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ronok)
/dev/sdc1 on /media/Music_Disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush) [Music_Disk]
/dev/sdb1 on /media/ShuJu type ext3 (rw,nosuid,nodev,uhelper=hal) [ShuJu]
/dev/sdc3 on /media/UB_BOOT type ext3 (rw,nosuid,nodev,uhelper=hal) [UB_BOOT]
/dev/sdb3 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal) []
/dev/sda3 on /media/disk-1 type ext3 (rw,nosuid,nodev,uhelper=hal) []
/dev/sda1 on /media/disk-2 type ext3 (rw,nosuid,nodev,uhelper=hal) []

---

### Post by jimmy the saint on 2009-01-24
[http://ubuntuforums.org/showthread.php?t=80811](http://ubuntuforums.org/showthread.php?t=80811)
a good guide for what you seem to want to do

---

### Post by Ronok on 2009-01-24
ok **Thanks** for your tips and time

I will work on this follow your tips and stay in sudo

bottom line I want to be able to:
a) access & write to my drives / change ownership if needed,  at home
b) at friends house: 
     share data from the Fat32 partition
     show friends "ubuntu 8.10" from the ext3 partition

Thanks again

---

