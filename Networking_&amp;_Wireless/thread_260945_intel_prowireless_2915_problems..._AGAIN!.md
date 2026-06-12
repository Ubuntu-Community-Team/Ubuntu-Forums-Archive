---
title: "intel pro/wireless 2915 problems... AGAIN!"
date: 2006-09-19
forum: Networking &amp; Wireless
---

### Post by kohlerbn on 2006-09-19
Okay, so I have been trying to get my wireless to work for weeks. I am following this thread

[http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)

I got all the way to the make command here

cd ..
cd ieee80211-1.0.3
make
sudo make install

I then get this set of errors. This is different then the first time. 


Checking in /lib/modules/2.6.15-27-386/build/ for ieee80211 components...

grep: /lib/modules/2.6.15-27-386/build//.config: No such file or directory
grep: /lib/modules/2.6.15-27-386/build//include/linux/autoconf.h: No such file or directory
make -C /lib/modules/2.6.15-27-386/build M=/home/kohlerbn/downloads/ieee80211-1.0.3 MODVERDIR=/home/kohlerbn/downloads/ieee80211-1.0.3 modules
make[1]: Entering directory `/lib/modules/2.6.15-27-386/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.15-27-386/build'
make: *** [modules] Error 2



can anyone help?

---

