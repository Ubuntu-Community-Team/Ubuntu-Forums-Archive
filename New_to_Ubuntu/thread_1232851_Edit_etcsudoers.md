---
title: "Edit /etc/sudoers"
date: 2009-08-06
forum: New to Ubuntu
---

### Post by ubudog on 2009-08-06
Hi, I typed: sudo gedit /etc/sudoers and it still says "Read Only"  Any ideas?  Thanks! :)

---

### Post by aysiu on 2009-08-06
The proper command is ```
sudo visudo
``` not ```
sudo gedit /etc/sudoers
``` By the way, not a big deal with Gedit in particular, but it's a good habit to get into to use *gksudo* with graphical applications instead of *sudo*; e.g., ```
gksu gedit /etc/sudoers
```

---

### Post by ubudog on 2009-08-06
> **aysiu said:**
> The proper command is ```
sudo visudo
``` not ```
sudo gedit /etc/sudoers
``` By the way, not a big deal with Gedit in particular, but it's a good habit to get into to use *gksudo* with graphical applications instead of *sudo*; e.g., ```
gksu gedit /etc/sudoers
```

Ok.  Thanks! :)

---

### Post by binbash on 2009-08-06
[http://www.ubuntu-inside.me/2009/07/howto-add-user-to-sudoers-list-on.html](http://www.ubuntu-inside.me/2009/07/howto-add-user-to-sudoers-list-on.html)

---

### Post by jpkotta on 2009-08-06
> **binbash said:**
> [http://www.ubuntu-inside.me/2009/07/howto-add-user-to-sudoers-list-on.html](http://www.ubuntu-inside.me/2009/07/howto-add-user-to-sudoers-list-on.html)

Why wouldn't you just add the user to the admin group?
```
sudo adduser jpkotta admin
```

---

### Post by ubudog on 2009-08-06
> **jpkotta said:**
> Why wouldn't you just add the user to the admin group?
```
sudo adduser jpkotta admin
```

The user is in the admin group.  But the other responses got it.  Thanks! :)

---

### Post by ubudog on 2009-08-06
> **aysiu said:**
> The proper command is ```
sudo visudo
``` not ```
sudo gedit /etc/sudoers
``` By the way, not a big deal with Gedit in particular, but it's a good habit to get into to use *gksudo* with graphical applications instead of *sudo*; e.g., ```
gksu gedit /etc/sudoers
```

This got it.  Thanks! :D

---

