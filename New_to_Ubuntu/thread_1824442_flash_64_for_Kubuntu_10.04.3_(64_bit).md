---
title: "flash 64 for Kubuntu 10.04.3 (64 bit)"
date: 2011-08-13
forum: New to Ubuntu
---

### Post by senorian on 2011-08-13
Falko's instructions (sudo kate /etc/apt/sources.list) didn't work.
I went to  the adobe site but could not understand the instructions
If there is a tutorial please let me know.
Thanks

---

### Post by oldos2er on 2011-08-13
Run Firefox, install the FlashAid extension: [https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

---

### Post by senorian on 2011-08-13
oldos2er
Thanks
The first step ran and I was told to restart. when I did I was presented with some choices which I did not understand and i lost all the windows when I selected the wrong button?
thanks
Sorry but would you be able to give me more details

---

### Post by oldos2er on 2011-08-14
What button did you click? Also not sure what you mean by "lost all the windows", are you talking about the Firefox window?

More help here: [http://support.webgapps.org/add-ons/flash-aid](http://support.webgapps.org/add-ons/flash-aid)

---

### Post by MountainX on 2012-03-15
> **oldos2er said:**
> Run Firefox, install the FlashAid extension: [https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)


It is no longer necessary to manually install flash. The package adobe-flashplugin will install the latest version of flash (currently 11) from the official Ubuntu repositories.

---

### Post by lovinglinux on 2012-03-15
> **MountainX said:**
> It is no longer necessary to manually install flash. The package adobe-flashplugin will install the latest version of flash (currently 11) from the official Ubuntu repositories.

Flash-Aid suggests the beta flash by default, which you can't get from the repositories. However, it also allows to use the stable versions from the repositories, including the 64bit *adobe-flashplugin*, if the partner repository is enabled. 

Additionally, Flash-Aid also removes conflicting plugins installed manually in several locations and apply performance tweaks.

---

### Post by MountainX on 2012-03-15
> **lovinglinux said:**
> Flash-Aid suggests the beta flash by default, which you can't get from the repositories. However, it also allows to use the stable versions from the repositories, including the 64bit *adobe-flashplugin*, if the partner repository is enabled. 

Additionally, Flash-Aid also removes conflicting plugins installed manually in several locations and apply performance tweaks.

What exactly do you get when you install the "beta version" now that Adobe has stopped development of an independent flash and closed Adobe Labs Flash? I think Flash Aid must be out of date.

---

### Post by lovinglinux on 2012-03-16
> **MountainX said:**
> What exactly do you get when you install the "beta version" now that Adobe has stopped development of an independent flash and closed Adobe Labs Flash? I think Flash Aid must be out of date.

It isn't out-of-date yet, because adobe released an RC version of 11.2 recently. I don't know what I am going to do with the beta installation in the future, once 11.2 is released, but Flash-Aid still has it's use, since it can solve other issues, by making sure no other versions are installed.

---

