---
title: "Flash issue in Karmic"
date: 2010-04-18
forum: New to Ubuntu
---

### Post by gryghost99 on 2010-04-18
Basically, I can't get Flash to work in anything (Firefox, Chrome... etc).  Whenever I browse to YouTube and select a video, the site says I need to upgrade.  The link provided takes me to Abode's download/install.  The version there is the same as what Synaptic reports, and the APT says that I am using the same version.

Ok... I have tried completely removing/reinstalling through Synaptic... removing then installing the -nonfree version... removing the plugin completely and installing through Adobe's site.... even tried this code... 
```
$ sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm  # Deletes a  troublesome config file
$ sudo dpkg-reconfigure adobe-flashplugin --force  # Force-reconfigures  adobe-flashplugin
$ sudo dpkg --purge --force-all adobe-flashplugin  # Force-removes  adobe-flashplugin
$ sudo apt-get install flashplugin-nonfree  # Installs flashplayer the  easy way
```I am getting nowhere.  Firefox currently is showing 2 versions of the Flash plugin installed (current and 9.0r999).  I have tried disabling each and still nothing.

Any and all help would be appreciated.

---

### Post by jmvbxx on 2010-04-18
I'd recommend trying:

```
sudo aptitude install flashplugin-installer
sudo aptitude install flashplugin-nonfree
```

---

### Post by lovinglinux on 2010-04-18
> **gryghost99 said:**
> Firefox currently is showing 2 versions of the Flash plugin installed (current and 9.0r999).  I have tried disabling each and still nothing

Disabling it won't work. You have to remove swfdec. See the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://lovinglinux.megabyet.net/?page_id=220#Flash--Optimization-1) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by gryghost99 on 2010-04-18
> **lovinglinux said:**
> Disabling it won't work. You have to remove swfdec. See the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://lovinglinux.megabyet.net/?page_id=220#Flash--Optimization-1) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).
Thx lovinglinux...  removing the swfdec fixed the problem.

---

