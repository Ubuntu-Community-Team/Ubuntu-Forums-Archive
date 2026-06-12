---
title: "Cant install kubuntu desktop in ubuntu"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by SwatKat on 2009-11-09
Hey,

I installed kubuntu desktop in ubuntu using sudo aptitude install kubuntu-desktop. I don't think there was any real problem with the installation itself. I didn't get any error messages  at any time during the download or installation. But I am unable to run a kde session.
Every time i boot into ubuntu I first get the kubuntu start up screen, then the ubuntu screen. Then in the log in screen, if I change the session from gnome to kde, I get the ubuntu start up screen again which brings me back to the login screen. Gnome works fine. Now I just have a lot of KDE applications cluttering the menus.  I had chosen the default display manager as gdm during the installation and mine is a wubi installation, if that matters. 
Suggestions please?

---

### Post by t0p on 2009-11-09
On my (non-wubi) ubuntu machine: when i get to the login page, in the bottom left corner is a button marked 'Options' or 'Sessions' (cant remember which). Click that and I get option to choose KDE or Gnome. Is it the same on your wubi installation?

If not, I would suggest doing a proper install. Wubi is okay for trying out Ubuntu but I dont think it is suitable for serious use. Just my opinion.

---

### Post by SwatKat on 2009-11-09
Yes, I get an option of choosing between  kde and gnome sessions too. But I get back the login screen if I choose kde while gnome works just fine.

---

### Post by lisati on 2009-11-09
You might want to try:
```
sudo aptitude reinstall kubuntu-desktop
```
(Note: it's "reinstall" in this example)

---

### Post by SwatKat on 2009-11-09
> **lisati said:**
> You might want to try:
```
sudo aptitude reinstall kubuntu-desktop
```(Note: it's "reinstall" in this example)

Thanks for the suggestion. I tried that, but doesn't seem to be working. 

Its just a thought, but are the system hardware requirements different for KDE and gnome? It just occurred to me that I have had an almost identical login page problem ( cant get past the login page. Even live cds asked to login!!) with the KDE live cds that I have tried ( opensuse and Mandriva) while the gnome ones ( Ubuntu and linux mint ) worked fine...

---

