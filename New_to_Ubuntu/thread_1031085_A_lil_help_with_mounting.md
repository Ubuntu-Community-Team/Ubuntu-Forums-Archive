---
title: "A lil help with mounting"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by CharmlessMan on 2009-01-05
After googling & browsing & not finding anything that really could help I'm braving a bashing by starting a thread for something that's more than likely been answered. I apologize in advance.

I just installed LInux today & when trying to mount my backup drive I get this[IMG]http://i125.photobucket.com/albums/p71/jigsaw695/crappitycrapcrap.jpg[/IMG]

I've tried a few things like sudo but I'm doing something wrong(as usual)

ANy help would be greatly appreciated.

---

### Post by solarix on 2009-01-05
please be so kind and follow those steps.

Open a terminal.

type in 

```
mount
```

and then paste it into the thread.

Are you using an USB Harddrive?

Next..

also on the terminal

```
cat /etc/fstab
```

provide this information too.

I assume your backup Disk is a Windows ntfs Disk. Am i right?

Cheers

---

### Post by CharmlessMan on 2009-01-05
> **solarix said:**
> please be so kind and follow those steps.

Open a terminal.

type in 

```
mount
```

and then paste it into the thread.

Are you using an USB Harddrive?

Next..

also on the terminal

```
cat /etc/fstab
```

provide this information too.

I assume your backup Disk is a Windows ntfs Disk. Am i right?

Cheers


From MOunt I got this


simon@Labratory:~$ mount
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
gvfs-fuse-daemon on /home/simon/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=simon)


And from the latter

simon@Labratory:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=f3d68456-6a12-4630-a4a5-b940e23df9f7 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=7cb78e09-196d-4574-a1a5-6524d916c0e8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
simon@Labratory:~$ 



IT's a SEaGAte INternal Hard Drive.

> I assume your backup Disk is a Windows ntfs Disk. Am i right?

I am not sure as my WIndows discs that came with my PC have been misplaced for quite sometime now.

---

### Post by joshmuffin on 2009-01-05
> **CharmlessMan said:**
> 

And from the latter

simon@Labratory:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=f3d68456-6a12-4630-a4a5-b940e23df9f7 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=7cb78e09-196d-4574-a1a5-6524d916c0e8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
simon@Labratory:~$ 


was the usb plugged in when you did this? it should be

If yes should be an easy fix:

In the terminal

```
sudo cat /etc/fstab
```

Put a # on the last line:

Old: > /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

New: #/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

Easy enough.Should fix all you problems. If not, I'm probably of no more use.



If no do it again with the USB in and then PM me.

Hope I helped, Joshmuffin.


and if both fail undo what I suggested and:
Plug it into an XP machine and instead of just pulling it out, safely remove it.
I trust you know how to do that, if not PM me.

---

### Post by Gwasanaethau on 2009-01-05
> **joshmuffin said:**
> …```
sudo cat /etc/fstab
```…
You mean:
```
gksu gedit /etc/fstab
```;)

---

### Post by joshmuffin on 2009-01-05
Both work

But CharmlessMan could you please re-do it with the USB in.

---

### Post by CharmlessMan on 2009-01-05
I tried with it plugged into the drive & not. No avail. I think I'm gonna have to use my friends Windows CD.

---

### Post by CharmlessMan on 2009-01-05
So I'm gonna have to re download WIndows then safely remove the INTERNAL drive. Blah.

Thanks for the help guys! I know many forums frown upon newbies starting new threads so thanks for being very helpful.

GIven how lil I know about this stuff, I'm sure I'll be back here soon heh.

---

### Post by Racecar56 on 2009-01-05
You don't have to.
Just  boot into Windows.
Safely remove your backup hard drive and unplug it.
Go in Ubuntu and plug in HD. Done!
EDIT: Realized that it was internal, it may be possible but it's gonna be more hard.

---

