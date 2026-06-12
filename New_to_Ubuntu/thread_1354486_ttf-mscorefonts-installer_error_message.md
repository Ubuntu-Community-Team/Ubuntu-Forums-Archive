---
title: "ttf-mscorefonts-installer error message?"
date: 2009-12-13
forum: New to Ubuntu
---

### Post by haveguitarwilltravel on 2009-12-13
Hello Ubuntu community, I'm having some difficulties, it doesn't appear to effect anything but whenever I go to install just any program through the package manager I get some error about ttf-mscorefonts-installer, and just now when I tried to install LAMP server it was hanging on configuring ttf-mscorefonts-installer and now I got this in terminal "tasksel: aptitude failed (100)". So I guess it didn't install lamp, any help would be much appreciated.

---

### Post by Redache on 2009-12-13
It sounds like ttf-mscorefonts-installer hasn't installed properly along the line. 

Try running:```
 sudo aptitude update
``` to see if it'll actually update apt. If not then come back with whatever error it gives and we'll help you further.

Also try: ```
sudo aptitude autoclean 
```to see if that clears it out.

---

### Post by Dennis N on 2009-12-14
Here is a workaround for the problem:

[http://friendlytechninja.vndv.com/2009/11/05/howto-fix-ttf-mscorefonts-installer-problems-in-ubuntu-9-10-karmic-koala/](http://friendlytechninja.vndv.com/2009/11/05/howto-fix-ttf-mscorefonts-installer-problems-in-ubuntu-9-10-karmic-koala/)

Following the procedures given to remove ttf-mscorefonts installer then run the script provided to install the mscorefonts without it.

---

### Post by philinux on 2009-12-14
> **haveguitarwilltravel said:**
> Hello Ubuntu community, I'm having some difficulties, it doesn't appear to effect anything but whenever I go to install just any program through the package manager I get some error about ttf-mscorefonts-installer, and just now when I tried to install LAMP server it was hanging on configuring ttf-mscorefonts-installer and now I got this in terminal "tasksel: aptitude failed (100)". So I guess it didn't install lamp, any help would be much appreciated.

Was your system fully up to date before installing lamp

```
sudo apt-get update
```

you might need a ..

```
sudo dpkg --configure -a
```

to sort out tasksel.

---

