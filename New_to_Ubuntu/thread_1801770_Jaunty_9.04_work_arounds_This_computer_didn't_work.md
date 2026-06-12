---
title: "Jaunty 9.04 work arounds? This computer didn't work with newer version."
date: 2011-07-11
forum: New to Ubuntu
---

### Post by lucyi on 2011-07-11
Do I ditch the old computer so I can upgrade to the latest Ubuntu versions?  When 9.04 was installed in April, we tried a 10.? and this computer didn't  work well with it at all, but Jaunty 9.04 was fine.  Now I want to use a new printer and can't get the driver because the Ubuntu is too old. Are there any work-around solutions to use with outdated unsupported versions?  
Jaunty9.04, Gnome, Debian.  Computer: Gateway year 2002, came with WinXP, and Celeron processor.  I got it for free in 2008, and spent a few hundred having memory added and other things tweaked.  Until April 2011 used the WinXP and HP Deskjet 722C from 1998.  The printer started getting wonky so I got a new HP Deskjet 1000 J110 this past week, but HPLIP does not support 9.04 and I'm having trouble installing newer version printer software from HPLIP.  
 I have learned how to use a few terminal commands and almost had HPLIP 3.10.9 installed when I hit a wall missing four dependencies: python-devel; cups-devel; libtool; and cups-image.  
 Any advice much appreciated.:confused:

---

### Post by jtarin on 2011-07-11
[python-dev 2.5.2-1ubuntu1 (i386 binary) in ubuntu jaunty]("https://launchpad.net/ubuntu/jaunty/i386/python-dev/2.5.2-1ubuntu1")
This package is a dependency package, which depends on Debian's default
 Python version (currently v2.5). (Must be installed first)
[You can find your other packages here also if they are not found in Synaptic.]("https://launchpad.net/ubuntu/jaunty")

---

### Post by Bucky Ball on 2011-07-11
Which April are you talking about? 2011? If not, a lot has changed in the 10.xx releases. I couldn't install 10.04 LTS last November. It installed without issue a couple of nights ago.

Try installing a 10.xx again and let us know the probs in a new thread. It would be wise to ditch 9.04 if possible. It is well out of support. (This will create security issues, amongst other things.)

> python-devel; cups-devel; libtool; and cups-image.  

Have you looked for these in Synaptic? If they are there, just install them.

---

### Post by oldos2er on 2011-07-11
You need to switch to the old releases repos, if you haven't already. [http://atlanticlinux.ie/blog/?p=143](http://atlanticlinux.ie/blog/?p=143)

---

### Post by LowSky on 2011-07-11
you could always try the alternative CD installation. it usually goes much smoother than the livecd version on older hardware.

---

### Post by bennyroger on 2011-07-11
I advice you to install lubuntu or Linux Mint LXDE if you run on old hardware, your computer will feel like brand new again :-)
I run these on a IBM laptop with 384mb ram and 466Mhz processor and its more than fast enough...........

---

### Post by lucyi on 2011-07-12
Thanks everybody.  I have given up for now.  It's too much for my brain to handle.  When I can afford it, I'll get a new 'puter and go from there.

---

