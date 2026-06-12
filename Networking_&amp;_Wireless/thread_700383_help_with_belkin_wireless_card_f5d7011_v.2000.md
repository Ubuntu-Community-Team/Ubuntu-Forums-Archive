---
title: "help with belkin wireless card f5d7011 v.2000"
date: 2008-02-18
forum: Networking &amp; Wireless
---

### Post by kristalee2003 on 2008-02-18
I'm looking for help as an absolute ubuntu (and linux) beginner.  I just wiped Windows off my laptop and installed ubuntu 7.10, and everything works except my wireless cards (and my dvd player... that's another post.) 

I have ndiswrapper running.  It recognizes the driver, as far as I can tell - I've pointed it toward both the .ini and the .sys files that Belkin provides, and when I go to "windows wireless drivers," under "currently installed windows drivers," it says: bcmwl5: hardware present.

The craziest part is that the card worked fine once, but after I rebooted my laptop it never recognized the card again.

Help!  I want to love linux but I'm totally frustrated.  I'd really appreciate ideas about how to make this card work OR a suggestions of a better card to use.

Thanks,
Krista

---

### Post by lanceros217 on 2008-04-20
This might be a bit late but anyways..... Try installing the  bcm43xx-fwcutter package from System-Administration-Synaptic package manager, and then go to System-Administration-Restricted Drivers Manager and enable broadcom 43xx. that did it for me using the belkin 54g f5d7011 v.1000 on a dell inpiron 1100. I don't even have to use ndiswrapper.

Hope it helps

---

