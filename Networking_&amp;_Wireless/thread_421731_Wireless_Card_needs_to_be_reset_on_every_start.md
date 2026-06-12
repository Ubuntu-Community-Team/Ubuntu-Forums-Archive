---
title: "Wireless Card needs to be reset on every start"
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by mrjoey on 2007-04-24
Specs: D-Link  WNA-2330 wireless card on a Thinkpad T21 with Ubuntu 7.4.  

Using this documentation,.

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Install](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Install) 

I've been able to load the proper driver, and my wireless card works (finally!). However, every time I restart, I need to run the following code in the terminal:

$ sudo modprobe ndiswrapper

How can I make it start every time?

I installed a .sys as a driver by mistake.  if I run:

$ ndiswrapper -l

I receive this message:

ar5211.sys : invalid driver!
file : invalid driver!
net5211 : driver installed
        device (168C:0013) present

Is that apart of the problem?  I've tried to uninstall it but not sure how.

---

### Post by spd106 on 2007-04-25
You should be able to remove the driver by using this command, first making sure that ndiswrapper has been unloaded.
```
sudo modprobe -r ndiswrapper
```
```
sudo ndiswrapper -r ar5211.sys
```
If that fails you might try deleting the /etc/ndiswrapper/ar5211.sys/ directory

To make sure that ndiswrapper is loaded on startup check that it is listed in the /etc/modules file.

---

### Post by NullHead on 2007-04-25
You might try.
```
sudo ndiswrapper -m
```

---

