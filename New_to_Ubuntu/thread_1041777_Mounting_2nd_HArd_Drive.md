---
title: "Mounting 2nd HArd Drive"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by dragonwolf on 2009-01-16
Hey Guys,

I know there is a way to do it yet I have yet to find a working solution. I am running Ubuntu 8.10 and am trying to get it tow where when I boot up my Windows HD automounts w/ the 3 folders in it that I want shared-shared.

What I am having to do right now is once I get logged in I have to go to places-Removable-and select the drive then recreate my shares everytime this while working is simply not acceptable, please help!

---

### Post by taurus on 2009-01-16
If you want to mount windows partitions when you boot Ubuntu, you need to add some entries in /etc/fstab so they would be mounted automatically.  Are those partitions ntfs?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

If they are, you can use ntfs-config to configure them.

```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

---

### Post by Miljet on 2009-01-16
You need to add an entry to /etc/fstab file to automount. This link may help.

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by dragonwolf on 2009-01-24
Well Guys seems between the two of you my issue with the 2nd HD has been solved now on to the next issue mounting network shares on startup, lol

---

