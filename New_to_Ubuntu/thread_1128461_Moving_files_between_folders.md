---
title: "Moving files between folders"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by JEBB on 2009-04-17
I have some files in two folders and I want to move some files from one folder to the other.  I recognize that I can move them by opening one folder, making it  smaller than full screen then opening up the second, making it smaller and then drag and drop.  Is that the only way to accomplish that task?

---

### Post by sp0nge on 2009-04-17
always more than one way to skin a cat... you can do this via command line, but when it comes to multiple files, I've always found it easier to move them graphically. Also, I prefer using the cp command to copy the files because I have screwed up in the past by using mv to a directory that doesn't exist and my files were gone!

---

### Post by michy99 on 2009-04-17
Open both folders in separate windows. In the original folder, select the files you want to move. Hold down ctrl as you click each file to select them all. Right click and choose Cut. Switch to the destination folder. Right click and choose Paste.

If you choose Copy instead of Cut, you will still have the original files where they were and copies in the destination folder.

Also you can use ctrl-C for Copy, ctrl-X for cut, and ctrl-V for Paste.

---

### Post by Bölvaður on 2009-04-17
additional info:

you can just open a new tab instead of window.

open 1 window and then "File &#8594; New Tab" or ctrl+T if you havent assigned it to open up gnome-terminal.

then when you move files from one directory to another you just drag them into the other tab.
or you can copy them with ctrl+c, then switch tabs, ctrl+v and then switch tabs back into the first directory, select all the files you copied and delete them with shift+delete to ignor the trash and just wipe them out.


you can also do like you suggested and have 2 windows open, but have one above the other at all time by clicking the icon in the top left corner of the window and select "Always on Top".


For moving multiple files commandline could be your best way. Like I had a very messy desktop as I was doing a project and wanted to move all the screenshots I took to another computer. But I had all sort of files on the desktop with no way of quickly selecting only... oh wait... I see an easy gui way to do this now.... -.-  well what I did was type "mv *.PNG /anothercomputer/pictures" after cd to my desktop.

---

### Post by Mze on 2009-04-17
Your profile shows you are dual-booting with WinXP, what file manager do you use in Windows? 

Take a look at this article about [file managers for Linux]("http://www.linux.com/feature/113952").

There's also [PCMan]("http://pcmanfm.sourceforge.net/") file manager, also available from the repositories.

Pretty much a "Cut" and "Paste" seems to be the solution if you don't want to use 2 windows.

---

### Post by JEBB on 2009-04-17
Mze wrote:  "Your profile shows you are dual-booting with WinXP, what file manager do you use in Windows? "

For Windows I use Windows Explorer, what XP comes with; I never thought about seeking out another.  But it's really inferior when compared to Mac OSX's Finder.

---

### Post by click4851 on 2009-04-17
you could midnight commander for a semi graphical method as well

---

