---
title: "Secure-delete"
date: 2009-11-14
forum: New to Ubuntu
---

### Post by lizandeen on 2009-11-14
I know this is similar to my last post but here goes! I downloaded Secure-Delete from my repos but now have no idea how to work it or make a launcher. I know I probably should have read up more beforehand but any help/ideas?

---

### Post by Paqman on 2009-11-15
It's a command line utility. [Secure Delete Howto]("http://www.techthrob.com/2009/03/02/howto-delete-files-permanently-and-securely-in-linux/").

Quick example:
```
shred -u -n3 /path/to/files/*
```

This would securely wipe then delete all the files in the folder located in the folder "files". More than about 2 or 3 passes of scrubbing are pointless. The default is 25, which just wastes time and increases wear on the drive.

---

### Post by lizandeen on 2009-11-16
Thanks! That link is very useful

---

