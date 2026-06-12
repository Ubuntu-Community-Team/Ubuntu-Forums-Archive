---
title: "[SOLVED] What do I need to get my xerox scanner working please?"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by scotttie on 2009-01-02
Hi all,
I have a xerox scanner, tried plugging it in but no joy, any help will be greatly appreciated.
thanks 
Scottie:(

---

### Post by scotttie on 2009-01-02
Bump

---

### Post by halitech on 2009-01-05
what model of scanner is it? and is it just a scanner or a multi-function device?

---

### Post by donkyhotay on 2009-01-05
I've found that *most* scanners work "out of the box" with sane which is installed by default. What happens when you go to
'applications > graphics > Xsane image scanner'?

---

### Post by scotttie on 2009-01-06
Hi halitech/donkyhotay,anyone!
Sorry about the long delay, Its a Xerox 4800 flatbed scanner (only)
and when I activate xsane it does a search and says no devices available, doesn't seem to see it, its plugged in a usb socket!
thanks Scottie

---

### Post by scotttie on 2009-01-06
Bump!

---

### Post by scotttie on 2009-01-06
Hi,
looking at previous links on this subject it seems my scanner is not supported by sane so thats appears to be it!
I'll have to use scanner on xp and import files as required.
thanks anyway
scottie

---

### Post by donkyhotay on 2009-01-06
did you already look through this how-to?
[http://tldp.org/HOWTO/Scanner-HOWTO/troubleshooting.html](http://tldp.org/HOWTO/Scanner-HOWTO/troubleshooting.html)

//edit: delayed post, never mind then

---

### Post by halitech on 2009-01-07
before you write it off completely, open a terminal and with the scanner not plugged in, run this```
lsusb
```then plug the scanner in, wait a minute and run it again then post the output here.

---

### Post by tungsten on 2009-01-17
I've got the same scanner - Xerox 4800.

lsusb before plugging it in gives:-

Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 04e6:0325 SCM Microsystems, Inc. eUSB ORCA Quad Reader
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


And after gives:-

Bus 005 Device 012: ID 04a7:03a0 Visioneer Xerox 4800 One Touch
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


So it's obviously being detected, but xsane still not picking it up.
(In case you're wondering, I did unplug the ORCA memory reader to plug the scanner in!).

Andy

---

### Post by halitech on 2009-01-19
so Ubuntu is seeing the device
[color=red]Bus 005 Device 012: ID 04a7:03a0 Visioneer Xerox 4800 One Touch[/color]
have you tried running ```
sudo xsane
```to see if the device is being seen by sudo?

---

### Post by tungsten on 2009-01-25
Sorry for the delay in replying.

Tried  sudo xsane  and got no devices found.

Searching the net does just seem to lead me to the conclusion that this device isn't supported.

Any idea how I go about creating a drive for it from the windows driver?

We could do with some kind of wrapper for scanners, like they use for wireless cards, so we can use windows drivers in-part.

---

### Post by halitech on 2009-01-25
darn, was hoping that it would be seen by sudo. I'm not sure how to do it but would require writing code to use the windows drivers. Maybe submit info to the xsane project and see if they can help out.

---

