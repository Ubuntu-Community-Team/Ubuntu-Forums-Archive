---
title: "install Kubuntu Desktop"
date: 2009-08-06
forum: New to Ubuntu
---

### Post by jacklinux on 2009-08-06
Is it possible to install the Kubunut desktop?
On ubuntu 9.04

---

### Post by MTGap on 2009-08-06
Yeah it's possible, I'm guessing your currently using Gnome? 

Go into synaptic package manager and do a search for kubuntu, mark those for install and wait for it to install. Then log out and there will be a button that will allow you to change your session one for Gnome and one for KDE. 

KDE 4.3 recently came out, you may want to check this page out: [http://www.kde.org/announcements/4.3/](http://www.kde.org/announcements/4.3/)


KDE is a great desktop environment, but if you decide to stick with it you may want to download the kubuntu iso and do a reinstall there's always a lot of extra packages when you have two desktop environments.

---

### Post by northern lights on 2009-08-06
```
sudo apt-get update && sudo apt-get install kubuntu-desktop
```

---

### Post by egalvan on 2009-08-06
> **MTGap said:**
> 
KDE is a great desktop environment, but if you decide to stick with it **you may want to download the kubuntu iso and do a reinstall there's always a lot of extra packages when you have two desktop environments.**

Re-install not needed if you follow *northern lights* post...

> **northern lights said:**
> ```
sudo apt-get update && sudo apt-get install kubuntu-desktop
```


This will install  all the KDE-centric stuff, same as an original install.

And if you don't like the command line (that command above works great, BTW), then fire up Synaptic and do a search for "kubuntu-desktop".
It's a "META-PACKAGE" by the way...
it just downloads a bunch of other stuff..

And this will give you the option to boot into Gnome or KDE,
just choose "sessions" option on the boot screen.

And this will give you both Gnome and KDE stuff in the menus..
some like this, some don't.

And this is the same manner to install other DE's, such as Xubuntu (xfce), or edubuntu...

And one last thing, you may want to install the 'kubuntu-restricted-extras'... these are packages for video and audio stuff, etc.

Use either the command line used to the desk-top

```
sudo apt-get update && sudo apt-get install kubuntu-restricted-extras
```
or use Synaptic to install... it's also a meta-package


Forgot to add, that I am running several boxen with Ubuntu install like this
Ubuntu, then added Kubuntu, then added Xubuntu.
On one, I added edubntu instead of Xubuntu.

---

