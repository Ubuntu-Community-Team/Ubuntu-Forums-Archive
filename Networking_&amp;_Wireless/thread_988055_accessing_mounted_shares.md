---
title: "accessing mounted shares?"
date: 2008-11-20
forum: Networking &amp; Wireless
---

### Post by shmish on 2008-11-20
Hi,
I'm able to mount a smb share with fstab, and then access it using the console.  However, I have problems when trying to use the gnome gui.  If I understand things correctly, I should be able to go to Places - Network and see my share.  What I see on Network is "Freenas", which seems to be a ftp connection to my NAS, and "Windows Network".  The ftp connection times out, and if I go to the windows network I can eventually browse to the share but it needs to be mounted again this way.  I don't see any place where I can browse to the share that is already mounted.

Example
fstab mounts this: ```
//192.168.100.148/Fileserver  /media  cifs  username=sluggo,password=8765,noexec 0 0
``` such that using the console I can go to /media/ and view the contents.

whereas if I browse I go this route: windows network -> networkname -> Freenas -> Fileserver

Any suggestions?

thanks

---

### Post by akudewan on 2008-11-20
Huh...you should be going to /media/ from Gnome, and not Network.
(Places > Computer > Filesystem > media)

Once something is mounted (whether a network share, or any other media), it can be accessed as a part of the local filesystem. 

Btw, it might be a good idea to create a subfolder under /media for your mount. Gnome automatically mounts removable media under /media, so it *might* create a problem if you don't have a subfolder.

---

### Post by superprash2003 on 2008-11-20
thats right you should have a /media/foldername not just a /media

---

### Post by shmish on 2008-11-20
Yikes, you're right.  I'm pretty new to this so when I first opened "Places" I didn't catch the filesystem folder.  When I open that I see the /media folder.

thanks

---

