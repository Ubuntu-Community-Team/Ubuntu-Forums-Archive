---
title: "apt-get autoremove question"
date: 2009-06-21
forum: New to Ubuntu
---

### Post by garmo on 2009-06-21
I want to remove packages I don't need but when I do apt-get autoremove wine is one of the packages to be removed. I sometimes use wine, why would it be removed?

The following packages were automatically installed and are no longer required:
  libstrigiqtdbusclient0 desktop-base libarts1c2a libartsc0 libqimageblitz4
  libparted1.8-9 kdenlive-data kdenlive wine-gecko libmlt++1 libmagick++10
  linux-headers-2.6.28-11 kdebase-data phonon libqt3-i18n libexiv2-4
  librasqal0 dolphin libgnome-desktop-2-7 inigo libttf2 libsdl-sound1.2
  libkonq5 linux-headers-2.6.28-11-generic libmikmod2 kfind kdebase-bin
  libpoppler3 recordmydesktop wine libdvdread3 libkonq5-templates exim4
  xfce4-mixer-alsa libmlt-data libmlt1 unhide libpoppler-glib3 libsmpeg0
Use 'apt-get autoremove' to remove them.

---

### Post by Bodsda on 2009-06-21
> **garmo said:**
> I want to remove packages I don't need but when I do apt-get autoremove wine is one of the packages to be removed. I sometimes use wine, why would it be removed?

The following packages were automatically installed and are no longer required:
  libstrigiqtdbusclient0 desktop-base libarts1c2a libartsc0 libqimageblitz4
  libparted1.8-9 kdenlive-data kdenlive wine-gecko libmlt++1 libmagick++10
  linux-headers-2.6.28-11 kdebase-data phonon libqt3-i18n libexiv2-4
  librasqal0 dolphin libgnome-desktop-2-7 inigo libttf2 libsdl-sound1.2
  libkonq5 linux-headers-2.6.28-11-generic libmikmod2 kfind kdebase-bin
  libpoppler3 recordmydesktop wine libdvdread3 libkonq5-templates exim4
  xfce4-mixer-alsa libmlt-data libmlt1 unhide libpoppler-glib3 libsmpeg0
Use 'apt-get autoremove' to remove them.
autoremove is used to remove packages that were automatically installed to satisfy dependencies for some package and that are no more needed. 

As to why it is removing wine, im not entirely sure, but you could always reinstall afterwards, although someone may know a way to remove it from the autoremove list.

Regards,

Bodsda

---

### Post by Lampi on 2009-06-21
try
```
sudo aptitude unmarkauto wine
```

---

### Post by CatKiller on 2009-06-21
> **Bodsda said:**
> someone may know a way to remove it from the autoremove list.

I think ```
sudo aptitude unmarkauto wine
```should do it.

EDIT: Beaten to the punch

---

### Post by garmo on 2009-06-21
I did sudo aptitude unmarkauto wine and it still going to be removed

sudo aptitude unmarkauto wine
[sudo] password for garmo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
The following packages will be REMOVED:
  desktop-base{u} dolphin{u} exim4{u} inigo{u} kdebase-bin{u} 
  kdebase-data{u} kdenlive{u} kdenlive-data{u} kfind{u} libarts1c2a{u} 
  libartsc0{u} libdvdread3{u} libexiv2-4{u} libgnome-desktop-2-7{u} 
  libkonq5{u} libkonq5-templates{u} libmagick++10{u} libmikmod2{u} 
  libmlt++1{u} libmlt-data{u} libmlt1{u} libparted1.8-9{u} 
  libpoppler-glib3{u} libpoppler3{u} libqimageblitz4{u} libqt3-i18n{u} 
  librasqal0{u} libsdl-sound1.2{u} libsmpeg0{u} libstrigiqtdbusclient0{u} 
  libttf2{u} linux-headers-2.6.28-11{u} linux-headers-2.6.28-11-generic{u} 
  phonon{u} recordmydesktop{u} unhide{u} wine{u} wine-gecko{u} 
  xfce4-mixer-alsa{u}

---

### Post by Lampi on 2009-06-21
well ... if that's the case I'd put it on hold:

```
aptitude hold wine
```

or

```
echo wine "hold" | dpkg --set-selections
```

to *un*set it this is:


```
aptitude unhold wine
```

```
echo wine "install" | dpkg --set-selections
```

The reason why I'm quoting to possible ways is the following: don't know what package management tool you use - adept for example will totally ignore aptitude holds, at least he did it in Intrepit. The dpkg way might be saver than aptitude

---

### Post by CatKiller on 2009-06-21
Well, you can do it in Synaptic too. Find Wine in the list and de-select Package -> Automatically installed.

---

### Post by garmo on 2009-06-21
I prefer doing it from the terminal, it's faster than synaptic for me.
aptitude hold wine worked, thank you all.

---

