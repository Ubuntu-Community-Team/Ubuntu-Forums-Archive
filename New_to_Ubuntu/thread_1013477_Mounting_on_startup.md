---
title: "Mounting on startup"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by Facetious Falcon on 2008-12-16
I have an issue with my NTFS SATA hard disk in that whenever I load up the system I have to goto the 'places' menu and click on the name of the hard drive there to get it to mount.

Is there anyway of knowing what device this hard disk represents in the /dev/ folder. If I can figure that out then I can make an executable script that runs on startup hopefully, unless there's an easier way!

Cheers for the help.

---

### Post by taurus on 2008-12-16
Install ntfs-config use it to configure your ntfs partition.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

---

### Post by iaculallad on 2008-12-16
On your terminal, issue the command below:

```
sudo fdisk -l
```

---

### Post by Facetious Falcon on 2008-12-16
Thanks!

Nice and quick as well!

---

