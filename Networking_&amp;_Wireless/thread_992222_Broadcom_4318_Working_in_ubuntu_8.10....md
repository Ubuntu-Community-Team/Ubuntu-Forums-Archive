---
title: "Broadcom 4318 Working in ubuntu 8.10..."
date: 2008-11-24
forum: Networking &amp; Wireless
---

### Post by myharshdesigner on 2008-11-24
Orignal Post from:
**_[http://ubuntuforums.org/showthread.php?t=885173&highlight=broadcom](http://ubuntuforums.org/showthread.php?t=885173&highlight=broadcom)_**

Post No : #9

######################################################################
 Re: Seeking Hardy users with BCM4306 Wireless that fail with b43
Larry, I'm sorry to invade your thread. However, I have the BCM4306 & may be able to contribute.

lspci -nn |grep Broadcom
00:09.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)

I get nothing with the "SPROM" commands


************************************************** ***********************


Hardy fresh install


I have a working connection with Ndiswrapper, with WPA (using XP 32bit bcmwl5.inf).


My problem...I lose the connection after a reboot. Seems like a problem with the "ssb" module loading, rather than "ndiswrapper".


To get the wlan0 connection up (from "network down") I run these in order....


sudo rmmod b43

sudo rmmod b44

sudo rmmod b43legacy #this step added Apr 27 2008

sudo rmmod ssb

sudo rmmod ndiswrapper

sudo modprobe ndiswrapper

sudo modprobe ssb

sudo modprobe b44 #this step added May 1 2008


echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/ndiswrapper

sudo /etc/init.d/networking restart


After the above, I now have my internet up!!!


According to lshw -C network...
Seems like a problem with "ssb" loading as my BCM4306 module at start, rather than "ndiswrapper". After running the above commands, the module shows as "ndiswrapper", therefor a simple network restart takes car of business.


So, how can I get Ndiswrapper, not ssb, to stick to my Broadcom interface???
######################################################################

---

### Post by Ayuthia on 2008-11-24
Do you have ndiswrapper in /etc/modules:
```
cat /etc/modules|grep ndiswrapper
```
If it is not there, ndiswrapper is not being loaded on restart.  You will need to add it by doing the following:
```
cat ndiswrapper|sudo tee -a /etc/modules
```

If you do not have a b44 module, you should be able to blacklist the b43 and ssb module and they will not come up on reboot.  If you are not for sure, please post the results of:
```
lshw -C network
```

---

