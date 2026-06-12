---
title: "ubutnu one and installing files"
date: 2011-04-01
forum: New to Ubuntu
---

### Post by AnnAni1234 on 2011-04-01
I have two different question

A) I am missing the Ubuntu One Icon in my internet sub-menu but apperently have it installed on my machine how do i get it there

B) i have a tar file that I want to install but am a complete noob when it comes to command line so how would i install it and does anyone know where can i learn command line from so i can fully take advantage of my ubutnu system 


thanks in advance

---

### Post by Tamlynmac on 2011-04-02
Problem A

Right click on your menu and select "Edit Menus". Select "Applications" on the left side window. On the right side window scan down and see if Ubuntu One is listed.

If so: The box next to it is probably unchecked. Check the box & close the window. The Ubuntu One icon should then appear in your menu.

If not: Left click on the "New Item" button on the top right side of the window. A Create Launcher window will open.
1. Type = Application
2. Name = Ubuntu One
3. Command = Paste this into the command window "/usr/bin/software-center". This is the location of the Ubuntu One executable. Note that it's located under the file system
* By left clicking on the icon in the create launcher window, you can select a different icon.
4. Comment = No comment is necessary

Upon completion click OK at the bottom right corner of the create launcher window and before closing the Edit Menu window, make sure there's a check mark in the box next to your new Ubuntu One launcher. This will add Ubuntu One to your menu.


Problem B

It may just be simpler (until you learn to use the terminal) to just double click on the .tar file in the file manager "places/home folder". Then simply  use the Archive Manager to extract the files and perform the install.


** As a new user, [this]("https://help.ubuntu.com/community/UsingTheTerminal") might be a good place to start regarding the terminal.

Good Luck & hope this helps

---

