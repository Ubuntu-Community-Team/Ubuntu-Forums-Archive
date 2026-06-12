---
title: "Wireless Driver problems"
date: 2007-08-26
forum: Networking &amp; Wireless
---

### Post by djm5091 on 2007-08-26
I am new to linux and ubuntu.  I recently installed ubuntu on my Thinkpad R60e.  Ethernet worked right out of the box, but wireless did not.  In fact, a wireless connection did not even show under the "Connections" tab in "Wireless settings" (System-->Administration-->Networking)

I assume this means that there is no wireless driver installed in Ubuntu for my wireless card.

This is my the info for my wireless card under device manager
Vendor: Atheros Communications, Inc.
Device:  AR5212 802.11abg NIC

I pretty sure the driver i need is in madwifi-0.9.3.2.tar.bz  
I downloaded it to my ubuntu desktop, but I don't know what to do with it.  I started reading the install text file but I had trouble using it and I don't think I know ubuntu well to install it according to the text file.  Can anyone dumb it down for me?

---

### Post by kevdog on 2007-08-26
First thing is to determine the kernel version you are using.  Type
uname -r 
at command line. 

Next I would try would be to go into Synaptic and do a search for restricted modules (just type restricted in the search field)

Find the package the says linux-restricted-modules-(your kernel version here).  Use the info above to fill in the last part.

If you single click on it, you will see it says it contains the madwifi drivers.  Right click on the package and select mark for installation. Click apply and have the package be installed.  I would then reboot, and then post back what happens.

Its worth a shot at least.

Next post please list
lshw -C network
lspci -nn

---

