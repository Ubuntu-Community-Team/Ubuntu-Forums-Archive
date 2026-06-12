---
title: "How to access ubuntu files from Windows 7"
date: 2010-02-13
forum: New to Ubuntu
---

### Post by imbube on 2010-02-13
I have installed Windows 7 in my computer and Ubuntu 9.10. How can I access my ubuntu files from Windows 7? I can't get a windows program to do it.

---

### Post by samantha_ on 2010-02-13
> **imbube said:**
> I have installed Windows 7 in my computer and Ubuntu 9.10. How can I access my ubuntu files from Windows 7? I can't get a windows program to do it.

since your using 9.10, which uses the ext4 filesystem, you cant access the ubuntu files from windows 7. However, you can access the windows 7 files from ubuntu ;)

---

### Post by louieb on 2010-02-13
odds are you can't. The Windows software that use to do that has not kept up with the improvements to the ext3 file system - and can't access ext4 formatted partitions at all. 
But if you want to try.
[Ext2 IFS Win w/write support]("http://www.fs-driver.org/index.html") 
[Explore2fs ext3 viewer - read only]("http://www.chrysocome.net/explore2fs")

---

### Post by SecretCode on 2010-02-13
If you need to access files from both OSes, the best approach is to create an ntfs partition to share. (FAT32 would work as well, but has a 4GB file size limit.)

---

