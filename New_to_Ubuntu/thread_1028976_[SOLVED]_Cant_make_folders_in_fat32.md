---
title: "[SOLVED] Cant make folders in fat32?"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by hopelessone on 2009-01-02
Hi there,

I can't make folders in a new formatted fat32 HDD...

usually i do:

> sudo chown -R USERNAME:USERNAME /media/mynewdrive

but it gives me:

> some@some-one:~$ sudo chown -R some:some /mnt/hdd_1
chown: changing ownership of `/mnt/hdd_1': Operation not permitted

my fstab:

> /dev/sda1 /mnt/hdd_1     vfat defaults 0 0

how can i do this?

thanks...

---

### Post by mc4man on 2009-01-02
Don't know exactly what your doing in the first 2 quotes but for the 1 fat32 volume I want auto mounted I use this in fstab

Edit: now i see the first 2 quotes are not related, if you want the volume auto mounted thru fstab then just make a proper entry as below
If for some reason you need to chown it, then comment the fstab out, let it mount to the default of /media/<volume label> and chown that if needed(though you shouldn't have to with a vfat volume

```
/dev/sdb8        /media/music   vfat iocharset=utf8,umask=000 0 0
```

---

### Post by wolfen69 on 2009-01-02
> /dev/sda1 /mnt/hdd_1 vfat defaults 0 0 
are you sure it shouldn't be sdb1? (sdc1,etc) sda1 is usually the main drive/partition.

do ```
sudo fdisk -l
```

---

### Post by hopelessone on 2009-01-05
i formatted to NTFS and continued...

sda1 is right..weird but right...

---

