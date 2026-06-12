---
title: "Wine problems"
date: 2009-02-24
forum: New to Ubuntu
---

### Post by Drenriza on 2009-02-24
I've uninstalled wine, but it is still in the applications menu.

I've went into the protocol and used
sudo apt-get autoclean
suto apt-get autoremove, with no luck.

i've also used synaptic package handler to try and remove all the folders & subfolders. but it is still their.

Anybody who can help me?

Thanks on advance

---

### Post by simeon87 on 2009-02-24
System > Preferences > Main Menu, try removing it there.

---

### Post by Drenriza on 2009-02-24
> **simeon87 said:**
> System > Preferences > Main Menu, try removing it there.

already tryed that, doesn't work

---

### Post by Eddie Wilson on 2009-02-24
Right click on main menu. Choose edit menu,(I believe that's correct. I'm not at my Ubuntu machine.) Either uncheck or delete Wine. It should be gone now from your menu. If not, restart x.

---

### Post by Drenriza on 2009-02-24
> **Eddie Wilson said:**
> Right click on main menu. Choose edit menu,(I believe that's correct. I'm not at my Ubuntu machine.) Either uncheck or delete Wine. It should be gone now from your menu. If not, restart x.


Thanks for the suggestion but i've also tryed that, both deleting wine throw edit menu and deleting it, and then tryed to restart x

---

### Post by Eddie Wilson on 2009-02-24
Sorry but you've got me on this one. I've never had a menu entry that I couldn't get rid of. I've had some where I couldn't delete them so I would just uncheck it and it wouldn't show up. I'm sure someone else may be able to help.

---

### Post by jmszr on 2009-02-24
Drenriza,
           Try Places > Home Folder > View > click on Show Hidden Files > scroll down to .Wine > Delete (or Move to Trash). It has worked for me to delete leftover application names in Wine (after opening the Wine Folder); so it should be able to delete the whole folder.

---

### Post by achase79 on 2009-02-24
sometimes you have to search for and delete the associated *.desktop files for the wine applications.

---

### Post by Drenriza on 2009-02-25
Thanks for the great suggestions, i will try these suggestions as soon as i booting up my laptop :)

---

### Post by Drenriza on 2009-02-26
> **jmszr said:**
> Drenriza,
           Try Places > Home Folder > View > click on Show Hidden Files > scroll down to .Wine > Delete (or Move to Trash). It has worked for me to delete leftover application names in Wine (after opening the Wine Folder); so it should be able to delete the whole folder.

i have deleted wine and all subfolders in home and hidden files but still wine and uninstalled programes and folders can be seen in the applications tab................

What now :)?

---

### Post by jmszr on 2009-02-26
Drenriza,
  This is from: [https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine) 

 Open up a terminal window and type "uninstaller" - this will open up a program similar to Windows' "add/remove programs" control panel, allowing you to uninstall applications from a Wine installation.
 Worth a try, hope it works for you.

---

