---
title: "How do I remove a space in the drive name"
date: 2009-07-02
forum: New to Ubuntu
---

### Post by gatorbrit on 2009-07-02
My internal NTFS disk mounts in the "Local Disk" directory as in this screenshot.  This is a pain when I want to type in the location as I have to put quotes around it because of the space between Local and Disk.   How can I change this to something with no space?
thanks

Rich

---

### Post by WRDN on 2009-07-02
First, open the Terminal and type:

```
sudo fdisk -l
```

This will give you information on the disks connected to the system.

Now, unmount the disk using:

```
sudo umount /dev/sdaX
```

X refers to the disk number.

Rename "Local Disk" (the mount point):

```
mv "/media/Local Disk" /media/LocalDisk
```

Finally, remount the disk using the mount command:

```
mount /dev/sdaX /media/LocalDisk
```

Again, X refers to the disk number.

---

### Post by gatorbrit on 2009-07-02
Thanks for the quick reply.   This:
```
mv "/media/Local Disk" /media/LocalDisk
```
doesn't work because it can't find the "Local Disk" anymore after I unmounted it.  

But I created a new directory "LocalDisk" and mounted to that using 
```
mount /dev/sdaX /media/LocalDisk
```
as you suggest.  

This works fine until I reboot and we're back to mounting in the old location.   How would I make this change permanent?

thks

---

### Post by WRDN on 2009-07-02
Edit /etc/fstab to change the mount point.

```
gksudo gedit /etc/fstab
```

---

### Post by gatorbrit on 2009-07-02
> **WRDN said:**
> Edit /etc/fstab to change the mount point.

```
gksudo gedit /etc/fstab
```

That did it.  Thks

---

