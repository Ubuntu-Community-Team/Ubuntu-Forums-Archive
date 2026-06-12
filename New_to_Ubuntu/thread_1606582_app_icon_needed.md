---
title: "app icon needed"
date: 2010-10-26
forum: New to Ubuntu
---

### Post by dbowlin17 on 2010-10-26
I installed an app - gournal. there is no way to launch it. there is nothing in the home folder that looks like it, and I need this to take notes on my tablet

---

### Post by bioterror on 2010-10-26
> **dbowlin17 said:**
> I installed an app - gournal. there is no way to launch it. there is nothing in the home folder that looks like it, and I need this to take notes on my tablet

Did you install [http://www.adebenham.com/old-stuff/gournal/]("http://www.adebenham.com/old-stuff/gournal/")

.deb or did you take sources and compiled by yourself?
If you installed .deb, you can always say in terminal:

dpkg -L gournal

and it should print you what files it did install.
Usually you should find the executable binary file from the /usr/bin/

If you compiled and you made "sudo make install clean", then it should be located /usr/local/bin.

---

### Post by ironic.demise on 2010-10-26
> **bioterror said:**
> Did you install [http://www.adebenham.com/old-stuff/gournal/]("http://www.adebenham.com/old-stuff/gournal/")

.deb or did you take sources and compiled by yourself?
If you installed .deb, you can always say in terminal:

dpkg -L gournal

and it should print you what files it did install.
Usually you should find the executable binary file from the /usr/bin/

If you compiled and you made "sudo make install clean", then it should be located /usr/local/bin.

Try opening a terminal and just typing "gournal" or right click your "applications" menu and "edit applications" see if it's listed under a hidden section.

---

### Post by ArgusVision on 2010-10-26
If you want to create an "icon" on your desktop. It goes like this...
First, Check your "Applications" menu and see if it appears there. If it does, right click the app and choose "Create desktop launcher"

If it's not located in the Applications menu, open a terminal and find out what command opens your app. (In this case gournal) You can usually just try the name of the app. If that doesnt work, try typing the first few letters of the name and press the <tab> button twice. (That's called tab completion.)

Once you know the command, you can right click on the desktop, select "Create Launcher...". In the window that pops up, enter a name for the "icon", the command you found earlier, and any discription you might like.
You can then click on the button in the upper left that looks like a spring, and choose an picture to use for the launcher. (I'm pretty sure it has to be in the .png or .svg formats.) Click "OK" and you're set.

Hope this helps. :) Let me know if any part is unclear.

---

### Post by dbowlin17 on 2010-10-26
Thanks! It worked perfectly!!!

---

### Post by ArgusVision on 2010-10-26
Great! Make sure you remember to mark the thread solved.
And have fun Ubuntuing! :)

---

