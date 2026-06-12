---
title: "USB pen drive"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by cjv8888 on 2009-03-27
I have a USB pen drive which Ubuntu could not see initially.  Then I worked out that it is unformatted and Gparted see it as unallocated space.  Now I found that other USB pen drives are always formatted as FAT16.
Why is this so and is there any reason that they cannot be formatted as ext3 or NTFS?   Should I follow suit and format this one as FAT16 too?

Thanks in advance.

---

### Post by emnii on 2009-03-27
You can format it for whatever filesystem you like, however, if you're going to be using it in Windows machines, you should stick with a Windows filesystem such as FAT32 or NTFS. Windows machines by default won't read ext3 or other standard Linux filesystems.

---

### Post by mb_webguy on 2009-03-27
FAT32 is used partially because the most commonly recognized filesystem, and partially because it has less overhead than ntfs.  Pretty much every operating system can read and write to it.  And it needs less disk space for the filesystem information, so it will give you slightly more usable storage space which is especially important on low-capacity USB pen drives.

---

