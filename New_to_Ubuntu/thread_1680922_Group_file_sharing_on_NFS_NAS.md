---
title: "Group file sharing on NFS NAS"
date: 2011-02-03
forum: New to Ubuntu
---

### Post by thgthg on 2011-02-03
Aloa!
I have recently installed a ReadyNAS Duo using NFS protocol, and mounted to a local folder, /NAS.
 
/NAS shall be used by several users/groups with R & W permissions for all. With "CHMOD -R" I can change R&W permissions on all existing files, but as soon as ad some new files I have to run the CMOD command again to set correct permissions.

Is there a way to _**permanent**_ set, or inherit folder permissions, for all files and subfolders.

Grateful for your help

---

### Post by thgthg on 2011-02-03
Anyone???

---

### Post by wormyblackburny on 2011-02-03
*man setfacl*
                                            setfacl -d -m g:riskyusers:r mypreciousdir                                 
Set *read only* perms  to any new file created in *mypreciousdir* by a member of the *riskyusers* group.

You will obviously need to tweak it a little bit for however you want it set up. Hit up the man pages for it and you should be able to figure it out...

---

### Post by Zill on 2011-02-03
thgthg:  Default permissions in Ubuntu are 644 (rw-r--r--) for files and 755 (rwxr-xr-x) for directories.  If you wish to change the default permissions to 664 (rw-rw-r--) for files and 775 (rwxrwxr-x) for directories then one way is to change the default umask from 022 to 002.

The /etc/profile script is where the umask command is usually set for *all* users.  Simply edit this file (using sudo) with your favourite editor, change umask from 022 to 002 and Logout then Login again for the new default permissions to take effect.

Note:  If you only want to change umask for a *single* user then you can just add "umask 002" to the appropriate ~/.bashrc file.

---

