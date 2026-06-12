---
title: "mount fat partition via command-line"
date: 2010-09-05
forum: New to Ubuntu
---

### Post by feddozz on 2010-09-05
Hello ladies and gents,

I need to mount a FAT partition on my ubuntu 10.4. It works when clicking on Places -> E:
I tried typing 
```
sudo mount /dev/sda5 /media/E_/
```
and i got this error
```
fuse: failed to access mountpoint /media/E_/: No such file or directory
```
E_ is the folder that's normally used when I do places -> E:.

Can you please help me? I looked for posts on this but I did not ifnd anything specific. 

Do I need to do this first?
```
mkdir /media/E_/
```

Tnx

---

### Post by HermanAB on 2010-09-05
Howdy,

The /media directory is used for automounting and the directories used as mount points are dynamic - they get deleted when a device is unmounted.

If you want to mount something manually, use the /mnt directory:
$ sudo mkdir /mnt/e
$ sudo mount  /dev/sda5 /media/e

---

### Post by c9-3Rr0r on 2010-09-05
yes u need to make that dir before executing mount command 
also u should add -t vfat to mount command

```

sudo mount -t vfat /dev/sda5 /media/E_/

```

---

### Post by feddozz on 2010-09-05
Great!
It obviously worked.
Tnx

---

