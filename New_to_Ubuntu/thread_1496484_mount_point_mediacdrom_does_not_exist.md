---
title: "mount point /media/cdrom does not exist"
date: 2010-05-29
forum: New to Ubuntu
---

### Post by harryliddic on 2010-05-29
I am getting an error message > mount: mount point /media/cdrom does not exist. a cdrom was mounted in both /etc/fstab and /etc/mtab just late last night now it 10.04 can't see it

---

### Post by ajgreeny on 2010-05-29
The /etc/fstab file no longer has an entry for cdrom, which it used to have, even in karmic, like this:-
```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```
The cdrom dev name is now /dev/sr0 I think, so I don't know if it is possible to add a line to fstab staring with this instead of /dev/scd0, but I suspect it will not help.  Even when a cd is in my drive and playing, showing mounted in the disk-mounter applet, there is still no entry for it in /etc/fstab.

---

### Post by harryliddic on 2010-05-29
My fstab has /dev/sr0 but the mount point was /media/cdrom. I changed it to /media/cdrom0 but it still did not work. should I erase the entry all together. as I recall last night that was working of course I filled up six pages of the terminal and I am a little hazy on what all I I typed ( speaking of which my typing is getting better with linux)

---

### Post by spykerhond on 2011-11-17
I have the same buggy ubuntu 11.10 server problem .
ubuntu 10.04 , 11.04, 11.10 servers cant use cdrom drives (sudo mount /media/cdrom0)
Please ubuntu forum????? What is the nerd factor secret to being able to eject the god dam thing , but not being able to mount it ???

---

