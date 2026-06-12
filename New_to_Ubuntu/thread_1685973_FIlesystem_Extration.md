---
title: "FIlesystem Extration"
date: 2011-02-11
forum: New to Ubuntu
---

### Post by TitansWrath on 2011-02-11
Hie iam new to ubuntu 10.10 and i would like to install the driver of my wireless card i.e Intel Wifi 5100 i have the driver extracted but i want to put the extracted file in the filesystem. whenever i do that it says "You dont Have Permission" please help i really wanna know how to ???

---

### Post by cariboo on 2011-02-11
Are you sure there isn't a driver already loaded for your wireless device? Open an Applicaions->accessories->Terminal and type:

```
sudo lshw -C network
```

and paste the results in your next post.

If you need to install the driver, you should extract it in your home directory, and run the installation script as root eg:

```
sudo make install
```

---

