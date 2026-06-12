---
title: "Reading/Writing files on a Mac from Ubuntu"
date: 2018-09-09
forum: Networking &amp; Wireless
---

### Post by rjgilbreath on 2018-09-09
I'm a new Ubuntu user running 16.04 LTS.  I would like to be able to access and edit files on my Mac which is running 10.12.6 Sierra.  The laptop with Ubuntu was previously running Windows 10 and I had set up file sharing between Windows 10 and the Mac that was working great.  After deciding to scrap Windows for good I installed Ubuntu on the same computer.  Under Files I can see and access the Mac documents but only after logging in as "anonymous".  When I try to log in as a registered user it doesn't accept my username or password (at least one, could be both, not quite sure).  I've confirmed I am using the correct credentials.  After logging in as anonymous I cannot edit any of the files as they all open as read-only.  Now, the dialogue box says they are locked for editing by "unknown user".  None of them are open on the Mac, I've restarted the system to rid it of any leftover lock files and no other computers are connected to the network.  

So that's where I am.  Would anyone have any advice on how to move forward with being able to edit the files?

Thank you in advance,

Robert

---

### Post by TheFu on 2018-09-10
Are you using NFS or CIFS?

If you use NFS, the uid/gid, which are numbers, need to match.  On both systems, run the **id** command to see those.
NFS is the native way for Unix systems to share storage over a LAN. Generally, it is a little faster and the best part is that full, native, posix, file and directory permissions are supported, unlike with CIFS/Samba.

Last time I touched a Mac, I found the hardest part of everything was discovering whatever name Apple decided to call stuff with universally accepted names, like NFS or CIFS.  Also, at the time, their CIFS implementation was broke.

If I were doing this, I'd setup the Mac as an NFS-server since it has the disk(s) you want to access.  Also, I think on the Mac, uids begin at 500 but on Ubuntu they start at 1000. That will be the largest barrier, probably.  For the same user, those need to match.
I googled for "osx nfs-server how-to" which returned a number of guides, but since I'm not an apple-guy, I can't tell which is reputable or not. 

If you want to use CIFS, someone else will need to help. Sorry.  CIFS is what Windows normally uses. CIFS on Apple was a mystery to me.

---

### Post by Morbius1 on 2018-09-10
I'm going to assume you shared the folders on macOS using SMB since that is the default these days.

There is a bug associated with the version of the samba client ( which Nautilus uses ) on 16.04 : [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1579540](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1579540)

You could use cifs instead of smbclient - it may take some trial and error before you get it right. 

The next time you access the macOS share post the output of the following command:
```
ls -l /run/user/$UID/gvfs
```
Then we can see if we can convert that to a cifs mount which doesn't have this bug.

I should note that this bug doesn't exist in 18.04.

---

