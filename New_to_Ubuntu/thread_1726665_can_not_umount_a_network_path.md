---
title: "can not umount a network path"
date: 2011-04-11
forum: New to Ubuntu
---

### Post by Guruprasad on 2011-04-11
I mounted a network path smbmount.

Now I am trying to unmount using umount but no sucess.

> sudo smbmount //192.168.100.9/bhoomijabackup /media/BhoomijaBackup -o username=username,password=password,uid=1000,mask=000

umount "/media/BhoomijaBackup/"

---

### Post by seawolf167 on 2011-04-11
Add a sudo in front of your command

```
sudo umount /media/BhoomijaBackup/
```

If you have an entry in /etc/fstab it'll be mounted automatically on boot, so you'll want to remove those entries as well

---

### Post by Guruprasad on 2011-04-15
thanks it worked...

---

