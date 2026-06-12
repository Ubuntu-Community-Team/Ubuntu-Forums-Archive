---
title: "About to give up on mount"
date: 2007-12-24
forum: Networking &amp; Wireless
---

### Post by roazena on 2007-12-24
I am attempting to create a shared folder on another Ubuntu box in my household so that I can back up my laptop's home folder.

NFS does this:
```
mount.nfs: trying 192.168.2.5 prog 100003 vers 3 prot tcp port 2049
mount.nfs: trying 192.168.2.5 prog 100005 vers 3 prot udp port 32771
mount.nfs: 192.168.2.5:/home/mythtv/temp failed, reason given by server: Permission denied
```

SMB does this:
```
Password: 
7322: session setup failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed
```

Everything I search on this forum seems to indicate that the folder sharing I installed in fact requires me to manually configure three to five text files with deep knowledge of how each protocol works, JUST TO SHARE A FREAKING FOLDER temporarily.

The laptop and the desktop are wireless. SMB asks for a password without indicating which one it needs (not that it matters, the host and client login passwords do not work). 

What the hell is going on here?:mad:

---

### Post by jeffus_il on 2007-12-24
To do and occasional backup you could use ftp or sftp, using a program like filezilla, which would do the job fast and well, maybe with no setup.

To help you with the nfs problem, you should post the "server" machine's exportfs  file and the clients fstab

---

