---
title: "Nfs with permissions in others"
date: 2019-12-15
forum: Networking &amp; Wireless
---

### Post by korrupto on 2019-12-15
Hello, I have mounted via fstab shared folders of my Nas by nfs. They are mounted perfectly and I can navigate through them, I can even create new ones, but although the owner and the group has permission to read and write, in the section "others" is prohibited, so I can not access from a mobile or a tvbox.
If I give Nas no_root_squash permissions, I can change "others" to read and write if I do it as root in ubuntu, but apart from the fact that I don't think it's best, it's uncomfortable.
On the server I have full access as a guest, but when I mount the ubuntu folder ubuntu only allows the owner and the group to read.
How can I read to any user on my network?

---

### Post by TheFu on 2019-12-15
The owner can chmod/chgrp files on NFS storage.  Is this not working?

Please "show exact commands and proof" wrapped in code tags if you aren't 100% of your chmod-fu.
```
ls -l # before
chmod 755 path-to-directory
ls -l # after
```

Not all NAS devices fully implement all the protocol standards.  Exact vendor and model is probably helpful.

---

### Post by korrupto on 2019-12-16
I have a Qnap Ts-251+

> **TheFu said:**
> The owner can chmod/chgrp files on NFS storage.  Is this not working?

Please "show exact commands and proof" wrapped in code tags if you aren't 100% of your chmod-fu.
```
ls -l # before
chmod 755 path-to-directory
ls -l # after
```

Not all NAS devices fully implement all the protocol standards.  Exact vendor and model is probably helpful.

For example:

```
drwxrwxrwx+   11 root  root    4096 dic 16 12:19  PELICULASRESERVA
drwxrwxrwx+   29 david root    4096 dic 16 12:20  SERIESNAS
drwxrwxrwx+   53 david root    4096 dic 16 09:37  TorrentNAS
drwxrwxrwx+    5 david root    4096 dic 16 12:32  TorrentPRUEBA

```

after:

```
chmod 755 /home/david/TorrentPRUEBA/
```


```
drwxrwxrwx+   11 root  root    4096 dic 16 12:19  PELICULASRESERVA
drwxrwxrwx+   29 david root    4096 dic 16 12:20  SERIESNAS
drwxrwxrwx+   53 david root    4096 dic 16 09:37  TorrentNAS
drwxr-xr-x+    5 david root    4096 dic 16 12:32  TorrentPRUEBA

```

Now from ubuntu:

PELICULASRESERVA I can read and write and "others" have read-write access
SERIESNAS I can read and write and "others" have read-write access forbidden
TorrentNAS I can read and write and "others" have read-write access forbidden
TorrentPRUEBA I can read and write and "others" have read-write access forbidden

I'm going crazy.

---

### Post by TheFu on 2019-12-16
The '+' attribute means there are ACLs applied to each directory.  We don't know anything about the permissions using **ls -l**.  
Please do a **getfacl *** to see the ACLs. Or just clear them all.

---

### Post by korrupto on 2019-12-16
> **TheFu said:**
> The '+' attribute means there are ACLs applied to each directory.  We don't know anything about the permissions using **ls -l**.  
Please do a **getfacl *** to see the ACLs. Or just clear them all.


Two examples:

```

# file: TorrentNAS
# owner: david
# group: root
user::rwx
user:root:rwx
user:david:rwx
user:1003:r-x
user:1004:r-x
user:nobody:rwx
group::rwx
group:root:rwx
group:users:rwx
mask::rwx
other::rwx
default:user::rwx
default:user:root:rwx
default:user:david:rwx
default:user:1003:r-x
default:user:1004:r-x
default:user:nobody:rwx
default:group::rwx
default:group:root:rwx
default:group:users:rwx
default:mask::rwx
default:other::---
```
```

# file: PELICULASRESERVA
# owner: root
# group: root
user::rwx
user:root:rwx
user:david:rwx
user:1004:rwx
user:nobody:---
group::rwx
mask::rwx
other::rwx
default:user::rwx
default:user:root:rwx
default:user:david:rwx
default:user:1004:rwx
default:user:nobody:---
default:group::rwx
default:mask::rwx
default:other::rwx

```

---

### Post by korrupto on 2019-12-16
I just checked that in the shared folder TorrentPRUEBA for example the permissions are correct. Even in the @Recycle folder that creates the default Qnap inside, the correct permissions appear. It's when I create a folder from Ubuntu when I don't give option to "others" to access it.

---

### Post by TheFu on 2019-12-16
If it was me, I'd remove all ACLs to remove their override of the normal 32-bit permissions bits.  As long as there is an ACL, those permissions mean ZERO, nothing, nada.

Then I'd chgrp so the group is never root.  The "correct" group needs to be the one that david and whatever other processing userids share.  On my plex storage, I use the plex group for that.  My userid is in the plex unix group.  Then I'd set the setgid flag on any top level directory before creating any files or subdirectories where that group is important to be shared with other users or processes run by other users.

I'm not a fan of ACLs.

---

### Post by korrupto on 2019-12-16
I wouldn't know where to start. I don't know if you mean all permissions in general or just the required folders. In a Nas as I see it and with my scarce knowledge I don't know if it's possible that a shared folder with NFS access doesn't have ACLs.

---

### Post by TheFu on 2019-12-16
> **korrupto said:**
> I wouldn't know where to start. I don't know if you mean all permissions in general or just the required folders. In a Nas as I see it and with my scarce knowledge I don't know if it's possible that a shared folder with NFS access doesn't have ACLs.

NFSv3/4 can definitely supports ACLs. I tested it here. [https://www.tecmint.com/secure-files-using-acls-in-linux/](https://www.tecmint.com/secure-files-using-acls-in-linux/)  has a primer for ACLs. Here's an option to disable ACLs on the client:
```
To disable it on NFS client side again use “no_acl” option during mount time.
``` That would be safer & easier than modifying the ACLs on the NFS server.

Just for completeness,  [https://unix.stackexchange.com/questions/339765/how-to-remove-acl-from-a-directory-and-back-to-usual-access-control](https://unix.stackexchange.com/questions/339765/how-to-remove-acl-from-a-directory-and-back-to-usual-access-control)  says to use **setfacl   --remove-all   --no-mask    {globbing-pattern}**  The normal -R option is available too, just use it the same as with chmod or chgrp or chown for recursive modifications. Be EXTREMELY careful using -R.  People who use it and modify entire directory structures, especially for the OS directories usually have to do a full reinstall to fix it later.  

I tested the *  --remove-all   --no-mask *  options too, they worked over NFS and cleared the '+' in the permissions display from ls -al.

Definitely use the **no_acl** mount option to start. Bet that will get the normal permissions working as expected.  Are you mounting through to fstab, autofs or with systemd.mount/automount?

---

### Post by korrupto on 2019-12-16
> **TheFu said:**
> 
Definitely use the **no_acl** mount option to start. Bet that will get the normal permissions working as expected.  Are you mounting through to fstab, autofs or with systemd.mount/automount?

I use fstab to mount shares.  I'll try "no_acl" first in fstab seems less....dangerous.
Thank you again!!

---

