---
title: "Help: wine uninstall program"
date: 2009-09-07
forum: New to Ubuntu
---

### Post by aljoriz on 2009-09-07
how do you remove a program folder entry in wine?  
 
>applications>wine>programs

how do I manually delete a certain folder in the programs folder of wine?

---

### Post by Shpongle on 2009-09-07
goin into your home directory and its a hidden directory .wine (the dot in front of the files means they are hidden) press control h to see hidden files and in .wine youll see c_drive or something similar and in that youll see the usual windows stuff like program files and itll be in there what you want to delete


you should be able to uninstall from the menu too where wine is?, im on openbox and the min and dont have wine installed but theres a gui option too

---

### Post by CatKiller on 2009-09-07
If you've uninstalled the program and it hasn't taken the menu shortcut with it (many Windows applications behave this way) you can remove them from your menu in one of two ways;

The first is to right-click on the menu and select Edit Menus, find the launcher in the list and either untick it to hide it or use the button to delete it.

The other way is to delete the appropriate .desktop files from ~/.local/share/applications and entries from ~/.config/menus.

---

### Post by Bankaipirate on 2011-04-01
@Catkiller Thanks! :)

---

