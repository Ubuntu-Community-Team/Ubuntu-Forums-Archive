---
title: "no wifi an startup"
date: 2005-08-23
forum: Networking &amp; Wireless
---

### Post by dphipps on 2005-08-23
I have gotten my wlan to work with a ndiswrapper but it does not come up at startup.  I have to use the cammand modprobe ndiswrapper before it will show the card and then activate) it after every startup. Is there anyway to get my wireless conection to start up at boot?

---

### Post by ape on 2005-08-23
Have you added the ndiswrapper module to the /etc/modules file to ensure that it loads at startup?

---

### Post by dphipps on 2005-08-23
I have not added the ndiswrapper module to the /etc/modules file.  How do I do that?

---

### Post by johannes on 2005-08-23
In treminal:
```
sudo gedit /etc/modules
```
It should look something like:
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

ide-cd
ide-disk
ide-generic
lp
mousedev
psmouse
```
Just add "ndiswrapper" (without the "")
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

ide-cd
ide-disk
ide-generic
lp
mousedev
psmouse
ndiswrapper
```

---

### Post by dphipps on 2005-08-23
Thanks, that help me a lot!

---

