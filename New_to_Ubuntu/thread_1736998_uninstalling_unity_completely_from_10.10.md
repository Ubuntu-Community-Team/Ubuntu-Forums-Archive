---
title: "uninstalling unity completely from 10.10"
date: 2011-04-22
forum: New to Ubuntu
---

### Post by dwhite on 2011-04-22
hi,

i installed Unity earlier today using Ubuntu software center (on top of 10.10 32 bit), and played around with it,when i  rebooted into the desktop edition,  unity seems to have highjacked various parts of my desktop.

My workspace switcher is screwed up...firefox opens without any window, full screen mode is disabled too...i'm sure other problems as well.

update: (in desktop edition mode, windows are not recognized as open at all, cannot be dragged etc.)

how can i completely deinstall unity (I uninstalled from the software center but obviously everything not removed) Do i have to do a complete reinstall of desktop 10.10?  kind of disappointed this didn't work out i would like to try Unity but i need this computer to be stable and ready to work

this must have been addressed before and i apologize, i did a quick search and didn't see anything relevant, so i guess i'm panicking.

---

### Post by frup on 2011-04-22
can you open software centre or synaptic to remove it? If so search for unity and remove it through there... synaptic allows you to remove all setting too.

If you can't open any windows, press ctrl + F1 it will drop you in to a terminal where you can log in.

type 
sudo apt-get --purge remove unity

once complete press ctrl F7 to return to the gui. Probably a good idea to restart or log out at that point.

---

### Post by dwhite on 2011-04-23
ok

booted to recovery console tried 

apt-get --purge remove unity

restarted but still windows screwed up

i have made a pendrive with 10.10 this morning, when i try to startup from i get an error something like it is not a 

"com 32r image"

downloaded iso from ubuntu and followed directions there, using pendrivelinux to install iso on usb drive, not sure what to do now.

---

### Post by cmcanulty on 2011-04-23
I tried Unity today also, made a big mess and I ended up reinstalling whole system. I hate the new interface and it seems very buggy.

---

