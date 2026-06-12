---
title: "can't connect to wireless network"
date: 2007-07-02
forum: Networking &amp; Wireless
---

### Post by wtfdop0987 on 2007-07-02
i am having problems with my Broadcom BCM4311 and connecting to a wireless network.  i guess i need a guide or walkthrough to connect to my wireless network...any help?

---

### Post by Ayuthia on 2007-07-02
You will have to install a driver to get the 4311 to work.  There are two options on how to do this.  bcm43xx-fwcutter is the quickest way to get it installed, but the speed tops out at 11Mb.  All you should have to do is this (provided that you have an internet connection):
sudo apt-get install bcm43xx-fwcutter

The other option is to go through ndiswrapper.  There are a lot of steps to this but the end result can provide you speeds up to 54Mb.  Here is a link to how someone did it for their 4311 card:
[http://wiki.waningsun.net/index.php?title=Dell_E1405_%26_Linux_HOWTO](http://wiki.waningsun.net/index.php?title=Dell_E1405_%26_Linux_HOWTO)

---

### Post by jpl80 on 2007-07-02
I tried [this method of ndiswrapper and the windows bcm4306 driver]("http://ubuntuforums.org/showthread.php?t=340689&highlight=inspiron+8500"). I can now see networks in range. However, I am still having trouble connecting to them. I feel like I am one step away.

---

### Post by thierce on 2007-07-02
Does 'iwconfig' list your wireless card?
If so, did you try to configure your network with any graphical network manager?
Sometimes good old 'iwconfig' just works best ;)

---

