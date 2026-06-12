---
title: "error in installing adobe flash player"
date: 2009-09-26
forum: New to Ubuntu
---

### Post by oaridus on 2009-09-26
Hi, I have tried to install adobe flash player in my ubuntu but it gives me the following error by package installer:

Error: Dependency is not satisfiable: libnspr4-dev

Could anyone help me out.

thanks

---

### Post by lkraemer on 2009-09-26
Just use:
SYSTEM -> ADMINISTRATION -> SYNAPTICS PACKAGE MANAGER
Search for libnspr4-dev and install it.

lk

---

### Post by 3rdalbum on 2009-09-26
> **oaridus said:**
> Hi, I have tried to install adobe flash player in my ubuntu but it gives me the following error by package installer:

Error: Dependency is not satisfiable: libnspr4-dev

Could anyone help me out.

thanks

Hit the "Reload" button in Synaptic in order to load the list of available packages from the repository.

When you install Ubuntu, it usually tries to load the full package list from the repository. If there's no internet connection when it tries this, it will not be able to download the package list, and so the only packages it will be aware of are those that are on the installation CD.

Note that you should be installing software from the Synaptic Package Manager, not just downloading them from various websites. Flash Player is available in the Ubuntu repositories - just look in Synaptic for "flashplugin".

---

### Post by timwuzhere9 on 2009-09-27
> **lkraemer said:**
> Just use:
SYSTEM -> ADMINISTRATION -> SYNAPTICS PACKAGE MANAGER
Search for libnspr4-dev and install it.

lk

i tried that and it said that its already running... and if i can't get flash i might as well go to one of the worst OS ever... vista](*,)

---

### Post by MelDJ on 2009-09-27
try installing the flashplugin-nonfree package

---

### Post by sandyd on 2009-09-27
are you using a 64 bit os or 32 bit.

if your using 32-bit, assuming you downloaded the file to the desktop,

```

sudo dpkg -i ~/Desktop/*deb
sudo apt-get -f install

```

---

### Post by timwuzhere9 on 2009-09-27
holy crap that was fast... i got it to work... my updates hadn't run yet

---

### Post by agmcclard on 2009-10-14
Read this hope it helps.

[http://ubuntuforums.org/showthread.php?t=1275716](http://ubuntuforums.org/showthread.php?t=1275716)

---

