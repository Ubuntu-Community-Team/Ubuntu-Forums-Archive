---
title: "How to mount ntfs if I want the one user to have read-write access"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by anonymous01 on 2009-05-13
How to mount ntfs if I want the one user to have read-write access but other users have read only acess

---

### Post by iaculallad on 2009-05-13
Editing /etc/fstab file for auto mounting NTFS partition for read/write access is possible but you can't apply Linux partitions on it by trying to limit other users on from accessing it:

Such as:

```
sudo chown -R username:username /media/NTFS_Partition
sudo chmod -R 700 /media/NTFS_Partition
```

Commands above cannot be applied on NTFS partitions.

---

### Post by anonymous01 on 2009-05-13
I want is that only root have read-write access and other users have read access only. Any help?

---

### Post by iaculallad on 2009-05-13
But placing Umask would probably solve that issue. Try:

```
sudo mount -t ntfs -o ro,noauto,umask=022 /dev/xxx /media/mount_point
```

Change xxx with the drive/partition device name. Also, change /media/mount_point with the mount point you created for that partition.

---

### Post by Russell Burrows on 2009-05-13
I  limit other users to read only via  selection in system administration users and groups    users settings   manage groups.

Hope this helps.

---

### Post by anonymous01 on 2009-05-13
I want to have permanent mount with the root have rw access and other users have ro access

---

### Post by saivin on 2009-05-13
> **iaculallad said:**
> But placing Umask would probably solve that issue. Try:

```
sudo mount -t ntfs -o ro,noauto,umask=022 /dev/xxx /media/mount_point
```

Is 'ro' option appropriate above?  umask=022 means read access to others and full access to root right?  Also, I think its better to use ntfs-3g.

I can't check and confirm as I don't have windoz... :)

---

### Post by anonymous01 on 2009-05-13
> **iaculallad said:**
> But placing Umask would probably solve that issue. Try:

```
sudo mount -t ntfs -o ro,noauto,umask=022 /dev/xxx /media/mount_point
```Change xxx with the drive/partition device name. Also, change /media/mount_point with the mount point you created for that partition.
Thank you problem solve.

---

