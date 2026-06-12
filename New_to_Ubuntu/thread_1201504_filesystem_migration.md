---
title: "filesystem migration"
date: 2009-07-01
forum: New to Ubuntu
---

### Post by sazan on 2009-07-01
I think i read somewhere that it is possible to migrate ext4 to ext3, 
is it really possible to migrate ext4 to ext3 ????

---

### Post by atomizer on 2009-07-01
[This post]("http://www.ibm.com/developerworks/linux/library/l-ext4/") says it is not possible when you use the ext4 features

> If you want to use an existing ext2 or ext3 file system as an ext4 file system, you may do so. Simply mount the device as described shortly. If you use certain new features, though, such as extents, you won't be able to go back to using the file system with the ext2 or ext3 drivers.

---

### Post by tarps87 on 2009-07-01
I believe you can only migrate up versions but I may be wrong, I have never tried going down versions

---

### Post by sazan on 2009-07-01
> **atomizer said:**
> [This post]("http://www.ibm.com/developerworks/linux/library/l-ext4/") says it is not possible when you use the ext4 features


I have read similar posts and I think migrating the Filesystem from higher to lower is not possible because of the extents and other add ons, I just need a viewpoint regarding Ext4 to confirm this.

---

### Post by tarps87 on 2009-07-01
From the reading I've done it looks like the use of the extents feature of ext4 stops it being compatible with ext3. Although I have not read the link above.

Edit: reading the link it appears to tie in although I does not state what features cause it

---

