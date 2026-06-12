---
title: "Renaming mounted media  and changing icons."
date: 2010-12-04
forum: New to Ubuntu
---

### Post by bvpainter on 2010-12-04
I have a Seagate external hard drive for back up, and have a separate formatted partition. These both show up on my desktop as the same icon and are both called "New Volume". I've tried renaming them and changing the icons, but do not seem to be able to find a way of doing this.

Can anyone help.:p

---

### Post by NightwishFan on 2010-12-04
In the System -> Administration -> Disk Utility I think you can label the filesystem. Though it always shows up in all caps for me. I am sure there is another way to do it without formatting but I am unsure how, sorry. :(

---

### Post by karthick87 on 2010-12-04
Also you can use Gparted-Partition Manager to rename the label of the file system.

```
sudo apt-get install gparted
```

Just open gparted,unmount the partition before renaming the label.And then right click the partition and choose Label to create a new one and press ok.After renaming goto edit menu and select Apply all Operations.

---

### Post by bvpainter on 2010-12-04
I tried using Gparted but it will not unmount the drive. It immediately re-mounts it when I press unmount.


> **karthick87 said:**
> Also you can use Gparted-Partition Manager to rename the label of the file system.

```
sudo apt-get install gparted
```

Just open gparted,unmount the partition before renaming the label.And then right click the partition and choose Label to create a new one and press ok.After renaming goto edit menu and select Apply all Operations.

---

### Post by NightwishFan on 2010-12-04
Gparted is a better choice. Run it from a live cd session of Ubuntu :)

---

### Post by bvpainter on 2010-12-04
I'll try this. 

> **NightwishFan said:**
> Gparted is a better choice. Run it from a live cd session of Ubuntu :)

---

