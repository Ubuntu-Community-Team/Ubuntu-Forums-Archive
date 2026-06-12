---
title: "Can not open Folders"
date: 2011-04-07
forum: New to Ubuntu
---

### Post by lixianlee1988 on 2011-04-07
Hello everyone 
  As we know that..there are three button on the top left corner....application, places, system, when i choose the places and wanna open any folder of it...can not work for example, i want to open home folder, normally left click places-> left click home folder...but after i do that, it only shows openning desktop on task bar(i mean the bottom bar with trash icon)~~!...but when i create a new folder on the desktop and open it, it works...so how to figure this problem `?! thanks for sharing your idear~!

---

### Post by 1991sudarshan on 2011-04-07
> **lixianlee1988 said:**
> Hello everyone 
  As we know that..there are three button on the top left corner....application, places, system, when i choose the places and wanna open any folder of it...can not work for example, i want to open home folder, normally left click places-> left click home folder...but after i do that, it only shows openning desktop on task bar(i mean the bottom bar with trash icon)~~!...but when i create a new folder on the desktop and open it, it works...so how to figure this problem `?! thanks for sharing your idear~!

Right click on the 'Home' folder in places and choose the option edit entry in that select the proper path for the home folder.

---

### Post by grahammechanical on 2011-04-07
May I suggest that you do this:

Create a new folder on the desktop. Right click it and select Open with other Application. Select File Browser and make sure that you tick the box Remember the application for "folder" files? The click Open. Not only will the new folder open but this action should associate the File browser (Nautilus) with the action to open a folder. You can then delete the new folder.

I am sure that this will work as I had to do it myself recently.

Regards.

---

### Post by irv on 2011-04-07
It sound like things got changed in your panel. If you want to get back to the default panel with everything working the way it did when you installed Ubuntu. Go to a terminal the type these two commands:
```
gconftool-2 --recursive-unset /apps/panel
rm -rf ~/.gconf/apps/panel
```

and reboot.

I had problems with my panel and I got this advice from stinkeye. See this thread: [http://ubuntuforums.org/showthread.php?t=1721964]("http://ubuntuforums.org/showthread.php?t=1721964")
By the way he had a nice script file for saving your panel and recovering your panel if things go wrong.

---

