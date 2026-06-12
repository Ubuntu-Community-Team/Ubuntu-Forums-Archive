---
title: "wmv"
date: 2009-06-04
forum: New to Ubuntu
---

### Post by silvernitrate on 2009-06-04
can someone help me with how to play wmv movies

---

### Post by Wa1k3rTXRang3r on 2009-06-04
just try to play it in movie player and it will download the correct plugins in order to play it

---

### Post by furialis on 2009-06-04
You need to have Medibuntu repository enabled. If you're running Jaunty ```
sudo wget http://www.medibuntu.org/sources.list.d/jaunty.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```
Then ```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

---

### Post by Bölvaður on 2009-06-04
to do the things the poster above me said go to Applications &#8594; Accessories &#8594; Terminal

then copy the text he said (one line at a time) and paste it into the terminal (with right clicking or ctrl+shift+v) and press enter.

after doing it with all the lines your problem will (probably) magically be gone away

---

### Post by LowSky on 2009-06-04
One command to rule them all, use the the one you need, 32 or 64bit... if you don't know assume you have the 32bit version

**32bit**
```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update && sudo apt-get install libdvdcss2 && sudo apt-get install w32codecs
```

**64bit**
```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update && sudo apt-get install libdvdcss2 && sudo apt-get install w64codecs
```

---

