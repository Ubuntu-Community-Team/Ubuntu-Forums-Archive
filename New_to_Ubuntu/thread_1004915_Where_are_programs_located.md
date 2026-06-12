---
title: "Where are programs located?"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by tegnoto89 on 2008-12-07
I need to choose a program to open my torrent files (I use KTorrent), and it opens a box for me to locate the program, but I have no idea where to look.  What do I do?

Thanks!

---

### Post by rhcm123 on 2008-12-07
> **tegnoto89 said:**
> I need to choose a program to open my torrent files (I use KTorrent), and it opens a box for me to locate the program, but I have no idea where to look.  What do I do?

Thanks!
It should be on the list. If not, look in /bin.

---

### Post by residualbit on 2008-12-07
Type this in the terminal:
```
whereis ktorrent
```

it will display the path.

---

### Post by taurus on 2008-12-07
Usually in /usr/bin.

---

### Post by rhcm123 on 2008-12-07
> **tegnoto89 said:**
> I need to choose a program to open my torrent files (I use KTorrent), and it opens a box for me to locate the program, but I have no idea where to look.  What do I do?

Thanks!

wait a minute, dosent transmission come bundled with kubuntu?

---

### Post by scorp123 on 2008-12-07
> **rhcm123 said:**
> wait a minute, dosent transmission come bundled with kubuntu? Transmission is a GNOME program last time I checked ;) Kubuntu is using KDE as desktop so I'd assume it uses ktorrent ...

---

### Post by Paqman on 2008-12-07
On Linux you don't need to specify the whole path to launch a program. Just use the package name (eg: ktorrent, tranmission) and the system will figure out the rest.

---

### Post by oldos2er on 2008-12-07
> **tegnoto89 said:**
> I need to choose a program to open my torrent files (I use KTorrent), and it opens a box for me to locate the program, but I have no idea where to look.  What do I do?

Thanks!

/usr/bin/ktorrent

---

### Post by Bölvaður on 2008-12-07
note that this is not the place where the actual program is located, this is only a place used for easy access (lunchers(shortcuts), autofill in the terminal)

everything in that directory can be executed by simply typing in the name of the file.

---

