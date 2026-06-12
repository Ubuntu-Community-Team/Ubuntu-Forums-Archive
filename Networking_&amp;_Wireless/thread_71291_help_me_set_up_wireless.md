---
title: "help me set up wireless"
date: 2005-10-02
forum: Networking &amp; Wireless
---

### Post by kufu on 2005-10-02
I just installed Ubuntu and I want to setup my Intel 2200BG wireless card now. The wireless card is detected under system/administration/device manager so I'm assuming the drivers are installed and working. 

But how do I configure it? If I go to Applications/system tools/network tools, under Network device only Loopback is available.

---

### Post by tehwa on 2005-10-02
Have a look through:

System > Administration > Network

It is likely to be there, but saying "Not Configured". If it isn't there, its not the end of the world, as it can be configured without a GUI.

---

### Post by kufu on 2005-10-03
It's not there either.

Also, i just noticed that after restarting my computer the gnome taskbar at the top is now frozen :(

---

### Post by tehwa on 2005-10-03
[QUOTE=kufu]It's not there either.
Also, i just noticed that after restarting my computer the gnome taskbar at the top is now frozen :([/QUOTE]
run:```
killall gnome-panel
```
to refresh your panels,  then to see what your WiFi NIC is playing at:```
lspci
```and paste the output here. This will show what Ubuntu thinks your WiFi card is, and possible tell us what chipset it uses.

---

### Post by kufu on 2005-10-04
killall gnome-panel didn't help, still frozen (as expected since restarting does nothing either).
I decided to try a clean install and setup the wireless when asked, maybe it will work then.

---

