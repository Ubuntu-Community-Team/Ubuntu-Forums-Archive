---
title: "Help fix broken fstab"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by InlawBiker on 2009-10-30
OK So I installed 9.10 yesterday and have run into a problem.  I made an error in /etc/fstab, no big deal right?  Now the system stops while booting saying there is a problem with /etc/fstab and cannot mount my data partition.

Hitting ESC here brings me into a root shell, but I cannot write to the / filesystem to edit /etc/fstab.  It mounts read only so even "w!" in vi will not work.

When I boot the live CD I also cannot mount the root partition read/write so I can edit /etc/fstab.

What is the proper way to mount my root partition read/write so I can fix fstab?

Thanks,
Greg.

---

### Post by SuperSonic4 on 2009-10-30
A Live CD would be the simplest way beyond a full restore (if you have to you may be able to copy any data off)

I'm not sure why it won't mount read/write, did you try passing the -rw flag when issuing the mount command?

---

### Post by diesch on 2009-10-30
```
mount -o remount,rw /
``` should mount / read/write

---

### Post by alphaniner on 2009-10-30
Boot into LiveCD.

Open terminal.

Run the following commands:

```
sudo mkdir /media/mount
sudo mount /dev/sd__ /media/mount
sudo vi /media/mount/etc/fstab
```

changing __ to reflect the name of your / partition.

When done,

```
sudo umount /media/mount
```

---

### Post by InlawBiker on 2009-10-30
> **diesch said:**
> ```
mount -o remount,rw /
``` should mount / read/write

This did the trick, thanks!

---

