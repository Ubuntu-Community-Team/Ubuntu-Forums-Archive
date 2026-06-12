---
title: "floppy drive"
date: 2009-02-28
forum: New to Ubuntu
---

### Post by boyax16 on 2009-02-28
newbie to Ubuntu....how do I make Ubuntu "see" my floppy drive (yes, I still use it). It sees my cd drive.
TY so much for your help.

---

### Post by 3rdalbum on 2009-02-28
From what I've read, you need to run:

```
sudo modprobe floppy
```

to enable it. You may also need to mount floppy disks manually, and I believe the device file is generally /dev/fd0. Mounting manually will require you to create a "mount point" (a directory that the contents of the floppy disk should appear in), make it readable and writable by your user or by everyone, and then mount it.

This would be a sample:

```
sudo mkdir /mnt/floppy
sudo chmod a+rw /mnt/floppy
sudo mount /dev/fd0 /mnt/floppy

```

UNMOUNT THE FLOPPY DISK BEFORE REMOVING IT. You can do this by running "sudo umount /mnt/floppy".

---

### Post by boyax16 on 2009-02-28
Thanks so much.....will try.

---

### Post by prshah on 2009-02-28
> **boyax16 said:**
> newbie to Ubuntu....how do I make Ubuntu "see" my floppy drive 

From Intrepid, the handling of dynamic filesystems such as floppy, cdrom etc has changed.

You now no longer need an entry in the /etc/fstab for such devices. If your fstab file has an entry for the floppy drive, comment it out, and restart.

Then, just insert your floppy and double click the drive in the "Places-Computer" window.

The floppy inside the drive will be automatically "loaded" (mounted), and the contents made available at a directory under /media/.

---

