---
title: "Careless Evolution Uninstall leads to Gnome/Nautilus Uninstall?"
date: 2009-08-10
forum: New to Ubuntu
---

### Post by jzacsh on 2009-08-10
Hello,

I don't know if this is going to necessarily help me, but maybe it'll keep others from making the same mistake.

I've been wondering why after about a week of using my eee pc, suddenly ubuntu stops working past the login screen, and only failsafe terminal works. I think I've been carelessly uninstalling Evolution, via synaptic, and in turn also uninstalling GNOME or Nautilus. (I'm going to try the following command when i get home today, and find out for sure).

*these are a guess* (I don't know enough about the debian package system, to figure out if simply typing "gnome" and "nautilus" will do the job here.)
```
sudo apt-get install gnome
sudo apt-get install nautilus

```
Just thought I'd put it out there, as it was driving me crazy for a while. Hope no one else has this same issue.

---

### Post by wojox on 2009-08-10
If you uninstall evolution it takes ubuntu-desktop with it.
```
sudo apt-get install ubuntu-desktop
```

---

### Post by jzacsh on 2009-08-10
> **wojox said:**
> If you uninstall evolution it takes ubuntu-desktop with it.
```
sudo apt-get install ubuntu-desktop
```

thank you! is this common knowledge? something that has been posted about  a ton of times? (I tried searching for it before posting; other than not duplicating a post, I'd like to know more  - like how come?)

---

### Post by Paddy Landau on 2009-08-10
> **jzacsh said:**
> thank you! is this common knowledge? something that has been posted about  a ton of times? (I tried searching for it before posting; other than not duplicating a post, I'd like to know more  - like how come?)
I guess most people just don't uninstall Evolution.

Ubuntu comes with a bunch of preinstalled packages. Generally, just leave them alone unless you have a severe disk space shortage. It's not as if extra programs slow down Linux (unlike Windows where you have registry problems and the like).

---

### Post by jzacsh on 2009-08-10
> **Paddy Landau said:**
> I guess most people just don't uninstall Evolution.

Ubuntu comes with a bunch of preinstalled packages. Generally, just leave them alone unless you have a severe disk space shortage. It's not as if extra programs slow down Linux (unlike Windows where you have registry problems and the like).

well, i just figured i'd save every possible byte, since its a netbook (only 16gb of space.). also, being its a netbook, i absolutely do not need an email client on the machine (or anything really outside of a browser and some basic office programs). I mean, i'm not complaining: if I have to just suck it up and keep evolution, I'll survive - this operating system is free (and awesome) so there's not much I can say.

Thanks for the help :)

---

### Post by Paddy Landau on 2009-08-10
> **jzacsh said:**
> only 16gb of space
How much space have you already taken up? I'm guessing not much more than 2Gb unless you have loads of music and videos.

If you're interested, you can get rid of old kernels.

There are plenty of posts about clearing out old stuff, but really it's not significant.

---

### Post by oldos2er on 2009-08-10
You can use aptitude or Synaptic Package Manager to remove Evolution without removing any necessities such as ubunutu-desktop. ubuntu-desktop is just a metapackage that a system can live without (unless or until you run a dist-upgrade).

---

### Post by jzacsh on 2009-08-10
> **Paddy Landau said:**
> How much space have you already taken up? I'm guessing not much more than 2Gb unless you have loads of music and videos.

If you're interested, you can get rid of old kernels.

There are plenty of posts about clearing out old stuff, but really it's not significant.

the files i'd be bringing onto my netbook would probably add up quite a bit. they're mostly web development files, programming file, scripts, etc. and not really any music (*I figure that's what pandora's for - though I'd like to start trying magnatune*). to be honest it won't add up to 16 gb, but ubuntu takes up a bit of space itself and i was toying with the idea of Windows 7 beta inside of Virtual box (*the netbook has 1gb ram, so i figure why not?*)

> **oldos2er said:**
> You can use aptitude or Synaptic Package Manager to remove Evolution without removing any necessities such as ubunutu-desktop. ubuntu-desktop is just a metapackage that a system can live without (unless or until you run a dist-upgrade).

I figured I'd be able to properly remove it w/o removing ubuntu-desktop, but how? Should I go through all the items that got "checked" off for removal in the process, and read about each one to make sure its only Evolution specific (*I did try the first time around, and only noticed some nautilus/pidgin/evolution stuff*)?

---

### Post by Sarai the Geek on 2009-08-10
There's always the Ubuntu Minimal Install, wherein you can choose what programs you want and it just doesn't install any of the others- more of an Arch mindset.
You can always install stuff ala carte later if you find you need it.

---

### Post by Paddy Landau on 2009-08-10
> **jzacsh said:**
> i was toying with the idea of Windows 7 beta inside of Virtual box (*the netbook has 1gb ram, so i figure why not?*)
I suspect that 1Gb RAM won't be enough for Windows inside a Virtual Box.

If you're adding Windows to the mix, then indeed 16Gb will be insufficient. Windows takes a huge amount of space.

Have you considered installing Windows to an external USB drive, or upgrading your system with a hard drive?

---

### Post by oldos2er on 2009-08-10
> **jzacsh said:**
>  I figured I'd be able to properly remove it w/o removing ubuntu-desktop, but how? Should I go through all the items that got "checked" off for removal in the process, and read about each one to make sure its only Evolution specific (*I did try the first time around, and only noticed some nautilus/pidgin/evolution stuff*)?

 Using Synaptic should work the way you described. **sudo aptitude remove evolution** should also work.

---

### Post by jzacsh on 2009-08-14
> **Sarai the Geek said:**
> There's always the Ubuntu Minimal Install, wherein you can choose what programs you want and it just doesn't install any of the others- more of an Arch mindset.
You can always install stuff ala carte later if you find you need it.

oh wow, that's awesome, i didn't know about that. is this something that would be done from the installer CD? (in the "press F# for more options"?)

> **Paddy Landau said:**
> I suspect that 1Gb RAM won't be enough for Windows inside a Virtual Box.

If you're adding Windows to the mix, then indeed 16Gb will be insufficient. Windows takes a huge amount of space.

Have you considered installing Windows to an external USB drive, or upgrading your system with a hard drive?
I would consider it, but i'm not sure its worth it - it was just to play around (wanted to see windows 7 on a netbook), ubuntu serves me just fine.

> **oldos2er said:**
> Using Synaptic should work the way you described. **sudo aptitude remove evolution** should also work.
oh, great.. i'll definitely just try that next time, thank you!

anyways, thank you to everyone! my problem was solved very quickly when i logged in and ran:
```
sudo apt-get install ubuntu-desktop
```

---

