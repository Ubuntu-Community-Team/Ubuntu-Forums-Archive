---
title: "Deleting Wine Files"
date: 2010-08-18
forum: New to Ubuntu
---

### Post by Pertinax on 2010-08-18
Hi, I'm having problems deleting a couple of programs I installed under wine. One of them has an uninstaller feature, but it has a command line error when I try to run it. Can I do this through terminal? I just want to get the programs of my system and removed from the wine menu under applications.

---

### Post by Zorgoth on 2010-08-18
Well your fake Windows installation will be in the hidden folder .wine/drive_c in your home directory, so you can look around in there to delete the files and get rid of registry keys with regedit if they exist.

As for the menus, if nothing else you can use alacarte (you can run alacarte as a command or else just right click your menu and "Edit Menus...") to disable the iconse.

---

### Post by pqwoerituytrueiwoq on 2010-08-18
you can reset wine by deleting you .wine folder
i am assuming your logon name is pertinax
folder is located in 
/home/pertinax/.wine
places -> home
[ctrl]+[h]
then you can see it
deleting ti will reset wine  
you remove it via the GUI
applications->ubuntu software center
type wine
command line uninstall is
sudo apt-get remove wine

---

### Post by Zorgoth on 2010-08-18
Unless you have done things with sudo (which in wine you should not do), removing .wine (and .winetrickschache I think if you've used winetricks) will reset your wine.  Uninstalling wine is not necessary.

---

