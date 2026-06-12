---
title: "links in place redirect to rhythmbox"
date: 2011-01-21
forum: New to Ubuntu
---

### Post by amitpokhrel on 2011-01-21
I have had this problem before and I solved it by following these commands:

gksudo gedit /usr/share/applications/defaults.list
and changing a line as: inode/directory=nautilus-folder-handler.desktop

But now when I type cat /usr/share/applications/defaults.list | grep inode,
I get: inode/directory=nautilus-folder-handler.desktop
this as output...
I don't know what went wrong

---

### Post by Verbeck on 2011-01-21
you wouldn't need to use gksudo to edit that file...

anyway, try
right click a folder on your desktop (create one if you don't have) > open with other application > file browser
and check "remember this application for 'folder' files"

#its same thing as above, but a different way of doing it

---

### Post by amitpokhrel on 2011-01-23
thanks it worked!!

---

