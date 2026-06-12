---
title: "BCM4318 wireless still not working"
date: 2009-07-25
forum: New to Ubuntu
---

### Post by MarkTX on 2009-07-25
I've found many tutorials about how to install drivers for the 05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02) but still no luck getting it connected.

I've got the latest bcmwl5a.inf and sys files
I've got ndiswrapper

i've run 'ndiswrapper -i bcmwl5a.inf' and it has installed itself, visible with ndiswrapper -l

But still nothing in network connections about it even starting up.

Please could someone help me find a single, simple (hopeful) way to get this resolved?


Thanks!!

---

### Post by LookTJ on 2009-07-25
I believe all bcm43xx models have a bug of some sort

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/365857](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/365857)

but then again, it depends on the revision(rev) of your card.

But you could try enabling the driver through restricted driver manager

---

### Post by lkraemer on 2009-07-25
MarkTX,
First of all you need to check out what drivers are already loaded,
before you start installing more!

If I remember correctly the bottom of your post states you are running
Jaunty (9.04) and it most likely has some drivers pre-installed for the
Broadcom hardware.

So, first remove the drivers installed with ndiswrapper, and remove
the ndiswrapper module.  Then use the lsmod command in a Terminal window
to see what Broadcom Drivers are installed (may want to Blacklist them
and use others).  At this point you should be back to what was originally
installed in Jaunty, unless you have loaded other drivers too!

Then you need to make a decision on what method you will use?
ndiswrapper and the Windows Drivers
b43fwcutter and the Firmware (available on the internet)
pre-installed 9.04 drivers and whatever is needed to make them work.

Looks to me like you are trying the first method, which certainly
is one way, may not be the best............as of 9.04 because
the drivers are always being updated and made to work better
in newer versions of Ubuntu.

I did choose the same method using the Windows drivers and I have
mine working, but it will not work on a WPA2 connection.

I am running 8.04.3 (Hardy Heron) and here is what I used.
[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

I made myself a txt file and here is what it contains:
		Broadcom Wireless Setup for Hardy (Step by step)
                [http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)


I used the following steps to enable my Broadcom Wireless BCM4318 on my Compaq V5201US.

    * Machine Brand and Model
      Compaq V5201US  
    * Wireless Brand and Model (please post the whole line): lspci | grep Broadcom
      06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
    * Wireless Chipset: lspci -n | grep '14e4:43'
      06:02.0 0280: 14e4:4318 (rev 02)
    * Ubuntu Version: lsb_release -d
      Description:	Ubuntu 8.04.3
    * Kernel / Architecture: uname -mr
      2.6.24-24-generic i686
    * Any extra boot options you might be using (e.g., noacpi, irqpoll, etc.)
      NONE
    * Whether or not you had to compile NDISWrapper
      NO
    * Which version of Step 2 you used (If you try the recommended step 2, and it doesn't work, and then you find some other,
      presumably newer, driver version that *does* work, please provide a link to the download, for inclusion consideration.)
      2A
    * If you're on Hardy, whether you had to apply the "Hardy Bug Fix" workaround or not
      NO


Step 1 (run in terminal)

echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
Install ndiswrapper-utils-1.9 with Synaptic.

Step 2 (run in terminal)

sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper
sudo cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
sudo ndiswrapper -m
echo 'ndiswrapper' | sudo tee -a /etc/modules
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant

Step 4 (run in terminal)

sudo aptitude remove b43-fwcutter

Step 5 (run in terminal)

sudo gedit /etc/init.d/wirelessfix.sh

Step 6

Paste the followings in the opened file(wirelessfix.sh)and make sure you save it before continuing Step 7

#!/bin/bash
modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe b44

Step 7 (run in terminal)

Run this :

cd /etc/init.d/ && sudo chmod 755 wirelessfix.sh

Step 8 (run in terminal)

finally run this:

sudo update-rc.d wirelessfix.sh defaults

Step 9
Add the DNS Servers to the Wifi Configuration in roaming mode
xx.xxx.x.x
xx.xxx.xxx.x

Restart your machine and enjoy the freedom from those wires....



lkraemer

---

### Post by keplerspeed on 2009-07-25
***REMEMBER***

When using ndiswrapper on a 64bit system, you will need the 64bit windows driver for your card.

Similarly, on 32bit ubuntu you will need to use the 32bit windows driver.

I have made this mistake a few times...

---

### Post by MarkTX on 2009-07-25
lkraemer, i tried your method above.  Removed drivers that i'd installed (which was just the bcmwl5) and followed the rest of your directions, but now i don't have wireless even listed in network manager.


Any other ideas?

EDIT:

Ok, i think i got it fixed.  I had to rename the ndiswrapper file, ndiswrapper.conf, and also i had blacklist and blacklist.conf.  I removed the blacklist so that it could read blacklist.conf.

After i did that, it all worked!

Thanks for your help guys!

---

