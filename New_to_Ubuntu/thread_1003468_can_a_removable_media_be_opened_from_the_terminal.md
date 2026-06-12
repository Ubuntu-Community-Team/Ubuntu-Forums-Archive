---
title: "can a removable media be opened from the terminal"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by rburkartjo on 2008-12-06
i know i can do this places/removable media/280.7 GB media and this will mount the the 280.7 GB media. however is there a way of doing this from the terminal./tks cheesemaker

---

### Post by Nepherte on 2008-12-06
Yes you can. The command to use is mount. Typical use of mount is:
```
mount -t filesystemtype devicetomount dir
```
Note that the directory (dir) has to exist before you try to mount.
For more information about mount:
```
man mount
```

For example, when I want to mount my external disk, I do this:
```
sudo mount -t vfat /dev/sdc1 /media/MyBook
```

---

