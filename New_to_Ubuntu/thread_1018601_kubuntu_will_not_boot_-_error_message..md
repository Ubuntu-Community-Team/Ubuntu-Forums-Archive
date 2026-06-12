---
title: "kubuntu will not boot - error message."
date: 2008-12-22
forum: New to Ubuntu
---

### Post by boblettoj99 on 2008-12-22
Hi when i start up kubuntu it gets about halfway through the blue loading bar then goes to this error message:

/etc/init.d/rc: 2: sed: Permission denied
init: Unable to execute "/bin/sh" for rc-default: Permission denied
init: rc-default main process (4270) terminated with status 255


the first line is shown about 20 times!
i think iv properly messed up my fstab which is where this is all going wrong...i think!
please someone heeeeelp!

---

### Post by taurus on 2008-12-22
See if you can boot into recovery mode from GRUB menu.  If not, try to boot your machine with a LiveCD, mount your partition (harddrive) where / is, and post the content of your /etc/fstab on the harddrive if you think that is where it goes wrong.

```
sudo fdisk -l
```

---

### Post by boblettoj99 on 2008-12-22
took a while but eventually managed to get it:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/sda2
UUID=c6c6db2c-d1cf-4f4a-b6f5-d28dee6adf4d / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/sda5
UUID=3e5ed18f-e85f-4b4e-88f6-6e0d0c4ed96b none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/fd0 /media/floppy0 auto user,atime,noauto,rw,dev,exec,suid 0 0
<device> /dev/disk auto nouser,atime,noauto,rw,nodev,noexec,nosuid 0 0
/dev/sda1 / auto nouser,atime,auto,rw,nodev,noexec,nosuid 0 0

---

### Post by boblettoj99 on 2008-12-22
windows partition is sda1
linux ext3 is sda2

---

### Post by taurus on 2008-12-22
> **boblettoj99 said:**
> took a while but eventually managed to get it:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/sda2
UUID=c6c6db2c-d1cf-4f4a-b6f5-d28dee6adf4d / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/sda5
UUID=3e5ed18f-e85f-4b4e-88f6-6e0d0c4ed96b none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/fd0 /media/floppy0 auto user,atime,noauto,rw,dev,exec,suid 0 0
**[COLOR="Blue"]<device> /dev/disk auto nouser,atime,noauto,rw,nodev,noexec,nosuid 0 0[/COLOR]**
**[COLOR="Red"]/dev/sda1 / auto nouser,atime,auto,rw,nodev,noexec,nosuid 0 0[/COLOR]**

The second to last line in your /etc/fstab is wrong.

The last line is dangerous.  Since /dev/sda1 is ntfs (windows), somehow you try to mount it to /, root filesystem.  If you want to mount your windows partition so you can access it, mount it to somewhere like /media/windows BUT not /.

So, edit /etc/fstab and either remove the second to last line and modify the last line to make it look something like this.

```

/dev/sda1 /media/windows auto nouser,atime,auto,rw,nodev,noexec,nosuid 0 0

```
And of course, you need to create that new mount point, /media/windows, it /dev/sda1 will be able to mount to it.

---

### Post by amitkr on 2009-06-27
**/etc/init.d/rc: 2: sed: Permission denied** 			
I am not able to login to ubuntu 7.04. As the bootin starts and the bar starts filling, a black screen appears and it says - /etc/init.d/rc: 2: sed: Permission denied, almost 20 times. I tried to login from recovery mode, but failed. I don't have any clue now, how to recover my data. I got the ubuntu 7.04 live cd, somebody said run it, but it doesn't shows my data, so I am not installing it. Please, help me out.........plzzzzzzzzzzzz. My position is very bad and I despeately need my data. I don't have any backup of those. plzzzzzzzzzzzzzzzzz:sad:

---

