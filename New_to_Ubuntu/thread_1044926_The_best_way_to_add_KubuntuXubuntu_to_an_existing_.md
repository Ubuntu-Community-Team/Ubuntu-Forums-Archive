---
title: "The best way to add Kubuntu/Xubuntu to an existing Ubuntu installation?"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by biggiemokey on 2009-01-19
So I have Ubuntu 8.10 installed and I tried to install Kubuntu by downloading kubuntu-desktop package.  This caused my loading screen to change to Kubuntu, which I did not want to happen.  I have read a thread about splash screens changing and I'm pretty sure I can follow the directions there to fix it.  However, after my Kubuntu install the fan on my computer got louder and the air expelled was hotter.  I DO NOT want that to happen, that is a much bigger deal than the splash screens.  Also, choosing to boot into a KDE session didn't seem to be any different, except it wouldn't connect to my wireless network.  It also changed (unless it was always that instead of Gnome) my default session to Xfce.Client, which I do not understand since that sounds like Xubuntu, which I didn't install.  I then did a fresh install of Intrepid to fix the problems.

So, since I still want to install Kubuntu and Xubuntu, how would I go about doing it without messing up my fan and splash screens?  I would like to know the best way -  a little Googling led me to think downloading kubuntu-desktop was the best way but it did not work for me.  Any help is greatly appreciated.

---

### Post by dnRoyston on 2009-01-19
for me, I simply installed xubuntu-desktop, but that's not exactly kubuntu. For Xubuntu, it should do either of those, it didn't for me. As for Kubuntu, someone else will post it, because I have no idea.

---

### Post by 2hot6ft2 on 2009-01-19
Here you go. THis will lead you thru it.
[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

---

### Post by biggiemokey on 2009-01-19
Thanks, that's what I did but it just didn't seem to work - I guess I'll try again.  But when I chose the session "KDE" it said my default session was X<something>.client.  Is that normal?  I figured Gnome would be default in Ubuntu.

---

### Post by Primefalcon on 2009-01-19
```
sudo apt-get install kubuntu-desktop
```
or
```
sudo apt-get install xubuntu-desktop
```

---

### Post by 2hot6ft2 on 2009-01-19
> **biggiemokey said:**
> Thanks, that's what I did but it just didn't seem to work - I guess I'll try again.  But when I chose the session "KDE" it said my default session was X<something>.client.  Is that normal?  I figured Gnome would be default in Ubuntu.
I run Ultimate Edition which already has both KDE and Gnome it even has some Xfce apps but I don't switch back and forth for several reasons.

First I like the gnome desktop better. I have read that if you switch back and forth you'll end up having some kind of artifacts from the other desktops show up. Beats me but I didn't like the way it sounded.

If you want to try each I would either try them with the livecds or do an install for each and try them out that way. Or use the Ultimate Edition which has the best of all 3 and choose the one you like the best.

You can use kde apps in gnome and vise versa.

---

### Post by biggiemokey on 2009-01-20
Thanks, just did a fresh install and I'm trying it out now.  Hopefully it won't make my fan loud.

---

### Post by pansz on 2009-01-20
> **biggiemokey said:**
> a little Googling led me to think downloading kubuntu-desktop was the best way but it did not work for me.  Any help is greatly appreciated.

Yes it is the best way, the only thing you need is to "change your mind" to the linux philosophy: Fresh-reinstall does not solve problems, you need to face directly to the problem.

So, if your problem is the loud fan, then search for how to solve the problem of the loud fan. Don't try to re-install your kubuntu since re-installation isn't intresting at all. once set up you won't need to reinstall your Linux in *years*.

---

### Post by biggiemokey on 2009-01-20
Good, that's the kind of stability that I want.  Doing a fresh install did seem to quiet my computer down, but I downloaded Kubuntu and didn't turn on Ubuntu afterwards.  When I get to my home computer I'll see how it goes, I really don't like doing fresh installs but I would rather do that then have a loud computer.  I have done two fresh installs after installing Ubuntu initially, by keeping the /home partition and reformatting the /root.  All my Firefox addons and desktop icons seem to stay, is that normal?  If so the /home partition is very intuitive.

---

### Post by biggiemokey on 2009-01-20
Kubuntu seems to be working fine, although I'm not sure about Konqueror, but I've never used it before so maybe it's supposed to be like that.  The fan does get loud at times but then quiets down when not in use, it's not a constant sucking noise and my computer isn't acting as a space heater, so I think it's good, thanks for the help.  Two questions though:

1.  Now when I boot up the boot menu (Grub?) shows two Ubuntus - Ubuntu 8.10, kernel 2.6.27-9-generic and Ubuntu 8.10, kernel 2.6.27-7-generic.  There doesn't seem to be a difference, except that -9- has Kubuntu loading screens, while -7- has an Ubuntu load up screen and Kubuntu shut down screen.  I did a fresh install before installing Kubuntu and didn't notice these two different options, so I think it came from installing Kubuntu-desktop, but I guess I could have missed it before.

2.  What is "Run Xclient script"?  It is my default session, which I figured would be Gnome.

---

