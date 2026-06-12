---
title: "gutsy problem with samba server"
date: 2007-11-14
forum: Networking &amp; Wireless
---

### Post by gkapog on 2007-11-14
I have intstalled kubuntu 7.10 but unfortunatelly samba is not working when I share my drives mounted on /media directory. I can login to samba server can access my home directory, can see the shared folders but when I try to access my /media mounted forders I get an error "tree connect failed: NT_STATUS_BAD_NETWORK_NAME". The file smb.conf is the same as the one in version 6.10. I solved the problem making a symbolic link in my home directory of the disks (ln -s /media/sdxx name).
Any solution to the problem???

---

### Post by Rob_Frohne on 2007-11-27
Try using the IP address (the number of the server).  It works for me when I do that, but when I use the DNS name it doesn't.

Rob

---

