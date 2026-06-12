---
title: "[SOLVED] Samba File Shares &amp;amp; Subfolders"
date: 2008-11-08
forum: Networking &amp; Wireless
---

### Post by TDragon on 2008-11-08
I have set up samba (through the GUI control panel) to serve my Music, Videos, and Pictures directories from my home folder on my Ubuntu box by allowing specific users access and not everyone. The users can read all folders and their subfolders, and only have write access to the root of each fileshare (\\<machinename>\Music).


I know that this is most likely a permission issue because the folders reside in my home directory. What do I need to do in order to have subfolders of the fileshares inherit the permissions that samba allows, in other words read/write access for all folders not just the root.

---

### Post by TDragon on 2008-11-08
Nevermind, solved it with chmod

For Example:
*chmod 777 -R /home/<username>/Music*

---

