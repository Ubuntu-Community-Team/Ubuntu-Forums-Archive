---
title: "Sharing samba drive via Fstab"
date: 2016-10-08
forum: Networking &amp; Wireless
---

### Post by justcop2 on 2016-10-08
Hi all, I'm struggling trying to automount my samba network drive on boot. 


If I type in the following command after boot it works fine, 
```

sudo mount -t cifs //192.168.1.1/usbdisk/JMicron_USBtoATA/ATAPIbridge_1_49f7  /home/justcop/External -o guest,uid=justcop 



```

but if I try to automount by including the following line in /etc/fstab I get nothing mounted. 


```
//192.168.1.1/usbdisk/JMicron_USBtoATA/ATAPIbridge_1_49f7 /home/justcop/External cifs rw,_netdev,guest,uid=justcop, 0 0

```

Any ideas? I've always found fstab incredibly frustrating.

---

### Post by TheFu on 2016-10-08
uid is a number (like 1000).  username is text.  Also, if the storage supports NFS, it would be better to use that over CIFS.  Also, don't think you want that trailing comma.

Garbage in. Garbage out. Typical computer.

BTW, "automount" is a specific tool that mounts storage only when it is requested. The autofs package makes that possible. It is slightly more complicated than the fstab to setup, but for USB and networked storage, I prefer it, especially on portable systems where the storage might not always be available.

---

### Post by justcop2 on 2016-10-08
The answer is always garbage in. garbage out. The hard part is working out where the garbage is!

With your help got it working with following

> //192.168.1.1/usbdisk/JMicron_USBtoATA/ATAPIbridge_1_49f7 /home/justcop/External cifs  guest,uid=1000  0  0

Thanks so much

---

### Post by TheFu on 2016-10-08
> **justcop2 said:**
> The answer is always garbage in. garbage out. The hard part is working out where the garbage is!
With your help got it working with following

Thanks so much

That is not always the answer. There are bugs sometimes, but not with well-tested/well-used stuff (usually). BTW, the manpage for fstab and/or mount.cifs might have had the answer too.  Yep - **man mount.cifs** had it:
```
       uid=arg
           sets the uid that will own all files or directories on the mounted
           filesystem when the server does not provide ownership information.
           It may be specified as either a username or a numeric uid. When not
           specified, the default is uid 0. The mount.cifs helper must be at
           version 1.10 or higher to support specifying the uid in non-numeric
           form. See the section on FILE AND DIRECTORY OWNERSHIP AND
           PERMISSIONS below for more information.

```
Based on that, the uid=justcop2 option probably would work. Maybe it was the trailing comma?  Most config files care about that detail, though perl usually doesn't, most other languages do.  However, I wouldn't expect uid to allow anything other than the uid as specified in the passwd entry (that can be in the /etc/passwd file or through some external directory service like AD or LDAP or x.500 used for authentication.  'id' usually means a number in Unix systems.  *gid* would be the group number, similarly.  People not used to working in groups don't take advantage of the groups. Some amazing things can be done with groups.

Anyway, the main thing is that it works now.

---

