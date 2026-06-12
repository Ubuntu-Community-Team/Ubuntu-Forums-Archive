---
title: "wireless problem  ?"
date: 2008-11-28
forum: Networking &amp; Wireless
---

### Post by regdabs on 2008-11-28
Hi, I am new to this and have (had) a wireless problem.  I have a buffalo air station card.  Didn't work at all, light didn't come on, nothing. Did some reading and decided I needed to use ndiswrapper.  Installed it and the util program, and then went into network config and disabled the broadcom 43 driver, and then everything  started working.  I didn't do anything else. I did find the .inf and .sys windows drivers that I thought I needed and put them in a file on the desktop.  I never did use the ndiswrapper, does it auto. find the files it needs and use them?  I did run the ndiswrapper -l and got the following results, not sure what they mean:



usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid' (dangerous)
-r driver        remove 'driver'
-l               list installed drivers
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information

where 'devid' is either PCIID or USBIDd and put them in a file on the desktop. 

I never did use ndidwrapper as such

any ideas or suggestions as to what is happening.  Guess as long as it works just leave things alone?

---

