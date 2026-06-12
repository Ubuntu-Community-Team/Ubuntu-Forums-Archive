---
title: "Reiserfs question"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by CM Xtasy on 2008-12-15
If my linux partition is reiserfs, and I use an external HD to transfer files that is an NTFS, can my linux partition crash my HD and make it lose all of the data?

---

### Post by Locke_99GS on 2008-12-15
No, you'll be fine copying between differing file-systems.

---

### Post by EdThaSlayer on 2008-12-15
I wouldn't recommend having the external hard drive partition as ntfs(better choose something like fat32 where the support is much better).

[http://www.linuxquestions.org/questions/linux-software-2/copying-reiserfs-to-ntfs-161569/](http://www.linuxquestions.org/questions/linux-software-2/copying-reiserfs-to-ntfs-161569/) has some extra info.

To summarize it, don't copy more than 2 gb at a time(as things will be slow).
Besides that I think it should be alright(but then again, it's the ntfs partition that is the *dangerous* one).

---

### Post by Locke_99GS on 2008-12-15
> **EdThaSlayer said:**
> [http://www.linuxquestions.org/questions/linux-software-2/copying-reiserfs-to-ntfs-161569/](http://www.linuxquestions.org/questions/linux-software-2/copying-reiserfs-to-ntfs-161569/) has some extra info.

NTSF support is *considerably* better now than it was in 2004, when the posts in that link were made.

---

