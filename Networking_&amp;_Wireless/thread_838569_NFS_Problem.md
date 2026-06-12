---
title: "NFS Problem"
date: 2008-06-23
forum: Networking &amp; Wireless
---

### Post by jagnikam on 2008-06-23
Hi all,
i want mount directory with permission

#NFS Server = FreeBSD
/etc/export =
/data -alldirs -network 192.168.0.0 -mask 255.255.255.0

#NFS Client = Ubuntu
192.168.0.8:/data /dir nfs intr

but i m unable to create folder in /dir

whts the wrong?
Please Help me

---

### Post by durand on 2008-06-23
> **jagnikam said:**
> Hi all,
i want mount directory with permission

#NFS Server = FreeBSD
/etc/export =
/data -alldirs -network 192.168.0.0 -mask 255.255.255.0

#NFS Client = Ubuntu
192.168.0.8:/data /dir nfs intr

but i m unable to create folder in /dir

whts the wrong?
Please Help me

/dir resides in the root of the filesystem and you cannot add folders to it without **root access**.
Try:
```
sudo mkdir /dir 
```

---

### Post by jagnikam on 2008-06-23
> **durand said:**
> /dir resides in the root of the filesystem and you cannot add folders to it without **root access**.
Try:
```
sudo mkdir /dir 
```

thanks for reply 
I am using the root user.

---

### Post by durand on 2008-06-23
Can you mount this partition in other places?

If so, do that, then symlink the mount place to /dir

```
sudo ln -s /place/where/you/mounted/it /dir
```

It should work in the same way.

---

