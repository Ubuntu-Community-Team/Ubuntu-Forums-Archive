---
title: "Edgy 64 bit, RTL8168/8111 - Manual Driver Install?"
date: 2007-02-24
forum: Networking &amp; Wireless
---

### Post by kreyszig on 2007-02-24
Hi all,

I'd really appreciate some help setting up my network drivers manually. I have downloaded the drivers for my network interface (onboard RTL8168/8111, the closest I could find were specified : [Linux driver for kernel 2.4.x and 2.6.x (Support x86 and x64)] on the realtek site) and followed the readme instructions:

  Unpack the tarball :
	tar vzxf r1000_vX.YZ.tgz

  Change to the directory:
	cd r1000_vX.YZ

  If you are running the target kernel, then you should be
  able to do :

	make clean modules	(as root or with sudo)
	make install
	depmod -a


sudo'ing when required. However my network device is still showing as unknown and I'm not really sure what the next diagnostic step is. No errors reported when doing the above. Am I right to use the linux drivers from the realtek site, or will these not work at all?
I have seen posts about this device stating that it is now supported in latest releases - however I downloaded this edgy 64bit yesterday (from a UK mirror) so I guess it hasn't made it's way into 64bit yet. 
Your help/advice very much appreciated..

---

### Post by kreyszig on 2007-02-24
...I've also just tried the latest 32bit (alternate) version and it doesn't know about this device either. Can anyone help? I am completely stuck!

---

