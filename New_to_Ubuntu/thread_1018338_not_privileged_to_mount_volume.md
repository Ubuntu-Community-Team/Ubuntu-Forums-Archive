---
title: "not privileged to mount volume?"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by Jin127 on 2008-12-22
Apparently I'm not privileged to mount my external HD.  Why?  I'm confused, it seemed fine a minute ago.  How do I get around this?

Thanks for the help.

---

### Post by DGortze380 on 2008-12-22
> **Jin127 said:**
> Apparently I'm not privileged to mount my external HD.  Why?  I'm confused, it seemed fine a minute ago.  How do I get around this?

Thanks for the help.

preface the mount command with the word sudo to execute with root privledges

---

### Post by Jin127 on 2008-12-22
I don't know the command for mounting, sorry.  What is it?

---

### Post by DGortze380 on 2008-12-22
how were you trying to mount the drive before then??

open a terminal
type the command: df -l

plug your hard drive in.

type df -l again
find you drive by comparing the outputs of the df -l commands

create a new mount point, for example, the command: sudo mkdir /media/myExternal
mount your drive to the mount point, example: sudo mount /dev/sdb1 /media/myExternal

to unmount this example:
sudo umount /media/myExternal

---

### Post by Jin127 on 2008-12-22
i dunno, right-click, + "mount"
>.> thanks though.

---

### Post by igknighted on 2008-12-22
In nautilus (the file browser) you should see your drive listed on the left hand side column.  Click it, and it should pop up a box asking for your sudo password to mount the drive.

If you add your user to the group 'mount' it should let you do it without a password, but you would need your sudo password to do that.

---

### Post by vanadium on 2008-12-22
This could be just an ntfs formatted drive that was not properly closed.

By default, an external drive should mount automatically. If it doesn't, then there is something wrong. First we need to find out what.

@Jin127: you should provide the precise error message you get when the drive is being connected. Also tell how you are trying to do the mounting (just connecting the drive? Clicking an icon?...) Otherwise, we can only guess and you will continue to get well-intended but confusing and inappropriate help.

---

### Post by Jin127 on 2008-12-22
eh, well it works now though.  ??  Dunno why, but that's alright.  :D  Thanks for the help though, I'll save it in case it fails again.

---

