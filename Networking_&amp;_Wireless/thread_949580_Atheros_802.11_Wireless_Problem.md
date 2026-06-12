---
title: "Atheros 802.11 Wireless Problem"
date: 2008-10-16
forum: Networking &amp; Wireless
---

### Post by Rogue Yun on 2008-10-16
Noob here,

I can't seem to connect to the internet using my wireless card.  I've gone through several tutorials and hit stopping points somewhere along all of them at points where maybe I just didn't understand or I came across some kind of error.  Is there someone out there patient enough to help me through this one?  Thanks in advance.

Craig

---

### Post by az on 2008-10-16
> **Rogue Yun said:**
> Noob here,

I can't seem to connect to the internet using my wireless card.  I've gone through several tutorials and hit stopping points somewhere along all of them at points where maybe I just didn't understand or I came across some kind of error.  Is there someone out there patient enough to help me through this one?  Thanks in advance.

Craig

It depends on your hardware.  What kind of machine is it?  What does 
sudo lshw -C network
show?

I found these things helpful for me:

1)
[https://bugs.launchpad.net/bugs/182489](https://bugs.launchpad.net/bugs/182489)
(Synopsis:  Add the following line:
blacklist ath_pci
to the /etc/modprobe.d/blacklist file and reboot.  If you are running an up-to-date Hardy, this should enable the free/libre ath5k driver.)


2)
[http://madwifi.org/ticket/1192](http://madwifi.org/ticket/1192)
(Synopsis:
0. Connect to wired network and install build-essential (sudo apt-get install build-essential)
1. wget http: / /snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3835-20080801.tar.gz
2. tar -zxvf madwifi-hal-0.10.5.6-r3835-20080801.tar.gz
3. cd madwifi-hal-0.10.5.6-r3835-20080801
4. sudo make
5. sudo make install
6. System -> Administration -> Hardware Drivers -> Uncheck both hal and Atheros support
7. sudo vi /etc/modprobe.d/blacklist -> blacklist ndiswrapper (Do this if you had tried ndiswrapper)

This downloads and installs a non-free binary-only driver for the atheros chipset.  You need to rebuild and reinstall the driver every time you update your kernel.


3)  The wireless LED on my laptop does not work in linux.  I may have pressed the wireless button while troubleshooting and turned off wireless without knowing it.  So while fiddling around, I may have installed the right driver but not known it.

---

