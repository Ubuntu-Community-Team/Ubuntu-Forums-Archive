---
title: "Arrange Items by File Size"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by subaruwrc01 on 2009-03-07
I'm trying to clean out some diretories on my HD.  I'm using Intrepid.

When I right click then arrange items by file size, it arranges them by how many items the folder contains, not the size of the folder.  How would I arrange them by the actual size of the folder?

---

### Post by blueridgedog on 2009-03-08
Open a terminal and cd to the parent directory you are interested in and issue:

```
du --max-depth=1 | sort -g
```

---

### Post by subaruwrc01 on 2009-03-08
Works perfectly! Thanks!

---

### Post by blueridgedog on 2009-03-08
You are welcome!  I used that one a log when I managed servers and needed to find large files.

---

### Post by karlr42 on 2009-03-08
For a GUI solution, try running baobab from a terminal. It shows graphically the proportinate sizes of folders on your HD

---

### Post by blueridgedog on 2009-03-08
Good tool.  I have never ran it before.

---

