---
title: "fstab: full permissions"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by TironN on 2009-11-16
hey i want to add fstab a partition in. I had it working before but read-write priviledges were only for root. I want this for all users. Its FAT32. What would I use to do this?

---

### Post by Zoot7 on 2009-11-16
```
sudo chmod -R 777 <where device is mounted>
```

Should do the job.

---

### Post by TironN on 2009-11-16
Sad to say it but I think i read somewhere that if its FAT chmod won't work... hmmmm I'll try it again though

---

### Post by CaptainMark on 2009-11-16
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
should have everything you need

adding rw will give read/write privilidge. the options are the same for mount commands so pop 'man mount' into a terminal

---

### Post by TironN on 2009-11-16
Ok.

So what I have written is:

/dev/sda2       /media/bigd     auto    rw,user,auto,exec       0       0

now it works but is still only giving root permission for write and mounting/unmounting

---

### Post by hal10000 on 2009-11-16
1.) you have to be a member of the group plugdev (gid 46 on my system). You can set this with your user-admin tool.

2.) make your fstab entry look like this:
```
/dev/sda2 /media/bigd vfat utf8,umask=007,gid=46 0       1
``` 

3.) unmount and remount /dev/sda2:
```
sudo umount /dev/sda2
sudo mount /dev/sda2
```

---

### Post by TironN on 2009-11-16
Hey, its all working finally. umask was all it needed!

---

### Post by 3rdalbum on 2009-11-16
> **TironN said:**
> Sad to say it but I think i read somewhere that if its FAT chmod won't work... hmmmm I'll try it again though

It does if you're chmodding the mount point itself, because the mount point is a folder sitting on a Linux filesystem.

---

