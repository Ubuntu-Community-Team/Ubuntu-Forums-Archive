---
title: "Just installed Ubuntu desktop 16.04 and can't connect to wifi"
date: 2016-05-15
forum: Networking &amp; Wireless
---

### Post by 1two3 on 2016-05-15
I had u Ubuntu 14.04 previously but reinstalled Windows again overwriting Ubuntu and now I've just installed Ubuntu again overwriting Windows.

The only thing I've done is enable ufw.

Tried to connect to the wifi but nothing happens but it worked on Ubuntu 14.04 before. I don't have any Ethernet to try.

---

### Post by padnoter on 2016-05-15
maybe connected to the may 13th network update that cause a few problems - see the threads in this forum around yours for more info.
e.g. [http://ubuntuforums.org/showthread.php?t=2324693](http://ubuntuforums.org/showthread.php?t=2324693)

---

### Post by jeremy31 on 2016-05-15
See if the wifi works after ```
systemctl restart NetworkManager.service
```

There seems to be an issue with Network Manager and the systemd renaming of wireless

---

### Post by 1two3 on 2016-05-16
Thanks Jeremy, that worked :)

---

