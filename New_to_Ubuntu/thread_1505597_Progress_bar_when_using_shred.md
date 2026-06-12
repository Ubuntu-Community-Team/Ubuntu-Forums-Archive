---
title: "Progress bar when using shred"
date: 2010-06-09
forum: New to Ubuntu
---

### Post by unknown user on 2010-06-09
When I select to shred a document, I am unable to see the progress bar working. I can see that it is working as it slows the system down and changes the document type/icon a couple of times before it totally disappears. However, there is no progress bar shown to show how much more time if left. Is there anyway I can get the bar to be shown?

---

### Post by cariboo on 2010-06-09
Shred is a command line program, to see progress use:

```
shred -v <filename>
```

---

### Post by unknown user on 2010-06-09
Thanks it works and I can see the progress of each 25 times. Did notice that the command was a little fussy with the naming of the file extension, but I got to the end of it.

With my Shred it is accessed via the right click menu. Are you able to have the progress show on that way too?

---

### Post by -kg- on 2010-06-09
> **unknown user said:**
> With my Shred it is accessed via the right click menu. Are you able to have the progress show on that way too?

Interesting.  I don't have "Shred" available in my right-click menu.  How did you do that?  I do have "coreutils" (which contains Shred, among others) installed.  No where in the man files or in "info coreutils 'shred invocation'" can I find any information on enabling this.

It should be noted (from "info coreutils 'shred invocation'"):

>    *Please note* that `shred' relies on a very important assumption:
that the file system overwrites data in place.  This is the traditional
way to do things, but many modern file system designs do not satisfy
this assumption.  Exceptions include:

   * Log-structured or journaled file systems, such as those supplied
     with AIX and Solaris, and JFS, ReiserFS, XFS, Ext3 (in
     `data=journal' mode), BFS, NTFS, etc. when they are configured to
     journal _data_.

   * File systems that write redundant data and carry on even if some
     writes fail, such as RAID-based file systems.

   * File systems that make snapshots, such as Network Appliance's NFS
     server.

   * File systems that cache in temporary locations, such as NFS
     version 3 clients.

   * Compressed file systems.

   In the particular case of ext3 file systems, the above disclaimer
applies (and `shred' is thus of limited effectiveness) only in
`data=journal' mode, which journals file data in addition to just
metadata. In both the `data=ordered' (default) and `data=writeback'
modes, `shred' works as usual.  Ext3 journaling modes can be changed by
adding the `data=something' option to the mount options for a
particular file system in the `/etc/fstab' file, as documented in the
mount man page (man mount).

   If you are not sure how your file system operates, then you should
assume that it does not overwrite data in place, which means that shred
cannot reliably operate on regular files in your file system.

To see the full text, issue the following command in the terminal:

```
info coreutils 'shred invocation'
```

I would make the assumption that this would apply to ext4 partitions, as well, since it is also a "journaling file system".  I would assume that a FAT32 file system would be safe...I don't know about default NTFS (i.e., whether it is set up to journal data as a default setting).

---

### Post by unknown user on 2010-07-23
Sorry about the late reply, but only just noticed your post.

Here is the link that I followed to get it in my right click menu. Hope it helps

[http://ubuntuforums.org/showthread.php?t=531703&highlight=shred](http://ubuntuforums.org/showthread.php?t=531703&highlight=shred)

---

### Post by unknown user on 2010-07-27
I have also found this on the net whilst looking, it is saying the same thing, but has a few screenshots to help:

[http://www.ubuntugeek.com/tools-to-delete-files-securely-in-ubuntu-linux.html](http://www.ubuntugeek.com/tools-to-delete-files-securely-in-ubuntu-linux.html)

---

