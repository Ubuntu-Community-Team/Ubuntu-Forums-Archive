---
title: "ndiswrapper, changing ESSID"
date: 2007-04-10
forum: Networking &amp; Wireless
---

### Post by ittiam on 2007-04-10
Hey,

Whenever i change  my wireless network am always forced to modprobe on ndiswrapper. if i move to my school from my home i have do a modprobe -r ndiswrapper, modprobe ndiswrapper and iwconfig wlan0 essid ..... !

if i try to set the essid without doing modprobe it doesnt get set...! The same happens when i switch to my home network after coming back.

Any idea why?

---

### Post by dragomirov on 2007-04-10
I'm not sure I got your problem, but I think NetworkManager can solve the issue. It's capable to recognize a network and immediately connect to it. 
Alternatively you can setup you essid directly as an alias in your network card configuration and it's explained very well here [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu") at point #7

---

