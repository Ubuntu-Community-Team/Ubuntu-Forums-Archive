---
title: "Ubuntu does not recognize my iPod :("
date: 2010-06-23
forum: New to Ubuntu
---

### Post by wishingstar on 2010-06-23
I just started facing this problem today: Whenever I plug in my iPod (nano 3G) it does not show up in nautilus or under the devices in the /media folder.

Now here's where it gets weird, even though my iPod doesn't show up anywhere on my system, it is listed, and can be browsed and played in Enna Media Center!!

Here's my setup: Ubuntu Lucid (fresh install), Kernel 2.6.32-23-generic, GNOME 2.30.0, updated to the latest updates from canonical.

I think i should also mention that the iPod is recognized with no problems on my other XP machine.

Help is much appreciated.

Edit: I also discovered that the iPod can be seen by virtualbox and can be opened by the VM!

---

### Post by zkriesse on 2010-06-24
Ok first things first, I've found that if your iPod screen is locked (I'm assuming you have a touch) then it won't be recognized or mounted. The screen has to be unlocked before it'll mount. As to playing/loading music with it you'll need to install some packages which I shall list for you below. The following packages can be installed by going to the Applications Menu -> Ubuntu Software Center.

libipoddevice0
libipoddevice-dev
libgpod4-nogtk
gtkpod

Any other packages related to use of iPod's can be found by typing in "iPod" (without the quotes :D ) in the Ubuntu Software Center search. Hope this helps you out!

---

### Post by cliff01 on 2010-06-25
That certainly helps me. Thanks you.

---

### Post by wishingstar on 2010-06-26
> **zkriesse said:**
> Ok first things first, I've found that if your iPod screen is locked (I'm assuming you have a touch) then it won't be recognized or mounted. The screen has to be unlocked before it'll mount. As to playing/loading music with it you'll need to install some packages which I shall list for you below. The following packages can be installed by going to the Applications Menu -> Ubuntu Software Center.

libipoddevice0
libipoddevice-dev
libgpod4-nogtk
gtkpod

Any other packages related to use of iPod's can be found by typing in "iPod" (without the quotes :D ) in the Ubuntu Software Center search. Hope this helps you out!

I installed the libraries and was finally able to open my ipod, as an external drive though. I checked it only to find that it had an autorun.inf virus, i removed it and reconnected the ipod, and now Rhythmbox kicks in right away!

Thanks for the help :)

---

