---
title: "[SOLVED] evolution mail"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by som1special2 on 2008-12-24
anyone know how to save settings, mail and contacts from evolution mail? I am switching to a new HDD and would like to save the settings to a usb flash before doing it. Please explain how to install import afterwards. Thank you very much and Merry Christmas!

---

### Post by LowSky on 2008-12-24
save you files from your /home folder  

should be /home/.evolution or something simular (sorry on a windows machine at work) and then just copy them back to the same spot, when you load EVO it should just work

---

### Post by Maverick1712 on 2008-12-24
There should be a file in your home directory that starts with . so that it is hidden. Open a terminal and do 

```
ls -a
```

 to see them or browse to it using your graphical file manager and press ctrl+h. I don't know exactly what the filename should be called since I use thunderbird instead of evolution, but it should be as easy as moving that setting file to your new home directory.

Cheers,
Adam

Edit:LowSky beat me to it, but it's basically the same thing.

---

### Post by LowSky on 2008-12-24
yeah I just forgot to mention its a hidden folder

ctrl+h to show hidden files in Nautilus file manager

---

### Post by newbee70 on 2008-12-24
> **som1special2 said:**
> anyone know how to save settings, mail and contacts from evolution mail? I am switching to a new HDD and would like to save the settings to a usb flash before doing it. Please explain how to install import afterwards. Thank you very much and Merry Christmas!

go to your home folder, click on view hidden files, copy .evolution to a removable media.

and do a evolution backup first. start evolution: in the program file menu backup, point it to your media. it will backup settings.

---

### Post by frank002 on 2008-12-24
In Evolution do the folloowing:
 Click  File>Backup settings
 This will save your settings to a file named     evolution-backup.tar.gz
save to a removable media
To restore, insert removable media,  open Evolution and click File<Restore settings.
Merry Christmas

---

