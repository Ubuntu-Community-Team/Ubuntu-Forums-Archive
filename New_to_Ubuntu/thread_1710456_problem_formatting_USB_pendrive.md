---
title: "problem formatting USB pendrive"
date: 2011-03-19
forum: New to Ubuntu
---

### Post by Ditchdoc7893 on 2011-03-19
This has to be a ridiculous question, but I'm trying to format my 8 GB Kingston pendrive.  I went into disk utility and attempted to format it, but it says its in use.  Its not in use other than the fact that it is inserted into the usb port.  I don't have anything open that is utilizing the drive at all.  What am I doing wrong?  Is there another way to format it?  Maybe from terminal?

---

### Post by fabricator4 on 2011-03-19
> **Ditchdoc7893 said:**
> This has to be a ridiculous question, but I'm trying to format my 8 GB Kingston pendrive.  I went into disk utility and attempted to format it, but it says its in use.  Its not in use other than the fact that it is inserted into the usb port.  I don't have anything open that is utilizing the drive at all.  What am I doing wrong?  Is there another way to format it?  Maybe from terminal?

I've had some problems with pen drives in the cases where they are formatted as W95 file system, normally with some special software on them.  Open Disk Utilities:

```

->System
   ->Administration
      ->Disk Utility

```

Make sure you select the pen drive from the list.  Select unmount to (obviously) unmount the drive from Linux.  Next delete the partition.

Now you can recreate the partition.  You may get an error that you need to create the partition table first. This seems to be a characteristic of these devices that have some special software loaded.

You can then create whatever file system partition you like.  I like to use ext2 for drives that I don't need to use with Windows (which is hardly at all)  or FAT32 if you want to use it between systems.

Once you've done this the pen drive will always work as you expect.

If you want to be able to access ext2 partitions (or ext3, ext4 etc) then just load the opensource driver Ext2 in Windows and you'll be able to do so.

Chris.

---

### Post by Ditchdoc7893 on 2011-03-19
Hey thanks!  That worked like a charm!

---

### Post by fabricator4 on 2011-03-19
> **Ditchdoc7893 said:**
> Hey thanks!  That worked like a charm!

Yeah, it's great when things work to plan.  :-)

---

