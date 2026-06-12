---
title: "cp without overwrite"
date: 2009-10-10
forum: New to Ubuntu
---

### Post by KCormier on 2009-10-10
Hey guys.  I have a large filesystem that i'm searching through for all .jpg files.  Right now I'm using the command

```

find ./ -name *.jpg -exec cp {} /path/to/backup/dir/ -b \;

```

If I have 2 files with the same name, I'm safe, but if I have 3 or more with the same name they overwrite the backup.  Anything I can do to make cp backup the backup?

---

### Post by lloyd_b on 2009-10-10
```
find ./ -name *.jpg -exec cp --backup=numbered {} /path/to/backup/dir/ \;
```The "--backup=numbered" means that you'll wind up with "file.ext.~1~", "file.ext.~2~", etc, rather than having it overwrite anything.

Lloyd B.

---

