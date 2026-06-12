---
title: "video editing"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by DarinB on 2009-03-05
anybody know of a super easy video editing application for Intrepid?

---

### Post by bluenova on 2009-03-05
kdenlive, but the version in intrepid repos is way out of date, get the latest version from this ppa:

Go to your system menu > Software sources > Third-Party Software 
Click add and paste this line in:
deb [http://ppa.launchpad.net/baudm/ubuntu](http://ppa.launchpad.net/baudm/ubuntu) intrepid main 
Close software source and click reload 
Then type:
sudo apt-get update && sudo apt-get install kdenlive dvgrab frei0r swh-plugins

---

### Post by DarinB on 2009-03-05
is it for kde or gnome i use gnome

---

### Post by MrWES on 2009-03-05
> **DarinB said:**
> anybody know of a super easy video editing application for Intrepid?

Try Avidemux

[http://fixounet.free.fr/avidemux/]("http://fixounet.free.fr/avidemux/")

It's in the repositories and GNOME based.

Bill

---

### Post by DarinB on 2009-03-05
in third party software when i click add and paste the above in the box the add source is grayed out and doesn't allow me to add it

---

### Post by DarinB on 2009-03-05
thanks avidemux is great already did what i needed in just a few minutes of fiddling with the tools

---

