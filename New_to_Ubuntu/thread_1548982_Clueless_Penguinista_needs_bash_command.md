---
title: "Clueless Penguinista needs bash command"
date: 2010-08-09
forum: New to Ubuntu
---

### Post by nnjond on 2010-08-09
Hi,

I need to add into /etc/modprobe.d/blacklist.conf

```
 blacklist nouveau
```

I understand Blacklist.conf is a text file to which i add the above line; So i need to know the commands to open, edit and save.

Thanks for your time.

---

### Post by Bachstelze on 2010-08-09
```
sudo nano -w /etc/modprobe.d/blacklist.conf
```

Or if you want a graphical editor:

```
gksudo gedit /etc/modprobe.d/blacklist.conf
```

---

