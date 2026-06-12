---
title: "Building my own distro - automounting help"
date: 2010-02-14
forum: New to Ubuntu
---

### Post by Zerp64 on 2010-02-14
I'm trying to scrape together my own distro so I can show off how nerdy I am to my friends. Everything is going smoothly, except I can't figure out how to automount files. I'm trying to use autofs, but it's a pain. I really wish that installing it would have some type of default configuration to use, but it's mostly just files containing examples. Does ubuntu use a different automounting system? Can someone maybe help me out here, maybe even trow me their default configs or something?

*Edit:*Oh, forgot to mention: I installed Ubuntu 9.10 cli system from the alternate disk.

---

### Post by Satoru-san on 2010-02-14
You are building your own distro? So are you using LFS? I have tried doing that, it takes FOREVER, and I don't have the patience. 

As far as automounting, that is all done by gnome and HAL I believe. 

I am not really sure what you are doing, but if you are using for instance debian as a base like what is done in ubuntu, then you should just add gnome to do this.

If you are using LFS, you would know this already. >_<

> **Zerp64 said:**
> *Edit:*Oh, forgot to mention: I installed Ubuntu 9.10 cli system from the alternate disk.

ubuntu is already a distro, so changing it is cool, but not your own distro

---

### Post by FlyDude on 2010-02-14
Thunar could be used as daemon with volman support pulled in. 

But as far as the automounting go, HAL and DBUS controls the automounts. Ubuntu might be moving in the direction of DeviceKit, if you're interested in that. It's a new, rewritten version of HAL by the same author. Udev also has this functionality. But then again, I read last time that DeviceKit is deprecated and merged with udev. Someone could correct me in this or i'll research later.

---

### Post by wojox on 2010-02-14
You could:

```
man mount
```

It'll show you ways like editing your /etc/fstab file to auto-mount for you.

---

### Post by Zerp64 on 2010-02-17
> **FlyDude said:**
> Thunar could be used as daemon with volman support pulled in. 


Hey, that sounds like it'll work. Anything special I'll have to do to get Thunar to work this way? To be honest, I was hoping to use PacMan, but Thunar's almost just as good.


> ubuntu is already a distro, so changing it is cool, but not your own distro

You sure? Ever heard of Linux Mint? Fluxbuntu? OpenGeu? X/K/edubuntu? Last I heard those are distros. And hey, Ubuntu is based off of Debian, so is Ubuntu not a distro, either?

---

### Post by Satoru-san on 2010-02-17
> **Zerp64 said:**
> You sure? Ever heard of Linux Mint? Fluxbuntu? OpenGeu? X/K/edubuntu? Last I heard those are distros. And hey, Ubuntu is based off of Debian, so is Ubuntu not a distro, either?
Yea those are called derivatives, and Debian is the base.

[http://www.ubuntu.com/products/whatisubuntu/derivatives](http://www.ubuntu.com/products/whatisubuntu/derivatives)

---

### Post by Zerp64 on 2010-02-17
> **Satoru-san said:**
> Yea those are called derivatives, and Debian is the base.

[http://www.ubuntu.com/products/whatisubuntu/derivatives](http://www.ubuntu.com/products/whatisubuntu/derivatives)

So Ubuntu isn't a distribution?

---

