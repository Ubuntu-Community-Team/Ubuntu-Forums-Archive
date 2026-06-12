---
title: "GPSDrive"
date: 2009-07-07
forum: New to Ubuntu
---

### Post by mn_voyageur on 2009-07-07
I have loaded GPSDrive from the package manager.

So, Ver 2.10pre4 is installed.

From:[http://linux.die.net/man/1/gpsdrive](http://linux.die.net/man/1/gpsdrive)

Since Version 2.08 GpsDrive is now able to handle the serial connection itself, so you don't need to start (and use) gpsd anymore.
To enable this feature go into the settings menu, switch to settings 2 and select Use serial connection.

I would think that 2.08 would precede 2.10.  If this is true, then where do I find "Settings 2"?  It is my understanding that GPSD is used to interface the serial to USB information from the older puck style GPS antennas, ie the ones supplied by MS.

I only have two pull down menus.  Options and Help.

I have looked everywhere, but have yet to find where I can switch to the serial connection.

I would appreciate the help.

---

### Post by tgalati4 on 2009-07-07
I'm not on a machine with gpsdrive installed, but I recall that I had to use gpsd to talk to a usb-puck.  Then I set the appropriate device (/dev/ttyUSB0 or similar) in the  gpsdrive configuration.

This worked well.  I was able to run 7 instances of gpsdrive sharing one puck with gpsd.  No memory leaks or hiccups after 4 days of continuous use.  Of course starting up the 8th instance of gpsdrive caused my process count to go from 400 to 4000 quickly and the machine slowed to a crawl.  I was able to recover by killing the 8th instance.

For older gps units that only have a serial hookup (pre-USB) then perhaps you can specify /dev/tty0 and they will work without gpsd.  All I know is you need to start gpsd to create the /dev/ttyUSB0 device so that gpsdrive can see it.

Configuration that you set within gpsdrive is normally stored in ~/.gpsdrive/gpsdriverc

My desktop computer showed /dev/ttyS3 when I was playing with it.  I don't have the laptop handy to check it's configuration.

---

### Post by mn_voyageur on 2009-07-08
I'll try starting gpsd.  I thought that my version was newer and therefore I did not need it.

---

