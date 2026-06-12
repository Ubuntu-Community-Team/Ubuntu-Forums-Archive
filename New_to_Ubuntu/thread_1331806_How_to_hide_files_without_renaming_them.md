---
title: "How to hide files without renaming them"
date: 2009-11-19
forum: New to Ubuntu
---

### Post by RealG187 on 2009-11-19
I need to hide a folder without renaming it as that will mess up the path used to access it.

I heard there is a way. You make a file and list the files to be hidden in it, but I can't remember what the file is called.

---

### Post by falconindy on 2009-11-19
You can add the name of the folder/file to a .hidden in that folder. It will only work in Nautilus and Konqueror though. It will still be visible from a terminal.

---

### Post by sisco311 on 2009-11-19
> **RealG187 said:**
> I need to hide a folder without renaming it as that will mess up the path used to access it.

I heard there is a way. You make a file and list the files to be hidden in it, but I can't remember what the file is called.

The name of the file is: .hidden  :)

i.e.
/home/username/.hidden:
```
pr0n
Music 

```
will hide the pr0n and Music directories (or files) in your home dir. :)

EDIT: d'oh!, too late. falconindy beat me on this.

---

