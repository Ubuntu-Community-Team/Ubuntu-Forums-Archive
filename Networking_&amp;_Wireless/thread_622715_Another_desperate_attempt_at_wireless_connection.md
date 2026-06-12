---
title: "Another desperate attempt at wireless connection"
date: 2007-11-25
forum: Networking &amp; Wireless
---

### Post by Buster95 on 2007-11-25
After 6 months of pathetically struggling with getting my RTL8187B USB wireless card working with Fiesty on my laptop, slavishly following every thread that I though might lead towards a wireless connection, I gave up.

Gutsy promised salvation, with its on board driver, so I gave it a try. Well, I didn't get the wireless to work, plus a few other applications went west as well.

So, back to Fiesty and with a deep breath, I tried again. Started with a download of ndiswrapper and a suitable W98 driver, unzipped and untarred them and followed the installation steps.

Unfortunately, with the <make> step, I got this...

[I][B]dexter@dexter-laptop:~/Desktop/ndiswrapper-1.49$ sudo make install 
Password: 
make -C driver install 
make[1]: Entering directory `/home/dexter/Desktop/ndiswrapper-1.49/driver' 
make -C /usr/src/linux-headers-2.6.20-16-generic SUBDIRS=/home/dexter/Desktop/ndiswrapper-1.49/driver 
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic' 
  Building modules, stage 2. 
  MODPOST 1 modules 
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic' 
echo /lib/modules/2.6.20-16-generic/misc 
/lib/modules/2.6.20-16-generic/misc 
mkdir -p /lib/modules/2.6.20-16-generic/misc 
install -m 0644 ndiswrapper.ko /lib/modules/2.6.20-16-generic/misc 
/sbin/depmod -a 2.6.20-16-generic -b / 
make[1]: Leaving directory `/home/dexter/Desktop/ndiswrapper-1.49/driver' 
make -C utils install 
make[1]: Entering directory `/home/dexter/Desktop/ndiswrapper-1.49/utils' 
gcc -g -Wall -I../driver -o loadndisdriver loadndisdriver.c 
loadndisdriver.c:15:20: error: stdlib.h: No such file or directory 
loadndisdriver.c:16:19: error: stdio.h: No such file or directory [/B][/I]

and on and on for a few pages more until....

[I][B]make[1]: *** [loadndisdriver] Error 1 
make[1]: Leaving directory `/home/dexter/Desktop/ndiswrapper-1.49/utils' 
make: *** [install] Error 2 
dexter@dexter-laptop:~/Desktop/ndiswrapper-1.49$ [/B][/I]

Help would be appreciated

---

