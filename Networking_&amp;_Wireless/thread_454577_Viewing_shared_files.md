---
title: "Viewing shared files"
date: 2007-05-25
forum: Networking &amp; Wireless
---

### Post by clsyorkshire on 2007-05-25
Hi all,

I have some media files shared in a directory on a PC running Windows 2000.

I want to be able to play them on a pc running Ubuntu linux. All the Ubuntu apps won't let me view the shared files though, as if I try and browse using the directory SMB://JFS/Music/ it says no such directory, where JFS in the PC name and Music is the shared folder. I don't know why this doesn't work but I'm sure it used to.

---

### Post by bung33 on 2007-05-28
Restart samba first to make sure it's running...

```
sudo /etc/init.d/samba restart
```

Then use nautilus to browse your Windows network and see if you can view the computer...

---

