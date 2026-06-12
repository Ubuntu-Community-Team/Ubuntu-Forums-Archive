---
title: "What packages can I remove from Gnome?"
date: 2009-07-18
forum: New to Ubuntu
---

### Post by Mariane on 2009-07-18
I have just installed ubuntu 9.04 on an old computer with dual boot. Ubuntu has very little space on it. What package can I remove without destroying gnome?

Or should I try to remove gnome altogether and install some lighter gui? I remember seeing one but I don't remember it's name. 

Mariane

---

### Post by jerome1232 on 2009-07-18
I think it's easier to start with a base system and install what you need rather than figure out what you don't need and can remove.

There are MANY alternate Window Managers, xfce (comes with xubuntu) is very similar to gnome. There are others and they can look very nice when setup correctly.

I liked icewm and fluxbox quite a bit.

You could look through synaptic and start blasting away at programs you know aren't essential first and then go from there.

---

### Post by Mariane on 2009-07-18
My problem is that I don't know all the names... I tried fiddling with synaptic and nearly destroyed my system. 

Mariane

---

### Post by CatKiller on 2009-07-18
> **Mariane said:**
> dual boot. Ubuntu has very little space on it.

You could just give Ubuntu more space.

If you find that you are using a **lot** of space for Ubuntu, there are a [number of tips]("http://ubuntuforums.org/showthread.php?t=81840") to free up some space.

---

### Post by philcamlin on 2009-07-18
> **CatKiller said:**
> You could just give Ubuntu more space.

If you find that you are using a **lot** of space for Ubuntu, there are a [number of tips]("http://ubuntuforums.org/showthread.php?t=81840") to free up some space.

+1 

ubuntu uses 4gb as is

all you need is like 15gb tops to have alot of space 

dont remove stuff :popcorn:

my grandma blew hers up removing stuff :P

---

### Post by Mariane on 2009-07-20
It says to delete stuff from the root account but it does not say where this is... Should I be looking for a folder called "root"?

---

### Post by NightwishFan on 2009-07-20
Just remove some packages you do not want using synaptic. If it asks to remove 'ubuntu-desktop' that is fine, it will only remove the virtual package that keeps the whole desktop installed.

If you want all the software from Ubuntu back, just install ubuntu-desktop again.

Doing this should not cause problems, just search the main menu for software you do not use, such as fspot or openoffice. You can always get them back.

---

### Post by CatKiller on 2009-07-20
> **Mariane said:**
> Should I be looking for a folder called "root"?

Yes.

/root is the root account's Home folder. root's Trash is in there. Either at /root/.Trash or /root/.local/share/Trash, depending on your setup.

---

### Post by SuperSonic4 on 2009-07-20
In your situation I would recommend the Minimal CD and then you can add whatever packages you want from a base system. This would be a text based installer though

---

### Post by Bartender on 2009-07-20
Is this a desktop PC?
If so, I have a hardware-based suggestion.  Add a second HDD, install Ubuntu to that drive, and let Windows have the first drive back.  If you've got any geek friends I'll betcha you could bum a PATA HDD for free.  I assume the PC is PATA.  Does it have wide, flat ribbon cables coming off the backs of the drives?  If so, you'll have to make sure to set the little jumpers correctly.  Setting the jumpers is one of those tasks that's really easy, but confusing the first time.

Once you've got the second drive spinning and recognized correctly in BIOS, just make sure to install Ubuntu to sdb (the second HDD), not sda (the first HDD), and let GRUB install itself.  You'll end up with the same GRUB window at boot giving you a choice of operating systems, and GRUB will know that Ubuntu is on a separate drive.

---

### Post by colau on 2009-08-16
> **Mariane said:**
> I have just installed ubuntu 9.04 on an old computer with dual boot. Ubuntu has very little space on it. What package can I remove without destroying gnome?

Or should I try to remove gnome altogether and install some lighter gui? I remember seeing one but I don't remember it's name. 

Mariane
xfce may be the alternative for gnome, if you want lighter gui.
You can get command to have pure gnome other.
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by XubuRoxMySox on 2009-08-16
The *most* lightweight desktop environment available by far is [LXDE]("http://lxde.org"). Graphical like Xfce (Xubuntu) but simpler and much faster.

It's so lightweight, in fact, that it is often accused of not even being a true desktop environment at all. Yet it has a built in file manager (PCManFM) and customizability and even works with Compiz if you want to add some eye candy (but you want light weight).

```
sudo apt-get install lxde
```

LXDE on top of a minimal Ubuntu installation works sweetly and runs at mind-bending speed on my old Dell.

But for anything less than 256 RAM I would encourage you to use Damn Small Linux instead. You can install the ultralight graphical desktop (LXDE) for a super-simple, superfast Debian-based custom mixture that will kick butt on an old 'puter!

-Robin

---

### Post by Mariane on 2009-09-07
Thank you all for your suggestions. Yes, I have the ribbon cables. The PC is an IBM IntelliStation M Pro. 

Mariane

---

