---
title: "Cannot find and launch Wine after install"
date: 2011-07-07
forum: New to Ubuntu
---

### Post by c-23 on 2011-07-07
New Ubuntu 11.04 user here. I have tried Googling the answer to this problem many, many times with no luck; After multiple attempts at installing Wine from the Ubuntu software center, it will never show up in the applications window, ever. I also am not familiar with either the file system or the Terminal, so I have no clue how to launch any files from there.

I only have two icons in the application list that are related to Wine: Configure Wine and Winetricks, neither of which launch any sort of application that I can use to launch / install windows programs. If these somehow are able to launch the programs, could I get some help with that? And if not, could I get help with locating the correct file and making a shortcut out of it?

Thanks for any help, in advance!

EDIT: If this is in the wrong forum section, I do apologize. Feel free to move it to the appropriate section!

---

### Post by An Sanct on 2011-07-07
WINE is a wrapper of Windows API.

So you can actually see WINE, just like you can see Windows 32 API :) -> you can't

Install or run something, that is supposed to run in Windows and Wine will 'run' (but will not be visible).


edit: If you choose "browse c:" in the wine menu, you can find IE, regedit, notepad and other small applications, that where migrated.

---

### Post by mastablasta on 2011-07-07
play on linux is the GUI interface. otherwise to launch wine 
 
either right click the file and select open with wine
 
or open terminal and type in "wine" then add a space then go to file manager click, drag and drop the file you want to launch to terminal
 
after install with wine a shortcut from the porgramme will appear.

---

### Post by beew on 2011-07-07
The programs you install with WINE should have a menu launcher just like other sofware. Say you have installed a program called x, then open the dash and search for x you will find it.

If you want the old WINE menu with all the WINE "parts" group together you can install either version of "classic menu" in Unity.
[http://www.ubuntu-corner.com/2011/06/classic-menu-in-unity-classicmenu-indicator-and-cardapio/](http://www.ubuntu-corner.com/2011/06/classic-menu-in-unity-classicmenu-indicator-and-cardapio/)

---

### Post by grahammechanical on 2011-07-07
First, I would suggest that you run the Configure Wine utility. Then look for something called Uninstall Wine Software. Yes, I know that it is crazy but when you run the Uninstall utility you will see a button marked Install. Click on that and browse to the folder/CD that contains the setup file or program file of the program that you want to install. Click on the setup exe file.

I also suggest that you do this using Ubuntu classic mode. The installation may put an icon on the desktop. That icon may still be there when you switch to Unity/Ubuntu mode. From there you can drag it to the Dash if you wish. This is what I had to do to get one of my Windows programs loading from the Dash or the desktop.

The Uninstall Wine Software utility should be called the Add/Remove programs utility. But there you are. Development progresses but some little things get missed.

Regards.

---

### Post by mikejonesey on 2011-07-07
```
wine notepad.exe
```

---

### Post by c-23 on 2011-07-07
Thanks all! I can launch Wine now. :) Lookin' good!

---

