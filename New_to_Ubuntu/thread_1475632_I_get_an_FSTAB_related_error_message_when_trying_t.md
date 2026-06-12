---
title: "I get an FSTAB related error message when trying to mount a data DVD"
date: 2010-05-07
forum: New to Ubuntu
---

### Post by diablo75 on 2010-05-07
I just whipped out some data DVD discs that I burned several years ago that are still in mint condition.  Yet when I insert them into my computer I get the following error:

```
Error mounting: mount exited with exit code 1: helper failed with:
[mntent]: line 15 in /etc/fstab is bad
mount: can't find /dev/sr0 in /etc/fstab or /etc/mtab
```

Not sure what to do about this.  Any ideas?


Here is a copy of my fstab file:

> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=9408c45f-970c-408f-a313-9bd019ba963d /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=92916a37-406f-4a43-b6d2-0200d0275a16 /home           ext3    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=4a9b3714-c90f-4a58-96f0-621aa84d26a8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       none /proc/bus/usb usbfs devgid=46,devmode=666 0 0

---

### Post by diablo75 on 2010-05-07
I think I figured it out... to a certain extent.

Line 15 of my fstab file actually contained two statements which should have been seperated by a carraidge return but weren't.  So this:

```
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 none /proc/bus/usb usbfs devgid=46,devmode=666 0 0 
```

Should have read more like this:

```
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 
none /proc/bus/usb usbfs devgid=46,devmode=666 0 0 
```

However, I got an error message during boot saying there was an error mount "/proc/bus/usb" which I chose to skip.

That particular line was added a couple years ago to bypass a permission issue I used to have with Virtualbox, not being able to mount USB devices like I needed it to.  This issue, I believe, no longer exists but I haven't tested it yet.  I have commented out that line which should get rid of the error upon reboot and hopefully USB functionality will still work in Virtualbox... have to see...

Anyway, I solved my own issue... love that feeling :)

---

### Post by Mustard on 2010-05-07
Well done. :)

---

