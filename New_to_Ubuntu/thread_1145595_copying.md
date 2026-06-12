---
title: "copying"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by jj3502 on 2009-05-01
how do i copy to /usr/share/gnome-screensaver/ it says permission denied

i also need to create a folder in /usr/share/icons

thanks in advance

(ubuntu 8.04)

---

### Post by Didius Falco on 2009-05-01
You need to have root privileges to do things in system areas. If you want to do it through Nautilus (the file manager) you can open a Terminal windows and type```
 gksudo nautilus
```

You can also do it from the command line (straight from the Terminal shell) by using sudo, but it sounds like you are pretty new at this.

Be very careful using sudo - as root, you can do anything, including destroying your whole install.

---

### Post by jj3502 on 2009-05-01
thx (by the way, im using vm were to play and test ubuntu)

---

### Post by zvacet on 2009-05-01
For create folder for example let say it is named **myfolder**

```
mkdir /usr/share/icons/myfolder
```

For copy files 

```
sudo cp file_name /usr/share/gnome-screensaver/
```

---

