---
title: "? about storage..."
date: 2009-03-17
forum: New to Ubuntu
---

### Post by Leo Dragonheart on 2009-03-17
I have Mandriva 2008 and Ubuntu 8.10 installed on my computer and I was wondering I have all these storage places on my HD. Can someone tell me what they are for and if I can delete them? I know that HD-2 is my second installed HD but what are the rest? Thanx...

---

### Post by iamkrazee on 2009-03-17
Give out the outputs of the following.. That could help us figure out.

```
sudo cat /etc/fstab
```
```
sudo cat /etc/mtab
```

---

### Post by Leo Dragonheart on 2009-03-17
> **iamkrazee said:**
> Give out the outputs of the following.. That could help us figure out.

```
sudo cat /etc/fstab
```
```
sudo cat /etc/mtab
```

Below is the outputs you requested...

sudo cat /etc/fstab =

```
leo@Illuzionz:~$ sudo cat /etc/fstab
[sudo] password for leo: 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=c05ca6a3-243f-4c51-80aa-ab57af891f0e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=37ac14cd-3328-4110-a1c9-4675477994fc none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
leo@Illuzionz:~$ 

```

sudo cat /etc/mtab =

```
leo@Illuzionz:~$ sudo cat /etc/mtab
/dev/sda7 / ext3 rw,relatime,errors=remount-ro 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
/proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
lrm /lib/modules/2.6.27-7-generic/volatile tmpfs rw,mode=755 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/leo/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=leo 0 0
leo@Illuzionz:~$ 


```

Thanx for your help...

---

### Post by iamkrazee on 2009-03-17
Woah.. no idea! lol. See now, the 8.4G media is your root... and then that's it! That's all I could figure out. It's a strange scheme of partitioning. And none of them are set to be mounted automatically. Except root that is.

---

### Post by kanikilu on 2009-03-17
```
sudo fdisk -l
``` might give you some more information on your partitioning...

---

