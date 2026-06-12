---
title: "but it's not mounted"
date: 2010-08-15
forum: New to Ubuntu
---

### Post by pilosopotacio on 2010-08-15
here's my problem:
edson@edson-laptop:~$ fsck
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
/dev/sda1 is mounted.  

WARNING!!!  The filesystem is mounted.   If you continue you ***WILL***
cause ***SEVERE*** filesystem damage.

Do you really want to continue (y/n)? yes

fsck.ext4: Permission denied while trying to open /dev/sda1
You must have r/w access to the filesystem or be root

 but it's not mounted. need help please really stupid

---

### Post by Sealbhach on 2010-08-15
Try instead to force a fsck on your next boot. I'm not sure if this still works, but it's a safer way to do it:

[http://www.cyberciti.biz/faq/linux-force-fsck-on-the-next-reboot-or-boot-sequence/](http://www.cyberciti.biz/faq/linux-force-fsck-on-the-next-reboot-or-boot-sequence/)

.

---

### Post by surfer on 2010-08-15
what does
```
mount
```
give as output?

---

### Post by pilosopotacio on 2010-08-23
> **surfer said:**
> what does
```
mount
```give as output?

 this is what i got

edson@edson-laptop:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
none on /var/lib/ureadahead/debugfs type debugfs (rw,relatime)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/edson/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=edson)
edson@edson-laptop:~$

---

### Post by surfer on 2010-08-23
> **pilosopotacio said:**
> this is what i got

edson@edson-laptop:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
...

see, [FONT=Courier New]/dev/sda1[/FONT] is mounted on [FONT=Courier New]/type[/FONT] .

you have to
```

$ sudo umount /type

```first.

---

### Post by eriktheblu on 2010-08-23
I think that means he has /dev/sda1 mounted as / (ext4 as the file system)

Unmounting / does not seem like a winning proposition. Try it from a live CD instead.

---

### Post by Elfy on 2010-08-23
it's mounted / the type is ext4

---

### Post by surfer on 2010-08-23
oh, of course. sorry, it's late here.

[FONT=Courier New]/dev/sda1[/FONT] is mounted on [FONT=Courier New]/[/FONT]  .

+1 for "Unmounting / does not seem like a winning proposition. Try it from a live CD instead".

---

### Post by silverglade00 on 2010-08-23
> **surfer said:**
> 

[FONT=Courier New]/dev/sda1[/FONT] is mounted on [FONT=Courier New]/[/FONT]  .

How the heck do you get Slashdot mounted on your system?!?!? ;)

---

### Post by FuturePilot on 2010-08-23
You can't run fsck on a mounted partition and you can't unmount your / while the system is running. You have to use the live CD to run fsck on your /. Also, you can't fsck your partitions as a normal user. Use sudo.

---

