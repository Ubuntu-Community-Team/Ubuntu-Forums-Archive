---
title: "CD/DVD-ROM Drive Mounting Problems"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by Davurnium on 2008-12-14
Greetings everyone, this is my first post on these forums and second day running ubuntu. I recently converted from Windows Vista. I love almost everything about this linux system so far, but I've encountered a rather nasty problem. 

I cannot seem to mount the CD drive that is installed in my laptop. The system is an HP dv6000 which has had no drive troubles in the past. Each time that I run commands along the lines of 

> "nathan@nathan-laptop:~$ sudo mount /dev/scd0" 

I get the result: 
> 
"mount: special device /dev/scd0 does not exist"


Hopefully someone here could help me address this. Here is my cat /etc/fstab information. 

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d24036b4-909b-4cd8-a37a-b2be8d954bdd /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=ae110bfb-e787-41e8-8fdf-b12a580e469a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,auto,exec,utf8 0       0


Thank you in advance for any help!

---

### Post by newbee70 on 2008-12-14
> **Davurnium said:**
> Greetings everyone, this is my first post on these forums and second day running ubuntu. I recently converted from Windows Vista. I love almost everything about this linux system so far, but I've encountered a rather nasty problem. 

I cannot seem to mount the CD drive that is installed in my laptop. The system is an HP dv6000 which has had no drive troubles in the past. Each time that I run commands along the lines of 



I get the result: 


Hopefully someone here could help me address this. Here is my cat /etc/fstab information. 




Thank you in advance for any help!



open terminal and.


enter mount.

post the results.   (copy / paste the results in your reply)

And Welcome to the forums.

---

### Post by Davurnium on 2008-12-14
As requested: 

> /dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/nathan/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=nathan)
/dev/sdb1 on /media/KINGSTON type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)


---

### Post by newbee70 on 2008-12-14
> **Davurnium said:**
> As requested:

Davurnium;

Do you have a dvd or cd with data on it in the drive?

if not please put one in and after it loads redo the mount and post it again. I should have asked if you had a disk in the drive.

---

### Post by Davurnium on 2008-12-14
No trouble! Actually, though, an audio CD was present (Beethoven's 9th). This is a repeat of the process using a data DVD, the one containing the files used to install ubuntu. It appears to me at first glance to be the same...

> 
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/nathan/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=nathan)
/dev/sdb1 on /media/KINGSTON type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

---

### Post by newbee70 on 2008-12-14
> **Davurnium said:**
> No trouble! Actually, though, an audio CD was present (Beethoven's 9th). This is a repeat of the process using a data DVD, the one containing the files used to install ubuntu. It appears to me at first glance to be the same...



Do you have a thumb drive in your system?

if not try cd'ing " changing directory to your cd as /media/KINGSTON

or this:  /dev/cdrom

I was actually expecting to find something like this in that file.

/dev/scd1 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=newbee70)

newbee70@hooters:~$

---

### Post by Davurnium on 2008-12-14
Whoops, I did indeed have a thumb drive in a usb port. I've removed it now, here is the newest attempt. 

> /dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/nathan/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=nathan)


As for the commands you want me to carry out, could you specify what they would look like in more detail? I did the following; 

"nathan@nathan-laptop:~$ /dev/cdrom
bash: /dev/cdrom: No such file or directory"

---

### Post by newbee70 on 2008-12-14
ghost@hooters:~$ cd /media/cdrom0
ghost@hooters:/media/cdrom0$ ls -a
.                         bookmarks.html            misc documents
..                        Zars Site                 My Pictures
ammunition inventory.xls  linux_file_structure.jpg  reloading
Application Data          Local Settings
ghost@hooters:/media/cdrom0$


this is my printout of terminal to show it does work.

---

### Post by newbee70 on 2008-12-14
> **Davurnium said:**
> Whoops, I did indeed have a thumb drive in a usb port. I've removed it now, here is the newest attempt. 




As for the commands you want me to carry out, could you specify what they would look like in more detail? I did the following; 


                                   |
"nathan@nathan-laptop:~$ /dev/cdrom **missed the 0 here "zero" **
bash: /dev/cdrom: No such file or directory"


try that again with /dev/cdrom0 

and did you try /media/cdrom0 ?

---

### Post by newbee70 on 2008-12-14
have you tried this???? from your fstab file.



 mount /dev/scd0\ media/cdrom0

or sudo mount /dev/scd0\ media/cdrom0

---

### Post by Davurnium on 2008-12-14
Sorry for the delay, and worry not, I believe you when you say things should work! Here is the result of the most recent suggestion: 

> nathan@nathan-laptop:~$ mount /dev/scd0\ media/cdrom0
mount: can't find /dev/scd0 media/cdrom0 in /etc/fstab or /etc/mtab


I also tried accessing the media directory and using the "ls -a" command to display the contents of the disk. I accessed the directory successfully (zeroes at the end of "cdrom" and all), but I got ". .." in response, which suggests that there's nothing in there.

---

### Post by newbee70 on 2008-12-14
> **Davurnium said:**
> Sorry for the delay, and worry not, I believe you when you say things should work! Here is the result of the most recent suggestion: 



I also tried accessing the media directory and using the "ls -a" command to display the contents of the disk. I accessed the directory successfully (zeroes at the end of "cdrom" and all), but I got ". .." in response, which suggests that there's nothing in there.



 (ii)  When  mounting  a  file system mentioned in fstab, it suffices to
       give only the device, or only the mount point.

 (iii) Normally, only the superuser can mount  file  systems.   However,
       when  fstab  contains  the user option on a line, anybody can      mount the corresponding system.

       Thus, given a line

              /dev/cdrom  /cd  iso9660  ro,user,noauto,unhide

       any user can mount the iso9660 file system found on his CDROM using the command
              mount /dev/cdrom
       or
              mount /cd

       For  more details, see fstab(5).

I'm gonna have to let the more knowledgeable on the forums work with you on this.

---

### Post by Davurnium on 2008-12-14
Alright, well I appreciate all you've done (that's a thank you - I take it they mean something on these forums? :) ). If anyone else has any ideas or suggestions for me, please, I am all ears.

---

