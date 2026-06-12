---
title: "External media box NTFS"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by webwiller on 2009-03-06
Hi guys!
I have a media box, external hd NTFS. I would like to know what I need to install in order to safely read/write ntfs disks (my win partition too).
thx in adv!:)

---

### Post by taurus on 2009-03-06
You don't need to install anything extra.  Just plug it in and see if it's auto-mounted.  If not, you can mount it from a terminal with ntfs-3g driver.  However, remember to unmount it first before you unplug it from your computer, even in windows (_safely remove hardware_ option).

---

### Post by webwiller on 2009-03-06
I get the error "Impossible to mount the volume" as you can see in the enc screenshot and I'm not sure if it's safe to "force" the procedure.

---

### Post by taurus on 2009-03-06
Did you just unplug that harddrive from your computer the last time you used it (in windows)?

1.  Connect it back to a windows machine and use _safely remove hardware_ icon (bottom right corner) to unmount it first before you unplug it.

2.  Install ntfsprogs and use ntfsfix to fix it.

```
sudo apt-get update
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sdb1
sudo mkdir /media/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
df -h
```

3.  Or use the force option to mount it.

```
sudo mkdir /media/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force
df -h
```

---

### Post by stchman on 2009-03-06
> **webwiller said:**
> I get the error "Impossible to mount the volume" as you can see in the enc screenshot and I'm not sure if it's safe to "force" the procedure.

I have an external drive formatted in NTFS and it mounts fine in read/write mode.  You probably have a dirty file system and need to run ntfs fix utilities.

---

### Post by webwiller on 2009-03-06
It was like taurus said...just had to "safelt remove" it in win & it worked fine straight away without doing anything.
Ty all!;)

---

