---
title: "Updating wicd by slash &amp; burn"
date: 2008-10-14
forum: Networking &amp; Wireless
---

### Post by mringer on 2008-10-14
I tried to update wicd to 1.5.3, failed, read other people's posts, and
tried the following. It  worked for me (on X-Ub 8.04), I hope it will work for you. Sorry, but I cannot give help if not. 

1. Download the package file. Also download the old version, so that
you can revert if things go wrong.

2. Stop wicd programs by
   ps -ax | grep wicd
and kill all the processes found.

3. sudo dpkg --purge wicd

4. cd /
   find . -name '*wicd*' -print
(note the quotes). This gives a long list of files that did not get
deleted by the purge. Delete all of these except the downloaded 
packages.

5. Install by
   cd wherever
   sudo dpkg -i wicd_1.5.3_all.deb
This gave errors about 1 or more missing directories. (I forget the
details). Create these and re-install. 

6. Shutdown, reboot, login. If all is well, the wicd icon will appear
on the desktop. Click it to open the manager; click the entry for  
your router; click advanced; enter the encryption method and the key.
Try to connect.

---

### Post by jimv on 2008-10-14
I remember getting an error about /opt/wicd/encryption missing, but I think that's an old folder from 1.4.  I checked the 1.5 package and it's not putting anything in that folder, and it seems to work just fine without it.

---

