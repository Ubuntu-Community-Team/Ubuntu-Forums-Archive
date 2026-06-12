---
title: "Network Manager 7"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by TechDragon on 2009-01-27
I want to use Kubuntu 8.04 but need to use Gnomes Network Manager 7.

How do I accomplish this? How do I get Kubuntu to use Gnomes Network mangager 7 in version 8.04


Thanks

---

### Post by XanTrax on 2009-01-27
> **TechDragon said:**
> I want to use Kubuntu 8.04 but need to use Gnomes Network Manager 7.

How do I accomplish this? How do I get Kubuntu to use Gnomes Network mangager 7 in version 8.04


Thanks

First, may I ask why you _need_ to use Gnome's network manager in KDE and not just use KDE's version?

I dont even know if there is a difference, just first would like to know why you want to use Gnomes and not just KDE's

---

### Post by TechDragon on 2009-01-27
yes, you may ask :)

I have a novatel sprint cellular card that works withs gnomes network manager and not KDE's.  I even went so far as to install Fedora to see their workaround and their solution was to use the gnome network manager inside of kde.

---

### Post by pHreaksYcle on 2009-01-27
I think it would be a matter of just installing it and setting it to start up on boot, then remove the other program from auto-start.

---

### Post by XanTrax on 2009-01-27
> **TechDragon said:**
> yes, you may ask :)

I have a novatel sprint cellular card that works withs gnomes network manager and not KDE's.  I even went so far as to install Fedora to see their workaround and their solution was to use the gnome network manager inside of kde.

Alright.  I dont see this not working so lets give it a try.

Running
```
sudo apt-get remove knetworkmanager
```

will remove KDE's version of network manager.  Then,

```
sudo apt-get install network-manager network-manager-gnome
```

will install Gnome's network-manager application.

---

