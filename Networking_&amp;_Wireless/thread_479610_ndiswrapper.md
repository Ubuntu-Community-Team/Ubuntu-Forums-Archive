---
title: "ndiswrapper"
date: 2007-06-20
forum: Networking &amp; Wireless
---

### Post by theflakes on 2007-06-20
I want to stop using the atheros drivers for my wireless card and switch to ndiswrapper.  How do I switch to ndiswrapper.  I have ndiswrapper installed and have loaded the windows driver via the ndiswrapper -i command.  I can't find how to disable the atheros driver being used by the gnome network manager applet.  I did disable the driver in the restricted drivers module, but it still get loaded.

Also when I use ndiswrapper to install the windows driver the wlan0 interface never gets created even though it gives me now errors.


thanks...

---

### Post by kevdog on 2007-06-20
I dont have an atheros chipset in my card, however dont atheros based cards use the madwifi drivers instead of ndiswrapper??  

Please post the results of:
lspci | grep Network

---

