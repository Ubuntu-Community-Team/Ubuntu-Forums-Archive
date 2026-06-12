---
title: "Not Another problem with the CDROm/DvD"
date: 2010-04-07
forum: New to Ubuntu
---

### Post by revlimit7000 on 2010-04-07
Another problem, ok well I need some help my cdrom inside of my laptop with ubuntu cant see the dvd/cd.
I have tried so many different cd and dvds that I know have data on them.  
It does not see them but when I restart the computer with the disk inside the drive it can see it until I take the disk out and put it back in. Can someone please help.

Thanks in advance

---

### Post by revlimit7000 on 2010-04-07
duplicity@duplicity-laptop:~$ mout -l
No command 'mout' found, did you mean:
 Command 'lout' from package 'lout' (universe)
 Command 'mount' from package 'mount' (main)
 Command 'mount' from package 'loop-aes-utils' (universe)
 Command 'most' from package 'most' (universe)
mout: command not found
duplicity@duplicity-laptop:~$ mount -l
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/duplicity/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=duplicity)
duplicity@duplicity-laptop:~$ ^C
duplicity@duplicity-laptop:~$ 


I cant tell if the drive is mounted....

---

### Post by brij on 2010-04-08
what is the output of dmesg when you insert the CD

---

### Post by revlimit7000 on 2010-04-08
Same

---

### Post by brij on 2010-04-08
weird are you sure its not a hardware problem?

---

### Post by snapback77 on 2010-04-08
I had a problem that drove me mad. My DVD burner would not work but my other dvdram would.  I disconnected the dvdram and my burner began to work perfectly.  If applicable this may save you hours!

---

