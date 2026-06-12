---
title: "iPod touch setup"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by Intell on 2008-12-15
Hello,
I'm currently trying to figure out how to set up my iPod touch on kubuntu. I'm currently running fw2.0 on my ipod. I've installed ipod-convenience and entered the ip of my ipod. Ssh is working fine on my ipod. If I do not sudo I get this message: ```
touch: cannot touch `/media/ipod/test': Permission denied
Unable to write to /media/ipod.  Please adjust permissions and try again.

```
So, I sudo and get this message: ```
Please add yourself to the fuse group, logout/in and try again.

```
I'm in the fuse group:
```

username adm dialout cdrom plugdev fuse lpadmin admin sambashare
```

Why isn't this working correctly?
Thanks

---

### Post by Nepherte on 2008-12-15
That is because as sudo, you're not in the fuse group anymore. If you change the ownership of the directory to your user, you won't have to use sudo anymore.
```
sudo chown yourusername /media/ipod
```

---

