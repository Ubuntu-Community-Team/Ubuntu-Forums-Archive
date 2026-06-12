---
title: "Permissions problem with Samba shared folder"
date: 2010-04-14
forum: New to Ubuntu
---

### Post by MSich on 2010-04-14
I have a folder called shared files.  It resides in my home folder.  I have it shared, via Samba and I'm using it as a shared repository with my wife's XP laptop.  When I create a file, or folder using the XP machine then it is locked when I try to access it from my Ubuntu desktop.

When I first tried to fix the problem I did this:

sudo chown -hR default /home/default/SharedFiles

to change ownership of the files, folders and sub-folders.  But new files created in the subfolders still show as locked.  How do I handle the permission issues?

More info: I created the SharedFiles folder from Ubuntu, but I created the subfolders, where the files are stored, in XP.

---

### Post by Gone fishing on 2010-04-15
That should be: 

chown -R newowner filename

is default the name of a user? and is that user you?

How about chmod to give all users access to the folder 

chmod 777 -R /thedirectory

If you want to change samba in the samba conf you need to change 

create mask = 0600
directory mask = 0700

[http://www.cyberciti.biz/tips/how-do-i-set-permissions-to-samba-shares.html](http://www.cyberciti.biz/tips/how-do-i-set-permissions-to-samba-shares.html)

---

### Post by MSich on 2010-04-17
> **Gone fishing said:**
> That should be: 

chown -R newowner filename

is default the name of a user? and is that user you?

How about chmod to give all users access to the folder 

chmod 777 -R /thedirectory

If you want to change samba in the samba conf you need to change 

create mask = 0600
directory mask = 0700

[http://www.cyberciti.biz/tips/how-do-i-set-permissions-to-samba-shares.html](http://www.cyberciti.biz/tips/how-do-i-set-permissions-to-samba-shares.html)


Sorry to take so long.  I haven't had a chance to try this until today.  The chmod777 -R did not work.  Still if I create a file in the share from the XP system it is unavailable in Ubuntu.  If I create a file in the share from Ubuntu, it is available in XP.  But, if I open it and save it, then it is unavailable in Ubuntu.  It changes the file owner to nobody.

I still need to edit the smb.conf file.  I will try to do that tonight.

default is the name of a user, the only user.

---

### Post by Scunizi on 2010-04-17
I'm following this thread too.  I have pretty much the same issue +1.  Directories created or files created by either machine are owned by the machine creating them.  I also want universal access (ie no authentication) for read/write access from anyone within my LAN.  The data is not sensitive or critical but needs to be accessed by all.

---

