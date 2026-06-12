---
title: "Getting Error msg in Wine and cannot find a fix."
date: 2009-11-23
forum: New to Ubuntu
---

### Post by Rasthor on 2009-11-23
I am trying to play WOW in wine, using wine 1.1.33

I keep getting this error msg when running wow.

Failed to change to directory '/home/jason/.wine/dosdevices/c:/Program Files/World of Warcraft/' (Permission denied)

Ubuntu 9.10.

Any ideas?

---

### Post by Mrandersonjr on 2009-11-23
The problem could be that you do not have sufficient permissions.

Try opening up a terminal then running:

sudo wine


Or,you may have to go into your virtual c:\ drive under the wine menu,and change the permissions of the WoW folder.
Try running(IF ALL ELSE FAILS):
chown /home/jason/.wine/dosdevices/c:/Program Files/World of Warcraft/

IF that doesn't work then run whatever your filemanager is as root (sudo su in terminal)
and right click and change the permissions of that folder so that you have full control.
(make sure you ctrl+h in your filemanager to show hidden files so you can navigate to the folder.)

---

### Post by polpak on 2009-12-08
This problem is caused by a recent patch to WoW. It now removes the permissions from the World of Warcraft directory from the user, so you can't access it after you run the launcher.

To fix this, just reset the permissions:

chmod 750 /path/to/"World of Warcraft"

then run the game using the Wow.exe program directly rather than the launcher.

---

