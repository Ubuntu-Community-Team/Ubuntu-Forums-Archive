---
title: "Mounting an nfts external drive"
date: 2009-07-23
forum: New to Ubuntu
---

### Post by m_ad on 2009-07-23
I just reinstalled 8.04, and I'm faced with a problem.. I can't give myself access to mount this WD My Book (ntfs).

/etc/fstab
```
# WD MyBook
UUID=1BF01501126BEDB9	/media/MyBook	ntfs-3g	user,rw,noauto	0	0
```

I swear this is exactly what I had in my last fstab and it worked fine. Now I'm getting an error:

```
Unprivileged user can not mount NTFS block devices using the external FUSE
library. Either mount the volume as root, or rebuild NTFS-3G with integrated
FUSE support and make it setuid root. Please see more information at
http://ntfs-3g.org/support.html#unprivileged

```

This didn't happen on my last system.

---

### Post by yeats on 2009-07-23
can you do

```
ls -l /etc/fstab
```

?

This sounds like a permissions thing....

---

### Post by llamabr on 2009-07-23
Or mount it as root:

```
sudo mount /media/MyBook
```

---

### Post by crf on 2009-07-24
[http://ntfs-3g.org/support.html#useroption2]("http://ntfs-3g.org/support.html#useroption2") -- gives some things to try.

---

### Post by ~sHyLoCk~ on 2009-07-24
> **m_ad said:**
> 
/etc/fstab
```
# WD MyBook
UUID=1BF01501126BEDB9	/media/MyBook	ntfs-3g	user,rw,noauto	0	0
```

Make the "user" as "users" and also put "defaults"

---

### Post by m_ad on 2009-07-24
> **chrissharp123 said:**
> can you do

```
ls -l /etc/fstab
```

?

This sounds like a permissions thing....

```
[matt@matt-desktop:~]$ ls -l /etc/fstab
-rw-r--r-- 1 root root 734 2009-07-23 18:03 /etc/fstab
```


> **llamabr said:**
> Or mount it as root:

```
sudo mount /media/MyBook
```

This is why I'm adding it to fstab though, so that I (not root) can write to the drive

> **crf said:**
> [http://ntfs-3g.org/support.html#useroption2]("http://ntfs-3g.org/support.html#useroption2") -- gives some things to try.

Thanks, I'll read through it..

> **~sHyLoCk~ said:**
> Make the "user" as "users" and also put "defaults"

Let me try this, thanks.

---

