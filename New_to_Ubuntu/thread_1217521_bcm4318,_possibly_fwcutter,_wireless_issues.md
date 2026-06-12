---
title: "bcm4318, possibly fwcutter, wireless issues"
date: 2009-07-19
forum: New to Ubuntu
---

### Post by noclock on 2009-07-19
I'm having trouble connecting to a wireless network on ubuntu 8.10.  the wireless card if bcm4318, ndiswrapper is installed, bcm43xx is blacklisted, and i have the appropriate driver on the computer.  or, at least, as far as I can tell, all those things have happened.  i am still new to ubuntu and linux, so i can't say for certain that I actually understand the way things are.
the command ndiswrapper -l gives 
"bcmwl5 : driver installed
              device (14E4:4318) present (alternate driver: ssb)"

my best guess at the moment as to the problem is that it involved not having fwcutter working.  system>administration>hardware drivers opens a window that says: no proprietary drivers are in use on this system.  i think bcm4318 is a 'proprietary driver', right?  so that would seem like a problem.
'broadcom b43 wireless driver', with an empty grey bubble to its left is in the upper subwindow.
in the lower subwindow, I see:
'Broadcom B43 wireless driver
tested by the ubuntu devlopers
license: free
fwcutter is a tool which can extract firmware from various source files.  it's written for bcm43xx driver files.'
I clicked "activate" in the lower right hand corner, and its gets 50% through "downloading and installing drivers", then the progress window closes and i am still wireless-less.

in the terminal, i tried:
"sudo apt-get install b43-fwcutter"
and get the following:
"Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up b43-fwcutter (1:011-4ubuntu1) ...
--2009-07-19 11:16:59--  [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
Resolving downloads.openwrt.org... failed: Name or service not known.
wget: unable to resolve host address `downloads.openwrt.org'
dpkg: error processing b43-fwcutter (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 b43-fwcutter
E: Sub-process /usr/bin/dpkg returned an error code (1)"

this error happened because it can't access the internet, right?  is there anyway I can get my wireless working without directly using the internet?  I used a different computer to download the bcmwl5 driver and ndiswrapper to a zip drive that i then loaded on to the ubuntu comp last time that something similar happened.
am i on the right track with this?
any help is greatly appreciated.

---

### Post by Tman5293 on 2009-07-19
Is this a laptop or desktop cause if its a laptop you can just go to your router and use a ethernet connection to get internet. Then you can use sudo apt-get install b43-fwcutter. I had this same problem with my broadcom wireless card.

---

### Post by noclock on 2009-07-19
it would be kind of a hassle to reconnect this thing with an ethernet cord.  is there a solution that doesn't involve that?

---

