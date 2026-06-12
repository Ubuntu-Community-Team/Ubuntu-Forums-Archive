---
title: "working with GPS receiver"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by fredfelter on 2009-01-01
I am having ongoing problems with the computer (Thinkpad T22, Ubuntu 8.04) seeing my GPSrs. Finally I installed the Garmin_gps module, viewed a working connection with dmesg and then managed to get GPSMan and my usb eTrex to see each other. Next I tried to do the same with my serial eTrex but no go. Now I go back to the usb unit and nothing is working again.
This is from ¨dmesg¨:

 1314.296316] usb 1-1.3: new full speed USB device using uhci_hcd and address 4
[ 1314.346885] usb 1-1.3: configuration #1 chosen from 1 choice
[ 1315.664827] usb 1-1.3: USB disconnect, address 4
[ 1322.629239] usb 1-1.3: new full speed USB device using uhci_hcd and address 5
[ 1322.649988] usb 1-1.3: configuration #1 chosen from 1 choice
[ 1347.925860] usb 1-1.3: USB disconnect, address 5
[ 1348.032685] usb 1-1.3: new full speed USB device using uhci_hcd and address 6
[ 1348.052720] usb 1-1.3: configuration #1 chosen from 1 choice
[ 1364.786221] usb 1-1.3: USB disconnect, address 6
[ 1560.225370] usb 1-1.3: new full speed USB device using uhci_hcd and address 7
[ 1560.354420] usb 1-1.3: configuration #1 chosen from 1 choice
fred@fred-laptop:~$ 
 

There is no mention of a Garmin device at /dev/ttyUSB0. 
I have no idea what is going on but I´d sure like to know if someone has experience with this issue.
Thanks.

---

### Post by mikepeters76 on 2009-04-18
hi, did you solve this problem?  I have an etrex H and am trying to connect via my serial port, I am running 8.04, I get nothing when I connect the cable to the serial port via dmsg and nothing in /var/log/messages either.

---

### Post by fredfelter on 2009-04-19
> **mikepeters76 said:**
> hi, did you solve this problem?  I have an etrex H and am trying to connect via my serial port, I am running 8.04, I get nothing when I connect the cable to the serial port via dmsg and nothing in /var/log/messages either.

Nope, not yet. 
I had given up again but a couple days ago I got inspired to launch back into the GPSr-Ubuntu challenge since I had run into a new app called TangoGPS that was described as easy to use. It looked great after the download but sure enough it couldn't see my GPSr.

The key to all this is GPSd which is the link app between the GPSr and the end app. I cannot make it work nor can I find any clear instructions on what to do to get there. This is all strange because I can't believe but a fraction of Linux users interested in working with their GPSrs would be able to configure GPSd on their own. Why do the app people, like Tango, Vicking, GPSMan, etc. not provide the info to make GPSd function because without it there is no hope to be able to use the app with satellite data?

---

### Post by jimmyjones on 2009-04-22
If I enter

sudo modprobe garmin_gps


the system installs the garmin driver and mapquest (running under wine) sees the gps (garmin quest)

I just need to make the loading of the garmin driver part of boot. 

I'm trying to figure out how I did it before.

The kernel is suppose to support the garmin, so the driver isn't needed, but it is for Hardy.

I think I need to un blacklist the garmin driver.

---

### Post by PhrankDaChickenGeek on 2009-04-23
Just add the module name to /etc/modules to load it at boot

---

### Post by gerkin on 2009-07-01
I'm using an eTrex yellow and a eTrex H with no problems on Intrepid, Crunchbang & Juanty

Check out my thread here: [http://ubuntuforums.org/showthread.php?t=875478](http://ubuntuforums.org/showthread.php?t=875478)

I will be posting a 0.4 version of my Garmin script (hopefully) in the next few days>

Feel free to and email me if you have any suggestions/questions

cheers..............gerkin

---

