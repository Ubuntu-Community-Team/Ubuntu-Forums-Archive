---
title: "advanced scripting help"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by rburkartjo on 2008-12-12
i moderate a linux form on another site and cant figure this out. i need a script to mount an unmounted volume. i can do it manually after i login by going to places computer:/// right clicking 280.7 GB Media and then clicking on mount. maybe this cant be done. /tks cheesemaker

---

### Post by karlr42 on 2008-12-12
```
sudo mount -t ext3 /dev/<parition to mount> /<mountpoint>  
```
? But you really need to mount it in your fstab. Search the forum, this has been covered a million times.

---

### Post by wd5gnr on 2008-12-12
After you mount the volume using the GUI, open a terminal and type:

mount

You will get a bunch of lines that look like this:

/dev/sdc3 on /media/foo type ext3 (rw,errors=remount-ro)

Yours will be different of course. If the type is fuseblk, you may need to know the type of the filesystem (NTFS, ext3, etc.).

Now the script command is:

mount -t ext3 -o rw,errors=remount-ro /dev/sdc3 /media/foo

The script will have to run as root (sudo) unless you have your system set up to allow user mounts.

You can also modify /etc/fstab to name the volume and then issue:

mount NAME 

(where NAME is whatever you called the disk in mtab). You can add the "user" option in fstab to allow non-root to mount the disk.

A line in fstab looks like:

/dev/sdc3 /media/foo ext3 rw,errors=remount-ro 0 0

The noauto option will keep it from mounting automatically (although maybe that's what you want anyway). You can cat /proc/mounts to see what's already mounted.

---

### Post by rburkartjo on 2008-12-12
wd, still lost i want to mount this
/dev/sda3 on /media/disk type ext2 (rw,nosuid,nodev,uhelper=hal)
tks/cheesemaker

---

### Post by wd5gnr on 2008-12-12
> /dev/sda3 on /media/disk type ext2 (rw,nosuid,nodev,uhelper=hal)

sudo mount -t ext2 -o nosuid,nodev,rw /dev/sda3 /media/disk

Try that.

---

### Post by rburkartjo on 2008-12-12
wd got this from terminal
ray@ray-desktop:~$ sudo mount -t ext2 -o nosuid,nodev,rw /dev/sda3 /media/disk
[sudo] password for ray: 
mount: mount point /media/disk does not exist
ray@ray-desktop:~$ 
also this might help when i restart i get the error message that i have an error on fstab line #4 . here is fstab  


proc            /proc           proc    defaults        0       0


 
UUID=b28b7c0f-4480-442e-836c-100b5157c333 /               ext3    relatime,errors=remount-ro 0       1
UUID=4dce963f-5a4a-4d91-9196-09b1d6ef8c76 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
tks/cheesemaker

---

### Post by wd5gnr on 2008-12-12
So the HAL is creating /media/disk when you plug the drive in. You can either make a new mount point or create /media/disk yourself (e.g., mkdir /media/disk). If you make a different name (highly suggested) you would need to change your mount command, of course.

---

### Post by rburkartjo on 2008-12-12
wd, tks for your help but still lost 
here is something that might help dont know but i ran this after i mounted 

ray@ray-desktop:~$ cat /proc/mounts
rootfs / rootfs rw 0 0
none /sys sysfs rw,nosuid,nodev,noexec 0 0
none /proc proc rw,nosuid,nodev,noexec 0 0
udev /dev tmpfs rw,mode=755 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
/dev/disk/by-uuid/b28b7c0f-4480-442e-836c-100b5157c333 / ext3 rw,relatime,errors=remount-ro,data=ordered 0 0
/dev/disk/by-uuid/b28b7c0f-4480-442e-836c-100b5157c333 /dev/.static/dev ext3 ro,errors=remount-ro,data=ordered 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=755 0 0
varrun /var/run tmpfs rw,nosuid,mode=755 0 0
varlock /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /lib/modules/2.6.27-10-generic/volatile tmpfs rw,mode=755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,nosuid,noexec,gid=5,mode=620 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,nosuid,nodev,noexec 0 0
/dev/sda3 /media/disk ext2 rw,nosuid,nodev,errors=continue 0 0
gvfs-fuse-daemon /home/ray/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user_id=1000,group_id=1002 0 0
ray@ray-desktop:~$ 

note the one that begins /dev/sda3 is the one
and again i really appreciate your help and the help i always get from this form.still for the life of me i cant figure out why when i do it the manual way that i mentioned in the beginning of my thread that it works and cant get it to work from a script/cheesemaker

---

### Post by wd5gnr on 2008-12-12
So what happens if with the disk unmounted you say:

mkdir /media/disk
mount -t ext2 -o nosuid,nodev /dev/sda3 /media/disk

(run as root)

???

---

### Post by rburkartjo on 2008-12-12
wd, tks for the extra effort we are getting somewhere that works
now all i need to know is the what to enter as the first line or two of the script i have tried sudo and that wont work because i must log on as root also tried the following and wont work

root@ray-desktop:~#
mkdir /media/disk
mount -t ext2 -o nosuid,nodev /dev/sda3 /media/disk
tks/cheesemaker

---

### Post by wd5gnr on 2008-12-14
Well if you set the permissions correctly you can make an entry in fstab as mentioned earlier to allow user mounting of the volume. Or you can run the script as root.

---

### Post by rburkartjo on 2008-12-14
wd, as always thanks for replying how would i write the script. note i just started messing around with them. was a windows user for years and never used scipts. here is what i wrote. i know it isnt the best. i have to open a root terminal and then copy and paste the script. then hit enter and it works. not the best way but a start.

root@ray-desktop:/home/ray# mkdir /media/disk
mount -t ext2 -o nosuid,nodev /dev/sda3 /media/disk

/tks cheesemaker

---

### Post by wd5gnr on 2008-12-14
The script would look like:

```

#!/bin/sh
mkdir /media/disk
mount -t ext2 -o nosuid,nodev /dev/sda3 /media/disk

```

If you put this in a file called "mountme" you'd need to issue this command one time:

chmod +x mountme

However, you still have to run it as root.
On the other hand, if you make /dev/sda3 user mountable you could simplify things. Edit /etc/fstab and make sure there is no line for sda3 already there. Either make a new line or replace the existing one with:

/dev/sda3   /media/disk    ext2     defaults,nosuid,nodev,user,noauto   0  0

By the way, unless you really need it to be on /media/disk I'd put it somewhere else since HAL may mount something else there. So do a mkdir once (doesn't need to be in the script) called /media/userdisk or whatever and then chmod 777 /media/userdisk (or whatever makes sense... 777 will give everyone read/write/browse on that directory). Then everywhere we've said /media/disk change to /media/userdisk.

If you make the directory permanent and make the above entry in fstab the script becomes really simple:

```

#!/bin/sh
mount /dev/sda3 

```

Because of the user option, you don't have to be root to run this.

Note that there are various security risks involved with all of this and if your server is public, you ought to understand them. For example, you might put noexec on the options to keep programs from running from the volume if you let users mount it. Etc. Etc.

---

