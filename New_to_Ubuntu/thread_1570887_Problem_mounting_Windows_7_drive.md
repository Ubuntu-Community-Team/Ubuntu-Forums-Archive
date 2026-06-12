---
title: "Problem mounting Windows 7 drive"
date: 2010-09-08
forum: New to Ubuntu
---

### Post by baddnady23 on 2010-09-08
I get this message...  Never had this happen before.  What do I need to change to get around this?

---

### Post by sandyd on 2010-09-08
> **baddnady23 said:**
> I get this message...  Never had this happen before.  What do I need to change to get around this?
post the output of
```

sudo cat /etc/fstab
```
you just need to add "users" to the opts column of the cdrom's entry in the fstab

---

### Post by baddnady23 on 2010-09-08
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sdb1 :
UUID=b9d5171c-0d54-4bef-b2a3-613a922f656b    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sdb4 :
UUID=794c6ff5-df36-462e-a2db-6184f8f50618    /home    ext4    defaults    02
#Entry for /dev/sdc1 :
UUID=178C148D5D7947A6    /media/Windows 7    ntfs    defaults,nls=utf8,umask=0222,nosuid,nodev    0    0
#Entry for /dev/sda1 :
UUID=6f23b0ac-0650-49da-9c4b-cacda4dcec57    /media/storage    auto    defaults0    0
#Entry for /dev/sdb3 :
UUID=4151f5bd-04d6-416c-969c-fb41c0444435    none    swap    sw    0    0
/dev/fd0    /media/floppy0    auto    rw,user,noauto,exec,utf8    0    0
#
#
# Entry for andrew-server NFS share
# Note that you mush create mount point /media/andrew-server
192.168.1.70:/media/data    /media/andrew-server    nfs    rsize=8192,wsize=8192,timeo=14,intr

```

---

### Post by sandyd on 2010-09-08
> **baddnady23 said:**
> ```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sdb1 :
UUID=b9d5171c-0d54-4bef-b2a3-613a922f656b    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sdb4 :
UUID=794c6ff5-df36-462e-a2db-6184f8f50618    /home    ext4    defaults    02
#Entry for /dev/sdc1 :
UUID=178C148D5D7947A6    /media/Windows 7    ntfs    defaults,nls=utf8,umask=0222,nosuid,nodev    0    0
#Entry for /dev/sda1 :
UUID=6f23b0ac-0650-49da-9c4b-cacda4dcec57    /media/storage    auto    defaults0    0
#Entry for /dev/sdb3 :
UUID=4151f5bd-04d6-416c-969c-fb41c0444435    none    swap    sw    0    0
/dev/fd0    /media/floppy0    auto    rw,user,noauto,exec,utf8    0    0
#
#
# Entry for andrew-server NFS share
# Note that you mush create mount point /media/andrew-server
192.168.1.70:/media/data    /media/andrew-server    nfs    rsize=8192,wsize=8192,timeo=14,intr

```
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sdb1 :
UUID=b9d5171c-0d54-4bef-b2a3-613a922f656b    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sdb4 :
UUID=794c6ff5-df36-462e-a2db-6184f8f50618    /home    ext4    defaults    02
#Entry for /dev/sdc1 :
UUID=178C148D5D7947A6    /media/Windows 7    ntfs    users,defaults,nls=utf8,umask=0222,nosuid,nodev    0    0
#Entry for /dev/sda1 :
UUID=6f23b0ac-0650-49da-9c4b-cacda4dcec57    /media/storage    auto    defaults0    0
#Entry for /dev/sdb3 :
UUID=4151f5bd-04d6-416c-969c-fb41c0444435    none    swap    sw    0    0
/dev/fd0    /media/floppy0    auto    rw,user,noauto,exec,utf8    0    0
#
#
# Entry for andrew-server NFS share
# Note that you mush create mount point /media/andrew-server



192.168.1.70:/media/data    /media/andrew-server    nfs    rsize=8192,wsize=8192,timeo=14,intr

```

This should get you rolling.

---

### Post by baddnady23 on 2010-09-08
Got it working! Thanks for the continued help here on the forums carlee.  Both your guidance and your blog are top notch

---

### Post by sandyd on 2010-09-09
> **baddnady23 said:**
> Got it working! Thanks for the continued help here on the forums carlee.  Both your guidance and your blog are top notch

your welcome :)

---

