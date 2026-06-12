---
title: "Trying to backup wirelessly to local Linux Box, but many obstacles are in my path"
date: 2007-05-11
forum: Networking &amp; Wireless
---

### Post by Falcorian on 2007-05-11
In preparation for (finally) upgrading to Feisty, I'd like to back up everything first.

I'm trying to do so to my local Ubuntu server, which currently uses samba to communicate with all the other machines in the apartment (because we've got some Window's Boxes). However, smbfs won't allow more than a 2 gig file to be moved over it, which is a really problem when I'm trying to create 20gig tar files.

I tried using cifs, but I couldn't get it running right away, is it worth looking into this more? I would, but I'm worried it will run into the same problems as bellow.

I then tried nfs. It works great, for small file transfers. For large ones it freezes my computer on and off for minutes are a time every few minutes (so that I can't use it, period). I tried setting rsize-1024 as suggested here and elsewhere for wireless, but this only makes the freezes more spread out, and after a few hours, they seem to return to their normal rate (which is ever few minutes).

My fstab looks like this currently (I've removed my cifs attempt):

```

#Oski Samba Shares
//192.168.1.2/storage2 /media/oski2 smbfs credentials=/root/.smbcredentials,uid=user 0 0
//192.168.1.2/storage1 /media/oski1 smbfs credentials=/root/.smbcredentials,uid=user 0 0

#Oski NFS Shares
#192.168.1.2:/media/storage1 /media/oski1 nfs rsize=1024,wsize=1024,timeo=14,intr 0 0 
#192.168.1.2:/media/storage2 /media/oski2 nfs rsize=1024,wsize=1024,timeo=14,intr 0 0

```

Now, I've tried to go back to smbfs, and simply split the tar files during creation, but I can't seem to do this (maybe it's not possible? Or maybe I just can't read the info page well enough ;) ). I don't have the free space to put 20gig tars on my drive, so I was creating them on the networked drive, and it seems the common method for splinting tarballs (split) needs an already created file.


Does anyone have any advice? It would certainly be appreciated.

---

### Post by motin on 2007-05-29
Check out this: [ Brief HOWTO: "Upgrade" (by reinstalling) from Dapper to Feisty]("http://ubuntuforums.org/showthread.php?t=412183")

The first part mentions some backup pointers. 

The most secure way to do this mentioned in the part "If you want to be really sure..." and involves using a disk imaging tool. Either Drive Snapshot for Windows or maybe Mondo Rescue for Linux. The first mentioned automatically zips and splits the backup and is really fast and easy to use. It saved my computer when I tried upgrading from Dapper to Edgy and got everything corrupted.

---

