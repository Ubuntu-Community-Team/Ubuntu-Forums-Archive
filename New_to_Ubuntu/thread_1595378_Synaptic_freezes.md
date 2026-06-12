---
title: "Synaptic freezes"
date: 2010-10-13
forum: New to Ubuntu
---

### Post by beew on 2010-10-13
I have installed Maverick on a 40G external drive. I was very happy with its performance until I notice that Synaptic feezes quite often. I don't know if it is a bug or if it is because the installation is on an external drive or the drive is old or because I am using ext4 instead of ex3. I have installed Lucid on an external drive before (ext3) and this has never happened.

I wonder if anyone else has experienced the same problem.

---

### Post by ibuclaw on 2010-10-13
I assume you mean 'freezes' rather than 'feezes' - because it would be odd if a program worried alot. ;)

Is your problem reproducible? Care to walkthrough the steps?

---

### Post by beew on 2010-10-13
> **ibuclaw said:**
> I assume you mean 'freezes' rather than 'feezes' - because it would be odd if a program worried alot. ;)

Is your problem reproducible? Care to walkthrough the steps?

Basically I clicked on Synaptic, it asks for password. I gave the password, it opened and the little circle thingy started rotating forever and synaptic's screen went dim and everything was frozen and I have to turn off power to reboot.

Seems like maybe I have installed something (probably R-cmdr from the repo, as there are missing packages and R had to pull them from its mirrors). I noticed that installing programs is a bit tricky in Maverick, probably because the packaging was a bit rushed. A few days ago I busted the system while trying to install something from a PPA (so after that I am holding off adding PPAs) Today I got an error about something trying to overwrite something already in use blah blah while trying to update Linux-header (suggested by update-manager), I end up having to lock the version.

---

### Post by ibuclaw on 2010-10-13
What repositories do you have enabled? Go to 'System->Admin->Software Sources' and 
check the Ubuntu and Other software tabs.

And do you have any broken packages on the system?
```
sudo apt-get install -f
```
Should attempt to satisfy all package dependencies if one or more are broken.

---

### Post by beew on 2010-10-13
> **ibuclaw said:**
> What repositories do you have enabled? Go to 'System->Admin->Software Sources' and 
check the Ubuntu and Other software tabs.

And do you have any broken packages on the system?
```
sudo apt-get install -f
```Should attempt to satisfy all package dependencies if one or more are broken.

Sudo apt-get install -f and the system freezes as well (pretty much whenever apt-get anything it freezes, kind of expected as Synaptic is just a front end to apt).

No, I don't have anything else on my sources list except the "official" repositories (checked all the boxes in Synaptic and that's it). Like I said, I installed R-cran-cmdr from the repo but when I started the R dialogue said there were missing packages and it pulled a bunch of stuffs from its mirrors (with my permission of course), so maybe something it pulled caused a conflict?

I am not sure if there are broken packages, if there were installation would have stopped abnormally somehow and there would be a warning on the panel (at least that is how it works in  Lucid). But installation from Synaptic went smoothly (apparently) and there is no warning.

I am doing a fresh installl since I have nothing on my system yet. I think I will just hold off installing stuffs and stick to updates and perhaps only the very basic things for a few days and see what happens. I read somewhere on the forums that things tend to be a bit confusing after a new release because repositories may not be properly sync yet (hence missing dependencies) and there are probably some sloppy packaging that will be ironed out. But thanks for trying to help anyway.

Looking at the bright side, the installation process of Maverick is so fast and smooth that I almost want an excuse to experience it again. :)

---

### Post by QLee on 2010-10-13
[QUOTE=beew]Sudo apt-get install -f and the system freezes as well (pretty much whenever apt-get anything it freezes, kind of expected as Synaptic is just a front end to apt).
...[/QUOTE]
I want to clarify this so inexperienced users don't get a mistaken impression. All the various higher-level package managers, Synaptic; Ubuntu Update; aptitude; apt-get and several others which we don't normally encounter in Ubuntu are all front-ends to APT, the Advanced Package Tool. It's another case where case matters, Synaptic is not a front-end to "apt" as in apt-get. You probably already knew this beew, users not as experienced as you might not have realised the difference.

---

### Post by ibuclaw on 2010-10-13
> **beew said:**
> I read somewhere on the forums that things tend to be a bit confusing after a new release because repositories may not be properly sync yet (hence missing dependencies) and there are probably some sloppy packaging that will be ironed out. But thanks for trying to help anyway.
I think it's just a new-user thing. Happened quite frequently when I started out. I never get any trouble during upgrades nowadays... Then again, long gone are the days of me installing piles of software because I may or may not ever use it. And oh the constant tweaking! :)

> **beew said:**
> 
Looking at the bright side, the installation process of Maverick is so fast and smooth that I almost want an excuse to experience it again. :)
That brings back some fond memories of Debian. 3 months installing on a (near) Daily basis, using KDE3, trying to find that middle ground between what I expect to happen and what I want to happen on my computer. ;)
> **QLee said:**
> I want to clarify this so inexperienced users don't get a mistaken impression. All the various higher-level package managers, Synaptic; Ubuntu Update; aptitude; apt-get and several others which we don't normally encounter in Ubuntu are all front-ends to APT, the Advanced Package Tool.
That's not quite right, but I'm too tired to correct your assumptions.

---

### Post by QLee on 2010-10-14
[QUOTE=ibuclaw]...
That's not quite right, but I'm too tired to correct your assumptions.[/QUOTE]

Assumptions?

Well then, please do so when you have rested sufficiently. I wasn't trying to write a three page bulletproof explanation that took everything into account, I look forward to yours. You're probably going to say that aptitude would be better described as a front-end to dpkg, and I'll concede that. I don't think you have much to criticise about the rest of it.

---

### Post by ibuclaw on 2010-10-14
> **QLee said:**
> You're probably going to say that aptitude would be better described as a front-end to dpkg, and I'll concede that.
Not just aptitude, but all software you mentioned.

APT isn't the backend, it is **one** frontend. apt-get is **part** of the APT frontend that interfaces to dpkg.

---

### Post by QLee on 2010-10-15
> **ibuclaw said:**
> Not just aptitude, but all software you mentioned.

APT isn't the backend, it is **one** frontend. apt-get is **part** of the APT frontend that interfaces to dpkg.
Front end to a front end eh? Somewhat a question of semantics.

Yes, of course that is correct and our discussion should clear up the point that I was trying to make, namely to correct the comment that synaptic was a" front end to apt".  I'm being pedantic I suppose but that is not unknown in the forums.

This illustrates the value of peer review, with lots of people looking at posts and discussing, all have the chance to benefit from the clarifications of others.

Can't imagine how you could have been too tired to write that brief comment previously but thanks for doing so now.

---

### Post by beew on 2010-10-15
I think I should mark this as "solved" because in a way it was (through a fresh install) and the ongoing debate seems to have nothing to do with my original question. But thanks for the input guys, at least I learn some fine points about apt, apt-get and dpkg, it can be confusing to beginners. :)

---

