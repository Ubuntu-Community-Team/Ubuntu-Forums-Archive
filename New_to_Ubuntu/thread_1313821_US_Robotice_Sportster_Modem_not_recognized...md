---
title: "US Robotice Sportster Modem not recognized.."
date: 2009-11-04
forum: New to Ubuntu
---

### Post by frank cox on 2009-11-04
I bought a serial modem and attached it with a 25 pin serial cable at the modem and the machine. 
Is ir possible I need to attach it to the 9 pin connection on the machine?
It does not show up in gnome-ppp or anywhere else I can find.

TIA

---

### Post by nhasian on 2009-11-04
it should work on either the 9pin or 25pin serial connectors.  just make sure you have the com ports enabled by your bios.

---

### Post by lkraemer on 2009-11-05
It should work fine if you have a standard serial cable.  Most Linux
and Windows Boxes use a 9 pin MALE on the RS-232C port, and the Modem
has a 25 Pin Male (Pins).  I don't have the cable pinout handy, but
it shouldn't matter if you have a standard bought cable.

If you have a 25 Pin FEMALE Connector on your Box, it most likely is
the Parallel Port.  It is easy to tell, because when you open the Box and
follow the cable back to the Motherboard, or ISA (PCI) card a Serial
cable will only have 9 Conductors, and a Parallel will be a much wider
25 Conductor Cable.  Not many Computers nowdays still have a 25 Pin
Serial Connectors.  I'd bet you have connected to a Parallel port.

You most likely will have to go to another computer and download wvdial and the
four dependencies that are needed to install wvdial.....unless you have
an Ethernet connection available.  I can tell you the dependencies needed
if you need them, as I have been through that.  It will just take a bit
to find my document.

You should be able to configure wvdial and use wvdial to locate the port.
In a Terminal window do:
```

sudo wvdial /etc/wvdial.conf

``` 
wvdial should locate the port and build a configuration file.

You can also buy a USB to RS-232C Cable and use that with wvdial.
The USB to Serial Converter is from [www.newegg.com](www.newegg.com) and is a
N82E16812156008 SABRENT 1 ft. USB to Serial db9 Male RS-232 (9-pin)
Converter Model SBT-USC1M - Retail @ $10.99.

These work wonderful with wvdial, etc.

And for a Guide on getting on with Dialup via Modem see this post.
[http://ubuntuforums.org/showthread.php?t=1100310&highlight=sm56](http://ubuntuforums.org/showthread.php?t=1100310&highlight=sm56)
Post #4

lk

---

### Post by Shazaam on 2009-11-05
Others here have posted using pppconfig instead of wvdial in Jaunty. It is supposedly simpler but I haven't tried it yet. Do a search of the forums.
Run this in terminal for info...
```
man pppconfig
```

---

### Post by Bartender on 2009-11-05
> **frank cox said:**
> I bought a serial modem and attached it with a 25 pin serial cable at the modem and the machine. 
Is ir possible I need to attach it to the 9 pin connection on the machine?
It does not show up in gnome-ppp or anywhere else I can find.

TIA

25 pin serial at the PC end??  I've never heard of this before.  I have several Sportsters.  They all connect at the PC via the small port that looks very similar to the old video D-sub port, except the serial port is a light greenish-blue color and it's a male port (pins sticking out of it) instead of a female port.

All I remember seeing at the PC end is one, or two, of those small serial ports, not a big fat connector like the one on the back of the modem. 

What kind of PC you got?

---

### Post by frank cox on 2009-11-07
> **Shazaam said:**
> Others here have posted using pppconfig instead of wvdial in Jaunty. It is supposedly simpler but I haven't tried it yet. Do a search of the forums.
Run this in terminal for info...
```
man pppconfig
```

Thanks-I finally got Ubuntu to recognize the modem and dial but it still won;t connect. No problem in Puppy Linux,odd.

---

### Post by frank cox on 2009-11-07
Thanks everyone for all the help. I have the modem working but still not connecting in Ubuntu-only Puppy. I will try the hints first and if necessary ask again.

---

