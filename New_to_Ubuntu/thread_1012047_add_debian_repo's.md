---
title: "add debian repo's?"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by djbushido on 2008-12-15
can i add the debian repositories to get access to more software, since Ubuntu was build on Debian? If so, which one would i add (Etch, etc.)?

---

### Post by dracayr on 2008-12-15
Maybe there are special "ubuntu-debian" repos. but once I added them, and ubuntu got totally screwed up. It might have been a coincidence, but I think it was the repos...

dracayr

---

### Post by Bachstelze on 2008-12-15
Technically you can, but it's a very bad idea because it could damage your system very severely. If you really want something that is available only in Debian, download the individual package and install it, but do not add the entire repos.

---

### Post by Michael.Godawski on 2008-12-15
> Adding Debian repositories is a recipe for unpleasantness. You will almost certainly break your Ubuntu at some point - a critical library will be overwritten by a Debian one with a higher version number, and the Debian packages aren't guaranteed to be binary compatible.
quoted a ubuntu developer RAOF so ...
[http://ubuntuforums.org/showthread.php?t=126566](http://ubuntuforums.org/showthread.php?t=126566)

better just download the application you need in a deb and install it separately.

---

### Post by JoshuaRL on 2008-12-15
Really not a good idea.  I once added Ubuntu's repos to Linux Mint because I wanted a couple of applications.  It jacked it up hard.  If you want a few applications for a specific reason, try getting the .deb for it [here.](http://www.debian.org/distrib/packages)  It may not be able to get all of the dependencies, but at least that is the safe way.

If you're sure you want to do this, please read up on APT pinning before you try this.  [Here is one good link,](http://jaqque.sbih.org/kplug/apt-pinning.html) [and here is another one.](http://wiki.debian.org/AptPinning)  If you plan on adding repositories from another distro, this is the only way to have a chance at a stable system.

---

### Post by djbushido on 2008-12-15
Okay, so the general idea is to not add the repo. Ok. I might just look at the APT pinning for fun. Or not. Anyway, thank you all once again.

---

### Post by bodhi.zazen on 2008-12-15
> **djbushido said:**
> Okay, so the general idea is to not add the repo. Ok. I might just look at the APT pinning for fun. Or not. Anyway, thank you all once again.

You can use pinning, but be prepared for problems.

---

