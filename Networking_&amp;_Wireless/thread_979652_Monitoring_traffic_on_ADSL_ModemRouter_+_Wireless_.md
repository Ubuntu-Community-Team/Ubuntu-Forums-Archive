---
title: "Monitoring traffic on ADSL Modem/Router + Wireless Traffic Monitoring"
date: 2008-11-12
forum: Networking &amp; Wireless
---

### Post by milesmonk on 2008-11-12
Dear All,
I'm a newbie, so pardon my ignorance.

Anyway, here goes.  I recently got broadband at home.  Along with the connection, I got an ADSL modem/router (Manufacturer:ITI | Model: DNA-A211-I | Board ID: 96338W-20P2).  I've configured wireless on this modem/router.  (Please note: I did not need an extra router or anything.  The modem doubles as a router.)  My roommate and I use this wireless connection.  I've enabled "Wireless Guest Network" (which is without any passwords), so that my neighbours can use it too.

Here's what I wish to do:
1. Monitor the bandwidth usage overall on this router (both the regular wireless network, as well as the guest network).  (I think Darkstat will work, but I have no clue how to install it on a modem/router.)
2. Throttle bandwidth to my neighbours when I'm at home, and enable access when I'm not.  Preferably, this should be automatic (time-bound, or something), or a simple script that I can run each time I get home.
3. Monitor (graphically, like Netspeed) and record network (wireless, that is) usage on my own computer.  This would be something on the lines of (Windows programs) DUMeter or NetMeter.  Basically, without running something like Firestarter, I wish to know what program is using how much bandwidth.  Could anyone recommend a good, light program?

Any help would be appreciated.  Thanks a bunch!

Cheers.

---

### Post by milesmonk on 2008-11-13
/bump/

---

### Post by sefs on 2008-11-13
Hmmmm...sounds like you need to change the stock firmware of your wireless router if it supports that, to something like dd-wrt, open-wrt or tomato.

You would have to google those three firmwares and see if your router is supported though.

These open source firmwares support traffic monitoring.

---

### Post by milesmonk on 2008-11-14
Thanks.  But I don't know what to make of this:

Board ID:  	96338W-20P2
Software Version: 	3.08.02.IB.02.01_1206_030308
Bootloader (CFE) Version: 	1.0.37-10.1
Firmware Version: 	DNA-A211-I-0001.01
Hardware Version: 	DNA-A211-I 2.6
Model Name: 	DNA-A211-I
Wireless Driver Version: 	3.131.35.6.cpe2.0a.s

Don't think Tomato, DD-WRT, OpenWRT, or any of the others are possible.  Should I download it, and flash the firmware in any case?  I'm not too sure about it.  Thanks, though.

Any other ideas?

---

