---
title: "Samba allowing read only on to annonymous users for a folder not own by user"
date: 2008-08-25
forum: Networking &amp; Wireless
---

### Post by thejipster on 2008-08-25
I have a directory structure on my server that my friends upload his music to for offline storage.  I basically want to make this folder readable by everyone on my home network over SMB.  

The folder has file permission of 700
ls -l /storage/music

drwx------  5 user1 group1   4096 2008-08-09 19:43 music

Is there a way to make that folder real-only to authenticated users over SMB, where no one would have to know the user1's password in order to mount the drive?  I cannot change the permission of the folder structure to chmod 750 or 755

In my smb.conf

[music]
   comment = music folder
   read only = yes
   locking = no
   path = /storage/music
   guest ok = yes


Any creative way to make it accessible without changing group or owner permissions.

Thanks
- J

---

### Post by Iowan on 2008-08-27
It *looks* (to my feeble mind) like your share should accomplish that - but Samba can't be more generous than Linux, so the directory permissions will (probably) need editing.  I'm curious why you can't change permissions (not via **sudo**?)

---

### Post by amedac on 2008-08-27
Try open terminal and do this:
```
sudo gedit /etc/samba/smb.conf
```
and in [GLOBAL] section add this line:

```
usershare owner only = False
```

---

### Post by thejipster on 2008-08-29
> **amedac said:**
> Try open terminal and do this:
```
sudo gedit /etc/samba/smb.conf
```
and in [GLOBAL] section add this line:

```
usershare owner only = False
```

thanks for the suggestion.
This global option didn't work.

---

