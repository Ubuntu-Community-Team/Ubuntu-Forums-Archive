---
title: "Where is my iPhone mounted?"
date: 2011-01-12
forum: New to Ubuntu
---

### Post by asuastrophysics on 2011-01-12
Hey guys,

I'm trying to make songs I add via Rhythmbox actually show up in the ipod library on my iPhone. I'm following this guide:
[http://ubuntuforums.org/showthread.php?t=1484757](http://ubuntuforums.org/showthread.php?t=1484757)
The last post on the thread, written by "Zorael".

I can see, access, and modify fils on my iphone via the "Places" sidebar in nautilus, but I cannot figure out where it's being mounted at. 

I've checked the /media folder, but I don't see any folder named "ipod". I see a folder named "disk", but it's definitely not my iphone because it says it's 150GB. I tried unmounting this to see if maybe the iphone was trying to use the same name, but Nautilus says that "Disk" is already unmounted.
I've checked the /mnt folder, but it's empty.
I've checked the /dev folder, but there's no file in there named "ipod".

Any ideas? Is there a way to tell where devices are being mounted? It would greatly help, as then I could fix my iphone so that I can actually listen to music on it. Thanks in advance!!! :D

---

### Post by ephmanjmm on 2011-01-12
In terminal:

sudo mount

---

### Post by asuastrophysics on 2011-01-12
Thanks for your quick reply! :P This was my output:
> jake@jake-desktop:~$ sudo mount
[sudo] password for jake: 
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/jake/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jake)

Do you know which of these is my iphone by any chance?

---

### Post by asuastrophysics on 2011-01-12
Ahh!!! Found it! 
> **gvfs-fuse-daemon on /home/jake/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jake) **

That's the one! Thanks for your help!

---

