---
title: "wmp54gs not finding network after gutsy to hardy upgrade"
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by ihavenoidea on 2008-04-27
I followed the directions on this post: [http://ubuntuforums.org/showthread.php?t=197102&highlight=bcm4318](http://ubuntuforums.org/showthread.php?t=197102&highlight=bcm4318)
(The second method, ndiswrapper, for gutsy and hardy) and worked perfect in Gutsy, but then the thing i did right after was uncomment the secuirity sources, because i didnt have a connection when installing and then i updated, upgraded, and upgraded to hardy. Now it recognizes the device and its wireless, but it cant find the network. It worked 5 min before the hardy restart, then cant find it, idk the problem. Other laptops in my house connect to it fine as well.

---

### Post by ihavenoidea on 2008-04-27
anyone?

---

### Post by Laeth on 2008-05-10
I had similar problems. It's best on a fresh install, but when I followed [http://ubuntuforums.org/showthread.php?t=766560]("http://ubuntuforums.org/showthread.php?t=766560") and instead of the drivers they suggest, used the WMP54GS ones (Should be on your instalation CD under drivers, make sure to change the bcmwl5.inf in the instructions to the name of the .inf file in your driver folder), I found it worked perfectly after a reboot.

Haven't had troubles since. Hopefully this will help you. :)

---

