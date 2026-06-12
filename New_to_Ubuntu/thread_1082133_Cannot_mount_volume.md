---
title: "Cannot mount volume"
date: 2009-02-27
forum: New to Ubuntu
---

### Post by I Use Dial on 2009-02-27
My Windows partition has become corrupted and I cannot open Windows.  Running Linux I can't open any of the other partitions and I get this message:

$logFile indicates unclean shutdown (0, 0) failed to mount '/dev/sdb1': Operation not supported Mount is denied because NTFS is marked to be in use. Choose one action: Choice 1: if you have Windows then disconnect the external devices by clicking on the 'Safely Remove Hardware' icon in the Windows taskbar then shutdown Windows cleanly. Choice 2: if you don't have Windows then you can use the 'force' option for your won responsibility. For example type on the command line: mount -t ntfs -3g /dev/sdb1 /media/disk -o force Or add the option to the relevant row in the /etc/fstab file: /dev/sdb1 /media/disk ntfs -3g force 0 0

I Choice 2 but it says invalid option -- 3

Can someone help me?

---

### Post by SuperSonic4 on 2009-02-27
You may need to create the directory in media first

```
sudo mkdir /media/disk
```

```
sudo mount -t ntfs-3g /dev/sdb1 /media/disk -o force
```

---

### Post by taurus on 2009-02-27
Or

```
sudo apt-get update
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sdb1
sudo mkdir /media/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
df -h
```

p.s.  There shouldn't be a space between ntfs and -3g.

---

### Post by I Use Dial on 2009-02-27
> **taurus said:**
> p.s.  There shouldn't be a space between ntfs and -3g.

Aha, that's what threw me off.

Thanks!

---

