---
title: "Removing downloaded software"
date: 2009-09-20
forum: New to Ubuntu
---

### Post by Scunnered on 2009-09-20
I have been attempting to work with iTunes by using Wine & VirtualBox.  Wine was downloaded via Synaptic & similarly deleted but still shows up under Applications > Wine > Programs.  Against programs it displays Bonjour, iTunes, Quicktime & Apple Software Support. How can I ensure that there is no residue of Apple software against this item.

With VirtualBox I was able to download it directly from their web page and therefore seek a way of removing it from the system.

My purpose in this is to ensure that there is no chance of anything Apple (iTunes in particular) remaining on my system.

Apple have really messed up with their latest offering iTunes 9 and has half the world up in arms so beware if you are offered it as an update. So far nothing is being done.

Thanking you for your kind assistance

---

### Post by sideaway on 2009-09-20
If i'm not mistaken you want to remove wine and all its residue (programs)? If so one simple command;

sudo apt-get autoremove wine

EDIT: Also, the wine in the repos is horribly outdated and inferior to the one found at [www.winehq.org](www.winehq.org)

---

### Post by 3rdalbum on 2009-09-20
Programs installed in Wine are stored per-user; the hidden folder ".wine" in your home directory. Remove the .wine directory and then remove the Wine submenu from your Applications menu.

---

### Post by Scunnered on 2009-09-20
My thanks to you both for your assistance.

That lets me have another look at the problem. 

Much appreciated

---

