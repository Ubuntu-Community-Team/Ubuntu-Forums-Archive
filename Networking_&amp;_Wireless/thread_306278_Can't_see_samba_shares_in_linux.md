---
title: "Can't see samba shares in linux"
date: 2006-11-24
forum: Networking &amp; Wireless
---

### Post by daveyiv on 2006-11-24
I have a linux fileserver and have it setup to share a few directories via samba so that I can access them from the windows machines on my lan. However, I can't see those samba shares from another linux machine for some reason, yet they work fine in windows. Does anyone have any tips as to what could be causing this?

---

### Post by CowzRule on 2006-11-24
I think you use a protocol called "nfs" for networking between linux boxes. I don't know anything about it, but that should give you a place to start.

---

### Post by diverjustjim on 2006-11-24
Hi,
    make sure that samba is turn on in all linux machine's.
Then compare your smb.conf file on your working linux fileserver against smb.conf with your other linux machines. 

/etc/samba/smb.conf

It's a starting point.

Jim

---

### Post by jamesr on 2006-11-24
Hi,

I am running Ubuntu 6.10 Edgy on this system and I have had no problem getting at Samba shared Directories on my Server. My Network is mainly comprised of Window's PCs with a couple of Linux Servers.

All I had to do was add a user, in my case, the PC name and suitable password to the servers, this created the home directory.
Added the same password, to samba passwords on the server. In other words I just set it up as another Windows PC
Then on this PC, connect using Places ==> Connect to server ==> select using smb, ==> supply password. This leaves a link to my server(tubby) on the desktop. 
Click on link which gives both directories. 

The preferred way would be to use NFS but this way, gives a common directory between my Linux PC and my Windows PCs for transfers of files.

---

