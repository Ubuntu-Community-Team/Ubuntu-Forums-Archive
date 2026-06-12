---
title: "Write permission for samba (cifs) NAS"
date: 2014-05-21
forum: Networking &amp; Wireless
---

### Post by Arjunanda on 2014-05-21
WD My Net N600 Router, with an USB port. I have hooked a WD Elements 1TB external hard drive on it. The router recognised it correctly, and I have configured the storage through the router admin interface.
I had some problems getting connected there from my Ubuntu desktop, but got that resolved by 

```
sudo apt-get install cifs-utils
```

And then editing my /etc/fstab, by adding the following line in the end:
```
//192.168.1.1/wd_elements_10b8_65/ /media/FFV-backup cifs guest 0 0
```

Instructions taken from here: [http://askubuntu.com/questions/109505/how-do-i-access-an-external-hard-drive-plugged-into-my-router](http://askubuntu.com/questions/109505/how-do-i-access-an-external-hard-drive-plugged-into-my-router)

Now the problem: I have no write access to my drive, if I try to access this mounted fs through the mount point:

```
drwxr-xr-x   2 root root    0 Mai 21 13:57 FFV-backup/
```

How should I change the permissions so that the user would have also write permission for this disk?

---

### Post by Arjunanda on 2014-05-21
I unmounted the FS, and tried 

```
sudo chown flow:flow FFV-backup 
```

which changed the permisson, but as soon as I mount it, the permissions are back to root:root

---

### Post by Arjunanda on 2014-05-21
Got it mounted manually with:
```
sudo mount -o nosuid,uid=1000,gid=1000 //192.168.1.1/wd_elements_10b8_65/ /media/FFV-backup/
```

Now trying to figure out how to include those options in the /etc/fstab

---

### Post by Arjunanda on 2014-05-23
Ok, got it working with the following line in my /etc/fstab:

```
//192.168.1.1/wd_elements_10b8_65/ /media/FAV-backup cifs guest,nosetuids,noperm 0 0
```

All is fine, except that I'm getting errors for symlinks when trying to run backup to that location with Back in Time.

---

