---
title: "more smbfs questions"
date: 2007-03-20
forum: Networking &amp; Wireless
---

### Post by sjxm9203 on 2007-03-20
I am also having trouble mounting my remote windows server on my system.  When I run the following command with mount I get an error.
```

sudo mount -t smbfs -o username=[removed],password=[removed] //drive/folder$ /mnt/localfolder/

9815: session setup failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed
```


Does anyone know what the 9815 errors mean?

Thank you.[SIZE="4"][/SIZE]

---

### Post by theolster on 2007-03-20
This sounds like a permissions error, what are the permissions for the shared folder on the host?

---

