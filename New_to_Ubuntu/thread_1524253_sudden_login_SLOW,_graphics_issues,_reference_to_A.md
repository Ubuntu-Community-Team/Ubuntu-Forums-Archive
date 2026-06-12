---
title: "sudden: login SLOW, graphics issues, reference to AppArmor on login"
date: 2010-07-04
forum: New to Ubuntu
---

### Post by UbuNoob001 on 2010-07-04
Hi all, I am new to linux but will try and be as precise as I can. 

I have a Dell Insp. 1545 with 3GB ram with 10.04_64

Problem: Rather out of the blue upon login, from the time of entering password to the desktop is MUCH slower. I have no splash enabled and  there is some reference to AppArmour profiles (it sits there at this apparmour reference , then sits trying to load desktop). However, I have never installed AppArmour. Finally, on last login, there was some sort of screen corruption prior to getting to desktop.


Note: prior to all this i noticed that firefox "blinked" when I was using it, and then said that it needed to shutdown/restart for updates. I did notice after that that two of my previous tabs sortof acted oddly (moved around then disappeared). 

Note: I have no SSH/Server software etc activated. 

**Shall I post the output of some logs for you guys? Any idea if any of this is related? **

Note2: I did change visudo so that sudo timeout shorter than it was. However that is the only modification to the system recently.

---

### Post by the.phantom on 2010-07-04
i am not a expert, but did find this ! ???

>  AppArmor was first successfully ported/packaged for Ubuntu in April 2007. AppArmor comes installed by default in Ubuntu 7.10 Gutsy Gibbon, and came as a part of the release of Ubuntu 8.04. Although it only protects CUPS by default, the user can install new profiles and enforce them.

As of Ubuntu 9.04 Jaunty Jackalope more items such as MySQL have installed profiles in /etc/apparmor.d/abstractions. AppArmor hardening continued to improve in Ubuntu 9.10 Karmic Koala as it ships with profiles for its guest session, libvirt virtual machines, the Evince document viewer, and an optional Firefox profile.[6
from 
[http://en.wikipedia.org/wiki/AppArmor](http://en.wikipedia.org/wiki/AppArmor)

---

