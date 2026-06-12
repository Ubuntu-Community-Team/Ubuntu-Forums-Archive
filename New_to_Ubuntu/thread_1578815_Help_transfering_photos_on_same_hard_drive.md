---
title: "Help transfering photos on same hard drive"
date: 2010-09-21
forum: New to Ubuntu
---

### Post by sammyjo on 2010-09-21
Ok so I am new to this software and what I am trying to do is transfer my photos from windows 7 to ubuntu. Now I did the install via the windows installer online where is doent make you do a partition, so I am just trying to find my photos from windows to bring them over here. Any help on this matter would greatly be appreciated! Thank you

---

### Post by Rasa1111 on 2010-09-21
If you click on "Places" menu, 
Do you see the file system/hard drive in there? 

most likely below "computer" and "floppy drive" (if you have one).
I think it should say "60GB file system" 
(or however much your hard drive is).

 Sorry if Im wrong, havent used a wubi install in awhile. 
but that's how it is on my dual boot, 10.04 and 10.10.

---

### Post by NightwishFan on 2010-09-21
Welcome to Ubuntu! If you installed using the Wubi (Windows Ubuntu Installer) then all Windows files are found under /host. Go to Places -> Computer. Then open "Filesystem" and look for a folder called **host**.

This should be the Windows you installed Ubuntu under. Be careful not to delete any system files while under Ubuntu!

---

### Post by Rasa1111 on 2010-09-21
> **NightwishFan said:**
> Welcome to Ubuntu! If you installed using the Wubi (Windows Ubuntu Installer) then all Windows files are found under /host. Go to Places -> Computer. Then open "Filesystem" and look for a folder called **host**.

This should be the Windows you installed Ubuntu under. Be careful not to delete any system files while under Ubuntu!

oops, see, i was wrong. lol
my apologies. :/

---

### Post by NightwishFan on 2010-09-21
Quite alright, I know this because I manage a lot of folks with Wubi. I could be wrong in this case as well. If it is a separate drive, you are correct. :)

Another tip is if you find the folder you want in Windows, such as your user folder: Middle-click drag (hold middle mouse button in and move the folder) over your desktop and let go. A menu will appear, choose Create Link (or Link Here not sure). That way you do not have to browse through computer -> filesystem every time you want to access a Windows file. Be careful you do not COPY but just LINK.

---

### Post by sammyjo on 2010-09-22
Hey thank you guys so much for being so quick on the draw on that one!!! I totally found everything that I was looking for so again thank you so much for all that!!!

---

