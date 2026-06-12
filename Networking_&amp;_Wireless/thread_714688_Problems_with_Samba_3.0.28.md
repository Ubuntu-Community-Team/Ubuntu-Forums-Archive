---
title: "Problems with Samba 3.0.28"
date: 2008-03-04
forum: Networking &amp; Wireless
---

### Post by ambiman2 on 2008-03-04
Hello guys,

i've a strange problem with samba ( ver 3.0.28 )!

When i tried to mount the smb share like this:

mount -t cifs //server-ip/share /mountpoint -o username=name

or

mount -t cifs //server-ip/share /mountpoint -o username=name

it results in

mount error 20 = Not a Directory

Btw: The mountpoint and the shared folder exist  :-)

On the samba-system  the modules cifs.ko and smbfs.ko are loaded! Also the package smbfs is installed on both systems.
The test of the smb.conf with testparm produces no warnings.

The connection with smbclient //server-ip/share works great without any errors :-/
So the permissions are ok!

I also tried to share an empty directory on the server like /testfolder. (to exlude some charset or codepage errors), but it results in the same error.

Any ideas?

P.S.: The workaround ( echo 0 > /proc/fs/cifs/LinuxExtension ) also won't work.

Kind regards,

Daniel

---

### Post by Eiríkr on 2008-03-10
The last time I saw that same error scenario was when troubleshooting a thread about Samba connections using Windows usernames with no passwords assigned.  Is this your case as well?  

Cheers,

Eiríkr

---

### Post by morgan_greywolf on 2008-04-30
Don't know if you got this problem resolved or not, but what you need to do is
```
sudo apt-get install smbfs
```

---

