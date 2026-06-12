---
title: "ubuntu-xubuntu"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by keygiwawah on 2008-12-10
Does the size of xubuntu really make enough of a difference in the speed of my computer.  I'm running on really low ram right now like .5 GB.

---

### Post by Titan8990 on 2008-12-10
Xubuntu, not really. Other OSes that use XFCE, yes.

---

### Post by Michael.Godawski on 2008-12-10
Xubuntu is the light-weight version of Ubuntu. 
> **Minimum system requirements**

 To run the Desktop CD (LiveCD + Install CD), you need 128 [MB]("http://en.wikipedia.org/wiki/Megabyte") [RAM]("http://en.wikipedia.org/wiki/RAM") to run or 192 [MB]("http://en.wikipedia.org/wiki/Megabyte") [RAM]("http://en.wikipedia.org/wiki/RAM") to install. The Alternate Install CD only requires you to have 64 [MB]("http://en.wikipedia.org/wiki/Megabyte") [RAM]("http://en.wikipedia.org/wiki/RAM").  To install Xubuntu, you need 1.5 [GB]("http://en.wikipedia.org/wiki/Gigabyte") of free space on your hard disk.  Once installed, Xubuntu can run with 192 MB RAM, but it is strongly recommended to have at least 256 MB RAM.

If you experience real unbearable slowness on Ubuntu I would try out Xubuntu.
```

sudo apt-get install xubuntu-desktop
```

---

### Post by ajcham on 2008-12-10
According to this article [(LINK)]("http://hightechsorcery.com/2008/10/evaluating-desktop-environments-ubuntu-810-intrepid-ibex"), Xubuntu only used about 20MB less RAM than a standard Ubuntu install using Gnome, so the performance benefit would be minimal.

---

### Post by Titan8990 on 2008-12-10
Although it is not an official release fluxbuntu is another ligtweight variant that is an option for you.

---

### Post by snowpine on 2008-12-10
Crunchbang is another unofficial Ubuntu variant that I find to be even faster than Xubuntu.

---

### Post by Titan8990 on 2008-12-10
Now I feel I should point out the **fastest**.


It is not an official or unofficial release, just a window manager. It takes some configuring to get it set up right but joe's window manager (jwm), is the fasted GUI environment I have used a *buntu system.

---

### Post by dawynn on 2008-12-10
And don't forget Opengeu.  E17 (Enlightenment) mixed with enough Gnome to make an operating system.  Plenty of eye candy, even on a slow machine.  It's beautiful.  Its intended for use alongside the Ubuntu repositories.

[http://opengeu.intilinux.com/Home.html](http://opengeu.intilinux.com/Home.html)

Worth noting that they don't advertise it, but they do have 'Intrepid' directories in their repositories.  Evidently, they don't consider the Intrepid release stable enough to advertise, yet.

---

### Post by keygiwawah on 2008-12-10
Where can I find all of these unofficial releases?

---

### Post by Titan8990 on 2008-12-10
[http://en.wikipedia.org/wiki/List_of_Ubuntu-based_distributions](http://en.wikipedia.org/wiki/List_of_Ubuntu-based_distributions)

---

### Post by keygiwawah on 2008-12-10
What about that Joe's Window Manager... How complicated is it to get that running?

---

### Post by mkvnmtr on 2008-12-10
If I understand right you hava about half a gigibite or 500MB. That should be enough to run Ubuntu. If you want something install the minimal disk of ubuntu and nanly add what you want. Google Ubuntu minimal install. First page you will find where to install and some pages of how to install.

---

### Post by keygiwawah on 2008-12-10
Well I have a small windows partition on my hard drive for school, so I'm just trying to use the smallest one I can find.

---

### Post by Michael.Godawski on 2008-12-10
Additionally you can check with the command
```
top
```
what the biggest "RAM-eaters" are.

Linux uses as much RAM as it can. So do not be concerned, because you should have a swap partition which backs your system up.

---

### Post by keygiwawah on 2008-12-10
Oh I didn't know that... I think I'll just try Ubuntu.  If that doesn't work out I will probably try JWM just to learn about it more.  Does anyone have like a tutorial or something on how to configure it?

---

### Post by bodhi.zazen on 2008-12-10
Of the 3 Xubuntu is the fastest. The main benefit comes from using lighter weight apps (abiword in place of OpenOffice).

Performance depends on factors other then RAM, especially on Linux.

You can tell if you are limited by RAM with ```
free
```

If you are using swap, yo are low on RAM.

Yo could try this : [http://code.google.com/p/compcache/](http://code.google.com/p/compcache/)

There is a noticeable boots in speed on xubuntu compared to K/Ubuntu, but if that is not enough, see :

[http://ubuntuforums.org/showthread.php?t=575456](http://ubuntuforums.org/showthread.php?t=575456)

---

### Post by lykwydchykyn on 2008-12-10
Just open synaptic, install the jwm package.  Then log out and under the "session" menu, choose jwm.  Log back in.

Easy peasy.

By the way, if you're interested in trying some alternative window managers, there is no shortage of them:

 - icewm: similar to jwm, has the toolbar and menu at the bottom like Windows
 - afterstep/wmaker: both modeled after NeXTstep (an ancestor of OSX)
 - fluxbox/openbox: similar, very minimal interface with a right-click menu instead of a traditional taskbar menu.

That's just the tip of the iceberg.  Fvwm, enlightenment, ion2 -- all good stuff, just different ways of interacting with the computer.  Pretty much all of them are just a matter of installing a package and logging back in.

---

### Post by cardinals_fan on 2008-12-10
> **keygiwawah said:**
> Does the size of xubuntu really make enough of a difference in the speed of my computer.  I'm running on really low ram right now like .5 GB.
500 MB is a lot of RAM.  I would use just a window manager (Fluxbox is good) or Xfce (not the whole Xubuntu package).
> **keygiwawah said:**
> What about that Joe's Window Manager... How complicated is it to get that running?
It's not too hard, but I think Fluxbox is better.
> **keygiwawah said:**
> Oh I didn't know that... I think I'll just try Ubuntu.  If that doesn't work out I will probably try JWM just to learn about it more.  Does anyone have like a tutorial or something on how to configure it?
I would recommend Fluxbox over JWM.  A tutorial is here: [https://help.ubuntu.com/community/Fluxbox](https://help.ubuntu.com/community/Fluxbox)

You might also like this guide: [http://linuxowns.wordpress.com/2008/07/22/fluxbox_on_ubuntu_guide/](http://linuxowns.wordpress.com/2008/07/22/fluxbox_on_ubuntu_guide/)

---

### Post by keygiwawah on 2008-12-11
Thanks for the tutorials... they helped out a lot.

---

### Post by Locke_99GS on 2008-12-11
My other machine is a 500mhz K6-2 with 384m RAM - It runs Xubuntu Hardy well enough, only consuming 80m of RAM after login.

I seldom log into it, but it is always running, hosting MPD to the network.

---

### Post by keygiwawah on 2008-12-12
I just set up a new machine with a windows partition... For the other partition I'm trying xubuntu, which is working just fine.

---

