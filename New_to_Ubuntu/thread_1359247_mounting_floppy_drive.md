---
title: "mounting floppy drive"
date: 2009-12-19
forum: New to Ubuntu
---

### Post by bobanshirl on 2009-12-19
I have tried to find the answer on the forum and in two Ubuntu books,but no joy.I have the floppy disk drive icon on the desktop,I put a floppy in and double click the icon,I get an error box,Unable to mount Location.
         No medium in the drive.Dont really know what to do now.Appreciate any advice.Many thanks

---

### Post by chuina on 2009-12-19
insert a floopy disk
open a terminal and type 

```
sudo mount
```it will show where the floppy is mounted.

---

### Post by bobanshirl on 2009-12-19
Im afraid this didnt work.I will copy and paste the result as I have not a clue.
  /dev/loop0 on / type ext4 (rw,errors=remount-ro)
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
/dev/sda5 on /host type fuseblk (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/bobstocker/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=bobstocker)
/dev/sda1 on /media/A25898125897E379 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)

---

### Post by chuina on 2009-12-19
your previous post 's last two line:

```
/dev/sda1 on /media/A25898125897E379 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,b  lksize=4096)
```

have u try to browse in  /media/A25898125897E379 ?

---

### Post by bobanshirl on 2009-12-19
Being a newbie from Windows XP I dont know with what and how to brwse the last two lines and in the end is it going to mount my floppy disk drive.It is incomprehensible that Linux/Ubuntu or whatever does not see the floppy disk drive but sees my two cd/dvd drives.

---

### Post by garyed on 2009-12-19
look in /media & see if you have a directory called floppy.
If not create one. ```
sudo mkdir /media/floppy
``` 
Then do:
```
sudo mount /dev/fd0 /media/floppy
```

---

### Post by joes7 on 2009-12-19
You don't have to do a thing apart from plugging it in.

---

### Post by bobanshirl on 2009-12-19
Many thanks Gary there was a floppy shown in Media so the second input in Terminal did the trick.I am getting there slowly.

---

### Post by bobanshirl on 2009-12-19
It might work on your pc but it does not work on mine.Reading your reply one would think I have been sitting here with the floppy in my hand

---

### Post by Old_Grey_Wolf on 2009-12-19
This is off topic I think.

After I read this thread, I got an old Floppy drive out of my junk box. I hooked it up to my computer running Ubuntu 9.04. It was recognized without any problems. I then, installed DOSBox Emulator from the repository. I had an old floppy of the DOS version of SOKOBAN.EXE. I changed to the directory were SOKOBAN was located and ran the .EXE file. It started up just fine.

WOW, this is going to be fun. I have a lot of those old floppies in my computer junk box for no reason. Now they can actually be used again.

Oh, Sokoban is in the repositories in a Linux incarnation. 

:lolflag::guitar:

---

### Post by garyed on 2009-12-19
Just because floppy drive shows up it doesn't mean that it is already mounted properly. I don't know if it's a bug or not but it is unpredictable
on both my computers with 3 different versions of Ubuntu & all have them mounted in fstab. After manually mounting it always works.

---

### Post by DJnRF on 2010-02-26
> **garyed said:**
> look in /media & see if you have a directory called floppy.
If not create one. ```
sudo mkdir /media/floppy
```Then do:
```
sudo mount /dev/fd0 /media/floppy
```


Now, that would seem simple enough. However, 
since I am very 'simple minded', a kind of simpleton, 
I still cannot find any file, word, or other indication 
of a place called "Media" in my Ubuntu 9.10. 

Plus, since I do not have any floppy icon, nor can 
I find any reference to such anywhere here, How 
can I get this OS to recognise my floppy drive so 
that I may use it?  

I have tried two separate methods listed in Help, and 
in the forum to 'mount' it to no avail. What is the 
trick?

---

