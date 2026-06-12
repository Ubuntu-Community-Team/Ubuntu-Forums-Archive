---
title: "Feisty, OpenOffice.org and mounting home with cifs"
date: 2007-05-17
forum: Networking &amp; Wireless
---

### Post by lemfab on 2007-05-17
Hello,

I use Windows 2003 server with XP and Ubuntu box.
The home of the users are on the 2003 server.
I use pam_mount for mounting homes on Ubuntu.
the code is :
volume * cifs daphne &$ /home/& uid=&,gid='Utilisa. du domaine',umask=027,file_mode=0540,dir_mode=0750,iocharset=utf8  - -

This work with Ubuntu 6.10 (just a problem with gedit which don't modify any file..., just to create them)

But with Ubuntu 7.04, OpenOffice don't start, (a window with message "internal error"...)
Gimp work fine (create and modify a file)

Anyone else having the same problem or solution ?

Thank's 

Sorry for my bad english ...

---

### Post by ubnutu on 2007-06-25
I have exactly the same problem.  Any progress or fix for this?

Thanks.

---

### Post by ubnutu on 2007-06-25
Figured this one out.  CIFS does not allow symbolic links.  Not user about the Windows 2003 Unix file extensions, I don't control that server.  So get a working ~/.openoffice.org2 config directory from a file system that supports symlinks, make a copy and put that in the users CIFS home directory (cp will make file copies instead of symlinks).  The symlinks to files appear in .openoffice.org2/user/config.

After that is in place, it starts right up.

---

