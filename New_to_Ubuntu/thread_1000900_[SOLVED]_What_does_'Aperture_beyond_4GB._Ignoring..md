---
title: "[SOLVED] What does 'Aperture beyond 4GB. Ignoring.' mean?"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by bwallum on 2008-12-03
I get this message on the screen at the beginning of the Intrepid boot up:-
> [    0.004000] Aperture beyond 4GB. Ignoring.What does it mean? Should I fix it? If so, how?

The system appears to be working ok otherwise.

---

### Post by philinux on 2008-12-03
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/271070](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/271070)

---

### Post by Michael.Godawski on 2008-12-03
It seems to me that you have to look into your bios setup if you can configure something which deals with AGP Aperture or IO MMU.

Also it depends on what bit version you are. If you are on a 64 bit version the machine just tells you can use more than 4GB Ram and you have less. Or maybe I am mixing something up?

There is a long thread running dealing with this issue:

[http://ge.ubuntuforums.com/showthread.php?t=963892](http://ge.ubuntuforums.com/showthread.php?t=963892)

---

### Post by philinux on 2008-12-03
This "bug" is on Jaunty 64 bit as well.
I just ignore it.

---

### Post by bwallum on 2008-12-04
Thanks guys, I have looked at it on Launchpad and added a +1 to a very long list. It seems to affect 64 bit machines and a message is to be had if you have 4Gb ram. Ignoring it seems a good thing to do...

---

