---
title: "Unable to access mounted NFS share"
date: 2019-09-26
forum: Networking &amp; Wireless
---

### Post by DebilMudak on 2019-09-26
I have a Synology NAS and a Ubuntu laptop. I have successfully mounted a shared folder on the NAS to this laptop using the terminal command ```
sudo mount 192.168.xxx.xxx:/volume1/Example /mnt/Example
```
However I am unable to access the mounted directory unless I launch *Nautilus* as sudo. I would like to be able to access this share without sudo priviledges. How to address this problem? I am guessing this requires some permission changes.

The NFS permissions on the NAS are configured as follows:
[IMG]https://i.ibb.co/GMbj9VN/nfs-permissions.png[/IMG]

(Please move this thread to the correct subforum if this is in a wrong one.)

---

### Post by SeijiSensei on 2019-09-26
I usually mount NFS shares as root.  Then users will have the same permissions on the share as they do on the Linux filesystem itself. 

For instance, my NFS server (running Linux; not a NAS) has about half-a-dozen users defined in /etc/passwd.  I mount the server's /home to a mount point in my desktop machine.  Then I can access the directories to which I have rights and am blocked from the directories for which I don't have permissions.  How you'd do this with a NAS I don't know.  Can you get around that GUI and access the underlying operating system on the device?

---

### Post by DebilMudak on 2019-09-28
> **SeijiSensei said:**
> I usually mount NFS shares as root.  Then users will have the same permissions on the share as they do on the Linux filesystem itself. 

For instance, my NFS server (running Linux; not a NAS) has about half-a-dozen users defined in /etc/passwd.  I mount the server's /home to a mount point in my desktop machine.  Then I can access the directories to which I have rights and am blocked from the directories for which I don't have permissions.  How you'd do this with a NAS I don't know.  Can you get around that GUI and access the underlying operating system on the device?

Synology's DSM is a Linux based operating system and I can SSH my way into the NAS. I think it uses Linux kernel.

What do you mean by *mounting NFS shares as root*? Should I mount the share to a folder inside my own home directory?

---

### Post by TheFu on 2019-09-28
Linux/Unix is multi-user OS. Every process runs under a specific userid, which provides the permissions for that process.  Mounting is typically performed as root for NFS.  Other types of mounts, like CIFS would typically be run as the end user who wants access.

To me, the root issue appears to be permissions.  NFS supports native Unix permissions, so it might be possible to change them using normal methods. But if nautilus is used with sudo/root, then that could make things more complicated.
```
ls -al /mnt/Example
```
would be helpful. Just need to see the permissions for the parent, current directory and a few files to know. 

Different NAS devices have, in the past, cut corners by not implementing a full NFS/CIFS/AFS program.  If the NFS on the NAS device isn't a full version, that makes it hard for all the expected features to be used, which leads to limitations.  I've always used NFS servers from full implementations, never from consumer NAS devices, but we see limitations from time to time in these forums.
In a full NFS implementation, root on the client machine cannot be used to manage permissions on the NAS storage. By default, root on a client doesn't have any access without a special, seldom used, option.  OTOH, if the NAS sets this option to allow client-side root to control permissions, then a simple chown and chmod would likely fix this issue. 

How many different userids on the clients need access to the storage? Are they in the same group?  Can they be?  Do they need write permissions or just read?

And IMHO, storage should never be mounted inside any HOME directory.  Mount it somewhere else, like /opt/d1 and create a symbolic link to it from any HOME directories where easy access is desired.

Really, the best place to get help with a NAS is on the NAS device forums, being specific about the exact model used and the specific client you want to use.

---

### Post by SeijiSensei on 2019-09-28
No, you want to mount the shares to a mount point somewhere outside anyone's home directory.  I usually create mount points under /media, e.g., /media/nfs.

```

sudo mkdir /media/nfs
sudo mount server:/share /media/nfs

```

That will make a mount point owned by root.  If the share is also owned by root, e.g., /home, then all users will have the same permissions on the share as they do on local files and directories.

The other traditional mount point is /mnt, but I prefer to keep that available for temporary mounts.

---

### Post by DebilMudak on 2019-09-29
> **TheFu said:**
> Linux/Unix is multi-user OS. Every process runs under a specific userid, which provides the permissions for that process.  Mounting is typically performed as root for NFS.  Other types of mounts, like CIFS would typically be run as the end user who wants access.

To me, the root issue appears to be permissions.  NFS supports native Unix permissions, so it might be possible to change them using normal methods. But if nautilus is used with sudo/root, then that could make things more complicated.
```
ls -al /mnt/Example
```
would be helpful. Just need to see the permissions for the parent, current directory and a few files to know. 

Different NAS devices have, in the past, cut corners by not implementing a full NFS/CIFS/AFS program.  If the NFS on the NAS device isn't a full version, that makes it hard for all the expected features to be used, which leads to limitations.  I've always used NFS servers from full implementations, never from consumer NAS devices, but we see limitations from time to time in these forums.
In a full NFS implementation, root on the client machine cannot be used to manage permissions on the NAS storage. By default, root on a client doesn't have any access without a special, seldom used, option.  OTOH, if the NAS sets this option to allow client-side root to control permissions, then a simple chown and chmod would likely fix this issue. 

How many different userids on the clients need access to the storage? Are they in the same group?  Can they be?  Do they need write permissions or just read?

And IMHO, storage should never be mounted inside any HOME directory.  Mount it somewhere else, like /opt/d1 and create a symbolic link to it from any HOME directories where easy access is desired.

Really, the best place to get help with a NAS is on the NAS device forums, being specific about the exact model used and the specific client you want to use.

Here are the results:

```
drwxrwxrwx 17 root root   4096 syys   18 23:31  .
drwxr-xr-x  3 root root   4096 syys   24 23:44  ..
drwxrwxrwx  8 1026 users  4096 heinä   5 20:24  xxx
drwxrwxrwx  3 1026 users 20480 heinä  16 22:50  xxx
drwxrwxrwx 31 1026 users  4096 syys   28 13:28  xxx
drwxrwxrwx  5 1026 users  4096 syys   12 12:42  xxx
drwxrwxrwx  3 1026 users  4096 heinä   7 21:41  xxx
drwxrwxrwx  3 1026 users 28672 heinä   1 23:53  xxx
drwxrwxrwx  3 1026 users  4096 heinä  18 23:44  xxx
drwxrwxrwx 78 1026 users  4096 elo    25 21:58  xxx
drwxrwxrwx 53 1026 users  4096 kesä   29 22:50  xxx
drwxrwxrwx  8 1026 users  4096 syys   26 23:41  xxx
drwxrwxrwx  4 1026 users  4096 syys    9 22:32  xxx
drwxrwxrwx  3 1026 users  4096 syys    6 15:41  xxx
drwxrwxrwx  4 root root   4096 syys   26 23:41 '#recycle'
drwxrwxrwx 29 1026 users  4096 syys   18  2018  xxx
-rwxrwxrwx  1 1032 users 37888 elo     6 21:54  Thumbs.db

```

This client PC has only one user account and it is the only account that needs to access these shares through NFS.

---

### Post by TheFu on 2019-09-29
On the client PC, run 'id', what does that show?
If the uid  isn't 1026 or 1032, that could be part of the issue. I'm not certain about that. 

Having 777 permissions is a huge security failure, IMHO.  Allowing "other" to have write permissions on a network device is bad for many reasons.  It shouldn't stop any userid from being able to write based on the files show.

In theory, if it is allowed, **sudo chown -R $LOGNAME /mnt/Example/* ** might fix it.  It wouldn't work on any of my NFS servers, but it might with a device like yours. Then you can use chgrp -R - only the owner can do that.

Unix permissions tutor: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)   NFS supports native permissions.

---

### Post by DebilMudak on 2019-10-02
> **TheFu said:**
> On the client PC, run 'id', what does that show?
If the uid  isn't 1026 or 1032, that could be part of the issue. I'm not certain about that. 

Having 777 permissions is a huge security failure, IMHO.  Allowing "other" to have write permissions on a network device is bad for many reasons.  It shouldn't stop any userid from being able to write based on the files show.

In theory, if it is allowed, **sudo chown -R $LOGNAME /mnt/Example/* ** might fix it.  It wouldn't work on any of my NFS servers, but it might with a device like yours. Then you can use chgrp -R - only the owner can do that.

Unix permissions tutor: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)   NFS supports native permissions.

Uid was **1000**. What exactly does that command of yours do?

The mounted folder is behaving differently now. Now if I log I navigate to the folder in Nautilus and open it, Ubuntu simply prompts me for my local password. Then I can freely browse inside the shared folder except when I try to open any file at all, I am required to enter my local password.

---

### Post by TheFu on 2019-10-02
> **DebilMudak said:**
> Uid was **1000**. What exactly does that command of yours do?

The mounted folder is behaving differently now. Now if I log I navigate to the folder in Nautilus and open it, Ubuntu simply prompts me for my local password. Then I can freely browse inside the shared folder except when I try to open any file at all, I am required to enter my local password.

The link provided is a tutorial on what **chmod** and **chown** do.  Good that you didn't run any commands without understanding what they do first.

---

### Post by DebilMudak on 2020-01-01
I studied chmod and chown a bit and I was able to successfully mount a shared folder named TEST. I was able to do this by claiming ownership of the folder in Terminal. My local Ubuntu user is now the owner of said TEST folder. It belongs to the group *users*. However I am unable create, modify or delete any files within this TEST folder. I am guessing the permissions are still messed up. What is wrong?

Permissions are as follows:
```
drwxrwxr-x 3 mylocaluser users  4096
drwxrwxr-x 3 mylocaluser users 20480
drwxrwxr-x 2 mylocaluser root   4096
```
These are 3 folders within the shared folder.

EDIT: Apparently I can freely edit files within these existing folders but I can not make any modifications to the root of shared folder TEST.

---

