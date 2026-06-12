---
title: "Solved! Broadcom 4311 Access Point"
date: 2008-06-28
forum: Networking &amp; Wireless
---

### Post by WhiteHorse on 2008-06-28
This worked for me:
I have a  **Broadcom Corporation BCM94311MCG wlan mini-PCI** (rev 01) as shown by:
lspci

If you want to make your wireless card act as a Wireless Access Point (WAP) then you need to enable master mode:
iwconfig eth1 mode Master

However, this gives an error as an unsupported mode with the default drivers in Ubuntu 8.04 known as b43, b43legacy, and b43xx. Here's what I had to do to get it working:

Steps taken:
1.) Install  bcm43xx-fwcutter:
**sudo apt-get install  bcm43xx-fwcutter**

mine is bcm43xx-fwcutter version 006

2.) **Get the file bcmwl5.sys** from your windows partition or download it from your laptop manufacturer's website. It's the windows driver! Here's mine(as an attachment).

3.) Install the firmware with the following command:
[B]sudo bcm43xx-fwcutter bcmwl5.sys
[/B]
4.)Next you get rid of the b43 module:
**modprobe -r b43**
5.) Now load the b43xx module:
**modprobe b43xx**
4.) Voila! You should be able to enter Master mode with the following:
**iwconfig eth1 mode Master**

Now you can proceed to the usual HowTos on setting up an AP with bridging, dns, dhcp, etc.

---

### Post by WhiteHorse on 2008-06-28
Seems this works to get master mode enabled but then I can't use ifconfig to set the parameters for the card... It just says device not found. I must be missing something...

Must do the following:

modprobe -r b43 b43legacy ssb bcm43xx
modprobe bcm43xx

I also had to reinstall bcm43xx-fwcutter from the repos and it reinstalled the firmware. All seems to be working now. Yay! Don't forget to add the following to /etc/modprobe.d/blacklist 

blacklist b43
blacklist b43legacy
blacklist ndiswrapper

and also to /etc/modules add:
bcm43xx

Oh and one more thing, ssb module prevents bcm43xx from loading so you have to create a file called /etc/init.d/bcm43xx and add the following:
#! /bin/sh
### BEGIN INIT INFO
# Provides: bcm43xx
# Required-Start:
# Required-Stop:
# Default-Start: S
# Default-Stop:
# Short-Description: enable to load broadcom drivers
# Description: enable to load ndiswrapper
### END INIT INFO

rmmod ohci_hcd
rmmod ssb
rmmod bcm43xx
modprobe bcm43xx
modprobe ssb
modprobe ohci_hcd

############# end file ############

Then do a 

sudo chmod 755 /etc/init.d/bcm43xx

Then link to it in rc2.d so it runs at boot:

sudo ln -s /etc/init.d/bcm43xx /etc/rc2.d/S99bcm43xx

---

