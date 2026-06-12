---
title: "Where did 7zip go?"
date: 2009-06-12
forum: New to Ubuntu
---

### Post by webmiester on 2009-06-12
Hi, Im using ubuntu 8.10,

I placed a check mark on the Install/uninstall application of ubuntu for 7zip...  it's supposedly installed but I cant find it in the application menu.

When I double click on a rar or other archive, it opens archive manager.  When I click on "Open with other..." 7zip isnt there.

Where did 7zip go and how do I access it?

---

### Post by Mornedhel on 2009-06-12
If you installed p7zip, it registered 7z files as a valid archive format for file-roller. You should be able to create/unpack 7z archives from the standard Gnome archive manager.

There is no separate GUI 7zip program in the Ubuntu repositories that I know of, although I might be mistaken.

---

### Post by lamego on 2009-06-12
The package 7zip is a command line utility, it is not a full graphical archive manager like the windows version.
The package does provide the file-roller integration as Mornedhel explained.

If you reall want/need to, you can install/use the windows 7zip using wine.

---

