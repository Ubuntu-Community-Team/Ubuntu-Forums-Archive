---
title: "/etc/network/interfaces  Permissions"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by Samerious on 2009-02-02
How do I get permission to this file to edit and save?

---

### Post by Kobalt on 2009-02-02
Press Alt+F2 and enter : 
```
gksudo gedit /etc/network/interfaces
```

Beware, you will be editing an important file, **make a backup before modifying anything.**

---

### Post by Praxicoide on 2009-02-02
Either:
1.- "Gksudo" and the name of your editor, followed by the name of your file.

The defaults are:

On Ubuntu:

```
gksudo gedit /etc/network/interfaces
```

on Kubuntu:

```
gksudo kate /etc/network/interfaces
```

on Xubuntu:

```
gksudo mousepad /etc/network/interfaces
```

2.- "Sudo" followed by the name of the terminal text editor, most likely

```
sudo nano /etc/network/interfaces
```

I don't need to tell you that you have to be careful with this file, since you can break stuff like network manager. It's always a good idea to make a backup, just in case:

```
sudo cp /etc/network/interfaces /etc/network/interfaces.backup
```

That way, if you mess up, you can just do the opposite to get your original configuration:

```

sudo rm /etc/network/interfaces
sudo cp /etc/network/interfaces.backup /etc/network/interfaces 
```

---

