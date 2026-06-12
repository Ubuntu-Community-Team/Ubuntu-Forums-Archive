---
title: "Dlink DWL-G132 USB Success!"
date: 2007-08-17
forum: Networking &amp; Wireless
---

### Post by HermanAB on 2007-08-17
Howdy folks!

I got the Dlink DWL-G132 USB adaptor to work.  To do that, I copied the drivers (Two .inf and one .bin file) from the CD to /usr/local/bin.  Then I loaded both .inf files using 'ndiswrapper -i filename.inf'.  Finally, I wrote this little script:

#! /bin/bash
# Bring the USB Dlink DWL-G132 WiFi adaptor up
killall dhclient
ifconfig eth0 down
ifconfig wlan0 down
sleep 1
rmmod ndiswrapper
rmmod bcm43xx
sleep 1
loadndisdriver /usr/local/bin/ar5523.bin
sleep 5
modprobe ndiswrapper
sleep 1
iwconfig wlan0 mode managed essid aeronetworks key 1234567890
sleep 1
ifconfig wlan0 up
dhclient wlan0 

The script first removes all competing drivers, then load the WiFi program to the little Arm processor, wait for the dust to settle and then load ndiswrapper with the Windows driver.  After that, wlan0 is visible and can be configured the usual way.

I simply put the script in /usr/local/bin made it executable and added a launcher to the desktop.

La Voila!

Cheers,

Herman

---

### Post by josb on 2007-09-05
Hey,, is this solution for x64 version of window?
or is it just for x32?

---

