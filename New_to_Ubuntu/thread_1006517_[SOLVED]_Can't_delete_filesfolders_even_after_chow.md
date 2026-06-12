---
title: "[SOLVED] Can't delete files/folders even after chown"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2008-12-09
I used an application called photorec to try to recover shift-deleted files. It wrote 179 folders to my drive.

I now want to delete those files & folders.

In a terminal I did:

sudo chown -R mark:mark /path/to/file/recup*.*

Permissions shows they are owned by user: mark and by group: mark, but cannot be deleted.

Anybody know how to help me clear this up?

---

### Post by Mark_in_Hollywood on 2008-12-09
Duhhh!!!

So I used gksudo nautilus and that did the trick. Still I don't understand what was keeping those files.

---

