---
title: "File Permissions for a partition"
date: 2009-11-14
forum: New to Ubuntu
---

### Post by TironN on 2009-11-14
Hey, I currently only have read permission to an internal partition mounted to /media/bigd
I really need to change it so i can write, how would I go about this? (Its FAT32 by the way)

Thanks, Fergus!

---

### Post by ddnev45 on 2009-11-14
If it's just for you you, you can change the ownership with the chown command. In a terminal:

```
sudo chown <your user name> /media/bigd
```

If it's for everyone, you can use chmod. In terminal:

```
sudo chmod 777 /media/bigd
```

The chmod option will give read-write-execute permissions to everyone -- not always the most secure option.

There are probably some GUI ways to accomplish this, but I haven't used Gnome or KDE in so long, I can't help you there.

You can also edit your /etc/fstab file -- search through the "Tutorials and Tips" forum for some good examples of how to edit /etc/fstab.

---

