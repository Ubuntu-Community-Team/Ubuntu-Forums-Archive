---
title: "Adding an item on the Application dropdown menu"
date: 2010-03-06
forum: New to Ubuntu
---

### Post by glj on 2010-03-06
I have an Ubuntu 9.04 server in a classroom with 16 LTSP thin clients. Up to this point it has been operating basically with the default apps. I have to add an ooBase database client that is used by students to access the library card catalog database server (on a remote database server in the school library). The database client uses macros in forms. I would like students to be able to click on an item on the Application dropdown menu to launch the client.

It looks like I need help in doing two things: 1. making the item appear on the Application menu for all users and 2. getting the macros to work for all users.

I searched the OpenOffice forums and the Ubuntu forums and as much documentation as I could find, but probably didn't know exactly what key words to search for because I didn't come up with anything that helped. Maybe this forum isn't even the best place to get the information I need.

Any help will be greatly appreciated.

---

### Post by RevKeltina on 2010-03-06
I have asked myself this question as well.  Though it was never a real priority for me, I will be waiting to see what the answer is!

---

### Post by glj on 2010-03-07
I finally resorted to incorporating the macros in the client documents to get the macros to work for all users.

I still haven't figured out how to add items to the Application dropdown menu (Gnome) so that they are there for all users who connect to the Ubuntu server. Can anyone help me with this?

---

### Post by 2hot6ft2 on 2010-03-07
To add to the menu. Right click on the ubuntu logo on the menu and select Edit Menus.
In the left go to the section you want the item in.
In the right select New Item.
Select if it's an app or a terminal command.
Fill in the name for it and the command to start it.
You can also click on the springboard icon to change it to something else if you want.
Click on OK then close.
All done try it out and make changes as needed by going back and selecting Properties instead of New Item after selecting it in the right pane.

---

### Post by twisted_steel on 2010-03-07
The shortcut (.desktop file) should reside in /usr/share/applications/ to show up in the menu for every user.  You can try copying one you make yourself with *2hot6ft2*'s method to that directory.  I believe any local you create using the menu editor will end up in /home/youruser/.local/share/applications/.  

Another option is to create one yourself with a text editor.  The spec is on [this freedesktop page]("http://standards.freedesktop.org/desktop-entry-spec/latest/"), but it might be easier to look at one of the existing .desktop files in /usr/share/applications.

---

### Post by glj on 2010-03-08
Thanks twisted_steel. I copied the .desktop files to the /usr/share/applications directory as you suggested. The items show up under Other on the Application dropdown menu for all users. That is a very good start. At least now the card catalog search utilities are available to everyone.

Now all I have to do is find out how to add Library to the menu for all users and have the two "catalog search" items show up as items under Library.

---

### Post by glj on 2010-03-08
I found a better way to add items to Application dropdown menus and submenus for all users on my Ubuntu server. This should be the method of choice and is described in detail at
[http://portland.freedesktop.org/xdg-utils-1.0/xdg-desktop-menu.html](http://portland.freedesktop.org/xdg-utils-1.0/xdg-desktop-menu.html).

Basically you have to create .desktop files for each item and a .directory file for the submenu that the items are under. Then as admin run the xdg-desktop-menu command to install the .desktop and .directory files. Complete instructions on how to create the necessary files and how to run the command are found at the above link.

---

