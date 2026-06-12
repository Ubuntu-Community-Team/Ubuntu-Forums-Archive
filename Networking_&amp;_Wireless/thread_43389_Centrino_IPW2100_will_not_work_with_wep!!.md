---
title: "Centrino IPW2100 will not work with wep!!"
date: 2005-06-21
forum: Networking &amp; Wireless
---

### Post by Siorfin on 2005-06-21
I have tried upgrading using that WPA IPW2200 howto but I keep getting this bs:

iorfin@catharsis:~/Desktop/driver/ipw2100-1.1.0$ make
make -C /lib/modules/2.6.10-5-386/build SUBDIRS=/home/siorfin/Desktop/driver/ipw2100-1.1.0 MODVERDIR=/home/siorfin/Desktop/driver/ipw2100-1.1.0 modules
make[1]: Entering directory `/lib/modules/2.6.10-5-386/build'
make[1]: Nothing to be done for `modules'.
make[1]: Leaving directory `/lib/modules/2.6.10-5-386/build'

I have tried doing the fixes by installing modules and all that crap from another thread which links to the howto yet I still cannot get this stupid file to "make". So my question is either how do I get this damn thing working or how do I remove the stupid IPW2100 craphole driver from ubuntu hoary and then install ndiswrapper. It says source so I am not sure if I need to do anything but install and use it, I assume not. How do I do one of these two things or get wep working with the original drivers. I don't care what I just want this stupid thing to start working because I don't have all week to get this working. Very frustrating I finally find a build that gets my Radeon 9200 mobility working in 3d and now the stupid ass wireless won't work unless I run it unsecured and I am not running it unsecured.

relevant threads: [http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)

Not sure what the other thread was that describes the stupid make problem and I have been through so many I am not searching for it again. Please help this is really pissing me off. Been working on getting a working linux setup for a week.

---

### Post by luca_linux on 2005-06-22
[QUOTE=Siorfin]I have tried upgrading using that WPA IPW2200 howto but I keep getting this bs:

iorfin@catharsis:~/Desktop/driver/ipw2100-1.1.0$ make
make -C /lib/modules/2.6.10-5-386/build SUBDIRS=/home/siorfin/Desktop/driver/ipw2100-1.1.0 MODVERDIR=/home/siorfin/Desktop/driver/ipw2100-1.1.0 modules
make[1]: Entering directory `/lib/modules/2.6.10-5-386/build'
make[1]: Nothing to be done for `modules'.
make[1]: Leaving directory `/lib/modules/2.6.10-5-386/build'

I have tried doing the fixes by installing modules and all that crap from another thread which links to the howto yet I still cannot get this stupid file to "make". So my question is either how do I get this damn thing working or how do I remove the stupid IPW2100 craphole driver from ubuntu hoary and then install ndiswrapper. It says source so I am not sure if I need to do anything but install and use it, I assume not. How do I do one of these two things or get wep working with the original drivers. I don't care what I just want this stupid thing to start working because I don't have all week to get this working. Very frustrating I finally find a build that gets my Radeon 9200 mobility working in 3d and now the stupid ass wireless won't work unless I run it unsecured and I am not running it unsecured.

relevant threads: [http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)

Not sure what the other thread was that describes the stupid make problem and I have been through so many I am not searching for it again. Please help this is really pissing me off. Been working on getting a working linux setup for a week.[/QUOTE]
 Did you install all the needed packages mentioned in the HowTo?

---

### Post by Siorfin on 2005-06-22
yes

---

