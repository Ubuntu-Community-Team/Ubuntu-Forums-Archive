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

### Post by benson444 on 2008-12-09
To delete files and folders you need write permission on the parent folder. Try

```
chmod -R 755 /path/to/parent/folder
```

to make sure you have write permission to all the folders. You should be able to delete everything then.

---

### Post by northern lights on 2008-12-09
While it appears you should theoretically  be able to delete the files with user mark, root always can, so maybe running ```
gksu nautilus
```and deleting from there is the quickest solution.

---

### Post by jenkinbr on 2008-12-09
There should be no reason to use nautilus in root to delete a users own files.  Use it as a last resort.

+1 to benson444's suggestion.

---

### Post by Mark_in_Hollywood on 2008-12-09
using 

gksudo nautilus

did solve the problem.

---

