---
title: "home directory"
date: 2008-11-20
forum: Networking &amp; Wireless
---

### Post by Fitz_the_gap on 2008-11-20
Hi, how would you go about locating a users home directory on a windows server so their application data roams with them?

---

### Post by scorp123 on 2008-11-20
> **Fitz_the_gap said:**
> Hi, how would you go about locating a users home directory on a windows server so their application data roams with them? Does it really have to be Windows? If not, e.g. if an Ubuntu server that offers the same features would be OK as well, I'd go with this guide:
[http://ubuntuforums.org/showthread.php?t=640760](http://ubuntuforums.org/showthread.php?t=640760)

Other than that you'd have to google "Likewise Open". That package will allow a Linux machine to join a Windows AD Domain. You'd have to place the /home/* directories on remote shares that the Linux client would have to mount upon login.

---

### Post by Fitz_the_gap on 2008-11-20
Hi, I'm currently using likewise open for validation with our windows domain and have them mount their windows home folders via PAM. But all application data stays in the the Ubuntu home folder therefor remains on the local machine. What I need is for the app data to mount to their windows home folder on the server.
cheers
fitz

---

### Post by Fitz_the_gap on 2008-11-20
Silly me, all I needed to do was change the mount location in the pam_mount.conf.xml file from:

mountpoint="~/home"  to  mountpoint="~/"

This mounted the home folder on the windows server.

Cheers
Fitz

---

### Post by Fitz_the_gap on 2008-11-25
Well as far as mounting the home directory on a windows server is concerned, it has caused a couple of issues. Firstly firefox has problems with its .mozilla directory on a windows partition and secondly open office is also experiencing problems when opening files. Conclusion, It would have been nice to have a roaming profile type ubuntu set up but it obviously still has some issues when using windows servers. All settings will have to be preconfigured leaving no room for editing personal preferences for certain programs.

---

