---
title: "CIFS PC shutdown problem"
date: 2008-11-06
forum: Networking &amp; Wireless
---

### Post by tomcheng76 on 2008-11-06
Hello,
i am using Ubuntu 8.10 AMD64
i mount samba share with fstab using cifs
```
//192.168.0.2/Music                       /media/music   cifs    rw,_netdev,credentials=/root/.creds,iocharset=utf8,rsize=16384,wsize=57344 0 0
```

If the 192.168.0.2 PC shutted down already and i didn't unmount before the PC shutdown, all file manager will refuse to open due to unaccessible drive. Even reboot will wait the umount. It may require hard reset.

How to fix this stupid problem?

Thanks

---

### Post by tomcheng76 on 2008-11-06
bump~

---

