---
title: "[FIX] Tool to fix ATI and NVIDIA drivers problems"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by Mariane on 2009-11-11
I discovered there is a specific tool for installing and fixing ATI and NVIDIA drivers: it is called envyng. 


KDE run commands:

```

sudo apt-get install envyng-core
sudo apt-get install envyng-qt
sudo envyng -k

```


GNOME run commands:

```

sudo apt-get install envyng-core
sudo apt-get install envyng-gtk
sudo envyng -g

```


In recovery mode root terminal:

```

apt-get install envyng-core
envyng -t

```


-k means "kde"
-g means "gnome"
-t means "text mode"


If I had known that before the 9.10 upgrade it would have saved me a lot of time. Combined with the xfix option in recovery mode it launched the X server properly. 


Mariane

---

