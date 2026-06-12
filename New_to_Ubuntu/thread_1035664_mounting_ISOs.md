---
title: "mounting ISOs"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by Zopiac on 2009-01-10
How do i mount an .iso file? I tried just saying 'mount /path/to/iso.iso' but it told be that it 'cannot find /path/to/iso.iso in /etc/fstab or /etc/mtab'

I then looked online, and tried to do this: 
```
sudo mkdir /media/iso
sudo mount -o loop /path/to/iso.iso
```
but this replied the same way.

How do i do this?

---

### Post by adult swim on 2009-01-10
you can do with gui
```
sudo apt-get install gmountiso
```
it will be in applications>system tools>gmountiso

---

### Post by Vendettaseve on 2009-01-10
Acetone ISO works like magic too :)

---

### Post by Zopiac on 2009-01-10
i would prefer CLI, but if no one comes up with one its fine :)

---

### Post by donkyhotay on 2009-01-10
> **adult swim said:**
> you can do with gui
```
sudo apt-get install gmountiso
```
it will be in applications>system tools>gmountiso

I had this question myself, GUI works fine for me.

---

### Post by adult swim on 2009-01-10
```
sudo mkdir /mnt/iso
sudo mount -t iso9660 -o loop FileYouWantToMount.iso /mnt/iso


```

---

### Post by jfr1tz on 2009-01-10
in relation to the previous post and your fstab error,

you tell ubuntu to mount an iso file using loopback, but you do not specify where, so it looks in fstab to see if it is described there where it should be mounted, or gives an error otherwise. adding the mount point fixes that

---

### Post by babloo75 on 2009-01-10
Just another question related to this thread:
Is there any software for Ubuntu 8.10 which can mount various file formats used by Power iso/ Daemon Tools in Windows XP?

If its there, can u plz suggest one and also how to install it. 
Thanks in advance.

---

### Post by mkvnmtr on 2009-01-10
Power iso and Aceton Iso are both free downloads for linux. You will need to google there sites and follow their instructions. There are other tools in the repositories that will help also. It takes a bit of study and searching and downloading dependencies but in the end it is worth it. There will be nothing that you can;t do better than in Windows.

---

