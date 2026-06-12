---
title: "Mounting samba shares with write"
date: 2007-05-25
forum: Networking &amp; Wireless
---

### Post by mortuk on 2007-05-25
Hey all, managed to get samba shares with write access working using the credentials method in the /etc/fstab

```
sudo mount -t cifs //netbiosname/sharename /media/sharename -o username=winusername,password=winpassword,iocharset=utf8,file_mode=0777,dir_mode=0777
```

Anyways it works, but whenever I copy a file into the directory it has read only on so I cant edit it, any ideas?

Cheers

---

