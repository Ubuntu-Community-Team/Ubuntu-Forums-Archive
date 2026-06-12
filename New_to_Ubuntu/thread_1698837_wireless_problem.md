---
title: "wireless problem"
date: 2011-03-02
forum: New to Ubuntu
---

### Post by brianmjasper on 2011-03-02
I have installed ubuntu 10.10 I have followed the instructions in the forums etc. but I cannot get online. Really disappointed as i like it, but if everything is this difficult I may as well just put up with windows. I have a belkin F6d4050v1 wireless usb adaptor. I have installed ndisgtk etc and installed the driver but it says N0 HARDWARE. even when plugged in .The wireless network drivers window is just blank.........I have already re installed ubuntu any help greatly appreciated. If i can't get online its no good to me

---

### Post by larsantos on 2011-03-02
[http://ubuntuforums.org/showthread.php?t=1509403](http://ubuntuforums.org/showthread.php?t=1509403)
 
It may help

---

### Post by 3rdalbum on 2011-03-02
If all else fails, you could try buying a wifi adapter that is known to work out-of-the-box on Ubuntu (there are plenty around), or at least can be made to easily work (I have an Alfa AWUS050NH adapter that works when you add one line to one file).

---

### Post by wep940 on 2011-03-02
Be sure the .inf and .sys files for your driver are Windows XP (ndiswrapper only supports XP drivers0; be sure they "match" your Ubuntu architecture - 32 or 64 bit; be sure the .inf and .sys files are in the same folder, and point ndisgtk to the .inf file in that folder.

---

