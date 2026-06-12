---
title: "Ubuntu 10.10 64 bit and Win 7 64 bit on same partition question"
date: 2011-01-21
forum: New to Ubuntu
---

### Post by watcher6342 on 2011-01-21
I put ubuntu 10.10 64 bit and win7 64 bit on same partition, my question is, how or can i get access to all my files in win7 and transfer them to ubuntu ? also, since im using firefox in both, is there a way for me to transfer all my bookmarks to the ubuntu side without having to go back and do it manually?

---

### Post by cascade9 on 2011-01-21
You cant run ubuntu 10.10 and Win7 on the same partition. Ubuntu will use linux partitions (ext2/3/4, xfs, reiser FS, etc) and win7 will use NTFS.

---

### Post by Amente on 2011-01-21
cascade is write how did you manage to do that first of all?

---

### Post by Linyx on 2011-01-21
I think he is talking about WUBI....isn't? but he didn't mentioned about that...Also, its impossible to have both on same partition, because of different partition formates

---

### Post by Amente on 2011-01-21
I see, If the case is what Linyx mentioned(wubi,ubuntu installed inside windows),then He can find the windows partition on the ubuntu file system  /host there the whole windows partition is mounted.

---

