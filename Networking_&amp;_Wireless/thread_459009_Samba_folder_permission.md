---
title: "Samba folder permission"
date: 2007-05-30
forum: Networking &amp; Wireless
---

### Post by riccardodivirgilio on 2007-05-30
hi. i have set up a samba server.

i would like to create several folder that can be created and deleted only by the root
this is simple. ;)
inside this folders i would like another user to read and write.

so there is a first level of folder that can be created and deleted only by the root, this first level is in read only mode for a normal user.
Inside this folder either root and users can read and write.

how can i done this?
thanks! :p

---

### Post by apunc1 on 2007-05-30
I think you need to use the mkdir (make directory) command with -m to control the permissions as seen in this link
[http://www.bellevuelinux.org/mkdir.html](http://www.bellevuelinux.org/mkdir.html)

---

### Post by doogy2004 on 2007-05-30
Set the share as read write, set the individual folder permissions of the subfolders within the share

---

