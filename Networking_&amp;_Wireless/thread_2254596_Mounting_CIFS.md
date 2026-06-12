---
title: "Mounting CIFS"
date: 2014-11-28
forum: Networking &amp; Wireless
---

### Post by Dr._B on 2014-11-28
I have had a script which mounted a shared drive on another server that worked successfully for over 2 years. Recently, it has failed and I cannot figure out why. The command I run is:

mount.cifs //<IP address/folder> /home/lab/Backups/backup1  -o user=<uid>,password=<uid>,nounix,sec=ntlmssp,noperm,rw

stuff in < > removed to preserve security.

Any ideas why this no longer works?

Thank you

Bryan

EDIT: the error I get is ```
mount error(5): Input/output error
```

---

### Post by bashiergui on 2014-11-30
According to this [https://help.ubuntu.com/community/Samba/SambaClientGuide#Connecting_using_CIFS](https://help.ubuntu.com/community/Samba/SambaClientGuide#Connecting_using_CIFS)
> after Ubuntu 12.10, smbfs has been replaced by cifs-utils.Make sure you have cifs-utils installed especially if you did any kind of upgrade recently.

---

