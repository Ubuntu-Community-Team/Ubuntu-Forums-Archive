---
title: "Access ubuntu from Windows Vista"
date: 2009-10-11
forum: New to Ubuntu
---

### Post by jobishia on 2009-10-11
I'd like to access my linux partition from Windows.  I downloaded the Ext2 Installable File System For Windows driver and assigned a drive letter to the partition.  But when I try to open it, Windows still says that I need to format it.  Does Ubuntu not use an ext2/ext3 system?  Is there a better way to do this?  Thanks.

---

### Post by powel212 on 2009-10-11
On my dual boot machines I keep my data on a separate NTFS partition so I can access it from Both windows and Linux.

---

### Post by falconindy on 2009-10-11
9.04 uses Ext3 by default, not Ext2. If you'd like to double check what filesystem you're using, from an Ubuntu terminal prompt you can type `blkid` and it'll show you the FS type for each mounted partition.

---

### Post by sandyd on 2009-10-11
> **jobishia said:**
> I'd like to access my linux partition from Windows.  I downloaded the Ext2 Installable File System For Windows driver and assigned a drive letter to the partition.  But when I try to open it, Windows still says that I need to format it.  Does Ubuntu not use an ext2/ext3 system?  Is there a better way to do this?  Thanks.
it does.

however, for some reason, it doesn't really work right in vista.
the same thing went for me.
i installed that thing and tinkered with it for a month before it worked.

---

