---
title: "KDE apps without KDE"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by technosinner on 2009-01-16
So... I don't care much for KDE (too googly, counter-intuitive and wonky for my likes) BUT I really like how Dolphin works as far as a file explorer.

Is it possible to use Dolphin with all the bells and whistles but without the rest of KDE?

I have a wierd phobia.  It's called "installapackageyoudontlikeandcantuninstallitrightobia"!

Thanks

---

### Post by taurus on 2009-01-16
If you install a KDE app, it will download and install all the necessary dependencies so there is no way around it.  And if you remove it later, you can use the autoremove to clean out all the unused dependencies.

```
sudo apt-get autoremove
```

---

### Post by Ben Page on 2009-01-16
As far as I know, this is impossible, dolphin is integrated to KDE core, like KWin, and some other stuff. I tried to install Konqueror (web browser for KDE) and it offered to install KDE core. I managed to install KDE icons, cursors and Ktorrent (bittorrent client for KDE) only. rest is KDE exclusive, but you can install both KDE and Gnome on the same machine and log in to desktop in witch ever DE you want, also that way its posible to use KDE exclusive apps in gnome (but you have to install KDE/but not use it). Also, with installing KDE you will install KDE version of Open office 2.4, so if you have 3.0 it will be overwritten.

---

### Post by oldos2er on 2009-01-16
You can install dolphin; kde-core is not one of its dependencies.

---

### Post by technosinner on 2009-01-16
Gotcha!  Thanks guys.

---

### Post by Ben Page on 2009-01-16
> **oldos2er said:**
> You can install dolphin; kde-core is not one of its dependencies.

Im not saying youre wrong, but how will Nautilus cope with Dolphin, just dolphin--replace would do?

---

### Post by oldos2er on 2009-01-16
> **Ben Page said:**
> Im not saying youre wrong, but how will Nautilus cope with Dolphin, just dolphin--replace would do?

 Nautilus doesn't have anything to "cope" with. It's possible to run any file manager, as well as have a bunch of them installed. The OP didn't ask how to replace Nautilus with dolphin, after all, merely how to install dolphin on Gnome.

---

### Post by technosinner on 2009-01-17
Now now don't argue over my noob questions ;)
But it's true I just want to have Dolphin available, not replace Nautilus.
I'll give it a whirl soon, as soon as I re-install Ubuntu actually!

Thank you!

---

### Post by Ben Page on 2009-01-17
Ok, I tried installing Dolphin only, and its true that its not dependant from KDE-core, but you still have to install a bunch of archives to get it installed:

```
ben@ben-desktop:~/Desktop$ sudo apt-get install dolphin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  kde-icons-oxygen kdebase-runtime kdebase-runtime-bin-kde4
  kdebase-runtime-data kdebase-runtime-data-common kdelibs-bin kdelibs5
  kdelibs5-data kfind khelpcenter4 libclucene0ldbl libkonq5 libkonq5-templates
  libphonon4 libsoprano4 libstreamanalyzer0 libstreams0 libstrigiqtdbusclient0
  phonon phonon-backend-gstreamer soprano-daemon
Suggested packages:
  kdebase phonon-backend-xine phonon-backend-vlc phonon-backend-mplayer
The following NEW packages will be installed:
  dolphin kde-icons-oxygen kdebase-runtime kdebase-runtime-bin-kde4
  kdebase-runtime-data kdebase-runtime-data-common kdelibs-bin kdelibs5
  kdelibs5-data kfind khelpcenter4 libclucene0ldbl libkonq5 libkonq5-templates
  libphonon4 libsoprano4 libstreamanalyzer0 libstreams0 libstrigiqtdbusclient0
  phonon phonon-backend-gstreamer soprano-daemon
0 upgraded, 22 newly installed, 0 to remove and 7 not upgraded.
Need to get 37.1MB of archives.
After this operation, 101MB of additional disk space will be used.
```

So thats 100MB of your HDD space just for one file manager.
It works independently, and works without any glitches or bugs, but I dont know how to get into My Computer via Dolphin, it opens Home folder as default and its posible to browse from there, but no My comp place.
Offcourse, Dolphin wont open as the default file browser, so you have to open it manualy and then go to folder you like, Gnome will still open Nautilus as the default file browser.
This your noob-ish Q, was not so noobis to me, it peeked my interest. Maybe this will be usful to somebody...

---

### Post by oldos2er on 2009-01-17
You can go into the settings to change the default directory.

---

### Post by Ben Page on 2009-01-18
Yes I can, but I can't change it to display the " Computer " place. I can't mount or acces other media drives, I can only browse the " filesystem ". Only when I mount other drives via nautilus, then they apear on the left panel in dolphin.

---

### Post by oldos2er on 2009-01-18
Yes, you're right. I hardly ever use dolphin so I hadn't noticed that. If the drives you want to mount are local, you could add them to your /etc/fstab so that they're automounted for you--assuming you want to do that.

---

### Post by jrusso2 on 2009-01-18
Well you have to install the KDE libraries at least or it won't work.

---

