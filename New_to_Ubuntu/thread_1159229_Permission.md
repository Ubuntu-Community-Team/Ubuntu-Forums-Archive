---
title: "Permission"
date: 2009-05-14
forum: New to Ubuntu
---

### Post by ibizatunes on 2009-05-14
I am setting up a computer for a friend with ubuntu, and i have copy the files using nautilus onto a usb hard drive and back using nautilus as root
the only problem is that all the files are now owned by root and i want to allow the owner of the home drive to own the files (there are alot of files and i can do it one by one!)

---

### Post by ibizatunes on 2009-05-14
```
cd '/home/adam/'
sudo chown -R adam:adam *
find -type d -exec chmod 755 {} \;
find -type f -exec chmod 644 {} \;
```


Is this right as i dont want to lose any data

---

### Post by Locutus_of_Borg on 2009-05-14
chown -R adam: /home/adam

is sufficient

---

### Post by ibizatunes on 2009-05-14
Thanks your a live saver!!

---

