---
title: "Trouble Saving Downloaded AC Map"
date: 2010-08-02
forum: New to Ubuntu
---

### Post by muddpup64 on 2010-08-02
I just downloaded a map file for my Assault Cube game. And when I try to save it to my AC map file It tells me:

```
Error: Permission Denied
```I can save to my desktop and in documents but I can't save it to the AC map file.

What do I do?

---

### Post by Darkness Des on 2010-08-02
I assume that you're trying to do this in the File Browser? If so, go to the terminal and type in 
```
gksudo nautilus
```
to open up a file browser with root permission. Be sure to close it as soon as you're done and don't move anything. I've never played Assault Cube or worked with it's map system, so I'm assuming that this isn't a file and that it is a folder. If it's a file, then use 
```
gksudo gedit
```
and open the file. Again, don't edit things other than the Map file and close it as soon as you're done.

---

### Post by muddpup64 on 2010-08-02
Thanks a lot. It worked like a charm.

Thanks.:D

---

