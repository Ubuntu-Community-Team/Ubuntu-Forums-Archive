---
title: "Make Desktop location a symlink"
date: 2009-09-08
forum: New to Ubuntu
---

### Post by RealG187 on 2009-09-08
I have just installed Ubuntu again (I installed Windows for a game and messed up my Ubuntu partition while trying to access it from Windows, now I have an NTFS partition that both OSes can access).

I have mounted my NTFS Partition as "/media/Files" and made:

"/home/mpg/Documents" symlink to "/media/Files/Documents"
"/home/mpg/Music" symlink to "/media/Files/Music"
"/home/mpg/Pictures" symlink to "/media/Files/Pictures"
"/home/mpg/Videos" symlink to "/media/Files/Videos"
and
"/home/mpg/Desktop" symlink to "/media/Files/Desktop"

I want the contents of my desktop to reside on /media/Files/Desktop, but it's not working. On my Desktop I see an icon for a folder called "Desktop" and it's empty...

---

### Post by zvacet on 2009-09-09
```
ln -s /path/to/real/file /path/to/non-existant/file
```

---

