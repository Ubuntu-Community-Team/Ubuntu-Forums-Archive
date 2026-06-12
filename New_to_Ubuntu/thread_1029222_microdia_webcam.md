---
title: "microdia webcam"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by NDUFB11 on 2009-01-03
Hi to everybody ! I'm a new entry with ....old commons problem
Could someone help me? My webcam doesen't function and I have just intalled several package or progranms uselessly
Thanks and happy new year : )

patrizio@ubuntu:~$ lsusb
Bus 003 Device 002: ID 0425:f102 Motorola Semiconductors HK, Ltd
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 004: ID 0c45:613c Microdia PC Camera (SN9C120)
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I'm not an PC expert ,but with this action "lsusb" I had this answers
ehmm...finally I'm sorry for my english

---

### Post by Sef on 2009-01-03
1) Moved to absolute beginner.

2) What version of Ubuntu do you have?

3) Your English is fine.  It is very clear what you are asking.

---

### Post by NDUFB11 on 2009-01-03
thnks for you interest
my version is ubuntu 8.10 intrepid
I'm sorry if I have posted in uncorrect topic #-o

---

### Post by NDUFB11 on 2009-01-04
Have you need of some information like this? 

patrizio@ubuntu:~$ ls -l /dev/vi*
crwxrwxrwx+ 1 root video 81, 0 2009-01-04 10:59 /dev/video0
patrizio@ubuntu:~$ 



uid=1000(patrizio) gid=1000(patrizio) gruppi=4(adm),20(dialout),24(cdrom),44(video),46(plugdev),108(lpadmin),123(admin),124(sambashare),1000(patrizio)
patrizio@ubuntu:~$ 

please...

---

### Post by scorp123 on 2009-01-04
> **NDUFB11 said:**
> Hi to everybody ! I'm a new entry with ....old commons problem
Could someone help me? My webcam doesen't function and I have just intalled several package or progranms uselessly
Thanks and happy new year : )

patrizio@ubuntu:~$ lsusb
Bus 003 Device 002: ID 0425:f102 Motorola Semiconductors HK, Ltd
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 004: ID 0c45:613c Microdia PC Camera (SN9C120)
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I'm not an PC expert ,but with this action "lsusb" I had this answers
ehmm...finally I'm sorry for my english

Try these threads:
[http://ubuntuforums.org/showthread.php?t=436732](http://ubuntuforums.org/showthread.php?t=436732)
[http://ubuntuforums.org/showthread.php?t=449721](http://ubuntuforums.org/showthread.php?t=449721)
[http://ubuntuforums.org/showthread.php?t=449740](http://ubuntuforums.org/showthread.php?t=449740)

---

### Post by NDUFB11 on 2009-01-04
I try now them and I make to know you

---

### Post by scorp123 on 2009-01-04
> **NDUFB11 said:**
> I try now them and I make to know you ... whatever ... :confused:

---

### Post by NDUFB11 on 2009-01-04
Beleave me,I would like to avoid you evrythink possible ! :(

I Have readed this links,( with similar problems ) and I have installed other think.. .
but in this case:
[http://www.linux-projects.org/modules/mydownloads/viewcat.php?cid=7](http://www.linux-projects.org/modules/mydownloads/viewcat.php?cid=7)
I can't install 
Download Now!Generic SN9CXXX Video4Linux1 & Video4Linux2 driver for Ubuntu 7.04 (Feisty, 32Bit) 
meybe because my ubuntu is intrepid and not feisty? ..but I haven't found for them 

so I have fallowed this guide(every guide has always other links )
 [https://groups.google.com/group/microdia/web/testing-microdia-driver-draft](https://groups.google.com/group/microdia/web/testing-microdia-driver-draft)
but in the 5 step I haven't no one answer from my terminal...positive or negative 

I have installed so camorama or cheese .... and by terminal I have this : 

patrizio@ubuntu:~$ camorama
/home/patrizio/.themes/Darker theme/gtk-2.0/gtkrc:50: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/patrizio/.themes/Darker theme/gtk-2.0/gtkrc:51: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/patrizio/.themes/Darker theme/gtk-2.0/gtkrc:52: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.

and from an windows
Could not connect to video device (/dev/video0)
please check connection

So from my inexperience I thought that the problem is the device ....

---

### Post by NDUFB11 on 2009-01-06
I think that the problems are or the device,because I have this result


patrizio@ubuntu:~$ lsmod | grep video
video                  25104  0
output                 11008  1 video
videodev               41344  1 sn9c102
v4l1_compat            22404  1 videodev
or this gspca,so I have followed this guide again 


[http://ubuntufacile.blogspot.com/2007/12/abilitare-il-modulo-gspca-per-webcam.html](http://ubuntufacile.blogspot.com/2007/12/abilitare-il-modulo-gspca-per-webcam.html)

 and I had a uncorrect make

patrizio@ubuntu:/usr/src/gspcav1-20071224$ sudo make
[sudo] password for patrizio: 
make -C /lib/modules/`uname -r`/build SUBDIRS=/usr/src/gspcav1-20071224 CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /usr/src/gspcav1-20071224/gspca_core.o
/usr/src/gspcav1-20071224/gspca_core.c:54:27: error: asm/semaphore.h: Nessun file o directory
/usr/src/gspcav1-20071224/gspca_core.c: In function &#8216;spca5xx_ioctl&#8217;:
/usr/src/gspcav1-20071224/gspca_core.c:2463: error: implicit declaration of function &#8216;video_usercopy&#8217;
/usr/src/gspcav1-20071224/gspca_core.c: At top level:
/usr/src/gspcav1-20071224/gspca_core.c:2609: error: unknown field &#8216;owner&#8217; specified in initializer
/usr/src/gspcav1-20071224/gspca_core.c:2609: warning: initialization from incompatible pointer type
/usr/src/gspcav1-20071224/gspca_core.c:2611: error: unknown field &#8216;type&#8217; specified in initializer
/usr/src/gspcav1-20071224/gspca_core.c: In function &#8216;spca50x_create_sysfs&#8217;:
/usr/src/gspcav1-20071224/gspca_core.c:2769: error: implicit declaration of function &#8216;video_device_create_file&#8217;
/usr/src/gspcav1-20071224/gspca_core.c:2780: error: implicit declaration of function &#8216;video_device_remove_file&#8217;
/usr/src/gspcav1-20071224/gspca_core.c: In function &#8216;spca5xx_probe&#8217;:
/usr/src/gspcav1-20071224/gspca_core.c:4301: error: incompatible types in assignment
make[2]: *** [/usr/src/gspcav1-20071224/gspca_core.o] Error 1
make[1]: *** [_module_/usr/src/gspcav1-20071224] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make: *** [default] Error 2
patrizio@ubuntu:/usr/src/gspcav1-20071224$ 

Any suggestestion :( ?

---

### Post by chrisj26 on 2009-05-23
mate have you managed to get your webcam up and running? I too have a microdia cam and after much effort I managed to get it all working(luckily mine was a supported cam). What's the problem you're stuck at?

---

### Post by afrodeity on 2009-05-28
just managed to get my iSonix Webcam working on 64bit. Its a Microdia and I followed this [http://groups.google.com/group/microdia/web/testing-microdia-driver-draft?msg=cs](http://groups.google.com/group/microdia/web/testing-microdia-driver-draft?msg=cs) to the letter. It really works. Can't believe it. Been worrying about this for months.

---

