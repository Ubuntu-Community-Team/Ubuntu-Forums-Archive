---
title: "Hp dv8305c, bcm4318, restarting wireless on reboot"
date: 2007-06-01
forum: Networking &amp; Wireless
---

### Post by WieboJJ on 2007-06-01
Hi all,

Recently installed feisty fawn on my hpdv8305c notebook, 
all worked perfect on install except wireless which was easily fixed using this guide here [http://ubuntuforums.org/showthread.php?t=190177](http://ubuntuforums.org/showthread.php?t=190177)    Thanks to user piracyrocks....

When I boot into Ubuntu though, I had to still type in terminal

modprobe ndiswrapper

Which I than added to /etc/rc.local to get to run on startup, 

but I find that I still have to turn my wireless off/on via the button before my card seems to be recognized and I can connect to my network...

Network manager runs but there is no green, just searching randomly; when I turn off/on the wireless by the button (which is by default 'on' at startup) the lower dot turns green and than it finds my network and both turn green, after which it switches to monitoring signal strength....

Any clue how to get around this and maybe force the card to restart on login? Is that the problem? Or should I be quiet and thankful for the easy fix I already have, considering some peoples apparent problems with this card?

On a side note, any one with this same laptop who wants to install beryl, this guide 

[http://ubuntuforums.org/showthread.php?t=399643&highlight=xgl+feisty](http://ubuntuforums.org/showthread.php?t=399643&highlight=xgl+feisty)

worked perfectly for me, nice and simple on my ati200m.


this is my first post, but both those other two posts from Ubuntu forum users were incredibly helpful last week on my first install of a Linux distro...so thanks to the Ubuntu community!


jef

---

