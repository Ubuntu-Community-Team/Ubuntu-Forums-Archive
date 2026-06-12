---
title: "CIFS mount file permissions break after mounted for a certain period"
date: 2007-03-17
forum: Networking &amp; Wireless
---

### Post by bluearcus on 2007-03-17
Hi there,

I recently bought a Thecus N2100 network SAN box, which I've been setting up to access from my Edgy Kubuntu system.

All seems fine with the setup under SMBFS, but obviously performance on the shares is very poor with this, so I have been experimenting with CIFS VFS instead.

CIFS is much faster, but when leaving a network share mounted for a long period of time (over a day) all file read operations start to fail with 'permission denied' errors, even though the permission attributes on the files are still reporting correctly.

Unmounting and remounting the volume does not fix this, only rebooting or reverting back to an SMBFS mount.

Any ideas?

Regards,

Mike

---

### Post by jegHegy on 2007-09-13
Bumping this because I'm getting similar symptoms. I'm mounting Windows Server 2003 R2 shares with lines like this in /etc/fstab:
```
//szerver/it    /media/szak/it  cifs    user,auto,credentials=/root/.smbpw,iocharset=utf8,file_mode=0777,dir_mode=0777  0       0
```

Except unlike the Original Poster, mine fail after a few hours, throwing me "Permission denied" when I try to access the shares, even as root. Is /media a special directory that might cause things like this?

PS: Mounting with smbfs gives me errors about disabled signatures.

---

### Post by Voland on 2007-09-14
I've found the same problem. Does anyone can help to solve it?

---

### Post by Voland on 2007-09-20
OK I've found solution: troubles were with win user profile.

---

