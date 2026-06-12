---
title: "Central local package server"
date: 2010-12-13
forum: New to Ubuntu
---

### Post by Blutkoete on 2010-12-13
Hello!

I'm using Kubuntu 10.10 at the moment and now my girl friend wants to try it out on her netbook, too. As our Internet access is limited to 5 GB at UMTS speed (and afterwards only EDGE), I was wondering whether I could somehow prevent duplicate downloads of updated packages, e.g. if I've already downloaded the latest Kernel for my computer, my girl friend's netbook doesn't have to download it again, only apply it.

Is there a way to achieve this or a tool for it?

Thank you very much,

Blutkoete

---

### Post by migs73 on 2010-12-13
Is this the sort of thing you were looking to do?

[http://www.uluga.ubuntuforums.org/showthread.php?t=910017](http://www.uluga.ubuntuforums.org/showthread.php?t=910017)

Don't know how good it is though.

---

### Post by Blutkoete on 2010-12-13
Thank you! It's not exactly what I want, but it helps - so the packages are stored in */var/cache/apt/archives*, maybe I can find a way to sync the folder on both computers over the local network.

I thought about using Keryx somehow, but that'll mean doing it manually.

It's simply that I don't want both computers e.g. to download a Firefox update, computer 2 should use the downloaded packages from computer 1.

---

### Post by migs73 on 2010-12-13
All right I get it now;

Try this then

[http://my.opera.com/ubuntunerd1/blog/how-to-create-an-ubuntu-update-cd-dvd](http://my.opera.com/ubuntunerd1/blog/how-to-create-an-ubuntu-update-cd-dvd)

more what you had in mind I think.:D

---

### Post by gmargo on 2010-12-13
You should run an apt package caching daemon, such as **apt-cacher-ng**.
[http://packages.ubuntu.com/maverick/apt-cacher-ng](http://packages.ubuntu.com/maverick/apt-cacher-ng)

---

