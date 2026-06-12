---
title: "WMP54G card freezes on connect"
date: 2007-06-10
forum: Networking &amp; Wireless
---

### Post by cyran on 2007-06-10
I got a Linksys WMP54G ver 4.1 installed via a PCI slot on a fairly old desktop PC that works in Windows, but completely locks up Feisty Fawn as soon as one tries to connect to the router-- which it detects fine. I've found similar, but not identical, cases on the forums, so I don't know if I can trust solutions that were for Edgy or that do have some internet connection. I can't attach an Ethernet to the PC or anything, so there's no internet at all for Ubuntu-- so I can't tell if the latest .20.x kernel updates fix this or not. It seems to be using the rt61 driver.

I've read allusions...somewhere(I didn't bookmark it apparently)... that I should add rt61 to a blacklist file and use rt61pci instead, but for it to be successful I have to blacklist it before I even 'install' the card. How does that work? Would I have to physically uninstall the card, then boot up and blacklist the module, then stick it back in? Or just uninstall the rt61 module via Synaptic or such?

---

### Post by roar on 2007-06-11
got the same card.. its working, but in dapper, which seems to be the only ubuntu I can install on the old desktop. Just thought I`d let you know, but it doesn`t help much for feisty off course.

Used the howto on

[http://ubuntuforums.org/showthread.php?t=132980](http://ubuntuforums.org/showthread.php?t=132980)

---

### Post by waylow on 2007-06-12
I have the same card and I managed to get it working on Feisty thanks to this thread

[http://ubuntuforums.org/showthread.php?t=202834]("http://ubuntuforums.org/showthread.php?t=202834")

it was a about a month ago now but from memory 
you need the ndiswrapper driver
make sure the system sees your wireless card as **wlan** not eth
and if you are using WPA security instead of WEP there are a few extra steps

it is all there on the link

I am pretty new to linux but let me know if you get stuck
although weiman01 from the thread is great

---

