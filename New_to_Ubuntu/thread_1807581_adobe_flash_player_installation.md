---
title: "adobe flash player installation"
date: 2011-07-19
forum: New to Ubuntu
---

### Post by nadsjinx on 2011-07-19
Hi! I just installed ubuntu and updated firefox to v5 now im trying to install flash player for firefox...

at the adobe flash site i click on download and the 'launch application'  pop-up appears. it has two choices, 1)apturl and 2) choose  application... when i choose apturl nothing seems to happen... and i  dont know which application to choose if i use the second choice...

please help!

thanks in advance!

---

### Post by ratcheer on 2011-07-19
I think one of the choices will let you download a .deb file. Download it and then use:

dpkg -i <full path and filename of the .deb file>

Tim

---

### Post by gandaran on 2011-07-19
> **nadsjinx said:**
> Hi! I just installed ubuntu and updated firefox to v5 now im trying to install flash player for firefox...

at the adobe flash site i click on download and the 'launch application'  pop-up appears. it has two choices, 1)apturl and 2) choose  application... when i choose apturl nothing seems to happen... and i  dont know which application to choose if i use the second choice...

please help!

thanks in advance!
open the ubuntu software center and type flash in the search box, it'll show the flash packages available to install (flashplugin-installer)
the apturl link is the correct choice to choose in the adobe flash website, apturl will lead you to install flash from software center too. 
you may need to update packages before using software center, type in terminal
```
sudo apt-get update
```

---

### Post by srisharan on 2011-07-19
search for flash in software center or install ubuntu restricted extras from the software centre.They have other things also like mp3 codecs.SO installing it would be better

---

### Post by ajgreeny on 2011-07-19
Even easier and more likely to overcome any problems with conflicting packages is to get the flash aid add-on for firefox.  The flash plugin installed by this will also work out of the box in other browsers, eg chromium.
[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

---

### Post by beew on 2011-07-19
> **ajgreeny said:**
> Even easier and more likely to overcome any problems with conflicting packages is to get the flash aid add-on for firefox.  The flash plugin installed by this will also work out of the box in other browsers, eg chromium.
[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

+1 to flash-aid. But I think it will work for all browsers except chromium since as far as I know chromium comes with its own embedded flash, unlike other browsers.

---

### Post by lovinglinux on 2011-07-19
> **beew said:**
> +1 to flash-aid. But I think it will work for all browsers except chromium since as far as I know chromium comes with its own embedded flash, unlike other browsers.

It works for Chromium. It doesn't work for Chrome 32bit only, unless you disable the built in flash in about[noparse]:[/noparse]plugins. Chrome detects the flash plugin from the system as well.

---

