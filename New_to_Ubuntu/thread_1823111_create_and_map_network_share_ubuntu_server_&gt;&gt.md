---
title: "create and map network share ubuntu server &gt;&gt; ubuntu desktop"
date: 2011-08-11
forum: New to Ubuntu
---

### Post by iconoclast hero on 2011-08-11
I've been trying to figure out how to do this but I keep finding tutorials on how to share with windows.

Setup:
server:  lucky@192.168.1.3, Ubuntu Server 10.10. has music files I would like to share in /media/windows/media/music with most all music in folders with format "artist -- disc"
client:  ruth@192.168.1.4, Ubuntu 10.10.  want to add /media/windows/media@lucky as a network share directory in fstab i.e. /media/shares/lucky

I can't figure out if I should be using samba for this or if there is a better choice to network linux to linux, but the bottom line is I want to map the server directory to the client machine.  Help and/or a tutorial on this would be appreciated.

Thank you

---

### Post by WelshChris on 2011-08-11
NFS might be better than Samba, although others will know better!

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

---

### Post by Paqman on 2011-08-11
NFS works well, and is pretty easy to set up. Install one package on the server, add entries to /etc/exports, then add entries to /etc/fstab on the client. Job done, and a bit less flaky than SMB/CIFS (although setting up security on SMB seems a lot easier).

---

### Post by iconoclast hero on 2011-08-22
Ok, I've gotten this up and running.  I was looking at the NFS tutorial and after the quick start guide, it starts to get into various options for user and group permissions.  This quickly got over my head since I don't know what NIS or LDAP are...  For the moment since I am only exporting
```
/media/windows/media    192.168.1.0/24 (rw,fsid=0,insecure,no_subtree_check,async) 
``` to my local network with the 192.168.1.0/24 portion, if my wireless is locked down, this should be secure?  I can return to the user permissions later.

---

