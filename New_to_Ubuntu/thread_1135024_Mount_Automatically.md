---
title: "Mount Automatically"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by balachandarlinks on 2009-04-24
Hai,
  I want to mount all my fat and ntfs partitions automatically when ubuntu starts up...Now every time i need to mount all the drives manually by double click them...Is there any command to do this...??
           Thk u....

---

### Post by Elfy on 2009-04-24
You can add them to /etc/fstab 

Make a folder to mount each partition on, for example /media/fat1 then you add a line to fstab referring to that partition.

Information here - [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

If you want help then please post the results of these commands

```
sudo fdisk -l
ls -al /dev/disk/by-uuid/
```

You will also need to know what each partitions needs to be called.

---

