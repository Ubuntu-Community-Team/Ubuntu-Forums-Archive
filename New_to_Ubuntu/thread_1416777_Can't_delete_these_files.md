---
title: "Can't delete these files"
date: 2010-02-26
forum: New to Ubuntu
---

### Post by cap10Ibraim on 2010-02-26
The files underlined ([COLOR=Red]RED[/COLOR]) I can't delete them and they don't show up in the explorer 

[IMG]http://lh3.ggpht.com/_tcUf5ZJRmuc/S4gWHv2Q6XI/AAAAAAAAAIk/8_GQ7J9jVs0/delete%20problem.png[/IMG]

---

### Post by jocko on 2010-02-26
Try typing the *complete* filename and not just part of it.
It's "dns~", not "dns" and "1.bob~", not "1.bob"...
These are automatically saved backups files, that are created every time you edit a file in gedit, and their names differ from the original files by the "~" at the end.
They are normally hidden in nautilus, but can be seen if you show hidden files (ctrl+h).

And you definitely do NOT need to be root to delete them. They are in your home directory, and are owned by you.

---

### Post by cap10Ibraim on 2010-02-26
Thanks 
Im new to the Linux world

---

### Post by Fancycakes on 2010-02-26
You can set gedit to not create a backup for every file you create or save, but it's not good practice. Just in case something bad happens you'll want that "file~" to restore what you've lost.

If you're a stickler for all the unused file space then you might want to look into using vim instead.

---

