---
title: "ordinary user can mount but can't umount"
date: 2006-12-01
forum: Networking &amp; Wireless
---

### Post by manifoldronin on 2006-12-01
(Edgy)
I have this entry in /etc/fstab:
```
//AWindowsBox/ASharedFolder /mnt/winshare smbfs username=someuser,rw,user,noauto               0       0

```

Now I can always "mount /mnt/winshare" without sudo, but I still have to "sudo umount /mnt/winshare". Without sudo, umount gives me "only root can unmount //AWindowsBox/ASharedFolder from /mnt/winshare".

What am I missing?

---

### Post by jpkotta on 2006-12-01
```
man smbumount
```

setuid root:

```
sudo chmod u+s $(which smbumount)
```

---

### Post by manifoldronin on 2006-12-02
Mmm... interesting. So I suid root on both smbmount and smbumount, but I have to do mount/smbumount (as opposed to mount/umount). Not too consistent... Oh well, so long as it works.

Thanks for the tip.

---

