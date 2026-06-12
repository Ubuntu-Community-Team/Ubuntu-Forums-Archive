---
title: "Wireless card won't display"
date: 2007-10-22
forum: Networking &amp; Wireless
---

### Post by chowdahead84 on 2007-10-22
I recently installed ubuntu, and I can't get it to do much yet, mostly because I can't connect to the internet.  I have a Trendnet TEW-423PI wireless card (which apparently is not automatically supported but can work with ndiswrapper).  I have tried installing ndiswrapper via both the graphical application tool and with the terminal/install cd.  It seems it is not on the install cd, so I can't install it that way, and when I downloaded the files from a different computer and put them onto my desktop with a flashdrive, I can't get it to install that way either.  I have followed the instructions on how to install ndiswrapper to the letter and still it won't work.  I am hoping once I can connect I can get drivers and codecs to get everything else to work, but really nothing can work until I can connect.  I would greatly appreciate any help on how to install ndiswrapper (if that is in fact the best method to fix this problem).  Thanks in advance.

---

### Post by loveshackdave on 2007-10-22
ndiswrapper should be on the cd and you can easily install it with synaptics. Make sure the cd is mounted. click on System > Administration > Software Sources  and make sure the CD is enable as a software source. Then open Synaptics and click update, search for ndiswrapper and install. 

Is your wireless card broadcom based? if so, you will have to disable the native driver for the cards. Most people do this:

sudo rmmod bcm43xx
sudo vim /etc/modprobe.d/blacklist
add this line: blacklist bcm43xx
reboot.

This however did not work for me and I had to physically delete the drivers in order to get them not to load. Type modprobe -l | grep bcm43xx in order to get the path to the drivers, then cd to the path and delete the drivers.

---

