---
title: "Partial Access Denied with Samba"
date: 2008-08-13
forum: Networking &amp; Wireless
---

### Post by k3nt0456 on 2008-08-13
I'm using Samba server to share a folder; from the client machines I can run/copy from two of the three subfolders.

But the files from one of the subfolders are access denied (a multipart rar)



Trying to copy files out of the shared folder or opening the archive from the client result in access denied errors.

It doesn't matter what permissions I set; the other 2 folders reflect them correctly but not this one.

*for the record the files are not corrupt, I can use them fine on the server. I have also restarted Samba and the server machine to no avail.
If I browse the network to the server from the server itself I get the same behavior


thanks for reading, anyone have any suggestions? I'm new to Linux so hopefully keep the command line use to a basic level

---

### Post by cariboo on 2008-08-14
This is how I've got my shares setup in /etc/samba/smb.conf:

```
[music]
	comment = Audio Directory
	path = /home/storage/Mp3
	read only = No
	guest ok = Yes
	locking = No
```

This gives me full read/write access to the directory

Jim

---

