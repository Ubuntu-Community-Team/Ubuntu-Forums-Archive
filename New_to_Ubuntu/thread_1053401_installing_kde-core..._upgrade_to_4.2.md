---
title: "installing kde-core... upgrade to 4.2?"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by le singe on 2009-01-28
Well my title is essentially what I'd like to clarify.  If I install the kde-core package, and having added the kubuntu-experimental repository (deb [http://ppa.launchpad.net/kubuntu-experimental/ubuntu](http://ppa.launchpad.net/kubuntu-experimental/ubuntu) intrepid main), will it soon enough prompt itself to upgrade to the latest 4.2 build?  Or will this somehow only work on a complete KDE package install?

How are those of you who have gotten this latest version liking it, by the way?

---

### Post by snova on 2009-01-28
> **le singe said:**
> If I install the kde-core package, and having added the kubuntu-experimental repository (deb [http://ppa.launchpad.net/kubuntu-experimental/ubuntu](http://ppa.launchpad.net/kubuntu-experimental/ubuntu) intrepid main), will it soon enough prompt itself to upgrade to the latest 4.2 build?

It's already there, actually.

> Or will this somehow only work on a complete KDE package install?

Nope, you can have as much or as little of it installed as you like.

> How are those of you who have gotten this latest version liking it, by the way?

:D

---

### Post by shrndegruv on 2009-01-28
can someone write out some instructions on how to get stable 4.2?  I followed some instructions online and now i get nightly builds.  with 4.2 out i want to go to stable.

---

### Post by snova on 2009-01-28
> **shrndegruv said:**
> can someone write out some instructions on how to get stable 4.2?  I followed some instructions online and now i get nightly builds.  with 4.2 out i want to go to stable.

[http://www.kubuntu.org/news/kde-4.2](http://www.kubuntu.org/news/kde-4.2)

You'll also probably have to disable whatever repos you're getting the nightly builds from.

---

### Post by shrndegruv on 2009-01-28
yeah but what package to install after enabling that repo?

---

### Post by snova on 2009-01-28
> **shrndegruv said:**
> yeah but what package to install after enabling that repo?

Nothing. Not sure what you mean.

Just update and upgrade.

Synaptic way:

Open Synaptic, press Reload, Mark all Upgrades, Apply. (I think; I wouldn't know, I never use it. :))

Terminal way:

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by shrndegruv on 2009-01-28
what packages to install if i dont have kde4 installed?

---

### Post by snova on 2009-01-28
> **shrndegruv said:**
> what packages to install if i dont have kde4 installed?

One of kde-core, kde, or kubuntu-desktop, in increasing order of size.

I recommend kde-core if you just want the desktop; kde if you want to sample some of its applications.

kubuntu-desktop brings in a lot of other stuff I don't particularly find necessary, like a different login manager and boot splash. So one of the other two is probably preferable.

---

### Post by shrndegruv on 2009-01-28
ahh i see.

i find it a bit buggy and slow -- do you have nvidia graphics?  do the default restricted drivers work for you?

---

