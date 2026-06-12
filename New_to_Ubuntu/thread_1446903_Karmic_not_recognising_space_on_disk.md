---
title: "Karmic not recognising space on disk"
date: 2010-04-04
forum: New to Ubuntu
---

### Post by aquascrotum on 2010-04-04
Fairly simple problem - am not sure if it has come up before.

Whenever I use a USB memory stick (all used have this problem), when I remove files to free disk space Ubuntu / nautilus isn't recognising that that the space is free, and so won't allow me to add new files to the disk.

This also happens on my parents PC which I have running Karmic.

I've got round this problem by formatting the disk in GParted or similar but its becoming a pain in the ***.

Any help welcomed.

---

### Post by NightwishFan on 2010-04-05
I am willing to bet you have deleted files on the usb disk. You can fix this by emptying trash. A manual way to delete trash on a USB disk is to view hidden files by clicking View -> Show Hidden Files or pressing CTRL+H. Look for a folder called .trash. Highlight it and use Shift+Delete to permanently delete it. You can also use Shift+Delete all the time to permanently delete files. [COLOR="DarkRed"]Use with caution.[/COLOR]

---

### Post by Paqman on 2010-04-05
If you do have items in trash, it should ask you if you want to empty them on removal. So simply unmounting and then plugging it back in would also clear the trash.

---

