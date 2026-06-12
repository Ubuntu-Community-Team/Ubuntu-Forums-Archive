---
title: "[SOLVED] sudo Deleting files in the GUI"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by beastrace91 on 2008-12-31
So often times I really want to do remove some unneeded files, how ever most often times these files are in a folder such as /usr/ or some where else I need root privileges to remove them. Is there any way I can get root in my folder viewer to remove such files? I have been using terminal but that gets tedious after a while.

~Jeff

---

### Post by jimmy the saint on 2008-12-31
```
gksudo nautilus
```
will open a file browser session with sudo powers.  Be very careful because you can do a lot of damage if you are not careful!

---

### Post by bumanie on 2008-12-31
If you put the code > gksudo nautilus in terminal you will be given root access in GUI mode. Go to Places --> Computer--> Filesystem. Double click filesystem and you will be able to navigate where you want in GUI mode. Be careful, it is root in GUI mode and anything deleted will be almost impossible to retrieve if you delete the wrong thing.

---

