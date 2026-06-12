---
title: "D-link DWA-160 + Ubuntu?"
date: 2008-10-18
forum: Networking &amp; Wireless
---

### Post by Purefire on 2008-10-18
Hey there, I'm running Hardy on my laptop and the internal wireless died (technically the mini-pci-express slot died...)   I've been a long time windows user and am trying to expand my knowledge into the linux area a bit more, but i ran into a problem today.   To recover my wireless connection I picked up a D-link DWA-160 usb wnic. the CD has no linux drivers and my initial searches pointed me to its Ralink chipset (Rt2870?)

i tried to get the drivers from ralink, but i couldn't get them to MAKE
-----
iapyx@iapyx-laptop:~/Desktop$ cd 2008_0925_RT2870_Linux_STA_v1.4.0.0/
iapyx@iapyx-laptop:~/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0$ ls
common   iwpriv_usage.txt  os          RT2870STA.dat  tools
include  Makefile          README_STA  sta
iapyx@iapyx-laptop:~/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0$ sudo make
make -C tools
make[1]: Entering directory `/home/iapyx/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/tools'
gcc -g bin2h.c -o bin2h
bin2h.c:28:19: error: stdio.h: No such file or directory
bin2h.c:29:20: error: string.h: No such file or directory
bin2h.c:30:20: error: stdlib.h: No such file or directory
bin2h.c: In function ‘main’:
bin2h.c:34: error: ‘FILE’ undeclared (first use in this function)
bin2h.c:34: error: (Each undeclared identifier is reported only once
bin2h.c:34: error: for each function it appears in.)
bin2h.c:34: error: ‘infile’ undeclared (first use in this function)
bin2h.c:34: error: ‘outfile’ undeclared (first use in this function)
bin2h.c:42: warning: incompatible implicit declaration of built-in function ‘memset’
bin2h.c:45: warning: cast to pointer from integer of different size
bin2h.c:46: warning: cast to pointer from integer of different size
bin2h.c:49: warning: incompatible implicit declaration of built-in function ‘printf’
bin2h.c:54: warning: incompatible implicit declaration of built-in function ‘printf’
bin2h.c:57: warning: incompatible implicit declaration of built-in function ‘strcat’
bin2h.c:69: error: expected expression before ‘)’ token
bin2h.c:71: warning: incompatible implicit declaration of built-in function ‘printf’
bin2h.c:76: error: expected expression before ‘)’ token
bin2h.c:78: warning: incompatible implicit declaration of built-in function ‘printf’
bin2h.c:146: warning: incompatible implicit declaration of built-in function ‘sprintf’
bin2h.c:155: warning: incompatible implicit declaration of built-in function ‘exit’
make[1]: *** [all] Error 1
make[1]: Leaving directory `/home/iapyx/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/tools'
make: *** [build_tools] Error 2
iapyx@iapyx-laptop:~/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0$ 
-----

I tried using the NDISWrapper to install the win32 XP driver from the CD, and it looks like it installed... but Ubuntu still isnt talking to the card.

-----
iapyx@iapyx-laptop:~/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0$ ndiswrapper -l
rt2870 : driver installed
	device (07D1:3C11) present
-----



any suggestions? I hate to take things back, and the card looks like it'll fit my need, so i'd like to use it if i can...

I wont be back to check till after midnight tonight, but I'm hoping someone can lend a hand to a linux-newb

---

### Post by sixstringmonk on 2008-11-20
Any luck? I'm thinking of picking up a DWA-160 myself.

---

### Post by loveeer on 2008-11-20
I'll give you a quick reference for the DWA-110.  This uses the rt73 driver.  I'll take it as a given that your driver is the right one.  I simply don't know.  There is a list of suitable drivers somewhere.

[http://ubuntuforums.org/showthread.php?t=400236&highlight=dwa-110](http://ubuntuforums.org/showthread.php?t=400236&highlight=dwa-110)

This technique assumes you have as least ethernet connection to the Internet.

Download your driver to /usr/src.  Set your pointer to that  cd /usr/src

Untar it  (sudo tar -zxvf  ....)

Usually it would have a Module directory.  Go to that

sudo cd ./rt2570......./Module

sudo aptitude install build-essential linux-headers-`uname -r`

You need those progs to compile your driver.  Note the back inverted comma, found under the tilde on my keyboard

You can then make and then make install your driver

and then modprobe it.  See the reference for details.

REMEMBER every time you change your kernel, you need to re-compile the driver.  My driver came from serialmonkey.com and the rt3570 one does too.  You will have to change some of the blacklisting, because there are conflicts between rt73usb and rt3570.

I hope this helps.

Cheers, loveer

---

### Post by Wulfrunner on 2008-11-24
I have a dwa-130 that uses the rt2870 driver. loveeer is correct that you will need the build-essential package in order to run the make commands. I had trouble with NetworkManager playing nicely with the rt2870 in Hardy and had to do some messing around with wpa_supplicant to get it working. The good news is that the driver works very well with the version of NetworkManager included with Intrepid Ibex so it may be worth upgrading. Running "make" then "make install" (then restart) should get things up and running.

---

### Post by CDrewing on 2009-09-13
Well I do not understand your problems - perhaps they added the ar9170 drivers in the mean time.

I am running Ubuntu 9.04 Jaunty from a live DVD and the Dlink DWA-160 runs from the scratch. No problem at all.

Can anyone tell how I can figure out if it is connecting with **802.11_g_** or **802.11_n_**? Just want to make sure that I got full throttle :D

Best regards
Christian

---

