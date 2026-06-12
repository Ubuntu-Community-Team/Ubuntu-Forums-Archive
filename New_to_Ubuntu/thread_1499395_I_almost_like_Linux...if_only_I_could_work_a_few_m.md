---
title: "I almost like Linux...if only I could work a few more things out...."
date: 2010-06-01
forum: New to Ubuntu
---

### Post by CaptMorgane on 2010-06-01
I installed ubuntu over the week-end and am getting comfy with it, but there are a couple of things that are preventing me from letting windoze go.

1) itunes - I haven't found a way to get it to install, even with wine. Nor have I found a substitute.

2) Sound driver - I have a good sound setup on my laptop which sounded great with my old OS. I even installed winamp w/wine, but the volume doesn't go high enough, and it sounds tinny.

Can anyone help/advise?

---

### Post by marshmallow1304 on 2010-06-01
From what I've read, iTunes is best run in a Virtualized Windows environment using software such as [Virtualbox]("http://www.virtualbox.org/wiki/Linux_Downloads").

As for sound, how is it in native (non-Wine) apps?  Wine's sound can be flaky.

---

### Post by hogarth on 2010-06-01
> **CaptMorgane said:**
> 1) itunes - I haven't found a way to get it to install, even with wine. Nor have I found a substitute.

As far as substitutes go, i would definitely suggest Amarok.

---

### Post by Frdbrkl on 2010-06-01
"2) Sound driver - I have a good sound setup on my laptop which sounded great with my old OS. I even installed winamp w/wine, but the volume doesn't go high enough, and it sounds tinny."

First...solve sound issues by installing and running gnomealsa-mixer.  Check and make sure your preferred devices aren't muted or disabled here.

Once your sound is up to *average*, improve by installing and configuring pulseaudio-equalizer.  See this link:

[http://ubuntuforums.org/showthread.php?t=1308838&highlight=equalizer](http://ubuntuforums.org/showthread.php?t=1308838&highlight=equalizer)

I'm running Studio Ubuntu 10.04 X64, and had the same issues, concerns.  I loaded the eq program tonite, and so far I'm impressed.  No problems with install either.

You WILL HAVE TO "apply" changes each time they're made-the sliders don't change at movement, only after the apply button is hit.

Awesome, and my hats off to psyke83. Good on ya, mate.

EDIT: as an afterthought....iTunes????  WTF for?  I loaded that drivel onto a machine when it first came out and uninstalled it within minutes.  Resource hog, digital rights nazi, proprietary to the teats, and so closed source even their own engineers probably don't know what's in the package. No thanks.  I'm too open(source) minded.

---

### Post by waynefoutz on 2010-06-01
you need to let go of your Windows apps to take full advantage of Ubuntu. If you want to move on to a different OS, it's best to move on to different programs. Winamp under WINE is unnecessary, open up synaptic package manager and install Audacious, it's the Linux equivalent to Winamp, it can even be skinned, and has a look-alike winamp skin. And it's much faster. Wine trying to use Ubuntu's pulseaudio is never going to be as good as a native program. For an Itunes replacement, there are many alternatives. Amarok, Banshee, Rhythembox, gtkpod, and Songbird are all good. It won't hurt anything to install them all, because they do have subtle differences. If you must use iTunes, the best way to install it that I've found is with PlayonLinux, a front end for WINE. It will download it and set it up for you, but it's slow and buggy.

WINE's pulseaudio (what Ubuntu uses) drivers are pretty new. They're ok for some games. But I wouldn't expect too much sound quality out of WINE.

---

