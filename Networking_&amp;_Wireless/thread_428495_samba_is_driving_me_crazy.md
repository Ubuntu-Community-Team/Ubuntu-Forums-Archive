---
title: "samba is driving me crazy"
date: 2007-04-30
forum: Networking &amp; Wireless
---

### Post by rvdb on 2007-04-30
HI There

i have a NAS (LaCie) and i mount it using

sudo mount -t smbfs -o credentials=/home/user/.credentials,uid=username,gid=username //NAS/username /home/username/MyDocuments

and it works....

but not for long. After a while it invariably hangs. I have to umount the drive (sudo umount -l /home/usernmae/MyDocuments) and mount it again.

What is going on. This is driving me real crazy!

Regards
Rein

---

### Post by Churnd on 2007-04-30
Does it happen on any other machine?  That would be the first step to determin if it's your machine or the NAS.

---

### Post by rvdb on 2007-04-30
it happens on my laptop as well (same OS... Ubuntu 7.04)

never happens from a windows machine (although tend to spend as long 5 minutes with that machine...)

Rein

---

### Post by dmizer on 2007-04-30
try cifs instead:
```
sudo mount -t cifs -o //NAS/username /home/username/MyDocuments credentials=/home/user/.credentials,file_mode=0777,dir_mode=0777
```

---

### Post by rvdb on 2007-04-30
thanks i wil try

i did in the past but without the file_mode en dir_mode options. I gave up because when mounting as root the fiiles are owned by root, not me. Is that what file and dir mode remedy?

Rein

---

### Post by dmizer on 2007-04-30
it should ... yes.  but if it doesn't, cifs can make use of similar options to uid, gid options in smbfs.

---

