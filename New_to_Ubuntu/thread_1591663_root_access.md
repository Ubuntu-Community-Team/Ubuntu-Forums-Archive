---
title: "root access"
date: 2010-10-09
forum: New to Ubuntu
---

### Post by hduguay on 2010-10-09
I downloaded the  ubuntulooks engine and I need to get root access to copy into my themes folder. Can anyone help me with this?

---

### Post by RJ12 on 2010-10-09
If you are trying to copy a file to somewhere in your home directory then you don't need root permissions. Anywhere else you will need to open Nautilus as root.
```
gksudo nautilus /
```

Make sure in the root controlled nautilus you don't open your home folder! I would open another nautilus window as your regular user and then drag the files into the other nautilus window.

---

