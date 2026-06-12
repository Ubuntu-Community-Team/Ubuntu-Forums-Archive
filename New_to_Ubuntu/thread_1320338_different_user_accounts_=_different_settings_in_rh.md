---
title: "different user accounts = different settings in rhythmbox?"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by marquee moon on 2009-11-09
If I set up two separate login accounts, will they be able to have different preferences in rhythmbox? 

for example, my wife wants to download a podcast to her mp3 player, but I'd like to download a different podcast to my hard drive. So if we have different accounts, could we have different podcast lists and "save to..," locations? 

thanks, mm

---

### Post by nothingspecial on 2009-11-09
Yes

---

### Post by ajgreeny on 2009-11-09
Most of the application configurations are stored in hidden folders on the users /home/username folder, so as nothingspecial says, the answer is yes.

If you want to share documents and music etc etc it is quite easy to make a separate partition or folder, and with the appropriate permissions set, and mounting of the partition, if you use one, you can save on duplication of disk space.

---

### Post by donato roque on 2009-11-09
In my case, I share the computer with my sister and we share my music folder.  She gets her own configuration files but I share my music collection by setting the appropriate permissions. I guess the real issue is not hard disk space but how to keep it simple.  My suggestion is to name a folder "shared folder" or "public" then put everything you want to share in that folder.  Give it the appropriate permission.  The rest of my stuff is private.

---

### Post by Gaweph on 2009-11-09
Every account will have a folder in theri home called:

.rhythmbox

which will hold the settings, so your computer will have 2 files:

/home/userA/.rhythmbox
and
/home/userB/.rhythmbox

So it will all be sepeerate.

This is also true for any otehr application you both use, from firefox to pidgin to whatever.

Gaw

---

### Post by ajgreeny on 2009-11-09
In fact the the config folders for rhythmbox are all over your home folder in various subfolders of ~/.cache, ~/.gconf, ~/.gnome2, and ~/.local.  There is no ~/.rhythmbox, but there are several dotted/hidden folders named directly for many other applications.

---

