---
title: "install folder."
date: 2010-02-17
forum: New to Ubuntu
---

### Post by jmviles on 2010-02-17
I'm a fresh user of karmic and I was wondering how I can change where aptitude installs new programs.  I have a pretty small hard drive on my laptop, but I have an external drive where I would like to install all my big programs (games etc.)  Any advice on how to do this would be greatly appreciated. 

Thanks

---

### Post by cariboo on 2010-02-17
Linux doesn't work that way, most programs are installed in /usr and it's sub-directories. If you are running out of space on your hard drive, make sure you clear out the archived packages in /var/cache/apt/archives. You can do this by opening an Applications->accessories->Terminal and type:

```
sudo apt-get clean
```

Another idea, if you never disconnect your external drive is to move your home directory to it.

---

### Post by achase79 on 2010-02-17
Linux installs the programs in specific places.  You can create a partition and set the /home directory as the mountpoint for that partition.  This is relatively easy to do upon installation, and less easy but not impossible after installation.

---

