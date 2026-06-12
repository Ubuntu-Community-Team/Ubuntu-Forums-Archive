---
title: "Broadcom BCM4352 Issues"
date: 2015-02-06
forum: Networking &amp; Wireless
---

### Post by mdmoreau on 2015-02-06
I'm having some issues with the BCM4352 [14e4:43b1] on Ubuntu 14.04.  It seems to work fine initially with the Broadcom STA driver (installed during Ubuntu setup using ethernet), but once I power up my Windows machine on the same network the speeds of both (and other devices) plummet.  The issue only seems to be resolved once one of them goes into standby or shuts down, disabling the WiFi.  Even then sometimes it takes a while for the speed to catch back up, and on Ubuntu even accessing localhost gets really slow.

Right now the driver in use is [COLOR=#000000]6.30.223.141 which is from July 2013 ([/COLOR]http://www.broadcom.com/docs/linux_sta/README.txt).  I noticed there is a more recent driver ([http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)), but my device isn't listed on either of the readme files' supported devices.

Is this device just not well supported in Linux at the moment?  I've got other USB wifi sticks that work well on the machine, but I was hoping to use the BCM4352 since it's built-in to the motherboard.  Thanks in advance for any help!

---

