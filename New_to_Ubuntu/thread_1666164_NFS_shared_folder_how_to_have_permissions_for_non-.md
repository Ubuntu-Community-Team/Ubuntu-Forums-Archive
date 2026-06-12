---
title: "NFS shared folder: how to have permissions for non-root user?"
date: 2011-01-13
forum: New to Ubuntu
---

### Post by Unewbeginner on 2011-01-13
hi all, I set my /etc/exports as

```
/share 192.168.1.3(rw,no_root_squash,no_subtree_check)
```

On my client, I have the same folder /share to mount.

I could read all the files inside the share folder. But I can't write to it unless I do that as root user. Anything I did wrong? Thanks.

---

### Post by cariboo on 2011-01-13
I use the following in my exports file:

```
/media/documents	192.168.1.0/24(rw,async,no_subtree_check)
```

files and directories are owned by whomever created them using the above.

The ip address allows any one on my internal network to access the shares and write to them.

---

