---
title: "IPWireless setup"
date: 2005-09-16
forum: Networking &amp; Wireless
---

### Post by ehsan on 2005-09-16
Hi all,

I have recently installed Ubuntu 5.04 AMD64 on my Compaq R3440CA laptop.  The installation was smooth, and I had no problems with that.

Then, I tried to setup my IPWireless connection, which has a USB modem (which seems to belong to the [www.ipwireless.com](http://www.ipwireless.com/)  manufaturer.)

While having a console window running 'tail -f /var/log/messages' open, I plugged in the USB modem, and the ipw kernel module got loaded correctly.  I can see the device in lsusb.

I then created pppd and chatscripts based on the instructions found at [http://rodent.za.net/MyLinuxDrivers](http://rodent.za.net/MyLinuxDrivers) and [http://www.wlug.org.nz/WooshWireless](http://www.wlug.org.nz/WooshWireless) .

Then I executed 'sudo pppd debug call datakipw', where datakipw is the name of the pppd peer I have created.

The /var/log/messages output shows that pppd successfully connects the ppp0 interface to /dev/ttyUSB0, but after that, no IP is assigned to the interface, and after a few seconds, the connection gets dropped with an LCP error.

The Windows client uses DHCP to obtain the IP address and nameservers, etc. so pppd should be able to do the same as well.

What's going wrong?  What can I do to get my connection working?  It's too much a pain to boot into Windows to access the net.   :? 

Thanks!
Ehsan

---

