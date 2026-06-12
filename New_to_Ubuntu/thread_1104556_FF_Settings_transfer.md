---
title: "FF Settings transfer"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by icyest on 2009-03-23
Um, hey where are my firefox profiles stored? Without Program Files, stuff is kind of difficult to find. 

[IMG]http://drop.io/download/49c824cb/2cd351b0c0bb07fd5b873fa2305077aaef4a2c92/3d770b70-c8d3-012b-cff3-f0ab570eca75/75d58b10-fa35-012b-3a9f-f2bd84d919f8/screenshot.png/screenshot_png.png[/IMG]
I need to transfer my firefox settings to my Windows XP virtual computer.

See those folders Ive highlighted? What are they and where is my profile?

---

### Post by aeiah on 2009-03-23
files in /usr/lib are well, user libraries :p

all personal settings for programs are in hidden folders in your home directory. hidden folders begin with a dot. i believe firefox's settings are in .mozilla

to view hidden files and folders in nautilus hit ctrl+h

---

### Post by karlr42 on 2009-03-23
Logically, all files to do with you are in your home directory. Remember Linux was designed for a multi-user environment with potentially hundreds of users. They all would have individual home directories with their own files and settings. So it makes no logical sense for configuration and setting files for your account to be in a system directory like /usr/lib. Hopefully that explains why files are organised as they are.
Anyway, the folder you want is ~/.mozilla/firefox All your history, bookmarks, saved passwords and other settings are in there.

---

### Post by icyest on 2009-03-26
Hey could you guys actually see the photos I posted? It showed up when i posted this thread, but now it doesnt display. Is there something wrong with the image display function in ubuntuforums?

---

