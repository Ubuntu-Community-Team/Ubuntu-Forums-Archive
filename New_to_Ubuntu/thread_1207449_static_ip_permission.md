---
title: "static ip permission"
date: 2009-07-08
forum: New to Ubuntu
---

### Post by benh13 on 2009-07-08
when trying to edit /etc/network/ interfaces to gain a static ip, i can't get permission to save the file? how can i get permission?

---

### Post by Gazneth on 2009-07-08
Sounds like you are not opening with admin authority, use sudo before your command, an example is:```
sudo gedit /etc/network/interfaces
```

Now if you are trying to open your file graphically, use the command for a root nautilus window first.```
gksudo nautilus
```

---

