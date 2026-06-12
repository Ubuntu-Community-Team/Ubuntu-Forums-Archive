---
title: "[SOLVED] Deleting anything Ethernet"
date: 2008-10-01
forum: Networking &amp; Wireless
---

### Post by AlexBellisBrown on 2008-10-01
Right... lets see, this is an interesting question. Im wondering if its possible to totally delete anything to do with the Ethernet connection on my laptop, i was using it for about a year, but after so much use, it actually "broke" off the motherboard, rendering it totally useless. So in order to avoid my computer getting confused, or trying to connect to the ethernet port, if its possible to delete it from "existance". If its not possible, it doesnt matter, its just it would free up an entry on the Network settings, and also, when i turn off the computer, the splash screen disappears, and endles "network manager bla bla ethernet close fail bla bla" or something to that effect, would disappear.

Any ideas? :)

---

### Post by iponeverything on 2008-10-01
blacklist the module for the Ethernet card and the OS won't know its there.


sudo echo "blacklist somemodule" >> /etc/modprobe.d/blacklist

---

### Post by murphykieran on 2008-10-01
You should be able to disable various onboard devices in the computer's BIOS, including the ethernet.  

Startup the compute and as soon as it starting to POST, hit the necessary key (F2, F5, del, depends on your computer, it'll be in the manually or it might be displayed on screen when starting up).  

There should be an option somewhere in the various BIOS menus to disable different devices like USB, audio, ethernet, etc.  It may be called LAN in the BIOS instead of Ethernet.  Disable it, save the settings and restart.  If you don't know what you're doing, don't screw around with any other settings, although there's usually an option to restore the BIOS to factory or safe settings.

If in doubt, check the manual that came with the laptop.

---

### Post by AlexBellisBrown on 2008-10-09
Thanks guys, worked perfectly! Marking solved! :)

---

