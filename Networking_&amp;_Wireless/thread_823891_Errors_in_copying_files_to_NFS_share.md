---
title: "Errors in copying files to NFS share"
date: 2008-06-09
forum: Networking &amp; Wireless
---

### Post by sang froid on 2008-06-09
I have an NFS share on a server running Xubuntu 7.10 and the client is running Ubuntu 8.04. The share mounts fine but when I try to copy files from my hard drive to the share using nautilus I get this error:

```
Error while copying "$file".
There was an error copying the file into $share.
Error while opening file '$path': operation not permitted
```

However, it creates a blank file that doesn't appear in nautilus and if I try again it says the file already exists and allows me to successfully copy over it.

If I try to copy using the command line I get the following:

```
~$ cp $file $share
cp: cannot create regular file '$file': Operation not permitted
```

But if I copy recursively (cp -r) it does copy without an error...so I think that means the problem is on the client side. Also, copying as root, even recursively, returns permission denied.

Here is the fstab

```
NAS:/data /home/$user/Shared nfs user,rsize=8192,wsize=8192,timeo=14,intr
```

This problem only popped up recently, so I think it might be something that changed in the upgrade to Hardy. Thanks in advance.

---

### Post by sang froid on 2008-06-09
bump

---

### Post by sang froid on 2008-06-11
last bumb

---

