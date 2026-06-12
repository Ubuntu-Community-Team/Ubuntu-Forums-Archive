---
title: "Ubuntu can't access shared files on Windows computer"
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by masterofthemelee on 2008-04-27
When I tell my Ubuntu 8.04 laptop to share a folder, my Vista SP1 desktop (named "computer") can access and open the files just fine.

But when I tell my desktop to share a folder, Ubuntu won't see it.  I go to Places->Network->computer and it says that no folders on computer are being shared, even though they are.

SO, I decided to try typing in smb://computer/games/ into the location field, and it still gives me nothing.  The content of the games folder does not display.  So I type in smb://computer/games/snes/ and all of my snes roms appear.

Now, this is terribly inconvenient.  My 20 GB laptop can't be expected to hold all of my music, movies, and games.  On top of that, even though I can still access the snes roms, when I open zsnes I don't see a way to list "smb://computer/games/snes/" as the rom directory, which I'm guessing will also be a problem when I begin trying to play music from my windows box on the laptop.

Help?

---

### Post by superprash2003 on 2008-04-27
it could be a PERMISSIONS problem. right click on the games folder and click on properties and go to permissions and check and make sure they are set alright

---

### Post by masterofthemelee on 2008-04-27
Its set so that everyone can read it.

---

### Post by masterofthemelee on 2008-04-28
Okay, now it *will* display the contents of the games folder when I type in smb://computer/games/, but it still won't display any of the shared folders when I type in smb://computer/

---

### Post by Dabbill on 2008-04-28
I have found that it doesnt work with vista to browse folders, but for an XP computer it does work. Seems to be some thing broke in samba for hardy. 

Dont mean to hi-jack the thread but any one know how to make hardy not auto mount network folders to my desktop when i try to view them?

---

### Post by superprash2003 on 2008-04-28
you might want to install and setup samba again according to this guide [http://ubuntuguide.org](http://ubuntuguide.org)

---

### Post by S.O.P on 2008-04-28
Or check this thread - [http://ubuntuforums.org/showthread.php?p=4821333](http://ubuntuforums.org/showthread.php?p=4821333)

Konqueror can still browse Samba shares.  Nautilus can't.

---

