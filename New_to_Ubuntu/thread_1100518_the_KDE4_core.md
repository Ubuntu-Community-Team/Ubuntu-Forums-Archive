---
title: "the KDE4 core?"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by cptrohn on 2009-03-19
I remember reading here before that it was possible to just download the KDE4 core without getting all the apps that comes with a Kubuntu desktop.  How does this work?  I really like the look of the KDE4 desktop, but I don't like getting a lot of double aplications when you install the desktop..

would it be ```
sudo apt-get install Kubuntu-core
```?

And my desktop would basically still work as a gnome desktop with the KDE4 look correct?

---

### Post by gandaran on 2009-03-19
> And my desktop would basically still work as a gnome desktop with the KDE4 look correct?
no, if you want the KDE look you have to install kubuntu-desktop and either run KDE or gnome, installing qt4-core and gui only permits you to run kde apps but they will still have an ugly look in gnome.

---

### Post by SunnyRabbiera on 2009-03-19
KDE and Gnome are two different things, KDE is not a theme, its an entire desktop environment.

---

### Post by cptrohn on 2009-03-19
I read in this thread that it is possible to just install the KDE core, although it doesn't say how to do it...


[http://ubuntuforums.org/showthread.php?t=1087845&highlight=KDE+core](http://ubuntuforums.org/showthread.php?t=1087845&highlight=KDE+core)

---

### Post by LowSky on 2009-03-19
the problem with trying to add just KDE is that KDE has many programs that are built in, so you will end up with a bunch of apps you don't need or want.

the best thing to do is to edit the menu after installaition, which is very easy. or install Kubuntu to a seperate partition. A little annoying but keeps things seperate.

---

### Post by gandaran on 2009-03-19
> **cptrohn said:**
> I read in this thread that it is possible to just install the KDE core, although it doesn't say how to do it...


[http://ubuntuforums.org/showthread.php?t=1087845&highlight=KDE+core](http://ubuntuforums.org/showthread.php?t=1087845&highlight=KDE+core)
why don't you go ahead? KDE core will only install a few kde apps, you can always remove everything easily with synaptic if you don't like it, and let us know if you get the KDE look.

---

### Post by cptrohn on 2009-03-19
> **gandaran said:**
> why don't you go ahead? KDE core will only install a few kde apps, you can always remove everything easily with synaptic if you don't like it, and let us know if you get the KDE look.

"why don't you go ahead"

LOL because I don't how...

I liked the look of the KDE desktop and had it installed before, but there were things that it just wouldn't let me uninstall that I didn't like (like the KDE movie player, Konquerer etc)

It just wouldn't let me get rid of those apps at all and came back with an error message everytime I tried to get rid of them.

---

### Post by gandaran on 2009-03-19
> **cptrohn said:**
> "why don't you go ahead"

LOL because I don't how...

I liked the look of the KDE desktop and had it installed before, but there were things that it just wouldn't let me uninstall that I didn't like (like the KDE movie player, Konquerer etc)

It just wouldn't let me get rid of those apps at all and came back with an error message everytime I tried to get rid of them.
I was checking kde-core dependencies in synaptic and it installs kde-window-manager so maybe it's possible to get that kde look, if I liked KDE I would try, no problem.

---

### Post by LowSky on 2009-03-19
> **cptrohn said:**
> "why don't you go ahead"

LOL because I don't how...

I liked the look of the KDE desktop and had it installed before, but there were things that it just wouldn't let me uninstall that I didn't like (like the KDE movie player, Konquerer etc)

It just wouldn't let me get rid of those apps at all and came back with an error message every time I tried to get rid of them.

You cant remove them they are part of KDE, built in remove one and it removes the whole thing. You can disable the icons from showing up, but that's its. Its very easy to remove icons, especially in Gnome (Never tried under KDE)

---

