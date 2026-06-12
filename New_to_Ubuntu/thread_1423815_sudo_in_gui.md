---
title: "sudo in gui ?"
date: 2010-03-07
forum: New to Ubuntu
---

### Post by anatak on 2010-03-07
Is it possible to open a file from the gui with sudo ?
I would like to edit the php.ini file but would prefer not to do it with vi.

I would like to edit it with gedit
is there a way to browse to the file using the gui and then open it as root or do I have to use terminal ?

---

### Post by ibuclaw on 2010-03-07
> **anatak said:**
> Is it possible to open a file from the gui with sudo ?
I would like to edit the php.ini file but would prefer not to do it with vi.

I would like to edit it with gedit
is there a way to browse to the file using the gui and then open it as root or do I have to use terminal ?
Press **Alt+F2** to open a run command box, then type in.
```
gksudo gedit /path/to/php.ini
```

gksu and gksudo are graphical frontends to su and sudo.

Regards
Iain

---

### Post by dnairb on 2010-03-07
For GUI apps use gksudo rather than sudo in terminal.
For example:

```
gksudo gedit /etc/fstab
```

will open the fstab file in gedit with sudo priveleges.

The terminal window will remain open, and needs to remain open, while you edit the php.ini file.

---

### Post by anatak on 2010-03-07
thank you so much
anatak

---

