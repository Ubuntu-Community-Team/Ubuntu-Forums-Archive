---
title: "Which one am I using? Ubuntu or Kubuntu"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by ozark_hillbilly on 2010-01-17
Awhile back (6 mths or so) I had lost my graphical desktop interface (using Ubuntu 8.10) after my email app Evolution got screwed up royally.

As a temporary solution it was recommended I dump the graphical interface that comes with the Ubuntu distro and try something else.
So I loaded Kubuntu and it started up fine. I never did go back to the Ubuntu GUI. 

Now I have upgraded to 9.04. When the computer boots I get the Kubuntu screen on startup. Am I running Kubuntu or Ubuntu? I think it is Kubuntu as it is just the GUI and doesn't change with an upgrade. Is this the correct way to look at it?

Ed

---

### Post by OlyPerson on 2010-01-18
Ubuntu uses GNOME and Kubuntu uses KDE.  Just look up pictures of both online and see which you have, shouldn't be hard unless I'm not understanding correctly.  And it should stay with whichever WM you chose after it updates still.

---

### Post by warfacegod on 2010-01-18
It sounds like you installed Ubuntu first and then put the KDE desktop into it. I guess you might say you are running a hybrid of the two? Anyway you can use the terminal to find out:

```
uname -o
```

If it says GNU/Linux its Ubuntu

If KDE/... Kubuntu

---

### Post by baddog144 on 2010-01-18
> **warfacegod said:**
> It sounds like you installed Ubuntu first and then put the KDE desktop into it. I guess you might say you are running a hybrid of the two? Anyway you can use the terminal to find out:

```
uname -o
```

If it says GNU/Linux its Ubuntu

If KDE/... Kubuntu

I'm running Kubuntu, and it still says GNU/Linux :|

EDIT: When you boot the computer , if it has a Kubuntu splash screen, I think that's a pretty sure indicator you're using Kubuntu.

---

### Post by audiomick on 2010-01-18
As far as I understand it, the difference doesn't go too deep. I don't know how much comes with the Ubuntu desktop (gnome) and the Kbuntu desktop (KDE) respectively, but it is fair to say that the package manager takes pretty good care of making sure you have all the dependencies you need.

Chances are, your system is a bit of a hybrid compared to a standard Ubuntu or Kbuntu, but don't let that worry you. That could also become the case if you install a KDE application onto an Ubuntu system (or a gnome application onto a KDE), because the dependencies might mean that you have loaded components of the other desktop to the one you have in order for the appication to be able to run.

My system started out as an Ubuntu Studio, has been re-installed as a standard Ubuntu, but had the old package list imposed on it to get all the programs back, so I have no idea how close it is to either of the starting points. I plan on doing a fresh install when 10.04 comes out, and installing the programs I really want by hand, as I have a lot of stuff installed that I don't really need, but for the time being it is all working quite happily.

Anyway, the important bits of the system, i.e. everything under the GUI, is basically the same. Having a "hybrid" wont disturb your updater. It just keeps track of what is installed and keeps that up to date. It doesn't know and doesn't particularly care which flavour you have. 

If it annoys you that it is not a "real" Kbuntu, Ubuntu or whatever, you could think about a fresh install when 10.04 has been out long enough to see that it is healthy and stable. That will give you time until then to get prepared for a "pain free" re-install, i.e. get backups done, organize a list of things you need to install additionally and so on.

---

### Post by Zorael on 2010-01-18
I remember reading someone saying that the threshold is passed after installing **kubuntu-default-settings**. If it's installed, it's Kubuntu. If not, it's Ubuntu. I found that a bit harsh. I'd just say to choose which to associate yourself with and stick with that.

Now, if we could all agree to rename Ubuntu to **G**ubuntu, with the G for GNOME, then it would logically follow that Ubuntu would be terminal stuff and libraries. The core of all its flavors; Kubuntu, Gubuntu, Xubuntu, Edubuntu, Xubuntu, etc. Then it'd make sense. :3

---

### Post by warfacegod on 2010-01-18
> **Zorael said:**
> I remember reading someone saying that the threshold is passed after installing **kubuntu-default-settings**. If it's installed, it's Kubuntu. If not, it's Ubuntu. I found that a bit harsh. I'd just say to choose which to associate yourself with and stick with that.

Now, if we could all agree to rename Ubuntu to **G**ubuntu, with the G for GNOME, then it would logically follow that Ubuntu would be terminal stuff and libraries. The core of all its flavors; Kubuntu, Gubuntu, Xubuntu, Edubuntu, Xubuntu, etc. Then it'd make sense. :3

Elegant words by a sock puppet.:D:D

---

