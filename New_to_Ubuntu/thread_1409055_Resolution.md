---
title: "Resolution"
date: 2010-02-17
forum: New to Ubuntu
---

### Post by s.fletcher on 2010-02-17
Hi, I'm very new to Linux, I've manage to solve a few issue like sound, and installing a video card, but when I run a DVI/HDMI cable to my tv from my video card, I loose the top and bottom of the desktop, I've played around with the resolution with out any luck, it works fine with a VGA cable.

I'm running a nvidea 8400GS Video Card

Could any one help with this, thanks.

---

### Post by aeiah on 2010-02-17
this is an issue with your HDTV. most HDTVs, for some odd reason, overscan the image through hdmi. some give you an option to disable this.



if, like me, yours will always overscan you can create a custom modeline in your xorg.conf to create a bounding box but to be honest, this can be a bit of a nightmare. if you're using gnome you may want to simply consider placing panels in the invisible parts. it really depends what you're using it for. if you're just using it to watch movies the overscan doesn't really matter.. its the same overscan you'd get if you played a dvd in a dvd player.

---

### Post by s.fletcher on 2010-02-17
Ok, thanks... I've got another TV I can try it on... it is movies that I want to use this for.
Gnome... this may sound extremely stupid but how do I know if I'm using this or not, as I just to my knowledge I installed Ubunutu 9.10

---

### Post by tom.swartz07 on 2010-02-17
> **s.fletcher said:**
> Ok, thanks... I've got another TV I can try it on... it is movies that I want to use this for.
Gnome... this may sound extremely stupid but how do I know if I'm using this or not, as I just to my knowledge I installed Ubunutu 9.10

Gnome is the window manager. If you installed plain Ubuntu, then thats what you have.

There are other window managers; KDE and XFCE to name a few, all of them have special little tweaks that make them different than the others.

---

### Post by s.fletcher on 2010-02-17
Is there a choice that I have when I put the boot disc in? or do I need to download a new version.

What's best?

---

### Post by tom.swartz07 on 2010-02-17
> **s.fletcher said:**
> Is there a choice that I have when I put the boot disc in? or do I need to download a new version.

What's best?

Nope, you make the choice when you download the version of Ubuntu. KDE is packaged with Kubuntu, and XFCE is packed with Xubuntu. You could get the other versions after you install, but its kind of tricky.

I have a feeling that now, because you asked 'whats best' you will get about 1000000000 replies. This is probs the most heavily contested topic in all of Ubuntu.

For what you are using it for, Gnome is best. 

Gnome is probably best for balancing neat visual effects with a very productive and lightweight window manager.

KDE is great for impressing your friends with sweet visual effects, but if you dont have a perfectly working video card- itll be rough. KDE is probably just as popular as Gnome, and it features much more in-depth customizations- maybe too much for simply a media server that you described.

XFCE is a super lightweight window manager. Its used mostly on computers with low amounts of ram and old old video cards. Its really fast, but doesnt support many neat visual tricks.

You could read up more about each here: [http://www.psychocats.net/ubuntu/kdegnome](http://www.psychocats.net/ubuntu/kdegnome)

Hope this helps!

---

### Post by s.fletcher on 2010-02-17
Excellent that clears a lot up cheers.

---

### Post by aeiah on 2010-02-17
if you really want to get around this overscanning for movies then a few of the players allow you to create a black border, but like i said, when you watch dvds or TV they're always overscanned too, and films are converted to dvd with this in mind so they never put anything interesting in the 1cm around the edges.

---

