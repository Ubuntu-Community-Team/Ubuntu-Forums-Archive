---
title: "Porting over programs to run on ubuntu"
date: 2010-07-10
forum: New to Ubuntu
---

### Post by WubiNoob on 2010-07-10
I am running 10.04 along with Vista using wubi on my laptop, and I can't install programs directly to ubuntu because the wifi driver does not work with ubuntu yet. I can go to numerous websites on Vista, and download programs, then I use a flash drive to bring then into ubuntu, and this is where things don't work.
The files have a .deb extention, and when I go to open them in archive manager, it just gives me more .deb packages! 

Is there a way to bring .deb packages to ubuntu and install them that way? Thanks.

---

### Post by yetiman64 on 2010-07-10
Installing programs in Ubuntu using .deb packages requires the package to be opened with gdebi installer not the archive manager. 

Just double clicking them in Ubuntu should by default use the gdebi package installer. 

If archive manager is set as the default, right click the .deb file and select Properties > Open With tab, and choose GDebi Package Installer and try again.

---

### Post by mike555 on 2010-07-10
Many files have dependencies , you might need to download them also .

---

