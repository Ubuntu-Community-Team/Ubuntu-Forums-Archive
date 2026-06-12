---
title: "[SOLVED] NFS Mounting Problem"
date: 2007-05-31
forum: Networking &amp; Wireless
---

### Post by borobudur on 2007-05-31
Hi there,
I have successfully mounted (in fstab) a directory from my desktop to the laptop over a wireless connection with NFS. 
Now I added a user to the laptop machine and with this user I can't access the mounted directory. I can't even access with sudo but if I change the user it's still working. 
This user which has access must be stored in some file somewhere on the desktop.
Has anyone an idea where to add the second user?
Thanks!

---

### Post by netztier on 2007-05-31
> **borobudur said:**
> Hi there,
I have successfully mounted (in fstab) a directory from my desktop to the laptop over a wireless connection with NFS. 
Now I added a user to the laptop machine and with this user I can't access the mounted directory. I can't even access with sudo but if I change the user it's still working. 
This user which has access must be stored in some file somewhere on the desktop.
Has anyone an idea where to add the second user?
Thanks!

You need to have a user with the *same* UID/GID numbers on **both** machines, then it will work (see **Advanced** tab in the properties dialog of each user in in **System - Administration - Users and Groups**).

This requirement of NFS is the reason why in larger UNIX environments, you need some central service providing this information (NIS for example). Keeping the user and group files in sync on dozens or hundreds of machines would be a nightmare without it...

Best regards

Marc

---

### Post by borobudur on 2007-06-04
I have the same UID on both machines. Still the same :-(

---

### Post by borobudur on 2008-03-01
I did finally the following and it works now more or less:

_**Server**_

Install
```
sudo apt-get install nfs-kernel-server nfs-common portmap
```

Editing /etc/exports For Full Read Write Permissions allowing any computer from 192.168.1.1 through 192.168.1.255
```
/files 192.168.1.1/24(rw,no_root_squash,async)
/media/BACKUP 192.168.1.1/24(fsid=0,rw,squash_uids=1000-1001,squash_gids=1001,sync,no_subtree_check)
```

save this file and then in a terminal type
```
sudo /etc/init.d/nfs-kernel-server restart
```

Also aftter making changes to /etc/exports in a terminal you must type
```
sudo exportfs -a
```

_**Client**_

Install
```
sudo apt-get install portmap nfs-common
```


The mount point /files must first exist on the client machine.
```
sudo mount server.mydomain.com:/files /files
```

Note you may need to restart above services:
```
sudo /etc/init.d/portmap restart
sudo /etc/init.d/nfs-common restart
```

Mounting at boot using /etc/fstab
```
server.mydomain.com:/files /files nfs rsize=8192,wsize=8192,timeo=14,intr
```

These links helped me:

[http://linuxreviews.org/man/exports/index.html](http://linuxreviews.org/man/exports/index.html)
[http://www.linux-praxis.de/linux2/nfs.html](http://www.linux-praxis.de/linux2/nfs.html)

---

