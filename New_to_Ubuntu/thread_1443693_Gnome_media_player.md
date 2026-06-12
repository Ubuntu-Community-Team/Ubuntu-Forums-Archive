---
title: "Gnome media player"
date: 2010-03-31
forum: New to Ubuntu
---

### Post by Muhammad Ahmed on 2010-03-31
I installed Gnome media player and is nmot showing in any menu and works only via command,I dont want a manual entry in menu,can u tell me how to have that in menu

---

### Post by PocketDog on 2010-03-31
Right Click your Gnome menu > 

Edit Menus > 

Choose a category on the left, and click 'new item' on the right.

Give your program a title in the first box, and put the terminal command in the second box.

That's it :)

---

### Post by Muhammad Ahmed on 2010-03-31
doing it this way does not show Gnome media player in every menu like files right click menu,,,,,,,help please any command so it could be available in any menu, also i entered the command for right click menu nut doing this does not open every file with gnomne-media-player even with the association option checked

---

### Post by _h_ on 2010-03-31
Does Gnome Media Player show under Open With list via Properties at all?

---

### Post by Muhammad Ahmed on 2010-03-31
not at all

---

### Post by _h_ on 2010-03-31
Hm, maybe try reinstalling it perhaps? Or maybe restarting?

---

### Post by Muhammad Ahmed on 2010-04-01
I have tried reinstalling and completely removing and also restarting

---

### Post by Muhammad Ahmed on 2010-04-02
Solved it myself, well borrowed help from launchpad
it works as 
changing he launch command to
code:::
gnome-media-player -e gstreamer

---

