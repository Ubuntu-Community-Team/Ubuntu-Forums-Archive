---
title: "How do I change the default folder that Nautilus Opens"
date: 2009-09-11
forum: New to Ubuntu
---

### Post by kendoori on 2009-09-11
I have my personal data mounted on a separate partition, bookmarked this as "Documents." The default nautilus behavior is to open the user's home directory. I would like it to open /media/sda1 instead. I realize I could create a launcher that does this, but am curious as to whether there is an underlying preference file in nautilus where I can do this tweak.

---

### Post by LewRockwell on 2009-09-11
[http://opensuse-tutorials.com/2008/07/nautilus-tips-and-tricks/](http://opensuse-tutorials.com/2008/07/nautilus-tips-and-tricks/)

.

---

### Post by LoScrondo on 2013-01-07
In order to have Nautilus/Files open on a particular folder,   just open the menu editor Alacarte  and change the command associated with Files:

```
 nautilus %U 
```to the following command:

```
 nautilus /path/to/a/directory 
```(tested on Ubuntu GnomeShell Remix 12.04 AMD64 )

---

