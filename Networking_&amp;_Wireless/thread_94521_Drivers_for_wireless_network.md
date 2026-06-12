---
title: "Drivers for wireless network"
date: 2005-11-24
forum: Networking &amp; Wireless
---

### Post by naxoc on 2005-11-24
Hi!

I just installed Breezy Badger and I am very pleased with how easy that is. Some years ago I put Red Hat on my machine and that was hell getting it to recongnize all my hardware. So far so good. 

I have bought a wireless network USB thingy (Planet WL-U356) that I really need to work. I found the drivers here: [http://warder.ath.cx:81/projects.php]("http://warder.ath.cx:81/projects.php") and Planet even has a driver for Linux on their homepage [http://www.planet.com.tw/support/news_more.php?start=80&sort=snews_filename%20]("http://www.planet.com.tw/support/news_more.php?start=80&sort=snews_filename%20"). Doing a lsusb shows me that the thingy is found. I also know that I need ndiswrapper.

My problem now is that I have not compiled ubuntu myself because I used the nice installer. I can see in the makefile of the driver that it needs to read some of the sourcecode on my machine. I am stuck here (and not very comfortable with compiling kernels), so can anyone help me out? I think I can do with getting the sourcecode and running "make config", but where do I get it and how do I do the "make config"?

Or, has anyone seen a walkthrough on installing drivers like the ones I found?

Thanks :-)

---

### Post by Lambert on 2005-11-24
You don't need to compile your kernel nor do you need ndiswrapper.  Ndiswrapper is making a windows driver work in linux and this looks like it has a native linux driver.

Go to this page. [http://zd1211.ath.cx/](http://zd1211.ath.cx/)

> 
**nstallation**

  [LIST]
[*]Make sure you have your kernel sources in /usr/src/linux
[*]Make sure your kernel is compiled with wireless extensions ([COLOR=Red]it is)[/COLOR] (CONFIG_NET_WIRELESS) and USB support
[*]Make sure iwconfig is installed (Debian: *wireless-tools* package)([COLOR=Red]it is)[/COLOR] [/LIST] [LIST]
[*][Download]("http://zd1211.ath.cx/download") latest drivers [/LIST] [LIST]
[*]untar, make, make install
[*]modprobe -v zd1211
[*]lsmod - you should see zd1211 loaded (see *dmesg* otherwise)
[*]ifconfig wlan0 up (*iwconfig* will not work otherwise)
[*]iwconfig wlan0 essid *youressid*
[*]dhclient wlan0 (or ifconfig.../route... for static IP) - use *dhcpd* or *pump* if your distribution does not feature dhclient [/LIST] [LIST]
[*]With Debian you can optionally use *zd1211-firmware* and *zd1211-source* packages. In addition, for managing coldplug *udev* might be useful instead of just using the required *hotplug* package. [/LIST] ?

 
You will need to install a package called build-essentals, your linux headers and maybe something else

 
[https://wiki.ubuntu.com/forum/software/Compiler?highlight=%28compile%29](https://wiki.ubuntu.com/forum/software/Compiler?highlight=%28compile%29)

---

### Post by naxoc on 2005-11-26
Thanks, that looks like something I can do. I will try it out on my day off next week and post how it went.
:-)

---

