---
title: "mount"
date: 2008-04-18
forum: Networking &amp; Wireless
---

### Post by Gaute91 on 2008-04-18
i try to mount a networkfolder but i only get this message:
 6880: session setup failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed, i have make a typed inn the passwords in the fstab file, but it don't work :(

---

### Post by dstew on 2008-04-18
> i try to mount a networkfolderHow are you doing this? Are you using the mount command on the command line, or graphical tools? Is the network folder set up for sharing? Is samba client installed on your Ubuntu machine?

---

### Post by Gaute91 on 2008-04-18
i've tried different stuff from command line... i have to mount it to a special folder (/mnt/NetRender)... i have also tried to edit the fstab file...

---

### Post by dstew on 2008-04-18
Post the output of```
smbclient -L *<hostname>*
```

---

### Post by Gaute91 on 2008-04-18
when i write my password or the root password to the network host i get:
```

Password: 
session setup failed: NT_STATUS_LOGON_FAILURE

```

---

### Post by Gaute91 on 2008-04-20
Does anyone have any idea?

---

### Post by Gaute91 on 2008-04-20
solved!

---

