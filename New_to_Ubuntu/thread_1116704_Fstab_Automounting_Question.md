---
title: "Fstab Automounting Question"
date: 2009-04-05
forum: New to Ubuntu
---

### Post by Chrissd on 2009-04-05
Hi, my computer is setup to automount this hard drive, however, I've recently changed it from FAT32 to EXT3 (I think?), and now the system keeps linking everything to the wrong place. I think it's due to the line below in /etc/fstab, can anyone tell me if this is correct?

Thanks in advance.   

UUID=489E-E1C6 /media/80GB vfat defaults,umask=0007,gid=46 0 0

---

### Post by lucasl on 2009-04-05
Change 'vfat' to 'auto' or 'ext3'.

---

### Post by Chrissd on 2009-04-05
Didn't work, tried both auto and ext3. I'll be more specific. If I go to Places - 80GB Media it goes to a place with just lost+found, if I click up then 80GB, it shows the contacts that I expect (music).

---

### Post by lamalex on 2009-04-05
If you changed the file system then the UUID has changed, look in /dev/disk/by-uuid for the new UUID of the disk.

---

### Post by Chrissd on 2009-04-07
```
ls /dev/disk/by-uuid
```
returns this:
```
0adb8e95-aae9-4557-abf5-029626d1b4a7  3606b7a5-9bed-4c3c-bcc1-7276c91016fd
1617BD3D5ECF9453                      660c88b7-d32b-4007-96bc-d7ac0d822096
```

---

