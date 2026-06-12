---
title: "Need help running Jdownloader through Opera 11"
date: 2010-12-19
forum: New to Ubuntu
---

### Post by livedlooz on 2010-12-19
I'm using Ubuntu 10.10 and Opera 11. I need help to run JDownloader from Opera custom menu.ini.

I got the tips to edit custom menu.ini from here [http://my.opera.com/Tamil/blog/edit-menu-setup](http://my.opera.com/Tamil/blog/edit-menu-setup) menu setup and for adding JDownloader(this only works for windows) into the menu [http://board.jdownloader.org/showthread.php?t=1279](http://board.jdownloader.org/showthread.php?t=1279)

Is it possible to run application through Opera in Ubuntu?

---

### Post by livedlooz on 2010-12-27
Bump?

---

### Post by furiat on 2012-04-14
Hi, I don't know if I should reply to such an archaic post, but I guess if you still need a solution then i have it:

Open Opera and go to **Opera>Settings>Preferences>Advance>Toolbars**

and in the section Menu Setup duplicate your Opera Standard settings. This is done because Opera overwrites standard settings after the upgrade. Then open the menu settings file 

**/home/$USER/.opera/menu/standard_menu_1.ini**

and then find **[Link Popup Menu]** and below it add the following line 

**Item, "Download with JDownloader" = Copy link & Execute program, "jdownloader","%c"**

If you wish to have menu item for highlited text as well find **[Hotclick Popup Menu]** and add line 

**Item, "Download with JDownloader" = Copy & Execute program, "jdownloader","%c"**

Instructions adapted from here:

[http://my.opera.com/Tamil/blog/edit-menu-setup](http://my.opera.com/Tamil/blog/edit-menu-setup)
[http://board.jdownloader.org/showpost.php?p=6284&postcount=3](http://board.jdownloader.org/showpost.php?p=6284&postcount=3)

---

### Post by Elfy on 2012-04-14
Old thread closed.

---

