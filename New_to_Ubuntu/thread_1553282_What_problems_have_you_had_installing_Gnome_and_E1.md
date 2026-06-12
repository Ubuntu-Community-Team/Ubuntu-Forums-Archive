---
title: "What problems have you had installing Gnome and E17 on the same OS?"
date: 2010-08-14
forum: New to Ubuntu
---

### Post by Nick_Jinn on 2010-08-14
Or LXDE and E17 for that matter. Say you wanted to have different default desktop environments for different users. What kind of problems can that cause besides incompatible apps?

---

### Post by yabbadabbadont on 2010-08-14
It shouldn't cause any problems at all.  Each user can select their default desktop environment every time that they login from GDM.  Their preference is stored in ~/.dmrc (I believe) and is what is used when they choose to use the "Last session" option on their next login.  As for app issues, other than them possibly not looking "pretty", they should all run fine in any desktop environment.

---

### Post by Nick_Jinn on 2010-08-14
Opinions about this seem to be all over the place.


Now, Elive is a Debian based operating system, compatible with Ubuntu and Mint, right? Should there be a problem with adding their repositories if I add E17 to Mint Gnome edition?

---

### Post by yabbadabbadont on 2010-08-14
It is almost always a bad idea to mix repositories from different distributions, even if they are all based on the same root distribution.

---

### Post by Nick_Jinn on 2010-08-14
What happens? Is it 'not popper' or will it bork my system?

---

### Post by yabbadabbadont on 2010-08-14
It can "bork" your system, but is not guaranteed to.  Generally speaking, if you are not aware of the potential issues, you really shouldn't try it.  :)  Stick to the official repositories and those that were built specifically for the version of Ubuntu you are using, such as launchpad ppa's.

---

### Post by bodhi.zazen on 2010-08-14
> **Nick_Jinn said:**
> Or LXDE and E17 for that matter. Say you wanted to have different default desktop environments for different users. What kind of problems can that cause besides incompatible apps?

Gnerally you can run as many desktop environments (gnemo/kde/xfce) or window managers (fluxbox, openbox (lde uses openbox), icewm, etc) as you wish, including E17.

The problems you might have would be

1. Disk space. With modern HD this is trivial.

2. Duplicate apps (kate/gedit/mousepad or k3b/brassero) in the menus.

3. slightly increased RAM due to loading KDE + gnome libs (trivial on modern hardware).

In general you can NOT mix and match repos. Just because it is a .deb does not mean you can run it on any .deb distro, and you can not easily mix and match Debian and Ubuntu reops 9ease / difficulty depends on which version of Ubuntu and Debian repos).

If you wish to run mixed repos, google search apt pinning.

[http://jaqque.sbih.org/kplug/apt-pinning.html](http://jaqque.sbih.org/kplug/apt-pinning.html)

[http://www.howtoforge.com/a-short-introduction-to-apt-pinning](http://www.howtoforge.com/a-short-introduction-to-apt-pinning)

[https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto)

From the third page :

> Pinning should never be used for installing Debian binary packages on Ubuntu. Ubuntu strongly recommends against using Debian binary packages on Ubuntu

It can be done (the geeks do it), but it can cause breakage.

---

### Post by murderslastcrow on 2010-08-15
The main issues I run into is using different themes in each, since it's all technically the same account, so changing the theme in one may alter it in the other. Also, the fonts used by e17 won't be the same used by GTK applications, so you'll have to modify them separately.

Other than those visual distinctions, you shouldn't run into any problems, and you can use as many DEs/WMs as you'd like.

---

### Post by Nick_Jinn on 2010-08-15
This is a very noobish question but what is the difference between a DE and WM? Can you use a different WM in Gnome?

---

### Post by Nick_Jinn on 2010-08-15
Thank you Bodhi. 

Now, how do I completely eliminate updates from the new sources showing up under 'update manager', yet allow the app list to be updated in Synaptic?

---

### Post by bodhi.zazen on 2010-08-15
> **Nick_Jinn said:**
> This is a very noobish question but what is the difference between a DE and WM? Can you use a different WM in Gnome?

A window manager is just the decorations - open / close / minimize boxes, mouse, keyboard, etc.

A DE is a Window manager (gnome uses compiz or metacity, XFCE xfwm4, and KDE some K manager) PLUS a suite of applications suchas Network manager, an editor, etc to make a more complete basic.

See also:

[http://xwinman.org/](http://xwinman.org/)

and

[http://penguinpetes.com/XWM_Guide/index.php](http://penguinpetes.com/XWM_Guide/index.php)

> **Nick_Jinn said:**
> Thank you Bodhi. 

Now, how do I completely eliminate updates from the new sources showing up under 'update manager', yet allow the app list to be updated in Synaptic?

from you post, I advise you simple disable update manager from starting automatically when you log in (Preferences -> start up applications).

You can always run update manager or synaptic or apt-get manually. You can configure automatic updates or security only updates via synaptic.

---

