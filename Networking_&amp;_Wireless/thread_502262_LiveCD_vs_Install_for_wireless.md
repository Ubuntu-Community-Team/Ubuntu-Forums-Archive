---
title: "LiveCD vs Install for wireless"
date: 2007-07-16
forum: Networking &amp; Wireless
---

### Post by wolfmanyoda on 2007-07-16
Hello everyone, I've been thinking of trying out Ubuntu for quite awhile now. I've had OpenSuse for about a year just playing around a bit with it, still have a dual boot with XP.
The only thing keeping me from installing Ubuntu was the bloody nightmare it was to get my wireless USB to work in OpenSuse.

I downloaded the LiveCD of Ubuntu this morning to try it out. It did detect my USB adapter but I can't get onto the Internet. I went into the Network Settings and filled in Network Name and Network Password for my router but no luck, not sure if I have to change anything else.

Here is some info that I grabbed with lshw and lsusb:

*-usb                   
description: Generic USB device                   
product: Belkin 54g USB Network Adapter                   
vendor: Belkin                   
physical id: 5                   
bus info: usb@4:5                   
version: 0.01                  
capabilities: usb-2.00                   
configuration: driver=rt73usb maxpower=300mA speed=480.0MB/s
      
 *-network       
description: Wireless interface       
physical id: 1       
logical name: wlan0       serial: 00:11:50:a4:e8:2a       
capabilities: ethernet physical wireless       
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

Bus 004 Device 002: ID 050d:705a Belkin Components 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

I'm far from an expert, still a beginner really and I was wondering if the info I put into the Network Settings only works on the full install and not the LiveCD?
Thanks for reading.

---

### Post by aysiu on 2007-07-16
I don't have a Belkin 54g wireless card, but one of these threads might help:
[http://ubuntuforums.org/showthread.php?t=187004](http://ubuntuforums.org/showthread.php?t=187004)
[http://ubuntuforums.org/showthread.php?t=272813](http://ubuntuforums.org/showthread.php?t=272813)
[http://ubuntuforums.org/showthread.php?t=291917](http://ubuntuforums.org/showthread.php?t=291917)

---

