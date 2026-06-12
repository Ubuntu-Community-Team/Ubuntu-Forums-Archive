---
title: "Pharos GPS-360 from MS Streets &amp; Trips and GPSD"
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by Mud.Knee.Havoc on 2007-10-19
I'm having problems getting the Pharos GPS-360 (ie. the GPS puck that comes with Microsoft Streets and Trips 2006) working with my Ubuntu setup.  It's on a Dell Inspiron 1501 laptop.  I was hoping to get some GPS going on so I could map out some parks that so far aren't on Openstreetmap.org.

I plugged in the usb cable that comes with it, dmesg shows me > [ 5611.808000] pl2303 4-1:1.0: pl2303 converter detected
[ 5611.808000] usb 4-1: pl2303 converter now attached to ttyUSB0


and lsusb shows

> Bus 004 Device 003: ID 067b:aaa0 Prolific Technology, Inc.

So far, everything seems fine.

I've installed gpsd and gpsdrive, and as far as I know have the necessary config files all set up properly.  When I run gpsdrive, though, it stays in simulation mode (granted, I'm not sure exactly which GPS settings to use - I've tried everything) after saying that no GPS was found.

According to [http://roadnav.sourceforge.net/wiki/index.php/GPS_units](http://roadnav.sourceforge.net/wiki/index.php/GPS_units) and a couple other spots, the Pharos/MS GPS-360 should work with little problem.  

I've seen other people have success with some Windows programs running via Wine, but I haven't had such luck.  I tried SeaClear, but it doesn't pick up anything either.  I've even made the symbolic link within wine to make it seem as if my ttyUSB0 is actually a com port. 

Does anybody have any tips?  I'm pretty confused...

---

### Post by tgalati4 on 2007-10-19
I assume that you are using this outdoors.

The Pharos GPS-360 uses the SirFStar II chipset which is weaker than the current SirFStar III units out now.  You need to be outside, in the clear to get decent satellite lock.  If you are inside or under trees, satellite lock is spotty.

Grab the latest gpsdrive and compile it from source.  It's much better than the old version in the repos.  You don't need gpsd if you set the correct /dev/ttyUSB0 port in gpsdrive's preference settings.

---

