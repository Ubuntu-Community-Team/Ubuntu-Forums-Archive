---
title: "Mounting in /media, needs to be /dev"
date: 2009-03-28
forum: New to Ubuntu
---

### Post by Saerox on 2009-03-28
I need to mount a floppy disk in /dev/fdo, but the system default is putting it in /media/disk.  The mount command doesn't work because I can't create a folder in /dev.  Can anyone help me?

---

### Post by JKyleOKC on 2009-03-28
The problem here is that /dev, like /proc, isn't really a directory although it looks like one. It's the list of devices that your system recognizes, and /dev/fd0 is the first floppy disk device. To access that device, you must mount it which makes its file system available, and the mount point has to be an actual directory. The system default of /media/disk is just fine. If you open that directory after doing the mount, you'll see all of the files on your floppy disk (assuming that you actually have one in the drive).

This distinction between the device itself and the filesystem that lives in it is always confusing to newcomers, but it will rapidly become familiar...

---

