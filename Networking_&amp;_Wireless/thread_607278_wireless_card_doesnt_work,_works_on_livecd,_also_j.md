---
title: "wireless card doesnt work, works on livecd, also just worked in fiesty"
date: 2007-11-08
forum: Networking &amp; Wireless
---

### Post by travm on 2007-11-08
So I upgraded to gutsy, with some headaches that i wont get into.  and now i need to boot up the livecd just so I can use my "used to work" wireless card.  Its an X-micro usb adapter based on the zydal 1211 chipset.  The drive module for this chipset appears to be loaded.  iwconfig shows nothing for wireless.  I only have eth0.  In the livecd iwconfig shows eth0 and eth1, where eth1 is the wireless adapter.  How can I give the system the kick it needs, and where do i kick it?  Frankly I dont know where to start here because it seems to be properly detected, but network manager just doesnt show any wireless options and iwconfig shows wired only aswell.  Please help, anyone.

---

### Post by mpierce on 2007-11-08
See the post to madjack - 1 minute ago!

---

### Post by SpiritIsReality on 2007-11-08
howdy
[http://ubuntuforums.org/archive/index.php/t-324148.html](http://ubuntuforums.org/archive/index.php/t-324148.html)
> 
  dmizer
August 17th, 2007, 07:15 PM

now i just gotta get it to work through network manager somehow
you can try this: [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/) instead of network manager

You could try wicd. It is highly recommended by many on this forum.
how I found somebody talking about it
[http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+wireless+managers&btnG=Search&meta=]("http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+wireless+managers&btnG=Search&meta=")

[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)
good help page
[https://help.ubuntu.com/community/WifiDocs/](https://help.ubuntu.com/community/WifiDocs/)
[http://www.google.ca/search?hl=en&q=ndiswrapper&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=ndiswrapper&btnG=Google+Search&meta=)
I think your chip is a zidas ? google's pretty good at guessing sometimes. other times not.
[http://www.google.ca/search?hl=en&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=site:ubuntuforums.org+zydas+1211&spell=1](http://www.google.ca/search?hl=en&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=site:ubuntuforums.org+zydas+1211&spell=1)
[http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+zydal+1211&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+zydal+1211&btnG=Search&meta=)
in case you want to try ndiswrapper, it's kind of fun. It's the only way I could get the toshiba satellite 2140XCDS with a linksys pcmia WPC54GS wireless card (that pcmia doesn't look quite right, oh well pci somethingorother?) on the air!!!
That ndiswrapper is like a workout at the gym. It feels good to get it ov3er with. haha! No, it's more like an mountain hike above the timberline. A little tougher than a walk in the park, but more refreshing too. haha.
all the best
trails

---

### Post by travm on 2007-11-09
thanks for the advice, but i want network manager to work.  i like how integrated it is.   I heard wicd is not so.  Frankly, It works out of the box on the livecd, and also on fiesty, why the problem.  There has to be something i can do to make it work now inside my gutsy install.

---

### Post by SpiritIsReality on 2007-11-09
howdy
something here might help
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide) or
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
trails

---

