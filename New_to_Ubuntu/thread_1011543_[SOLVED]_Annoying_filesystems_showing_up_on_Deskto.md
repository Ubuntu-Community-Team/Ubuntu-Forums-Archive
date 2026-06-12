---
title: "[SOLVED] Annoying filesystems showing up on Desktop"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by jakupl on 2008-12-14
I have four partitions, mostly for fun and to learn something about it.
one ext3 for /
one ext3 for /home
one reiserfs for /home/jakup/Pictures
and one ext2 for /home/jakup/Videos

the problem is that the last two partitions also show up on desktop.
How do I get rid of it?

here is my fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=a2ff8373-0811-4fb1-b701-ddd2e2659356 /               ext3    relatime,errors=remount-ro 0       1
# /dev/hda3
UUID=31ea3a12-dfab-42f2-b323-bd9d09cd6140 /home           ext3    relatime        0       2
# /dev/hda5
UUID=4e131ad6-d5df-4360-9f0c-8ad877f9f5f3 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/hda4 /home/jakup/Pictures reiserfs nodev,nosuid 0 2
UUID=37af7dce-4c5f-410c-92e4-990405223edf /home/jakup/Videos ext2 nodev,nosuid 0 2
```

---

### Post by drs305 on 2008-12-14
Here is one solution, although it is not an elegant one.

Using gconf-editor, deselect /apps/nautilus/desktop/volumes_visible . This will remove all volumes from the Desktop. I don't know of a way to selectively display only certain volumes (although I believe there may have been a time when only those mounted in /media were displayed).

Here is the command line to do the above. You can show the volumes by changing the value back to 'true':
```

gconftool-2 --type bool --set /apps/nautilus/desktop/volumes_visible 'false'

```
Now you can make a symlink of any mountpoint you want and place the link on the Desktop. It will initially appear as a folder icon, but you can change the icon if you wish. Note the symlink will always be on the Desktop, whether the volume is actually mounted or not, since the link is to a mountpoint and not the device itself.

---

### Post by nhasian on 2008-12-14
I know that things mounted in /media appear on the desktop but yours arnt in /media.  you can try this in a terminal:

```
gconf-editor
```

apps->nautilus->desktop-> volumes visible (unselect) removes all volumes icon

---

