---
title: "ntfs-3g query"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by ArtificialDream on 2009-03-02
1. i haven't yet installed ntfs-3g in my pc (ibex) and i can already save/delete/view my fuseblk partition. if so, what's ntfs-3g for?

2. i tried downloading konqueror using the terminal command. then, i accidentally closed the terminal window. i was wondering where the files are so that i could remove them since it's bothering me that there are files that are part of an unfinished download in my pc.

---

### Post by ArtificialDream on 2009-03-02
edit bump.

---

### Post by stchman on 2009-03-02
> **ArtificialDream said:**
> 1. i haven't yet installed ntfs-3g in my pc (ibex) and i can already save/delete/view my fuseblk partition. if so, what's ntfs-3g for?

2. i tried downloading konqueror using the terminal command. then, i accidentally closed the terminal window. i was wondering where the files are so that i could remove them since it's bothering me that there are files that are part of an unfinished download in my pc.

The ntfs-3g is installed by default on Ubuntu Hardy and later.  When you add NTFS drives in your fstab using the ntfs is the same as using ntfs-3g flag.  If you do not want to have an NTFS drive written to use the ro option.

---

### Post by blueridgedog on 2009-03-02
I believe if you install the tool now, it will only add a gui.

---

### Post by ArtificialDream on 2009-03-07
thanks for the responses.  however, to tweak my partition to auto mount everytime i log in must be done on the terminal still.

---

### Post by blueridgedog on 2009-03-08
To mount it permanently, you will need to put the mount parameters in the file /etc/fstab.  You can edit the file with:

```
gksudo gedit /etc/fstab
```

Then add a line such as:

```
/dev/sdc2 /mnt/Backup ntfs-3g defaults,locale=en_US.UTF-8 0 0
```

Change /dev/sdc2 to what your partition is and change /mnt/Backup to where you want the drive mounted.

---

### Post by Paqman on 2009-03-08
> **blueridgedog said:**
> To mount it permanently, you will need to put the mount parameters in the file /etc/fstab.

The package ntfs-config can do this for you if you want a nice GUI, btw. No need to be manually messing about with config files.

---

