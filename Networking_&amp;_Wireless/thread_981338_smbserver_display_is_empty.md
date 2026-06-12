---
title: "smb://server/ display is empty"
date: 2008-11-13
forum: Networking &amp; Wireless
---

### Post by hmhef on 2008-11-13
as the title says, 
places > network > 
here i see the PCs in my network that have windows sharing enabled, when i double click on one of them, it opens and displays an empty display, like i am not sharing any folders on those pcs

but when i try to add to the address the folder name, like this:
smb://server/mysharedfiles 
it works and asks me for the username/password


i installed smbfs
and i did this:
smbpasswd -a username
and entered password when prompted (username/password of windows share)


how can i be able to browse shared folders in those pcs ?

---

### Post by hmhef on 2008-11-14
bump

---

### Post by Iowan on 2008-11-14
Looks like the (gvfs?) bug that popped up in Hardy isn't fixed yet.

---

