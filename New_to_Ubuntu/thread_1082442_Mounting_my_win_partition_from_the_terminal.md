---
title: "Mounting my win partition from the terminal"
date: 2009-02-27
forum: New to Ubuntu
---

### Post by m4lte on 2009-02-27
Hey guys,

I do not mount my win partition on boot, though it appears in the Nautilus side bar and I can mount it by clicking on it.

I want to write a script that mounts the partition and gets some files from it. How can I easily mount it from the terminal?
blkid returns this:
/dev/sda2: UUID="988E517D8E5154BA" LABEL="windows" TYPE="ntfs" 

I do not have the partition in my fstab. Can I include it in the fstab without it automatically getting mounted during start up?

cheers!

---

### Post by taurus on 2009-02-27
```
sudo mkdir /media/sda2
sudo mount -t ntfs-3g /dev/sda2 /media/sda2
df -h
```

---

### Post by m4lte on 2009-02-27
Thanks!

---

### Post by geirha on 2009-02-27
> **m4lte said:**
> 
/dev/sda2: UUID="988E517D8E5154BA" LABEL="windows" TYPE="ntfs" 

I do not have the partition in my fstab. Can I include it in the fstab without it automatically getting mounted during start up?

cheers!

Putting it in the fstab is a good idea. Try with this line:
```
UUID="988E517D8E5154BA" /media/sda2 defaults,noauto,user 0 0
```

The noauto option will make it not mount automatically during boot, and the user option allows regular users to mount it, so after adding that line you can do run the following (without sudo) to mount it ```
mount /media/sda2
```

---

