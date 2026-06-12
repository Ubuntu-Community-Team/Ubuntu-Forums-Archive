---
title: "unable to show contents of the folder"
date: 2009-04-21
forum: New to Ubuntu
---

### Post by supererki on 2009-04-21
hello.

i was trying to change songs on my creative zen v so i plugged it and everything was fine, it recognized the device and everything, so i then went to the drive and tried to open music folder and it said : 
The folder contents could not be displayed.
Sorry, could not display all the contents of "Music": Failed to get file list: -8: Fixed limit exceeded

i just upgraded to jaunty. and i didnt have this problem before. and also i tried it with gnomad, which said that it doesn't find the device. 

another thing what takes my piss to the boil is that I can't see where it is mounted? 

erki@psytrance:~$ mount
/dev/sda5 on / type ext3 (rw)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
/dev/sda6 on /home type ext3 (rw,relatime)
/dev/sda2 on /data2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/erki/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=erki)
/dev/sdc1 on /media/FRISBY type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sda7 on /media/stuff type ext3 (rw,noexec,nosuid,nodev,user=erki)
/dev/sdb1 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

and FS type is gphoto2.. wtf is this?

---

### Post by supererki on 2009-04-21
nobody?

---

### Post by halitech on 2009-04-21
there's a few ideas here on getting the zen to work

[http://ubuntuforums.org/showthread.php?t=216191](http://ubuntuforums.org/showthread.php?t=216191)

---

### Post by Ocat on 2009-05-22
Exact same problem here, Creative Zen V Plus.
Gnomad, kzenexplorer, Rhytmbox+MTP plugin do not work, my guess is because of the fact that it makes it "gphoto2://[usb:001,004]/". I can navigate most of its directories, but the important one, the Music directory, gives the "Sorry, could not display all the contents of "Music": Failed to get file list: -8: Fixed limit exceeded" error.

---

### Post by Ocat on 2009-06-17
I am able to open it in Rhythmbox now. It only works if I open Rhythmbox first, and then attach the mp3 player. Between the gphoto thing and Rhythmbox all folders are usable now.

---

### Post by freddybob on 2009-09-10
I see this problem when trying to view an MTP folder containing 1000 files or more in Nautilus.

Anyone know where the fixed limit is configured?

---

### Post by anywebloco on 2009-10-31
I think the problem muight be in this line in gphoto2-list.c

#define 	MAX_ENTRIES   1024

[http://www.gphoto.org/doc/api/gphoto2-list_8c.html](http://www.gphoto.org/doc/api/gphoto2-list_8c.html)

---

