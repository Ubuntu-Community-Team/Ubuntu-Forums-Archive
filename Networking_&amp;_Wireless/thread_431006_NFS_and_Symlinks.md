---
title: "NFS and Symlinks"
date: 2007-05-02
forum: Networking &amp; Wireless
---

### Post by jbarry on 2007-05-02
Hi All

I was following a How-To

[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

The NFS share worked great, but i have a bit of a problem. A little background on my set up

On the server side this is what it looks like

/home/uname/shared  #this is the NFS shared folder
/home/uname/Desktop/music
/home/uname/Desktop/videos

on the client i have
/home/uname/nfshare #this is the mount point for the above share

Now I want to control what files the client can see in the shared folder.

so i created symlinks on the server, for the music and videos folder into the shared folder, but in the client side the symlinks don't work. It seems that on the client side symlinks are interpreted relative to the local machine not to  the server.

I know this symlink trick works for SMB, is there a way for it to work for NFS?

Or are there "tricks" to duplicate the easyness of controlling the shared folder?

If not what do you think is my best recourse outside of using SMB.

thanks

---

### Post by dmizer on 2007-05-02
i'm not sure what exactly you're trying to do here with the system links.

if you don't want the file to be shown in the shared directory ... don't put the file in the shared directory.  i'm not trying to be condescending at all, i'm just not sure i understand the need for the added complexity of using system links.

---

