---
title: "ubunt partitioner problem"
date: 2009-11-19
forum: New to Ubuntu
---

### Post by ashu. on 2009-11-19
hi i used to use ubuntu installed within in windows XP but some of my frnzforced me to change to windows 7 so i had to partition so i lost my ubuntu
now windows 7 had some boot file compressed error so i installed kubuntu 9.04 but i didnt quite like it. so i tried to install ubuntu 9.04 in same partition but the partition manager shows that there is no os loaded n its going to use complete space available but i have some files on NTFS partition of windows 7 which i can open in kubuntu.i need those files without harm how to install ubuntu????plz help

---

### Post by meson2439 on 2009-11-19
Try getting 9.10 because 6 months ago there is no windows 7. Hope it helps.

---

### Post by tarps87 on 2009-11-19
You could try removing the Kubuntu packages and installing the Ubuntu desktop.
```
sudo apt-get remove kubuntu-desktop && sudo apt-get install ubuntu-desktop
```

Failing this you can try a manual install, if you select the ext3 partition tell it to format it as ext4 and then mount / (root) here and mount swap on the swap formatted partition.

This may be useful as a refernece [http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

If you need help with a any of the partition process just post back

---

