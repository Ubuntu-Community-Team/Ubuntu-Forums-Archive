---
title: "Can't install wine or wine 1.2 on Ubuntu 9.10?!?"
date: 2010-04-18
forum: New to Ubuntu
---

### Post by Sepiraph on 2010-04-18
I can't seem to install wine 1.2 on Ubuntu 9.10 (64 bit version), I got it to work under 32 bit version before but now if I go to Synaptic to install either it, I get this message:

> wine1.2:
 Depends: lib32nss-mdns (>=0.10-3) but it is not installable
 Recommends: ttf-mscorefonts-installer but it is not going to be installed

And if I try to install ttf-mscorefonts-installer, I get:

> ttf-mscorefonts-installer:
 Depends: cabextract  but it is not installable


And I still haven't how/where to install cabextract.

Did anyone else have this issue (not sure if it's only for the 64 bit version).

---

### Post by Sepiraph on 2010-04-18
I went to check in the repository for 'communities' maintained and now it's installed.  They should maybe put in 'suggestion' for automatically tell user that!

---

### Post by coffeecat on 2010-04-18
> **Sepiraph said:**
> I went to check in the repository for 'communities' maintained and now it's installed.  They should maybe put in 'suggestion' for automatically tell user that!

Not necessary. The "community maintained" (aka Universe) repository is enabled by default. You must have disabled it if it wasn't enabled.

The three packages you mention are indeed in the Universe repository, but will be available for installation if you don't change the repository settings from the default.

---

### Post by Sepiraph on 2010-04-18
> **coffeecat said:**
> Not necessary. The "community maintained" (aka Universe) repository is enabled by default. You must have disabled it if it wasn't enabled.

The three packages you mention are indeed in the Universe repository, but will be available for installation if you don't change the repository settings from the default.

Right but it is quite easy for someone to uncheck it and then they would have no idea why it is not working, which happened to me.

---

