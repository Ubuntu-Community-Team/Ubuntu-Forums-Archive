---
title: "How to mount Windows share without a password using cifs"
date: 2017-07-17
forum: Networking &amp; Wireless
---

### Post by databaseman77 on 2017-07-17
I want to mount a Windows share on Ubuntu 14 via fstab.  Here is an fstab entry that mostly does the trick:
   //share/folder  /mnt/dir  cifs  uid=username,credentials=/home/username/.smbcredentials,sec=ntlm  0  0
That entry mounts the share but requires a Windows password for the share.  Is it possible to mount a share without a password?
Ideally I would like to authenticate on the Windows side and allow read/write access to anyone logged into a particular computer.
For the share, Windows Explorer allows me to grant access to all users from a specific computer.  My problem is getting a fstab
entry to work without a Windows password.

---

### Post by TheFu on 2017-07-17
The type of authentication required is control by the system providing the storage to the network.  If that is Windows, then tell windows to allow guests to have access.

But I think guess access is a bad idea.

Just put in the Windows userid/password into the .smbcredentials and chmod 600 on that file.

---

### Post by Morbius1 on 2017-07-18
> I want to mount a Windows share on Ubuntu 14 via fstab.  Here is an fstab entry that mostly does the trick:
   //share/folder  /mnt/dir  cifs  uid=username,credentials=/home/username/.smbcredentials,sec=ntlm  0  0
That will mount the remote share writeable only to "username" so if you want to open this up to be writeable to evey user on the client you need to add some more options:

//share/folder  /mnt/dir  cifs  uid=username,credentials=/home/username/.smbcredentials,sec=ntlm[COLOR=#0000cd]**,dir_mode=0777,file_mode=0666**[/COLOR]  0  0

---

