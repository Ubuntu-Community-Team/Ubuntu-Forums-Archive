---
title: "Seamonkey"
date: 2009-12-15
forum: New to Ubuntu
---

### Post by bobanshirl on 2009-12-15
Hi,installed Seamonkey to have a looksee, and upon opening it,it told me that the version I was using was an old one 1.1 ??? and to download ver2,which I did.I ended up with Seamonkey -2.0.tar.bz2 on my desktop.After a lot of searching I actually extracted this tar,the thing was when I typed in the command in terminal and pessed enter it clicked to the next line with the little black square flashing,I sat watching for a time which made me think it had not worked,but then it resumed to the command line.I was not sure wat to do then,when I looked I had Seamonkey icon on the desktop.All I need to know now is how do I get the icon into Applications/Internet,if I can do that?Many Thanks

---

### Post by spiderbatdad on 2009-12-15
So it appears this version2 runs as an executable file from with a seamonkey directory in your home directory. In other words. ```
cd seamonkey
./seamonkey
``` launches it. You are not actually installing anything. To add an item under Internet menu. Go System>>Preferences>>Main Menu and select Internet on the left. Then Add new item. Name it seamonkey. For the command use "browse" and find seamonkey inside /home/user/seamonkey. There is also a "Readme" file inside the seamonkey directory for creating a launcher.
You can change the default icon most easily by adding it to panel, then right click on icon and choose properties. When the properties open, click on the icon itself in the upper left corner of the properties windows...browse to the icon you want. You can of course browse other icon files or add properly sized icons to the files.

---

### Post by bobanshirl on 2009-12-15
Many thanks for you info.Got it first time.

---

