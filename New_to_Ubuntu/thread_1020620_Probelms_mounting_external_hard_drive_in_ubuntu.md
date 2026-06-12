---
title: "Probelms mounting external hard drive in ubuntu"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by letters on 2008-12-24
Before I installed Ubuntu I was running the live cd. I would turn on my external hard drive and it would mount with no problem. Now I installed Ubuntu, but when I turn on the external hard drive I get this error:

[IMG]http://img32.picoodle.com/img/img32/3/12/24/f_mounterrorm_4b71fac.png[/IMG]

:confused:

---

### Post by taurus on 2008-12-24
Looks like the last time you used that external harddrive, you didn't go into Safely Remove Hardware option first; instead, you just unplugged it from a machine.  So, you can either plug it back into a windows machine and use the safely remove hardware icon on the bottom right to unmount it first or you can use the force option to mount it in Ubuntu.

Applications -> Accessories -> Terminal
```
sudo mkdir /media/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force
df -h
```

---

### Post by letters on 2008-12-24
Thank you very much taurus. You are knowledgeable and very helpful. 

;)

---

### Post by letters on 2008-12-24
One last question. To safely unmount in Ubuntu. Do I right click the drive. Unmount?

---

### Post by halitech on 2008-12-24
right click -> unmount or eject

depends on the type of drive but should be used for all external drives and cdroms

---

### Post by taurus on 2008-12-24
Yes.  You can do that from your desktop or you run unmount it from a terminal.

```
sudo umount /media/sdb1
```

---

### Post by letters on 2008-12-24
Thank you again.

---

