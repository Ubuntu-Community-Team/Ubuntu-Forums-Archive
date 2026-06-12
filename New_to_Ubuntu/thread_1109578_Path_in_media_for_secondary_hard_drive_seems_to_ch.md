---
title: "Path in /media/ for secondary hard drive seems to change; I need it to be static"
date: 2009-03-28
forum: New to Ubuntu
---

### Post by diablo75 on 2009-03-28
I have a few different hard drives attached to a machine and a virtual XP machine running in Virtualbox.  I set up a mapped network drive via Virtualbox shared folders to /media/disk-1/ which gave me access to everything on that drive within the virtual machine.  But this path does not seem to always be the same.  Most recently, the HD mounted as /media/disk-2/ instead of disk-1 so when XP tried to access it, it said it was unavailable because VB was no pointing to the wrong path.

Is there a way to force this drive to mount always as "disk-1" in the media directory?

---

### Post by doas777 on 2009-03-28
to do that, you just need to add the second drive in your \etc\fstab file
heres a tutorial for fstab: [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by Rolcol on 2009-03-28
One solution would be to label the partitions so they always mount as their names.

---

### Post by diablo75 on 2009-03-29
> **Rolcol said:**
> One solution would be to label the partitions so they always mount as their names.

How do you do that?

---

### Post by diablo75 on 2009-03-29
After digging through that guide and going to a community doc for automounting, I'm using the **pysdm** package, as it's simple to use and eliminates the need for me to manually edit the fstab file (it does it for me).

---

### Post by mikechant on 2009-03-29
> How do you do that?

(label volumes)


Just use the e2label command for ext2/ext3 partitions.
E.g.I did
sudo e2label /dev/sdc1 usba
and my external drive always mounts as /media/usba

---

