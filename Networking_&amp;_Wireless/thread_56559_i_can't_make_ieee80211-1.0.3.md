---
title: "i can't make ieee80211-1.0.3"
date: 2005-08-13
forum: Networking &amp; Wireless
---

### Post by jdavros on 2005-08-13
I have an acer travelmate 4000, when i tried to install my wireless card (intel 2200) using this guide [http://ubuntuforums.org/showthread.php?t=26623](http://ubuntuforums.org/showthread.php?t=26623), i got this problem when i type make on my konsole.

root@samantha:/home/jdavros/Instaladores/Intel2200Wireless/ieee80211-1.0.3 # mak e
Checking in /lib/modules/2.6.10-5-386/build/ for ieee80211 components...

find: /lib/modules/2.6.10-5-386/build/: No existe el fichero o el directorio
grep: /lib/modules/2.6.10-5-386/build//.config: No existe el fichero o el direct orio
grep: /lib/modules/2.6.10-5-386/build//include/linux/autoconf.h: No existe el fi chero o el directorio
make -C /lib/modules/2.6.10-5-386/build M=/home/jdavros/Instaladores/Intel2200Wi reless/ieee80211-1.0.3 MODVERDIR=/home/jdavros/Instaladores/Intel2200Wireless/ie ee80211-1.0.3 modules
make: *** /lib/modules/2.6.10-5-386/build: No existe el fichero o el directorio.   Alto.
make: *** [modules] Error 2

i don't know what to do besides i'm just a newbie :-?

---

### Post by PeP on 2005-08-13
[QUOTE=jdavros]I have an acer travelmate 4000, when i tried to install my wireless card (intel 2200) using this guide [http://ubuntuforums.org/showthread.php?t=26623]("http://ubuntuforums.org/showthread.php?t=26623"), i got this problem when i type make on my konsole.

root@samantha:/home/jdavros/Instaladores/Intel2200Wireless/ieee80211-1.0.3 # mak e
Checking in /lib/modules/2.6.10-5-386/build/ for ieee80211 components...

find: /lib/modules/2.6.10-5-386/build/: No existe el fichero o el directorio
grep: /lib/modules/2.6.10-5-386/build//.config: No existe el fichero o el direct orio
grep: /lib/modules/2.6.10-5-386/build//include/linux/autoconf.h: No existe el fi chero o el directorio
make -C /lib/modules/2.6.10-5-386/build M=/home/jdavros/Instaladores/Intel2200Wi reless/ieee80211-1.0.3 MODVERDIR=/home/jdavros/Instaladores/Intel2200Wireless/ie ee80211-1.0.3 modules
make: *** /lib/modules/2.6.10-5-386/build: No existe el fichero o el directorio.   Alto.
make: *** [modules] Error 2

i don't know what to do besides i'm just a newbie :-?[/QUOTE]
use synaptic to install build-essentials

---

