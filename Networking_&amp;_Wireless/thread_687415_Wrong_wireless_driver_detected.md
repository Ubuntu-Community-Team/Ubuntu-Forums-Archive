---
title: "Wrong wireless driver detected"
date: 2008-02-04
forum: Networking &amp; Wireless
---

### Post by tombarker on 2008-02-04
I have an Edimax wireless USB dongle.  This is detected fine on the live CD with the rt73 driver, and has previously been detected and worked perfectly well on ubuntu 7.10 - running in ad hoc mode.
However upon reinstalling my system it works fine with the live CD but when ubuntu is installed on the hard drive it detects the rt2500 driver.  While this is detected to an extent and the nm applet shows there is some kind of network the card fails to show any of these networks in nm.

I assume this is a problem with the driver being used and upon one reinstall it worked fine detecting the rt73 driver, but on  another reinstall it went back to the rt2500.
Is there some way I can force change the driver used to rt73 and make it work?

---

### Post by alan34 on 2008-02-04
You could try blacklisting the rt2500 driver.

Go Applications - Accessories - Terminal

Make a backup of your original file so

sudo cp /etc/modprobe.d/blacklist /etc/modprobe.d/blacklist.backup

then

sudo gedit /etc/modprobe.d/blacklist

at the bottom add

blacklist rt2500

Save and exit, then restart your computer.

Then we hope it picks up the correct driver, if not just either re-edit the file and
delete the last line or

sudo cp /etc/modprobe.d/blacklist.backup /etc/modprobe.d/blacklist

Not sure if this will work for you so good luck

---

### Post by tombarker on 2008-02-04
Spot on Alan, that was exactly what I what I was trying to do but didnt know how.
For anyone else with the same problem the exact text to enter into the blacklist file is:

blacklist rt2500usb

At least that is is what worked for me.

Cheers,

Tom

---

