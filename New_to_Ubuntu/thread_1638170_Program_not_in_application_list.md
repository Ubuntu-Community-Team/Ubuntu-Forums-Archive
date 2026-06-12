---
title: "Program not in application list"
date: 2010-12-05
forum: New to Ubuntu
---

### Post by Saxo on 2010-12-05
I'm running linux 10.10 desktop edition. I have installed a program maple 14. There isn't a shortcut in the applications list. I have been in the root folder and there's a map with maple. But I don't know which file I have to click on to start the application or what I can do to make a shortcut for the program.

---

### Post by arjunlalb on 2010-12-05
try running the program from the terminal first, to see if it is properly installed.

or press alt+f2 and type in your program name.

---

### Post by zazlox on 2010-12-05
applications

+
right click
+
edit menu

then look for you programm

check it

then close

and you'll see it on application menu

that if your programm is GUI interface

*****************
sorry for my bad english

---

### Post by arjunlalb on 2010-12-05
alt+f2 and type ur pgm name

---

### Post by gandaran on 2010-12-05
> Shortcuts for Desktop and Applications menus

During installation, a maple14.desktop file is created in Maple's bin directory. If you request the installer to have a shortcut placed on your desktop, this file is also created in the ~/Desktop directory. If you wish to have a shortcut placed in your Applications menu, the maple14.desktop file can be copied to /usr/share/applications (which may require root access) or ~/.local/share/application
according to the instructions look for the desktop file in maple 14 bin directory.

---

### Post by Saxo on 2010-12-05
The first methods didn't work. The programs didn't show up in the lists. The last method is going to work I think. I have found the .desktop file and tried to copy it to the desktop directory. (I used sudo bash command to get into the root directory) But now I try to click on the icon and it says: "Untrusted Application Launcher The application launcher "maple14.desktop" has not been marked as trusted. If you do not know the source of this file, launching it may be unsafe."

---

### Post by Saxo on 2010-12-05
I also tried to copy the file to to /usr/share/applications and ~/.local/share/applicatio. The program is now showing up in the applications list, but this error message comes: Could not launch 'Maple 14' Failed to execute child process "/root/maple14/bin/xmaple" (Permission denied)"

---

### Post by gordintoronto on 2010-12-05
> **Saxo said:**
> I'm running linux 10.10 desktop edition. I have installed a program maple 14. There isn't a shortcut in the applications list.

How did you install it?

---

### Post by gandaran on 2010-12-06
> **Saxo said:**
> I also tried to copy the file to to /usr/share/applications and ~/.local/share/applicatio. The program is now showing up in the applications list, but this error message comes: Could not launch 'Maple 14' Failed to execute child process "/root/maple14/bin/xmaple" (Permission denied)"
how did you copy it? using sudo nautilus, sometimes using root nautilus the files are blocked, its best to use the sudo mv command (or sudo cp) in terminal to move or copy files to root directory, 
check if the desktop file in /usr/share/applications has a cross attached, if it has try changing permissions or delete it then use the terminal to copy the file, and don't copy the file to both locations, just use one.

---

