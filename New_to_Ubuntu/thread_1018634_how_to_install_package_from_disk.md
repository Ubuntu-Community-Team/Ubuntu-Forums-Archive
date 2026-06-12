---
title: "how to install package from disk?"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by professor1 on 2008-12-22
I need to install build-essential but without a network connection, any ideas?

---

### Post by Duck2006 on 2008-12-22
This may help. It is a bit old but the install will be the same.

[http://ubuntuforums.org/showthread.php?p=6353549](http://ubuntuforums.org/showthread.php?p=6353549)

---

### Post by taurus on 2008-12-22
The build-essential package is on the install disc.  Insert it into a drive, open a terminal, and then run

Applications -> Accessories -> Terminal
```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by professor1 on 2008-12-22
Just one more point, if I saved all the files from 

/var/cache/apt/archives

is there  a way to install packages from a directory

e.g.

/mnt/sda5/saved_deb_files_from_var-cache-apt-archives

---

### Post by oldos2er on 2008-12-22
> **professor1 said:**
> Just one more point, if I saved all the files from 

/var/cache/apt/archives

is there  a way to install packages from a directory

e.g.

/mnt/sda5/saved_deb_files_from_var-cache-apt-archives

 Yes, use the command "sudo dpkg -i /mnt/sda5/saved_deb_files_from_var-cache-apt-archives/*.deb"

---

