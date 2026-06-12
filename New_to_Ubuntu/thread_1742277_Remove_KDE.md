---
title: "Remove KDE"
date: 2011-04-28
forum: New to Ubuntu
---

### Post by pi3.1415926535... on 2011-04-28
I installed KDE, now I have decided that I want to remove it. The problem is that I cannot remember the name of the package I installed. Does anyone know the names of packages commonly used to install KDE?

Thank you

---

### Post by ivanovnegro on 2011-04-28
Hm, I think kubuntu-desktop and maybe kde-base, look for this in Synaptic.

---

### Post by RJ12 on 2011-04-28
If you used "apt-get" to install "kubuntu-desktop" uninstalling that package won't do much I think (it's a metapackage and I don't think it auto removes all the KDE stuff)

---

### Post by pi3.1415926535... on 2011-04-28
Is there a way to uninstall all of the packages that KDE installed?

Thank you

---

### Post by rockstarrem on 2011-04-28
I'm guessing you could do:

```

sudo apt-get remove kubuntu-desktop --purge

```

Let me know how it goes.

---

### Post by ankspo71 on 2011-04-28
Hi,
If you installed the package called "kubuntu-desktop" then the following link has a command to remove all of kubuntu-desktop's related packages, then the command reinstalls Ubuntu to make sure nothing is missing. They don't have a command to use on Ubuntu 11.04 yet, but they have one for 10.10
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)
Hope this helps.

---

### Post by rockstarrem on 2011-04-28
> **ankspo71 said:**
> Hi,
If you installed the package called "kubuntu-desktop" then the following link has a command to remove all of kubuntu-desktop's related packages, then the command reinstalls Ubuntu to make sure nothing is missing. They don't have a command to use on Ubuntu 11.04 yet, but they have one for 10.10
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)
Hope this helps.

I'd recommend doing that command actually, and if you do do the one I posted before, please add:

```

sudo apt-get remove kubuntu-desktop --purge && sudo apt-get install ubuntu-desktop

```

---

### Post by Atomic-Fanboy on 2011-09-05
I'm in the same position - I have recently fallen in love with XFCE and I want to remove KDE for the time being. However, there are quite a few KDE applications that I absolutely love and can't do without (a good example would be Konqueror - a dire, dire web browser but the best file management program I have ever seen).

---

### Post by mikechant on 2011-09-06
> I'm in the same position - I have recently fallen in love with XFCE and I want to remove KDE for the time being. However, there are quite a few KDE applications that I absolutely love and can't do without (a good example would be Konqueror - a dire, dire web browser but the best file management program I have ever seen).

In that case it's probably not worth removing anything - you need a lot of KDE libs to run any KDE applications so you won't save much disc space (and disc space is pretty plentiful and cheap these days!).

It's only worth doing if you've got a serious disc space shortage. In that case, remove all KDE stuff as per above and then reinstall Konquerer etc. which will just pull in the bits it needs (this is probably a lot easier than try to selectively remove the packages that Konquerer etc. do not require).

---

