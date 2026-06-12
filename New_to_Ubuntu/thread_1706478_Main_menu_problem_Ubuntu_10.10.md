---
title: "Main menu problem Ubuntu 10.10"
date: 2011-03-13
forum: New to Ubuntu
---

### Post by zlkoh on 2011-03-13
Hi all,

I am very new to Ubuntu and only been using since Saturday. Did some customisation on it by follow this guide.

[http://www.omgubuntu.co.uk/2011/03/follow-this-customization-guide-for-a-slick-ubuntu-desktop/]("http://www.omgubuntu.co.uk/2011/03/follow-this-customization-guide-for-a-slick-ubuntu-desktop/")

I have no idea if that caused the problem that I am facing now or not.

My gnome panel, the one with the main menu like Application, Places System was un-editable. I tried right clicking on it and click on edit menu, but nothing pops up. I tried alt-F2 and did a gksudo alacarte and it did pops a menu editor out but when I add my programs in, it is not shown on the menu. It seems like the only way for my programs to show on the menu is through installing them via the software centre. 

Is there anyway around, I have tried setting it back to the default via following this link [http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html]("http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html") but i still cannot edit the menu. Please help me. I need to add my programs in.

Thank you

---

### Post by andrewthomas on 2011-03-14
You should not be using gksu with alacarte.  

You can just use alacarte in the terminal or 
System > Preferences > Main Menu

---

### Post by 311005901 on 2011-03-14
I've had issues with the GNOME menu being uneditable.

You should run "alacarte" without gksu or sudo.  The gksu/sudo command runs the menu editor under the super user (aka administrator) and isn't what your looking for as a regular user (because it won't change your default GNOME menu). 

As andrewthomas noted, you can access the menu through "System>Preferences>Main Menu" or by pressing Alt+F2 and typing in "alacarte".

In my case, sometimes the menu would not reload after I closed the menu editor, so you may need to log out and log back in for the menu to update completely.

---

