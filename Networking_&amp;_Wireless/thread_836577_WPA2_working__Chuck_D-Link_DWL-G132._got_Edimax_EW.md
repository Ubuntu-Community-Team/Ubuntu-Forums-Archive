---
title: "WPA2 working : Chuck D-Link DWL-G132. got Edimax EW-7318USg"
date: 2008-06-21
forum: Networking &amp; Wireless
---

### Post by pokipoki08 on 2008-06-21
After getting a new wireless card Edimax EW-7318UGs, I got it working in less than 15 mins in Hardy. And it's still working now even after 12 hours. I haven't reboot though, but I guess it should be ok as the initialization of the wifi is done by the new linux module (rt73) and /etc/init.d/networking. **[COLOR="Blue"]No more windows drivers or ndiswrapper. No Network Manager, wicd or wpa_supplicant.[/COLOR]**

It's a good card, with exchangeable antenna! My wifi ordeal is OVER!!! Thanks to all the authors of the posts below.

Here's what I did :

Edimax EW-7318USg aka [COLOR="Lime"]Hawking HWUG1 (rebranded in US)[/COLOR]

# Driver : rt73
# Chipset : Ralink 
Ralink RT2571W chipset (can be used with rt73 drivers)
chipset : RT2571WF or RT2528L

HOWTO:RT2500 wireless cards etc. sticky
Ralink 257x/2671 using RT73 driver?

======================
I think that you might be doing some of these steps in the wrong order. eg from the instructions I was given you need to blacklist first. Here are the instructions I use:

1. sudo rmmod rt73usb (remove old drivers)

2. sudo gedit /etc/modprobe.d/blacklist and add these lines to the end of the file:

blacklist rt73usb
blacklist rt2570
blacklist rt2x00lib
blacklist rt2500usb
blacklist rt2x00usb

3. sudo apt-get install build-essential

4. sudo apt-get install linux-headers-`uname &#8211;r`

5. get the latest version of the driver source from the serialmonkey site. The name is rt73-cvs-daily.tar.gz. I saved it in my user dir:

6. sudo wget [http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz) -O ~/rt73-cvs-daily.tar.gz

7. sudo tar -zxvf rt73-cvs-daily.tar.gz

8. cd ~/rt73*/Module

9. sudo make

10. if the file produced is 2Mb in size there is a problem as it should be about 250Kb. To fix this, use the "strip" command:
strip &#8211;S rt73.ko

11. sudo make install

12. sudo modprobe rt73

13. as sudo, edit /etc/modules &#8211; add the text rt73 at the end

14. as sudo, create text file called rt73 in /etc/modprobe.d

15. put the text &#8220;alias wlan0 rt73&#8221; in this file

16. remove /etc/modprobe.conf as it&#8217;s no longer needed (back it up first &#8211; but note I didn&#8217;t have one)

17. add the following to /etc/network/interfaces file. You might need to customise this to suit your particular situation (eg if you don't use WPA encryption):

```
auto wlan0
iface wlan0 inet dhcp
pre-up ifconfig wlan0 up
pre-up ifconfig wlan0 down
pre-up ifconfig wlan0 up
pre-up iwconfig wlan0 essid "yourSSID" # use quotes if you have spaces in the name of essid
pre-up iwconfig wlan0 mode Managed
pre-up iwpriv wlan0 set Channel=11 # change channel accordingly
pre-up iwpriv wlan0 set AuthMode=WPAPSK
pre-up iwpriv wlan0 set EncrypType=TKIP
pre-up iwpriv wlan0 set WPAPSK="yourkey"
pre-up ifconfig wlan0 up
```

18. reboot

=====================

Notes :

[http://ubuntuforums.org/showthread.php?t=400236&highlight=rt73+hardy](http://ubuntuforums.org/showthread.php?t=400236&highlight=rt73+hardy)
[http://ubuntuforums.org/showthread.php?t=757607](http://ubuntuforums.org/showthread.php?t=757607)
[http://www.lockergnome.com/linux/2007/11/04/ubuntu-gutsy-with-expresscard-working-options/](http://www.lockergnome.com/linux/2007/11/04/ubuntu-gutsy-with-expresscard-working-options/)
[http://ubuntuforums.org/showthread.php?t=616685](http://ubuntuforums.org/showthread.php?t=616685)
[http://homepages.tu-darmstadt.de/~p_larbig/wlan/](http://homepages.tu-darmstadt.de/~p_larbig/wlan/)
[http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page](http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page)
[http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?t=4402](http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?t=4402)
[http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=4402](http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=4402) (older driver works)
[http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?t=4405](http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?t=4405)
Ralink RT2571W chipset (can be used with rt73 drivers)
[http://www.tu-darmstadt.de/~p_larbig/wlan](http://www.tu-darmstadt.de/~p_larbig/wlan) driver used for hacking
[http://www.lockergnome.com/linux/2007/11/04/ubuntu-gutsy-with-expresscard-working-options/](http://www.lockergnome.com/linux/2007/11/04/ubuntu-gutsy-with-expresscard-working-options/)

---

### Post by nickdbliss on 2008-06-21
Congrates buddy i have the same adapter working on my friends pc. It is good one

---

### Post by pokipoki08 on 2008-06-21
The Edimax saved me a lot of grief. Get this card if using Linux! Best money I've ever spent.

I've rebooted many times. It autodetects (module rt73 autoloads) and join my WPA2 wireless network automatically.

---

### Post by caseyb on 2009-07-03
I am attempting to follow these steps because I have an Endimax EW-7318USg.  Unfortunately, the driver source ( [http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz) ) is no longer available at that location.  Any help? :-|

---

### Post by ugm6hr on 2009-07-05
What version of Ubuntu are you using?

9.04 should work out of the box with Network Manager (it does with WPA, uncertain re: WPA2).  The driver is already included.

If it doesn't, it may be easier just to remove Network Manager, and use the included kernel driver.

This explains why the drivers are no longer available as a daily updated version (as of April 2009): [http://rt2x00.serialmonkey.com/wiki/index.php/Downloads](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads)

---

### Post by cakatz on 2009-07-28
Help! I am trying to get an Edimax EW-7318USG running on a Kubuntu Hardy system (kernel 2.6.24). I went through the whole procedure listed here, and rt73 installs just fine. However, the system never recognizes the adapter, so there&#8217;s no wlan0 available and thus nothing for rt73 to do!


 When I plug in the adapter, I just get 
     kernel: [92396.334414] usb 5-7: new high speed USB device using ehci_hcd and address 7
    kernel: [92396.605502] usb 5-7: configuration #1 chosen from 1 choice
 
lsusb says only (for this device):
 
    Bus 005 Device 006: ID 7392:7318 

 with no other identifying information.
 

Does anyone know how to get the system to recognize this as a wireless network adapter and assign it to wlan0 ?

---

### Post by cakatz on 2009-07-29
I've made some progress.  Can someone with a working EW-7318USg adapter check something for me?

1) determine the USB address: use "lsusb" or just look in the console messages when you plug in the adapter.  For example, on mine, when I plug it in, I get

Jul 29 09:33:20 encona kernel: [69332.038843] usb 5-8: new high speed USB device using ehci_hcd and address 11
Jul 29 09:33:20 encona kernel: [69332.317750] usb 5-8: configuration #1 chosen from 1 choice

2) probe the device using "udevinfo" on the USB address.  In my case it is 5-8, so I type "udevinfo -a -p /sys/bus/usb/devices/5-8:1.0/"

Look for a line reporting the MAC address.  It will look like

  ATTRS{address}=="<mac address here>"


When I do this there is *no* MAC address reported!  This could explain why the system isn't recognizing it as a network adapter.

I've now tried installing it both in Linux and on a Mac and it doesn't work in either place.  I'm beginning to suspect faulty hardware...

Anyway, if you can check that and report to me it will help me troubleshoot.  Thanks!

---

### Post by cakatz on 2009-07-29
Okay, I was wrong.  I found this:

[http://www.electricshaman.com/2009/07/17/edimax-ew-7318usg/](http://www.electricshaman.com/2009/07/17/edimax-ew-7318usg/)

The rt73 driver source just needed to have the device's vendor and product IDs added!

So simple.

---

### Post by kurraider on 2010-07-28
Thanks pokipoki08, your solution worked perfectly

---

