---
title: "Backup USB Hard drive format"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by dndrich on 2009-11-11
Ubuntupals:

I plan to use Lucky Backup from the repositories as a simple gui for rsync. Looks really nice. I will back up to a USB external drive. How should I format the drive? NTFS, Ext4 or Ext3?

---

### Post by earthpigg on 2009-11-11
i'd probably use the same as the drive i was backing up.

---

### Post by Rayve on 2009-11-11
NTFS is used by Windows, so if you plan that this data will also need to be read/accessible to Windows, you'll need to go that route, I believe.

Between ext3 and ext4, both Linux filesystems (and possibly not readable by Windows), the last I heard, ext4 was the "newer" one and somewhat less stable than ext3.  I have ext3 on my Linux partitions myself.

Someone with more knowledge please correct me on any of this!

---

