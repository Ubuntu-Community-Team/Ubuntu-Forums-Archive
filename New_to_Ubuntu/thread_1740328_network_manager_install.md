---
title: "network manager install"
date: 2011-04-26
forum: New to Ubuntu
---

### Post by crip720 on 2011-04-26
Hi need to install network manager from cd, but after ticking cd for software source and trying apt-get install it does not work.  Says no indices or packages found[?].  Think the cd is good , will open on desktop.  I was having problems with networkmanager and thought if I uninstalled it and reinstall from cd it might fixed it.  This is on pinguy 10.10 64bit.  I am now using ubuntu 10.04 32bit to write this.  Thank you for your help.  Colin.

---

### Post by MSPdwalt on 2011-04-26
Did you refresh your sources?

```
sudo apt-get update
```

---

### Post by 3rdalbum on 2011-04-26
> **crip720 said:**
> I was having problems with networkmanager and thought if I uninstalled it and reinstall from cd it might fixed it.

So you know in future, replacing a bit-perfect copy of any piece of software with another bit-perfect copy will not fix any problems. Sometimes, removing a preferences or settings file might help; but it depends on exactly what sort of problem you were having. Removing part of the operating system is, really, asking for trouble.

You could try going to [http://packages.ubuntu.com](http://packages.ubuntu.com) and downloading the Network Manager packages that you removed, booting up your borked copy of Ubuntu and then double-clicking the packages to install them.

---

### Post by crip720 on 2011-04-26
Yes I did and it took me apt-cdrom  and then I got lost.  This is where it said indices and packages not found.  I probaly goof up somewhere.  I have downloaded network manager, but need help getting it from ubuntu 10.04 32bit to pinguy 10.10 64bit partition.  I think I just burn it to a cd from downloads,yes?  Thanks Colin

---

