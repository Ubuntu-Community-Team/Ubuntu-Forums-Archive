---
title: "Have Java programs show in Applications menu"
date: 2011-09-08
forum: New to Ubuntu
---

### Post by Aaronneyer on 2011-09-08
Is there a way to make Java programs show in the applications menu?

---

### Post by Dragonbite on 2011-09-08
Manually make a menu item? Not sure if/how it is done in Unity, but I have added a few applications (Xampp start / stop, Aptana, etc.) manually.

---

### Post by geoff13 on 2011-09-08
I think you can right click the taskbar and there should be an option for create new launcher panel... my rig is out of service so can't be sure

---

### Post by snip3r8 on 2011-09-08
> **Dragonbite said:**
> Manually make a menu item? Not sure if/how it is done in Unity, but I have added a few applications (Xampp start / stop, Aptana, etc.) manually.
How did you achieve this in unity?

---

### Post by Dragonbite on 2011-09-08
One thing that may help is are you running Unity or a Gnome 2.x (classic) session?

Gnome 2, I think there is an entry under System (Admin? Preference? not sure) called "Main Menu" or something like that.

Unity? I don't have that running on any of my systems to be able to even start to tell you how to do it.

Maybe I can give better directions when I am home and in front of my machine.

---

### Post by Aaronneyer on 2011-09-08
I'm currently running classic although I will be running Unity soon, just having problems with it(Posted about it [here](http://ubuntuforums.org/showthread.php?t=1841001)).

---

### Post by Dragonbite on 2011-09-08
System > Preferences > Main Menu

---

### Post by mcduck on 2011-09-09
...or just right-click the Applications men and select "Edit Menus" & create a launcher for your program.

For Unity I've just used the same menu editor to create launchers for my applications. (of course with Unity you need to access it through System Settings instead as there is no Applications-menu to click. ;))

---

### Post by ExileAmongYou on 2011-09-09
Note: Might be a bit advanced if you're completely new to Ubuntu, if you are, you might be better off with the Main Menu dialog as others have suggested.

I'm not sure how comfortable you are with the terminal, but if you need to add entries for custom applications, open up your ~/.local/share/applications folder. If you add a .desktop file to that folder for your application, it'll show up in the menus. Hopefully there'll be some .desktop files in there that you can use as a reference to show you what needs to be put in the .desktop file (if there's nothing in there, you'll have to check /usr/share/applications).

---

