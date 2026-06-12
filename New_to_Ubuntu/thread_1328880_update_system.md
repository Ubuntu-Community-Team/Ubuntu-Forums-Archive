---
title: "update system"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by Sheed3036 on 2009-11-16
kk im new to linux and i was wondering how i can update my system through a live cd , i have ubuntu 9.04 installed but its not working and cant accesss it,the only way i can is through terminal on a live cd, when i change directories in terminal on live cd i can get to my regularsystem through terminal, but when i do a apt-get upgrade, and apt-get install it says that files are locked and i cant update that way.   Is there anyway thet i can update through live terminal , ps i dont want to reformat the hdd thanks for ur help

---

### Post by halitech on 2009-11-16
you can't update from the live cd, only from the alternate install cds. The Live CD uses the squashfs to alow the files to run so apt will not see any files on the disk that it can use.

whats not working on your current install?

---

### Post by Sheed3036 on 2009-11-16
> **halitech said:**
> you can't update from the live cd, only from the alternate install cds. The Live CD uses the squashfs to alow the files to run so apt will not see any files on the disk that it can use.

whats not working on your current install?

[http://ubuntuforums.org/showthread.php?t=1328396](http://ubuntuforums.org/showthread.php?t=1328396)

---

