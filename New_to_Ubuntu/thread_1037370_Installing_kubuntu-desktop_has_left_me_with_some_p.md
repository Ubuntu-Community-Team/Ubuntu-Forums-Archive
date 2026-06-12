---
title: "Installing kubuntu-desktop has left me with some problems."
date: 2009-01-11
forum: New to Ubuntu
---

### Post by tpdi on 2009-01-11
Background: I installed ubuntu-eee, which is a ubuntu hardy distribution with a specialized kernel.

So far so good.

I then installed kdebase, which got me kde. On bootup, I got my grub menu, and that got me to gdm, and I started a kde session.

So far so good.

I then installed kubuntu-desktop. This is where it gets weird.

On bootup, after grub, I now get a text login. I login, sudo kdm, login, and I have my GUI. 

How can I get the after grub to start kdm, without doing it manually?

Also, after installing kubuntu-desktop, runnng gnome-appearence-properties shows big question marks over the theme. Did installing kubuntu do some violence to my gnome themes?  This is important, because I need GTK apps to use particular themes (compact ones, as I have a 1024x600 pixel screen).


Thanks.

---

### Post by Xiong Chiamiov on 2009-01-11
> **tpdi said:**
> How can I get the after grub to start kdm, without doing it manually?
Try
```

sudo dpkg-reconfigure kdm

```
which will give you the option of choosing which (kdm or gdm) you want to load on startup.  You can use either to boot into the other, so it's pretty much just preference.

> **tpdi said:**
> Also, after installing kubuntu-desktop, runnng gnome-appearence-properties shows big question marks over the theme. Did installing kubuntu do some violence to my gnome themes?  This is important, because I need GTK apps to use particular themes (compact ones, as I have a 1024x600 pixel screen).

It shouldn't have affected anything, since KDE uses QT for everything, rather than GTK.  Do the themes still work?  If not, are they still installed in synaptic?  Try reinstalling them?

---

### Post by abn91c on 2009-01-11
why you have to do sudo kdm to log in, what happens when you type[COLOR="Red"] startx[/COLOR] at the prompt

---

### Post by tpdi on 2009-01-11
> **Xiong Chiamiov said:**
> Try
```

sudo dpkg-reconfigure kdm

```


Ah,thanks, that works.

---

