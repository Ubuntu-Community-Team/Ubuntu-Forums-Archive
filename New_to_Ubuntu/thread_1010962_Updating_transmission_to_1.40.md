---
title: "Updating transmission to 1.40"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by nilsolaris on 2008-12-14
Okay so at one point a friend of mine had added transmission to my sources, which i do not understand and it was constantly updating itself. Now that ive reinstalled ubuntu i cannot figure out how to update transmission. Any help would be highly appreciated!

---

### Post by Michael.Godawski on 2008-12-14
Add this to the sources.lst
```

deb [http://ppa.launchpad.net/transmissionbt/ubuntu](http://ppa.launchpad.net/transmissionbt/ubuntu) <ubuntu_release_name> main
deb-src [http://ppa.launchpad.net/transmissionbt/ubuntu](http://ppa.launchpad.net/transmissionbt/ubuntu) <ubuntu_release_name> main
```change the ubuntu release name to your distro for instance intrepid or hardy or gutsy...
for instance
```
deb [http://ppa.launchpad.net/transmissionbt/ubuntu](http://ppa.launchpad.net/transmissionbt/ubuntu) intrepid main
```
open the sources.lst with

```
gksudo gedit /etc/apt/sources.list
```add the lines save and then run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by nilsolaris on 2008-12-14
Thank you! I was about to go crazy. haha

---

### Post by Michael.Godawski on 2008-12-14
You are welcome. I hope everything works fine now?

---

### Post by Hydrid on 2008-12-14
> **Michael.Godawski said:**
> Add this to the sources.lst
```

deb [http://ppa.launchpad.net/transmissionbt/ubuntu](http://ppa.launchpad.net/transmissionbt/ubuntu) <ubuntu_release_name> main
deb-src [http://ppa.launchpad.net/transmissionbt/ubuntu](http://ppa.launchpad.net/transmissionbt/ubuntu) <ubuntu_release_name> main
```change the ubuntu release name to your distro for instance intrepid or hardy or gutsy...
for instance
```
deb [http://ppa.launchpad.net/transmissionbt/ubuntu](http://ppa.launchpad.net/transmissionbt/ubuntu) intrepid main
```
open the sources.lst with

```
gksudo gedit /etc/apt/sources.list
```add the lines save and then run

```
sudo apt-get update
sudo apt-get upgrade
```

Thanks man!This helped me too!

---

