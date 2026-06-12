---
title: "Using Gnome Right Now. Is it Risky to Experiment with KDE?"
date: 2009-08-22
forum: New to Ubuntu
---

### Post by kendoori on 2009-08-22
Curious as to how seamless switching back and forth between Gnome and KDE would be on my 9.04 machine. Is it as easy as installing KDE and selecting it at login? Should I be concerned that certain apps might not work? will everything I already have installed show up?

---

### Post by MelDJ on 2009-08-22
yes. everything will work. it just looks and operates differently. kde will use its default programmes e.g konqueror for web browsing

---

### Post by sandyd on 2009-08-22
gnome and kde are backwards-compatible... or at least 99.9% of all apps are.

and all of your programs will show up.
they won't conflict.

---

### Post by Revolutionary101 on 2009-08-22
> **MelDJ said:**
> yes. everything will work. it just looks and operates differently. kde will use its default programmes e.g konqueror for web browsing

I used KDE on Ubuntu 9.04 and it worked perfectly.

---

### Post by .nedberg on 2009-08-22
It will work, no problem!

I would however advise you to wait until 9.10 comes along or install KDE 4.3 ([http://www.kubuntu.org/news/kde-4.3](http://www.kubuntu.org/news/kde-4.3)). IIRC 9.04 comes with 4.1 and a lot has happened since then!

I use 9.04 with KDE 4.3, and I am a happy user!

---

### Post by Hendrixski on 2009-08-22
totally safe.  You can experiment with all of the desktop environments you like. KDE3, KDE4, XFCE, GNOME, Enlightenment, java desktop, RatPoison, BlackBox....


Ok, well, maybe you don't want to try ratpoison, but Enlightenment is pretty cool.

enjoy!

---

### Post by lovinglinux on 2009-08-22
Instead of installing the full KDE, which will download/install a lot of stuff and pollute your Gnome menu with it's applications, install kde-core and plasma.

```
sudo apt-get install kde-core plasma
```

Then you can login into KDE with basic applications needed to work.

You can also login into Gnome and run this command:

```
plasma
```

This will launch the KDE panel and widgets on the top of Gnome, so you can just see how it works.

To close it:

```
killall plasma
```

---

