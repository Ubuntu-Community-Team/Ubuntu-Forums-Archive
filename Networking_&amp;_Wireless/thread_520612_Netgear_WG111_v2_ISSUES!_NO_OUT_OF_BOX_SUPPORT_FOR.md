---
title: "Netgear WG111 v2 ISSUES! NO OUT OF BOX SUPPORT FOR ME!"
date: 2007-08-08
forum: Networking &amp; Wireless
---

### Post by ajmctaggart on 2007-08-08
THIS ADAPTER IS SUPPOSED TO WORK "OUT OF BOX" IN FEISTY, BUT IT ISN'T FOR ME!

I have a static ip on my ethernet connection for work 
Wireless can by dynamic though
I unblacklisted the r8187 driver in /etc/modprobe.d/blacklist

but still not working

Any suggestions?

PS- nothing refers to it in /etc/network/interfaces

I am running Feisty on a Powerbook Pismo w/ all updates, I literally haven't touched the machine yet, so it's as virgin as it'll ever be...

Can anyone help me on this one?
thanks
ajm

---

### Post by kevdog on 2007-08-08
Youve got a crappy card.  If your card uses the rt8187 drivers you either have to do ndiswrapper/win98 driver combination, or patch the r8187 drivers with the aircrack patch.  Ive heard that faking your essid by adding an extra character at the end of the name with the r8187 driver-- such as adding an x -- might work, but can not confirm.

---

