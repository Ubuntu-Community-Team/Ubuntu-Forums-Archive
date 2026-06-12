---
title: "How to restore from root trash"
date: 2011-02-21
forum: New to Ubuntu
---

### Post by captain_rob on 2011-02-21
I accidentally deleted all files with the name "invest" from all directories, like python, svg, omf files and symbolic links and now I cannot install the Invest applet anymore even after reinstalling gnome-applets.
Yes I know, I was stupid. 

In the root trashbin  /root/.local/share/Trash I see all the deleted files in a folder "files" and there is also a folder "info" with files giving information about the origin of the deleted files.

If I right click on the deleted files in the "files" folder I cannot see a restore function. 

How can I restore these root trash files? Do I have to put them back manually? And how about the symbolic links?

:confused:

Thnx in advance

---

### Post by TeoBigusGeekus on 2011-02-21
```
gksu nautilus
```
and try to restore them.

---

### Post by captain_rob on 2011-02-21
Thank you for your reply. 

Its just what I wrote, there is no restore function in the right click menu of nautilus in superuser mode. :(

---

### Post by mtoloo on 2011-02-28
> **captain_rob said:**
> 

In the root trashbin  /root/.local/share/Trash I see all the deleted files in a folder "files" and there is also a folder "info" with files giving information about the origin of the deleted files.


Simply copy  your files in "files" directory to the directory it was deleted.

Are you sure the path is /root/.local/share/Trash? I found the root trash in /home/.Trash-0/ directory. And copy the files I was needed from "files" directory to where it was deleted from.

---

