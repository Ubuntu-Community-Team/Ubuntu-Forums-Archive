---
title: "General noob question"
date: 2010-10-12
forum: New to Ubuntu
---

### Post by chamm on 2010-10-12
I'm an experienced PC user, and I know Linux from the command line pretty well, but I'm really uncomfortable with the GUI. So I'm probably coming at this backwards, but any information would be appreciated.   I'm starting out on a netbook. I installed 10.04 of UNR and really liked it, but I don't care for unity in 10.10, so I'm playing around with different window managers.  Is it fundamentally different if I install Ubuntu Desktop Edition, and get the netbook window manager through aptitude? Or vice versa? How about if I also install Lubuntu, Kubuntu and Xubuntu and switch back and forth. Does the netbook remix use a different kernel that is somehow faster?

---

### Post by renzokuken on 2010-10-13
from what i understand its the same kernel/drivers i.e. underlying base as normal ubuntu. the only difference is the desktop environment.

[http://ubuntuforums.org/showthread.php?p=9945305](http://ubuntuforums.org/showthread.php?p=9945305)

---

### Post by Hippytaff on 2010-10-13
> **renzokuken said:**
> from what i understand its the same kernel/drivers i.e. underlying base as normal ubuntu. the only difference is the desktop environment.
 
[http://ubuntuforums.org/showthread.php?p=9945305](http://ubuntuforums.org/showthread.php?p=9945305)
 
Thats what I believe, and I think it's mainly to do with resolution with unity (designed for netbook size screens) you should have the option to choose at boot-up if you have more than one window manager.

---

### Post by renzokuken on 2010-10-13
you can easily install Gnome/kde/openbox etc as well though. i'm not sure how they deal with the lower resolutions and smaller screen. but at least you can choose them from GDM (login)

FYI
```

sudo apt-get install ubuntu-desktop  *(for Gnome)*
sudo apt-get install kubuntu-desktop  *(for KDE)*
sudo apt-get install xubuntu-desktop  *(for XFCE)*

```

GDM will allow you to choose at login

---

