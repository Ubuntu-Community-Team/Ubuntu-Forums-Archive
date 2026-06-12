---
title: "Simple question: Share a home folder with X-, K-, and Ubuntu?"
date: 2011-08-15
forum: New to Ubuntu
---

### Post by Lucypie on 2011-08-15
I want to triple boot Xubuntu, Kubuntu, and Ubuntu. Any way to share all 3  home folders? Any way to share settings (or is that in the home folder.. some is in home). 

I have a 300G drive, so theres 97.3 GB for each one + 8G swap. Is this good?

---

### Post by cbowman57 on 2011-08-15
Is it really the /home folders that you want to share or what's stored inside them? ie. Downloads, Music, etc..

---

### Post by Lucypie on 2011-08-15
Everything. I want to be able to go from Ubuntu to Kubuntu, and still have the same things on my desktop and in my downloads as on Ubuntu.

---

### Post by cbowman57 on 2011-08-15
You can do it, but I wouldn't recommend it.  Your configuration gets screwed up in one there is a possibility you won't be able to get into any of your desktops, but that's just my opinion.

If it's just your Downloads that you want to share you can put that on a partition of it's own and mount it with an entry in the fstab.  That way all three environments can share the same folder.  Assuming your Downloads directory is the only one you use to collect a lot of files, your actual root/home partition can be about 20 GB.

You could also just install Xfce & KDE onto your Ubuntu installation.  Would accomplish the same thing but save a ton of space.

---

### Post by Lucypie on 2011-08-15
> **cbowman57 said:**
> 
You could also just install Xfce & KDE onto your Ubuntu installation.  Would accomplish the same thing but save a ton of space. That sounds better, personally. How can this be accomplished?

---

### Post by cbowman57 on 2011-08-15
I'm not in Ubuntu right now, but in synaptic there should be something like kde-standard or kde-desktop, they may go by another name but they are metapackages for installing the same applications & environment that comes with kubuntu.  Look for a metapackage with xfce4 in it for the xubuntu desktop.  Then you just select the one you want from the login screen.

---

