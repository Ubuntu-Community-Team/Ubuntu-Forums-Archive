---
title: "dd HDD and lost &quot;Desktop&quot; folder."
date: 2011-06-10
forum: New to Ubuntu
---

### Post by mn_voyageur on 2011-06-10
I began receiving drive warnings on my laptop.  So, I "clonezilla-ed" the drive and restored the image on another drive.  Installed the drive and booted without any problems.

However ....

I no longer have a "Desktop" folder.  I have shortcuts and files on my desktop, but they are listed under my home folder: "mark."  (instead of /mark/Desktop)


I created a new "Desktop" folder: /mark/Desktop.  And a folder labeled "Desktop" is now ON my desktop!

Any help would be appreciated.

MarkN

---

### Post by Quintilian on 2011-06-10
hit alt-f2 to open up a "Run Application" window and type in:
gconf-editor
In gconf-editor, browse to /apps/nautilus/preferences and uncheck the box "desktop_is_home_dir" (if it's not checked, try checking it and unchecking it. 
did that help?

---

### Post by mn_voyageur on 2011-06-10
Nope.  Checked and Unchecked with reboots inbetween.

Still the same.

---

### Post by oldfred on 2011-06-11
What is in this setting file
Mount with settings in ~/.config/user-dirs.dirs:
[http://ubuntuforums.org/showthread.php?p=10430718#post10430718](http://ubuntuforums.org/showthread.php?p=10430718#post10430718)

part of mine:
```
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Downloads"

```

---

