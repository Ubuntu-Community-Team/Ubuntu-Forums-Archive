---
title: "Mounting SMB share Nas4free on ubuntu problems."
date: 2015-11-29
forum: Networking &amp; Wireless
---

### Post by ryttge on 2015-11-29
Hello i'm using ubuntu 14.04 LTS have created a SMB share on my nas4free nas and have problems mounting it in CLI.
Works with windows, works with linux mint GUI works with smbclient on the server.

I need to mount it on the server then add it in fstab, tried everything i could find on google but to no avail.

```

root@xxx:/# mount.cifs //192.168.1.xx/Share /Share -o username=myusername,password=mypassword,iocharset=utf8,file_mode=0777,dir_mode=0777
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

```

Smbclient on the same server
```

root@xxx:/# smbclient //192.168.1.xxx/Share /Share -o username=mysuername,
Domain=[WORKGROUP] OS=[Windows 6.1] Server=[Samba 4.2.5]
smb: \> ls
  .                                   D        0  Fri Nov 27 16:56:38 2015
  ..                                  D        0  Thu Nov 26 17:19:11 2015
  xxx                               D        0  Sun Nov 29 16:35:53 2015
  xxx                               D        0  Fri Nov 27 16:56:29 2015
  xxx                               D        0  Fri Nov 27 16:56:33 2015

```

Any ideas?

Kind Regards Ryttge

---

