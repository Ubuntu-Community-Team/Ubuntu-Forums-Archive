---
title: "Partitioning my Hard drive"
date: 2011-02-15
forum: New to Ubuntu
---

### Post by hard knock on 2011-02-15
What are the steps for partitioning my hard drive in UBUNTU

---

### Post by TeoBigusGeekus on 2011-02-15
1)Boot up with a live cd so that you whole hard drive is available (not mounted) for partitioning.

2)Lauch gparted as root
```
gksu gparted
```
If you don't have it, install it
```
sudo apt-get install gparted
```

...and that's it.

---

