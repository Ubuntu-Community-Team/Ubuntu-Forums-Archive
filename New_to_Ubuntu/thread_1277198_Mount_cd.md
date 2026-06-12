---
title: "Mount cd"
date: 2009-09-28
forum: New to Ubuntu
---

### Post by Drenriza on 2009-09-28
How do you mount an windows xp cd, on ubuntu for installation on an virtual box.

Thanks on advance :KS

---

### Post by Drenriza on 2009-09-28
Or how can i mount the cd so i can create an ISO-file from it?

---

### Post by Drenriza on 2009-09-28
nevermind

---

### Post by ErikEhlert on 2009-09-28
So your running Ubuntu as the main OS, and you want to install Windows in that virtual box so you wanted to create an ISO from your Windows disc?

Why do you need an ISO at all for a windows disc you already have?

---

### Post by jimingkui on 2009-09-28
You mean you have a Windows LiveCD and you want to creat an ISO image on your computer?

1.Insert this CD in your CD-rom Open a terminal window(Applications->Accessories->Terminal) and run:
**mount**
Following output is an example.



wraith@wraith-desktop:~$ mount
/dev/sda7 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/wraith/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=wraith)
/dev/sr0 on /media/DEEPIN LITE XP 5.10 type iso9660 (ro,nosuid,nodev,uhelper=hal,uid=1000,utf8)



In last line,we know ***/dev/sr0*** is mount to ***/media/DEEP....*** which is my XP cd.Here **/dev/sr0** is what we want.
2. Use this command to create .iso image:
**dd if=/dev/sr0 of=~/winXP.iso bs=1000000 count=512**
This will create winXP.iso in my /home/user_name folder and it'll take a few minutes coping files.
After this command run:
**sync**
OK

---

### Post by jimingkui on 2009-09-28
<pre>errrrr</pre>

---

