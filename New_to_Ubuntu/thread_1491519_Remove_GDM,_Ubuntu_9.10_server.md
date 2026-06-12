---
title: "Remove GDM, Ubuntu 9.10 server ?"
date: 2010-05-23
forum: New to Ubuntu
---

### Post by WitchCraft on 2010-05-23
Hi, I had to install gnome/gdm to install my HP printer on my (supposed to be console) console server.

The problem now is gdm/gnome startsup automatically.
I did update-rc.d -f gdm remove, but gnome still starts autocrapically. service gdm remove doesn't work either.

I removed gdm and ubuntu-desktop, but then, that f*ing HP printer stopped working.

What must I do to stop gnome/gdm on 9.10 server ?

---

### Post by -humanaut- on 2010-05-23
Try sudo init3 then try removing GDM

---

### Post by WitchCraft on 2010-05-24
That's part of the problem. init3 doesn't switch to console.
In fact, init xy doesn't do anything for any value of xy.

I have to issue pkill gdm to get to the console.

---

### Post by warfacegod on 2010-05-24
```
sudo apt-get purge gdm
``` Works in regular Ubuntu anyway.

---

### Post by WitchCraft on 2010-05-24
> **warfacegod said:**
> ```
sudo apt-get purge gdm
``` Works in regular Ubuntu anyway.

Thath's the funny thing, it still started gnome when I did apt-get remove gdm.

I had to do: apt-get remove gnome* xorg* xserver* ubuntu-desktop
and afterwards apt-get autoremove

But somehow it still wants to boot into graphical mode, but now it can't.
It doesn't crash though, but I have to switch to another virtual terminal to start working.

---

### Post by warfacegod on 2010-05-24
There's probably some .gnome and .gdm folders floating around getting rid of them might help.

ubuntu-desktop is just a meta package. It doesn't do anything but pull in the Gnome Environment, Desktop programs, and the dependencies. Removing it does nothing.

When I read your first post, I didn't realize that you had installed the entire Ubuntu Desktop environment. Getting rid of all that is a huge task. I don't even know where you should begin. The only thing I can recommend is using Synaptic (if you still have it) and completely removing anything that says gnome. That *should* get rid of most of the desktop but I'm making little more than an educated guess.

The only certain way I know of to get rid of Gnome, with out breaking your system, is to do a fresh install.

---

### Post by WitchCraft on 2010-05-25
I think I pretty much got it.
 
It installed about 1200 MB for gnome, and I removed about 1100 mb.
QT might account for the rest.
 
It's probably just some settings in some config files that weren't removed.
Plus taking a look was good, I saw that dovecot and postfix were running, although I never installed them.
 
Must have come with the default server install. 
So I removed them, too.

---

