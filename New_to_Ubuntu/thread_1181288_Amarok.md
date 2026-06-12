---
title: "Amarok"
date: 2009-06-07
forum: New to Ubuntu
---

### Post by susanpenter on 2009-06-07
I am using the most up to date Ubuntu package 9.04 however my copy of Amarok says it is using KDE 3.5 and I would like to upgrade it to a 2.2 version of Amarok which uses KDE 4.x.

I use a mixture of Gnome and KDE software within Ubuntu and would like to know the best way of upgrading my KDE without braking anything as this is very much my stable PC not a testing computer, please can someone advise me of the way forward.

Also it may be connected to this but although I am still getting notifications of updates to download and install I often have an exclamation mark in the top right tray telling me some of my repositories are out of date.

thank you in advance for your help.

Susan

---

### Post by sandyd on 2009-06-07
> **susanpenter said:**
> I am using the most up to date Ubuntu package 9.04 however my copy of Amarok says it is using KDE 3.5 and I would like to upgrade it to a 2.2 version of Amarok which uses KDE 4.x.

I use a mixture of Gnome and KDE software within Ubuntu and would like to know the best way of upgrading my KDE without braking anything as this is very much my stable PC not a testing computer, please can someone advise me of the way forward.

Also it may be connected to this but although I am still getting notifications of updates to download and install I often have an exclamation mark in the top right tray telling me some of my repositories are out of date.

thank you in advance for your help.

Susan
was the 9.04 an upgrade from 8.04 or 8.10?
upgrading to KDE isn't such a dangerous process (unless you isntall kde-nightly)

just
```

sudo apt-get install kde

```
or if you want all the kde apps...
```

sudo apt-get install kubuntu-desktop

```

then upgrade and update everything
```

sudo apt-get update&&sudo aptitude safe-upgrade

```

gnome and KDE have always and will always be capable of coexisting.

---

### Post by susanpenter on 2009-06-07
It was an upgrade from 8.10, I like to upgrade to the newest version when it is released (stable rather than beta etc)

I like the idea of installing the Kubuntu desktop as long as it will not interfere with things like my internet connection, I have a bad memory of changing distros when I first started using Linux and being unable to access the internet!

---

### Post by cagechuck on 2009-06-07
I am very happy with the 8.10 and haven't upgraded yet.  Do I have to or need to?

---

### Post by susanpenter on 2009-06-07
There are a few things that I prefer about it like the notifications, there is no major upgrades as such just a lot of little tweeks to make it cleaner and smoother.

I think I'll go for the KDE option because then I can still add other KDE software later....

---

### Post by susanpenter on 2009-06-07
I've run into problems, I followed the advice to sudo install KDE trough the terminal and it has brought this screen up which I can't move on from, I've tried clicking on the OK but I think it is just an image!

---

### Post by susanpenter on 2009-06-08
I still have this window minimized I'm not sure whether I can close it or what I need to do about it before a possible re-boot, I don't want to get trapped out of my system.

Please advise

---

### Post by MDNZ on 2009-06-08
> **susanpenter said:**
> I still have this window minimized I'm not sure whether I can close it or what I need to do about it before a possible re-boot, I don't want to get trapped out of my system.

Please advise

Pressing enter also doesn't work? I believe it's safe to close that window since you didn't make any configuration changes.

---

### Post by susanpenter on 2009-06-08
Surely by installing the KDE environment I have made a change in the configuration. If I close the window will the worst that could happen be that I have to choose a login screen on each re-boot?

---

### Post by sandyd on 2009-06-08
use the tab and the arrow keys to select it.

---

### Post by sandyd on 2009-06-08
if you closed it already, do ```
sudo dpkg --reconfigure gdm
```

---

### Post by susanpenter on 2009-06-09
> **carlee said:**
> if you closed it already, do ```
sudo dpkg --reconfigure gdm
```

Thanks I tried this and I got this response:

dpkg: unknown option --reconfigure

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license|--licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !

I'm not sure what to do next!

---

