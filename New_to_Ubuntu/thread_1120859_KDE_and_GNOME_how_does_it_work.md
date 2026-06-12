---
title: "KDE and GNOME: how does it work?"
date: 2009-04-09
forum: New to Ubuntu
---

### Post by eeeandrew on 2009-04-09
hi all, I've been using the GNOME desktop since I started ubuntu 2 years ago. I recently saw some screenshots of the kubuntu desktop and it looks great. I read in some forum posts that its possible to have both desktops installed and to choose between them at the login screen. 

My question is: how exactly does this work? 

Is nautilus used by both desktops or does it change to the KDE window manager?

Can I still view all my files?

Are there likely to be any conflicts between GNOME and KDE that could cause problems?

Thanks in advance,
Andrew

---

### Post by mdsmedia on 2009-04-09
> **eeeandrew said:**
> hi all, I've been using the GNOME desktop since I started ubuntu 2 years ago. I recently saw some screenshots of the kubuntu desktop and it looks great. I read in some forum posts that its possible to have both desktops installed and to choose between them at the login screen. 

My question is: how exactly does this work? 

Is nautilus used by both desktops or does it change to the KDE window manager?

Can I still view all my files?

Are there likely to be any conflicts between GNOME and KDE that could cause problems?

Thanks in advance,
Andrew

In general, you can have KDE desktop installed alongside Gnome. I've had it installed that way and had no problems.

Yes, your files are accessible from either desktop.

No conflicts that I know of cause problems. There are strange effects on your Gnome desktop, like KDE look in some windows, but nothing that caused any problems.

---

### Post by fazza on 2009-04-09
actually, I'm not completely sure what is meant to/does happen, but I've found (and it's really annoying) that lots of my gnome-apps become defaults in kde. I'm sure it's not right... eg, I click the file-browser link from the file plasmoid, and nautilus opens instead of dolphin. Or rhythmbox opens instead of amarok. And, openoffice stays gnome-themed instead of switching to the kde themes.

any help with that? Perhaps I was meant to select the kde task in synaptic, but i didn't know about that then...

---

### Post by JoshuaRL on 2009-04-09
No, you can use both.  When you login, under Sessions, choose KDE and it will boot into that.  KDE in Intrepid by default uses Dolphin for file management.  I've used both, and personally I like Dolphin better.  But you have to get used to the one-click way of doing things.  :)

If you want to try it out, do the following:
```

sudo aptitude install kubuntu-desktop

```
That will install everything you need to have to get the full Kubuntu experience.  There's also "kdebase" you could install if you don't want all of it.

You can also try out XFCE the same way:
```

sudo aptitude install xubuntu-desktop

```
Something else to keep in mind is that these are -desktop packages are what's called meta-packages.  They actually contain nothing, but point to a bunch of other packages needed to make that meta-package.  The reason this is important is that apt-get doesn't know how to remove those.  So while you can feel free to apt-get install them, if you ever decide to remove them, you'll need to use aptitude.

---

### Post by mdsmedia on 2009-04-09
In terminal use

```
apt-get install kubuntu-desktop
```
to install the KDE desktop. Then you can use either on login, or switch between them at your leisure.

---

### Post by mdsmedia on 2009-04-09
> **JoshuaRL said:**
> No, you can use both.  When you login, under Sessions, choose KDE and it will boot into that.  KDE in Intrepid by default uses Dolphin for file management.  I've used both, and personally I like Dolphin better.  But you have to get used to the one-click way of doing things.  :)

If you want to try it out, do the following:
```

sudo aptitude install kubuntu-desktop

```
That will install everything you need to have to get the full Kubuntu experience.  There's also "kdebase" you could install if you don't want all of it.

You can also try out XFCE the same way:
```

sudo aptitude install xubuntu-desktop

```
Something else to keep in mind is that these are -desktop packages are what's called meta-packages.  They actually contain nothing, but point to a bunch of other packages needed to make that meta-package.  The reason this is important is that apt-get doesn't know how to remove those.  So while you can feel free to apt-get install them, if you ever decide to remove them, you'll need to use aptitude.
While I don't disagree at all, just to clarify. If you want to remove them you need to INSTALL using aptitude, in order to remove using aptitude.

---

### Post by JoshuaRL on 2009-04-09
> **mdsmedia said:**
> While I don't disagree at all, just to clarify. If you want to remove them you need to INSTALL using aptitude, in order to remove using aptitude.

Yeah, you're right.  Sorry for the confusion.

---

### Post by mdsmedia on 2009-04-09
I rarely make a post which doesn't need to be edited for clarification :lolflag:.

---

### Post by fazza on 2009-04-09
how do you stop kde using default gnome-apps and vice versa though? mine does it all the time, and I installed kubuntu-desktop...

---

