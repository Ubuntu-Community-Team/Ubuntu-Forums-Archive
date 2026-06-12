---
title: "Trash Full?"
date: 2010-12-18
forum: New to Ubuntu
---

### Post by JP121 on 2010-12-18
Hi,

I was trying to delete a file this morning when a warning came up saying my Trash was full.  If I go there using Dolphin, there is nothing in TRash.  I also don't see anything if I go to ~/.local/share/Trash/info or ~/.local/share/Trash/files.  Any advice?

Thanks.

---

### Post by ajgreeny on 2010-12-18
Could this be the root trash?

Have a look for all the trash folders on your system with ```
locate -i trash
``` and you may find that there is a /root/.local/share/Trash with used space.

---

### Post by JP121 on 2010-12-21
> **ajgreeny said:**
> Could this be the root trash?

Have a look for all the trash folders on your system with ```
locate -i trash
``` and you may find that there is a /root/.local/share/Trash with used space.

Thanks.  I found the root's trash, but no files were listed in it.  I set KDE up to delete the files in Trash as it gets full from the GUI, hope that works.

---

### Post by sffvba[e0rt on 2010-12-21
Maybe not enough space in your partition(s)?

---

