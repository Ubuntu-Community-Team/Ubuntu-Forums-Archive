---
title: "Moving the 3 Window buttons"
date: 2010-12-08
forum: New to Ubuntu
---

### Post by Kruger2147 on 2010-12-08
Is there a way to move the main window command buttons (Maximize, minimize, close) from the upper left corner, to the upper right?

---

### Post by philinux on 2010-12-08
> **Kruger2147 said:**
> Is there a way to move the main window command buttons (Maximize, minimize, close) from the upper left corner, to the upper right?

[http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475)

Scroll down the page a bit.

---

### Post by uRock on 2010-12-08
[http://www.howtogeek.com/howto/13535/move-window-buttons-back-to-the-right-in-ubuntu-10.04/](http://www.howtogeek.com/howto/13535/move-window-buttons-back-to-the-right-in-ubuntu-10.04/)

[http://ubuntu-tutorials.com/2010/06/08/move-window-buttons-back-to-the-right-ubuntu-10-04/](http://ubuntu-tutorials.com/2010/06/08/move-window-buttons-back-to-the-right-ubuntu-10-04/)
```
gconftool -s /apps/metacity/general/button_layout -t string menu:minimize,maximize,close
```

---

### Post by tad1073 on 2010-12-08
Applications>System Tools>Configuration Editor>Apps>Metacity>General>button_layout menu:minimize,maximize,close

or hit alt+f2 then type gconf-editor

---

### Post by xtjacob on 2010-12-08
Press Alt+F2 to bring up the run application dialog, type in "gconf-editor", go to apps/metacity/general, find the one with the name "button_layout", double click on it and change the field to "menu:maximize,minimize,close".

---

### Post by burdebc on 2011-03-04
> **tad1073 said:**
> Applications>System Tools>Configuration Editor>Apps>Metacity>General>button_layout menu:minimize,maximize,close

or hit alt+f2 then type gconf-editor
You now have to run it with Alt + F2, since the Configuration Editor (gconf) is no longer displayed in Applications > System Tools.

---

### Post by migrate from windows on 2011-03-04
For me the simplest option was to install ubuntu tweak (just google and find it) it gives a direct select option for shifting the button plus a number of features , no commanda involved)

---

### Post by coffeecat on 2011-03-04
> **burdebc said:**
> You now have to run it with Alt + F2, since the Configuration Editor (gconf) is no longer displayed in Applications > System Tools.

Gconf-editor was never enabled in the System Tools menu by default. You have to edit the main menu from System > Preferences > Main Menu, or right-click on the main menu and choose 'Edit Menus'. After that you can enable the gconf-editor menu item by ticking its box.

---

### Post by DGINSD on 2011-03-04
Just a thought guys and kinda a question with it, the gconf-editor looks like a very cool tool but also looks like something I could really screw up my computer with if I didn't know what I was doing. Where can one learn to wisely use this tool effectively to change various things? seems rather intimidating to a newb

---

### Post by Kirboosy on 2011-03-04
Try [ubuntu tweak]("http://www.ubuntu-tweak.com"). It has a section where you can just drag and drop the buttons to the order you want. Also it has a few extra features that prove handy. :)

---

