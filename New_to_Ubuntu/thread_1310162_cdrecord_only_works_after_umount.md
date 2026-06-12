---
title: "cdrecord only works after umount"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by SirSlipALot on 2009-11-01
Hi All,

I want to determine the manufacturer or media id, and other information like the date of creation,
of my cds and dvds using the shell (bash)

$ cdrecord -atip dev=/dev/sr0
gives errors...:
(...)
WARNING: /dev/sr0 seems to be mounted!
(....)

so i tried :
$ umount /dev/sr0
$ cdrecord -atip -> now it works and i can see the manufacturer !

but now i have a problem: i can't remount the cd-rom
$ mount /dev/sr0
hangs for a while and then gives an error:
mount: can't find /dev/sr0 in /etc/fstab or /etc/mtab


if I add to /etc/fstab the line
/dev/sr0 /media/cdrom0 udf,iso9660 ro,user,auto 0 0

I can mount and umount without su priviliges but the mount point isnt't /media/<volume name> anymore! :(

How can I get around this?
Is there a way to edit /etc/fstab  that allows a normal user to umount and mount preserving the labeled mount point?

help...

PS: I understand that hal mounts the cd automatically to the mount point /media/<volume name>
and
$ gnome-mount --display-settings --device /dev/sr0
Displaying settings for volume (overrides drive settings)
hal udi:      /org/freedesktop/Hal/devices/volume_label_books_online01
There are no settings; you can use --write-settings

but it is still beyond me how to umount and remount without a fuss .......

---

### Post by schily on 2009-11-02
As mentioned in the other thread: you are not using cdrecord
but a defective fork and your problems are caused by the fork.

Please use recent original software from:

[ftp://ftp.berlios.de/pub/cdrecord/alpha/](ftp://ftp.berlios.de/pub/cdrecord/alpha/)  
[http://cdrecord.berlios.de](http://cdrecord.berlios.de)

---

