---
title: "View system specs?"
date: 2010-06-05
forum: New to Ubuntu
---

### Post by TriBlox6432 on 2010-06-05
In Windows I would just right click on "My Computer" and hit settings and it would tell me everything.  And also, I could navigate to my C: drive, right click, properties and I would be able to see exactly what size it is, and how much is used.  How do I do this in Ubuntu?

---

### Post by rraj.be on 2010-06-05
Install sysinfo and try this.This will give everything you need.

To install sysinfo

```
sysinfo
```

```
sudo apt-get install sysinfo
```

To look at memory of disk you can use

```
sudo fdisk -l
```

Try this friend. 

```
sudo lshw
```


You can also use Partion manager to view details and edit memory as shown in Disk management Console of windows.

```
sudo gparted
```

But you may need to install gparted before you use.
To install Gparted use this
```
sudo apt-get install gparted
```

---

### Post by Phrea on 2010-06-05
> **rraj.be said:**
> ```
sudo lshw
```

Sudo for lshw?

---

