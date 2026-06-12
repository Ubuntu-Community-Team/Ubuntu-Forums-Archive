---
title: "wireless problem"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by rideburton56 on 2009-11-04
Hi All,

I decided that with the new verison out and all, I would try out Kubuntu this time around.  The problem is,  I can't connect to the internet.  I am using a linksys WUSB54G USB dongle to connect to my router on this box.  In Ubuntu (9.04 anyway) it worked right off the bat.  I do have WPA Personal Security.  Kubuntu is seeing the antenna (and picking up my router) but when I go to connect and put in my password, it does not connect (as if it was wrong).  I know I am typing in the right password.  What am I doing wrong?

---

### Post by papangul on 2009-11-04
Give WICD network manager a try:
If your wired connection is working then:
```
sudo aptitude install wicd
``` and if you don't have access to wired connection then follow this thread:
[http://ubuntuforums.org/showthread.php?t=1150797](http://ubuntuforums.org/showthread.php?t=1150797)
These instructions are for jaunty and ubuntu but you get the idea anyway.

---

### Post by rideburton56 on 2009-11-05
how would I go about finding the .deb for the python-gtk2 package.  I am googling but cant find it.

---

### Post by papangul on 2009-11-05
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

---

### Post by rideburton56 on 2009-11-05
I am not able to get a wired connection to this computer, and every time I download a .deb it tells me another dependency needs to be filled.  On the WICD package page (on ubuntu.com) it has a huge list (~20) of dependencies.  Should I just get all those?

---

### Post by Nightstrike2009 on 2009-11-05
I'd keep going until it says all dependancies satisfied, this is common with linux and reffered to as "Dependancy Hell", some only require a few .debs to work, others loads. If you sort out all dependancies (find & install) it works in the end. :)

---

### Post by rideburton56 on 2009-11-05
In reading the bug reports, it seems that Kubuntu has a known issue with Hidden SSID's.  How can I tell if mine is hidden or not?  I assume that if it comes up as an option when I scan networks then its not hidden, but everybody knows what happens when you assume....

---

