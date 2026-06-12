---
title: "how to set up multiple share using samba?"
date: 2008-08-11
forum: Networking &amp; Wireless
---

### Post by mahela007 on 2008-08-11
Hi.. I have already set up samba according to the tutorial at [http://ubuntuforums.org/showthread.php?t=202605]("http://ubuntuforums.org/showthread.php?t=202605"). I want to know how I can set up multiple sharing folders

---

### Post by dmizer on 2008-08-11
Hello, please try to refrain from making so many new samba share related threads. It's much easier for those of us trying to help you if we only have to follow one thread.  For help related to the howto, it's best to simply post in the howto.

For multiple shares, just add a new "myfiles" section to the bottom of smb.conf like so:
```
[MyFiles-one]
    path = /media/myfiles-one/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = YOUR_USERNAME
    force group = YOUR_USERGROUP

[MyFiles-two]
    path = /media/myfiles-two/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = YOUR_USERNAME
    force group = YOUR_USERGROUP
```

---

### Post by mahela007 on 2008-08-11
Thanks. I will follow your advice.. sorry about all the extra threads

---

