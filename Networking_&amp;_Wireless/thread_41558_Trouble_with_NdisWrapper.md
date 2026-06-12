---
title: "Trouble with NdisWrapper"
date: 2005-06-13
forum: Networking &amp; Wireless
---

### Post by vtechstu on 2005-06-13
Ok, I'm new here to ubuntu, and even more new to X.  I got ubuntu to install great second time, lets not talk about the first.  Anyway, I can't seem to get NdisWrapper to install so I use my wireless.  When I ran the "make, make install" this is what i got.

chase@ubuntu:~/ndiswrapper-1.1$ make
make -C driver
make[1]: Entering directory '/home/chase/ndiswrapper-1.1/driver'
Can't find kernel sources in /lib/modules/2.6.10-5-386/build;
  give the path to kernel sources with KSRC=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory '/home/chase/ndiswrapper-1.1/driver'
make: *** [all] Error 2
chase@ubuntu:~/ndiswrapper-1.1$

Please help if you can.  Thanks.

---

### Post by AMP on 2005-06-13
> **vtechstu]Ok, I'm new here to ubuntu, and even more new to X.  I got ubuntu to install great second time, lets not talk about the first.  Anyway, I can't seem to get NdisWrapper to install so I use my wireless.  When I ran the "make, make install" this is what i got.

chase@ubuntu:~/ndiswrapper-1.1$ make
make -C driver
make[1]: Entering directory '/home/chase/ndiswrapper-1.1/driver'
Can't find kernel sources in /lib/modules/2.6.10-5-386/build said:**
> : *** [prereq_check] Error 1
make[1]: Leaving directory '/home/chase/ndiswrapper-1.1/driver'
make: *** [all] Error 2
chase@ubuntu:~/ndiswrapper-1.1$

Please help if you can.  Thanks.

Ok make sure you have headers, so in Synaptic search headers and install those, also install gcc and then try a new build you should be golden!

---

### Post by vtechstu on 2005-06-14
Ok, thanks for all of that.  I realized i had the wrong ndiswrapper package.  I went through the SetupNdiswrapperHowTo guide and got it all set up to there.  Now, I started the WiFiHowTo and got stuck.

Doing it manually, i did
 ifconfig
sudo ifdown eth0
sudo ifup wlan0

This is where i stopped because this last one gave me "Ignoring unknown interface wlan0=wlan0.  Any ideas what is wrong/doing wrong? 

Also under network settings, it shows all of this, but in grey(can't edit/select):

wlan0        disabled wireless network device

Is this normal up to this point?  Thanks.

---

### Post by GeneralCody on 2005-06-14
U have to make a link:
sudo ln -s /usr/src/linux-<kernel-version> /lib/modules/VERSION/build

replace <kernel-version> with your kernel as in 
uname -r
and VERSION with the same kernel version number.

From your output u are running the 2.6.10-5-386 kernel.

This assumes u have the linux-headers package for your running kernel installed.

---

### Post by vtechstu on 2005-06-14
Once i get this done, should i start the WiFi HowTo again?  Or what?  Thanks for your help though.

PS..The only thing i didn't get to work with installing Ndiswrapper was the sudo gedit /etc/modules .  said something about not knowing what gedit was. weird

---

### Post by vtechstu on 2005-06-15
Finally got the wireless to work! So excited.  The only thing left to do is to get it to automatically get it to get an IP and to load in general, on start up.  

I did modprobe ndiswrapper, which gets it going, but it wasn't there when i logged back on.  I even did ndiswrapper -m but still didn't load at startup.  Any ideas?  Thanks!

---

### Post by Mr. Electric Wizard on 2005-06-15
Does anybody know if I need these Kernel Headers to modprobe ndiswrapper?
When I  sudo modprobe ndiswrapper, I get a Fatal Error?
[Here is a link to my thread in the Beginners Forum](http://www.ubuntuforums.org/showthread.php?t=40254&page=2) 
Any more expertise is greatly appreciated!
 :)

---

