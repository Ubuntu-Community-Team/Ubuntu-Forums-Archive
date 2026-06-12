---
title: "Unity Menu system choice missing"
date: 2010-12-30
forum: New to Ubuntu
---

### Post by yogshog on 2010-12-30
I used to have an HP Pavillion laptop with Lynx running, but it died and I finally got a new computer. It's a netbook style (Toshiba).

I installed Ubuntu's newest version, netbook version, and it has this unity menu system. I dislike it, but could live with it, except I can't figure out how to get access to the system menus. I can *edit* the *main menu* itself, but I can't actually seem to find how to to open the menu items. Down the left hand side of my screen it has the firefox symbol, the rhythmbox symbol, software center, file manager, main menu bar (which seems to be how you edit menus), workspaces, files & folders, and applications. So, you know when instructions say to do menu>system>administration & such? I can't.

---

### Post by Aero_Zeppelin on 2010-12-30
If you're more comfortable with the gnome desktop, i suggest you go for the gnome instead of unity.It should work fine on your net book.

---

### Post by yogshog on 2010-12-30
I'm actually trying to do that, but the instructions I've found online (at [https://help.ubuntu.com/community/UbuntuNetbookEdition/UninstallUnity](https://help.ubuntu.com/community/UbuntuNetbookEdition/UninstallUnity)) 
require me to do something in menu>system>administration>logon window, which I can't get to.

---

### Post by trinitydan on 2010-12-30
You can just select "desktop session" from the pull down menu at the login window and get back to the Gnome Desktop.  ;)

---

### Post by ajgreeny on 2010-12-30
If you have your netbook set to login automatically, so you don't see a login screen, just logout, and the login screen should then appear, and you can choose **gnome desktop**, or **classic desktop** as it is called in 10.10, if I remember correctly.

The session menu does not appear until you have entered or clicked on the username, so don't panic when the login screen shows without it at first.

---

### Post by yogshog on 2010-12-30
Thanks for all your help. 


I'll still check back with Unity once in a while, but the lack of a system tab/menu choice is a confusing design choice, IMO.

---

### Post by bapoumba on 2010-12-30
You can remove items from the  unity left panel with a right click. If you want to add an item, once the application is opened, right click on its icon.

---

### Post by jamestrowbridge on 2011-05-01
I wouldn't consider this solved, it seems more "worked-around".  Switching to Gnome is just a quick fix, where is the system menu in Unity?  Also, some applications seem to be missing some menu items in their respective toolbars.  For instance, before I upgraded to 11.04 from 10.10 I was able to see an export menu item on the MySQL Workbench application, now that I have upgraded it's no where to be found (I'll have to use Gnome in order to see this for now I guess, but I'd rather learn to use Unity).  After numerous Google searches, I keep getting this thread, so I figured this is a good place to try and find out what's going on.  Thank you.

---

### Post by Peter09 on 2011-05-01
System settings are in the drop down menu when you click the power button. Stick with Unity, once you understand how to use it, its good.

---

### Post by Peter09 on 2011-05-01
For missing menus, check by hovering over the top panel when you have the application window in focus, you should see its menus there, if not its a bug.

---

### Post by jamestrowbridge on 2011-05-01
Thank you.  Unity seems cool, and I've agreed with most of the other decisions that Canonical has made for Ubuntu, that's why I want to stick with it.  The application menu bar shows up, but it's missing stuff.. should I open a bug report each time I find an issue with Unity that I didn't have with Gnome?  In addition to the missing menu items, I run Notepad++ in WINE - it runs okay for the most part, but in Unity, if maximized, it doesn't render the window properly: let's say I click to put the cursor on line 3 it will go to line 6 instead, like it's adding 20 pixels to what I've actually clicked.  I have a feeling that moving the menu bar when maximized is causing the issue, but have worked around that by not maximizing that window.

Thanks again for the quick response, I wasn't expecting to hear anything tonight :)

---

### Post by jamestrowbridge on 2011-05-01
FYI, I found a better workaround for the MySQL Workbench issue.  I just boot into Gnome and learn the keyboard shortcut for the menu item I want, then use Unity to execute it.

The MySQL Workbench menu is orignally one thing when it starts up (which is what Unity shows), but then when you access a Model the menu changes to add in the export menu and a bunch of other ones, seems like Unity cannot handle a changing menu yet.

Thanks for your help though everyone.

---

### Post by odessa2 on 2011-06-19
I would say not only is it not solved but the original question was not addressed directly.  In several cases the solutions for Unity require you to access the System>Admin or System>Settings menus so either there is a way or someone is not reading the documentation.  There is a System setings in the power icon but it is not the same as the Gnome one as many application specific settings are not there, specifically flash in my case.  I think Unity is a decent framework but hardly ready for release.  Mor like an alpha or early beta testing phase.

---

