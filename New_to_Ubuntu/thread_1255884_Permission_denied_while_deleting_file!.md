---
title: "Permission denied while deleting file!"
date: 2009-09-02
forum: New to Ubuntu
---

### Post by L33Tsauce on 2009-09-02
I want to delete a file ( /var/cache/apt/archives/ ttf-mscorefonts-installer_2.6_all.deb) but i get permission denied HOW CAN I STOP THIS!

---

### Post by Finalfantasykid on 2009-09-02
Try typing...

```
gksu nautilus
```

and then try deleting the file.  Chances are you just need root access.

---

### Post by mprince on 2009-09-02
Type this command in terminal and it should clean out your apt cache.

> sudo apt-get clean

---

### Post by 3rdalbum on 2009-09-02
> **L33Tsauce said:**
> I want to delete a file ( /var/cache/apt/archives/ ttf-mscorefonts-installer_2.6_all.deb) but i get permission denied HOW CAN I STOP THIS!

The reason you got "permission denied" is because only root can modify files that are outside your home directory. This is normal behaviour, and it's part of the Linux security system.

You can run a single command as root, like this:

```
sudo rm /var/cache/apt/archives/ttf-mscorefonts-installer_2.6_all.deb
```

Or you can launch a file browser window as root:

```
gksudo nautilus
```

Use "sudo" before a command to run it as root. When you want to run graphical programs as root, use "gksudo" instead.

---

