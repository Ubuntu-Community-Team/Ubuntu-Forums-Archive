---
title: "WPN111 usbid changes?"
date: 2007-01-03
forum: Networking &amp; Wireless
---

### Post by sy1911 on 2007-01-03
Hello all,

First off, I'm completely new to the forum, so I apologize ahead of time if I breach some kind of etiquette or protocol.  

Is it common for usbid's as reported by lsusb to change, and if so, why/how does it happen?  I looked around but couldn't find anything; my impression is that the id is supposed to be a fixed association with the chipset.

Background:
I have a Netgear USB WPN111 that I have finally managed to get installed and working under Dapper(Gnome).  But it took a LOT of going around in circles, and I have noticed something really weird that happened in order for it to work.  The USBID changes, and only under one sequence of steps (that I have found).  Upon plugging the device, it comes up with a usbid of 1385:5f01.  I could not get the device to work with ndiswrapper while this was the case, even following the hints on the wiki list.  But (using the CD drivers) I got it to work by:  

ndiswrapper -i {path}/ndis5/athwpn.inf
ndiswrapper -i {path}/ndis5/netwpn11.inf
(here nidswrapper -l yields:  
athwpn : driver installed
        device (1385:5F01) present
netwpn11 : driver installed)
modprobe -r ndiswrapper
modprobe ndiswrapper 

and then wlan0 was created(inexplicably renamed to wlan1) and could be configured.
running ndiswrapper -l now gives:
athwpn : driver installed
netwpn11 : driver installed
        device (1385:5F00) present


Trying to associate 1385:5f01 with the netwpn11.inf results in failure.  athwpn doesnt actually seem to be necessary, I can uninstall it, unload ndiswrapper and reload and it works again.  But if I dont also install athwpn to begin with the usbid wont change.  I can plug in and remove the wireless stick all day, and the usbid won't change until I do the above.  It will even stick after reboot.  

Any experience with this and/or thoughts why this is happening?
 
Thanks ahead of time,
SY

---

