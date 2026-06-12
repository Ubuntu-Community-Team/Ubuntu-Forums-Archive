---
title: "ndiswrapper startup error help please"
date: 2005-12-06
forum: Networking &amp; Wireless
---

### Post by emerick7 on 2005-12-06
I need some help on this here... I can't stand having to set up ndiswrapper and wlan everytime I reboot...

I've got my wireless USB adapter finally working, but I can't seem to get it started during bootup.  During "loading modules," it times out and errors with "windows driver couldn't be initialized."  I added ndiswrapper to 'gedit /etc/modules,' but I have to modprobe ndiswrapper and then activate it every time I restart the computer.  Any ideas??  Thanks in advance, Ty.

Here's what my /etc/modules looks like (maybe I'm missing something?):
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
mousedev
psmouse
ndiswrapper

```

---

### Post by carlosqueso on 2005-12-06
Try deleting the ndiswrapper from your /etc/modules list.  Then modprobe it and type
```
sudo ndiswrapper -m
```  I think it does something similar, but it may work better.

---

