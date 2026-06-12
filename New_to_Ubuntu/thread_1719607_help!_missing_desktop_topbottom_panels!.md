---
title: "help! missing desktop top/bottom panels!"
date: 2011-04-02
forum: New to Ubuntu
---

### Post by luvc2b23 on 2011-04-02
Ok, so i really do not know what i exactly did. i was supposed to log out, but while my cursor was moviing around, i got abit impatient and started clicking on the entire panel, which sorta led to to my anxiety.. both my top and bottom panels or taskbars are missing! :(((  i tried pressing alt + f2 or ctrl+ alt + f2 but nothing happened. i just cant seem to open the terminal using any shortcuts! i have absolutely no access to my applications. and its so awkward seeing no panel. someone please help ease my anxiety!

---

### Post by matt-fender on 2011-04-02
> **luvc2b23 said:**
> Ok, so i really do not know what i exactly did. i was supposed to log out, but while my cursor was moviing around, i got abit impatient and started clicking on the entire panel, which sorta led to to my anxiety.. both my top and bottom panels or taskbars are missing! :(((  i tried pressing alt + f2 or ctrl+ alt + f2 but nothing happened. i just cant seem to open the terminal using any shortcuts! i have absolutely no access to my applications. and its so awkward seeing no panel. someone please help ease my anxiety!


[http://www.troublefixers.com/restore-recover-deleted-ubuntu-top-panel/](http://www.troublefixers.com/restore-recover-deleted-ubuntu-top-panel/)

Method 2:

Panel Restore Script, save in browser, open containing folder, extract and then run :popcorn:

---

### Post by dcsoldschool53 on 2011-04-02
**Question? Can you right click on your Desktop to open a list with the word create launcher in it? If you can do this ,then click on create launcher**. **For name, type terminal and for command type gnome-terminal**. [B]Click ok to add shortcut to desktop. Then, click on it.

If by chance, you can go into any folder via desktop, goto /usr/share/applications. You will see a icon for the terminal. Click on it to bring up the terminal
[/B]

---

### Post by taylortwt on 2011-04-03
I also have both panels missing and can not recover them.    After I installed Avant Window Navigator and rebooted my system, my top panel disappeared.  I tried the recommended solution with no success:
 
gconftool-2 --shutdown 
rm -rf ~/.gconf/apps/panel 
pkill gnome-panel 

I installed Avant Window Navigator using the following method:
sudo apt-get remove avant-window-navigator avant-window-navigator-data awn-settings awn-applets-c-core libawn1 vala-awn && sudo apt-get autoremove

sudo add-apt-repository ppa:awn-testing/ppa

sudo apt-get update

sudo apt-get install avant-window-navigator-trunk avant-window-navigator-data-trunk python-awn-trunk awn-settings-trunk awn-applets-python-core-trunk python-awn-extras-trunk awn-applets-python-extras-trunk awn-applets-c-core-trunk awn-applets-c-extras-trunk

sudo apt-get install dockmanager-daemon dockmanager


I am afraid if I un-install AWN, I will have no way to access my applications.  Any suggestions????


UPDATE:
My SOLUTION -- I somehow un-installed the gnome-panel application.  "sudo apt-get install gnome-panel"

---

