---
title: "Mounting Volumes and FSTAB"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by SillySod on 2009-01-11
Hello - could anybody help me with how I can put a reference to a mount point in the FSTAB file where I want the directory to have a space in it?

For example, if I want to have a volume called "Sillysod1 500GB" mounted to "media/Sillysod1 500GB" then how can I do this? If I try to enter this as the mount point in FSTAB, I get a "bad line in fstab" error.  The only way I can do it is putting a hyphen instead of the space, but I would prefer the space.

Is there a way of these mounted volumes appearing automatically on the desktop once they are mounted, and in the "Places" listing?  This seemed to happen originally when I first started using Ubuntu but hasn't happened for a few weeks now.

Hope somebody can help.

---

### Post by theozzlives on 2009-01-11
[http://ubuntuforums.org/showthread.php?t=1015834]("http://ubuntuforums.org/showthread.php?t=1015834")

---

### Post by drs305 on 2009-01-11
Enter it in fstab as:
```
Sillysod1**\040**500GB
```

*\040* is interpreted as a space.

---

### Post by supererki on 2009-01-11
i think that the easiest way to get correct mount options is to type

cat /etc/mtab
when the partition is mounted, and then add the line representing the partition to 
/etc/fstab

---

### Post by SillySod on 2009-01-14
Thanks for that, the \040 business has done the trick.

How do I get these mounted volumes showing up in "Places" and in the left-hand panel of the file manager, so I don't have to go through to the media directory every time to access them?

---

### Post by drs305 on 2009-01-15
> **SillySod said:**
> Thanks for that, the \040 business has done the trick.

How do I get these mounted volumes showing up in "Places" and in the left-hand panel of the file manager, so I don't have to go through to the media directory every time to access them?

If the device doesn't show up in the top portion of the Places list/left panel of your file manager, open the file browser and click on /media. Find the mountpoint in the right panel and drag it to the shortcuts section in the lower half of the left panel. You can rename the shortcut if you wish by right clicking and selecting Rename.

---

### Post by SillySod on 2009-01-18
Ooh good, that's it.  I've got all my hard drives showing up in the left panel now and in the "Places" menu!

Many thanks.

---

