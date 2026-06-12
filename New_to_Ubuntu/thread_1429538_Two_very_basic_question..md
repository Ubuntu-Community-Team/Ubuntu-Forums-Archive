---
title: "Two very basic question."
date: 2010-03-14
forum: New to Ubuntu
---

### Post by kazakore on 2010-03-14
9.10 32bit version.

When changing my Panel to be at the bottom and setting widgets I would like I found an option to group like windows/tabs. I thought this would just group them next to each other, not actually nest them, and now I can't find the option to change it. Right clicking and Properties doesn't seem to give me the menu I found anywhere.


Is it possible to change how Applications are ordered in the main Menu? on right-click there is an option called Edit Menus but it does nothing whatsoever.

---

### Post by Ryan Dwyer on 2010-03-14
I Googled it for you. You need to right click on the dotted line next to the window list, then go to Preferences.

---

### Post by kazakore on 2010-03-14
Thought I had tried that, definitely tried both sides of it, thanks.

Any idea about reorganizing the Applications list?

Should of probably put Ubuntu Studio as I'm sure of the differences (except that  kubuntu use KDE not Gnome.)

---

### Post by Ryan Dwyer on 2010-03-14
The menus can be edited through System > Preferences > Main Menu.

As far as I know the only differences in Ubuntu Studio are the packages installed by default, and the visuals such as the login screen and wallpaper.

---

### Post by kazakore on 2010-03-14
Hmmm - System > Preferences > Main Menu doesn't seem to actually do anything either. Guess something's broken somewhere...

---

### Post by pedro3005 on 2010-03-14
On a terminal, type:
```
alacarte
```
Report back if any errors are found.

---

### Post by kazakore on 2010-03-14
My .config/menu folder had become Unreadable somehow. Changed permissions with chmod and can now edit Menus.

No idea how this might of happened though!!

Also have all folders associated with a program I want to use (in fact the main program I want to use.) Can still run it from the download but not the install and unistalling it (using sh uninstall.sh) restarting and reinstalling didn't help there.


What can cause these folder permission changes?


EDIT2: Ahhh case sensitivity. That's why I couldn't get the -R to work for recursively changing permissions. Still be good to know what skewiffed everything and how.

---

