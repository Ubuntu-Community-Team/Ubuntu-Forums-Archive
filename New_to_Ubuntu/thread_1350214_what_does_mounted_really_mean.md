---
title: "what does mounted really mean?"
date: 2009-12-09
forum: New to Ubuntu
---

### Post by listerdl on 2009-12-09
Hi I created a partition called Storage which is NTFS, (I dual boot and wanted to share the same data storage partition).

I am certain that I have successfully made ubuntu NTFS-config so that it can write to the partition....

OK, my question - what does it really mean when I boot up in ubuntu the 'storage' partition is on my desktop, rather like if you pop in a thumb drive it displays the device. Now, if I was to unmount this partition as per my desktop, does that mean that it will stop working and reading/wrriting data?

Thanks.....

---

### Post by zeroseven0183 on 2009-12-09
I would say yes, it won't be able to read/write any file. You have to mount it so Linux can access the filesystem of that partition.

For more information, see [https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)

---

### Post by Robert Lutken on 2009-12-09
Mounted means that the linux o/s has "gone onto" that partition, when you un-mount the partition it means that linux is no longer lookin at that partition.
so yes it when you un- mount you can not read write anything on that partition.

---

### Post by SteveNorman on 2009-12-09
To add to Robert's post

Mounting *includes* the partition in the tree of files accessible by the OS. So the MOUNTED partition is included in the files of your working OS. Linux sees everything as a file, usb, mp3 players, cameras, Hard drives, partitions etc. When you mount something it becomes another file to your os, and the rules that apply to files now apply to the thing that was mounted. Note that you have to have a mount point directory to mount something, and its as if you are filling the directory with files when you do the mount.

unmounting (umount) removes the /dev from the tree of files that can be altered within the os.

you should always unmount something before pulling it to make sure that data is safe. Unmounting is a procedure that moves data to or from the thing being mounted before removing it from the file tree.

Note you can mount something without it being in fstab. But fstab entries can save you a pain in the buttocks.

What you are experiencing is the auto-mount devilry that gnome does. Only High priest in dark dark caverns know how it happens. It can madden you if you try. Run fluxbox without gnome for awhile if you want to really understand mounting, as you gotta do it all by the command line, without magic or witchcraft involved causing things to apperate onto your desktop.

---

### Post by John Bean on 2009-12-09
The term "mounted" comes from an era when the actual magnetic disk was generally separate from the drive electronics, much like a modern optical disk. Just like a CD/DVD the disk had to be physically mounted on the drive unit before it could be accessed (obviously) and this became the extended analogy describing the process of making any data source available as a filesystem - even for devices with physically fixed disks or no disks at all.

---

### Post by ukripper on 2009-12-09
> Mounting, in computing, is the process of making a file system ready for use by the operating system, typically by reading certain index data structures from storage into memory ahead of time. The term recalls a period in the history of computing when an operator had to physically place (mount) a magnetic tape or hard disk on a spindle before using it.

In Unix-like systems, the mount point is the location in the operating system's directory structure where a mounted file system appears. For example, many modern Linux distributions automatically mount the CD drive as /media/cdrom, so the contents of the CD drive will appear in the /media/cdrom directory.

Normally only the root user can mount a new file system usually using the mount utility, but there are often provisions to allow normal users to mount removable media, such as the pmount package.

Reference:
[http://en.wikipedia.org/wiki/Mount_%28computing%29](http://en.wikipedia.org/wiki/Mount_%28computing%29)

---

