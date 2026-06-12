---
title: "Error: Dependency is not satisfiable: python-support (&gt;= 0.90.0)"
date: 2009-09-21
forum: New to Ubuntu
---

### Post by MertTheGreat on 2009-09-21
Hi,

I tried to instal Deluge 1.1.9 for torrent files but when I open the .deb file Package Installer gave this 
> Error: Dependency is not satisfiable: python-support (>= 0.90.0)

What should I do ?

Thanks

---

### Post by Gaweph on 2009-09-21
you could try to do

```

sudo apt-get install python-support

```

or

```

sudo apt-get update python-support

```

Looks like your not satisfying something that the new deb needs before it can be installed.

If your not confortable iwth the command line, you could do:

SYSTEM -> ADMINISTRATION ->SYNAPTIC PACKAGE MANAGER (then search for python-support, and tick to install)

---

### Post by MertTheGreat on 2009-09-21
it gave me this command line:

> sudo apt-get install python-support
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python-support is already the newest version.
The following packages were automatically installed and are no longer required:
  libboost-thread1.37.0 libtorrent-rasterbar2 libswt-gnome-gtk-3.4-jni
  libboost-filesystem1.37.0 libcommons-lang-java libswt-cairo-gtk-3.4-jni
  libboost-system1.37.0 python-libtorrent libboost-python1.37.0
  libswt-gtk-3.4-jni libswt-mozilla-gtk-3.4-jni
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


I am still getting the error
and for update it gives>  E: The update command takes no arguments
 I couldn't find version >= 0.90.0 by using synaptic

---

### Post by Gaweph on 2009-09-21
lol, my bad.

should have been.
```

sudo apt-get update

```

But i dont think that is going to help.  Which version of python-support does synaptic say you have installed?

---

### Post by Bachstelze on 2009-09-21
> **MertTheGreat said:**
> 
 I couldn't find version >= 0.90.0 by using synaptic

It's available in Karmic, so if you're feeling adventurous, you could try installing the Karmic package (otherwise, just wait for release).

---

### Post by MertTheGreat on 2009-09-21
> **Gaweph said:**
> But i dont think that is going to help. Which version of python-support does synaptic say you have installed?

it says 0.8.7ubuntu4

---

### Post by MertTheGreat on 2009-09-21
> **Bachstelze said:**
> It's available in Karmic, so if you're feeling adventurous, you could try installing the Karmic package (otherwise, just wait for release).

What is Karmic? I have just migrated from vista.

---

### Post by Bachstelze on 2009-09-21
> **MertTheGreat said:**
> What is Karmic? I have just migrated from vista.

Karmic Koala is the codename of the next ubuntu release, to be released in october.

---

