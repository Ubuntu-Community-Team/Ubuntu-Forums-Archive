---
title: "help editing a launcher"
date: 2010-04-09
forum: New to Ubuntu
---

### Post by nikonvt on 2010-04-09
**EDIT:    **

alright - another hickup...

I'm good until I hit the svn up command - kicks back - **skipped: "."**

thoughts?

I'm trying to get my garmin workin and getting frustrated

[http://qlandkarte.org/index.php?opti...d=15&Itemid=17]("http://qlandkarte.org/index.php?option=com_content&view=article&id=15&Itemid=17")

"To build (out of source build, start one level above source root directory): mkdir build_GarminDev cd build_GarminDev ccmake ../GarminDevCCmake can be controlled by keys. Watch out for key hints at the bottom. Especially the"c" and"g" key. You might want to check for the value of CMAKE_INSTALL_PREFIX. The default is usually "/usr/local". If you changed it for QLandkarte GT you have to change it for GarminDev, too. 
Next you do:
 
     make The binary will be placed in ./qlandkartegt. To catch up latest changes (in the source root directory):
     svn upTo send a patch  (in the source root directory):
    svn diff > patchname.diff As user you might want to do a
         sudo make install to copy all stuff into your system."

---

### Post by themusicalduck on 2010-04-09
Instead of using vi, try using gedit.

```
sudo gedit /usr/local/share/applications/qlandkartegt.desktop

```
Then you can edit and save it using the normal text editor.

Or if it must be done in a terminal, use nano instead.

```
sudo nano /usr/local/share/applications/qlandkartegt.desktop

```
It tells you the commands at the bottom of the screen. Ctrl + O  I think is to save in nano.

---

### Post by nikonvt on 2010-04-09
that worked - thanks

---

### Post by nikonvt on 2010-04-10
alright - another hickup...

I'm good until I hit the svn up command - kicks back - **skipped: "."**

thoughts?

I'm trying to get my garmin workin and getting frustrated

[http://qlandkarte.org/index.php?option=com_content&view=article&id=15&Itemid=17](http://qlandkarte.org/index.php?option=com_content&view=article&id=15&Itemid=17)

"To build (out of source build, start one level above source root directory):    mkdir build_GarminDev    cd  build_GarminDev    ccmake ../GarminDevCCmake can be controlled by keys. Watch out for key hints at the bottom. Especially the"c" and"g" key. You might want to check for the value of CMAKE_INSTALL_PREFIX. The default is usually "/usr/local". If you changed it for QLandkarte GT you have to change it for GarminDev, too. 
Next you do:
 
     make The binary will be placed in ./qlandkartegt. To catch up latest changes (in the source root directory):
     svn upTo send a patch  (in the source root directory):
    svn diff > patchname.diff As user you might want to do a
         sudo make install to copy all stuff into your system."

---

### Post by nikonvt on 2010-04-10
new problem bump

---

