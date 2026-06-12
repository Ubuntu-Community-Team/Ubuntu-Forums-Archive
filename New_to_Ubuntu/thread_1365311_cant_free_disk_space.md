---
title: "cant free disk space"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by pingdoc on 2009-12-27
Hi guys, i am new to ubuntu and my laptop has run out of disk space. the issue is that whenever i empty the trash, the folders are not being permanently deleted. please help:confused:

---

### Post by cariboo on 2009-12-27
You may have to empty root's trash too. Run nautilus as root and empty the trash. Press Alt-F2 and type:

```
gksudo natilus
```

The above command will open the file manager as root and allow you to empty root's trash.

Another thing you can do to free up hard drive space is to remove the archived packages in /var/cache/apt/archives, by opening an Applications-->Accessories-->Terminal and type:

```
sudo apt-get autoremove
```

to get rid of unneeded dependencies and:

```
sudo apt-get clean
```

to remove the archived packages.

---

### Post by diablo75 on 2009-12-27
Be very careful not to delete something by mistake while running nautilus as root or you could royally screw your system up.

---

### Post by warfacegod on 2009-12-27
You may want to try terminal command: sudo tune2fs -m 1 /dev/sda1

By default, ubuntu reserves 5% of a drive for itself. The above command will change that to 1%. Or,if you prefer, change the first 1 to whatever you like (I use 0%).

Assuming you have a 100 GB drive and you go with 1%, that should free up roughly 4 GB.

Might I suggest, by the way, buying an external hard drive and transfering some files to it.

---

### Post by sliketymo on 2009-12-27
that should be : gksudo nautilus.

---

