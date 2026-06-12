---
title: "Customizing Icon Themes"
date: 2011-03-27
forum: New to Ubuntu
---

### Post by DGINSD on 2011-03-27
I've noticed while customizing my desktop, in some icon packages theres icons I like individually and would like to make a custom icon package of my own. Where are these stored and can they be easily modified, swapped and what not to create my own package of icons so I have a package of all the ones I like.

Is it as easy as creating a proper named file and filling it with the appropriately named icons or thumbnails or is it a more complex process than that. I've made cursor themes in my windows partition so I'm hoping it's similar

---

### Post by Mr Stoozer on 2011-03-27
Check out **/usr/share/icons** and **~/.icons**
Have a look at an index.theme file in gedit. That should give you a leg up with creating.

---

### Post by Frogs Hair on 2011-03-27
Take a look at the link , it could prove useful .  [http://live.gnome.org/GnomeArt/Tutorials/IconThemes](http://live.gnome.org/GnomeArt/Tutorials/IconThemes)

---

### Post by DGINSD on 2011-03-27
> **Mr Stoozer said:**
> Check out **/usr/share/icons** and **~/.icons**
Have a look at an index.theme file in gedit. That should give you a leg up with creating.

How do I give myself root permission, I can't look in my root folder?

---

### Post by Frogs Hair on 2011-03-27
```
gksudo nautilus
```

---

### Post by DGINSD on 2011-03-27
K it gave me an error

> Initializing nautilus-gdu extension

(nautilus:3050): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
eedesktop.ConsoleKit.Manager.GeneralError: Unable to lookup session information for process '3050'
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:3050): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:3050): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:3050): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed


What am I doing wrong?

---

### Post by Frogs Hair on 2011-03-27
I'm not sure what's going on the command opens nautilus as root , which gives the ability to make changes . Are you administrator ?

If you are the administrator , check system > administration > users and groups and see what permissions you have on that account.

---

### Post by DGINSD on 2011-03-27
Ok, its working I'm just a ra-tard.

Someone that knows how to write programs should make one to set up an icon theme on a per icon basis. I had to do some screwy stuff (and quite a bit of it) just to use the computer icon I like in the Icon theme I'm using.

Way above my skill level but it sure would be nice.

---

### Post by DGINSD on 2011-04-03
Thought I'd ask this question on an old related thread, rather than start a whole new one. How does one go about un-installing themes, icon packages and what not, that have been installed? I have some that I installed that I'll never use and I'd like to free up the space as it's at a premium on my tiny hard drive. Theres even some of the ones that came with Ubuntu I'd like to part with, that I have no use for.

---

### Post by Mr Stoozer on 2011-04-03
> **DGINSD said:**
> Thought I'd ask this question on an old related thread, rather than start a whole new one. How does one go about un-installing themes, icon packages and what not, that have been installed? I have some that I installed that I'll never use and I'd like to free up the space as it's at a premium on my tiny hard drive. Theres even some of the ones that came with Ubuntu I'd like to part with, that I have no use for.

Backgrounds:
/usr/share/backgrounds

Themes:
/usr/share/themes
~/.themes

Icons:
/usr/share/icons
~/.icons

Pointers:
/usr/share/icons
~/.icons

Delete any unwanted bits and bobs from these locations (or better, **move** them and reboot to check all is well before deleting).  Note you'll need admin privilages to modify anything in /usr/share so be sure you want to delete what you're deleting.

---

