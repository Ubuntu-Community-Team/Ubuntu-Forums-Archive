---
title: "External Hard Drive Question"
date: 2009-11-29
forum: New to Ubuntu
---

### Post by rcar1z on 2009-11-29
Total newbie question:  Can I purchase a removable external hard drive that is compatible with Ubuntu 8.04 without being reformatted?

---

### Post by SuperSonic4 on 2009-11-29
Short answer: Yes

long answer: Yes because ubuntu sees ntfs and vfat which is what most externals come in as since windows reads these. You might have to format it yourself but that's easy enough with gparted

---

### Post by u.b.u.n.t.u on 2009-11-29
External HDDs vary with how they are presented. It is probable that the file system would be NTFS, which is the current Windows standard and can be read and written to by Ubuntu.

Conversely Ubuntu uses ext4 as the file system and Windows cannot read or write to it by default.

So basically whatever external HDD you get, accessing such from Windows or Ubuntu should be a non issue as it would be using NTFS.

---

