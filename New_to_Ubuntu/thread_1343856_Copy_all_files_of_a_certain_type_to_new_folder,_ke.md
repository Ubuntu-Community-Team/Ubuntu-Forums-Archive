---
title: "Copy all files of a certain type to new folder, keeping the old folder structure"
date: 2009-12-02
forum: New to Ubuntu
---

### Post by krolben on 2009-12-02
Hi all

I need to copy all 'jpg' and 'JPG' files from my image library (containing many sub folders) to a new folder, keeping the folder structure.

Example:
This file
/volume1/photo/2001/2001_02_02/img1.jpg
Should be copied to
/volume1/photo/jpg/2001/2001_02_02/img1.jpg

I'm pretty sure I can get cp or rsync to do this, but I can't figure out how.

---

### Post by ukripper on 2009-12-02
> **krolben said:**
> Hi all

I need to copy all 'jpg' and 'JPG' files from my image library (containing many sub folders) to a new folder, keeping the folder structure.



I'm pretty sure I can get cp or rsync to do this, but I can't figure out how.
```
cp -v /volume1/photo/2001/2001_02_02/*.jpg /volume1/photo/jpg/2001/2001_02_02/
```

---

### Post by falconindy on 2009-12-02
A slightly more robust solution that doesn't involve the perils of globbing:

```
find /volume1/photo -depth -type f -iname *.jpg -print0 | cpio --null --sparse -pvd /volume1/photo/jpg
```

---

### Post by krolben on 2009-12-03
> **falconindy said:**
> A slightly more robust solution that doesn't involve the perils of globbing:

```
find /volume1/photo -depth -type f -iname *.jpg -print0 | cpio --null --sparse -pvd /volume1/photo/jpg
```

Worked like a charm. Thanks a lot :)

---

