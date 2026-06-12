---
title: "ndiswrapper - nearly but not quite"
date: 2007-09-10
forum: Networking &amp; Wireless
---

### Post by nikkkko on 2007-09-10
I have a 2004 Siemens Gigaset 54 usb wireless adapter which used to work under ndiswrapper - in 2004.  Damned if I can get it to work now.

Following the correct ndiswrapper procedure, I get to load the .inf file with no errors, ndiswrapper -l shows fine, modprobe ok with no errors, dmesg shows hardware and driver, ifconfig and iwconfig show wlan0 up and running and even the modem light blinks!  But then the light goes out and 'iwlist scan' shows no networks.

I also have a netgear wg121 adapter and following the identical procedure, this fires up fine.

Anyone got an idea, or maybe a newer .inf file for me to try?

---

### Post by nikkkko on 2007-09-21
anyone want a free Siemens Gigaset 54 usb wireless adapter?

---

### Post by HokeyFry on 2007-09-21
Question --

have you tried installing ndiswrapper from source? (the one from the [official ndiswrapper website]("http://ndiswrapper.sourceforge.net/joomla/"))

this solved loads of problems for me. if you do decide to take this route, uninstall ndiswrapper from your system, COMPLETELY, and then follow the compile instructions that come with the source code.

it seems you know how to use ndiswrapper though, so u probably dont need to look at instructions on how to install the driver again

NOTE: make sure you have the package "build-essentials" installed

---

### Post by nikkkko on 2007-09-24
You are probably right and I seem to remember I compiled ndiswrapper the last time I got it working, it's just that in the last year or so I've been able to rely completely on packages.  Not that I'm command line phobic, it's just less time consuming keeping everything working nicely together when apt-get is doing the work.

---

### Post by kevdog on 2007-09-24
Although I would recommend compiling the newest ndiswrapper version, possibly there is a way to salvage what you have.  

Can you post the following:
ndiswrapper -v
lshw -C network
cat /etc/iftab
ifconfig -a

---

