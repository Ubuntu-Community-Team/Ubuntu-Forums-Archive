---
title: "[SOLVED] unable to create folders"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by einfinger on 2008-12-19
on one of my drives when i right click the option for create folder is grey, there seem to be no way to create files and folders there. Anyone know what might be wrong ?

---

### Post by JoshuaRL on 2008-12-19
What is the drive, and where are you trying to create folders?  It just might be a permission problem.

---

### Post by einfinger on 2008-12-19
its the second drive on a laptop, not a partition. /dev/sdb1/

and im trying to create in the root of the drive, not /root or anything :P just on the root of the drive.

---

### Post by SuperSonic4 on 2008-12-19
I suspect you'd have to be root, you can create in the terminal using ```
sudo mkdir /dev/sbd1/<folder>
```

or launch nautilus as root: ```
gksu nautilus
``` and go from there

---

### Post by einfinger on 2008-12-19
but do i have to run nautilus everytime ?

---

### Post by JoshuaRL on 2008-12-19
> **einfinger said:**
> but do i have to run nautilus everytime ?

Only if you want to have write permissions.  You also could try Launching Nautilus like that and right-click the icon for that drive.  Then go into Preferences, go to the Permissions tab, and change it to write access for anyone you want.

---

### Post by atomizer on 2008-12-19
you can find out who the owner of the drive is
(I think it is root at the moment)

```
ls -l /path/to/second/drive
```

and change it to you as owner

```
sudo chown -R you /path/to/second/drive
```

---

### Post by einfinger on 2008-12-19
thank you, that did the trick. Just put permissions on to my user. :)

---

